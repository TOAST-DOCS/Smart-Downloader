## Game > Smart Downloader > Error Codes

## Client SDK

Below are the code values of DownloadResult, delivered as StartDownload API callbacks. 

| Error | Error Code | Description |
|--------|-------|-------|
| SUCCESS | 0 | Returned when download is successful. |
| SUCCESS_NO_DIFFERENCE | 1 | Not downloaded as there is no change between local and CDN files. <br>Deemed as successful. |
| USER_CANCEL | -9 | Download is cancelled. |
| ALREADY_DOWNLOADING | -10 | Already downloading. |
| ERROR_REQUEST_API | -199 | Failed to request for API server. <br>Check message for details. |
| ERROR_WRONG_REQUEST_API | -198 | Made a wrong request to API server. |
| ERROR_METAFILE_PARSE | -197 | Failed to parse metafile. |
| ERROR_PATCH_CHECK | -196 | Failed while comparing local and CDN file information. |
| ERROR_METAFILE_DOWNLOAD | -195 | Failed to download metafile. |
| ERROR_RESPONSE_API | -194 | Failed to respond to API server. |
| ERROR_EMPTY_FILE_LIST | -193 | Downloaded file is not found. |
| ERROR_FILE_INITIALIZE | -299 | Failed to initialize files (creating folder/file) for downloads. |
| ERROR_FILE_READ | -298 | Failed to read files. |
| ERROR_FILE_WRITE | -297 | Failed to write files. |
| ERROR_UNZIP | -296 | Failed to unzip files. |
| ERROR_ENOUGH_DISK_SPACE | -295 | Disk space is not enough. |
| ERROR_NOT_ACCESS_DIRECTORY | -294 | Cannot access folder. |
| ERROR_SOCKET_CONNECT | -399 | Socket is disconnected due to network issues. |
| ERROR_SOCKET_TIMEOUT | -398 | Timeout has occurred during network connection. |
| ERROR_HTTP_STATUS_CODE | -397 | Failed to request for HTTP.  <br>Check message for details. |
| ERROR_SOCKET_CONNECT_TIMEOUT | -396 | Timeout has occurred during socket connection. |
| ERROR_RAW_SOCKET | -395 | Error has occurred in raw socket. |