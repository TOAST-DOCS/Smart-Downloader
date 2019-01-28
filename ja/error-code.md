## Game > Smart Downloader > エラーコード


## Client SDK

StartDownload APIコールバックで伝達するDownloadResultのCode値です。

| エラー | エラーコード | 説明 |
|--------|-------|-------|
| Ok | 0 | ダウンロード成功時に返します。 |
| OkNoDiff | 1 | ローカルとCDNのファイルを比較し、変更されたファイルがないため、ダウンロードしません。<br>成功とみなします。 |
| Cancel | -9 | ダウンロードがキャンセルされました。 |
| AlreadyDownloading | -10 | すでにダウンロード進行中です。 |
| ErrorRequestApi | -199 | APIサーバー要請が失敗しました。<br>詳細はメッセージを確認してください。 |
| ErrorWrongApiRequest | -198 | APIサーバーに無効な要請をしました。 |
| ErrorMetafileParse | -197 | メタファイルの解析に失敗しました。 |
| ErrorFileUpdateCheck | -196 | ローカルとCDNファイル情報を比較する過程で失敗しました。 |
| ErrorMetafileDownload | -195 | メタファイルのダウンロードに失敗しました。 |
| ErrorResponseApi | -194 | APIサーバーレスポンスが失敗しました。 |
| ErrorFileNotFound | -193 | ダウンロードファイルが見つかりませんでした。 |
| ErrorFileInitialize | -299 | ダウンロードのためのファイル初期化(フォルダおよびファイル作成)が失敗しました。 |
| ErrorFileRead | -298 | ファイルの読み取りに失敗しました。 |
| ErrorFileWrite | -297 | ファイルの書き込みに失敗しました。 |
| ErrorUnzip | -296 | 圧縮ファイルの解凍に失敗しました。 |
| ErrorNotEnoughDiskSpace | -295 | ディスクスペースが不足しています。 |
| ErrorNotAccessDirectory | -294 | フォルダにアクセスできません。 |
| ErrorSocketConnect | -399 | ネットワークイシューにより、ソケット接続が切断されました。 |
| ErrorSocketTimeout | -398 | ネットワーク接続中にタイムアウトが発生しました。 |
| ErrorHttpStatusCode | -397 | HTTP要請が失敗しました。<br>詳細はメッセージを確認してください。 |
| ErrorSocketConnectTimeout | -396 | ソケット接続過程でタイムアウトが発生しました。 |
| ErrorRawSocket | -395 | Rawソケットエラーが発生しました。 |
