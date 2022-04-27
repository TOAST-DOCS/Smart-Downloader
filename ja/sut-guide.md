## Game > Smart Downloader > Unity Toolガイド

## はじめに

Smart Downloader Unity Tool(SUT)は、Unityからリソースをアップロードして配布できるツールです。

### Environments

#### Unity Supported Versions

* 2018.4.0 ~ 2021.1.15

### Download

[Smart Downloader Unity Tool](/Download/#game-smart-downloader)


### Unity Toolのインストール

1. Unityプロジェクトを開きます。
2. Unityで**Assets > Import Package > Custom Package**を選択します。
3. ダウンロードしたUnity Toolファイル'Smart-downloader-unity-tool-{Version}.unitypackage'を選択し、インポートします。
    ![sut_import.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_import.png)


## Unity Toolの使用

Unity Toolを使用するには、メニューから**Tool > NHN Cloud > Smart Downloader > Unity Tool**を選択します。

### 認証

認証前の場合は、**認証**タブが表示されます。

![sut_credentials_tab.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_credentials_tab.png)

* User ID：NHN CloudクラウドID
* User Access Key ID、Secret Access Key
    1. [APIセキュリティ設定](https://console.toast.com/securitySetting)で、**User Access Key ID作成**を選択します。
    2. 作成ダイアログボックスが表示されたら**User Access Key IDとSecret Access Key作成**を選択します。
    3. Secret Access Key(シークレットキー)発行完了ダイアログボックスが表示されます。
    4. APIセキュリティ設定ページで、発行されたUser Access Key ID情報と状態情報を確認します。

    > [注意]
    > - User Access Key IDは90日毎に変更することを推奨します。
    > - User Access Key IDはNHN Cloud ID毎に5個、 IAM ID毎に5個まで作成可能です。
    > - Secret Access Keyは再確認できず、紛失した場合は再作成する必要があります。発行時は安全な場所に保管してください。

* Project ID
    * Smart Downloaderを利用中のプロジェクトIDです。コンソールの**プロジェクト設定**で確認できます。
    ![console_project_id.png](https://static.toastoven.net/prod_smartdownloader/sut/console_project_id.png)

### サービス照会

認証が完了すると、**アップロード**タブが表示されます。
**Appkey**欄にアプリケーションキーを入力し、**照会**をクリックすると、コンソールで作成されたサービスリストが表示されます。

![sut_upload_tab_base.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_tab_base.png)

* Appkey
    * コンソールのSmart Downloaderサービスで**URL & Appkey**をクリックし、発行されたアプリケーションキーを確認します。
    ![console_appkey.png](https://static.toastoven.net/prod_smartdownloader/sut/console_appkey.png)

### リソースのアップロード

#### 1. サービス選択

サービスリストからアップロードするサービスをクリックし、リソースパスを選択します。
正しいパスを選択すると、**アップロード**ボタンが有効になります。

![sut_upload_step_1.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_1.png)

#### 2. アップロードするリソースの選択

最後にアップロードされたリソースと、選択したパスのリソースを比較し、変更されたリソースの情報を表示します。
アップロードするリソースを選択すると、**アップロード**ボタンが有効になります。

> 注意
OSで自動的に作成するファイル(.DS_Store、desktop.ini、thumbs.db)は除外されます。
リソース1つの最大サイズは、5GBに制限されます。

![sut_upload_step_2.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_2.png)


#### 3. リソースアップロードの進行

アップロード進行状況を表示します。
アップロード進行中にツールを終了すると、アップロードをキャンセルするかどうかを確認するウィンドウが表示されます。

> 注意
アップロード中は、Unityを強制終了しないでください。
強制終了するとアップロード状態で残り、30分後にアップロード失敗に変更されます。

![sut_upload_step_3.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_3.png)

#### 4. 完了

正常に完了すると、確認ウィンドウが表示されます。

![sut_upload_step_4.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_4.png)


### サービス詳細情報

サービスリストからサービスを選択してダブルクリックすると、**サービス詳細情報**画面が表示されます。

![sut_service_detail_info_window.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window.png)

* サービス情報
    * サービス名：サービス登録時に入力したサービス名です。
    * サービス説明：登録されたサービスの説明です。
    * CDNアドレス： CDN接続が完了したアドレスです。
* 最新アップロード情報
    * アップロード日時：リソースを最後にアップロードした日時です。
    * 最終登録者：リソースをアップロードしたUser IDです。
    * アップロードリソース情報：アップロードされたリソースの数と総サイズです。
        * 詳細情報：アップロードされたリソース情報です。
    * ビルド配布日時：最後にビルドが配布された日時です。配布状態が**配布予約中**状態の場合は配布が予約されている日時です。
    * 配布状態：配布状態を確認できます。配布状態は[コンソール使用ガイド](http://docs.toast.com/ja/Game/Smart%20Downloader/ja/console-guide/#4)を参照してください。
        * 更新：サービスの詳細情報を更新します。
        * ビルド配布：ビルドを配布できる状態になると有効になり、最新ビルドをCDNに配布できます。
* ビルド配布履歴：ビルド配布を行った直近10件の履歴が表示されます。

#### ビルド配布

配布状態が**配布待機**、**配布失敗**状態の場合にのみ、最新アップロードリソースをCDNに配布できます。

![sut_service_detail_info_window_deploy1.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window_deploy1.png)

**ビルド配布**ボタンを押すと、以下のようなウィンドウが出力されます。

![sut_service_detail_info_window_deploy2.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window_deploy2.png)

* 即時配布：今すぐ配布を行います。
* 予約配布：ユーザーが指定した時間に配布を行います。

#### 予約配布

**予約配布**を選択すると、以下のような画面が出力されます。

![sut_service_detail_info_window_deploy_reservation1.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window_deploy_reservation1.png)

* 時間帯：配布する基準時間帯を指定します。
* 配布時間：配布時間を指定します。

予約配布時間を指定した時間帯以前の時間に指定した場合、すぐに配布が実行され、予約配布に設定した時間まではアップロードが制限されます。

![sut_service_detail_info_window_deploy_reservation2.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window_deploy_reservation2.png)

配布予約が完了すると、配布状態が**予約状態中**に変更され、ビルド配布日時が予約した時間に変更されていることを確認できます。
**配布予約中**状態では、右側の**配布キャンセル** ボタンを押して予約をキャンセルできます。


### 設定

![sut_settings.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_settings.png)

* バージョン情報：Unity Toolのバージョン情報を表示します。
* 言語変更：ツールの言語を変更します。サポート言語は韓国語、英語、日本語です。
