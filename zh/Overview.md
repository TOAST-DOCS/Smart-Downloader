## Game > Smart Downloader > Overview

The Smart Downloader service supports for downloading resources required to run a game in multi-threads.  
The Client downloads resources and collects statistical data, so as to provide various information.  


## Main Features 


### Support for Multi-threaded Downloads 
- Make the most of the network bandwidth for a download. 
- Useful for an environment where the network is not speedy (global) and has a number of files .


### Update Revised File List Only 
- Updated on the file size- or checksum-basis. 
	- Update is available even for image or text files, for which the content has changed but the size remains (since file checksum changes).  
- After an initial full download, only increments are to be updated. 


### Allow Simple Uploads and Automate Uploading/Creating Deployment Files 
- Game resources are easily uploaded via console/Jenkins Plugin. 
	- Uploads can be automated by using Jenkins Plugin. 
- With game resources uploaded, deployment files are automatically updated. 


### Simplify Downloads and Updates 
- Download can be simply implemented through provided SDK, while the process details are provided. 


### Provide Statistics on Game Downloads 

- Provide real-time download status within 24 hours, as well as daily monitoring indicators 
- Check statistics on successful/failed downloads
- Check download statistics for each country, device, or OS
- Allow search  for download statistics during selected time range (around the time of game deployment)


## Glossary 

| Term | Description |
| --- | --- |
| Service | Individual unit of Smart Downloader. |
| Build | Game resources to be downloaded via Smart Downloader SDK: to be managed by each service. |
| Deployment File | Builds uploaded to Smart Downloader automatically create deployment files: to be managed by each service. |
| Internal CDN | CDN which is automatically created within Smart Downloader. |
| External CDN | When there is a CDN already in use, which is not an internal one. |


## Structure 

###### ![그림 1](http://static.toastoven.net/prod_smartdownloader/overview/smartdl_overview_structure_en.png)
<center> [Figure 1] Smart Downloader Structure </center>

<br>

| Component Name | Description |
| --- | --- |
| SDK | A client SDK to use SmartDownloader for a game client. |
| API Server | Processes NHN Cloud authentication and delivers CDN Download URL to a client SDK. |
| Console |	Allows to register Smart Downloader, or to upload or monitor builds. |
| Jenkins Plugin | Provided to directly upload builds on user's build server, not via console. |
