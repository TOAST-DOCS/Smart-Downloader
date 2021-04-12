## Game > Smart Downloader > SDK User Guide 

## Getting Started

To use Smart Downloader SDK, service must be enabled on console and a registered service must be available.
For more details, see [Console Guide](/Game/Smart%20Downloader/en/console-guide).

### Environments

Smart Downloader SDK supports Unity engines. 

#### Supported Versions

* 2017.4.16 ~ 2020.3.3

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


### Android 네트워크 보안 구성

* CDN을 HTTP로 사용하고 Android 9.0 이상에서 target API 28을 사용하는 경우, HTTP 허용 설정이 필요합니다.
* 자세한 내용은 [네트워크 보안 구성](https://developer.android.com/training/articles/security-config?hl=en)을 참고 바랍니다.

#### 1. AndroidManifest.xml 설정

* AndroidManifest.xml 내 application에 android:networkSecurityConfig 설정을 추가합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest ... >
    <application android:networkSecurityConfig="@xml/network_security_config"
    ... >
        ...
    </application>
</manifest>
```

#### 2. network_security_config.xml 추가

* Plugins/Android/res/xml/network_security_config.xml을 추가합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<network-security-config>
  <domain-config cleartextTrafficPermitted="true">
    <domain includeSubdomains="true">cdn.toastcloud.com</domain>
  </domain-config>
</network-security-config>
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
| UseStreamingAssets | false | Streaming Assets 리소스와 비교 여부 지정 |
| PatchCompareFunction | PatchCompareType.INTERGRITY | 리소스 검사 옵션 |
| ClearUnusedResources | false | 사용하지 않는 리소스 제거<br>(현재 CDN에 없는 이전에 다운로드한 리소스 제거) |

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

### Streaming Assets 리소스와 비교하기

UseStreamingAssets의 값을 활성화 하면 Streaming Assets 내부의 리소스와 업로드된 리소스의 경로를 비교하여 변경된 리소스를 다운로드 받습니다.

**주의**

* Smart Downloader에 업로드 된 데이터는 항상 최신임을 보장해야 합니다.
* 유니티 프로젝트의 Streaming Assets 경로를 기준으로 업로드 된 리소스 경로를 비교합니다.
* 업로드된 리소스가 Streaming Assets 내의 파일과 다르거나 신규 리소스가 있다면, 다운로드 시 지정한 DownPath에 해당되는 파일을 다운로드 받습니다.<br>사용자는 리소스를 사용할 때 지정한 DownPath에 파일이 있는지 확인하여 파일이 있으면 DownPath 경로의 파일을, 없으면 Streaming Assets 경로의 파일을 사용하면 됩니다.
* Streaming Assets가 업데이트 되어 DownPath에 파일과 동일하다면 DownPath의 파일은 제거됩니다.
* Android의 경우 `Split Application Binary` 설정이 활성화 되면 APK 확장 파일인 OBB 파일에 Streaming Assets이 포함되는데, 이 때 자동으로 디바이스에 OBB 파일을 검색하게 됩니다.
    디바이스에 OBB 파일이 없다면 업로드된 모든 리소스를 다운로드 받습니다. (참고 : [Unity Manual - APK 확장 파일 지원](https://docs.unity3d.com/kr/current/Manual/android-OBBsupport.html))
* PatchCompareFunction 옵션은 PatchCompareType.INTERGRITY 값으로 고정됩니다.


### 리소스 검사 옵션

#### PatchCompareType.INTERGRITY

기본 옵션으로 리소스 검사 시 다운로드된 모든 리소스의 CRC를 계산하여 업로드된 리소스와 비교합니다.

**특징**

* 리소스 무결성 보장
    * 리소스 누락 및 변조를 감지하여 업로드된 리소스를 다운로드 합니다.

#### PatchCompareType.SAVED_INFORMATION

해당 옵션을 사용하면 다운로드된 리소스의 기본 정보를 디바이스에 저장하여 다음 검사 시 업로드된 리소스와 비교합니다.

**특징**

* 리소스 검사 속도가 빠릅니다.

**취약점**

* 리소스 누락 및 변조를 감지할 수 없습니다.
    * 해결책으로 리소스 로드 시 정상적인 데이터가 아니라면 옵션을 INTERGRITY로 변경하여 재다운로드를 진행하여 복구할 수 있습니다.

#### PatchCompareType.SAVED_INFORMATION_AND_SIMPLE_FILE_SCAN

해당 옵션을 사용하면 다운로드된 리소스의 기본 정보를 디바이스에 저장하여 다음 검사 시 업로드된 리소스와 비교하고 디바이스에 실제 리소스가 존재하는지 간단한 검사를 진행합니다.

**특징**

* 리소스 검사 속도가 PatchCompareType.INTERGRITY 옵션에 비해 빠르고,<br>PatchCompareType.SAVED_INFORMATION 옵션보다 조금 느리지만 검사 시 리소스 존재 유무와 업로드 리소스와 다운로드된 리소스의 크기를 검사하여 리소스 누락 방지 및 간단한 검사를 진행합니다.

**취약점**

* 리소스 변조를 감지할 수 없습니다.
    * 해결책으로 리소스 로드 시 정상적인 데이터가 아니라면 옵션을 INTERGRITY로 변경하여 재다운로드를 진행하여 복구할 수 있습니다.


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

For download API, see [Download All Resources](/Game/Smart%20Downloader/en/sdk-guide/#_4).

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

Smart Downloader SDK에서 더 이상 지원하지 않는 API는 Deprecate 처리합니다.
Deprecated된 API는 다음 조건 충족 시 사전 공지 없이 삭제될 수 있습니다.

* 5회 이상의 마이너 버전 업데이트
    * Smart Downloader Version Format - XX.YY.ZZ
        * XX : Major
        * YY : Minor
        * ZZ : Hotfix

* 최소 5개월 경과