## Game > Smart Downloader > Release Notes

### 2021. 04. 13.
#### 기능 개선/변경

* [Unity SDK] v1.6.8
    * 제외된 리소스 제거 옵션 추가
        * API 추가
            * DownloadConfig.ClearUnusedResources
    * DownloadConfig API 개선
        * API 변경
            * DownloadConfig.CheckOption (Obsolete) → DownloadConfig.UseStreamingAssets, DownloadConfig.PatchCompareFunction 사용
    * 실패율 정보를 확인을 위한 로그 개선

### 2020. 11. 24.
#### 기능 개선/변경
```
Unity Tool v1.0.2 이하 버전을 사용하시는 경우 업데이트가 필요합니다.
이전 버전의 Unity Tool은 사용하실 수 없습니다.
```
* [Unity Tool] v1.0.3
    * 예약 배포 기능 추가
    * Unity 2019.3 에디터 UI 대응
* [Console] 일괄, 예약 배포 기능 추가.
    * Smart Downloader CDN을 사용하는 서비스는 목록 페이지에 일괄, 예약 배포를 진행할 수 있도록 기능 추가.
    * Smart Downloader CDN을 사용하는 서비스는 개별 배포시에도 예약 배포를 진행할 수 있도록 기능 추가.
* [Console] 서비스 생성 마법사의 파일 업로드 화면에서 파일 업로드 없이 서비스 생성이 가능하도록 수정.


### 2020. 08. 11.
#### 기능 개선/변경
* [Unity SDK] v1.6.7
    * 리소스 검사 로직 개선
    * 리소스 검사 옵션 추가
        * API 추가
            * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA_AND_LOCAL_SCAN
    * 압축 해제 기능 제외
        * API 변경
            * ResultCode.ERROR_UNZIP (Obsolete)

### 2020. 07. 14.
#### 기능 개선/변경
* [Unity SDK] v1.6.6
    * 디스크 여유 공간 확인 방법 개선
* [Console] 빌드배포 기능 수정.
    * 빌드배포시 5분간 같은 프로젝트의 Smart Downloader CDN을 사용하는 서비스의 배포가 불가능하도록 수정.
    * 배포 버튼의 명칭을 서비스의 상태에 맞게 노출하도록 기능 수정.

### 2020. 06. 23.
#### 버그 수정
* [Unity SDK] v1.6.5
    * 실행환경에 따라 OverflowException이 발생하는 오류 수정
    
### 2020. 06. 11.
#### 기능 개선/변경
* [Console] 빌드배포 기능 수정.
    * Smart Downloader CDN을 사용하는 경우, 빌드배포 실행시 원본소스 파일과 CDN에 배포된 파일을 비교한 후에 배포 완료 처리하도록 기능 수정.
    * 빌드배포 실행시 빌드배포 버튼이 바로 비활성화 되도록 기능 수정.
    
### 2020. 05. 12.
#### 기능 개선/변경
* [Unity SDK] v1.6.4
    * 리소스 검사 옵션 추가
        * API 변경
            * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA 추가

### 2020.04.28
#### 기능 개선/변경
* [Unity SDK] v1.6.3
    * Streaming Assets 지원
        * Streaming Assets 리소스와 업로드 된 리소스를 비교 다운로드 기능 추가
        * API 변경
            * DownloadResult.CheckAndroidObb (Obsolete) → DownloadResult.CheckOption

### 2020.04.14
#### 기능 개선/변경.
* [Console] Smart Downloader CDN 수정
    * CDN 밴더사 변경을 위한 마이그레이션 작업 지원을 위해 CDN 수정이 불가능하게 변경
* [Console] 파일 업로드
    * 파일 업로드 제한을 전체 5GB 이하에서 단일 파일 5GB 이하로 변경

### March 24, 2020
#### Feature Updates
* [Console] Integrated with Smart Downloader CDN 
    * Removed the feature of selecting CDN service regions.


### March 10, 2020
#### Feature Update
* [Unity SDK] v1.6.2
    * Supports Android - Split Application Binary(OBB) 
        * Can download by comparing streaming asset resources included to OBB with uploaded resources.
        * Added API 
            * DownloadConfig.CheckAndroidObb


### January 21, 2020
#### Bug Fixes
* [Unity SDK] v1.6.1
    * Fixed exceptions that occur when there's no downloaded file to inspect. 


### December 24, 2019 
#### Feature Updates
* [Console] Service Management
    * Added a feature of creating a new CDN, when it fails to create CDN, by deleting failed CDN. 
* [Unity SDK] v1.6.0
    * Added API to check download capacity (CheckDownload)
    * Change APIs 
        * DownloadResult.IsSuccessful (Obsolete) → DownloadResult.Code
        * ProgressInfo.TotalFileNumber (Obsolete) → ProgressInfo.TotalFileCount
        * ProgressInfo.TotalReceivedBytes (Obsolete) → ProgressInfo.DownloadedBytes
* [Unity Tool] v1.0.2
    * Modified the resource tree view into the ascending order of file names. 

#### Bug Fixes
* [Unity Tool] v1.0.2
    * Fixed abnormal resource output from the page selecting uploaded resources, when the folder name is same as a file name in the lower path. 


### October 29, 2019 
* [Unity SDK] v1.5.9
    * Improved statistics indicators.


### July 29, 2019
#### Bug Fixes
* [Unity SDK] v1.5.8
    * Fixed the occurrence of crash while completing with downloads on particular Android devices.


### June 25, 2019 
#### Feature Updates
* [Unity SDK] v1.5.7
    * Added the About menu.
    * Deliver success (SUCCESS_NO_DIFFERENCE) as the result code when there is no resources to download for downloading the entire resources. 
    * Changed the folder structure
        * Assets/SmartDL/ → Assets/TOAST/SmartDL
        * `The existing SmrtDL folder must be deleted before imported. `
* [Unity Tool] v1.0.1
    * Changed the folder structure
        * Assets/SmartDL/ → Assets/TOAST/SmartDL
        * `The existing SmartDL folder must be deleted first before imported.`


### June 12, 2019
* [Unity Tool] v1.0.0
    * Deployed


### January 29, 2019
#### Feature Updates
* [Console] Common
    * Supports multiple languages (English and Japanese) throughout the entire page.


### December 27, 2018
#### Bug Fixes
* [Unity SDK] v1.5.6
    * Fixed the issue in which result callback is not called when downloading is canceled. 

#### Feature Updates
* [Console] Common
    * Applies inspection results throughout the whole page for standard language. 
* [Unity SDK] v1.5.6
    * Common
        * [ResultCode Renewal](/Game/Smart%20Downloader/ko/error-code)
            * [Caution] Error occurs when updated from existing SDK
    * iOS
        * Supports iOS 12 
    * Standalone(Windows)
        * Changed name and path of DLL 
            * smartnative_x86.dll → x86/smartnative.dll
            * smartnative_x64.dll → x86_64/smartnative.dll


### November 27, 2018  
#### Bug Fixes
* [Unity SDK] v1.5.5
    * Supports IL2CPP builds. 
    * Modified infrequent failure in acquiring IP addresses on mac OS. 


### October 23, 2018 
#### Feature Updates
* [Unity SDK] v1.5.4
    * Supports Unity February 2018. 
    * Enables downloading by selecting paths and files. 
    * Improved calculation for download file sizes.
    * Added namespaces for example codes. 

#### Bug Fixes
* [Unity SDK] v1.5.4
    * Fixed the unavailability of downloading on iOS when Korean is included to a file name. 
    * Fixed the unavailability of downloading when a file name or a directory name includes specific special characters.
* [Console] Service Management 
    * Fixed an issue in which resource files cannot be properly uploaded when the number exceeds 10 thousand.
    

### July 5, 2018 
#### Feature Updates
* [Console] Common
    * The [Deploy Builds]  button
        * Modified to enable the  [Deploy Builds] button, when the recent build is **Ready for Deployment** or **Deployment Failed**.
* [Console] Service List
    * Modified the recent build area. 
        * Previously: Showed upload date and time, last uploader, and status data. 
        * Now: Shows deployment date and time, resource upload date and time, and status data.  The [Deploy Builds] button is available from the status area on the service list. 


### June 26, 2018
#### Feature Updates
* [Console] Common
    * Added pop-ups to notify users of network disconnection.
    * Edited phrases
        * URL for resource deployment -> URL for origin server
        * Internal CDN -> Smart Downloader CDN
        * External CDN -> Client CDN
* [Console] Service Management
    * Separated Uploading Builds from Deployment 
        * Previously: Deployed immediately uploaded resources to user, when a resource is uploaded. 
        * Now: After resource is uploaded, click the  [Deploy Builds] button on View Service Details to deploy uploaded resources.
    * Changed the order of execution of uploading resource files and CDN registration when they are executed within the service registration wizard.
    * Added the feature to disallow changes to service and integration CDN for service deployment. 
    * Changed View Upload History to View Deployment History, within Show Service Details.

#### Bug Fixees
* [Console] Service Management 
    * Fixed some errors occurred while uploading resources.
    * Fixed some errors occurred while setting CDN.
    * Fixed an issue in which confirmation URL goes beyond the pop-up area when the URL for client's CDN is too long. 
    * Fixed an issue in which the horizontal and vertical scroll bars move concurrently on Explorer's View Build Details.


### June 5, 2018
#### Feature Updates
* [Unity SDK] v1.5.3
    * Added the retry logic 
    * Separated connection timeout from read timeout.

### April 24, 2018
#### Feature Updates
* [Console] Common
    * Allows to show error pop-ups on the service list page, not the error page, when error occurs within server.
* [Console] Service Management
    * Smart Downloader CDN cannot be created in duplicates at one service. 

#### Bug Fixes
* [Console] Service Management.
    * Fixed error in which file uploading fails infrequently on Mac's Chrome.
    * Fixed failure of service disabling due to errors occurred at file repository or CDN.
* [Console] Monitoring
    * Fixed error occurred on the monitoring page when service is not registered.



### April 18, 2018
#### Bug Fixes
* [Unity SDK] v1.5.1
    * Fixed link error out of the setting for Unity optimization.



### March 22, 2018
#### Feature Updates
* [Console] Service Management
    * Updated to allow many kinds of domain information (including regex) for Referrers for CDN integration.

#### Bug Fixes
* [Console] Common

    * Fixed the exposure of an error page when another language is selected, other than Korean.
    * Fixed an issue in which a login page is redundantly created within the service area on web console, when it's been logged out on another tab.
* [Console] Service Management.

    * Fixed the build status which constantly shows Registering when the browser is refreshed, or closed while uploading a build. 

    * Fixed an issue in which the horizontal and vertical scroll bars move concurrently for View Build Details.

* [Console] Monitoring.

    * Fixed the unavailability of selecting the service list, for the search on the monitoring page, is hidden by the chart area.
    * Fixed the search condition field, which shows above the pop-up created on the monitoring page.
    * Fixed an issue in which tooltips for particular countries are created way below the mouse cursor on the map chart.
    * Fixed UI errors that occur on IE 10/11/Edge. 



### February 22, 2018
#### Feature Updates
* Added **Service** an individual unit under Smart Downloader. 
* [Console] Enhanced user convenience 
    * Added the feature of Upload/Deploy New Builds.
    * Allows to enable TOAST CDN to deploy builds. 
    * Updated Real-time/Monitoring indicators.
    * Specify status indicators for download errors. 
* [Unity SDK] Release v1.5.0 
    * Removed dependency on the core library.
    * Change API 
        * Changed Improve Usability API.
* [Jenkins Plugin] Provides Jenkins Plugin to uploade new builds. 



### October 26, 2017
#### Feature Updates
* [Unity SDK] Released v1.2.0 
    * Enhanced stability 
        * Removed dependency on internal SDKs. 
        * Decreased dependency on the native library.

#### Bug Fixes
* [Server] Fixed authentication-related bugs.
    * Fixed bugs in which authentication is successful even if total appkey is removed. 
    * Changed the error message for failed authentication. 



### February 23, 2017
#### Feature Updates
* [Console] Added tabs to access each page. 
* [Console] Modified the feature of resetting search items, when there's too much data to search for download details. 
* [Console] Updated to disallow the selection of 'Download Time/Speed' when download failure only is selected to search for download details. 
* Released [SDK][[Unity-1.1.0](/Download/#upcoming-products-smart-downloader)] 
    * Changed the class name (DLCSkin -> SmartDLUnitySkin).
    * Provides Only Static API 



### January 19, 2017
#### New Releases
* Released Smart Downloader 
    * Smart Downloader supports efficient downloading of resources that are required for a game.
    * A variety of statistical data are provided on the basis of downloaded game data. 
