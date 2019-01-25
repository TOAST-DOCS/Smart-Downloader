## Game > Smart Downloader > Error Codes

## Client SDK

Below are the code values of DownloadResult, delivered as StartDownload API callbacks. 

| Error | Error Code | Description |
|--------|-------|-------|
| Ok | 0 | Returned when download is successful. |
| OkNoDiff | 1 | Not downloaded as there is no change between local and CDN files. <br>Deemed as successful. |
| Cancel | -9 | Download is cancelled. |
| AlreadyDownloading | -10 | Already downloading. |
| ErrorRequestApi | -199 | Failed to request for API server. <br>Check message for details. |
| ErrorWrongApiRequest | -198 | Made a wrong request to API server. |
| ErrorMetafileParse | -197 | Failed to parse metafile. |
| ErrorFileUpdateCheck | -196 | Failed while comparing local and CDN file information. |
| ErrorMetafileDownload | -195 | Failed to download metafile. |
| ErrorResponseApi | -194 | Failed to respond to API server. |
| ErrorFileNotFound | -193 | Downloaded file is not found. |
| ErrorFileInitialize | -299 | Failed to initialize files (creating folder/file) for downloads. |
| ErrorFileRead | -298 | Failed to read files. |
| ErrorFileWrite | -297 | Failed to write files. |
| ErrorUnzip | -296 | Failed to unzip files. |
| ErrorNotEnoughDiskSpace | -295 | Disk space is not enough. |
| ErrorNotAccessDirectory | -294 | Cannot access folder. |
| ErrorSocketConnect | -399 | Socket is disconnected due to network issues. |
| ErrorSocketTimeout | -398 | Timeout has occurred during network connection. |
| ErrorHttpStatusCode | -397 | Failed to request for HTTP.  <br>Check message for details. |
| ErrorSocketConnectTimeout | -396 | Timeout has occurred during socket connection. |
| ErrorRawSocket | -395 | Error has occurred in raw socket. |ㄴ