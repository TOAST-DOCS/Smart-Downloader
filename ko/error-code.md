## Game > Smart Downloader > 오류 코드

## Client SDK

StartDownload API 콜백으로 전달받는 DownloadResult의 Code 값입니다.

| 결과 | 결과 코드 | 설명 |
|--------|-------|-------|
| SUCCESS | 0 | 다운로드를 성공했습니다. |
| SUCCESS_NO_DIFFERENCE | 1 | 로컬과 CDN의 파일 비교 후 변경된 파일이 없어 다운로드 하지 않습니다.<br>성공으로 간주합니다. |
| USER_CANCEL | -9 | 다운로드가 취소되었습니다. |
| ALREADY_DOWNLOADING | -10 | 이미 다운로드 진행 중입니다. |
| ERROR_REQUEST_API | -199 | API 서버 요청이 실패했습니다.<br>자세한 내용은 메시지를 확인 바랍니다. |
| ERROR_WRONG_REQUEST_API | -198 | API 서버로 잘못된 요청을 했습니다. |
| ERROR_METAFILE_PARSE | -197 | 메타파일 파싱에 실패했습니다. |
| ERROR_PATCH_CHECK | -196 | 로컬과 CDN 파일 정보를 비교하는 과정에서 실패했습니다. |
| ERROR_METAFILE_DOWNLOAD | -195 | 메타파일 다운로드에 실패했습니다. |
| ERROR_RESPONSE_API | -194 | API 서버 응답이 실패했습니다. |
| ERROR_EMPTY_FILE_LIST | -193 | 다운로드 파일을 찾지 못했습니다. |
| ERROR_FILE_INITIALIZE | -299 | 다운로드를 위한 파일 초기화(폴더 및 파일 생성)가 실패했습니다. |
| ERROR_FILE_READ | -298 | 파일 읽기에 실패했습니다. |
| ERROR_FILE_WRITE | -297 | 파일 쓰기에 실패했습니다. |
| ERROR_UNZIP | -296 | 압축 파일 해제에 실패했습니다. |
| ERROR_ENOUGH_DISK_SPACE | -295 | 디스크 공간이 부족합니다. |
| ERROR_NOT_ACCESS_DIRECTORY | -294 | 폴더 접근이 되지 않습니다. |
| ERROR_CHECK_DISK_SPACE | -293 | 디스크 공간 확인 시 실패했습니다.<br>자세한 내용은 메세지를 확인 바랍니다. |
| ERROR_SOCKET_CONNECT | -399 | 네트워크 이슈로 소켓 연결이 끊어졌습니다. |
| ERROR_SOCKET_TIMEOUT | -398 | 네트워크 연결 중 타임아웃이 발생했습니다. |
| ERROR_HTTP_STATUS_CODE | -397 | HTTP 요청이 실패 했습니다.<br>자세한 내용은 메세지를 확인 바랍니다. |
| ERROR_SOCKET_CONNECT_TIMEOUT | -396 | 소켓 연결 과정에서 타임아웃이 발생했습니다. |
| ERROR_RAW_SOCKET | -395 | Raw 소켓 에러가 발생했습니다. |