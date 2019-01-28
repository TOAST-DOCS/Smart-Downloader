## Game > Smart Downloader > SDK使用ガイド

### Environments

Smart Downloader SDKはUnityエンジンをサポートします。

#### Supported Versions

* 5.6.6 ~ 2018.3.1

#### Supported Platforms

* iOS
* Android
* Standalone
    * Windows
    * macOS
* Editor


## API Guide

SDKで提供するAPIはSmartDlタイプの下に静的メソッドとして定義されています。
提供されるAPIは、名前空間Toast.SmartDownloaderに定義されているため、using宣言を行うことを推奨します。


### 開始する

Smart Downloader SDKを使用するには、Consoleでサービスが有効になっている必要があり、登録されたサービスが必要です。

[Console Guide](/Game/Smart%20Downloader/ko/console-guide)


### ダウンロード開始

登録されたサービスを基準にダウンロードを実行します。

**API**

```cs
static void StartDownload(string appKey、string serviceName、string downPath、OnComplete callback)
static void StartDownload(string appKey、string serviceName、string downPath、DownloadConfig config、OnComplete callback)

delegate void OnComplete(DownloadResult result)
```

* appKey
    *発行されたAppKeyを入力します。サービス有効時に発行され、Consoleで確認できます。
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
SmartDl.StartDownload("AppKey"、"ServiceName"、"DownloadPath"、DownloadConfig.Default、result =>
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

#### DownloadResult

ダウンロード結果コールバックに渡されるタイプです。

| 変数名 | 説明 |
| --- | --- |
| Code | 結果コード |
| IsCompleted | ダウンロード完了可否 |
| Message | 結果メッセージ |
| IsSuccessful | ダウンロード成功可否 |


#### DownloadConfig

ダウンロードに必要な設定を変更でき、指定されたパスやファイルのみダウンロードできます。
`DownloadConfig.Default`からデフォルト値の設定を取得できます。

| 変数名 | 初期値 | 説明 |
| --- | --- | --- |
| FixedDownloadThreadCount | -1 | ダウンロード時に使用するスレッドの数を固定<br>(0以下の値ならSDKで自動的に設定) |
| DownloadConnectTimeout | 60 | ダウンロードの接続タイムアウト |
| DownloadReadTimeout | 20 | ダウンロードの読み取りタイムアウト |
| RetryDownloadCountPerFile | 3 | ダウンロード失敗時に再試行する回数 |

**Example**

```cs
DownloadConfig config = DownloadConfig.Default;
config.DownloadConnectTimeout = TimeSpan.FromSeconds(60);
config.DownloadReadTimeout = TimeSpan.FromSeconds(20);
config.RetryDownloadCountPerFile = 3;
```

##### パスやファイルを指定してダウンロード

**API**

```cs
void AddSpecifyPath(string path);
void RemoveSpecifyPath(string path);
void ClearSpecifyPath();
```

**Example**

```cs
// Charactersパスの下にあるすべてのファイル、Maps/M01パスの下にあるすべてのファイル、Data/CharacterInfo.txtファイルをダウンロードする。
var downloadConfig = DownloadConfig.Default;
downloadConfig.AddSpecifyPath(@"/Characters");
downloadConfig.AddSpecifyPath(@"/Maps/M01");
downloadConfig.AddSpecifyPath(@"/Data/CharacterInfo.txt");

SmartDl.StartDownload(AppKey、ServiceName、DownloadPath、downloadConfig、OnCompleteCallback);
```


### ダウンロード停止

進行中のダウンロードをキャンセルします。
StartDownloadコールバックが失敗(ResultCode : Cancel)を返します。

**API**

```cs
static void StopDownload()
```

**Example**

```cs
void StopDownload
{
    SmartDl.StopDownload();
}
```


### ダウンロード進行情報の取得

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



### ログレベルの設定

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
