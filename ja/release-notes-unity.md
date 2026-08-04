<!-- pre-align:aligned sig=5855a25dd24f -->

<a id="game-smart-downloader-release-notes-unity-sdk"></a>
## Game > Smart Downloader > リリースノート > Unity SDK { #game-smart-downloader-release-notes-unity-sdk }

<a id="70-20210914-download-sdk"></a>
### 1.7.0 (2021.09.14) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.7.0.unitypackage) { #70-20210914-download-sdk }

<a id="70-20210914-download-sdk-bug-fixes"></a>
#### バグ修正
* DLLエラー修正


<a id="69-20210727-download-sdk"></a>
### 1.6.9 (2021.07.27) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.9.unitypackage) { #69-20210727-download-sdk }

<a id="69-20210727-download-sdk-feature-updates"></a>
#### 機能改善/変更
* Unity最小サポートバージョンを2018.4.0に変更
* Unity 2020.2以降のバージョンで発生するWarningを除去


<a id="68-20210413-download-sdk"></a>
### 1.6.8 (2021.04.13) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.8.unitypackage) { #68-20210413-download-sdk }

<a id="68-20210413-download-sdk-feature-updates"></a>
#### 機能改善/変更
* 除外されたリソース除去オプションを追加
    * API追加
        * DownloadConfig.ClearUnusedResources
* DownloadConfig API改善
    * API変更
        * DownloadConfig.CheckOption (Obsolete) → DownloadConfig.UseStreamingAssets, DownloadConfig.PatchCompareFunction使用
* 失敗率情報を確認するためのログ改善


<a id="67-20200811-download-sdk"></a>
### 1.6.7 (2020.08.11) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.7.unitypackage) { #67-20200811-download-sdk }

<a id="67-20200811-download-sdk-feature-updates"></a>
#### 機能改善/変更
* リソースチェックロジックを改善
* リソースチェックオプションを追加
    * API追加
        * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA_AND_LOCAL_SCAN
* 解凍機能除外
    * API変更
        * ResultCode.ERROR_UNZIP (Obsolete)


<a id="66-20200714-download-sdk"></a>
### 1.6.6 (2020.07.14) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.6.unitypackage) { #66-20200714-download-sdk }

<a id="66-20200714-download-sdk-feature-updates"></a>
#### 機能改善/変更
* ディスクの空き容量確認方法を改善


<a id="65-20200623-download-sdk"></a>
### 1.6.5 (2020.06.23) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.5.unitypackage) { #65-20200623-download-sdk }

<a id="65-20200623-download-sdk-bug-fixes"></a>
#### バグ修正
* 実行環境によってはOverflowExceptionが発生するエラーを修正


<a id="64-20200512-download-sdk"></a>
### 1.6.4 (2020.05.12) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.4.unitypackage) { #64-20200512-download-sdk }

<a id="64-20200512-download-sdk-feature-updates"></a>
#### 機能改善/変更
* リソースチェックオプションを追加
    * API変更
        * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA追加

<a id="63-20200428-download-sdk"></a>
### 1.6.3 (2020.04.28) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.3.unitypackage) { #63-20200428-download-sdk }

<a id="63-20200428-download-sdk-feature-updates"></a>
#### 機能改善/変更
* Streaming Assetsサポート
    * Streaming Assetsリソースとアップロードされたリソースを比較ダウンロードする機能を追加
    * API変更
        * DownloadConfig.CheckAndroidObb (Obsolete) → DownloadConfig.CheckOption


<a id="62-20200310-download-sdk"></a>
### 1.6.2 (2020.03.10) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.2.unitypackage) { #62-20200310-download-sdk }

<a id="62-20200310-download-sdk-feature-updates"></a>
#### 機能改善/変更
* Android - Split Application Binary(OBB)をサポート
    * OBBに含まれるStreaming Assetsリソースとアップロードされたリソースを比較ダウンロードする機能を追加
    * API追加
        * DownloadConfig.CheckAndroidObb

<a id="61-20200121-download-sdk"></a>
### 1.6.1 (2020.01.21) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.1.unitypackage) { #61-20200121-download-sdk }

<a id="61-20200121-download-sdk-bug-fixes"></a>
#### バグ修正
* ダウンロードチェックするファイルがない場合に発生していた例外を修正


<a id="60-20191224-download-sdk"></a>
### 1.6.0 (2019.12.24) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.0.unitypackage) { #60-20191224-download-sdk }

<a id="60-20191224-download-sdk-feature-updates"></a>
#### 機能改善/変更
* 事前にダウンロード容量を確認するためにAPIを追加(CheckDownload)
* API変更
    * DownloadResult.IsSuccessful (Obsolete) → DownloadResult.Code
    * ProgressInfo.TotalFileNumber (Obsolete) → ProgressInfo.TotalFileCount
    * ProgressInfo.TotalReceivedBytes (Obsolete) → ProgressInfo.DownloadedBytes


<a id="59-20191029-download-sdk"></a>
### 1.5.9 (2019.10.29) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.9.unitypackage) { #59-20191029-download-sdk }

<a id="59-20191029-download-sdk-feature-updates"></a>
#### 機能改善/変更
* 統計指標改善

<a id="58-20190729-download-sdk"></a>
### 1.5.8 (2019.07.29) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.8.unitypackage) { #58-20190729-download-sdk }

<a id="58-20190729-download-sdk-bug-fixes"></a>
#### バグ修正
* 特定Androidでダウンロード完了処理中にクラッシュが発生する現象を修正


<a id="57-20190625-download-sdk"></a>
### 1.5.7 (2019.06.25) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.7.unitypackage) { #57-20190625-download-sdk }

<a id="57-20190625-download-sdk-feature-updates"></a>
#### 機能改善/変更
* Aboutメニューを追加
* 全てのリソースダウンロード時、ダウンロードするリソースが1つもない場合は、結果コードを成功(SUCCESS_NO_DIFFERENCE)として送信
* フォルダ構造を変更
    * Assets/SmartDL/ → Assets/TOAST/SmartDL
    * `インストールされているSmartDLフォルダを削除した後、インポート(import)する必要があります。`

<a id="56-20181227-download-sdk"></a>
### 1.5.6 (2018.12.27) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.6.unitypackage) { #56-20181227-download-sdk }

<a id="56-20181227-download-sdk-bug-fixes"></a>
#### バグ修正
* ダウンロードキャンセル時、結果コールバックが呼び出されない問題を修正

<a id="56-20181227-download-sdk-feature-updates"></a>
#### 機能改善/変更
* Common
    * [ResultCodeリニューアル](/Game/Smart%20Downloader/ko/error-code)
    * [注意]既存SDKでアップデートする場合、エラーが発生
* iOS
    * iOS 12サポート
* Standalone(Windows)
    * DLL名およびパス変更
        * smartnative_x86.dll → x86/smartnative.dll
        * smartnative_x64.dll → x86_64/smartnative.dll


<a id="55-20181127-download-sdk"></a>
### 1.5.5 (2018.11.27) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.5.unitypackage) { #55-20181127-download-sdk }

<a id="55-20181127-download-sdk-bug-fixes"></a>
#### バグ修正
* IL2CPPビルドサポート
* 断続的にmacOSでIPアドレスを取得できない問題を修正


<a id="54-20181023-download-sdk"></a>
### 1.5.4 (2018.10.23) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.4.unitypackage) { #54-20181023-download-sdk }

<a id="54-20181023-download-sdk-feature-updates"></a>
#### 機能改善/変更
* Unity 2018.2サポート
* パスおよびファイルを選択してダウンロードする機能を提供
* ダウンロードファイルサイズの計算を改善
* サンプルコードに名前空間を追加

<a id="54-20181023-download-sdk-bug-fixes"></a>
#### バグ修正
* iOSでファイル名にハングルが含まれる時、ダウンロードできない問題を修正
* ファイル名とディレクトリ名に一部特殊文字が含まれる時、ダウンロードできない問題を修正



<a id="53-20180605-download-sdk"></a>
### 1.5.3 (2018.06.05) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.3.unitypackage) { #53-20180605-download-sdk }

<a id="53-20180605-download-sdk-feature-updates"></a>
#### 機能改善/変更
* 再試行ロジックを追加
* 接続タイムアウト / 読み取りタイムアウトを分離


<a id="51-20180418-download-sdk"></a>
### 1.5.1 (2018.04.18) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.1.unitypackage) { #51-20180418-download-sdk }

<a id="51-20180418-download-sdk-bug-fixes"></a>
#### バグ修正
* Unity最適化オプション設定で発生するリンクエラーを修正


<a id="50-20180222-download-sdk"></a>
### 1.5.0 (2018.02.22) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.0.unitypackage) { #50-20180222-download-sdk }

<a id="50-20180222-download-sdk-feature-updates"></a>
#### 機能改善/変更
* Smart Downloader内の個別単位<b>サービス</b>を追加
* Coreライブラリの依存性を削除
* API変更
    * ユーザビリティを改善するためにAPIを変更


<a id="20-20171026-download-sdk"></a>
### 1.2.0 (2017.10.26) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.2.0.unitypackage) { #20-20171026-download-sdk }

<a id="20-20171026-download-sdk-feature-updates"></a>
#### 機能改善/変更
* 安定性強化
    * 内部Core SDKの依存性を削除
    * Nativeライブラリの依存性を削除

<a id="10-20170223-download-sdk"></a>
### 1.1.0 (2017.02.23) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/SmartDownloaderSDK_v1.1.0.unitypackage) { #10-20170223-download-sdk }

<a id="10-20170223-download-sdk-feature-updates"></a>
#### 機能改善/変更
* class Name変更(DLCSkin -> SmartDLUnitySkin).
* 静的APIのみ提供
