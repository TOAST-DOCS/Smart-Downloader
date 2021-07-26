## Game > Smart Downloader > SDK使用ガイド

## 開始する

Smart Downloader SDKを使用するには、コンソールでサービスが有効になっていて、登録されたサービスが存在している必要があります。
詳細は、[コンソール使用ガイド](/Game/Smart%20Downloader/jp/console-guide)を参照してください。

### Environments

Smart Downloader SDKはUnityエンジンをサポートします。

#### Supported Versions

* 2018.4.0 ~ 2021.1.15

#### Supported Platforms

* iOS
* Android
* Standalone
    * Windows
    * macOS
* Editor


### SDK 

#### 1. ダウンロード

[Download SDK](/Download/#game-smart-downloader)

#### 2. SDKのインストール

1. Unityプロジェクトを開きます。
2. Unityで[Assets > Import Package > Custom Package]を選択します。
3. ダウンロードしたSDKファイル'Smart-downloader-{Version}.unitypackage'を選択し、インポートします。
![smartdl_sdk_01.png](https://static.toastoven.net/prod_smartdownloader/sdk/smartdl_sdk_01.png)

#### 3. SDKの構造

* SDKは`Assets/SmartDL`フォルダにインストールされます。
* すべてインポートすると、PluginsとExampleに分けられます。
    * Plugins：SDKを使用するためのDLLをはじめとするプラグインが含まれています。
    * Example：SDKの動作を確認できるようにサンプルシーン(scene)とスクリプトが含まれています。

#### 4. SDK APIの使用

* SDKで提供するAPIは、名前空間`Toast.SmartDownloader`に定義されています。
* SDKで提供するAPIはSmartDlタイプの下に静的メソッドとして定義されています。

### Androidネットワークセキュリティ構成

* CDNをHTTPとして使用し、Android 9.0以上でtarget API 28を使用する場合、HTTP許容設定が必要です。
* 詳細内容は [ネットワークセキュリティ構成](https://developer.android.com/training/articles/security-config?hl=ja)を参照してください。

#### 1. AndroidManifest.xml 設定

* AndroidManifest.xml 内の applicationで android:networkSecurityConfig 設定を追加します。

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest ... >
    <application android:networkSecurityConfig="@xml/network_security_config"
    ... >
        ...
    </application>
</manifest>
```

#### 2. network_security_config.xml 追加

* Plugins/Android/res/xml/network_security_config.xmlを追加します。

```xml
<?xml version="1.0" encoding="utf-8"?>
<network-security-config>
  <domain-config cleartextTrafficPermitted="true">
    <domain includeSubdomains="true">cdn.toastcloud.com</domain>
  </domain-config>
</network-security-config>
```

### iOS 네트워크 보안 구성

* CDN을 HTTP로 사용하는 경우 HTTP 허용 설정이 필요합니다.

#### Info.plist 설정

* Info.plist에서 App Transport Security Settings를 추가합니다.

```
<key>NSAppTransportSecurity</key>
<dict>
    <key>NSExceptionDomains</key>
    <dict>
        <key>toastcdn.net</key>
        <dict>
            <key>NSExceptionAllowsInsecureHTTPLoads</key>
            <true/>
            <key>NSIncludesSubdomains</key>
            <true/>
        </dict>
    </dict>
</dict>
```


### ダウンロード開始

サービスを選択し、ダウンロードします。
基本的にはアップロードしたリソース全体をダウンロードしますが、一部のリソースのみ選択してダウンロードすることもできます。


#### ダウンロード設定

ダウンロードに必要な設定を変更でき、指定されたパスやファイルのみダウンロードできます。
`DownloadConfig.Default`からデフォルト値の設定を取得できます。

| 変数名 | 初期値 | 説明 |
| --- | --- | --- |
| FixedDownloadThreadCount | -1 | ダウンロード時に使用するスレッドの数を固定<br>(0以下の値ならSDKで自動的に設定) |
| DownloadConnectTimeout | 60 | ダウンロードの接続タイムアウト (単位：秒) |
| DownloadReadTimeout | 20 | ダウンロードの読み取りタイムアウト (単位：秒) |
| RetryDownloadCountPerFile | 3 | ダウンロード失敗時に再試行する回数 |
| UseStreamingAssets | false | Streaming Assets 리소스와 비교 여부 지정 |
| PatchCompareFunction | PatchCompareType.INTERGRITY | リソースを検査するオプション |
| ClearUnusedResources | false | 사용하지 않는 리소스 제거<br>(현재 CDN에 없는 이전에 다운로드한 리소스 제거) |

**Example**

```cs
DownloadConfig config = DownloadConfig.Default;
config.DownloadConnectTimeout = TimeSpan.FromSeconds(60);
config.DownloadReadTimeout = TimeSpan.FromSeconds(20);
config.RetryDownloadCountPerFile = 3;
config.UseStreamingAssets = false;
config.PatchCompareFunction = PatchCompareType.INTERGRITY;
config.ClearUnusedResources = false;
```

### Use Streaming Assets

Streaming Assets 内部のリソースとアップロードされたリソースのパスを比較して、変更されたリソースをダウンロードします。

**注意**

* Smart Downloaderにアップロードされたデータは常に最新であることを保障しなければなりません。
* UnityプロジェクトのStreaming Assetsパスを基準にアップロードされたリソースパスを比較します。
* アップロードされたリソースがStreaming Assets内のファイルと異なるか、新規リソースがある場合は、ダウンロード時に指定したDown Pathに該当するファイルをダウンロードします。<br>ユーザはリソースを使用するときに指定したDownPathにファイルがあるか確認して、ファイルがある場合はDownPathパスのファイルを、ない場合はStreamingAssetsパスのファイルを使用してください。
* Streaming Assetsがアップデートされ Down Pathのファイルと同じなら Down Pathのファイルは削除されます。
* Androidの場合 `Split Application Binary` 設定が有効になると、APK拡張ファイルであるOBBファイルにStreaming Assetsが含まれますが、このとき自動的にデバイスでOBBファイルを検索します。
     デバイスにOBBファイルがない場合は、アップロードされたすべてのリソースをダウンロードします。(参考 : [Unity Manual - APK 拡張ファイル対応](https://docs.unity3d.com/jp/current/Manual/android-OBBsupport.html))
* PatchCompareFunction 옵션은 PatchCompareType.INTERGRITY 값으로 고정됩니다.


### Check Downloadによる検査オプション

#### PatchCompareType.INTERGRITY

デフォルト設定で、リソースチェック時にダウンロードされたすべてのリソースのCRCを計算し、アップロードされたリソースと比較します。

**特徴**

* リソース完全性保障
    * リソースの漏れおよび改変を感知して、アップロードされたリソースをダウンロードします。

#### PatchCompareType.SAVED_INFORMATION

このオプションを使用すると、ダウンロードされたリソースの基本情報をデバイスに保存して、次のスキャン時にアップロードされたリソースと比較します。

**特徴**

* スピードの速いリソーススキャンが行えます。

**短所**

* リソースの漏れや改造を感知できません。
    * 解決策としてリソースロード時に正常なデータでなければ、オプションをINTERGRITYに変更し、再ダウンロードを行い復旧することができます。

#### PatchCompareType.SAVED_INFORMATION_AND_SIMPLE_FILE_SCAN

このオプションを使用すると、ダウンロードされたリソースの基本情報をデバイスに保存して、次のスキャン時にアップロードされたリソースと比較し、デバイスに実際にリソースが存在するのか簡単なスキャンを行います。

**特徴**

* PatchCompareType.INTERGRITYに比べて、処理スピードが速く、<br>PatchCompareType.SAVED_INFORMATIONオプションより少し遅いですが、検査時にリソースの存在有無とアップロードリソース、ダウンロードされたリソースの大きさを測定し、リソース漏れ防止および簡単なスキャンを行います。

**短所**

* リソースの改造を検知できません。
    * 解決策としてリソースロード時に正常なデータでなければ、オプションをINTERGRITYに変更して再ダウンロードを行い復旧することができます。


### 全リソースのダウンロード

ダウンロード設定で、ダウンロードするリソースを選択しなかった場合、サービスに配布されたすべてのリソースをダウンロードします。

**API**

```cs
static void StartDownload(string appkey, string serviceName, string downPath, OnComplete callback)
static void StartDownload(string appkey, string serviceName, string downPath, DownloadConfig config, OnComplete callback)

delegate void OnComplete(DownloadResult result)
```

* appkey
    *発行されたAppkeyを入力します。サービス有効時に発行され、Consoleで確認できます。
* serviceName
    *ダウンロードを進行するサービス名を入力します。サービス名はConsoleで確認できます。
* downPath
    *ダウンロードするをパスを入力します。別途推奨するパスはありません。
    *プラットフォームで別途にディレクトリを指定したい場合、Unity APIであるApplication.persistentDataPath、Application.temporaryCachePathをご確認ください。
* config (選択)
    *ダウンロード環境設定を変更できます。デフォルト値を使用することを推奨します。
* callback
    *ダウンロードが完了(成功または失敗)すると、処理するコードを作成します。コールバック関数が呼び出されるとDownloadResultタイプの結果値がパラメータに渡されます。

**Example**

```cs
SmartDl.StartDownload("Appkey", "ServiceName", "DownloadPath",
    (result) =>
    {
        if (result.IsSuccessful)
        {
            // 成功コードの作成
        }
        else
        {
            // 失敗コードの作成
        }
    });
```

### 選択したリソースのダウンロード

[ダウンロード設定]でダウンロードするリソースを選択し、該当リソースのみをダウンロードできます。
ファイルが見つからなかった場合、エラーを返します(結果コード：ERROR_EMPTY_FILE_LIST)。

ダウンロードAPIは、[全リソースダウンロード](/Game/Smart%20Downloader/jp/sdk-guide/#_4)を参照してください。

**API**

```cs
class DownloadConfig
{
    void AddSpecifyPath(string path);
    void RemoveSpecifyPath(string path);
    void ClearSpecifyPath();
}
```

**Example**

```cs
// ユーザーが指定したファイルをダウンロードします。
// - Charactersパスの下にあるすべてのファイル
// - Maps/M01パスの下にあるすべてのファイル
// - Data/CharacterInfo.txtファイル
var downloadConfig = DownloadConfig.Default;
downloadConfig.AddSpecifyPath(@"/Characters");
downloadConfig.AddSpecifyPath(@"/Maps/M01");
downloadConfig.AddSpecifyPath(@"/Data/CharacterInfo.txt");

SmartDl.StartDownload(Appkey, ServiceName, DownloadPath, downloadConfig, 
    (result) =>
    {
        if (result.IsSuccessful)
        {
            // 成功コードの作成
        }
        else
        {
            // 失敗コードの作成
        }
    });
```

### ダウンロード結果

ダウンロード結果コールバックに渡されるタイプです。

| 変数名 | 説明 |
| --- | --- |
| Code | 結果コード |
| IsCompleted | ダウンロード完了可否 |
| Message | 結果メッセージ |
| IsSuccessful | ダウンロード成功可否 |


## ダウンロードをキャンセル

進行中のダウンロードをキャンセルします。
StartDownloadコールバックが失敗を返します。(Result Code : USER_CANCEL)

**API**

```cs
static void StopDownload()
```

**Example**

```cs
void StopDownload()
{
    SmartDl.StopDownload();
}
```


## ダウンロード進行情報の取得

進行中のダウンロード情報はProgressInfoタイプで取得できます。

| 変数名 | 説明 |
| --- | --- |
| FileMap | 現在のスレッド別ダウンロード中のファイル情報を返す |
| Percentage | 全体進行率を返す |
| Speed | ダウンロード開始から今までのダウンロード速度を返す(単位：バイト/秒)<br>(全体ダウンロード容量 / ダウンロード開始時間から現在時間) |
| TotalReceivedBytes | 現在までダウンロードしたバイト数を返す |
| TotalFileBytes | ダウンロードする必要がある全体のバイト数を返す |
| CompletedFileCount | 現在までダウンロードそたファイル数を返す |
| TotalFileNumber | ダウンロードする必要がある全体のファイル数を返す |
| IsCompleted | ダウンロードが完了したかどうかを返す |

**API**

```cs
static ProgressInfo Progress;
```

**Example**

```cs
void StartDownload()
{
    SmartDl.StartDownload(AppKey、ServiceName、DownloadPath、downloadConfig、OnCompleteCallback);
    StartCoroutine(UpdateProgress());
}

IEnumerator UpdateProgress()
{
    while (true)
    {
        var progress = SmartDl.Progress;

        Debug.LogFormat("Percentage : {0} %"、progress.Percentage);

        var threadCount = progress.FileMap.Count;
        ThreadProgressContainer.Instance.ThreadCount = threadCount;
        for (int i = 0; i < threadCount; i++)
        {
            var file = progress.FileMap[i];
            Debug.LogFormat("Thread[{0}] Percentage : {1} %"、i、(file.DownloadedBytes / (float)file.TotalBytes) * 100.0f);
        }

        if (progress.IsCompleted)
            yield break;

        yield return null;
    }
}
```



## ログレベルの設定

SDK内部動作のログを出力するためにSmartDlLoggerタイプを提供します。
ログレベルのデフォルト値はErrorで、ログイベントを登録しなければ何も動作をしません。

**API**

```cs
static LogLevel CurrentLevel = LogLevel.Error;
static event Action<LogLevel、string> OnLog;
```

**Example**

```cs
void Initialize()
{
    SmartDlLogger.CurrentLevel = SmartDlLogger.LogLevel.Trace;
    SmartDlLogger.OnLog += (type、log) =>
    {
        switch (type)
        {
            case SmartDlLogger.LogLevel.Trace:
            case SmartDlLogger.LogLevel.Developer:
            case SmartDlLogger.LogLevel.Debug:
            case SmartDlLogger.LogLevel.Info:
                Debug.Log(log);
                break;
            case SmartDlLogger.LogLevel.Warn:
                Debug.LogWarning(log);
                break;
            case SmartDlLogger.LogLevel.Error:
                Debug.LogError(log);
                break;
            default:
                Debug.Log(log);
                break;
        }
    };
}
```

## API Deprecate Governance

Smart Downloader SDK에서 더 이상 지원하지 않는 API는 Deprecate 처리합니다.
Deprecated된 API는 다음 조건 충족 시 사전 공지 없이 삭제될 수 있습니다.

* 5회 이상의 마이너 버전 업데이트
    * Smart Downloader Version Format - XX.YY.ZZ
        * XX : Major
        * YY : Minor
        * ZZ : Hotfix

* 최소 5개월 경과