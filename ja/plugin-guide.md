## Game > Smart Downloader > プラグインガイド

## Smart Downloader Jenkins Plugin
Smart Downloader Jenkins Pluginを通して、NHN Cloud Smart Downloaderの**新規ビルドアップロード機能**を便利に使用できます。

## Pluginインストール

#### Jenkinsの最小要件

**Jenkins 2.60.1**以降のバージョンが必要です。Jenkins 2.60.1は、Java 8の実行が可能なJenkins LTSの最初のリリースです。
> 参考： [https://jenkins.io/changelog-stable](https://jenkins.io/changelog-stable)

##### 1. Jenkins Pluginダウンロード
下記リンクから**smartdl-uploader.hpi**ファイルをダウンロードします。
Download ： [smartdl-uploader.hpi](https://static.toastoven.net/toastcloud/sdk_download/Smart Downloader/smartdl-uploader.hpi)

##### 2. インストール
**[Jenkins] > [Jenkins管理] > [プラグイン管理] > [詳細設定] > [プラグインアップロード]**メニューで「1. Jenkins Pluginダウンロード」を通してダウンロードした**smartdl-uploader.hpi**ファイルを選択してアップロードします。

正常にインストールが完了すると、**インストールされたプラグインリスト**タブで下記[図1]のようにインストールされた内容を確認できます。

![図1](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_01.png)
<center>[図1]インストールされたプラグインリスト</center>

## Plugin使用

##### 事前準備
Smart Downloader Jenkins Pluginを使用するためには、「NHN Cloud APIセキュリティー設定」が必要です。
> NHN Cloud APIセキュリティー設定： [https://console.toast.com/securitySetting](https://console.toast.com/securitySetting)

<br>
##### 1. 認証設定

**[Jenkins] > [Credentials] > [System]**メニューでGlobal credentials選択し、Add CredentialsメニューからNHN Cloud認証を追加します。
下の[図2]のように、KindをNHN Cloud Credentiaslsに選択し、NHN Cloud UserID、NHN Cloud AccessKeyID、NHN Cloud SecretKeyを入力します。

![図2](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_02.png)
<center>[図2]認証設定</center>

* Socpe [必須] ： Global選択
* ID ： Jenkinsで内部的に使用するCredential ID値。未入力の時は、自動的にユニークなID値が作成されます。
* Descreption ：該当のNHN Cloud認証の説明を入力できます。
* NHN Cloud UserID [必須] ： NHN Cloud接続アカウント
* NHN Cloud AccessKeyID [必須] ： NHN Cloud APIセキュリティー設定メニューで発行されたAccessKeyID
* NHN Cloud SecretKey [必須] ： NHN Cloud APIセキュリティー設定メニューで発行されたSecretKey

> 参考： [必須]と表示された値は、必須入力値です。この値が未入力の場合は、プラグインが正常に実行されません。

<br>
##### 2. プロジェクト構成
**[Jenkins]** > プロジェクト選択 > **[構成] > [ビルド後の措置]**メニューで「SmartDL Uploader」を追加します。
下の[図3]のように設定値を入力します。

![図3](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_03.png)
<center>[図3]プロジェクト構成</center>

* NHN Cloud Credentials [必須]： <b>1.認証設定</b>を通して追加したNHN Cloud Credentialを選択します。無効な認証キーが入力された場合、認証に失敗し、プラグインが使用できません。
* Enable Upload [必須] ：プラグイン動作の有効 / 無効を決定するオプション値です。プラグイン設定が保存された状態を維持しながらプラグインの動作を無効にすることができます。
* ProjectID [必須] ： Smart Dowonloaderを使用するNHN Cloud Project ID。下の[図4]のようにNHN Cloudコンソールプロジェクト設定メニューで確認できます。
* Appkey [必須] ： Smart Dowonloader Appkey。下の[図5]のように、NHN Cloud Smart DowonloaderコンソールのURL & Appkey画面で確認できます。
* Service Name [必須] ：新規ビルドアップロードを処理するSmart Dowonloaderサービス名を入力します。
* Path [必須]  ：アップロードするフォルダのパスを入力します。フォルダアップロードのみサポートし、単一ファイルのアップロードはサポートしません。

> 参考： [必須]と表示された値は、必須入力値です。この値が未入力の場合は、プラグインが正常に実行されません。

<br>
![図4](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_04.png)
<center>[図4] NHN Cloudプロジェクト設定</center>
![図5](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_05.png)
<center>[図5] Smart Downloader Appkey確認</center>

<br>
##### 3. 結果確認
プロジェクトビルド後のログを通して、Plugin実行結果を確認できます。

![図6](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_06.png)
<center>[図6]コンソールログ</center>

またSmart Downloaderコンソール内の「サービス詳細情報」ページでビルドアップロード履歴を確認できます。
Pluginを通してビルドをアップロードすると、Last UploaderにPluginを実行させたサーバーIPが表示されます。

![図7](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_07.png)
<center>[図7]サービス詳細情報</center>

Pluginの実行結果が失敗の場合、コンソールログのエラーメッセージを参照してください。

## 参考事項
JenkinsでMaster/Slave nodeを構成して使用する場合は**必ずNode情報を設定**してください。

![図8-1](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_08_1.png)
<center>[図8-1] Node設定参考1 </center>

![図8-2](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_08_2.png)
<center>[図8-2] Node設定参考2 </center>

* Node設定は、各プロジェクトの構成に合わせて設定して使用してください。
