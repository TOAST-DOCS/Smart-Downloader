## Game > Smart Downloader > Console Guide

Smart Downloader 사용을 위해서 상품 이용 후 서비스를 등록해야 합니다.
서비스 등록은 [서비스 등록] > [빌드 업로드] > [CDN 연동] 3단계로 구성되어 있으며, 서비스 등록 후 실시간 모니터링과 모니터링 지표 데이터를 조회 및 다운로드 할 수 있습니다.

<br>

## Configuration

### Smart Downloader 서비스 활성화
Console 페이지 상단의 +서비스 선택 버튼을 클릭 후, Game 하위 Smart Downloader 서비스를 클릭하여 서비스 활성화를 합니다.

### AppKey 와 URL 확인.
Console 페이지 상단의 URL & Appkey 를 클릭하여 발급된 Appkey를 확인합니다. 확인된 Appkey는 SDK에 입력하여 사용하게 됩니다. Smart Downloader 서비스 비활성화 시, 발급된 Appkey는 복구되지 않으니 주의해주시기 바랍니다.

> 이미지 필요.

<br>
## 서비스 관리

### 서비스 목록
사용자가 등록한 서비스의 목록을 보여줍니다.
+ 서비스 이름
	+ 서비스 등록 시 사용자가 입력한 서비스 이름.
+ CDN
    + 서버 : CDN download URL. (CDN download URL 이 등록되어 있지 않는 경우에 \[CDN URL 입력이 필요합니다.\] 문구가 노출됩니다.)
    + 상태 : Smart Downloader CDN 이용 시, CDN 상태를 구분합니다. CDN 상태는 \[작업 중\], \[정상\], \[생성 실패\] 로 구성됩니다.
		- 작업 중 : Smart Downloader CDN 연동 중.
		- 정상 : Smart Downloader CDN 정상 연동.
		- 생성 실패 : Smart Downloader CDN 연동 실패.
- 최신 빌드
    - 업로드 일시 : 최신 빌드가 업로드 된 마지막 업로드 일시.
    - Last Uploader : 최신 빌드를 업로드한 유저 계정. Jenkins 서버로 업로드 한 경우는 Jenkins Plugin 이 설치된 서버 IP.
    - 상태 : 업로드할 빌드에 대한 상태로 \[등록 전\] , \[등록 중\] , \[등록 완료\] , \[등록 중 실패 - 관리자 문의\] 로 구성됩니다.
    	- 등록 전 : 빌드 등록을 하지 않은 상태.
    	- 등록 중 : 빌드 등록이 진행 중인 상태. 등록 중인 상태에서 신규 빌드 업로드 및 삭제 기능을 이용할 수 없습니다.
    	- 등록 완료 : 빌드 등록 완료.
    	- 등록 중 실패 - 관리자 문의 : 빌드 등록 실패.

<br>
서비스 열 클릭 시, 해당 서비스에 대한 \[서비스 상세 정보\] 페이지로 이동합니다.
<br>
### 서비스 상세 정보
#### 서비스 정보
서비스 등록 시 입력한 서비스 이름과 서비스 설명값을 보여줍니다.
- 서비스 이름
	서비스를 구분할 수 있는 식별값.
- 서비스 설명
	서비스 등록 시 입력한 서비스 설명값.

#### CDN 연동 안내
CDN 연동 완료 시 서비스에 연동한 CDN 정보가 나타납니다.
- CDN 서버
	SmartDownloader CDN 연동했다면 내부 CDN 사용 버튼이 활성화 되며, 외부(자체) CDN 을 사용한다면 외부 CDN 사용 버튼이 활성화 됩니다.
- CDN 서버 주소
-

CDN 미 연동 시 CDN 연동 안내 가이드 문구가 나타납니다.
> 이미지 필요.


#### 최신 빌드 정보
빌드 업로드 완료 시 최신 빌드 정보가 나타납니다.
- 신규 빌드 업로드
- 빌드 정보
	업로드 된 빌드의 파일 개수와 전체 파일 크기를 보여줍니다.
    - 상세 정보
    - 업로드 이력 보기
- 최종 업로드 일시

- Last Uploader

- 상태


빌드 등록 전 상태 시 빌드 정보는 모두 빈 값이 나타납니다. ( \[빌드 정보\] 영역에 상세 정보 버튼은 비활성화. )

#### 서비스 수정
- 우측 상단에 있는 수정 버튼을 통해 서비스 수정 페이지로 이동 할 수 있습니다.

#### 서비스 삭제
- 우측 상단에 있는 삭제 버튼을 통해 서비스 삭제를 진행할 수 있습니다.



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
