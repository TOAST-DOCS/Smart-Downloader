## Upcoming Products > Smart Downloader > Developer's Guide

## Smart Downloader Client SDK

Smart Downloader ClientSDK는 현재 Unity Version으로 개발이 되어 있으며, iOS / Android / Windows / MacOS 플랫폼을 지원하고 있습니다.

### **Smart Downloader Client SDK API**

Smart Downloader Client SDK API는 모두 static version으로 호출할 수 있습니다. 그리고 Toast.SmartDownloader 이하의 namespace를 사용하므로 using으로 미리 선언해두는 것을 권장합니다.

0. 용어 설명
- AppKey : 인증된 사용자임을 확인하기 위한 값. AppKey 인증이 성공해야 리소스들을 다운로드받을 수 있습니다.
- Service : 다운로드 리소스 묶음의 최소 단위. 사용자는 한번에 하나의 Service 를 다운로드 받을 수 있습니다. Service 등록은 웹콘솔을 통해서 할 수 있습니다.

1. 웹콘솔에서 Appkey 및 등록된 Service 확인
- 웹콘솔에서 상품을 활성화하면 AppKey를 확인할 수 있습니다.
- Smart Downloader SDK는 Service가 등록되어 있어야 사용할 수 있습니다. 만약 등록된 서비스가 없다면 웹콘솔을 통해서 등록해주시기 바랍니다.

2. Service 다운로드
- Smart Downloader SDK는 Service를 기준으로 다운로드를 수행합니다.
- 다운로드 완료시 콜백으로 들어오는 타입은 DownloadResult 이며 해당 타입에 대한 설명은 아래 설명을 참고해주시기 바랍니다.
- StartDownload API
    - 메소드 시그니쳐
        - void StartDownload(string appKey, string serviceId, string downPath, SmartDl.OnComplete callback)
        - void StartDownload(string appKey, string serviceId, string downPath, DownloadConfig config, SmartDl.OnComplete callback)
    - 콜백 대리자 시그니쳐
        - delegate void OnComplete(DownloadResult result)
    - 매개변수
        - appKey : 웹콘솔에서 확인한 AppKey를 입력합니다.
        - serviceName : 다운로드할 Service 이름을 입력합니다.
        - downloadPath : 다운로드 받을 경로를 입력합니다.
            - 플랫폼별 특정 디렉토리를 사용하고 싶은 경우, Unity3D가 제공하는 Application.persistentDataPath, Application.temporaryCachePath를 확인해주세요.
        - config (선택) : 다운로드에 필요한 설정을 함께 요청할 수 있습니다. 
            - 다운로드 설정은 기본값을 권장하므로, 특별한 경우가 아니라면 설정 객체를 필요로 하지 않는 StartDownload 메소드를 사용해주시기 바랍니다.
        - callback : 다운로드가 완료(성공 혹은 실패) 되면 처리할 코드를 작성합니다.
    - 콜백 반환값
        - DownloadResult : 다운로드 결과로 콜백을 통해서 반환되는 타입입니다.
            - Code : 결과 코드를 반환합니다.
            - IsCompleted : 다운로드 완료 여부를 반환합니다.
            - Message : 결과 메시지를 반환합니다.
            - IsSuccessful : 다운로드 성공 여부를 반환합니다. 

- 예제코드

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

### **Smart Downloader Error Code**

다음은 Smart Downloader Error Code에 대한 값 및 설명이다.

```
public enum DLCErrorCode
{
    DLC_ERR_OK = 0,
    DLC_ERR_CANCEL = 1,
    DLC_ERR_NO_DIFF = 2,
    DLC_ERR_APP_KEY_AUTH_FAILED = 3,
    DLC_ERR_METAFILE_PARSE_ERROR = 4,
    DLC_ERR_FILE_INITIALIZE = 5,
    DLC_ERR_FILE_READ = 6,
    DLC_ERR_FILE_WRITE = 7,
    DLC_ERR_UNZIP_FAILED = 8,
    DLC_ERR_THREAD_VANISHED = 9,
    DLC_ERR_INTERNET_CONNECT = 10,
    DLC_ERR_SOCKET_CLOSED = 11,
    DLC_ERR_SOCKET_CONNECT_FAILED = 12,
    DLC_ERR_SOCKET_TIMEOUT = 13
}
```

| 에러코드 | 설명 |
|--------|-------|
| DLC_ERR_OK | 다운로드가 성공적으로 끝난 후 리턴하는 값이다. |
| DLC_ERR_CANCEL | 추후 사용 예정 |
| DLC_ERR_NO_DIFF | 이미 리소스를 다운로드 받은 후에 다시 다운로드 시에 로컬 파일과 CDN의 파일들이 변한 것이 없을때 리턴하는 값이다. 이 값도 성공으로 간주하고 구현을 진행하면 된다.  |
| DLC_ERR_APP_KEY_AUTH_FAILED | DLC 상품 이용시에 할당 받은 appkey로 상품 인증을 하는데, 그 인증이 실패 했을 때 리턴하는 값이다. |
| DLC_ERR_METAFILE_PARSE_ERROR | CDN에서 메타파일 데이터를 읽어온 후에 파싱을 해야 하는데 해당 파싱이 실패 했을 때 리턴하는 값이다. |
| DLC_ERR_FILE_INITIALIZE | 추후 사용 예정 |
| DLC_ERR_FILE_READ | 추후 사용 예정 |
| DLC_ERR_FILE_WRITE | 추후 사용 예정 |
| DLC_ERR_UNZIP_FAILED | 파일 다운로드 이후에 압축 해제가 실패했을때 리턴하는 값이다. |
| DLC_ERR_THREAD_VANISHED | 멀티 스레드로 다운로드 할 경우 특정 스레드에서 다운로드 실패 했을때 리턴하는 값이다. |
| DLC_ERR_INTERNET_CONNECT | DLC를 사용하는 디바이스나 데스크탑 환경이 인터넷 연결이 되어 있지 않거나 실패 했을때 리턴하는 값이다. |
| DLC_ERR_SOCKET_CLOSED | 외부 요인(망 변경, 인터넷 끊김 등)에 의해서 Socket이 닫혔을때 리턴하는 값이다. |
| DLC_ERR_SOCKET_CONNECT_FAILED | Socket연결에 실패 했을떄 리턴하는 값이다. |
| DLC_ERR_SOCKET_TIMEOUT | Socket 연결 시도 후에 타임아웃이 발생 했을때 리턴하는 값이다. |
