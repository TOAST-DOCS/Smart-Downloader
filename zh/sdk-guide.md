## Game > Smart Downloader > SDK Guide

### Environments

Smart Downloader SDK는 Unity 엔진을 지원합니다.

#### Supported Version

* 5.6.6 ~ 2018.2.12

#### Supported Platforms

* iOS
* Android
* Windows
* macOS


## API Guide

SDK에서 제공하는 API는 SmartDl 타입에 정적 메서드로 정의되어 있습니다.
제공되는 API는 네임스페이스 Toast.SmartDownloader에 정의되어 있으므로 using 지시문을 미리 선언해두는 것을 권장합니다.


### 시작하기

Smart Downloader SDK를 사용하려면 Console에서 상품이 활성화되어 있어야 하며 등록된 서비스가 있어야 합니다.

[Console Guide](/Game/Smart%20Downloader/zh/console-guide)


### 다운로드 시작

등록된 서비스를 기준으로 다운로드를 수행합니다.

**API**

```cs
static void StartDownload(string appKey, string serviceName, string downPath, OnComplete callback)
static void StartDownload(string appKey, string serviceName, string downPath, DownloadConfig config, OnComplete callback)
```

* appKey
    * 발급된 AppKey를 입력합니다. 상품 활성화 시에 발급되며 Console에서 확인할 수 있습니다.
* serviceName
    * 다운로드 진행할 서비스 이름을 입력합니다. 서비스 이름은 Console에서 확인할 수 있습니다.
* downPath
    * 다운로드 받을 경로를 입력합니다. 별도로 권장하고 있는 경로는 없습니다.
    * 플랫폼에서 별도로 디렉터리를 지정하고 싶은 경우 Unity API인 Application.persistentDataPath, Application.temporaryCachePath를 확인 바랍니다.
* config (선택)
    * 다운로드 환경 설정을 변경할 수 있습니다. 기본값 사용을 권장합니다.
* callback
    ```cs
    delegate void OnComplete(DownloadResult result)
    ```
    * 다운로드가 완료(성공 혹은 실패) 되면 처리할 코드를 작성합니다.
        콜백 함수가 호출되면 DownloadResult 타입의 결과값이 파라미터로 전달됩니다.

**Example**

```cs
SmartDl.StartDownload("AppKey", "ServiceName", "DownloadPath", DownloadConfig.Default, result =>
{
    if (result.IsSuccessful)
    {
        // 성공 코드 작성
    }
    else
    {
        // 실패 코드 작성
    }
});
```

#### DownloadResult

다운로드 결과 콜백으로 전달되는 타입입니다.

| 변수명 | 설명 |
| --- | --- |
| Code | [결과 코드](/Game/Smart%20Downloader/zh/error-code) |
| IsCompleted | 다운로드 완료 여부 |
| Message | 결과 메시지 |
| IsSuccessful | 다운로드 성공 여부 |


#### DownloadConfig

다운로드에 필요한 설정을 변경할 수 있으며 지정된 경로나 파일만 다운로드 받을 수 있습니다.
`DownloadConfig.Default`를 통해 기본값 설정을 가져올 수 있습니다.

| 변수명 | 초기값 | 설명 |
| --- | --- | --- |
| FixedDownloadThreadCount | -1 | 다운로드 시 사용할 쓰레드 개수 고정<br>(0 이하의 값이면 SDK에서 자동으로 설정) |
| DownloadConnectTimeout | 60 | 다운로드에 대한 연결 타임아웃 |
| DownloadReadTimeout | 20 | 다운로드에 대한 읽기 타임아웃 |
| RetryDownloadCountPerFile | 3 | 다운로드 실패시 재시도하는 횟수 |

**Example**

```cs
DownloadConfig config = DownloadConfig.Default;
config.DownloadConnectTimeout = TimeSpan.FromSeconds(60);
config.DownloadReadTimeout = TimeSpan.FromSeconds(20);
config.RetryDownloadCountPerFile = 3;
```

##### 경로나 파일을 지정하여 다운로드

**API**

```cs
void AddSpecifyPath(string path);
void RemoveSpecifyPath(string path);
void ClearSpecifyPath();
```

**Example**

```cs
// Characters 경로 하위 모든 파일, Maps/M01 경로 하위 모든 파일, Data/CharacterInfo.txt 파일을 다운로드 받습니다.
var downloadConfig = DownloadConfig.Default;
downloadConfig.AddSpecifyPath("/Characters");
downloadConfig.AddSpecifyPath("/Maps/M01");
downloadConfig.AddSpecifyPath("/Data/CharacterInfo.txt");

SmartDl.StartDownload(AppKey, ServiceName, DownloadPath, downloadConfig, OnCompleteCallback);
```


### 다운로드 정지

진행 중인 다운로드를 취소합니다.
StartDownload 콜백이 실패(ResultCode : Cancel)로 반환됩니다.

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


### 다운로드 진행 정보 가져오기

진행 중인 다운로드 정보는 ProgressInfo 타입으로 가져올 수 있습니다.

| 변수명 | 설명 |
| --- | --- |
| FileMap | 쓰레드 별 다운로드 중인 파일 정보를 반환 |
| Percentage | 전체 진행율을 반환 |
| Speed | 다운로드 시작으로부터 지금까지의 다운로드 속도를 반환 (단위 : 바이트/초)<br>(전체 다운로드 용량 / 다운로드 시작 시간부터 현재 시간) |
| TotalReceivedBytes | 현재까지 다운로드 받은 바이트 수를 반환 |
| TotalFileBytes | 다운로드 해야 할 전체 바이트 수를 반환 |
| CompletedFileCount | 현재까지 다운로드 받은 파일 개수를 반환 |
| TotalFileNumber | 다운로드 해야 할 전체 파일 개수를 반환 |
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



### 로그 레벨 설정

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