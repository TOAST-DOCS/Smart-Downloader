## Game > Smart Downloader > Plugin Guide 

## Smart Downloader Jenkins Plugins
With Smart Downloader Jenkins Plugin, **Uploading New Builds** of NHN Cloud Smart Downloader can be applied more easily.    

## Installing Plugin 

#### Minimum Requirements for Jenkins 

**Jenkins 2.60.1** or later version is required.  
Jenkins 2.60.1 is the first release of Jenkins Long-term Support (LTS) enabled for Java 8. 

> See: [https://jenkins.io/changelog-stable](https://jenkins.io/changelog-stable)

##### 1. Download Jenkins Plugin
Go to the below link and download **smartdl-uploader.hpi**.  
To download : [smartdl-uploader.hpi](http://static.toastoven.net/toastcloud/sdk_download/Smart Downloader/smartdl-uploader.hpi)

##### 2. Install 
Go to **[Jenkins] > [Manage Jenkins] > [Plugin Management] > [Advanced Tab] > [Uploading Plugins]**, select and upload the **smartdl-uploader.hpi** file downloaded from  `1.Download Jenkins Plugin`.

When it is properly installed, the installation can be found on the tab of **List of Installed Plugins** as in the below [Figure 1]. 

![그림 1](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_01.png)
<center> [Figure 1] List of Installed Plugins </center>

## Using Plugin 

##### Prerequisites 
To use Smart Downloader Jenkins Plugin,  `NHN Cloud API Security Configuration` is required.
> NHN Cloud API Security Configuration: [https://toast.com/account/api_settings](https://toast.com/account/api_settings)

<br>
##### 1. Set Authentication 

From **[Jenkins] > [Credentials] > [System]**, select  Global Credentials and go to Add Credentials to add NHN Cloud Credentials. 
Select NHN Cloud Credentials for Kind like [Figure 2] as below, and enter NHN Cloud User ID, NHN Cloud AccessKeyID, and NHN Cloud SecretKey.  

![그림 2](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_02.png)
<center>[Figure 2] Authentication Setting </center>

* Scope [Required]: Choose Global 
* ID: Credential ID value used within Jenkins. If it is left blank, a unique ID is automatically created. 
* Description: Enter description for NHN Cloud authentication. 
* NHN Cloud UserID [Required]: Account for NHN Cloud access 
* NHN Cloud AccessKeyID [Required]: AccessKeyID issued from NHN Cloud API Security Configuration
* NHN Cloud SecretKey [Required]: SecretKey issued from NHN Cloud API Security Configuration

> Note: [Required] means a value is required to enter. If it is left blank, Plugin cannot be properly executed. 

<br>
##### 2. Configure Project  
On **[Jenkins]** > Select Projects > **[Configuration] > [Build and Process]**, add `SmartDL Uploader`.
Enter values as in [Figure 3]. 

![그림 3](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_03.png)
<center> [Figure 3] Project Configuration </center>

* NHN Cloud Credentials [Required]: <b> 1. Select the NHN Cloud Credential added from Authentication Setting </b>. If authentication key is wrong, authentication fails, and Plugin cannot be enabled. 
* Enable Upload [Required]: Determines whether Plugin activities are enabled or disabled. Plugin activities may be disabled while the setting remains as saved. 
* ProjectID [Required]: NHN Cloud Project ID for Smart Dowonloader. It is available in the NHN Cloud Console Project Setting, like in [Figure 4] as below.   
* Appkey [Required]: Smart Dowonloader Appkey. It is available on the URL & Appkey page in the NHN Cloud Smart Downloader Console, like in [Figure 5] as below. 
* Service Name [Required]: Enter name of Smart Downloader service to process new build uploads. 
* Path [Required]: Enter path of the folder to upload. Supports uploads only by the folder, not by the single file.

> Note: [Required] means a value is required to enter. If it is left blank, Plugin cannot be properly executed.

<br>
![그림 4](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_04.png)
<center> [Figure 4] NHN Cloud Project Configuration </center>
![그림 5](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_05.png)
<center> [Figure 5] Check Smart Downloader Appkey </center>

<br>
##### 3. Check Result 
After a project build, Plugin execution results can be found through logs.  

![그림 6](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_06.png)
<center> [Figure 6] Console Logs </center>

Build upload history is also available on the `Service Detail Information` page in the Smart Downloader console. 
When build is uploaded through Plugin, the server IP which executed Plugin to Last Uploader is displayed. 

![그림 7](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_07.png)
<center> [Figure 7] Service Detail Information </center>

When Plugin execution results in failure, see error messages in console logs.  

