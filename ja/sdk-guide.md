## Game > Smart Downloader > SDK使用ガイド

## 開始する

Smart Downloader SDKを使用するには、コンソールでサービスが有効になっていて、登録されたサービスが存在している必要があります。
詳細は、[コンソール使用ガイド](/Game/Smart%20Downloader/jp/console-guide)を参照してください。

### Environments

Smart Downloader SDKはUnityエンジンをサポートします。

#### Supported Versions

* 2017.4.16 ~ 2019.3.10

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
| CheckOption | PatchCheckOption.NONE | 리소스 검사 옵션 |

**Example**

```cs
DownloadConfig config = DownloadConfig.Default;
config.DownloadConnectTimeout = TimeSpan.FromSeconds(60);
config.DownloadReadTimeout = TimeSpan.FromSeconds(20);
config.RetryDownloadCountPerFile = 3;
config.CheckOption = PatchCheckOption.NONE;
```

### Check Download 검사 옵션

#### PatchCheckOption.DEFAULT

기본 옵션으로 리소스 검사 시 다운로드된 리소스를 CRC를 계산하여 업로드된 리소스와 비교합니다.

**특징**
* 리소스 무결성 보장
    * 리소스 누락 및 변조를 감지하여 업로드된 리소스를 다운로드 합니다.

#### PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA

해당 옵션을 사용하면 다운로드된 리소스의 기본 정보를 디바이스에 저장하여 다음 검사 시 업로드된 리소스와 비교합니다.

**특징**
* 리소스 검사 속도가 빠르다.

**취약점**
* 리소스 누락 및 변조를 감지할 수 없습니다.
    * 해결책으로 리소스 로드 시 정상적인 데이터가 아니라면 옵션을 DEFAULT로 변경하여 재다운로드를 진행하여 복구할 수 있습니다.

```cs
DownloadConfig config = DownloadConfig.Default;
config.CheckOption |= PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA;
```

#### PatchCheckOption.COMPARE_WITH_STREAMING_ASSETS

Streaming Assets 내부의 리소스와 업로드된 리소스의 경로를 비교하여 변경된 리소스를 다운로드 받습니다.

**주의**
* Smart Downloader에 업로드 된 데이터는 항상 최신임을 보장해야 합니다.
* 유니티 프로젝트의 Streaming Assets 경로를 기준으로 업로드 된 리소스 경로를 비교합니다.
* 업로드된 리소스가 Streaming Assets 내의 파일과 다르거나 신규 리소스가 있다면, 다운로드 시 지정한 DownPath에 해당되는 파일을 다운로드 받습니다.<br>사용자는 리소스를 사용할 때 지정한 DownPath에 파일이 있는지 확인하여 파일이 있으면 DownPath 경로의 파일을, 없으면 Streaming Assets 경로의 파일을 사용하면 됩니다.
* Streaming Assets가 업데이트 되어 DownPath에 파일과 동일하다면 DownPath의 파일은 제거됩니다.
* Android의 경우 `Split Application Binary` 설정이 활성화 되면 APK 확장 파일인 OBB 파일에 Streaming Assets이 포함되는데, 이 때 자동으로 디바이스에 OBB 파일을 검색하게 됩니다.
    디바이스에 OBB 파일이 없다면 업로드된 모든 리소스를 다운로드 받습니다. (참고 : [Unity Manual - APK 확장 파일 지원](https://docs.unity3d.com/kr/current/Manual/android-OBBsupport.html))
* PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA 옵션과 중복 적용은 불가능 합니다.

**Example**

```cs
DownloadConfig config = DownloadConfig.Default;
config.CheckOption |= PatchCheckOption.COMPARE_WITH_STREAMING_ASSETS;
```

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