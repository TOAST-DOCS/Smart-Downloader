## Game > Smart Downloader > SDK使用ガイド

## 開始する

Smart Downloader SDK를 사용하려면 콘솔에서 상품이 활성화되어 있어야 하며 등록된 서비스가 있어야 합니다.
자세한 내용은 [콘솔 사용 가이드](/Game/Smart%20Downloader/jp/console-guide)를 참고 바랍니다.

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


### SDK 

#### 1. 다운로드

[Download SDK](/Download/#game-smart-downloader)

#### 2. SDK 설치

1. 유니티 프로젝트를 엽니다.
2. 유니티에서 [Assets > Import Package > Custom Package]를 선택합니다.
3. 다운로드한 SDK 파일 'Smart-downloader-{Version}.unitypackage'을 선택한 후 임포트 합니다.
![smartdl_sdk_01.png](https://static.toastoven.net/prod_smartdownloader/sdk/smartdl_sdk_01.png)

#### 3. SDK 구조

* SDK는 'Assets/SmartDL' 폴더에 설치됩니다.
* 전부 임포트하면 Plugins와 Example로 나뉘어 있습니다.
    * Plugins : SDK 사용을 위한 DLL을 비롯한 플러그인을 포함하고 있습니다.
    * Example : SDK 동작을 확인할 수 있도록 샘플 씬과 스크립트를 포함하고 있습니다.

#### 4. SDK API 사용

* SDK에서 제공하는 API는 네임스페이스 'Toast.SmartDownloader'로 정의되어 있습니다.
* SDKで提供するAPIはSmartDlタイプの下に静的メソッドとして定義されています。


### ダウンロード開始

서비스를 선택해서 다운로드를 진행합니다.
기본적으로 업로드한 리소스 전체를 다운로드하지만 일부 리소스만 선택해서 다운로드할 수 있습니다.


#### DownloadConfig

ダウンロードに必要な設定を変更でき、指定されたパスやファイルのみダウンロードできます。
`DownloadConfig.Default`からデフォルト値の設定を取得できます。

| 変数名 | 初期値 | 説明 |
| --- | --- | --- |
| FixedDownloadThreadCount | -1 | ダウンロード時に使用するスレッドの数を固定<br>(0以下の値ならSDKで自動的に設定) |
| DownloadConnectTimeout | 60 | ダウンロードの接続タイムアウト (単位：秒) |
| DownloadReadTimeout | 20 | ダウンロードの読み取りタイムアウト (単位：秒) |
| RetryDownloadCountPerFile | 3 | ダウンロード失敗時に再試行する回数 |

**Example**

```cs
DownloadConfig config = DownloadConfig.Default;
config.DownloadConnectTimeout = TimeSpan.FromSeconds(60);
config.DownloadReadTimeout = TimeSpan.FromSeconds(20);
config.RetryDownloadCountPerFile = 3;
```

### 전체 리소스 다운로드

다운로드 설정에서 다운로드할 리소스를 선택하지 않았다면, 서비스에 배포된 모든 리소스를 다운로드 합니다.

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

### 선택한 리소스 다운로드

다운로드 설정에서 다운로드할 리소스를 선택하여, 해당 리소스만 다운로드할 수 있습니다.
파일을 찾지 못하면 오류가 반환됩니다. (Result Code : ERROR_EMPTY_FILE_LIST)

다운로드 API는 [전체 리소스 다운로드](/Game/Smart%20Downloader/jp/sdk-guide/#전체%20리소스%20다운로드)를 참고 바랍니다.

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
// 사용자가 지정한 파일을 다운로드 합니다.
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

### 다운로드 결과

ダウンロード結果コールバックに渡されるタイプです。

| 変数名 | 説明 |
| --- | --- |
| Code | 結果コード |
| IsCompleted | ダウンロード完了可否 |
| Message | 結果メッセージ |
| IsSuccessful | ダウンロード成功可否 |


## 다운로드 취소

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