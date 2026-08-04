<!-- pre-align:aligned sig=5855a25dd24f -->

<a id="game-smart-downloader-release-notes-unity-sdk"></a>
## Game > Smart Downloader > Release Notes > Unity SDK { #game-smart-downloader-release-notes-unity-sdk }

<a id="70-20210914-download-sdk"></a>
### 1.7.0 (2021.09.14) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.7.0.unitypackage) { #70-20210914-download-sdk }

<a id="70-20210914-download-sdk-bug-fixes"></a>
#### Bug Fixes
* Fixed a DLL error

<a id="69-20210727-download-sdk"></a>
### 1.6.9 (2021.07.27) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.9.unitypackage) { #69-20210727-download-sdk }

<a id="69-20210727-download-sdk-feature-updates"></a>
#### Feature Updates
* Changed the minimum supported version of Unity to 2018.4.0
* Removed warnings that occur on Unity 2020.2 or later


<a id="68-20210413-download-sdk"></a>
### 1.6.8 (2021.04.13) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.8.unitypackage) { #68-20210413-download-sdk }

<a id="68-20210413-download-sdk-feature-updates"></a>
#### Feature Updates
* Added the option to remove the excluded resource
    * Added API
        * DownloadConfig.ClearUnusedResources
* Improved DownloadConfig API 
    * Changed API
        * DownloadConfig.CheckOption (Obsolete) → DownloadConfig.UseStreamingAssets, DownloadConfig.PatchCompareFunction 사용
* Improved log to check the failure rate information


<a id="67-20200811-download-sdk"></a>
### 1.6.7 (2020.08.11) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.7.unitypackage) { #67-20200811-download-sdk }

<a id="67-20200811-download-sdk-feature-updates"></a>
#### Feature Updates
* Improved resource check logic
* Added a resource check option
    * Added API
        * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA_AND_LOCAL_SCAN
* Exclude decompression feature
    * Changed API
        * ResultCode.ERROR_UNZIP (Obsolete)


<a id="66-20200714-download-sdk"></a>
### 1.6.6 (2020.07.14) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.6.unitypackage) { #66-20200714-download-sdk }

<a id="66-20200714-download-sdk-feature-updates"></a>
#### Feature Updates
* Improved the way to check available disk space


<a id="65-20200623-download-sdk"></a>
### 1.6.5 (2020.06.23) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.5.unitypackage) { #65-20200623-download-sdk }

<a id="65-20200623-download-sdk-bug-fixes"></a>
#### Bug Fixes
* Fixed an error where OverflowException occurs depending on the execution environment


<a id="64-20200512-download-sdk"></a>
### 1.6.4 (2020.05.12) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.4.unitypackage) { #64-20200512-download-sdk }

<a id="64-20200512-download-sdk-feature-updates"></a>
#### Feature Updates
* Added a resource check option
    * Changed API
        * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA 추가

<a id="63-20200428-download-sdk"></a>
### 1.6.3 (2020.04.28) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.3.unitypackage) { #63-20200428-download-sdk }

<a id="63-20200428-download-sdk-feature-updates"></a>
#### Feature Updates
* Changed to support Streaming Assets
    * Added a feature to compare and download the Streaming Assets resources and the uploaded resources
    * Changed API
        * DownloadResult.CheckAndroidObb (Obsolete) → DownloadResult.CheckOption


<a id="62-20200310-download-sdk"></a>
### 1.6.2 (2020.03.10) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.2.unitypackage) { #62-20200310-download-sdk }

<a id="62-20200310-download-sdk-feature-updates"></a>
#### Feature Updates
* Supports Android - Split Application Binary(OBB) 
    * Can download by comparing streaming asset resources included to OBB with uploaded resources.
    * Added API 
        * DownloadConfig.CheckAndroidObb

<a id="61-20200121-download-sdk"></a>
### 1.6.1 (2020.01.21) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.1.unitypackage) { #61-20200121-download-sdk }

<a id="61-20200121-download-sdk-bug-fixes"></a>
#### Bug Fixes
* Fixed exceptions that occur when there's no downloaded file to inspect. 


<a id="60-20191224-download-sdk"></a>
### 1.6.0 (2019.12.24) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.0.unitypackage) { #60-20191224-download-sdk }

<a id="60-20191224-download-sdk-feature-updates"></a>
#### Feature Updates
* Added API to check download capacity (CheckDownload)
* Change APIs 
    * DownloadResult.IsSuccessful (Obsolete) → DownloadResult.Code
    * ProgressInfo.TotalFileNumber (Obsolete) → ProgressInfo.TotalFileCount
    * ProgressInfo.TotalReceivedBytes (Obsolete) → ProgressInfo.DownloadedBytes


<a id="59-20191029-download-sdk"></a>
### 1.5.9 (2019.10.29) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.9.unitypackage) { #59-20191029-download-sdk }

<a id="59-20191029-download-sdk-feature-updates"></a>
#### Feature Updates
* Improved statistics indicators.

<a id="58-20190729-download-sdk"></a>
### 1.5.8 (2019.07.29) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.8.unitypackage) { #58-20190729-download-sdk }

<a id="58-20190729-download-sdk-bug-fixes"></a>
#### Bug Fixes
* Fixed the occurrence of crash while completing with downloads on particular Android devices.


<a id="57-20190625-download-sdk"></a>
### 1.5.7 (2019.06.25) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.7.unitypackage) { #57-20190625-download-sdk }

<a id="57-20190625-download-sdk-feature-updates"></a>
#### Feature Updates
* Added the About menu.
* Deliver success (SUCCESS_NO_DIFFERENCE) as the result code when there is no resources to download for downloading the entire resources. 
* Changed the folder structure
    * Assets/SmartDL/ → Assets/TOAST/SmartDL
    * `The existing SmrtDL folder must be deleted before imported. `

<a id="56-20181227-download-sdk"></a>
### 1.5.6 (2018.12.27) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.6.unitypackage) { #56-20181227-download-sdk }

<a id="56-20181227-download-sdk-bug-fixes"></a>
#### Bug Fixes
* Fixed the issue in which result callback is not called when downloading is canceled.

<a id="56-20181227-download-sdk-feature-updates"></a>
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


<a id="55-20181127-download-sdk"></a>
### 1.5.5 (2018.11.27) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.5.unitypackage) { #55-20181127-download-sdk }

<a id="55-20181127-download-sdk-bug-fixes"></a>
#### Bug Fixes
* Supports IL2CPP builds. 
* Modified infrequent failure in acquiring IP addresses on mac OS. 


<a id="54-20181023-download-sdk"></a>
### 1.5.4 (2018.10.23) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.4.unitypackage) { #54-20181023-download-sdk }

<a id="54-20181023-download-sdk-feature-updates"></a>
#### Feature Updates
* Supports Unity 2018.2. 
* Enables downloading by selecting paths and files. 
* Improved calculation for download file sizes.
* Added namespaces for example codes. 

<a id="54-20181023-download-sdk-bug-fixes"></a>
#### Bug Fixes
* Fixed the unavailability of downloading on iOS when Korean is included to a file name. 
* Fixed the unavailability of downloading when a file name or a directory name includes specific special characters.



<a id="53-20180605-download-sdk"></a>
### 1.5.3 (2018.06.05) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.3.unitypackage) { #53-20180605-download-sdk }

<a id="53-20180605-download-sdk-feature-updates"></a>
#### Feature Updates
* Added the retry logic 
* Separated connection timeout from read timeout.


<a id="51-20180418-download-sdk"></a>
### 1.5.1 (2018.04.18) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.1.unitypackage) { #51-20180418-download-sdk }

<a id="51-20180418-download-sdk-bug-fixes"></a>
#### Bug Fixes
* Fixed link error out of the setting for Unity optimization.


<a id="50-20180222-download-sdk"></a>
### 1.5.0 (2018.02.22) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.0.unitypackage) { #50-20180222-download-sdk }

<a id="50-20180222-download-sdk-feature-updates"></a>
#### Feature Updates
* Added **Service** an individual unit under Smart Downloader. 
* Removed dependency on the core library.
* Change API 
    * Changed Improve Usability API.


<a id="20-20171026-download-sdk"></a>
### 1.2.0 (2017.10.26) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.2.0.unitypackage) { #20-20171026-download-sdk }

<a id="20-20171026-download-sdk-feature-updates"></a>
#### Feature Updates
* Enhanced stability 
    * Removed dependency on internal SDKs. 
    * Decreased dependency on the native library.

<a id="10-20170223-download-sdk"></a>
### 1.1.0 (2017.02.23) [Download SDK](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/SmartDownloaderSDK_v1.1.0.unitypackage) { #10-20170223-download-sdk }

<a id="10-20170223-download-sdk-feature-updates"></a>
#### Feature Updates
* Changed the class name (DLCSkin -> SmartDLUnitySkin).
* Provides Only Static API 

