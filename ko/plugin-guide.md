## Game > Smart Downloader > 플러그인 가이드

## Smart Downloader Jenkins Plugin
Smart Downloader Jenkins Plugin 을 통해 Toast Smart Downloader의 **신규 빌드 업로드 기능** 을 편리하게 사용할 수 있습니다.

## Plugin 설치

#### Jenkins 최소 요구사항 버전

**Jenkins 2.145.1** 이후 버전을 요구합니다. 이전 버전 Jenkins에서는 Plugin 기능에 대한 지원이 불가능한 상태이므로 사용 전 버전확인이 필요합니다.

##### 1. Jenkins Plugin 다운로드
아래 링크를 통해 **smartdl-uploader.hpi** 파일을 다운로드 합니다.
Download : [smartdl-uploader.hpi](http://static.toastoven.net/toastcloud/sdk_download/Smart Downloader/smartdl-uploader.hpi)

##### 2. 설치
**[Jenkins] > [Jenkins 관리] > [플러그인 관리] > [고급 탭] > [플러그인 올리기]** 메뉴에서 `1. Jenkins Plugin 다운로드` 를 통해 다운받은 **smartdl-uploader.hpi** 파일을 선택 후 올립니다.

정상적으로 설치가 완료 되면 **설치된 플러그인 목록** 탭에서 아래 [그림 1]와 같이 설치된 내역을 확인할 수 있습니다.

![그림 1](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_01.png)
<center>[그림 1] 설치된 플러그인 목록</center>

## Plugin 사용

##### 사전 준비
Smart Downloader Jenkins Plugin 을 사용하기 위해서는 `Toast API 보안설정` 이 필요합니다.
> Toast API 보안설정 : [https://toast.com/account/api_settings](https://toast.com/account/api_settings)

<br>
##### 1. 인증 설정

**[Jenkins] > [Credentials] > [System]** 메뉴에서 Global credentials 선택 후 Add Credentials 메뉴를 통해 Toast 인증을 추가합니다.
아래 [그림 2] 와 같이 Kind 를 Toast Credentiasls 로 선택 후 Toast UserID, Toast AccessKeyID, Toast SecretKey 를 입력합니다.

![그림 2](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_02.png)
<center>[그림 2] 인증 설정</center>

* Socpe [필수] : Global 선택
* ID : Jenkins 에서 내부적으로 사용하는 Credential ID 값. 미 입력시 자동으로 유니크한 ID 값이 생성됩니다.
* Descreption : 해당 Toast 인증에 대한 설명을 입력할 수 있습니다.
* Toast UserID [필수] : Toast 접속 계정
* Toast AccessKeyID [필수] :  Toast API 보안설정 메뉴에서 발급받은 AccessKeyID
* Toast SecretKey [필수] : Toast API 보안설정 메뉴에서 발급받은 SecretKey

> 참고 : [필수] 로 표시 된 값은 필수 입력 값 입니다. 해당 값이 입력되지 않을 경우 플러그인이 정상적으로 실행되지 않습니다.

<br>
##### 2. 프로젝트 구성
**[Jenkins]** > 프로젝트 선택 > **[구성] > [빌드 후 조치]** 메뉴에서 `SmartDL Uploader` 를 추가 합니다.
아래 [그림 3] 과 같이 설정 값을 입력 합니다.

![그림 3](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_03.png)
<center>[그림 3] 프로젝트 구성</center>

* Toast Credentials [필수] : <b>1.인증설정</b> 을 통해 추가한 Toast Credential 을 선택합니다. 잘못 된 인증키가 입력되었을 경우 인증 실패로 플러그인 사용이 불가합니다.
* Enable Upload [필수] : 플러그인 동작의 활성화 / 비활성화 여부를 결정하는 옵션 값 입니다. 플러그인 설정이 저장 된 상태를 유지하면서 플러그인의 동작을 비활성화 시킬 수 있습니다.
* ProjectID [필수] : Smart Dowonloader 를 사용하는 Toast Project ID. 아래 [그림4] 와 같이 Toast 콘솔 프로젝트 설정 메뉴에서 확인이 가능 합니다.
* Appkey [필수] : Smart Dowonloader Appkey. 아래 [그림5] 와 같이  Toast Smart Dowonloader 콘솔에서 URL & Appkey 화면에서 확인이 가능합니다.
* Service Name [필수] : 신규 빌드 업로드를 처리 할 Smart Dowonloader 서비스 명을 입력합니다.
* Path [필수]  : 업로드할 폴더의 경로를 입력합니다. 폴더 업로드만 지원하며 단일 파일 업로드는 지원하지 않습니다.

> 참고 : [필수] 로 표시 된 값은 필수 입력 값 입니다. 해당 값이 입력되지 않을 경우 플러그인이 정상적으로 실행되지 않습니다.

<br>
![그림 4](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_04.png)
<center>[그림 4] Toast 프로젝트 설정</center>
![그림 5](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_05.png)
<center>[그림 5] Smart Downloader Appkey 확인</center>

<br>
##### 3. 결과 확인
프로젝트 빌드 후 로그를 통해 Plugin 실행 결과를 확인할 수 있습니다.
성공시에는 업로드에 성공한 파일 내역 및 총 업로드 파일 개수, 총 용량, 완료시간, 소요시간 등의 정보를 확인하실 수 있습니다.
업로드 중 로그를 확인하시면 현재 업로드중인 파일 정보를 실시간으로 확인하실 수도 있습니다.

![그림 6](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_06_01.png)
![그림 6](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_06_02.png)
<center>[그림 6] 콘솔 로그</center>

또한 Smart Downloader 콘솔 내 `서비스 상세정보` 페이지에서 빌드 업로드 이력을 확인할 수 있습니다.
Plugin 을 통해 빌드 업로드 시 Last Uploader 에 Plugin에 등록한 Toast UserID 가 표시됩니다.

![그림 7](http://static.toastoven.net/prod_smartdownloader/jenkins_plugin/jenkinsplugin_img_07_v2.png)
<center>[그림 7] 서비스 상세 정보</center>

Plugin 실행 결과가 실패 일 경우 콘솔 로그의 에러메세지를 참고해주세요.

