## Game > Smart Downloader > Unity Tool 사용 가이드

## 시작하기

Smart Downloader Unity Tool(SUT)은 Unity에서 리소스를 업로드하고 배포할 수 있는 툴입니다.

### Environments

#### Unity Supported Versions

* 2018.4.0 ~ 2021.1.20

### Download

[Smart Downloader Unity Tool](/Download/#game-smart-downloader)


### Unity Tool 설치

1. Unity 프로젝트를 엽니다.
2. Unity에서 **Assets > Import Package > Custom Package**를 선택합니다.
3. 다운로드한 Unity Tool 파일 'Smart-downloader-unity-tool-{Version}.unitypackage'를 선택한 후 가져옵니다.
    ![sut_import.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_import.png)

## Unity Tool 사용

Unity Tool을 사용하려면 메뉴에서 **Tool > NHN Cloud > Smart Downloader > Unity Tool**을 선택합니다.

### 인증

인증 전이라면 **인증** 탭이 나타납니다.

![sut_credentials_tab.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_credentials_tab.png)

* User ID: NHN Cloud 클라우드 ID
* User Access Key ID, Secret Access Key
    1. [API 보안 설정](https://console.toast.com/securitySetting)에서 **User Access Key ID 생성**을 선택합니다.
    2. 생성 대화 상자가 나타나면 **User Access Key ID와 Secret Access Key 생성**을 선택합니다.
    3. Secret Access Key(비밀 키) 발급 완료 대화 상자가 나타납니다.
    4. API 보안 설정 페이지에서 발급된 User Access Key ID 정보와 상태 정보를 확인합니다.

    > [주의]
    > - User Access Key ID는 90일마다 변경하기를 권장합니다.
    > - User Access Key ID는 NHN Cloud ID당 5개, IAM ID당 5개까지 생성 가능합니다.
    > - Secret Access Key는 다시 확인할 수 없으며 잃어버린 경우 재생성해야 합니다. 발급 시 안전한 장소에 보관하시기 바랍니다.

* Project ID
    * Smart Downloader를 이용 중인 프로젝트 ID로, 콘솔의 **프로젝트 설정**에서 확인할 수 있습니다.
    ![console_project_id.png](https://static.toastoven.net/prod_smartdownloader/sut/console_project_id.png)


### 서비스 조회

인증이 완료되면 **업로드** 탭이 나타납니다.
**Appkey**란에 앱키를 입력하고 **조회**를 클릭하면 콘솔에서 생성된 서비스 목록이 나타납니다.

![sut_upload_tab_base.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_tab_base.png)

* Appkey
    * 콘솔의 Smart Downloader 서비스에서 **URL & Appkey**를 클릭하여 발급된 앱키를 확인합니다.
    ![console_appkey.png](https://static.toastoven.net/prod_smartdownloader/sut/console_appkey.png)

### 리소스 업로드

#### 1. 서비스 선택

서비스 목록에서 업로드할 서비스를 클릭하고 리소스 경로를 선택합니다.
올바른 경로를 선택하면 **업로드** 버튼이 활성화됩니다.

![sut_upload_step_1.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_1.png)

#### 2. 업로드 리소스 선택

마지막으로 업로드된 리소스와 선택한 경로의 리소스를 비교하여 변경된 리소스의 정보를 표시합니다.
업로드할 리소스를 선택하면 **업로드** 버튼이 활성화됩니다.

> 주의
OS에서 자동으로 생성하는 파일(.DS_Store, desktop.ini, thumbs.db)은 제외됩니다.
리소스 하나의 최대 크기는 5GB로 제한됩니다.

![sut_upload_step_2.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_2.png)

#### 3. 리소스 업로드 진행

업로드 진행 상황을 표시합니다.
업로드 진행 중에 툴을 종료하면 업로드 취소 여부를 묻는 창이 나타납니다.

> 주의
업로드 중에는 Unity를 강제로 종료하지 마십시오.
강제로 종료하면 업로드 상태로 남게 되며 30분 후 업로드 실패로 변경됩니다.

![sut_upload_step_3.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_3.png)


#### 4. 완료

정상적으로 완료되면 확인 창이 나타납니다.

![sut_upload_step_4.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_4.png)


### 서비스 상세 정보

서비스 목록에서 서비스를 선택해 더블클릭하면 **서비스 상세 정보** 화면이 나타납니다.

![sut_service_detail_info_window.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window.png)

* 서비스 정보
    * 서비스 이름: 서비스 등록 시 입력한 서비스 이름입니다.
    * 서비스 설명: 등록된 서비스 설명입니다.
    * CDN 주소: CDN 연결이 완료된 주소입니다.
* 최신 업로드 정보
    * 업로드 일시: 리소스를 마지막으로 업로드한 일시입니다.
    * 최종 등록자: 리소스를 업로드한 User ID입니다.
    * 업로드 리소스 정보: 업로드된 리소스의 개수와 총 크기입니다.
        * 상세 정보: 업로드된 리소스 정보입니다.
    * 빌드 배포 일시: 마지막으로 빌드 배포된 일시입니다. 배포 상태가 **배포 예약 중** 상태인 경우 예약 배포되는 일시입니다.
    * 배포 상태: 배포 상태를 확인할 수 있습니다. 배포 상태는 [콘솔 사용 가이드](http://docs.toast.com/ko/Game/Smart%20Downloader/ko/console-guide/#4)를 참고하시기 바랍니다.
        * 갱신: 서비스의 상세 정보를 갱신합니다.
        * 빌드 배포: 빌드를 배포할 수 있는 상태가 되면 활성화되며 최신 빌드를 CDN으로 배포할 수 있습니다.
* 빌드 배포 이력: 빌드 배포를 진행한 최근 10건의 이력이 표시됩니다.


#### 빌드 배포

배포 상태가 **배포 대기**, **배포 실패** 상태인 경우에만 최신 업로드 리소스를 CDN에 배포할 수 있습니다.

![sut_service_detail_info_window_deploy1.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window_deploy1.png)

**빌드 배포** 버튼을 누르면 아래와 같은 창이 출력됩니다.

![sut_service_detail_info_window_deploy2.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window_deploy2.png)

* 즉시 배포 : 지금 즉시 배포를 시도합니다.
* 예약 배포 : 사용자가 지정한 시간에 배포를 시도합니다.

#### 예약 배포

**예약 배포** 를 선택하면 아래와 같은 화면이 출력됩니다.

![sut_service_detail_info_window_deploy_reservation1.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window_deploy_reservation1.png)

* 시간대 : 배포할 기준 시간대를 지정합니다.
* 배포 시간 : 배포 시간을 지정합니다.

예약 배포 시간을 지정한 시간대 이전의 시간으로 지정한 경우 즉시 배포가 실행되며, 예약 배포로 설정된 시간까지는 업로드가 제한됩니다.

![sut_service_detail_info_window_deploy_reservation2.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_window_deploy_reservation2.png)

배포 예약이 완료되면 배포 상태가 **예약 상태 중** 으로 변경되며 빌드 배포 일시가 예약된 시간으로 변경됨을 확인하실 수 있습니다.
**배포 예약 중** 상태에서는 우측에 **배포 취소** 버튼을 눌러 예약을 취소할 수 있습니다.


### 설정

![sut_settings.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_settings.png)

* 버전 정보: Unity Tool 버전 정보를 표시합니다.
* 언어 변경: 툴의 언어를 변경합니다. 지원 언어는 한국어, 영어, 일본어입니다.