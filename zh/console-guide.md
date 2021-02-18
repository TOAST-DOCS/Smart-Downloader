## Game > Smart Downloader > Console Guide

To use Smart Downloader, the service must be enabled before registered.  
The service registration is configured in the three-stage Wizard format, such as \[Register Service\] > \[Integrate CDN] > \[Upload Resources\]. After the Wizard service is registered, \[Deploy Build] must be completed, so as to download deployment documents via SDK. 
After service registration, real-time status and indicators of downloads can be provided in various charts of formats, while data download is enabled.  
<br>

## Configuration

### Enable Smart Downloader 
Click **Select Services** on top of the Console page, and select Smart Downloader below Game, to enable the service. 

### Check AppKey and URL 
Click URL & Appkey on top of the Console page to check issued Appkey. Enter the Appky for SDK. 
Take note that when Smart Downloader is disabled, an issued Appkey cannot be restored. 

![smartdl_01_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_01_201812.png)

## Service Management Tab

### 1. Register Services 
#### 1.1 Register Services ![smartdl_02_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_02_201812.png)
- Service Name 
    - It is a **Required Entry** as it identifies service.
    - Used as an identifier, same service name cannot be registered more than once for a project. 
    - Only **Alphabets, numbers, and special characters (_),(-)** are available, while the first letter must start with a **small-case alphabet or number**. 
    - Cannot start with a space. 
    - Cannot exceed 30 bytes. 

- Service Description 
	- Enter description for each service, not exceeding 100 bytes. 

- When service registration is completed, go to \[Phase 1. Service Registration Completed\].

#### 1.2 Complete Service Registration 
![smartdl_03_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_03_201812.png)

- Registered service name and description can be found. Click \[Next\] to go to \[Integrate CDN], which is Phase 2 of the service registration Wizard. 

### 2. Integrate CDN 
#### 2.1 Guide for CDN Integration 

![smartdl_04_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_04_201812.png)

- 2.1.1 Select Integration for Smart Downloader CDN
	- Enter CDN setting information on the \[Creating CDN Service\] pop-up. 
		![smartdl_05_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_05_201812.png)
		- Service
			- Service Area: Select the range of CDN application. Choose either Korea or Global; default is Korea. 
			- Description: Describe briefly about CDN. 
		- Cache
			- Cache Expiration: Select the replacement cycle for files saved in CDN with new ones. Default is set as 24 hours, and if further setting is required, select **User Configuration**.  
			- Cache Expiration (seconds): Enter cache cycle of CDN, when **User Configuration** is opted for **Cache Expiration** (unavailable for default setting). 
			- Referrer Access Management: Select the restriction type of access to CDN. **Blacklist** restricts access by entered referrers only, while **Whitelist** allows access by entered referrers only.  
			- Referrers: Enter referrers to restrict the access. Regular expression is supported, and use line feeds to enter many referrers. 
	- Integrating Smart Downloader CDN takes about a minute, to the maximum. 

- 2.1.2 Select Integration with External CDN 
	- \[Guide\] will pop up to proceed with Step 1 and Step 2, to use external CDNs.  
    ​   ![smartdl_06_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_06_201812.png)
	    - Step 1
	        - Provide **URL to be applied as Original Server Address**.
	    - Strep 2
    	    - Enter **CDN URL to Use** so as to integrate Smart Downloader with an external CDN. 
	        - Enter external CDN URL by selecting HTTP/HTTPS protocol. 

#### 2.2 Complete CDN Integration 

![smartdl_07_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_07_201812.png)

- Registered CDN server address and original server URL can be found. Click \[Next\] to go to \[Upload Resources\], which is Phase 3 of the service registration Wizard. 

### 3. Upload Resources 
- Resources are uploaded by folder, on principle. 
  (Click Upload, and the Search Folders window is loaded.)
- Internet Explorer does not support uploading resources: Chrome is recommended.  

#### 3.1 Guide for Resource Uploads 

![smartdl_08_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_08_201812.png)

- A. Uploads by Local Machine 
  ​    - Resources on user's local computer can be uploaded via console. 
  ​    - Click \[Upload Resources\] on this page.  
  ​    - With uploads completed, it is transferred to \[Phase 3. Complete Resource Uploads].

- B.  Uploads by Build Server (Remote)

  - Upload resources via Smart Downloader Jenkins Plugin (ToastCloud Smart Downloader Plugin).

  ​    - For more details on ToastCloud Smart Downloader Plugin, see [User Guide for Plugin](http://docs.toast.com/ko/Game/Smart%20Downloader/ko/plugin-guide/).

#### 3.2 Complete Resource Uploads  

![smartdl_09_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_09_201812.png)

- Service Name 
    - Name of registered service.

- Resource Upload Information  
	- Shows the number of uploaded resource files and the total file size.
	- Click details to see uploaded resources on the tree pop-ups.  

- Final Uploads 
    - Date and time of the last upload of the latest resources. 
    
- Deployment Status
    - Shows the current status of resources. 
    - When it is ready for deployment, deployment is available by clicking \[Deploy Builds\] on the \[Service Management\] - \[Service Details\] page. 

**\[Canceling Resource Uploads\]**

![smartdl_10_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_10_201812.png)

- Smart Downloader supports for canceling uploads while they are underway.
- Take note that, when upload is completely canceled, the deployment status returns to the state before uploaded. (*@업로드 취소 기능이 완료되면* - 업로드 취소가 완료되면??) 

### 4. List of Services 
Shows the list of services registered by user, by 10. Click each row of service, to go to \[Service Details\]. 

![smartdl_11_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_11_201812.png)

- Service Name

    - Name of service entered by user when it is registered.

- CDN
    - Server: CDN download URL. (If CDN download URL is not registered, \[CDN URL is required.\] shows.)
    - Status: Data is available only when Smart Downloader CDN is used. For external CDNs, the status is shown as **-**. 
    - | Status | Description |
      |----------|---------|
      |![작업 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_progressing.PNG)| Integrating Smart Downloader CDN. |
      |![정상](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_success.PNG)       |Smart Downloader CDN is properly integrated.|
      |![생성실패](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_fail.PNG)   |Failed to integrate Smart Downloader CDN; if it continues, contact Customer Center. |


- Latest Builds 
    - Date and Time of Build Deployment: Last deployment time of the latest build.
    - Date and Time of Resource Upload: Last uploaded time of the latest build.
    - Status: Current status of uploaded resources. When the status is **Ready for Deployment** or **Deployment Failed**, \[Deploy Builds\] is enabled.  
    - | Status | Description |
      |----------|---------|
      |![등록 전](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/resource_not_register.PNG)| Resource is not registered. |
      |![업로드 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/resource_uploading.PNG)  |Uploading resources. <br>Under the status, uploading or deleting new resources are not available.|
      |![배포 대기](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/build_complete.PNG)    |Resource has been completely uploaded. Click \[Deploy Builds\] to deploy builds.|
      |![배포 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/deploying.PNG)|Deployment is underway with \[Deploy Builds\].<br>Under the status, uploading, modifying, or deleting new resources are not available.|
      |![배포 완료](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/deploy_complete.PNG)   |Uploaded resources are completely deployed to CDN.|
      |![업로드 실패](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/upload_fail.PNG)   |Failed to upload resources. If it continues, contact Customer Center.|
      |![배포 실패](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/deploy_fail.PNG)   |Failed to deploy with \[Deploy Builds\]. Redeployment is available, with \[Deploy Builds\].<br>If the status continues, contact Customer Center.|


### 5. Service Details 
Detail information of registered services can be found. It is comprised of \[Service Information\], \[Guide for CDN Integration\], \[Latest Build Information\], and \[History of Build Deployment\].

![smartdl_13_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_13_201812.png)

#### 5.1 Service Information 
Shows the name and description of service, entered for registration.  

#### 5.2 Guide for CDN Integration 
Shows CDN information integrated with service, when it is completed. Describes how to integrate CDN, for each case of A to C.   

**A. Integration with Smart Downloader CDN**

| Item | Description |
| --- | --- |
| CDN Server | Displayed as Smart Downloader CDN. |
| CDN Server Address | Download CDN URL is automatically created along with integration with Smart Downloader CDN, with the URL exposed to the public. |
| CDN Configuration | Click Check Information to find configuration of Smart Downloader CDN. |

**B. Integration with External CDNs**

| Item | Description |
| --- | --- |
| CDN Server | Displayed as External CDN. |
| CDN Server Address | Shows external CDN URL entered by user for integration. If it is not available, go for modification and enter the URL of external CDN. |
| Original Server URL | Shows URL to be applied as original server address. |

**C. Not Integrated with CDN**

- Guide for CDN integration shows. Click Modify to configure CDN information. 

#### 5.3 Latest Build Information 
Uploaded resource information shows when upload is completed. 
If the deployment status is **Before Registration**, all information is blank (with detail information for \[Resource Upload Information\] disabled)

> \[Caution\]
If the deployment status is **Uploading, or Deploying**, new resources cannot be uploaded. 
If the deployment status is **Ready for Deployment**, the latest builds can be deployed to CDN.  (Even for the **Deployment Failed** status, \[Deploy Builds\] is enabled for redeployment.)

![smartdl_14_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_14_201812.png)

| Item | Description |
| --- | --- |
| Upload New Resources | New resources can be uploaded on this page.<br>If the deployment status is **Uploading or Deploying**, new resources cannot be uploaded. |
| Resource Upload Information | Shows the number of uploaded resource files and the total file size. |
| Detail Information | Displays uploaded resource information on the tree pop-ups. |
| View Deployment History | Shows \[Build Deployment History\] at the bottom of service detail information. |
| Date/Time of Last Upload | Date and time of user-configured resource uploads. |
| Last Registrar | NHN Cloud account information of the user who uploaded resources. |
| Deployment Status | Deployment status of the latest build, and each status value is same as information on List of Service > Latest Builds. |
| Deploy Builds | If the latest build is **Ready for Deployment**, such build can be deployed via integrated CDN. (Even for the **Deployment Failed** status, \[Deploy Builds\] is enabled for redeployment.)<br>Deployment for Smart Downloader CDN takes 10 minutes to the maximum, while it may vary for external CDNs depending on the environment. |

#### 5.4 Build Deployment History 

![smartdl_15_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_15_201812.png)

History information for **Deployment Successful**, or **Deployment Failed** is displayed in the descending date/time order of build deployment.  

| Item | Description |
| --- | --- |
| Date/Time of Build Deployment | Date and time when deployment is completed with the \[Deploy Builds\] button. |
| Last Deployer | NHN Cloud account information of the user who deployed with \[Deploy Builds\]. |
| Date/Time of Resource Upload | Date and time of user-configured resource uploads. |
| Last Registrar | NHN Cloud account information of the user who uploaded resources. |
| Status | Deployment status of the latest builds, and each status is same as \[Deployment Status\] of \[Latest Build Information\] at the top. |

#### 5.5 Deleting Services 
- Service can be deleted by using Delete on the right of the \[Service Detail Information\] page.  
>\[Caution\]
>If the deployment status is **Uploading or Deploying**, or if CDN is **Progressing**, service cannot be deleted. 
>Take note that, if a service is deleted, the original files and deployment files are all deleted, while CDN service is also suspended, for integration with Smart Downloader CDN.  


### 6. Modify Service 
Click Modify on the right of the \[Service Detail Information\] page, to go to Modify Service. 

> \[Caution\]
If the deployment status is **Uploading or Deploying**, or if CDN is **Progressing** for integration with Smart Downloader CDN, service cannot be modified. 

![smartdl_16_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_16_201812.png)

#### 6.1 Service Information 
Service name is a fixed value and cannot be modified, while service description is modifiable. 

#### 6.2 CDN Information
Modifying CDN information is guided for three types of current CDN integration as below:  

**6.2.1 For Smart Downloader CDN Integration**
​	- Change of integration is available from Smart Downloader CDN to External CDN.
​   - Server address of external CDN must be entered by selecting HTTP/HTTPS protocol.  

**6.2.2 For External CDN Integration**
​	- Change of integration is available from External CDN  to Smart Downloader CDN. 

**6.2.3 For Non CDN Integration**
​	- Select either Smart Downloader CDN or External CDN to integrate with CDN. 


## Real-Time Monitoring Tab
Shows statistical data of user who downloaded service throughout the day, up to now, at every 10 minutes, starting from 00:00:00. 

### 1. Status of Real-Time Downloads  
#### 1-1 Mini Charts 
Shows the entire statistical information for selected **search conditions** on a simple chart.  
Each item is described as below: 


![smartdl_21_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_21_201812.png)

| No. | Item | Description |
| --- | --- | --- |
| 1 | Select Service | - Select a service to check download status. <br> - A change of selected service changes charts on the whole page. |
| 2 | Select Country | - Select to find statistical data of a particular country.<br> - Shows top 10 downloaded countries only. <br> - A change of the country changes only the chart information on **Real-Time Download Status**. |
| 3 | Collecting Time of Chart Data | - Last time when the chart information was collected. |
| 4 | Chart Name | - Title for a chart of information. <br> - **Type** <br> -- Download Total: Total number of downloads. <br> -- Full Download Count: Number of full downloads for uploaded build files.<br> -- Download Success: Number of successful downloads.<br> -- Average Download Time: Average download time. |
| 5 | Number of Downloads | Refers to the total average download time for the average download time chart. |
| 6 | Comparison with Downloads at Same Time of Previous Day | Compare with the total average download time for the average download time chart. |
| 7 | Download Type | Specify full or updated downloads. |
| 8 | Success Rate | Success rate of downloads |


#### 1-2 Chart for Each OS 
Displays the entire statistical data for selected **search conditions** on a simple chart. 
Each item is described as below: 

![smartdl_22_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_22_201812.png)

| No. | Item | Description |
| --- | --- | --- |
| 1 | Select OS | - All (default): Shows statistics for all OS.<br> - iOS / Android / Windows: Shows downloaded statistics only on a selected OS. <br> - MacOS (optional): Selectable only when a download record from MacOS is available. |
| 2 | Download Success / Fail | - Column Chart (accumulated).<br> - Shows statistics in every 10 minutes.<br> - Number of successful/failed downloads. |
| 3 | Full / Update Download | - Column Chart (accumulated).<br> - Shows statistics in every 10 minutes.<br> - Number of downloads for total uploaded/some modified files.<br> - Unknown refers to failure during downloading the list of updates. |
| 4 | Average Download Time(sec) | - Column Chart.<br> - Shows statistics in every 10 minutes. <br> - Average downloading time. |


### 2. Download Status by Country 
Displays the statistical data for selected **search conditions** for each country on a table.
Each item is described as below: 

![smartdl_23_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_23_201812.png)

| No. | Item | Description |
| --- | --- | --- |
| 1 | Save Data | Click to download all download tables of each country in **.csv** files. |
| 2 | Table of Download Status by Country | - Shows top 5 downloaded countries only.<br> - Selectively shows downloaded records only, for MacOS. |


## Monitoring Indicator Tab 
Enable Smart Downloader to find usage statistical data by day, from when it was downloaded, up to now.  

### 1. Search Conditions 
Regards to selecting conditions to search for downloading indicators. 
Each item is described as below: 

![smartdl_24_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_24_201812.png)

| No. | Item | Description |
| --- | --- | --- |
| 1 | Search Period | - Search period for download statistical data.<br>- Selected by day.<br>- Available from initial downloaded day to the current day. |
| 2 | Search Conditions- Service | - Select a service to search for download statistics. |
| 3 | Search Conditions- Country | - Select a country to search for download statistics.<br> - Shows top 10 downloaded countries only. |
| 4 | Search Conditions- Download Type | - All Type: Search statistics for all download types regardless of conditions.<br> - Full Download: Search statistics only for full downloads of uploaded build files.<br> - Update Download: Search statistics only for the downloads of modified uploaded build files.<br> - Unknown: Search statistics only for troubled meta-file downloads to find if the downloads are full or for the updated. |
| 5 | Search | - Search for statistical data on selected conditions. |


### 2. Download Status by Day  
#### 2-1 Daily Statistical Data 
Displays daily statistical data for selected **search conditions** on a table. 
Each item is described as below: 

![smartdl_25_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_25_201812.png)

| No. | Item | Description |
| --- | --- | --- |
| 1 | Save Data | - Save download tables of each country in **.csv** files. |
| 2 | Daily Indicator | - Shows the number of full downloads of each OS and successful/failed downloads and average download time by day. <br> - Selectively shows downloaded records only, for MacOS.<br> - Shows 10-day statistical information on a page. |
| 3 | Select Page | - Select a page to search. |

#### 2-2 Daily Indicator Chart 

Displays statistical data for selected **search conditions** on a chart. 
Each chart type is described as below: 

![smartdl_26_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_26_201812.png)

| No. | Item | Description |
| --- | --- | --- |
| 1 | Download Total | - Column Chart (accumulated).<br> - Shows statistics by day.<br> - Total number of downloads for each OS. |
| 2 | Download Success | - Column Chart (accumulated).<br> - Shows statistics by day.<br> - Number of successful downloads for each OS. |
| 3 | Download Time (sec) | - Column Chart (compared).<br> - Shows statistics by day.<br> - Average download time for each OS. |
| 4 | Download Fail Type | - Pie Chart.<br> - Whole search period.<br> - Number and rate of failed downloads for each cause of failure. |


### 3. Download Status by Day 
Displays statistical data by country for selected **search conditions** on a table. 
Each item is described as below: 

![smartdl_27_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_27_201812.png)

| No. | Item | Description |
| --- | --- | --- |
| 1 | Save Data | Click to download all download tables of each country in **.csv** files. |
| 2 | Table of Download Status by Country | - Shows top 5 downloaded countries only.<br> - Selectively shows downloaded records only, for MacOS. |