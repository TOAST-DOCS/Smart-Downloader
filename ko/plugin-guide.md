## Game > Smart Downloader > 플러그인 가이드

## Smart Downloader Jenkins Plugin
Smart Downloader Jenkins Plugin 을 통해 NHN Cloud Smart Downloader의 **신규 빌드 업로드 기능** 을 편리하게 사용할 수 있습니다.

## Plugin 설치

#### Jenkins 최소 요구사항 버전

**Jenkins 2.145.1** 이후 버전을 요구합니다. 이전 버전 Jenkins에서는 Plugin 기능에 대한 지원이 불가능한 상태이므로 사용 전 버전확인이 필요합니다.

##### 1. Jenkins Plugin 다운로드
아래 링크를 통해 **smartdl-uploader.hpi** 파일을 다운로드 합니다.
Download : [smartdl-uploader.hpi](https://static.toastoven.net/toastcloud/sdk_download/Smart Downloader/smartdl-uploader.hpi)

##### 2. 설치
**[Jenkins] > [Jenkins 관리] > [플러그인 관리] > [고급 탭] > [플러그인 올리기]** 메뉴에서 `1. Jenkins Plugin 다운로드` 를 통해 다운받은 **smartdl-uploader.hpi** 파일을 선택 후 올립니다.

정상적으로 설치가 완료 되면 **설치된 플러그인 목록** 탭에서 아래 [그림 1]와 같이 설치된 내역을 확인할 수 있습니다.

![그림 1](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_01.png)
<center>[그림 1] 설치된 플러그인 목록</center>

## Plugin 사용

##### 사전 준비
Smart Downloader Jenkins Plugin 을 사용하기 위해서는 `NHN Cloud API 보안설정` 이 필요합니다.
> NHN Cloud API 보안설정 : [https://console.toast.com/securitySetting](https://console.toast.com/securitySetting)


##### 1. 인증 설정

**[Jenkins] > [Credentials] > [System]** 메뉴에서 Global credentials 선택 후 Add Credentials 메뉴를 통해 NHN Cloud 인증을 추가합니다.
아래 [그림 2] 와 같이 Kind 를 NHN Cloud Credentials 로 선택 후 NHN Cloud UserID, NHN Cloud AccessKeyID, NHN Cloud SecretKey 를 입력합니다.

![그림 2](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_02.png)
<center>[그림 2] 인증 설정</center>

* Scope [필수] : Global 선택
* ID : Jenkins 에서 내부적으로 사용하는 Credential ID 값. 미 입력시 자동으로 유니크한 ID 값이 생성됩니다.
* Description : 해당 NHN Cloud 인증에 대한 설명을 입력할 수 있습니다.
* NHN Cloud UserID [필수] : NHN Cloud 접속 계정
* NHN Cloud AccessKeyID [필수] :  NHN Cloud API 보안설정 메뉴에서 발급받은 AccessKeyID
* NHN Cloud SecretKey [필수] : NHN Cloud API 보안설정 메뉴에서 발급받은 SecretKey

> 참고 : [필수] 로 표시 된 값은 필수 입력 값 입니다. 해당 값이 입력되지 않을 경우 플러그인이 정상적으로 실행되지 않습니다.


##### 2. 프로젝트 구성
**[Jenkins]** > 프로젝트 선택 > **[구성] > [빌드 후 조치]** 메뉴에서 `SmartDL Uploader` 를 추가 합니다.
아래 [그림 3] 과 같이 설정 값을 입력 합니다.

![그림 3](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_03.png)
<center>[그림 3] 프로젝트 구성</center>

* NHN Cloud Credentials [필수] : <b>1.인증설정</b> 을 통해 추가한 NHN Cloud Credential 을 선택합니다. 잘못 된 인증키가 입력되었을 경우 인증 실패로 플러그인 사용이 불가합니다.
* Enable Upload [필수] : 플러그인 동작의 활성화 / 비활성화 여부를 결정하는 옵션 값 입니다. 플러그인 설정이 저장 된 상태를 유지하면서 플러그인의 동작을 비활성화 시킬 수 있습니다.
* ProjectID [필수] : Smart Downloader 를 사용하는 NHN Cloud Project ID. 아래 [그림4] 와 같이 NHN Cloud 콘솔 프로젝트 설정 메뉴에서 확인이 가능 합니다.
* Appkey [필수] : Smart Downloader Appkey. 아래 [그림5] 와 같이  NHN Cloud Smart Downloader 콘솔에서 URL & Appkey 화면에서 확인이 가능합니다.
* Service Name [필수] : 신규 빌드 업로드를 처리 할 Smart Downloader 서비스 명을 입력합니다.
* Path [필수]  : 업로드할 폴더의 경로를 입력합니다. 폴더 업로드만 지원하며 단일 파일 업로드는 지원하지 않습니다. 해당 폴더는 jenkins 내의 workspace 폴더 아래에 위치해야 합니다.

> 참고 : [필수] 로 표시 된 값은 필수 입력 값 입니다. 해당 값이 입력되지 않을 경우 플러그인이 정상적으로 실행되지 않습니다.


![그림 4](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_04.png)
<center>[그림 4] NHN Cloud 프로젝트 설정</center>
![그림 5](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_05.png)
<center>[그림 5] Smart Downloader Appkey 확인</center>

> **업로드시 유의사항**
> - OS 에서 자동으로 생성하는 파일 (.DS_Store, desktop.ini, thumbs.db) 은 업로드 시 제외됩니다. 
> - 업로드 시 최대 용량은 5GB 로 제한합니다.



##### 3. 결과 확인
프로젝트 빌드 후 로그를 통해 Plugin 실행 결과를 확인할 수 있습니다.
성공시에는 업로드에 성공한 파일 내역 및 총 업로드 파일 개수, 총 용량, 완료시간, 소요시간 등의 정보를 확인하실 수 있습니다.
업로드 중 실시간 로그를 확인하실 경우 현재 업로드중인 파일 정보를 확인할 수 있도록 실시간으로 로그가 남고 있으므로 진행상황을 보다 더 쉽게 확인하실 수 있습니다.

![그림 6](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_06_v2.png)
<center>[그림 6] 콘솔 로그</center>

또한 Smart Downloader 콘솔 내 `서비스 상세정보` 페이지에서 빌드 업로드 이력을 확인할 수 있습니다.
Plugin 을 통해 빌드 업로드 시 Last Uploader 에 Plugin에 등록한 NHN Cloud UserID 가 표시됩니다.

![그림 7](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_07_v2.png)
<center>[그림 7] 서비스 상세 정보</center>

Plugin 실행 결과가 실패일 경우 콘솔 로그의 에러 메세지를 참고하신 후 담당자에게 문의해 주시면 됩니다.

#### Pipeline 환경설정
Smart Downloader Plugin의 설치와 설정은 위와 동일하게 진행하되, [2. 프로젝트 구성(그림 3 참고)]의 '빌드 후 조치' 설정 대신 Pipeline 설정을 진행합니다.
**[Jenkins]** > 프로젝트 선택 > **[구성]** > **[Pipeline]** 메뉴에서 아래의 스크립트 내용을 마지막에 추가합니다.

![그림 8](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_08_1_pipeline.png)
<center>[그림 8] Pipeline 설정 참고</center>

```shell
node() {
    stage ('Smart Downloader'){
    step([$class:'BuildUploaderPublisher',
        credentialsId: '<NHN Cloud Credentials>',
        projectId: '<NHN Cloud Project ID>',
        appkey: '<Smart Downloader Appkey>',
        serviceName: '<Smart Downloader 서비스명>',
        path: '<업로드할 폴더의 경로>',
        enableUpload: 'enable'
    ])
    }
}
```

항목의 자세한 설정값은 위의 [2.프로젝트 구성] 항목의 [그림3]과 설명을 참고해 주시기 바랍니다.

## 참고사항
Jenkins에서 Master/Slave node를 구성하여 사용하는 경우 **반드시 Node 정보를 설정**해 주시기 바랍니다.

![그림 9-1](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_09_1.png)
<center>[그림 9-1] Node 설정 참고 1 </center>

![그림 9-2](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_09_2.png)
<center>[그림 9-2] Node 설정 참고 2 </center>

![그림 9-3](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_09_3.png)
<center>[그림 9-3] Node 설정 참고 3 - Pipeline 설정 </center>

* Node 설정은 각 프로젝트의 구성에 맞게 설정하여 사용하시기 바랍니다.
