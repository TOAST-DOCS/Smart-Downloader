## Game > Smart Downloader > User Guide for Unity Tool 

## Getting Started 

Smart Downloader Unity Tool (SUT) is a tool to upload and deploy resources for Unity.  

### Environments

#### Supported Unity Versions

* 2018.4.0 - 2021.1.20

### Download

[Smart Downloader Unity Tool](/Download/#game-smart-downloader)


### Install Unity Tool

1. Open a Unity project. 
2. In Unity, select **Assets > Import Package > Custom Package**.
3. Select and import 'Smart-downloader-unity-tool-{Version}.unitypackage', which is a downloaded Unity Tool file. 
    ![sut_import.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_import.png)

## Enabling Unity Tool  

To enable Unity Tool, select **Tool > NHN Cloud > Smart Downloader > Unity Tool** in the menu. 

### Authenticate 

If the authentication has not been performed, the **Authentication** tab appears. 

![sut_credentials_tab.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_credentials_tab.png)

* User ID: NHN Cloud ID
* User Access Key ID, Secret Access Key
    1. In [API Security Setting](https://console.toast.com/securitySetting), select **Create User Access Key ID**.
    2. When the dialog box appears, choose **Create User Access Key ID and Secret Access Key**.
    3. The dialog box indicating the completion of Secret Access Key issuance appears.
    4. Check the issued User Access Key ID information and status information on the API Security Setting page.

    > [Caution]
    > - It is recommended to change the User Access Key ID every 90 days.
    > - You can create up to 5 User Access Key IDs per NHN Cloud ID and 5 per IAM ID.
    > - The Secret Access Key cannot be verified again and must be reissued if lost. After creating the key, store the created key securely.

* Project ID
    * A project ID using Smart Downloader, which can be found from **Project Setting** on the console.  
    ![console_project_id.png](https://static.toastoven.net/prod_smartdownloader/sut/console_project_id.png)


### Query Services   

When the authentication is complete, the **Upload** tab appears. 
Enter the appkey in **Appkey** and click **Query**, and the list of services created on the console is displayed.  

![sut_upload_tab_base.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_tab_base.png)

* Appkey
    * Click **URL & Appkey** from Smart Downloader of the console and check the issued appkey.
    ![console_appkey.png](https://static.toastoven.net/prod_smartdownloader/sut/console_appkey.png)

### Uploading Resources 

#### 1. Select Services 

Click a service to upload from the service list and select resource path. 
If the path is correct, the **Upload** button will be activated. 

![sut_upload_step_1.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_1.png)

#### 2. Select Upload Resources 

Compares resources of the selected path with those of the last uploaded, and shows changes.
Select resources to upload, and the **Upload** button will be activated.  

> Caution 
Files that are automatically created from OS (.DS_Store, desktop.ini, thumbs.db) are excluded. 
Each resource cannot be larger than 5GB. 

![sut_upload_step_2.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_2.png)

#### 3. Upload Resources 

Shows uploading progress. 
If tool is closed while uploading is underway, a window pops up asking whether to cancel uploading or not. 

> Caution 
Do not force close unity while uploading is underway. 
If it is forced to close, the status remains to be uploading, and will be changed to failure in 30 minutes.  

![sut_upload_step_3.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_3.png)


#### 4. Complete

When it is normally completed, a windows pops up to confirm. 

![sut_upload_step_4.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_4.png)


### Service Details 

Select service from the list and double-click to show **Service Details**. 

![sut_service_detail_info_window.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window.png)

* Service Information
    * Service Name: Name of service entered for service registration.
    * Service Description: Description of registered service.
    * CDN Address: Address with which CDN is completely integrated.
* Most Recent Uploads 
    * Date and Time: The last upload time and date of resources.
    * Last Registrant: User ID uploading resources.
    * Upload Resource Information: Number and total size of uploaded resources.
        * Detail Information: Uploaded resource information.
    * Build deployment date: The date of the last build deployment, or the date of the scheduled deployment if the deployment status is **Deployment scheduled**.
    * Deployment Status: Check status of deployment. See [Console User Guide](http://docs.toast.com/zh/Game/Smart%20Downloader/zh/console-guide/#4-list-of-services) for deployment status. 
        * Updates: Upload service details.  
        * Build Deployment: To be activated when build is ready to be deployed, with the latest build deployed by CDN. 
* Build Deployment History: Shows the history of the most recent 10 build deployment cases.


#### Build Deployment 

Only when the deployment status is **Ready for Deployment, or Deployment Failed**, the most updated upload resources can be deployed to CDN.  

![sut_service_detail_info_window_deploy1.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window_deploy1.png)

If you click the **Deploy Build** button, the following pop-up window will show up.

![sut_service_detail_info_window_deploy2.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window_deploy2.png)

* Immediate deployment: Attempt deployment immediately.
* Scheduled deployment: Attempt deployment at the time specified by user.

#### Scheduled deployment

If you select **Scheduled deployment**, and the following screen will show up.

![sut_service_detail_info_window_deploy_reservation1.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window_deploy_reservation1.png)

* Time zone: Specify the base time zone for deployment.
* Deployment time: Specify the time to deployment.

If the scheduled deployment time is set to a time before the time of the specified time zone, the deployment is executed immediately, and uploading is restricted until the time set for the scheduled deployment.

![sut_service_detail_info_window_deploy_reservation2.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window_deploy_reservation2.png)

If you specify a scheduled deployment time that is before the current time in the specified time zone, deployment is performed immediately. Uploading is limited until the time set for the scheduled deployment.
Once deployment scheduling is completed, the deployment status changes to **Scheduled** and you can check that the build deployment date/time is changed to the scheduled time.
When the status is **Deployment scheduled**, you can cancel the schedule by clicking the **Cancel deployment** on the right.

### Settings 

![sut_settings.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_settings.png)

* Version information: Shows the version information of Unity Tool. 
* Change the language: Change the language for the tool: Korean, English, and Japanese are supported. 
