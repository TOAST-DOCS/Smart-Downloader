## Game > Smart Downloader > Console Guide

Smart Downloader 사용을 위해서 서비스 활성화 후 서비스를 등록해야 합니다.
서비스 등록은 \[서비스 등록\] > \[CDN 연동\] > \[리소스 업로드\] 3단계 Wizard 형식으로 구성되어 있습니다. 3단계 서비스 등록 Wizard 후 \[빌드 배포\] 까지 모두 완료되어야 SDK 를 통해 배포본을 다운로드할 수 있습니다.
서비스 등록 후 해당 서비스에 대한 실시간 다운로드 현황 및 다운로드 지표 데이터를 다양한 형태의 차트로 제공하며 데이터를 다운로드 할 수 있습니다.
<br>

## Configuration

### Smart Downloader 서비스 활성화
Console 페이지 상단의 **서비스 선택** 버튼을 클릭 후, Game 하위 Smart Downloader 서비스를 클릭하여 서비스 활성화 합니다.

![project_enabeld.png](http://static.toastoven.net/prod_smartdownloader/web_console/project_enabled.png)

### AppKey 와 URL 확인
Console 페이지 상단의 URL & Appkey 를 클릭하여 발급된 Appkey를 확인합니다. 해당 Appkey는 SDK 에 입력하여 사용하게 됩니다.
Smart Downloader 서비스 비활성화 시, 발급된 Appkey는 복구되지 않으니 주의하시기 바랍니다.

![smartdl_01_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_01_201812.png)

## 서비스 관리 Tab

### 1. 서비스 등록
#### 1.1 서비스 등록
![smartdl_02_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_02_201812.png)

- 서비스 이름
    - 서비스를 구분할 수 있는 식별값으로 **필수 입력** 입니다.
    - 서비스 이름은 식별값으로 사용되기 때문에 한 프로젝트에 동일한 서비스 이름으로 1개 이상 등록할 수 없습니다.
    - **영문 소문자, 숫자와 특수기호 (_),(-)** 만 사용 가능하며 첫 문자는 **영문 소문자나 숫자**로 시작해야 합니다.
    - 공백으로 시작할 수 없습니다.
    - 최대 30Byte로 입력을 제한합니다.

- 서비스 설명
	- 서비스에 대한 부연 설명값을 입력합니다. 최대 100Byte로 입력을 제한합니다.

- 서비스 등록이 완료되면 \[1단계. 서비스 등록 완료\] 페이지로 이동합니다.

#### 1.2 서비스 등록 완료 
![smartdl_03_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_03_201812.png)

- 등록된 서비스 이름과 설명을 확인할 수 있습니다. \[다음\] 버튼 클릭 시 서비스 등록 Wizard의 2 단계인 \[CDN 연동\] 단계로 이동합니다.

### 2. CDN 연동
#### 2.1 CDN 연동 안내

![smartdl_04_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_04_201812.png)

- 2.1.1 Smart Downloader CDN 연동 선택
	- \[CDN 서비스 생성\] 팝업을 통해 CDN 설정 정보를 입력합니다.
		![smartdl_05_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_05_201812.png)
		- Service
			- 서비스 지역 : CDN의 적용 범위에 대해서 선택하는 항목입니다. 서비스 대상 국가에 따라 Korea / Global 중 선택하시면 되며, 기본값은 Korea입니다.
			- 설명 : CDN에 대한 간략한 설명을 작성하는 항목입니다.
		- Cache
			- Cache 만료 설정 : CDN에 저장되어 있는 파일들을 신규 파일로 교체할 주기를 선택하는 항목입니다. 기본 24시간으로 지정되어 있으며, 필요에 따라서 임의로 설정이 필요한 경우 **사용자 설정 사용**을 선택하면 됩니다.
			- Cache 만료 설정(초) : **Cache 만료 설정**에서 **사용자 설정 사용**을 선택한 경우 CDN의 Cache 주기를 입력하는 항목입니다. (기본설정을 사용하는 경우 입력 불가)
			- Referrers 접근 관리 : CDN에 대한 접근 제한을 어떤 형태로 할 것인지 선택하는 항목입니다. **Blacklist**의 경우 입력한 Referrers만 접근 제한되며, **Whitelist**의 경우 입력한 Referrers만 접근 가능합니다.
			- Referrers : 접근 제한할 Referrer를 입력하기 위한 항목입니다. Regular Expression를 지원하며, 여러개의 Referrer를 입력하기 위해서는 줄을 바꾼후에 입력하시면 됩니다.
	- Smart Downloader CDN 연동은 최대 약 1분의 소요시간이 발생합니다.

- 2.1.2 고객사 CDN 연동 선택
	- \[안내\] 팝업이 나타나며 고객사 CDN 이용을 위한 Step1, Step2 를 진행합니다.
    ​   ![smartdl_06_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_06_201812.png)
	    - Step 1
	        - **원본 서버 주소로 적용할 URL** 을 제공합니다.
	    - Strep 2
    	    - **사용할 CDN URL** 을 입력하여 Smart Downloader 서비스와 고객사 CDN 이 연동되도록 설정합니다.
	        - 고객사 CDN URL은 HTTP/HTTPS 프로토콜을 선택해서 입력합니다.

#### 2.2 CDN 연동 완료

![smartdl_07_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_07_201812.png)

- 등록된 CDN 서버 주소 및 원본 서버 URL을 확인할 수 있습니다. \[다음\] 버튼 클릭 시 서비스 등록 Wizard의 3 단계인 \[리소스 업로드\] 단계로 이동합니다.

### 3. 리소스 업로드
- 리소스 업로드는 폴더 업로드를 원칙으로 합니다. (업로드 버튼 클릭 시, 폴더 찾아보기 윈도우가 로딩됩니다)
- OS 에서 자동으로 생성하는 파일 (.DS_Store, desktop.ini, thumbs.db) 은 업로드 시 제외됩니다. 
- 리소스 하나의 최대 용량은 5GB 로 제한합니다.
- Internet Explorer 브라우저는 리소스 업로드 기능을 제공하지 않습니다. 리소스 업로드는 Chrome 브라우저를 사용하시기 바랍니다.

#### 3.1 리소스 업로드 안내

![smartdl_08_202012.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_08_202012.png)

- A. 로컬 기기 업로드
​    - Console 페이지를 통해 사용자 Local PC 에 있는 리소스를 업로드 할 수 있습니다.
​    - 현재 페이지에서 \[리소스 업로드\] 버튼 클릭으로 진행할 수 있습니다.
​    - 업로드가 완료되면 \[3단계. 리소스 업로드 완료\] 페이지로 이동합니다.
- B.  빌드 서버(원격) 업로드
​    - Smart Downloader Jenkins Plugin(NHN CloudCloud Smart Downloader Plugin) 을 통해 리소스를 업로드.
​    - NHN CloudCloud Smart Downloader Plugin 에 대한 자세한 가이드는 [플러그인 사용 가이드](http://docs.toast.com/ko/Game/Smart%20Downloader/ko/plugin-guide/) 로 확인할 수 있습니다.
- C. 유니티 에디터 플러그인 업로드
    - 유니티 에디터로 수정하고 빌드한 리소스 파일을 에디터에 내장된 플러그인을 통해 업로드.
        - 유니티 에디터 플러그인에 대한 자세한 가이드는 [Unity Tool 사용 가이드](https://docs.toast.com/ko/Game/Smart%20Downloader/ko/sut-guide/)로 확인할 수 있습니다.

#### 3.2 리소스 업로드 완료

![smartdl_09_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_09_201812.png)

- 서비스 이름
    - 등록된 서비스 이름입니다.

- 리소스 업로드 정보
	- 업로드 된 리소스 파일 개수와 전체 파일 크기를 보여줍니다.
	- 상세 정보 버튼 클릭 시 업로드 된 리소스 정보가 Tree 형태 팝업으로 노출됩니다.

- 최종 업로드
    - 최신 리소스가 업로드 된 마지막 업로드 일시입니다.
    
- 배포 상태
    - 리소스의 현재 상태를 보여줍니다.
    - 배포 대기 상태인 경우, \[서비스 관리\] - \[서비스 상세\] 페이지에서 \[빌드 배포\] 버튼을 통해 배포할 수 있습니다.

**\[리소스 업로드 취소 기능\]**

![smartdl_10_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_10_201812.png)

- Smart Downloader 는 업로드 진행 중 업로드를 취소하는 기능을 제공합니다.
- 업로드 취소 기능이 완료되면 배포 상태는 업로드 하기 전 상태로 되돌아 가는 점 유의하시기 바랍니다.

### 4. 서비스 목록
사용자가 등록한 서비스의 목록을 한번에 10개씩 보여줍니다. 각 서비스 열 클릭 시, 해당 서비스에 대한 \[서비스 상세 정보\] 페이지로 이동합니다.

![smartdl_11_202012.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_11_202012.png)

- 서비스 이름
  
    - 서비스 등록 시 사용자가 입력한 서비스 이름.
    
- CDN
    - 서버 : CDN download URL. (CDN download URL 이 등록되어 있지 않는 경우에 \[CDN URL 입력이 필요합니다.\] 문구가 노출됩니다)
    - 상태 : Smart Downloader CDN 이용 시에만 알 수 있는 데이터입니다. 고객사 CDN 이용 시에 상태 영역은 **-** 로 표기됩니다.
	-   |  상태 | 설명 |
		|----------|---------|
		|![작업 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_progressing.PNG)| Smart Downloader CDN 연동 진행 중.|
        |![정상](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_success.PNG)       |Smart Downloader CDN 정상 연동.|
        |![생성실패](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_fail.PNG)   |Smart Downloader CDN 연동 실패.<br>CDN 상세보기 창에서 다시 생성 요청을 할 수 있습니다. |


- 최신 빌드
    - 빌드 배포 일시 : 최신 빌드의 마지막 배포 일시.
    
    - 리소스 업로드 일시 : 최신 빌드의 마지막 업로드 일시.
	
	- 상태 : 업로드한 리소스의 현재 상태. **배포 대기** 상태 혹은 **배포 실패** 상태인 경우 \[빌드 배포\] 버튼이 활성화 됩니다.
	
    -   |  상태 | 설명 |
        |----------|---------|
        |![등록 전](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/resource_not_register.PNG)| 리소스 등록을 하지 않은 상태.|
        |![CDN 생성 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_create.png) | Smart Downloader CDN을 생성하고 CDN Purge가 가능할 때까지 대기 중인 상태. |
        |![업로드 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/resource_uploading.PNG)  |리소스 업로드가 진행 중인 상태.<br>업로드 중인 상태에서 신규 리소스 업로드 및 삭제 기능을 이용할 수 없습니다.|
        |![배포 대기](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/build_complete.PNG)    |리소스 업로드가 완료 상태.<br> \[배포\] 버튼을 통해 빌드를 배포할 수 있습니다.|
        |![배포 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/deploying.PNG)|\[배포\] 버튼을 통해 배포가 진행 중인 상태.<br>배포 중인 상태에서 신규 리소스 업로드, 수정, 삭제 기능을 이용할 수 없습니다.|
        | ![배포 예약](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/deploy_reservation.png) | 업로드한 리소스의 배포를 예약해 놓은 상태.<br>배포 예약 중인 상태에서 신규 리소스 업로드, 수정, 삭제 기능을 이용할 수 없습니다.|
        |![배포 완료](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/deploy_complete.PNG)   |업로드한 리소스가 CDN 에 배포 완료된 상태.|
        |![업로드 실패](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/upload_fail.PNG)   |리소스 업로드가 실패한 상태.<br> 해당 상태가 지속될 시 고객센터로 문의하시기 바랍니다.|
        |![배포 실패](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/deploy_fail.PNG)   |배포가 실패한 상태. <br>\[재배포\] 버튼을 통해 재배포 할 수 있습니다.<br>해당 상태가 지속될 시 고객센터로 문의하시기 바랍니다.|
    	
    - | 버튼                                                         | 설명                                                         |
      | ------------------------------------------------------------ | ------------------------------------------------------------ |
      | ![배포 가능](http://static.toastoven.net//prod_smartdownloader/web_console/service/deploy_button_deploy.png) | 리소스 배포가 가능한 상태.<br>서비스 상태가 [배포 대기]일 때, 활성화 됩니다.<br>Smart Downloader CDN을 사용하는 서비스인 경우 프로젝트 내 Smart Downloader CDN을 사용하는 다른 서비스가 빌드 배포를 실행하면, CDN 캐시 재배포 작업으로 인해 버튼 클릭 후 5분동안 버튼은 무조건 [배포 불가] 처리됩니다. |
      | ![재배포](http://static.toastoven.net//prod_smartdownloader/web_console/service/deploy_button_redeploy.png) | 리소스 배포가 가능한 상태.<br>서비스 상태가 [배포 실패]일 때, 활성화 됩니다. |
      | ![예약취소](http://static.toastoven.net//prod_smartdownloader/web_console/service/deploy_button_cancel_reservation.png) | 리소스의 배포가 예약된 상태.<br>서비스의 상태가 [배포 예약] 상태일 때 활성화 됩니다. |
      | ![배포 불가](http://static.toastoven.net//prod_smartdownloader/web_console/service/deploy_button_deploy_disabled.png) | 리소스 배포가 불가능한 상태.<br>서비스 상태가 [배포 대기]와 [배포 실패], [배포 완료] 이외의 상태일 때 활성화 됩니다. |
      | ![배포 완료](http://static.toastoven.net//prod_smartdownloader/web_console/service/deploy_button_complete.png) | 리소스 배포가 불가능한 상태.<br>서비스 상태가 [배포 완료]일 때 활성화 됩니다. |

### 5. 서비스 배포

#### 5.1. 일괄 배포

- 서비스 목록의 상단에 있는 [일괄 배포] 버튼을 클릭하면 일괄 배포 팝업창이 열립니다.

![deploy_bulk_popup.png](http://static.toastoven.net//prod_smartdownloader/web_console/service/deploy/deploy_bulk_popup.png)

- 일괄 배포가 가능한 서비스의 목록은 현재 생성된 서비스 중, Smart Downloader CDN을 사용하고 배포 가능한 서비스만 선택이 가능합니다.

- 일괄 배포할 서비스를 선택하면 [배포 예약] 버튼과 [배포] 버튼이 활성화 됩니다.

  - [배포 예약] 버튼 클릭

    - 배포 예약 시간 입력을 위한 팝업이 열립니다.

      ![deploy_reservation_popup.png](http://static.toastoven.net//prod_smartdownloader/web_console/service/deploy/deploy_reservation_popup.png)

    - [기준 시간]과 [배포 시간] 을 선택한 후에 [확인] 버튼을 클릭하면 지정한 시간으로 배포 예약이 실행됩니다.

  - [배포] 버튼 클릭

    - 선택한 서비스들이 즉시 배포 됩니다.

#### 5.2. 배포

- 서비스 목록의 열에 있는 [배포] [재배포] 버튼을 클릭하거나 혹은 [서비스 상세 정보] 페이지의 [배포] 버튼을 클릭했을 때 배포 팝업창이 열립니다.

  ![deploy_popup.png](http://static.toastoven.net//prod_smartdownloader/web_console/service/deploy/deploy_popup.png)

  * [배포 예약] 버튼 클릭

    * 배포 예약 시간 입력을 위한 팝업이 열립니다.

      ![deploy_reservation_popup.png](http://static.toastoven.net//prod_smartdownloader/web_console/service/deploy/deploy_reservation_popup.png)

    * [기준 시간]과 [배포 시간] 을 선택한 후에 [확인] 버튼을 클릭하면 지정한 시간으로 배포 예약이 실행됩니다.

  * [배포] 버튼 클릭

    * 현재 서비스의 리소스가 즉시 배포 됩니다.



### 6. 서비스 상세 정보

등록한 서비스의 상세 정보 페이지 입니다. \[서비스 정보\], \[CDN 연동 안내\], \[최신 빌드 정보\], \[빌드 배포 이력\] 영역으로 구성되어 있습니다.

![smartdl_13_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_13_201812.png)

#### 6.1 서비스 정보
서비스 등록 시 입력한 서비스 이름과 서비스 설명값을 보여줍니다.

#### 6.2 CDN 연동 안내
CDN 연동 완료 시 서비스에 연동한 CDN 정보가 나타납니다. 아래 A ~ C 경우로 나눠서 CDN 연동 안내를 설명합니다.

**A. Smart Downloader CDN 연동**

| 항목 | 설명 |
| --- | --- |
| CDN 서버 | Smart Downloader CDN 으로 표기됩니다. |
| CDN 서버 주소 | Smart Downloader CDN 연동 시 자동으로 CDN 다운로드 URL 이 생성되며 해당 URL 이 노출됩니다. |
| CDN 설정 정보 | 정보 확인하기 버튼을 클릭하여 Smart Downloader CDN 설정을 확인할 수 있습니다. |

**B. 고객사 CDN 연동**

| 항목 | 설명 |
| --- | --- |
| CDN 서버 | 고객사 CDN 으로 표기됩니다. |
| CDN 서버 주소 | 고객사 CDN 연동을 위해 유저가 입력한 고객사 CDN URL 이 노출됩니다. 미입력 시 수정 화면으로 이동해 고객사 CDN URL 을 입력해야 합니다. |
| 원본 서버 URL | 원본 서버 주소로 적용할 URL 이 노출됩니다.|

**C. CDN 미 연동**

- CDN 연동 안내 가이드 문구가 나타납니다. 수정 버튼을 클릭하여 CDN 정보를 설정할 수 있습니다.

#### 6.3 최신 빌드 정보
리소스 업로드 완료 시 리소스 업로드 정보가 나타납니다.
배포 상태가 **등록 전** 이라면 리소스 업로드 정보는 모두 빈 값이 나타납니다. ( \[리소스 업로드 정보\] 영역에 상세 정보 버튼은 비활성화)

> \[주의점\]
배포 상태가 **업로드 중**, **배포 중** 이면 신규 리소스 업로드를 할 수 없습니다.
배포 상태가 **배포 대기** 상태인 경우, 최신 빌드를 CDN에 배포할 수 있습니다. (**배포 실패** 상태인 경우도 재배포를 위해 \[빌드 배포\] 버튼이 활성화됩니다.)

![smartdl_14_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_14_201812.png)

| 항목 | 설명 |
| --- | --- |
| 신규 리소스 업로드 | 현재 페이지에서 신규 리소스를 업로드 할 수 있습니다.<br> 배포 상태가 **업로드 중**, **배포 중** 이면 신규 리소스 업로드를 할 수 없습니다. |
| 리소스 업로드 정보 | 업로드 된 리소스의 파일 개수와 전체 파일 크기를 보여줍니다. |
| 상세 정보 | 업로드 된 리소스 정보가 Tree 형태 팝업으로 노출됩니다. |
| 배포 이력 보기 | 서비스 상세 정보 하단에 \[빌드 배포 이력\] 영역이 노출됩니다. |
| 최종 업로드 일시 | 유저가 지정한 리소스가 업로드된 일시입니다. |
| 최종 등록자 | 리소스를 업로드한 유저의 NHN Cloud계정 정보입니다. |
| 배포 상태 | 최신 빌드의 배포 상태이며 각 상태값은 서비스 목록 > 최신 빌드 영역 정보와 동일합니다. |
| 빌드 배포 | 최신 빌드 정보의 배포 상태가 **배포 대기** 상태인 경우 최신 빌드를 연동된 CDN 으로 배포할 수 있습니다.(**배포 실패** 상태인 경우도 재배포를 위해 \[빌드 배포\] 버튼이 활성화됩니다.)<br>배포 시 Smart Downloader CDN 의 경우 최대 60분, 고객사 CDN 의 경우 사용 환경에 따라 배포 시간이 상이할 수 있습니다. |

#### 6.4 빌드 배포 이력

![smartdl_15_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_15_201812.png)

**배포 성공**, **배포 실패** 상태의 이력정보를 빌드 배포 일시 내림차순으로 보여줍니다.

| 항목 | 설명 |
| --- | --- |
| 빌드 배포 일시 | \[빌드 배포\] 버튼을 통한 배포가 완료된 일시 입니다. |
| 최종 배포자| \[빌드 배포\] 버튼으로 배포한 유저의 NHN Cloud계정 정보입니다. |
| 리소스 업로드 일시 | 유저가 지정한 리소스가 업로드된 일시입니다. |
| 최종 등록자 | 리소스를 업로드한 유저의 NHN Cloud계정 정보입니다. |
| 상태 | 최신 빌드의 배포 상태이며 각 상태값은 상단의 \[최신 빌드 정보\] 영역의 \[배포 상태\]와 동일합니다. |

#### 6.5 서비스 삭제
- \[서비스 상세 정보\] 페이지 우측 상단에 있는 삭제 버튼을 통해 서비스 삭제를 진행할 수 있습니다.
>\[주의점\]
배포 상태가 **업로드 중**, **배포 중** 이거나 CDN 상태가 **작업 중** 이면 서비스를 삭제할 수 없습니다.
서비스 삭제 시, 원본 파일과 배포파일은 모두 삭제되며 Smart Downloader CDN 연동의 경우 CDN 사용도 정지되는 점을 주의하시기 바랍니다.


### 7. 서비스 수정
\[서비스 상세 정보\] 페이지 우측 상단에 있는 수정 버튼을 통해 서비스 수정 페이지로 이동 할 수 있습니다.

> \[주의점\]
배포 상태가 **업로드 중**, **배포 중** 이거나 Smart Downloader CDN 연동 시 CDN 상태가 **작업 중** 이면 서비스를 수정할 수 없습니다.

![smartdl_16_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_16_201812.png)

#### 7.1 서비스 정보
서비스 이름은 고정된 값으로 수정할 수 없으며 서비스 설명은 수정할 수 있습니다.

#### 7.2 CDN 정보
현재 CDN 연동 상태를 아래 3가지 경우로 나눠서 CDN 정보 수정을 안내하겠습니다.

**7.2.1 현재 Smart Downloader CDN 연동인 경우**
​	- Smart Downloader CDN -> 고객사 CDN 연동으로 변경할 수 있습니다.
​   - 고객사 CDN 서버 주소는 HTTP/HTTPS 프로토콜을 선택해서 입력해야 합니다.

**7.2.2 현재 고객사 CDN 연동인 경우**
​	- 고객사 CDN  -> Smart Downloader CDN 연동으로 변경할 수 있습니다.

**7.2.3 현재 CDN 미 연동인 경우**
​	- Smart Downloader CDN 사용 / 고객사 CDN 사용 중 한 가지를 선택하여 CDN 연동할 수 있습니다.


## 실시간 모니터링 Tab
하루동안 서비스를 다운로드한 유저에 대한 통계정보를 00:00:00 부터 현재까지 10분 주기로 보여줍니다.

### 1. 실시간 다운로드 현황
#### 1-1 미니 차트
**조회 조건**에서 선택한 조건에 해당하는 전체 통계정보를 간략한 차트로 보여줍니다.
각 항목별 설명은 다음과 같습니다.

![smartdl_21_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_21_201812.png)

| 번호 | 항목 | 설명 |
| --- | --- | --- |
| 1 | 서비스 선택 | - 다운로드 현황을 확인할 서비스를 선택. <br> - 선택한 서비스를 바꾸는 경우 페이지 전체의 차트가 변경. |
| 2 | 국가 선택 | - 특정 국가에 대한 통계정보를 확인하고 싶은 경우 선택.<br> - 다운로드 상위 10개 국가만 노출. <br> - 국가를 변경하는 경우 **실시간 다운로드 현황**의 차트 정보만 변경. |
| 3 | 차트 데이터 수집 시간 | - 마지막으로 차트 정보가 수집된 시간. |
| 4 | 차트 이름 | - 어떤 정보에 대한 차트인지 알려주기 위한 제목. <br> - **종류** <br> -- Download Total : 다운로드가 실행된 총 횟수. <br> -- Full Download Count : 업로드된 빌드 파일 전체를 다운로드 받은 횟수.<br> -- Download Success : 다운로드에 성공한 횟수.<br> -- Average Download Time : 다운로드 실행시 평균 소요 시간. |
| 5 | 다운로드 횟수 | Average Download Time 차트에서는 전체 평균 다운로드 시간을 의미. |
| 6 | 전날 동시간 다운로드 횟수와 비교 | Average Download Time 차트에서는 전체 평균 다운로드 시간과 비교. |
| 7 | 다운로드 유형 | 다운로드 횟수중 Full & Update 세분화|
| 8 | 성공률 | 다운로드 성공률 |


#### 1-2 OS별 차트
**조회 조건**에서 선택한 조건에 해당하는 전체 통계 정보를 간략한 차트로 보여줍니다.
각 항목별 설명은 다음과 같습니다.

![smartdl_22_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_22_201812.png)

| 번호 | 항목 | 설명 |
| --- | --- | --- |
| 1 | OS 선택 필터 | - All(기본값) : 모든 OS에 대한 통계 정보 노출.<br> - iOS / Android / Windows : 선택한 OS에서 다운로드 받은 통계 정보만 노출. <br> - MacOS(선택적) : MacOS에서 다운로드 받은 기록이 있는 경우에만 선택 가능. |
| 2 | Download Success / Fail | - Column Chart (누적).<br> - 10분 단위로 통계 정보 노출.<br> - 다운로드 성공 / 실패 횟수. |
| 3 | Full / Update Download | - Column Chart (누적).<br> - 10분 단위로 통계 정보 노출.<br> - 업로드 된 전체 파일 다운로드 횟수 / 수정된 일부 파일 다운로드 횟수.<br> - Unknown 은 업데이트 목록을 다운로드 하는 중에 실패한 경우. |
| 4 | Average Download Time(sec) | - Column Chart.<br> - 10분 단위로 통계 정보 노출. <br> - 평균 다운로드 시간. |


### 2. 국가별 다운로드 현황
**조회 조건**에서 선택한 조건에 해당하는 통계 데이터를 국가별로 구분하여 표로 보여줍니다.
각 항목별 설명은 다음과 같습니다.

![smartdl_23_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_23_201812.png)

| 번호 | 항목 | 설명 |
| --- | --- | --- |
| 1 | 데이터 저장 | 클릭시 모든 국가별 다운로드 표가 **.csv** 파일로 저장됨. |
| 2 | 국가별 다운로드 현황 표 | - 다운로드 총 횟수가 많은 상위 5개국만 표에 노출.<br> - MacOS의 경우 다운로드 받은 기록이 있는 경우에만 선택적으로 노출. |


## 모니터링 지표 Tab
Smart Downloader를 활성화하여 다운로드가 이루어진 시점부터 현재까지의 사용 통계 정보를 일별로 확인할 수 있습니다.

### 1. 조회 조건
다운로드 지표를 검색하기 위한 조건을 선택하기 위한 필터입니다.
각 항목별 설명은 다음과 같습니다.

![smartdl_24_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_24_201812.png)

| 번호 | 항목 | 설명 |
| --- | --- | --- |
| 1 | 조회 기간 | - 다운로드 통계정보를 검색할 기간.<br>- 검색기간은 일단위로 선택.<br>- 검색 기간은 최초 다운로드를 받은 날부터 검색 당일까지 가능. |
| 2 | 조회 조건 - 서비스 | - 다운로드 통계정보를 검색할 서비스를 선택. |
| 3 | 조회 조건 - 국가 | - 다운로드 통계 정보를 검색할 국가를 선택.<br> - 다운로드 상위 10개 국가만 노출. |
| 4 | 조회 조건 - 다운로드 타입 | - All Type : 조건에 상관없이 모든 다운로드 타입에 대한 통계 검색.<br> - Full Download : 업로드된 빌드 파일 전체를 다운로드 받은 것에 대한 통계만 검색.<br> - Update Download : 업로드된 빌드 파일 중 수정된 파일만 다운로드 받은 것에 대한 통계만 검색.<br> - Unknown : Full / Update Download 여부를 확인하기 위한 메타파일 다운로드 중에 문제가 발생한 경우에 대한 통계만 검색. |
| 5 | 검색 | - 선택한 조건을 기준으로 통계 정보를 검색하기 위한 버튼. |


### 2. 일별 다운로드 현황
#### 2-1 일별 통계 데이터
**조회 조건**에서 선택한 조건에 해당하는 일별 통계 데이터를 표로 보여줍니다.
각 항목별 설명은 다음과 같습니다.

![smartdl_25_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_25_201812.png)

| 번호 | 항목 | 설명 |
| --- | --- | --- |
| 1 | 데이터 저장 | - 클릭시 모든 국가별 다운로드 표가 **.csv** 파일로 저장됨. |
| 2 | 일별 지표 | - 각 OS별 전체 다운로드 횟수 및 각 OS별 다운로드 성공 / 실패 / 평균 다운로드 시간을 일별로 노출. <br> - MacOS의 다운로드한 기록이 있는 경우에만 선택적으로 노출.<br> - 한 페이지에 10일간의 통계 정보가 노출됨. |
| 3 | 페이지 선택 | - 조회할 페이지 선택. |


#### 2-2 일별 지표 차트
**조회 조건**에서 선택한 조건에 해당하는 통계 데이터를 차트로 보여줍니다.
차트의 종류는 다음과 같습니다.

![smartdl_26_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_26_201812.png)

| 번호 | 항목 | 설명 |
| --- | --- | --- |
| 1 | Download Total | - Column Chart (누적).<br> - 1일 단위로 통계 정보 노출.<br> - 각 OS 별 전체 다운로드 횟수. |
| 2 | Download Success | - Column Chart (누적).<br> - 1일 단위로 통계 정보 노출.<br> - 각 OS 별 다운로드 성공 횟수. |
| 3 | Download Time(sec) | - Column Chart (비교).<br> - 1일 단위로 통계 정보 노출.<br> - 각 OS 별 평균 다운로드 시간. |
| 4 | Download Fail Type | - Pie Chart.<br> - 조회 기간 전체.<br> - 다운로드 실패 원인 별 횟수 및 비율. |


### 3. 일별 다운로드 현황
**조회 조건**에서 선택한 조건에 해당하는 통계 데이터를 국가별로 구분하여 표로 보여줍니다.
각 항목별 설명은 다음과 같습니다.

![smartdl_27_201812.png](https://static.toastoven.net/prod_smartdownloader/web_console/smartdl_27_201812.png)

| 번호 | 항목 | 설명 |
| --- | --- | --- |
| 1 | 데이터 저장 | 클릭시 모든 국가별 다운로드 표가 **.csv** 파일로 저장됨. |
| 2 | 국가별 다운로드 현황 표 | - 다운로드 총 횟수가 많은 상위 5개국만 표에 노출.<br> - MacOS의 경우 다운로드 받은 기록이 있는 경우에만 선택적으로 노출. |