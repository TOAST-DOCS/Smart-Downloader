## Game > Smart Downloader > Console Guide

Smart Downloader 사용을 위해서 상품 이용 후 서비스를 등록해야 합니다.
서비스 등록은 \[서비스 등록\] > \[빌드 업로드\] > \[CDN 연동\] 3단계 Wizard 형식으로 구성되어 있습니다. 서비스 등록 후 해당 서비스에 대한 실시간 다운로드 현황 및 다운로드 지표 데이터를 다양한 형태의 차트로 제공하며 데이터를 다운로드 할 수 있습니다.
<br>

## Configuration

### Smart Downloader 서비스 활성화
Console 페이지 상단의  ![서비스 선택](http://static.toastoven.net/prod_smartdownloader/web_console/product_enable.PNG) 버튼을 클릭 후, Game 하위 Smart Downloader 서비스를 클릭하여 서비스 활성화를 합니다.

### AppKey 와 URL 확인.
Console 페이지 상단의 URL & Appkey 를 클릭하여 발급된 Appkey를 확인합니다.확인된 Appkey는 SDK에 입력하여 사용하게 됩니다.
Smart Downloader 서비스 비활성화 시, 발급된 Appkey는 복구되지 않으니 주의하시기 바랍니다.

![Appkey 와 URL 확인](http://static.toastoven.net/prod_smartdownloader/web_console/urlAndAppkey.PNG)
<br>
## 서비스 관리

### 서비스 등록
Smart Downloader 를 사용하기 위한 서비스를 등록합니다. \[서비스 등록\] > \[빌드 업로드\] > \[CDN 연동\] 3 단계 Wizard 형식으로 진행합니다. \[서비스 등록\] > \[빌드 업로드\] > \[CDN 연동\] 까지 모두 완료되어야 SDK 를 통해 배포본을 다운로드할 수 있습니다.
<br>
#### 서비스 등록
`1 단계 : 서비스 이름과 서비스 설명을 입력하여 서비스를 생성하는 단계.`
- 서비스 이름
    - 서비스를 구분할 수 있는 식별값으로 **필수 입력** 해야 합니다.
    - 서비스 이름은 식별값으로 사용되기 때문에 동일한 서비스 이름으로 2개 이상의 서비스를 등록할 수 없습니다.
    - **영문 소문자, 숫자와 특수기호 (_),(-)** 만 사용 가능하며 첫 문자는 **영문 소문자나 숫자**로 시작해야 합니다.
    - 공백으로 시작할 수 없습니다.

- 서비스 설명
	- 서비스에 대한 부연 설명값을 입력합니다. 최대 100자로 입력을 제한합니다.

#### 빌드 업로드
`2 단계 : Smart Downloader 를 통해 배포할 빌드 리소스를 업로드하는 단계.`
- 빌드 업로드는 폴더 업로드를 원칙으로 합니다. (업로드 버튼 클릭 시, 폴더 찾아보기 윈도우가 로딩됩니다.)
- Internet Explorer 브라우저는 빌드 업로드 기능을 제공하지 않습니다. 빌드 업로드는 Chrome 브라우저를 사용하시기 바랍니다.


**빌드 리소스 업로드 안내.**

![빌드 리소스 업로드 안내](http://static.toastoven.net/prod_smartdownloader/web_console/service/build/build_upload_1.PNG)
- Local machine 업로드
    - Console 페이지를 통해 사용자 Local 에 있는 빌드본을 업로드 할 수 있습니다.
    - 빌드 리소스 업로드 안내 페이지에서 \[예, 지금 업로드하겠습니다\] 버튼 클릭으로 진행할 수 있습니다.
    - 업로드가 완료되면 \[업로드 된 빌드 정보\] 페이지로 이동합니다.

- Build Server(원격) 업로드
    - Smart Downloader Jenkins Plugin(ToastCloud SmartDownloader Plugin) 을 통해 빌드를 업로드.
    - ToastCloud SmartDownloader Plugin 에 대한 자세한 가이드는 **서드파티 사용자 가이드 > Jenkins Plugin 사용 가이드** 로 확인할 수 있습니다.


**업로드 된 빌드 정보**

![업로드 된 빌드 정보](http://static.toastoven.net/prod_smartdownloader/web_console/service/build/build_upload_2.PNG)
- 원본 리소스
	- 폴더 찾아보기 윈도우에서 유저가 선택한 폴더의 이름은 빌드의 이름이 됩니다.
	- 빌드 재업로드 버튼 클릭 시, 현재 페이지에서 신규로 빌드를 업로드 할 수 있습니다. (단, 빌드 상태가 ![등록 중](http://static.toastoven.net/prod_smartdownloader/web_console/service_state/build_progressing.PNG) 이면 신규 빌드 업로드를 할 수 없습니다.)

- 빌드 정보
	- 업로드 된 빌드의 파일 개수와 전체 파일 크기를 보여줍니다.
	- 상세 정보 버튼 클릭 시 업로드 된 빌드 정보가 Tree 형태 팝업으로 노출됩니다.

- 최종 업데이트 : 최신 빌드가 업로드 된 마지막 업로드 일시입니다.


**빌드 업로드 취소 기능**

![빌드 업로드 취소](http://static.toastoven.net/prod_smartdownloader/web_console/service/build/build_uploading.PNG)

Smart Downloader 는 업로드 진행 중 업로드를 취소하는 기능을 제공합니다.
업로드 취소 기능이 완료되면 빌드 상태는 업로드 하기 전 상태로 되돌아 가는 점 유의하시기 바랍니다.


#### CDN 연동
`3 단계 : Smart Downloader CDN 혹은 외부 CDN 을 연동하는 단계.`

**CDN 연동 안내**
- Smart Downloader CDN 연동.
	- CDN 서비스 생성 팝업을 통해 CDN 설정 정보를 입력합니다.
		
		![CDN 설정 정보](http://static.toastoven.net/prod_smartdownloader/web_console/cdn/tc_cdn_register.PNG)
        > 부가 설명 추가!!
	- Smart Downloader CDN 연동은 최대 약 35초의 소요시간이 발생합니다.

- 외부 CDN 연동.
	- 원본 서버 주소로 적용할 **리소스 배포 URL** 을 제공합니다.
	- **사용할 CDN URL 을 입력**하여 Smart Downloader 서비스와 외부 CDN 이 연동되도록 설정합니다.
	- 외부 CDN URL은 HTTP/HTTPS 프로토콜을 선택해서 입력합니다.


#### 서비스 목록
사용자가 등록한 서비스의 목록을 한번에 10개씩 보여줍니다. 각 서비스 열 클릭 시, 해당 서비스에 대한 \[서비스 상세 정보\] 페이지로 이동합니다.

![서비스 목록](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_list.PNG)

- 서비스 이름
	- 서비스 등록 시 사용자가 입력한 서비스 이름.

- CDN
    - 서버 : CDN download URL. (CDN download URL 이 등록되어 있지 않는 경우에 \[CDN URL 입력이 필요합니다.\] 문구가 노출됩니다.)
    - 상태 : Smart Downloader CDN 이용 시에만 알 수 있는 데이터입니다. 외부 CDN 이용 시에 상태 영역은 **-** 로 표기됩니다.
		- ![작업 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_progressing.PNG) : Smart Downloader CDN 연동 진행 중.
		- ![정상](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_success.PNG) : Smart Downloader CDN 정상 연동.
		- ![생성실패](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_fail.PNG) : Smart Downloader CDN 연동 실패로 해당 상태가 지속될 시 관리자에게 문의하시면 됩니다.

- 최신 빌드
    - 업로드 일시 : 최신 빌드가 업로드 된 마지막 업로드 일시.
    - Last Uploader : 최신 빌드를 업로드한 유저 계정. Jenkins 서버로 업로드 한 경우는 Jenkins Plugin 이 설치된 서버 IP.
    - 상태 : 업로드한 빌드에 대한 상태입니다.
    	- ![등록전](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/build_not_register.PNG) : 빌드 등록을 하지 않은 상태.
    	- ![등록중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/build_progressing.PNG) : 빌드 등록이 진행 중인 상태. 등록 중인 상태에서 신규 빌드 업로드 및 삭제 기능을 이용할 수 없습니다.
    	- ![등록 완료](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/build_success.PNG) : 빌드 등록 완료.
    	- ![등록 중 실패](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/build_fail.PNG) : 빌드 등록 실패 상태로 해당 상태가 지속될 시 관리자에게 문의하시면 됩니다.


### 서비스 상세 정보

#### 서비스 정보
서비스 등록 시 입력한 서비스 이름과 서비스 설명값을 보여줍니다.
- 서비스 이름 : 서비스 등록 시 입력한 서비스 이름값.
- 서비스 설명 : 서비스 등록 시 입력한 서비스 설명값.

#### CDN 연동 안내
CDN 연동 완료 시 서비스에 연동한 CDN 정보가 나타납니다. 아래 1번 ~ 3번 경우로 나눠서 CDN 연동 안내를 설명합니다.

**1. Smart Downloader CDN 연동**

![smart downloader cdn](http://static.toastoven.net/prod_smartdownloader/web_console/service/cdn/tc_cdn_info.PNG)
- CDN 서버
	- 내부 CDN 사용 버튼이 활성화로 노출됩니다.
- CDN 서버 주소
	- Smart Downloader CDN 연동 시 자동으로 CDN Downloader URL 이 생성되며 해당 URL 이 노출됩니다.
- 내부 CDN 설정 정보
	- 정보 확인하기 버튼을 클릭하여 내부 CDN 설정을 확인할 수 있습니다.


**2. 외부 CDN 연동**

![smart downloader cdn](http://static.toastoven.net/prod_smartdownloader/web_console/service/cdn/external_cdn_info.PNG)
- CDN 서버
	- 외부 CDN 사용 버튼이 활성화로 노출됩니다.
- CDN 서버 주소
	- 외부 CDN 연동을 위해 유저가 입력한 외부 CDN URL 이 노출됩니다. 미입력 시 수정 화면으로 이동해 외부 CDN URL 을 입력해야 합니다.
- 원본 서버 URL
	- 원본 서버 주소로 적용할 리소스 배포 URL을 제공합니다.

**3. CDN 미 연동**

CDN 연동 안내 가이드 문구가 나타납니다.

![cdn 가이드](http://static.toastoven.net/prod_smartdownloader/web_console/service/cdn/cdn_guide.PNG)


#### 최신 빌드 정보
빌드 업로드 완료 시 최신 빌드 정보가 나타납니다.
빌드 등록 전 상태 시 빌드 정보는 모두 빈 값이 나타납니다. ( \[빌드 정보\] 영역에 상세 정보 버튼은 비활성화. )

- 신규 빌드 업로드
	- 현재 페이지에서 신규 빌드를 업로드 할 수 있습니다.
	- 빌드 상태가 ![등록 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/build_progressing.PNG) 이면 신규 빌드 업로드를 할 수 없습니다.
- 빌드 정보
	- 업로드 된 빌드의 파일 개수와 전체 파일 크기를 보여줍니다.
    - 상세 정보
    	- 업로드 된 빌드 정보가 Tree 형태 팝업으로 노출됩니다.
    - 업로드 이력 보기
    	-  서비스 상세 정보 하단에 \[빌드 업로드 History\] 영역이 노출됩니다.
    	
    	![빌드 업로드 History](http://static.toastoven.net/prod_smartdownloader/web_console/service/build/build_upload_history.PNG)
- 최종 업로드 일시
	- 서비스 목록 > 최신 빌드 영역 정보와 동일합니다.
- Last Uploader
	- 서비스 목록 > 최신 빌드 영역 정보와 동일합니다.
- 상태
	- 서비스 목록 > 최신 빌드 영역 정보와 동일합니다.


#### 빌드 업로드 History
빌드 업로드 history 정보가 업로드한 일시 내림차순으로 나타납니다.

- 원본 업데이트 일시
	- 유저가 지정한 빌드가 업로드된 일시입니다.
- Last Uploader
	- 서비스 상세 정보 > 최신 빌드 정보 > Last uploader 와 동일합ㄴ디ㅏ.
- 배포파일 생성일시
	- 유저가 업로드한 원본을 바탕으로 배포파일을 생성한 일시입니다.
- 상태
	- 빌드의 빌드 상태값으로 각 상태값은 서비스 목록 > 최신 빌드 > 상태 와 동일합니다.


### 서비스 수정
\[서비스 상세 정보\] 페이지 우측 상단에 있는 수정 버튼을 통해 서비스 수정 페이지로 이동 할 수 있습니다.

- 빌드 상태가 ![등록 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/build_progressing.PNG) 이거나 CDN 상태가 ![작업 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_progressing.PNG) 이면 서비스를 수정할 수 없습니다.

**서비스 정보**

서비스 이름은 고정된 값으로 수정할 수 없으며 서비스 설명은 수정할 수 있습니다.

**CDN 정보**

현재 CDN 연동 상태를 아래 1번 ~ 3번 경우로 나눠서 CDN 정보 수정을 안내하겠습니다.

1. 현재 Smart Downloader CDN 연동인 경우
	- 외부 CDN 연동으로 수정할 수 있습니다.
    
    ![외부 CDN 연동](http://static.toastoven.net/prod_smartdownloader/web_console/service/cdn/modify_external_cdn.PNG)
    - 외부 CDN 서버 주소는 HTTP/HTTPS 프로토콜을 선택해서 입력해야 합니다.

2. 현재 외부 CDN 연동인 경우
	- 내부 CDN (Smart Downloader CDN) 연동으로 수정할 수 있습니다.

3. 현재 CDN 미 연동인 경우
	- 내부 CDN 사용 / 외부 CDN 사용 중 한 가지를 선택하여 CDN 연동할 수 있습니다.


### 서비스 삭제
\[서비스 상세 정보\] 페이지 우측 상단에 있는 삭제 버튼을 통해 서비스 삭제를 진행할 수 있습니다.

- 빌드 상태가 ![등록 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/build_progressing.PNG) 이거나 CDN 상태가 ![작업 중](http://static.toastoven.net/prod_smartdownloader/web_console/service/service_state/cdn_progressing.PNG) 이면 서비스를 삭제할 수 없습니다.
- 서비스 삭제 시, 원본 파일과 배포파일은 모두 삭제되며 Smart Download CDN 연동의 경우 CDN 사용도 정지되는 점을 주의하시기 바랍니다.



## 모니터링
### 실시간 모니터링
하루동안 서비스를 다운로드한 유저에 대한 통계정보를 00:00:00 부터 현재까지 10분 주기로 보여줍니다.

#### 조회 조건.
![](http://static.toastoven.net/prod_smartdownloader/web_console/monitoring/realtime_filter.png)
1. 서비스
	* 다운로드 현황을 확인할 서비스를 선택.
	* 선택한 서비스를 바꾸는 경우 페이지 전체의 차트가 변경.

2. 국가
	* 특정 국가에 대한 통계정보를 확인하고 싶은 경우 선택.
	* 다운로드 상위 10개 국가만 노출.
	* 국가를 바꾸는 경우 `실시간 다운로드 현황`의 차트 정보만 변경.

#### 실시간 다운로드 현황.
![](http://static.toastoven.net/prod_smartdownloader/web_console/monitoring/realtime_realtimedownloadsummary.png)

1. 차트 데이터 수집 시간.
	* 마지막으로 차트 정보가 수집된 시간.

2. 미니 차트.
	* 항목
		* a. 차트 타이틀.
		* b. 다운로드 횟수(Average Download Time - 전체 평균 다운로드 시간).
		* c. 어제 동시간 다운로드 횟수(Average Download Time - 전체 평균 다운로드 시간)와 비교.
		* d. OS별 다운로드 횟수(Average Download Time - OS 별 평균 다운로드 시간).
		* e. 성공률. (Download Success 한정)
	* 종류.
		* Download Total
			* 다운로드가 실행된 총 횟수.
		* Full Download Count
			* 업로드된 리소스 파일 전체를 다운로드 받은 횟수.
		* Update Download Count
			* 업로드된 리소스 파일 중, 수정된 일부 파일만 받은 횟수.
		* Download Success
			* 다운로드에 성공한 횟수.
		* Average Download Time
			* 다운로드 실행시 평균 소요시간.

3. OS 차트.
	* 조회 조건.
		* All(기본값)
			* 모든 OS에 대한 통계 정보 노출.
		* iOS / Android / Windows
			* 선택한 OS에서 다운로드 받은 통계 정보만 노출.
		* MacOS(선택적)
		 	* MacOS에서 다운로드 받은 기록이 있는 경우에만 선택 가능.
			* MacOS에서 다운로드 받은 통계 정보만 노출.
	* 종류.
		* Download Success / Fail
			* Column Chart (누적).
			* 10분 단위로 통계 정보 노출.
			* 다운로드 성공 / 실패 횟수.
		* Download Fail Rate
			* Line Chart.
			* 다운로드 실패율.
			* 10분 단위로 통계 정보 노출.
			* 총 다운로드 수 상위 5개국만 노출.
		* Full / Update Install
			* Column Chart (누적).
			* 10분 단위로 통계 정보 노출.
			* 리소스 전체 파일 다운로드 / 수정된 일부 파일 다운로드 횟수.
			* Unknown 은 업데이트 목록을 다운로드 하는 중에 실패한 경우.
		* Average Download Time(sec)
			* Column Chart.
			* 10분 단위로 통계 정보 노출.
			* 평균 다운로드 시간.

#### 국가별 실시간 다운로드.
![](http://static.toastoven.net/prod_smartdownloader/web_console/monitoring/realtime_countrymap.png)
1. 지도 차트.
	* 차트 데이터 수집 시간.
		* 마지막으로 차트 정보가 수집된 시간.
	* 조회 조건.
		* 다운로드 전체
			* 국가별 다운로드 총 횟수를 차트에 노출.
		* 다운로드 실패.
			* 국가별 다운로드 실패 횟수를 차트에 노출.
	* 차트.
		* Map Chart.
		* 다운로드 횟수 정보를 국가별로 색상으로 표시.

#### 국가별 다운로드 현황.
![](http://static.toastoven.net/prod_smartdownloader/web_console/monitoring/realtime_countrygrid.png)
1. 데이터 저장.
	* 클릭시 모든 국가별 다운로드 표가 `.csv` 파일로 저장됨.

2. 국가별 다운로드 현황 표.
	* 다운로드 총 횟수가 많은 상위 5개국만 표에 노출.



### 모니터링 지표.
#### 조회 조건.
![](http://static.toastoven.net/prod_smartdownloader/web_console/monitoring/summary_filter.png)
다운로드 지표를 검색하기 위한 조건을 선택하기 위한 필터입니다.
각 항목별 설명은 다음과 같습니다.

1. 조회 기간
	* 다운로드 통계정보를 검색할 기간.
	* 검색기간은 일단위로 선택.
	* 검색 기간은 최초 다운로드를 받은 날부터 검색 당일까지 가능.

2. 조회 조건 - 서비스
	* 다운로드 통계정보를 검색할 서비스를 선택.

3. 조회 조건 - 국가
	* 다운로드 통계 정보를 검색할 국가를 선택.
	* 다운로드 상위 10개 국가만 노출.

4. 조회 조건 - 다운로드 타입
	* All Type
		* 조건에 상관없이 모든 다운로드 타입에 대한 통계 검색.
	* Full Install
		* 업로드된 리소스 파일을 전체를 다운로드 받은 것에 대한 통계만 검색.
	* Update Install
		* 업로드된 리소스 파일 중 수정된 파일만 다운로드 받은 것에 대한 통계만 검색.
	* Unknown
		* 업로드된 리소스 파일 목록을 다운로드 하는 중, 문제가 발생하여 파일을 다운로드 하지 못한 것에 대한 통계만 검색.

5. 검색
	* 선택한 조건을 기준으로 통계 정보를 검색하기 위한 버튼.

#### 일별 다운로드 현황.
![](http://static.toastoven.net/prod_smartdownloader/web_console/monitoring/summary_dailygrid.png)
`조회 조건`에서 선택한 조건에 해당하는 일별 통계 데이터를 표로 보여줍니다.
각 항목별 설명은 다음과 같습니다.

1. 데이터 저장.
	* 클릭시 모든 국가별 다운로드 표가 `.csv` 파일로 저장됨.

2. 일별 지표.
	* 각 OS별 전체 다운로드 횟수 및 각 OS별 다운로드 성공 / 실패 / 평균 다운로드 시간을 일별로 노출.
	* MacOS의 다운로드한 기록이 있는 경우에만 선택적으로 노출.
	* 한 페이지에 10일간의 통계 정보가 노출됨.

3. 페이지 선택.
	* 조회할 페이지 선택.

#### 일별 지표 차트.
![](http://static.toastoven.net/prod_smartdownloader/web_console/monitoring/summary_dailychart.png)
`조회 조건`에서 선택한 조건에 해당하는 통계 데이터를 차트로 보여줍니다.
차트의 종류는 다음과 같습니다.
* Downalod Total
	* Column Chart (누적).
	* 1일 단위로 통계 정보 노출.
	* 각 OS 별 전체 다운로드 횟수.
* Download Fail
	* Column Chart (누적).
	* 1일 단위로 통계 정보 노출.
	* 각 OS 별 다운로드 실패 횟수.
* Download Time(sec)
	* Column Chart (비교).
	* 1일 단위로 통계 정보 노출.
	* 각 OS 별 평균 다운로드 시간.
* OS Info
	* Pie Chart.
	* 조회 기간 전체.
	* 각 OS별 다운로드 횟수 및 비율.
* Download Fail Type
	* Pie Chart.
	* 조회 기간 전체.
	* 다운로드 실패 원인 별 횟수 및 비율.

#### 국가별 다운로드.
![](http://static.toastoven.net/prod_smartdownloader/web_console/monitoring/summary_mapchart.png)
`조회 조건`에서 선택한 조건에 해당하는 통계 데이터를 지도 차트로 보여줍니다.
각 항목별 설명은 다음과 같습니다.

1. 조회 조건.
	* 다운로드 전체
		* 국가별 다운로드 총 횟수를 차트에 노출.
	* 다운로드 실패.
		* 국가별 다운로드 실패 횟수를 차트에 노출.

2. 툴팁.
	* 특정 국가에 대해 마우스 오버시 툴팁 생성.
	* 해당 국가의 다운로드 정보가 노출.


#### 국가별 다운로드 현황.
![](http://static.toastoven.net/prod_smartdownloader/web_console/monitoring/summary_countrygrid.png)
`조회 조건`에서 선택한 조건에 해당하는 통계 데이터를 국가별로 구분하여 표로 보여줍니다.
각 항목별 설명은 다음과 같습니다.

1. 데이터 저장.
	* 클릭시 모든 국가별 다운로드 표가 `.csv` 파일로 저장됨.

2. 국가별 다운로드 현황 표.
	* 다운로드 총 횟수가 많은 상위 5개국만 표에 노출.
	* MacOS의 경우 다운로드 받은 기록이 있는 경우에만 선택적으로 노출.
