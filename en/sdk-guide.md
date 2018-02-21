## Upcoming Products > Smart Downloader > SDK Guide

## Smart Downloader Client SDK

Smart Downloader ClientSDK는 현재 Unity Version으로 개발이 되어 있으며, iOS / Android / Windows / MacOS 플랫폼을 지원하고 있습니다.

## **Smart Downloader Client SDK API**

Smart Downloader Client SDK API는 모두 SmartDl 타입 하위에 정적 메소드로 정의되어 있습니다. 그리고 Toast.SmartDownloader 이하의 namespace를 사용하므로 using으로 미리 선언해두는 것을 권장합니다.

### 0. 용어 설명
- AppKey : 인증된 사용자임을 확인하기 위한 값. AppKey 인증이 성공해야 리소스들을 다운로드받을 수 있습니다.
- Service : 다운로드 리소스 묶음의 최소 단위. 사용자는 한번에 하나의 Service 를 다운로드 받을 수 있습니다. Service 등록은 웹콘솔을 통해서 할 수 있습니다.

### 1. 웹콘솔에서 Appkey 및 등록된 Service 확인
- 웹콘솔에서 상품을 활성화하면 AppKey를 확인할 수 있습니다.
- Smart Downloader SDK는 Service가 등록되어 있어야 사용할 수 있습니다. 만약 등록된 서비스가 없다면 웹콘솔을 통해서 등록해주시기 바랍니다.

### 2. Service 다운로드 시작
- Smart Downloader SDK는 Service를 기준으로 다운로드를 수행합니다.
- 다운로드 완료시 콜백으로 들어오는 타입은 DownloadResult 이며 해당 타입에 대한 설명은 아래 설명을 참고해주시기 바랍니다.
- StartDownload API
    - 메소드 시그니쳐
        - static void StartDownload(string appKey, string serviceId, string downPath, SmartDl.OnComplete callback)
        - static void StartDownload(string appKey, string serviceId, string downPath, DownloadConfig config, SmartDl.OnComplete callback)
    - 콜백 대리자 시그니쳐
        - delegate void OnComplete(DownloadResult result)
    - 매개변수
        - appKey : 웹콘솔에서 확인한 AppKey를 입력합니다.
        - serviceName : 다운로드할 Service 이름을 입력합니다.
        - downloadPath : 다운로드 받을 경로를 입력합니다.
            - 플랫폼별 특정 디렉토리를 사용하고 싶은 경우, Unity3D가 제공하는 Application.persistentDataPath, Application.temporaryCachePath를 확인해주세요.
            - Smart Downloader가 따로 권장하는 다운로드 위치는 없습니다.
        - config (선택) : 다운로드에 필요한 설정을 함께 요청할 수 있습니다.
            - 다운로드 설정은 기본값을 권장하므로, 특별한 경우가 아니라면 설정 객체가 필요없는 StartDownload 메소드를 사용해주시기 바랍니다.
        - callback : 다운로드가 완료(성공 혹은 실패) 되면 처리할 코드를 작성합니다.
    - 콜백 반환값
        - DownloadResult : 다운로드 결과로 콜백을 통해서 반환되는 타입입니다.
            - Code : 결과 코드를 반환합니다.
            - IsCompleted : 다운로드 완료 여부를 반환합니다.
            - Message : 결과 메시지를 반환합니다.
            - IsSuccessful : 다운로드 성공 여부를 반환합니다. 
    - (참고) DownloadConfig 클래스
        - FixedDownloadThreadCount : 다운로드 쓰레드 갯수를 고정합니다. 0 이하의 값을 설정하면 SDK가 플랫폼별로 쓰레드 갯수를 자동으로 설정합니다.
        - DownloadTimeout : 다운로드 타임아웃 값을 지정합니다. 설정하지 않으면 기본 타임아웃 시간(20초)을 사용합니다.

    - 예제 코드

```
SmartDl.StartDownload("AppKey를 입력합니다", "Service 이름을 입력합니다", "다운로드 받을 경로를 입력합니다", result =>
{
    // 다운로드 완료 처리 코드 작성
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

### 3. Service 다운로드 정지
- 진행중인 다운로드를 정지합니다. 다운로드 정지 기능은 일시정지가 아니라 다운로드를 취소시킵니다.
- StopDownalod API
    - 메소드 시그니쳐
        - static void StopDownload()
    - 예제 코드

```
StopDownload();
```

### 4. 다운로드 진행 정보 가져오기
- 현재 다운로드 중인 진행정보를 가져옵니다.
- Progress API
    - 프로퍼티
        - static ProgressInfo Progress
    - ProgressInfo 타입
        - FileMap : 현재 쓰레드별 다운로드 중인 파일 정보를 반환합니다.
        - Percentage : 전체 진행율을 반환합니다.
        - Speed : 다운로드 시작으로부터 지금까지의 다운로드 속도를 반환합니다.
            - (전체 다운로드 용량 / 다운로드 시작으로부터 현재 시간)
            - 단위 : 바이트/초
        - TotalReceivedBytes : 현재까지 다운로드 받은 바이트 수를 반환합니다.
        - TotalFileBytes : 다운로드 받아야 할 전체 바이트 수를 반환합니다.
        - CompletedFileCount : 현재까지 다운로드 받은 파일 갯수를 반환합니다.
        - TotalFileNumber : 다운로드 받아야 할 전체 파일 갯수를 반환합니다.
        - IsCompleted : 다운로드 완료 여부를 반환합니다.
    - 예제 코드

```
SmartDl.StartDownload(...)
StartCoroutine(UpdateProgress())

// ...

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

### 5. Smart Downloader SDK 내부 로그 레벨 설정
- Smart Downloader SDK는 내부 동작에 대한 로그를 위해 SmartDlLogger 타입을 제공합니다.
- 내부 로그 레벨의 기본값은 Error 이며, 로그 이벤트를 등록하지 않으면 아무런 동작을 하지 않습니다.
- 로그 레벨 설정 예제
```    
SmartDlLogger.CurrentLevel = SmartDlLogger.LogLevel.Debug;
```
- 로그 이벤트 등록 예제
```
SmartDlLogger.OnLog += (type, log) =>
{
    switch (type)
    {
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
    }
};
```
