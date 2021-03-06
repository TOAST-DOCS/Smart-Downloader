## Game > Smart Downloader > 概要

Smart Downloaderは、ゲーム起動時にゲームに必要なリソースをマルチスレッドでダウンロードするサービスです。
クライアントでリソースをダウンロードして、さまざまな統計データを収集して多様な情報を提供します。


## 主な機能


### マルチスレッドダウンロード
- ネットワーク帯域幅を最大限活用してダウンロードできます。
- ファイルの個数が多く、ネットワーク環境が遅い環境(グローバル環境)で役立ちます。


### 更新されたファイルリストのみアップデート
- ファイルのサイズ、チェックサムに基づいてアップデートを行います。
	- 画像やテキストファイルのように、サイズは変わらず内容が変わったファイルについても(ファイルのチェックサムは変わるため)アップデートが可能です。
- 最初のフルダウンロード以降は増分のみアップデートを行います。


### 簡単なアップロードおよびアップロード/配布ファイルの作成を自動化
- コンソール / Jenkins Pluginを通して、簡単にゲームリソースアップロードが可能です。
	- Jenkins Pluginを通して、アップロードを自動化できます。
- ゲームリソースをアップロードすると、自動で配布ファイルをアップデートします。


### ダウンロードおよびアップデート実装の簡素化
- 提供されるSDKを通して簡単にダウンロード機能を実装でき、ダウンロード進行情報を詳細に確認できます。


### ゲームダウンロード統計データ提供

- 24時間以内のリアルタイムダウンロード状況と日別モニタリング指標を提供します。
- ダウンロード成功 / 失敗統計を確認できます。
- 国別 / 機器別 / OS別ダウンロード統計を確認できます。
- 検索機能を提供し、希望する時間帯(ゲーム配布前後)のダウンロード統計を確認できます。


## 用語

| 用語 | 説明 |
| --- | --- |
| サービス |	 Smart Downloaderの個別単位。|
| ビルド | Smart Downloader SDKを通してダウンロードしたゲームのリソース。サービス別に管理する。 |
| 配布ファイル | Smart Downloaderにアップロードされたビルドは自動的に配布ファイルを作成する。サービス別に管理する。 |
| 内部CDN | Smart Downloader内で自動的に作成するCDN。 |
| 外部CDN | 内部CDNではなく、既に使用中のCDNが存在する場合。 |


## 構造

![図1](http://static.toastoven.net/prod_smartdownloader/overview/smartdl_overview_structure_en.png)
<center>[図1] Smart Downloader構造 </center>

<br>

| Component名 | 説明 |
| --- | --- |
| SDK | Game ClientでSmartDownloaderを使用するためのClient SDK。 |
| API Server | NHN Cloud認証を処理し、CDN Download URLをClient SDKに伝達する。 |
| Console |	 Smart Downloaderサービス登録、ビルドアップロード、モニタリング機能を提供。 |
| Jenkins Plugin | コンソールを通さずに、ユーザーのビルドサーバーから直接ビルドアップロード機能を使用できるように提供。 |
