## Game > Smart Downloader > Console Guide

Smart Downloaderを使用するために、サービスを有効にした後にサービスを登録する必要があります。
サービス登録は、\[サービス登録\] > \[CDN連携\] > \[リソースアップロード\] 3ステップのWizard形式で構成されています。3ステップのサービス登録Wizardの後、\[ビルド配布\]まで全て完了すると、SDKを通して配布をダウンロードできます。
サービス登録後、該当サービスのリアルタイムダウンロード状況およびダウンロード指標データを多様な形のチャートで提供し、データをダウンロードできます。
<br>

## Configuration

### Smart Downloaderサービス有効
Consoleページ上部の**サービス選択**ボタンをクリック後、Gameの下部Smart Downloaderサービスをクリックしてサービス有効にします。

### AppKeyとURL確認
Consoleページ上部のURL & Appkeyをクリックして発行されたAppkeyを確認します。該当AppkeyはSDKに入力して使用します。
Smart Downloaderサービスを無効にすると、発行されたAppkeyは復旧できませんのでご注意ください。

![smartdl_01_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_01_201812.png)

## サービス管理Tab

### 1. サービス登録
#### 1.1サービス登録
![smartdl_02_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_02_201812.png)

- サービス名
    - サービスを区分できる識別値で**必須入力**です。
    - サービス名は、識別値として使用されるため、1つのプロジェクトに同じサービス名は登録できません。
    - **英小文字、数字、特殊記号(_)、(-)**のみ使用でき、頭文字には**英小文字と数字**のみ使用できます。
    - 頭文字にスペースは使用できません。
    - 最大30Byteに入力を制限します。

- サービス説明
	- サービスの説明を入力します。最大100Byteに入力を制限します。

- サービス登録が完了すると、\[ステップ1. サービス登録完了\]ページに移動します。

#### 1.2サービス登録完了
![smartdl_03_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_03_201812.png)

- 登録されたサービス名と説明を確認できます。\[次へ\]ボタンをクリックすると、サービス登録Wizardのステップ2\[CDN連携\]に移動します。

### 2. CDN連携
#### 2.1 CDN連携案内

![smartdl_04_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_04_201812.png)

- 2.1.1 Smart Downloader CDN連携選択
	- \[CDNサービス作成\]ポップアップを通して、CDN設定情報を入力します。
		![smartdl_05_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_05_201812.png)
		- Service
			- サービスエリア：CDNの適用範囲を選択する項目です。サービス対象国に応じてKorea / Globalを選択してください。デフォルト値はKoreaです。
			- 説明：CDNの簡単な説明を作成する項目です。
		- Cache
			- Cache満了設定：CDNに保存されているファイルを新規ファイルに置き換える周期を選択する項目です。デフォルトで24時間に指定されていて、必要に応じて任意で設定が必要な場合、**ユーザー設定使用**を選択します。
			- Cache満了設定(秒)：**Cache満了設定**で**ユーザー設定使用**を選択した場合、CDNのCache周期を入力する項目です。(デフォルト設定を使用する場合は入力不可)
			- Referrersアクセス管理：CDNへのアクセス制限をどのような形で行うかを選択する項目です。**Blacklist**の場合、入力したReferrersのみアクセスが制限され、**Whitelist**の場合、入力したReferrersのみアクセス可能です。
			- Referrers：アクセス制限するReferrerを入力するための項目です。Regular Expressionをサポートし、複数のReferrerを入力するためには、改行後に入力します。
	- Smart Downloader CDN連携は、最大で約1分かかります。

- 2.1.2顧客社CDN連携選択
	- \[案内\]ポップアップが表示され、顧客社CDNを利用するためのStep1、Step2を進行します。
    ​   ![smartdl_06_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_06_201812.png)
	    - Step 1
	        - **ソースサーバーアドレスに適用するURL**を提供します。
	    - Strep 2
    	    - **使用するCDN URL**を入力してSmart Downloaderサービスと顧客社CDNが連携するように設定します。
	        - 顧客社CDN URLはHTTP/HTTPSプロトコルを選択して入力します。

#### 2.2 CDN連携完了

![smartdl_07_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_07_201812.png)

- 登録されたCDNサーバーアドレスおよびソースサーバーURLを確認できます。 \[次へ\]ボタンをクリックすると、サービス登録Wizardのステップ3\[リソースアップロード\]に移動します。

### 3. リソースアップロード
- リソースアップロードはフォルダアップロードを原則とします。(アップロードボタンをクリックすると、フォルダ参照ウィンドウがロードされます)
- Internet Explorerは、リソースアップロード機能を提供しません。リソースアップロードはChromeを使用してください。

#### 3.1リソースアップロード案内

![smartdl_08_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_08_201812.png)

- A. Local machineアップロード
​    - Consoleページで、ユーザーLocal PCにあるリソースをアップロードできます。
​    - 現在のページで\[リソースアップロード\]ボタンをクリックして進行できます。
​    - アップロードが完了すると、\[ステップ3. リソースアップロード完了\]ページに移動します。

- B.  Build Server(遠隔)アップロード
​    - Smart Downloader Jenkins Plugin(TOAST Cloud Smart Downloader Plugin)でリソースをアップロード。
​    - TOAST Cloud Smart Downloader Pluginの詳細ガイドは、[プラグイン使用ガイド](http://docs.toast.com/ko/Game/Smart%20Downloader/ko/plugin-guide/)で確認できます。

#### 3.2リソースアップロード完了

![smartdl_09_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_09_201812.png)

- サービス名
    - 登録されたサービス名です。

- リソースアップロード情報
	- アップロードされたリソースファイル数と全体のファイルサイズを表示します。
	- 詳細情報ボタンをクリックすると、アップロードされたリソース情報がTree形式ポップアップで表示されます。

- 最終アップロード
    - 最新リソースがアップロードされた最後のアップロード日時です。
    
- 配布状態
    - リソースの現在の状態を表示します。
    - 配布待機状態の場合、\[サービス管理\] - \[サービス詳細\]ページから\[ビルド配布\]ボタンで配布できます。

**\[リソースアップロードキャンセル機能\]**

![smartdl_10_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_10_201812.png)

- Smart Downloaderは、アップロード進行中のアップロードをキャンセルする機能を提供します。
- アップロードのキャンセルが完了すると、配布状態はアップロードする前の状態に戻る点に注意してください。

### 4. サービスリスト
ユーザーが登録したサービスのリストを一度に10個ずつ表示します。各サービスをクリックすると、該当サービスの\[サービス詳細情報\]ページに移動します。

![smartdl_11_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_11_201812.png)

- サービス名
    - サービス登録時にユーザーが入力したサービス名。

- CDN
    - サーバー：CDN download URL. (CDN download URLが登録されていない場合、\[CDN URLを入力する必要があります。\]という文言が表示されます)
    - 状態：Smart Downloader CDN利用時にのみ知ることができるデータです。顧客社CDN利用時に状態領域は**-**と表示されます。
	-   | 状態 | 説明 |
		|----------|---------|
		|![作業中](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_progressing.PNG)| Smart Downloader CDN連携進行中。|
        |![正常](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_success.PNG)       |Smart Downloader CDN正常連携|
        |![作成失敗](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_fail.PNG)   |Smart Downloader CDN連携に失敗しました。この状態が続く場合、サポートへお問い合わせください。 |


- 最新ビルド
    - ビルド配布日時：最新ビルドの最後の配布日時。
    - リソースアップロード日時：最新ビルドの最後のアップロード日時。
    - 状態：アップロードしたリソースの現在の状態。 **配布待機**状態または**配布失敗**状態の場合、\[ビルド配布\]ボタンが有効になります。
	-   | 状態 | 説明 |
		|----------|---------|
		|![登録前](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/resource_not_register.PNG)| リソース登録をしていない状態。|
        |![アップロード中](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/resource_uploading.PNG)  |リソースアップロードが進行中の状態。<br>アップロード中の状態では、新規リソースアップロードおよび削除機能を利用できません。|
        |![配布待機](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/build_complete.PNG)    |リソースのアップロードが完了した状態。 \[ビルド配布\]ボタンを押すとビルドを配布できます。|
        |![配布中](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/deploying.PNG)|\[ビルド配布\]ボタンを押して配布が進行中の状態。<br>配布中の状態で新規リソースアップロード、修正、削除機能を利用できません。|
        |![配布完了](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/deploy_complete.PNG)   |アップロードしたリソースがCDNに配布完了した状態。|
        |![アップロード失敗](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/upload_fail.PNG)   |リソースのアップロードが失敗した状態。この状態が続く場合、サポートへお問い合わせください。|
		|![配布失敗](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/deploy_fail.PNG)   |\[ビルド配布\]ボタンを押して配布が失敗した状態。 \[ビルド配布\]ボタンを押して再配布できます。<br>この状態が続く場合、サポートへお問い合わせください。|


### 5. サービス詳細情報
登録したサービスの詳細情報ページです。 \[サービス情報\]、\[CDN連携案内\]、\[最新ビルド情報\]、\[ビルド配布履歴\]領域で構成されています。

![smartdl_13_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_13_201812.png)

#### 5.1サービス情報
サービス登録時に入力したサービス名とサービス説明を表示します。

#### 5.2 CDN連携案内
CDN連携完了時、サービスに連携したCDN情報が表示されます。下記のA～Cの場合に分けてCDN連携案内を説明します。

**A. Smart Downloader CDN連携**

| 項目 | 説明 |
| --- | --- |
| CDNサーバー | Smart Downloader CDNと表記されます。 |
| CDNサーバーアドレス | Smart Downloader CDN連携時、自動でCDNダウンロードURLが作成され、そのURLが表示されます。 |
| CDN設定情報 | 情報を確認するボタンをクリックしてSmart Downloader CDN設定を確認できます。 |

**B. 顧客社CDN連携**

| 項目 | 説明 |
| --- | --- |
| CDNサーバー | 顧客社CDNと表記されます。 |
| CDNサーバーアドレス | 顧客社CDN連携のためにユーザーが入力した顧客社CDN URLが表示されます。未入力の時は、修正画面に移動して顧客社CDN URLを入力する必要があります。 |
| ソースサーバーURL | ソースサーバーアドレスに適用するURLが表示されます。|

**C. CDN未連携**

- CDN連携の案内ガイド文言が表示されます。修正ボタンをクリックしてCDN情報を設定できます。

#### 5.3最新ビルド情報
リソースアップロード完了時、リソースアップロード情報が表示されます。
配布状態が**登録前**の時は、リソースアップロード情報はすべて空の値が表示されます。( \[リソースアップロード情報\]領域に詳細情報ボタンは無効)

> \[注意点\]
配布状態が**アップロード中**、**配布中**の場合、新規リソースのアップロードができません。
配布状態が**配布待機**状態の場合、最新ビルドをCDNに配布できます。(**配布失敗**状態の場合も、再配布のために\[ビルド配布\]ボタンが有効になります。)

![smartdl_14_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_14_201812.png)

| 項目 | 説明 |
| --- | --- |
| 新規リソースのアップロード | 現在のページで新規リソースをアップロードできます。<br>配布状態が**アップロード中**、**配布中**の場合、新規リソースのアップロードができません。 |
| リソースアップロード情報 | アップロードされたリソースのファイル数と全体ファイルサイズを表示します。 |
| 詳細情報 | アップロードされたリソース情報がTree形式ポップアップで表示されます。 |
| 配布履歴参照 | サービス詳細情報の下に\[ビルド配布履歴\]領域が表示されます。 |
| 最終アップロード日時 | ユーザーが指定したリソースがアップロードされた日時です。 |
| 最終登録者 | リソースをアップロードしたユーザーのTOAST Cloudアカウント情報です。 |
| 配布状態 | 最新ビルドの配布状態で、各状態値はサービスリスト > 最新ビルド領域情報と同じです。 |
| ビルド配布 | 最新ビルド情報の配布状態が**配布待機**状態の場合、最新ビルドを連携したCDNに配布できます。(**配布失敗**状態の場合も再配布のために\[ビルド配布\]ボタンが有効になります。)<br>配布時、Smart Downloader CDNの場合は最大10分、顧客社CDNの場合は使用環境によって配布時間が異なることがあります。  |

#### 5.4ビルド配布履歴

![smartdl_15_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_15_201812.png)

**配布成功**、**配布失敗**状態の履歴情報をビルド配布日時の降順で表示します。

| 項目 | 説明 |
| --- | --- |
| ビルド配布日時 | \[ビルド配布\]ボタンを押して配布が完了した日時です。 |
| 最終配布者| \[ビルド配布\]ボタンを押して配布したユーザーのTOAST Cloudアカウント情報です。 |
| リソースアップロード日時 | ユーザーが指定したリソースがアップロードされた日時です。 |
| 最終登録者 | リソースをアップロードしたユーザーのTOAST Cloudアカウント情報です。 |
| 状態 | 最新ビルドの配布状態で、各状態値は上部の\[最新ビルド情報\]領域の\[配布状態\]と同じです。 |

#### 5.5サービス削除
- \[サービス詳細情報\]ページの右上にある削除ボタンを押してサービスの削除を行えます。
>\[注意点\]
配布状態が**アップロード中**、**配布中**またはCDN状態が**作業中**の場合はサービスを削除できません。
サービスを削除すると、ソースファイルと配布ファイルはすべて削除され、Smart Downloader CDN連携の場合はCDNの使用も停止する点に注意してください。


### 6. サービス修正
\[サービス詳細情報\]ページの右上にある修正ボタンを押すとサービス修正ページに移動できます。

> \[注意点\]
配布状態が**アップロード中**、**配布中**またはSmart Downloader CDN連携時にCDN状態が**作業中**の場合はサービスを修正できません。

![smartdl_16_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_16_201812.png)

#### 6.1サービス情報
サービス名は固定された値で、修正できません。サービス説明は修正できます。

#### 6.2 CDN情報
現在のCDN連携状態を下記の3つの場合に分けてCDN情報修正を案内します。

**6.2.1現在、Smart Downloader CDN連携の場合**
​	- Smart Downloader CDN -> 顧客社CDN連携に変更できます。
​   - 顧客社CDNサーバーアドレスは、HTTP/HTTPSプロトコルを選択して入力する必要があります。

**6.2.2現在、顧客社CDN連携の場合**
​	- 顧客社CDN  -> Smart Downloader CDN連携に変更できます。

**6.2.3現在、CDN未連携の場合**
​	- Smart Downloader CDN使用 / 顧客社CDN使用のどちらかを選択して、CDN連携できます。


## リアルタイムモニタリングTab
1日の間に、サービスをダウンロードしたユーザーの統計情報を00:00:00から現在まで10分周期で表示します。

### 1. リアルタイムダウンロード状況
#### 1-1ミニチャート
**照会条件**で選択した条件に該当する全体の統計情報を簡単なチャートで表示します。
各項目別の説明は次のとおりです。

![smartdl_21_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_21_201812.png)

| 番号 | 項目 | 説明 |
| --- | --- | --- |
| 1 | サービス選択 | - ダウンロード状況を確認するサービスを選択。 <br> - 選択したサービスを変える場合、ページ全体のチャートが変更。 |
| 2 | 国選択 | - 特定の国の統計情報を確認したい場合に選択。<br> - ダウンロード上位10か国のみ表示。 <br> - 国を変更する場合**リアルタイムダウンロード状況**のチャート情報のみ変更。 |
| 3 | チャートデータ収集時間 | - 最後にチャート情報が収集された時間。 |
| 4 | チャート名 | - どんな情報のチャートなのかを知らせるためのタイトル。 <br> - **種類** <br> -- Download Total ：ダウンロードが実行された総回数。 <br> -- Full Download Count ：アップロードされたビルドファイル全体をダウンロードした回数。<br> -- Download Success ：ダウンロードに成功した回数。<br> -- Average Download Time ：ダウンロード実行時の平均所要時間。 |
| 5 | ダウンロード回数 | Average Download Timeチャートでは全体平均ダウンロード時間を意味。 |
| 6 | 前日の同じ時間のダウンロード数と比較 | Average Download Timeチャートでは全体平均ダウンロード時間と比較。 |
| 7 | ダウンロードタイプ | ダウンロード回数のうち、Full & Update細分化|
| 8 | 成功率 | ダウンロード成功率 |


#### 1-2 OS別チャート
**照会条件**で選択した条件に該当する全体統計情報を簡略化したチャートで表示します。
各項目別の説明は次のとおりです。

![smartdl_22_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_22_201812.png)

| 番号 | 項目 | 説明 |
| --- | --- | --- |
| 1 | OS選択フィルタ | - All(デフォルト値) ：すべてのOSの統計情報を表示。<br> - iOS / Android / Windows ：選択したOSでダウンロードした統計情報のみ表示。 <br> - MacOS(オプション)：MacOSでダウンロードした記録がある場合のみ選択可能。 |
| 2 | Download Success / Fail | - Column Chart (累積)<br> - 10分単位で統計情報を表示。<br> - ダウンロード成功 / 失敗回数。 |
| 3 | Full / Update Download | - Column Chart (累積)<br> - 10分単位で統計情報を表示。<br> - アップロードされた全体ファイルのダウンロード回数 / 修正された一部のファイルのダウンロード回数。<br> - Unknownはアップデートリストのダウンロード中に失敗した場合。 |
| 4 | Average Download Time(sec) | - Column Chart.<br> - 10分単位で統計情報を表示。 <br> - 平均ダウンロード時間。 |


### 2. 国別ダウンロード状況
**照会条件**で選択した条件に該当する統計データを国別に区分して表で表示します。
各項目別の説明は次のとおりです。

![smartdl_23_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_23_201812.png)

| 番号 | 項目 | 説明 |
| --- | --- | --- |
| 1 | データ保存 | クリックすると、すべての国別ダウンロード表が**.csv**ファイルで保存される。 |
| 2 | 国別ダウンロード状況表 | - ダウンロード総回数が多い上位5か国のみ表で表示。<br> - MacOSの場合、ダウンロードした記録がある場合のみオプションで表示。 |


## モニタリング指標Tab
Smart Downloaderを有効にして、ダウンロードされた時点から現在までの使用統計情報を日別に確認できます。

### 1. 照会条件
ダウンロード指標を検索するための条件を選択するフィルタです。
各項目別の説明は次のとおりです。

![smartdl_24_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_24_201812.png)

| 番号 | 項目 | 説明 |
| --- | --- | --- |
| 1 | 照会期間 | - ダウンロード統計情報を検索する期間。<br>- 検索期間は、1日単位で選択。<br>- 検索期間は、最初にダウンロードをした日から検索当日まで可能。 |
| 2 | 照会条件 - サービス | - ダウンロード統計情報を検索するサービスを選択。 |
| 3 | 照会条件 - 国 | - ダウンロード統計情報を検索する国を選択。<br> - ダウンロード上位10か国のみ表示。 |
| 4 | 照会条件 - ダウンロードタイプ | - All Type ：条件に関係なくすべてのダウンロードタイプの統計を検索。<br> - Full Download ：アップロードされたビルドファイル全体をダウンロードした場合の統計のみ検索。<br> - Update Download ：アップロードされたビルドファイル中、修正されたファイルのみダウンロードした場合の統計のみ検索。<br> - Unknown ： Full / Update Downloadの有無を確認するためのメタファイルダウンロード中に問題が発生した場合の統計のみ検索。 |
| 5 | 検索 | - 選択した条件を元に統計情報を検索するためのボタン。 |


### 2. 日別ダウンロード状況
#### 2-1日別統計データ
**照会条件**で選択した条件に該当する日別統計データを表で表示します。
各項目別の説明は次のとおりです。

![smartdl_25_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_25_201812.png)

| 番号 | 項目 | 説明 |
| --- | --- | --- |
| 1 | データ保存 | - クリックすると、すべての国別のダウンロード表が**.csv**ファイルで保存される。 |
| 2 | 日別指標 | - 各OS別全体ダウンロード回数および各OS別ダウンロード成功 / 失敗 / 平均ダウンロード時間を日別に表示。<br> - MacOSのダウンロードした記録がある場合のみオプションで表示。<br> - 1ページに10日間の統計情報が表示される。 |
| 3 | ページ選択 | - 照会するページ選択。 |


#### 2-2日別の指標チャート
**照会条件**で選択した条件に該当する統計データをチャートで表示します。
チャートの種類は次のとおりです。

![smartdl_26_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_26_201812.png)

| 番号 | 項目 | 説明 |
| --- | --- | --- |
| 1 | Download Total | - Column Chart (累積)<br> - 1日単位で統計情報を表示。<br> - 各OS別の全体ダウンロード回数。|
| 2 | Download Success | - Column Chart (累積)<br> - 1日単位で統計情報を表示。<br> - 各OS別ダウンロード成功回数。 |
| 3 | Download Time(sec) | - Column Chart (比較)<br> - 1日単位で統計情報を表示。<br> - 各OS別の平均ダウンロード時間。 |
| 4 | Download Fail Type | - Pie Chart.<br> - 照会期間全体。<br> - ダウンロード失敗原因別の回数および比率。|


### 3. 日別ダウンロード状況
**照会条件**で選択した条件に該当する統計データを国別に区分して表で表示します。
各項目別の説明は次のとおりです。

![smartdl_27_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_27_201812.png)

| 番号 | 項目 | 説明 |
| --- | --- | --- |
| 1 | データ保存 | クリックすると、すべての国別ダウンロード表が**.csv**ファイルで保存される。|
| 2 | 国別ダウンロード状況表 | - ダウンロード総回数が多い上位5か国のみ表で表示。<br> - MacOSの場合、ダウンロードした記録がある場合のみオプションで表示。|
