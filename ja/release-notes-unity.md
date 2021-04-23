## Game > Smart Downloader > リリースノート > Unity SDK


### 1.6.8 (2021.04.13) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.8.unitypackage)

#### 機能改善/変更
* 제외된 리소스 제거 옵션 추가
    * API 추가
        * DownloadConfig.ClearUnusedResources
* DownloadConfig API 개선
    * API 변경
        * DownloadConfig.CheckOption (Obsolete) → DownloadConfig.UseStreamingAssets, DownloadConfig.PatchCompareFunction 사용
* 실패율 정보를 확인을 위한 로그 개선


### 1.6.7 (2020.08.11) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.7.unitypackage)

#### 機能改善/変更
* 리소스 검사 로직 개선
* 리소스 검사 옵션 추가
    * API 추가
        * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA_AND_LOCAL_SCAN
* 압축 해제 기능 제외
    * API 변경
        * ResultCode.ERROR_UNZIP (Obsolete)


### 1.6.6 (2020.07.14) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.6.unitypackage)

#### 機能改善/変更
* 디스크 여유 공간 확인 방법 개선


### 1.6.5 (2020.06.23) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.5.unitypackage)

#### バグ修正
* 실행환경에 따라 OverflowException이 발생하는 오류 수정


### 1.6.4 (2020.05.12) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.4.unitypackage)

#### 機能改善/変更
* 리소스 검사 옵션 추가
    * API 변경
        * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA 추가

### 1.6.3 (2020.04.28) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.3.unitypackage)

#### 機能改善/変更
* Streaming Assets 지원
    * Streaming Assets 리소스와 업로드 된 리소스를 비교 다운로드 기능 추가
    * API 변경
        * DownloadConfig.CheckAndroidObb (Obsolete) → DownloadConfig.CheckOption


### 1.6.2 (2020.03.10) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.2.unitypackage)

#### 機能改善/変更
* Android - Split Application Binary(OBB)をサポート
    * OBBに含まれるStreaming Assetsリソースとアップロードされたリソースを比較ダウンロードする機能を追加
    * API追加
        * DownloadConfig.CheckAndroidObb

### 1.6.1 (2020.01.21) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.1.unitypackage)

#### バグ修正
* ダウンロードチェックするファイルがない場合に発生していた例外を修正


### 1.6.0 (2019.12.24) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.0.unitypackage)

#### 機能改善/変更
* 事前にダウンロード容量を確認するためにAPIを追加(CheckDownload)
* API変更
    * DownloadResult.IsSuccessful (Obsolete) → DownloadResult.Code
    * ProgressInfo.TotalFileNumber (Obsolete) → ProgressInfo.TotalFileCount
    * ProgressInfo.TotalReceivedBytes (Obsolete) → ProgressInfo.DownloadedBytes


### 1.5.9 (2019.10.29) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.9.unitypackage)

#### 機能改善/変更
* 統計指標改善

### 1.5.8 (2019.07.29) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.8.unitypackage)

#### バグ修正
* 特定Androidでダウンロード完了処理中にクラッシュが発生する現象を修正


### 1.5.7 (2019.06.25) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.7.unitypackage)

#### 機能改善/変更
* Aboutメニューを追加
* 全てのリソースダウンロード時、ダウンロードするリソースが1つもない場合は、結果コードを成功(SUCCESS_NO_DIFFERENCE)として送信
* フォルダ構造を変更
    * Assets/SmartDL/ → Assets/TOAST/SmartDL
    * `インストールされているSmartDLフォルダを削除した後、インポート(import)する必要があります。`

### 1.5.6 (2018.12.27) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.6.unitypackage)

#### バグ修正
* ダウンロードキャンセル時、結果コールバックが呼び出されない問題を修正

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


### 1.5.5 (2018.11.27) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.5.unitypackage)

#### バグ修正
* IL2CPPビルドサポート
* 断続的にmacOSでIPアドレスを取得できない問題を修正


### 1.5.4 (2018.10.23) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.4.unitypackage)

#### 機能改善/変更
* Unity 2018.2サポート
* パスおよびファイルを選択してダウンロードする機能を提供
* ダウンロードファイルサイズの計算を改善
* サンプルコードに名前空間を追加

#### バグ修正
* iOSでファイル名にハングルが含まれる時、ダウンロードできない問題を修正
* ファイル名とディレクトリ名に一部特殊文字が含まれる時、ダウンロードできない問題を修正



### 1.5.3 (2018.06.05) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.3.unitypackage)

#### 機能改善/変更
* 再試行ロジックを追加
* 接続タイムアウト / 読み取りタイムアウトを分離


### 1.5.1 (2018.04.18) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.1.unitypackage)

#### バグ修正
* Unity最適化オプション設定で発生するリンクエラーを修正


### 1.5.0 (2018.02.22) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.0.unitypackage)

#### 機能改善/変更
* Smart Downloader内の個別単位<b>サービス</b>を追加
* Coreライブラリの依存性を削除
* API変更
    * ユーザビリティを改善するためにAPIを変更


### 1.2.0 (2017.10.26) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.2.0.unitypackage)

#### 機能改善/変更
* 安定性強化
    * 内部Core SDKの依存性を削除
    * Nativeライブラリの依存性を削除

### 1.1.0 (2017.02.23) [SDKをダウンロード](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/SmartDownloaderSDK_v1.1.0.unitypackage)

#### 機能改善/変更
* class Name変更(DLCSkin -> SmartDLUnitySkin).
* 静的APIのみ提供

