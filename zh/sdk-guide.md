## Game > Smart Downloader > SDK User Guide 

## Getting Started

To use Smart Downloader SDK, service must be enabled on console and a registered service must be available.
For more details, see [Console Guide](/Game/Smart%20Downloader/zh/console-guide).

### Environments

Smart Downloader SDK supports Unity engines. 

#### Supported Versions

* 2018.4.0 - 2021.1.20

#### Supported Platforms

* iOS
* Android
* Standalone
    * Windows
    * macOS
* Editor


### SDK 

#### 1. Download

[Download SDK](/Download/#game-smart-downloader)

#### 2. Install SDK

1. Open a unity project.
2. In Unity, select [Assets > Import Package > Custom Package].
3. Select and import 'Smart-downloader-{Version}.unitypackage', which is a downloaded SDK file.
![smartdl_sdk_01.png](https://static.toastoven.net/prod_smartdownloader/sdk/smartdl_sdk_01.png)

#### 3. SDK Structure

* SDK is installed in the 'Asset/SmartDL' folder.
* Import all, and it is divided into Plugins and Example.
    * Plugins: Includes plugins, including DLL for the use of SDK.
    * Example: Includes sample scenes and scripts to check SDK operations.

#### 4. Apply SDK API

* API provided by SDK is defined as the `Toast.SmartDownloader` namespace.
* 'SmartDI' class is applied for download API.


### Android Network Security Configuration

* If you are using CDN as HTTP and target API 28 on Android 9.0 or higher, you need to add a setting to allow HTTP.
* Refer to [Network Security Configuration](https://developer.android.com/training/articles/security-config?hl=en) for details.

#### 1. Set AndroidManifest.xml

* Add android:networkSecurityConfig setting to the application in AndroidManifest.xml.

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest ... >
    <application android:networkSecurityConfig="@xml/network_security_config"
    ... >
        ...
    </application>
</manifest>
```

#### 2. Add network_security_config.xml

* Add Plugins/Android/res/xml/network_security_config.xml.

```xml
<?xml version="1.0" encoding="utf-8"?>
<network-security-config>
  <domain-config cleartextTrafficPermitted="true">
    <domain includeSubdomains="true">cdn.toastcloud.com</domain>
  </domain-config>
</network-security-config>
```

### iOS Network Security Configuration

* If you are using CDN as HTTP, you need to add a setting to allow HTTP.

#### Set Info.plist

* Add App Transport Security Settings in Info.plist.

```
<key>NSAppTransportSecurity</key>
<dict>
    <key>NSExceptionDomains</key>
    <dict>
        <key>toastcdn.net</key>
        <dict>
            <key>NSExceptionAllowsInsecureHTTPLoads</key>
            <true/>
            <key>NSIncludesSubdomains</key>
            <true/>
        </dict>
    </dict>
</dict>
```


## Start Download

Select a service and download. 
By default, all uploaded resources are downloaded, but only some resources can be selected for a download.


### Download Setting

Download setting can be modified by using DownloadConfig. 
Default setting can be imported from `DownloadConfig.Default`. 

| Parameter | Initial Value | Description |
| --- | --- | --- |
| FixedDownloadThreadCount | -1 | Fix the number of threads for downloads <br>(automatically set in SDK for 0 or below) |
| DownloadConnectTimeout | 60 | Timeout for download connection (unit: second) |
| DownloadReadTimeout | 20 | Timeout for download reading (unit: second) |
| RetryDownloadCountPerFile | 3 | Number of retries when download fails |
| UseStreamingAssets | false | Specify whether to compare with Streaming Assets resources |
| PatchCompareFunction | PatchCompareType.INTERGRITY | Resource check option |
| ClearUnusedResources | false | Remove unused resources (Remove resources downloaded before that are not available in the current CDN) |

**Example**

```cs
DownloadConfig config = DownloadConfig.Default;
config.DownloadConnectTimeout = TimeSpan.FromSeconds(60);
config.DownloadReadTimeout = TimeSpan.FromSeconds(20);
config.RetryDownloadCountPerFile = 3;
config.UseStreamingAssets = false;
config.PatchCompareFunction = PatchCompareType.INTERGRITY;
config.ClearUnusedResources = false;
```

### Comparing with Streaming Assets resources

It you set UseStreamingAssets to true, Smart Downloader SDK compares the paths of resources inside the Streaming Assets and the uploaded resources, and download the changed resources.

**Caution**

* You must ensure that the data uploaded to Smart Downloader SDK is always up to date.
* Smart Downloader SDK compares the path of uploaded resources with the Streaming Assets path of the unity project.
* If the uploaded resources are different from the files inside the Streaming Assets or there are new resources, Smart Downloader SDK downloads the files that correspond to the DownPath specified while downloading.<br>You should check if the files are in the DownPath specified when using the resources. If the files are available, use the files in the DownPath. Otherwise, use the files in Streaming Assets path.
* If the Streaming Assets are updated and becomes the same as files in the DownPath, the files in the DownPath are removed.
* For Android, when `Split Application Binary` setting is activated, Streaming Assets are included in the OBB file, which is an APK expansion file. At this time, the OBB file is searched on the device automatically.
    If there is no OBB file on the device, all uploaded resources are download. (See [Unity Manual - Support for APK expansion files](https://docs.unity3d.com/kr/current/Manual/android-OBBsupport.html))
* The value of PatchCompareFunction option is fixed to the PatchCompareType.INTERGRITY.


### Resource Check Option

#### PatchCompareType.INTERGRITY

The default option. During resource check, Smart Downloader SDK calculates the CRC of all downloaded resources and compare it with the uploaded resources.

**Feature**

* Ensures resource integrity
    * Detects missing or manipulated resources and download the uploaded resources.

#### PatchCompareType.SAVED_INFORMATION

When this option is used, Smart Downloader SDK saves the basic information of the downloaded resources on the device and compares it with the uploaded resources during the next check.

**Feature**

* Speeds up resource check.

**Vulnerability**

* Cannot detect missing or manipulated resources.
    * As a solution, if data is abnormal during the resource loading, you can change the option to INTEGRITY and re-download to repair the data.

#### PatchCompareType.SAVED_INFORMATION_AND_SIMPLE_FILE_SCAN

When this option is used, Smart Downloader SDK saves the basic information of the downloaded resources on the device, compares it with the uploaded resource during the next check, and performs a simple check to see if the actual resources exist on the device.

**Feature**

* Although the speed of resource check is faster than the PatchCompareType.INTERGRITY option
and slightly slower than the PatchCompareType.SAVED_INFORMATION option, it checks whether the resources exist and the sizes of the uploaded resources and downloaded resources to prevent missing resources and to perform a simple check.

**Vulnerability**

* Cannot detect manipulated resources.
    * As a solution, if data is abnormal during the resource loading, you can change the option to INTEGRITY and re-download to repair the data.


### Download All Resources

If a resource is not selected from download setting, all resources deployed for service are to be downloaded. 

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

### Download Selected Resources

Select a resource to download from [Download Setting] so as to download such resource only. 
If a file is not found, error is returned (result code: ERROR_EMPTY_FILE_LIST)

For download API, see [Download All Resources](/Game/Smart%20Downloader/zh/sdk-guide/#_4).

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
// Download user-specified files.
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

### Download Result

Delivered to download result callbacks.

| Parameter | Description |
| --- | --- |
| Code | Result code |
| IsCompleted | If download is completed or not |
| Message | Result message |
| IsSuccessful | If download is successful or not |


## Cancel Download

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


## API Deprecate Governance

The APIs that are not supported by Smart Downloader SDK are deprecated.
Deprecated APIs can be deleted without prior notice when the following conditions are met.

* Minor version updates for 5 times or more
    * Smart Downloader Version Format - XX.YY.ZZ
        * XX : Major
        * YY : Minor
        * ZZ : Hotfix

* 5 months or more have passed after deprecation.
