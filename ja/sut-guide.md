## Game > Smart Downloader > Unity Tool 가이드

## 시작하기

Smart Downloader Unity Tool(SUT)은 유니티에서 리소스를 업로드하고 배포하는 기능을 제공합니다.

### Environments

#### Unity Supported Versions

* 5.6.6 ~ 2019.1.4

### Download

[Smart Downloader Unity Tool](/Download/#game-smart-downloader)


### Unity Tool 설치

1. 유니티 프로젝트를 엽니다.
2. 유니티에서 [Assets > Import Package > Custom Package]를 선택합니다.
3. 다운로드한 Unity Tool 파일 'Smart-downloader-unity-tool-{Version}.unitypackage'을 선택한 후 임포트 합니다.
    ![sut_import.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_import.png)

## Unity Tool 사용하기

유니티 메뉴 `Tool > Toast > Smart Downloader > Unity Tool`을 선택하면 툴이 열립니다.

### 인증

인증이 되어 있지 않으면 [인증 탭] 화면으로 연결됩니다.

![sut_credentials_tab.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_credentials_tab.png)

* User ID : TOAST Cloud ID
* User Access Key ID, Secret Access Key
    1. [API 보안 설정](https://toast.com/account/api_settings)에서 `User Access Key ID 발급`을 선택합니다.
    2. Secret Access Key(비밀 키) 발급 완료 팝업이 출력됩니다.
    3. API 보안 설정 페이지를 다시 확인하면 발급된 User Access Key ID 정보와 상태 정보를 확인합니다.
    ![console_api_security_setting.png](https://static.toastoven.net/prod_smartdownloader/sut/console_api_security_setting.png)
* Project ID
    * Smart Downloader를 이용중인 프로젝트 ID로 Console의 프로젝트 설정에서 확인합니다.
    ![console_project_id.png](https://static.toastoven.net/prod_smartdownloader/sut/console_project_id.png)
        

### 서비스 조회

인증이 완료되면 [업로드 탭] 화면으로 연결됩니다.
Appkey 항목을 입력하고 [조회]를 클릭하면 Console에서 생성된 서비스 목록이 출력됩니다.

![sut_upload_tab_base.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_tab_base.png)

* Appkey
    * Console에 Smart Downloader 서비스에서 URL & Appkey를 클릭하여 발급된 Appkey를 확인합니다.
    ![console_appkey.png](https://static.toastoven.net/prod_smartdownloader/sut/console_appkey.png)

### 리소스 업로드

#### 1. 서비스 선택

서비스 목록에서 업로드 할 서비스를 클릭하고 리소스 경로를 선택합니다.
올바른 경로가 선택되면 [업로드] 버튼이 활성화 됩니다.

![sut_upload_step_1.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_1.png)

#### 2. 업로드 리소스 선택

마지막으로 업로드된 리소스와 선택한 경로의 리소스를 비교하여 변경된 리소스의 정보를 표시합니다.
업로드할 리소스를 선택하면 [업로드] 버튼이 활성화 됩니다.

> 주의사항
OS에서 자동으로 생성하는 파일(.DS_Store, desktop.ini, thumbs.db) 제외됩니다.
리소스 하나의 최대 크기는 5GB로 제한됩니다.

![sut_upload_step_2.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_2.png)

#### 3. 리소스 업로드 진행

업로드 진행 상황을 출력합니다.
업로드 진행 중에 툴을 종료한다면 업로드 취소 여부를 묻는 확인 팝업이 출력됩니다.

> 주의
업로드 중에는 유니티를 강제로 종료하지 마십시오.
강제 종료를 하면 업로드 상태로 남게 되며 30분 후 업로드 실패로 변경됩니다.

![sut_upload_step_3.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_3.png)


#### 4. 완료

정상적으로 완료되면 확인 팝업이 출력됩니다.

![sut_upload_step_4.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_upload_step_4.png)


### 서비스 상세 정보

서비스 목록에서 서비스를 선택해 더블클릭하면 [서비스 상세 정보] 화면이 출력됩니다.

![sut_service_detail_info.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info.png)

* 서비스 정보
    * 서비스 이름 : 서비스 등록 시 입력한 서비스 이름을 표시합니다.
    * 서비스 설명 : 등록된 서비스 설명을 표시합니다.
    * CDN 주소 : CDN 연결이 완료되었다면 출력됩니다.
* 최신 업로드 정보
    * 업로드 일시 : 마지막으로 업로드된 일시입니다.
    * 최종 등록자 : 리소스를 업로드한 User ID가 표시합니다.
    * 업로드 리소스 정보 : 업로드된 리소스의 개수와 총 크기를 표시합니다.
        * 상세 정보 : 업로드된 리소스 정보를 보여줍니다.
    * 배포 상태 : 배포 상태를 확인할 수 있습니다. 배포 상태 정보는 [콘솔 사용 가이드](http://alpha-docs.toast.com/ko/Game/Smart%20Downloader/ko/console-guide/#4)를 참고 바랍니다.
        * 갱신 : 서비스의 상세 정보를 갱신합니다.
        * 빌드 배포 : 빌드를 배포할 수 있는 상태가 되면 활성화 되며 최신 빌드를 CDN으로 배포할 수 있습니다. 
* 빌드 배포 이력 : 빌드 배포를 진행한 최근 10건의 이력을 표시합니다.


#### 빌드 배포

![sut_service_detail_info_deploy.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_service_detail_info_deploy.png)

* 배포 상태가 `배포 대기`, `배포 실패` 상태인 경우에만 최신 업로드 리소스를 CDN에 배포할 수 있습니다.

### 설정

![sut_settings.png](https://static.toastoven.net/prod_smartdownloader/sut/sut_settings.png)

* 버전 정보 : Unity Tool 버전 정보를 표시합니다.
* 언어 변경 : 툴의 언어를 변경합니다. (지원 언어 : 한국어, 영어, 일본어)