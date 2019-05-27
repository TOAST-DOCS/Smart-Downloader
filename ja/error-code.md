## Game > Smart Downloader > エラーコード

## Client SDK

StartDownload APIコールバックで伝達するDownloadResultのCode値です。

| エラー | エラーコード | 説明 |
|--------|-------|-------|
| SUCCESS | 0 | ダウンロードしました。 |
| SUCCESS_NO_DIFFERENCE | 1 | ローカルとCDNのファイルを比較し、変更されたファイルがないため、ダウンロードしません。<br>成功とみなします。 |
| USER_CANCEL | -9 | ダウンロードがキャンセルされました。 |
| ALREADY_DOWNLOADING | -10 | すでにダウンロード進行中です。 |
| ERROR_REQUEST_API | -199 | APIサーバー要請が失敗しました。<br>詳細はメッセージを確認してください。 |
| ERROR_WRONG_REQUEST_API | -198 | APIサーバーに無効な要請をしました。 |
| ERROR_METAFILE_PARSE | -197 | メタファイルの解析に失敗しました。 |
| ERROR_PATCH_CHECK | -196 | ローカルとCDNファイル情報を比較する過程で失敗しました。 |
| ERROR_METAFILE_DOWNLOAD | -195 | メタファイルのダウンロードに失敗しました。 |
| ERROR_RESPONSE_API | -194 | APIサーバーレスポンスが失敗しました。 |
| ERROR_EMPTY_FILE_LIST | -193 | ダウンロードファイルが見つかりませんでした。 |
| ERROR_FILE_INITIALIZE | -299 | ダウンロードのためのファイル初期化(フォルダおよびファイル作成)が失敗しました。 |
| ERROR_FILE_READ | -298 | ファイルの読み取りに失敗しました。 |
| ERROR_FILE_WRITE | -297 | ファイルの書き込みに失敗しました。 |
| ERROR_UNZIP | -296 | 圧縮ファイルの解凍に失敗しました。 |
| ERROR_ENOUGH_DISK_SPACE | -295 | ディスクスペースが不足しています。 |
| ERROR_NOT_ACCESS_DIRECTORY | -294 | フォルダにアクセスできません。 |
| ERROR_SOCKET_CONNECT | -399 | ネットワークイシューにより、ソケット接続が切断されました。 |
| ERROR_SOCKET_TIMEOUT | -398 | ネットワーク接続中にタイムアウトが発生しました。 |
| ERROR_HTTP_STATUS_CODE | -397 | HTTP要請が失敗しました。<br>詳細はメッセージを確認してください。 |
| ERROR_SOCKET_CONNECT_TIMEOUT | -396 | ソケット接続過程でタイムアウトが発生しました。 |
| ERROR_RAW_SOCKET | -395 | Rawソケットエラーが発生しました。 |
