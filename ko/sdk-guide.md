## Game > Smart Downloader > SDK 사용 가이드

## 시작하기

Smart Downloader SDK를 사용하려면 콘솔에서 상품이 활성화되어 있어야 하며 등록된 서비스가 있어야 합니다.
자세한 내용은 [콘솔 사용 가이드](/Game/Smart%20Downloader/ko/console-guide)를 참고 바랍니다.

### Environments

Smart Downloader SDK는 유니티 엔진을 지원합니다.

#### Supported Versions

* 2018.4.0 ~ 2021.1.20

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

### Android 네트워크 보안 구성

* CDN을 HTTP로 사용하고 Android 9.0 이상에서 target API 28을 사용하는 경우, HTTP 허용 설정이 필요합니다.
* 자세한 내용은 [네트워크 보안 구성](https://developer.android.com/training/articles/security-config?hl=ko)을 참고 바랍니다.

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

### iOS 네트워크 보안 구성

* CDN을 HTTP로 사용하는 경우 HTTP 허용 설정이 필요합니다.

#### Info.plist 설정

* Info.plist에서 App Transport Security Settings를 추가합니다.

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


## 다운로드 설정

DownloadConfig를 통해 다운로드 설정을 변경할 수 있습니다.
기본 설정은 `DownloadConfig.Default`를 통해 가져올 수 있습니다.

| 변수명 | 초기값 | 설명 |
| --- | --- | --- |
| FixedDownloadThreadCount | -1 | 다운로드 시 사용할 쓰레드 개수 고정<br>(0 이하의 값이면 SDK에서 자동으로 설정) |
| DownloadConnectTimeout | 60 | 다운로드에 대한 연결 타임아웃 (단위: 초) |
| DownloadReadTimeout | 20 | 다운로드에 대한 읽기 타임아웃 (단위: 초) |
| RetryDownloadCountPerFile | 3 | 다운로드 실패 시 재시도하는 횟수 |
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


## 다운로드

### 전체 리소스 다운로드

다운로드 설정에서 다운로드할 리소스를 선택하지 않았다면, 서비스에 배포된 모든 리소스를 다운로드 합니다.

**API**

```cs
static void StartDownload(string appkey, string serviceName, string downPath, OnComplete callback)
static void StartDownload(string appkey, string serviceName, string downPath, DownloadConfig config, OnComplete callback)

delegate void OnComplete(DownloadResult result)
```

* appkey
    * 발급된 Appkey를 입력합니다. 상품 활성화 시에 발급되며 콘솔에서 확인할 수 있습니다.
* serviceName
    * 다운로드 진행할 서비스 이름을 입력합니다. 서비스 이름은 콘솔에서 확인할 수 있습니다.
* downPath
    * 다운로드 받을 경로를 입력합니다. 별도로 권장하고 있는 경로는 없습니다.
    * 플랫폼에서 별도로 디렉터리를 지정하고 싶은 경우 Unity API인 Application.persistentDataPath, Application.temporaryCachePath를 확인 바랍니다.
        * iOS 경로 설정 참고 : [Unity Manual - iOS - 인앱 구매(IAP)를 위한 애플리케이션 준비](https://docs.unity3d.com/kr/2018.3/Manual/iphone-Downloadable-Content.html)
* config (선택)
    * 다운로드 환경 설정을 변경할 수 있습니다. 기본값 사용을 권장합니다.
* callback
    * 다운로드가 완료(성공 혹은 실패) 되면 처리할 코드를 작성합니다. 콜백 함수가 호출되면 DownloadResult 타입의 결과값이 파라미터로 전달됩니다.

**Example**

```cs
SmartDl.StartDownload("Appkey", "ServiceName", "DownloadPath",
    (result) =>
    {
        if (result.Code == ResultCode.SUCCESS || result.Code == ResultCode.SUCCESS_NO_DIFFERENCE)
        {
            // 성공 코드 작성
        }
        else
        {
            // 실패 코드 작성
        }
    });
```

### 선택한 리소스 다운로드

다운로드 설정에서 다운로드할 리소스를 선택하여, 해당 리소스만 다운로드할 수 있습니다.
파일을 찾지 못하면 오류가 반환됩니다. (결과 코드: ERROR_EMPTY_FILE_LIST)

다운로드 API는 [전체 리소스 다운로드](/Game/Smart%20Downloader/ko/sdk-guide/#_4)를 참고 바랍니다.

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
// - Characters 경로 하위 모든 파일
// - Maps/M01 경로 하위 모든 파일
// - Data/CharacterInfo.txt 파일
var downloadConfig = DownloadConfig.Default;
downloadConfig.AddSpecifyPath(@"/Characters");
downloadConfig.AddSpecifyPath(@"/Maps/M01");
downloadConfig.AddSpecifyPath(@"/Data/CharacterInfo.txt");

SmartDl.StartDownload(Appkey, ServiceName, DownloadPath, downloadConfig, 
    (result) =>
    {
        if (result.Code == ResultCode.SUCCESS || result.Code == ResultCode.SUCCESS_NO_DIFFERENCE)
        {
            // 성공 코드 작성
        }
        else
        {
            // 실패 코드 작성
        }
    });
```

### 다운로드 정보 확인 후 다운로드

다운로드 할 파일의 개수, 총 크기를 확인한 후 다운로드를 진행하는 과정입니다.
CheckDownload를 호출하여 다운로드 정보를 확인하고 StartDownload를 진행합니다. 만약 CheckDownload 후 다운로드를 하지 않는다면 StopDownload를 호출해야 합니다.
CheckDownload 호출 후 새롭게 배포가 된다면 StartDownload에서는 오류가 반환되며 다시 CheckDownload 호출부터 진행해야 합니다. (결과 코드: ERROR_CHANGE_METAFILE)

**API**

```cs
static void CheckDownload(string appkey, string serviceName, string downPath, OnComplete callback)
static void CheckDownload(string appkey, string serviceName, string downPath, DownloadConfig config, OnComplete callback)

static void StartDownload(OnComplete callback)

delegate void OnComplete(DownloadResult result)
```

**Example**

```cs
private void CheckDownload()
{
    SmartDl.CheckDownload("Appkey", "ServiceName", "DownloadPath",
        (result) =>
        {
            switch (result.Code)
            {
                case ResultCode.SUCCESS:
                    {
                        // 다운로드 할 파일이 있고, 여기서 SmartDl.Progress 정보를 통해 다운로드 될 파일 개수(SmartDl.Progress.TotalFileCount), 다운로드 받을 크기(SmartDl.Progress.TotalFileBytes)를 확인할 수 있습니다.
                        // 사용자에게 정보를 출력 후 다운로드를 진행한다면 SmartDl.StartDownload API를 호출합니다.
                        StartDownload();
                        break;
                    }
                case ResultCode.SUCCESS_NO_DIFFERENCE:
                    {
                        // 다운로드 받을 파일이 없으므로, 다음 스텝으로 진행합니다.
                        break;
                    }
                default:
                    {
                        //실패코드 작성
                        PrintResult(string.Format("Fail to download [{0}]", result));
                        break;
                    }
            }
        });
}

private void StartDownload()
{
    // SmartDl.CheckDownload 호출 후 수행하는 API로, CheckDownload 이후라면 콜백을 제외한 매개변수는 입력할 필요가 없습니다.
    SmartDl.StartDownload(
        (result) => {
            switch (result.Code)
            {
                case ResultCode.SUCCESS:
                    {
                        // 다운로드 성공
                        break;
                    }
                case ResultCode.ERROR_CHANGE_METAFILE:
                    {
                        // CheckDownload 호출 후 새로운 배포가 발생하여 다시 CheckDownload를 수행해야 합니다.  
                        break;
                    }
                default:
                    {
                        // 기타 실패 원인
                        break;
                    }
            }
        });
}
```

### 다운로드 결과

다운로드 종료 후 등록한 콜백 함수로 DownloadResult를 전달합니다.

| 변수명 | 설명 |
| --- | --- |
| Code | 결과 코드 |
| IsCompleted | 다운로드 완료 여부 |
| Message | 결과 메시지 |

## 다운로드 취소

진행 중인 다운로드를 취소합니다.
StartDownload 콜백이 실패로 반환됩니다. (결과 코드 : USER_CANCEL)

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


## 다운로드 진행 정보

진행 중인 다운로드 정보는 ProgressInfo 타입으로 가져올 수 있습니다.

| 변수명 | 설명 |
| --- | --- |
| FileMap | 현재 쓰레드별 다운로드 중인 파일 정보를 반환 |
| Percentage | 전체 진행율을 반환 |
| Speed | 다운로드 시작으로부터 지금까지의 다운로드 속도를 반환 (단위 : 바이트/초)<br>(전체 다운로드 용량 / 다운로드 시작 시간부터 현재 시간) |
| DownloadedBytes | 현재까지 다운로드 받은 바이트 수를 반환 |
| TotalFileBytes | 다운로드 해야 할 전체 바이트 수를 반환 |
| CompletedFileCount | 현재까지 다운로드 받은 파일 개수를 반환 |
| TotalFileCount | 다운로드 해야 할 전체 파일 개수를 반환 |
| IsCompleted | 다운로드 완료 여부를 반환 |

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



## 로그 레벨 설정

SDK 내부 동작에 대한 로그를 출력하기 위해 SmartDlLogger 타입을 제공합니다.
로그 레벨의 기본값은 Error이며, 로그 이벤트를 등록하지 않으면 아무런 동작을 하지 않습니다.

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