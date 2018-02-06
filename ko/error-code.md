## Game > Smart Downloader > 오류 코드

## **Smart Downloader Error Code**

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
