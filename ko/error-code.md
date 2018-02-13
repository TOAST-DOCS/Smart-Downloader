## Game > Smart Downloader > 오류 코드

## **Smart Downloader SDK Error Code**

다음은 Smart Downloader Result Code에 대한 값 및 설명입니다. 
해당 Result code는 콜백 결과 객체 DownloadResult의 Code 프로퍼티를 통해 받을 수 있습니다.

| 에러코드 | 설명 |
|--------|-------|
| Ok | 다운로드가 성공적으로 끝난 후 리턴하는 값입니다. |
| Cancel | 다운로드를 중지했을 때 리턴하는 값입니다. |
| OkNoDiff | 이미 리소스를 다운로드 받은 후에 다시 다운로드 시에 로컬 파일과 CDN의 파일들이 변한 것이 없을때 리턴하는 값입니다. 이 값도 성공으로 간주하고 구현을 진행하면 됩니다.  |
| ErrorRequestApi | API 서버 요청이 실패했을 경우 리턴하는 값입니다. 자세한 내용은 메시지를 확인하면 됩니다. |
| ErrorWrongApiRequest | API 서버로 잘못된 요청을 했을 경우 리턴하는 값입니다. |
| ErrorMetafileParse | 메타파일 데이터 파싱이 실패 했을 때 리턴하는 값입니다.|
| ErrorFileUpdateCheck | 기존에 다운로드된 파일과 다운로드 받아야할 파일 정보와의 비교 과정에서 실패했을 때 리턴하는 값입니다. |
| ErrorFileInitialize | 다운로드를 위한 파일 초기화가 실패했을 때 리턴하는 값입니다. (폴더를 생성 못했거나 파일 생성에 실패할 경우) |
| ErrorFileRead | 파일 읽기에 실패했을 때 리턴하는 값입니다. |
| ErrorFileWrite | 파일 쓰기에 실패했을 때 리턴하는 값입니다. |
| ErrorUnzip | 압축 파일 해제에 실패했을 때 리턴하는 값입니다. |
| ErrorNotEnoughDiskSpace | 디스크 공간이 부족할 때 리턴하는 값입니다. |
| ErrorNotAccessDirectory | 폴더 접근이 되지 않을 때 리턴하는 값입니다. |
| ErrorSocketConnect | 네트워크 이슈로 인해 소켓 연결이 끊어졌을 때 리턴하는 값입니다. |
| ErrorSocketTimeout | 네트워크 연결 중 타임아웃이 발생했을 때 리턴하는 값입니다. |
| ErrorHttpStatusCode | HTTP 요청이 실패했을 때 리턴하는 값입니다. 자세한 내용은 메시지를 확인하면 됩니다.  |

### (참고) DownloadResult 클래스
```
public class DownloadResult
{
    public ResultCode Code { get; }
    public bool IsCompleted { get; }
    public string Message { get; }
    public bool IsSuccessful { get; }
}
```