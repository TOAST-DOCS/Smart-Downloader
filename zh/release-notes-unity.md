## Game > Smart Downloader > Release Notes > Unity SDK

### 1.6.9 (2021.07.27) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.9.unitypackage)

#### Feature Updates
* Unity 최소 지원 버전을 2018.4.0으로 변경
* Unity 2020.2 이후 버전에서 발생하는 Warning 제거


### 1.6.8 (2021.04.13) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.8.unitypackage)

#### Feature Updates
* 제외된 리소스 제거 옵션 추가
    * API 추가
        * DownloadConfig.ClearUnusedResources
* DownloadConfig API 개선
    * API 변경
        * DownloadConfig.CheckOption (Obsolete) → DownloadConfig.UseStreamingAssets, DownloadConfig.PatchCompareFunction 사용
* 실패율 정보를 확인을 위한 로그 개선


### 1.6.7 (2020.08.11) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.7.unitypackage)

#### Feature Updates
* 리소스 검사 로직 개선
* 리소스 검사 옵션 추가
    * API 추가
        * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA_AND_LOCAL_SCAN
* 압축 해제 기능 제외
    * API 변경
        * ResultCode.ERROR_UNZIP (Obsolete)


### 1.6.6 (2020.07.14) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.6.unitypackage)

#### Feature Updates
* 디스크 여유 공간 확인 방법 개선


### 1.6.5 (2020.06.23) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.5.unitypackage)

#### Bug Fixes
* 실행환경에 따라 OverflowException이 발생하는 오류 수정


### 1.6.4 (2020.05.12) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.4.unitypackage)

#### Feature Updates
* 리소스 검사 옵션 추가
    * API 변경
        * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA 추가

### 1.6.3 (2020.04.28) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.3.unitypackage)

#### Feature Updates
* Streaming Assets 지원
    * Streaming Assets 리소스와 업로드 된 리소스를 비교 다운로드 기능 추가
    * API 변경
        * DownloadResult.CheckAndroidObb (Obsolete) → DownloadResult.CheckOption


### 1.6.2 (2020.03.10) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.2.unitypackage)

#### Feature Updates
* Supports Android - Split Application Binary(OBB) 
    * Can download by comparing streaming asset resources included to OBB with uploaded resources.
    * Added API 
        * DownloadConfig.CheckAndroidObb

### 1.6.1 (2020.01.21) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.1.unitypackage)

#### Bug Fixes
* Fixed exceptions that occur when there's no downloaded file to inspect. 


### 1.6.0 (2019.12.24) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.0.unitypackage)

#### Feature Updates
* Added API to check download capacity (CheckDownload)
* Change APIs 
    * DownloadResult.IsSuccessful (Obsolete) → DownloadResult.Code
    * ProgressInfo.TotalFileNumber (Obsolete) → ProgressInfo.TotalFileCount
    * ProgressInfo.TotalReceivedBytes (Obsolete) → ProgressInfo.DownloadedBytes


### 1.5.9 (2019.10.29) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.9.unitypackage)

#### Feature Updates
* Improved statistics indicators.

### 1.5.8 (2019.07.29) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.8.unitypackage)

#### Bug Fixes
* Fixed the occurrence of crash while completing with downloads on particular Android devices.


### 1.5.7 (2019.06.25) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.7.unitypackage)

#### Feature Updates
* Added the About menu.
* Deliver success (SUCCESS_NO_DIFFERENCE) as the result code when there is no resources to download for downloading the entire resources. 
* Changed the folder structure
    * Assets/SmartDL/ → Assets/TOAST/SmartDL
    * `The existing SmrtDL folder must be deleted before imported. `

### 1.5.6 (2018.12.27) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.6.unitypackage)

#### Bug Fixes
* Fixed the issue in which result callback is not called when downloading is canceled.

#### Feature Updates
* Common
    * [ResultCode Renewal](/Game/Smart%20Downloader/ko/error-code)
        * [Caution] Error occurs when updated from existing SDK
* iOS
    * Supports iOS 12 
* Standalone(Windows)
    * Changed name and path of DLL 
        * smartnative_x86.dll → x86/smartnative.dll
        * smartnative_x64.dll → x86_64/smartnative.dll


### 1.5.5 (2018.11.27) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.5.unitypackage)

#### Bug Fixes
* Supports IL2CPP builds. 
* Modified infrequent failure in acquiring IP addresses on mac OS. 


### 1.5.4 (2018.10.23) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.4.unitypackage)

#### Feature Updates
* Supports Unity 2018.2. 
* Enables downloading by selecting paths and files. 
* Improved calculation for download file sizes.
* Added namespaces for example codes. 

#### Bug Fixes
* Fixed the unavailability of downloading on iOS when Korean is included to a file name. 
* Fixed the unavailability of downloading when a file name or a directory name includes specific special characters.



### 1.5.3 (2018.06.05) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.3.unitypackage)

#### Feature Updates
* Added the retry logic 
* Separated connection timeout from read timeout.


### 1.5.1 (2018.04.18) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.1.unitypackage)

#### Bug Fixes
* Fixed link error out of the setting for Unity optimization.


### 1.5.0 (2018.02.22) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.0.unitypackage)

#### Feature Updates
* Added **Service** an individual unit under Smart Downloader. 
* Removed dependency on the core library.
* Change API 
    * Changed Improve Usability API.


### 1.2.0 (2017.10.26) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.2.0.unitypackage)

#### Feature Updates
* Enhanced stability 
    * Removed dependency on internal SDKs. 
    * Decreased dependency on the native library.

### 1.1.0 (2017.02.23) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/SmartDownloaderSDK_v1.1.0.unitypackage)

#### Feature Updates
* Changed the class name (DLCSkin -> SmartDLUnitySkin).
* Provides Only Static API 

