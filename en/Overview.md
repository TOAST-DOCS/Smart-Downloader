<!-- pre-align:aligned sig=f2991e90e240 -->

<a id="game-smart-downloader-overview"></a>
## Game > Smart Downloader > Overview { #game-smart-downloader-overview }

The Smart Downloader service supports for downloading resources required to run a game in multi-threads.  
The Client downloads resources and collects statistical data, so as to provide various information.  


<a id="main-features"></a>
## Main Features { #main-features }


<a id="support-for-multi-threaded-downloads"></a>
### Support for Multi-threaded Downloads { #support-for-multi-threaded-downloads }
- Make the most of the network bandwidth for a download. 
- Useful for an environment where the network is not speedy (global) and has a number of files .


<a id="update-revised-file-list-only"></a>
### Update Revised File List Only { #update-revised-file-list-only }
- Updated on the file size- or checksum-basis. 
	- Update is available even for image or text files, for which the content has changed but the size remains (since file checksum changes).  
- After an initial full download, only increments are to be updated. 


<a id="allow-simple-uploads-and-automate-uploadingcreating-deployment-files"></a>
### Allow Simple Uploads and Automate Uploading/Creating Deployment Files { #allow-simple-uploads-and-automate-uploadingcreating-deployment-files }
- Game resources are easily uploaded via console/Jenkins Plugin. 
	- Uploads can be automated by using Jenkins Plugin. 
- With game resources uploaded, deployment files are automatically updated. 


<a id="simplify-downloads-and-updates"></a>
### Simplify Downloads and Updates { #simplify-downloads-and-updates }
- Download can be simply implemented through provided SDK, while the process details are provided. 


<a id="provide-statistics-on-game-downloads"></a>
### Provide Statistics on Game Downloads { #provide-statistics-on-game-downloads }

- Provide real-time download status within 24 hours, as well as daily monitoring indicators 
- Check statistics on successful/failed downloads
- Check download statistics for each country, device, or OS
- Allow search  for download statistics during selected time range (around the time of game deployment)


<a id="glossary"></a>
## Glossary { #glossary }

| Term | Description |
| --- | --- |
| Service | Individual unit of Smart Downloader. |
| Build | Game resources to be downloaded via Smart Downloader SDK: to be managed by each service. |
| Deployment File | Builds uploaded to Smart Downloader automatically create deployment files: to be managed by each service. |
| Internal CDN | CDN which is automatically created within Smart Downloader. |
| External CDN | When there is a CDN already in use, which is not an internal one. |


<a id="structure"></a>
## Structure { #structure }

![그림 1](http://static.toastoven.net/prod_smartdownloader/overview/smartdl_overview_structure_en.png)
<center> [Figure 1] Smart Downloader Structure </center>

<br>

| Component Name | Description |
| --- | --- |
| SDK | A client SDK to use SmartDownloader for a game client. |
| API Server | Processes NHN Cloud authentication and delivers CDN Download URL to a client SDK. |
| Console |	Allows to register Smart Downloader, or to upload or monitor builds. |
| Jenkins Plugin | Provided to directly upload builds on user's build server, not via console. |
