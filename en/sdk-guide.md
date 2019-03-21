## Game > Smart Downloader > SDK User Guide 

## Getting Started

Smart Downloader SDK를 사용하려면 콘솔에서 상품이 활성화되어 있어야 하며 등록된 서비스가 있어야 합니다.
자세한 내용은 [콘솔 사용 가이드](/Game/Smart%20Downloader/en/console-guide)를 참고 바랍니다.

### Environments

Smart Downloader SDK supports Unity engines. 

#### Supported Versions

* 5.6.6 ~ 2018.3.8

#### Supported Platforms

* iOS
* Android
* Standalone
    * Windows
    * macOS
* Editor


### SDK 

#### 1. 다운로드

[Download SDK](/Download/#game-smart-downloader)

#### 2. SDK 설치

1. 유니티 프로젝트를 엽니다.
2. 유니티에서 [Assets > Import Package > Custom Package]를 선택합니다.
3. 다운로드한 SDK 파일 'Smart-downloader-{Version}.unitypackage'을 선택한 후 임포트 합니다.
![smartdl_sdk_01.png](https://static.toastoven.net/prod_smartdownloader/sdk/smartdl_sdk_01.png)

#### 3. SDK 구조

* SDK는 'Assets/SmartDL' 폴더에 설치됩니다.
* 전부 임포트하면 Plugins와 Example로 나뉘어 있습니다.
    * Plugins : SDK 사용을 위한 DLL을 비롯한 플러그인을 포함하고 있습니다.
    * Example : SDK 동작을 확인할 수 있도록 샘플 씬과 스크립트를 포함하고 있습니다.

#### 4. SDK API 사용

* SDK에서 제공하는 API는 네임스페이스 'Toast.SmartDownloader'로 정의되어 있습니다.
* 다운로드 API는 'SmartDl' 클래스를 사용합니다.


## Start Download

서비스를 선택해서 다운로드를 진행합니다.
기본적으로 업로드한 리소스 전체를 다운로드하지만 일부 리소스만 선택해서 다운로드할 수 있습니다.


### 다운로드 설정

DownloadConfig를 통해 다운로드 설정을 변경할 수 있습니다.
Default setting can be imported from `DownloadConfig.Default`. 

| Parameter | Initial Value | Description |
| --- | --- | --- |
| FixedDownloadThreadCount | -1 | Fix the number of threads for downloads <br>(automatically set in SDK for 0 or below) |
| DownloadConnectTimeout | 60 | Timeout for download connection (unit: second) |
| DownloadReadTimeout | 20 | Timeout for download reading (unit: second) |
| RetryDownloadCountPerFile | 3 | Number of retries when download fails |

**Example**

```cs
DownloadConfig config = DownloadConfig.Default;
config.DownloadConnectTimeout = TimeSpan.FromSeconds(60);
config.DownloadReadTimeout = TimeSpan.FromSeconds(20);
config.RetryDownloadCountPerFile = 3;
```

### 전체 리소스 다운로드

다운로드 설정에서 다운로드할 리소스를 선택하지 않았다면, 서비스에 배포된 모든 리소스를 다운로드 합니다.

**API**

```cs
static void StartDownload(string appkey, string serviceName, string downPath, OnComplete callback)
static void StartDownload(string appkey, string serviceName, string downPath, DownloadConfig config, OnComplete callback)

delegate void OnComplete(DownloadResult result)
```

* appkey
    * Enter issued Appkey. An Appkey is issued when a product is enabled and can be found in the console. 
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
SmartDl.StartDownload("Appkey", "ServiceName", "DownloadPath",
    (result) =>
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

### 선택한 리소스 다운로드

다운로드 설정에서 다운로드할 리소스를 선택하여, 해당 리소스만 다운로드할 수 있습니다.
파일을 찾지 못하면 오류가 반환됩니다. (Result Code : ERROR_EMPTY_FILE_LIST)

다운로드 API는 [전체 리소스 다운로드](/Game/Smart%20Downloader/en/sdk-guide/#전체%20리소스%20다운로드)를 참고 바랍니다.

**API**

```cs
class DownloadConfig
{
    void AddSpecifyPath(string path);
    void RemoveSpecifyPath(string path);
    void ClearSpecifyPath();
}
```

**Example**

```cs
// 사용자가 지정한 파일을 다운로드 합니다.
// - All files below the Characters
// - all files below the Maps/M01
// - Data/CharacterInfo.txt file
var downloadConfig = DownloadConfig.Default;
downloadConfig.AddSpecifyPath(@"/Characters");
downloadConfig.AddSpecifyPath(@"/Maps/M01");
downloadConfig.AddSpecifyPath(@"/Data/CharacterInfo.txt");

SmartDl.StartDownload(Appkey, ServiceName, DownloadPath, downloadConfig, 
    (result) =>
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

### 다운로드 결과

Delivered to download result callbacks.

| Parameter | Description |
| --- | --- |
| Code | Result code |
| IsCompleted | If download is completed or not |
| Message | Result message |
| IsSuccessful | If download is successful or not |


## 다운로드 취소

Cancel downloads under progress. 
StartDownload callback is returned as failure. (Result Code : USER_CANCEL)

**API**

```cs
static void StopDownload()
```

**Example**

```cs
void StopDownload()
{
    SmartDl.StopDownload();
}
```


## Download Progress Information 

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



## Setting Log Level 

SmartDILogger type is provided for log outputs on internal SDK activities. 
Default log level is Error, and unless a log event is registered, no activities can be found.  

**API**

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