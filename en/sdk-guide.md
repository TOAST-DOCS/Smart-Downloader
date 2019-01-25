## Game > Smart Downloader > SDK User Guide 

### Environments

Smart Downloader SDK supports Unity engines. 

#### Supported Versions

* 5.6.6 ~ Feb.19, 2018

#### Supported Platforms

* iOS
* Android
* Standalone
    * Windows
    * macOS
* Editor


## API Guide

APsI provided by SDK are defined as static methods under the SmartDI type. 
The provided API is defined in the namespace TOAST.SmartDownloader, so it is recommended to declare using directives in advance.  


### Getting Started 

To use Smart Downloader SDK, products must be enabled in console with registered services. 

[Console Guide](/Game/Smart%20Downloader/ko/console-guide)


### Start Downloading 

Execute downloading for registered services.  

**API**

```cs
static void StartDownload(string appKey, string serviceName, string downPath, OnComplete callback)
static void StartDownload(string appKey, string serviceName, string downPath, DownloadConfig config, OnComplete callback)

delegate void OnComplete(DownloadResult result)
```

* appKey
    * Enter issued AppKey. An AppKey is issued when a product is enabled and can be found in the console. 
* serviceName
    * Enter a service name to download. The service name can be found in the console. 
* downPath
    * Enter path to download. There is no recommended path. 
    * To specify a directory on a platform, check Unity APIs such as Application.persistentDataPath or Application.temporaryCachePath.  
* config (optional)
    * Setting for downloading environment can be changed. Default is recommended, though. 
* callback
    * Write codes to process when downloading is completed (successful or failed). When a callback function is called, the result value of DownloadResult type is delivered to parameters. 

**Example**

```cs
SmartDl.StartDownload("AppKey", "ServiceName", "DownloadPath", DownloadConfig.Default, result =>
{
    if (result.IsSuccessful)
    {
        // Write a success code
    }
    else
    {
        // Write a failure code 
    }
});
```

#### DownloadResult

Delivered to download result callbacks.

| Parameter | Description |
| --- | --- |
| Code | Result code |
| IsCompleted | If download is completed or not |
| Message | Result message |
| IsSuccessful | If download is successful or not |


#### DownloadConfig

Settings required for download can be changed, with only specified paths or files to be downloaded. 
Default setting can be imported from`DownloadConfig.Default`. 

| Parameter | Initial Value | Description |
| --- | --- | --- |
| FixedDownloadThreadCount | -1 | Fix the number of threads for downloads <br>(automatically set in SDK for 0 or below) |
| DownloadConnectTimeout | 60 | Timeout for download connection |
| DownloadReadTimeout | 20 | Timeout for download reading |
| RetryDownloadCountPerFile | 3 | Number of retries when download fails |

**Example**

```cs
DownloadConfig config = DownloadConfig.Default;
config.DownloadConnectTimeout = TimeSpan.FromSeconds(60);
config.DownloadReadTimeout = TimeSpan.FromSeconds(20);
config.RetryDownloadCountPerFile = 3;
```

##### Download by specifying paths or files 

**API**

```cs
void AddSpecifyPath(string path);
void RemoveSpecifyPath(string path);
void ClearSpecifyPath();
```

**Example**

```cs
// Download all files below the Characters path and Maps/M01 path, and Data/CharacterIfo.txt fils 
var downloadConfig = DownloadConfig.Default;
downloadConfig.AddSpecifyPath(@"/Characters");
downloadConfig.AddSpecifyPath(@"/Maps/M01");
downloadConfig.AddSpecifyPath(@"/Data/CharacterInfo.txt");

SmartDl.StartDownload(AppKey, ServiceName, DownloadPath, downloadConfig, OnCompleteCallback);
```


### Suspend Downloading

Cancel downloads under progress. 
StartDownload callback is returned as failure (ResultCode : Cancel).

**API**

```cs
static void StopDownload()
```

**Example**

```cs
void StopDownload
{
    SmartDl.StopDownload();
}
```


### Import Download Progress Information 

Information of progressing download can be imported in the ProgressInfo type. 

| Parameter | Description |
| --- | --- |
| FileMap | Returns information of files which are currently downloaded by thread |
| Percentage | Returns the total rate of progress |
| Speed | Returns download speed from the start, up to now (unit: byte/second) <br>(total download volume /current time from when download started) |
| TotalReceivedBytes | Returns the number of bytes downloaded up to now |
| TotalFileBytes | Returns the total number of bytes to download |
| CompletedFileCount | Returns the number of files downloaded up to now |
| TotalFileNumber | Returns the total number of files to download |
| IsCompleted | Returns whether download is complete |

**API**

```cs
static ProgressInfo Progress;
```

**Example**

```cs
void StartDownload()
{
    SmartDl.StartDownload(AppKey, ServiceName, DownloadPath, downloadConfig, OnCompleteCallback);
    StartCoroutine(UpdateProgress());
}

IEnumerator UpdateProgress()
{
    while (true)
    {
        var progress = SmartDl.Progress;

        Debug.LogFormat("Percentage : {0} %", progress.Percentage);

        var threadCount = progress.FileMap.Count;
        ThreadProgressContainer.Instance.ThreadCount = threadCount;
        for (int i = 0; i < threadCount; i++)
        {
            var file = progress.FileMap[i];
            Debug.LogFormat("Thread[{0}] Percentage : {1} %", i, (file.DownloadedBytes / (float)file.TotalBytes) * 100.0f);
        }

        if (progress.IsCompleted)
            yield break;

        yield return null;
    }
}
```



### Setting Log Level 

SmartDILogger type is provided for log outputs on internal SDK activities. 
Default log level is Error, and unless a log event is registered, no activities can be found.  

```cs
static LogLevel CurrentLevel = LogLevel.Error;
static event Action<LogLevel, string> OnLog;
```

**Example**

```cs
void Initialize()
{
    SmartDlLogger.CurrentLevel = SmartDlLogger.LogLevel.Trace;
    SmartDlLogger.OnLog += (type, log) =>
    {
        switch (type)
        {
            case SmartDlLogger.LogLevel.Trace:
            case SmartDlLogger.LogLevel.Developer:
            case SmartDlLogger.LogLevel.Debug:
            case SmartDlLogger.LogLevel.Info:
                Debug.Log(log);
                break;
            case SmartDlLogger.LogLevel.Warn:
                Debug.LogWarning(log);
                break;
            case SmartDlLogger.LogLevel.Error:
                Debug.LogError(log);
                break;
            default:
                Debug.Log(log);
                break;
        }
    };
}
```