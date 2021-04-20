## Game > Smart Downloader > Release Notes > Console


### 2020. 11. 24.
#### Feature Updates
* 일괄, 예약 배포 기능 추가.
    * Smart Downloader CDN을 사용하는 서비스는 목록 페이지에 일괄, 예약 배포를 진행할 수 있도록 기능 추가.
    * Smart Downloader CDN을 사용하는 서비스는 개별 배포시에도 예약 배포를 진행할 수 있도록 기능 추가.
* 서비스 생성 마법사의 파일 업로드 화면에서 파일 업로드 없이 서비스 생성이 가능하도록 수정.


### 2020. 07. 14.
#### Feature Updates
* 빌드배포 기능 수정.
    * 빌드배포시 5분간 같은 프로젝트의 Smart Downloader CDN을 사용하는 서비스의 배포가 불가능하도록 수정.
    * 배포 버튼의 명칭을 서비스의 상태에 맞게 노출하도록 기능 수정.


### 2020. 06. 11.
#### Feature Updates
* 빌드배포 기능 수정.
    * Smart Downloader CDN을 사용하는 경우, 빌드배포 실행시 원본소스 파일과 CDN에 배포된 파일을 비교한 후에 배포 완료 처리하도록 기능 수정.
    * 빌드배포 실행시 빌드배포 버튼이 바로 비활성화 되도록 기능 수정.


### 2020. 04. 14.
#### Feature Updates
* Smart Downloader CDN 수정
    * CDN 밴더사 변경을 위한 마이그레이션 작업 지원을 위해 CDN 수정이 불가능하게 변경
* 파일 업로드
    * 파일 업로드 제한을 전체 5GB 이하에서 단일 파일 5GB 이하로 변경

### March 24, 2020
#### Feature Updates
* Integrated with Smart Downloader CDN 
    * Removed the feature of selecting CDN service regions.


### December 24, 2019 
#### Feature Updates
* Service Management
    * Added a feature of creating a new CDN, when it fails to create CDN, by deleting failed CDN. 


### January 29, 2019
#### Feature Updates
* Common
    * Supports multiple languages (English and Japanese) throughout the entire page.


### December 27, 2018
#### Feature Updates
* Common
    * Applies inspection results throughout the whole page for standard language. 


### October 23, 2018 
#### Bug Fixes
* Service Management 
    * Fixed an issue in which resource files cannot be properly uploaded when the number exceeds 10 thousand.


### July 5, 2018 
#### Feature Updates
* Common
    * The [Deploy Builds]  button
        * Modified to enable the  [Deploy Builds] button, when the recent build is **Ready for Deployment** or **Deployment Failed**.
* Service List
    * Modified the recent build area. 
        * Previously: Showed upload date and time, last uploader, and status data. 
        * Now: Shows deployment date and time, resource upload date and time, and status data.  The [Deploy Builds] button is available from the status area on the service list. 


### June 26, 2018
#### Feature Updates
* Common
    * Added pop-ups to notify users of network disconnection.
    * Edited phrases
        * URL for resource deployment -> URL for origin server
        * Internal CDN -> Smart Downloader CDN
        * External CDN -> Client CDN
* Service Management
    * Separated Uploading Builds from Deployment 
        * Previously: Deployed immediately uploaded resources to user, when a resource is uploaded. 
        * Now: After resource is uploaded, click the  [Deploy Builds] button on View Service Details to deploy uploaded resources.
    * Changed the order of execution of uploading resource files and CDN registration when they are executed within the service registration wizard.
    * Added the feature to disallow changes to service and integration CDN for service deployment. 
    * Changed View Upload History to View Deployment History, within Show Service Details.

#### Bug Fixees
* Service Management 
    * Fixed some errors occurred while uploading resources.
    * Fixed some errors occurred while setting CDN.
    * Fixed an issue in which confirmation URL goes beyond the pop-up area when the URL for client's CDN is too long. 
    * Fixed an issue in which the horizontal and vertical scroll bars move concurrently on Explorer's View Build Details.


### April 24, 2018
#### Feature Updates
* Common
    * Allows to show error pop-ups on the service list page, not the error page, when error occurs within server.
* Service Management
    * Smart Downloader CDN cannot be created in duplicates at one service. 

#### Bug Fixes
* Service Management.
    * Fixed error in which file uploading fails infrequently on Mac's Chrome.
    * Fixed failure of service disabling due to errors occurred at file repository or CDN.
* Monitoring
    * Fixed error occurred on the monitoring page when service is not registered.


### March 22, 2018
#### Feature Updates
* Service Management
    * Updated to allow many kinds of domain information (including regex) for Referrers for CDN integration.

#### Bug Fixes
* Common
    * Fixed the exposure of an error page when another language is selected, other than Korean.
    * Fixed an issue in which a login page is redundantly created within the service area on web console, when it's been logged out on another tab.
* Service Management.
    * Fixed the build status which constantly shows Registering when the browser is refreshed, or closed while uploading a build. 
    * Fixed an issue in which the horizontal and vertical scroll bars move concurrently for View Build Details.
* Monitoring.
    * Fixed the unavailability of selecting the service list, for the search on the monitoring page, is hidden by the chart area.
    * Fixed the search condition field, which shows above the pop-up created on the monitoring page.
    * Fixed an issue in which tooltips for particular countries are created way below the mouse cursor on the map chart.
    * Fixed UI errors that occur on IE 10/11/Edge. 


### February 22, 2018
#### Feature Updates
* Added **Service** an individual unit under Smart Downloader. 
* Enhanced user convenience 
    * Added the feature of Upload/Deploy New Builds.
    * Allows to enable TOAST CDN to deploy builds. 
    * Updated Real-time/Monitoring indicators.
    * Specify status indicators for download errors. 


### February 23, 2017
#### Feature Updates
* Added tabs to access each page. 
* Modified the feature of resetting search items, when there's too much data to search for download details. 
* Updated to disallow the selection of 'Download Time/Speed' when download failure only is selected to search for download details. 

### January 19, 2017
#### New Releases
* Released Smart Downloader 
    * Smart Downloader supports efficient downloading of resources that are required for a game.
    * A variety of statistical data are provided on the basis of downloaded game data. 