## Game > Smart Downloader > Release Notes

### January.21, 2020

#### 버그 수정

* [Unity SDK] v1.6.1
    * 다운로드 검사할 파일이 없는 경우 발생하던 예외 수정

### December.24, 2019

#### 기능 개선/변경

* [Console] 서비스 관리.
    * CDN의 생성에 실패한 경우, 실패한 CDN을 삭제하고 새로운 CDN을 생성하기 위한 기능 추가.
* [Unity SDK] v1.6.0
    * 사전 다운로드 용량을 확인하기 위해 API 추가 (CheckDownload)
    * API 변경
        * DownloadResult.IsSuccessful (Obsolete) → DownloadResult.Code
        * ProgressInfo.TotalFileNumber (Obsolete) → ProgressInfo.TotalFileCount
        * ProgressInfo.TotalReceivedBytes (Obsolete) → ProgressInfo.DownloadedBytes
* [Unity Tool] v1.0.2
    * 리소스 트리 뷰에서 파일명으로 오름차순 정렬해서 보여주도록 수정

#### 버그 수정

* [Unity Tool] v1.0.2
    * 폴더명과 하위의 파일명이 동일한 경우 업로드 리소스 선택 화면에서 리소스 출력이 정상적이지 않은 문제 수정

### October.29, 2019

#### 기능 개선/변경

* [SDK] Unity SDK v1.5.9
    * 통계 지표 개선


### July.29, 2019

#### 버그 수정

* [SDK] Unity SDK v1.5.8
    * 특정 Android에서 다운로드 완료 처리 중 크래시가 발생하던 현상 수정


### Jun.25, 2019

#### 기능 개선/변경

* [SDK] Unity SDK v1.5.7
    * About 메뉴 추가
    * 전체 리소스 다운로드 시 다운로드 받을 리소스가 하나도 없는 경우 결과 코드를 성공(SUCCESS_NO_DIFFERENCE)으로 전달
    * 폴더 구조 변경
        * Assets/SmartDL/ → Assets/TOAST/SmartDL
        * `기존에 설치된 SmartDL 폴더를 삭제 후 임포트 해야 합니다.`
* [Unity Tool] v1.0.1
    * 폴더 구조 변경
        * Assets/SmartDL/ → Assets/TOAST/SmartDL
        * `기존에 설치된 SmartDL 폴더를 삭제 후 임포트 해야 합니다.`

### Jun.12, 2019

* [Unity Tool] v1.0.0
    * 배포
    
### Jan.29, 2019

#### 기능 개선/변경
* [Console] 공통
    * 페이지의 전체 메세지에 다국어(영어, 일어) 반영


### Dec.27, 2018

#### Feature Updates 
* [Console] Common
    * Applied the result of language correction throughout the whole pages.


### Nov.27, 2018

#### Bug Fixes 
* [SDK] Unity SDK v1.5.5
    * Support IL2CPP build  
    * Modified infrequently-failed acquisition of IP Address on MacOS 


### Oct.23, 2018
#### Feature Updates 
* [SDK] Unity SDK v1.5.4
    * Support Unity Feb.2018.
    * Allowed downloads by selecting paths and files.  
    * Improved calculating download file sizes. 
    * Added example code namespace.  

#### Bug Fixes 
* [SDK] Unity SDK v1.5.4
    * Fixed the issue of download failure when Korean is included to file name on iOS. 
    * Fixed the issue of download failure when file name or directory name includes some special characters.

* [Console] Service Management
    * Fixed the issue of download failure when the number of resource files to upload exceeds 10 thousand.
    

### July 5, 2018.07.05
#### Feature Updates
* [Console] Common
    * [Deploy Builds] Button
        * Updated to enable [Deploy Builds] when the latest build is **Ready for Deployment** or **Deployment Failed**.
* [Console] Service List 
    * Updated Recent Build Area
        * Before Updated: Showed date/time of uploads and last uploader, as well as status data.
        * After Updated: Shows date/time of build deployment and resource uploads, and status data. The [Deploy Builds] button is available in the status area of service list.


### June 26, 2018.06.26
#### Feature Updates
* [Console] Common
    * Added pop-ups to allow easy recognition when network is disconnected. 
    * Modified Phrases.
        * Resource Deployment URL -> Original Server URL
        * Internal CDN -> Smart Downloader CDN
        * External CDN -> External CDN (@*영어로는 기존과 같게 표기하고 있습니다*.)
* [Console] Service Management
    * Separate Upload Builds from Deploy Builds.
        * Before Updated: Resources, after immediately uploaded, were deployed to users.
        * After Updated: Resources, after uploaded, are deployed by clicking [Deploy Builds] from View Service Details.
    * Allowed the change of the task order for resource file uploads and CDN registration, when executed within the service registration wizard. 
    * Added a feature to disallow change in service and integration CDN when service is deployed.
    * Changed View Upload History into View Deployment History, within View Service Details.

#### Bug Fixes 
* [Console] Service Management
    * Fixed some errors that occur during resource uploads.
    * Fixed some errors that occur during CDN configuration.
    * Fixed the issue of a long URL of external CDN that extends beyond the pop-up window.
    * Fixed the issue of concurrent movement of horizontal and vertical scrolls, on View Build Details in Explorer.


### June 05, 2018
#### Feature Updates
* [SDK] Unity SDK v1.5.3
    * Added the logic of retries.
    * Separated timeouts for connection from read.

### April 24, 2018
#### Feature Updates
* [Console] Common
    * Added a feature to show error pop-ups on the Service List page, not on Error Page, when error occurs on a server.
* [Console] Service Management 
    * Added a feature not to redundantly create Smart Dowloader CDN for a single service.

#### Bug Fixes
* [Console] Service Management
    * Fixed the issue of failed file uploads on Mac Chrome.
    * Fixed the issue of failure, due to errors occurred in file depository or CDN, when service is disabled. 
* [Console] Monitoring 
    * Fixed the errors that occur on the monitoring page, when service is not registered.



### April 18, 2018
#### Bug Fixes
* [SDK] Unity SDK v1.5.1
    * Fixed the error in links, occurred due to Unity optimization option settings.



### March 22, 2018
#### Feature Updates
* [Console] Service Management
    * Allowed to enter many domains (including regex) among entry values for CDN integration, for Referrers.

#### Bug Fixes
* [Console] Common
    * Fixed the issue of error page displayed, when the language option is selected for others, except Korean. 
    * Fixed the redundant creation of the login page within service area of the web console, when it was logged out from another tab. 
* [Console] Service Management
    * Fixed the issue of continued display of the build status as Registering, when the window is closed or refreshed, during build uploads.
    * Fixed the issue of concurrent movement of horizontal and vertical scrolls when build details are queried.
* [Console] Monitoring.
    * Fixed the issue of failure in selecting services to search in the monitoring page, as the list is hidden by the chart area.
    * Fixed the display of the search condition field, upon pop-ups for monitoring page.
    * Fixed a map chart issue, where a tool-tip for particular countries, is created way below as it is larger than a mouse cursor.
    * Fixed UI errors that occur in IE 10, 11, or Edge.



### Feb. 22, 2018
#### Feature Updates
* Added **Service**, as an individual unit within Smart Downloader.
* [Console] Improved user convenience. 
    * Added uploading/deploying new builds.
    * Allowed to use TOAST CDN for build deployment.
    * Improved real-time/monitoring indicators. 
    * Specified status indicators for download errors.
* [SDK] Unity SDK v1.5.0 Release 
    * Removed dependency on the core library.  
    * Change API
        * Changed API for improved usability. 
* [Jenkins Plugin] Provided Jenkins Plugin to enable new build uploads.



### Oct.26, 2017
#### Feature Updates
* [SDK] Unity SDK v1.2.0 Release
    * Improved Stability 
        * Removed dependency on internal core SDKs.
        * Reduced dependency on native libraries.

#### Bug Fixes
* [Server] Fixed Authentication Issue.
    * Fixed the bug of successful authentication even after common Appkey is deleted.  
    * Updated the error message for failed authentication.



### Feb. 23, 2017
#### Feature Updates 
* [Console] Added a tab to access each page.  
* [Console] Allowed to re-configure search, if there is too much data to search of download details.
* [Console] Disabled selecting the 'Download Time/Speed' item, when only Download Failed is selected to search download details.
* [SDK][[Unity-1.1.0] (/Download/#upcoming-products-smart-downloader)] Release.
    * Changed the class name (DLCSkin -> SmartDLUnitySkin).
    * Provided only static API.



### Jan.19, 2017
#### Release of New Products 
* Release of Smart Downloader 
    * Smart Downloader is an efficient downloading service for game resources.
    * A variety of statistical data is provided based on downloaded game data.
