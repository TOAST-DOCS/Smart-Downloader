## Game > Smart Downloader > 릴리스 노트

### 2020. 11. 24.
#### 기능 개선/변경
```
Unity Tool v1.0.2 이하 버전을 사용하시는 경우 업데이트가 필요합니다.
이전 버전의 Unity Tool은 사용하실 수 없습니다.
```
* [Unity Tool] v1.0.3
    * 예약 배포 기능 추가
    * Unity 2019.3 에디터 UI 대응
* [Console] 일괄, 예약 배포 기능 추가.
    * Smart Downloader CDN을 사용하는 서비스는 목록 페이지에 일괄, 예약 배포를 진행할 수 있도록 기능 추가.
    * Smart Downloader CDN을 사용하는 서비스는 개별 배포시에도 예약 배포를 진행할 수 있도록 기능 추가.
* [Console] 서비스 생성 마법사의 파일 업로드 화면에서 파일 업로드 없이 업로드 가능하도록 수정.


### 2020. 08. 11.
#### 기능 개선/변경
* [Unity SDK] v1.6.7
    * 리소스 검사 로직 개선
    * 리소스 검사 옵션 추가
        * API 추가
            * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA_AND_LOCAL_SCAN
    * 압축 해제 기능 제외
        * API 변경
            * ResultCode.ERROR_UNZIP (Obsolete)

### 2020. 07. 14.
#### 기능 개선/변경
* [Unity SDK] v1.6.6
    * 디스크 여유 공간 확인 방법 개선
* [Console] 빌드배포 기능 수정.
    * 빌드배포시 5분간 같은 프로젝트의 Smart Downloader CDN을 사용하는 서비스의 배포가 불가능하도록 수정.
    * 배포 버튼의 명칭을 서비스의 상태에 맞게 노출하도록 기능 수정.

### 2020. 06. 23.
#### 버그 수정
* [Unity SDK] v1.6.5
    * 실행환경에 따라 OverflowException이 발생하는 오류 수정

### 2020. 06. 11.
#### 기능 개선/변경
* [Console] 빌드배포 기능 수정.
    * Smart Downloader CDN을 사용하는 경우, 빌드배포 실행시 원본소스 파일과 CDN에 배포된 파일을 비교한 후에 배포 완료 처리하도록 기능 수정.
    * 빌드배포 실행시 빌드배포 버튼이 바로 비활성화 되도록 기능 수정.

### 2020. 05. 12.
#### 기능 개선/변경
* [Unity SDK] v1.6.4
    * 리소스 검사 옵션 추가
        * API 변경
            * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA 추가

### 2020. 04. 28.
#### 기능 개선/변경
* [Unity SDK] v1.6.3
    * Streaming Assets 지원
        * Streaming Assets 리소스와 업로드 된 리소스를 비교 다운로드 기능 추가
        * API 변경
            * DownloadResult.CheckAndroidObb (Obsolete) → DownloadResult.CheckOption

### 2020. 04. 14.
#### 기능 개선/변경.
* [Console] Smart Downloader CDN 수정
    * CDN 밴더사 변경을 위한 마이그레이션 작업 지원을 위해 CDN 수정이 불가능하게 변경
* [Console] 파일 업로드
    * 파일 업로드 제한을 전체 5GB 이하에서 단일 파일 5GB 이하로 변경

### 2020. 03. 24.
#### 기능 개선/변경
* [Console] Smart Downloader CDN 연동
    * CDN 서비스 지역을 선택하는 기능 제거

### 2020. 03. 10.
#### 기능 개선/변경
* [Unity SDK] v1.6.2
    * Android - Split Application Binary(OBB) 지원
        * OBB에 포함된 Streaming Assets 리소스와 업로드된 리소스를 비교 다운로드 기능 추가
        * API 추가
            * DownloadConfig.CheckAndroidObb

### 2020. 01. 21.
#### 버그 수정
* [Unity SDK] v1.6.1
    * 다운로드 검사할 파일이 없는 경우 발생하던 예외 수정

### 2019. 12. 24.
#### 기능 개선/변경
* [Console] 서비스 관리
    * CDN의 생성에 실패한 경우, 실패한 CDN을 삭제하고 새로운 CDN을 생성하기 위한 기능 추가
* [Unity SDK] v1.6.0
    * 사전 다운로드 용량을 확인하기 위해 API 추가(CheckDownload)
    * API 변경
        * DownloadResult.IsSuccessful (Obsolete) → DownloadResult.Code
        * ProgressInfo.TotalFileNumber (Obsolete) → ProgressInfo.TotalFileCount
        * ProgressInfo.TotalReceivedBytes (Obsolete) → ProgressInfo.DownloadedBytes
* [Unity Tool] v1.0.2
    * 리소스 트리 뷰에서 파일명으로 오름차순 정렬해서 보여주도록 수정

#### 버그 수정
* [Unity Tool] v1.0.2
   * 폴더명과 하위의 파일명이 동일한 경우 업로드 리소스 선택 화면에서 리소스 출력이 정상적이지 않은 문제 수정

### 2019. 10. 29.
#### 기능 개선/변경
* [Unity SDK] v1.5.9
    * 통계 지표 개선

### 2019. 07. 29.
#### 버그 수정
* [Unity SDK] v1.5.8
    * 특정 Android에서 다운로드 완료 처리 중 크래시가 발생하던 현상 수정

### 2019. 06. 25.
#### 기능 개선/변경
* [Unity SDK] v1.5.7
    * About 메뉴 추가
    * 전체 리소스 다운로드 시 다운로드할 리소스가 하나도 없는 경우 결과 코드를 성공(SUCCESS_NO_DIFFERENCE)으로 전달
    * 폴더 구조 변경
        * Assets/SmartDL/ → Assets/TOAST/SmartDL
        * `기존에 설치된 SmartDL 폴더를 삭제한 후 가져와야(import) 합니다.`
* [Unity Tool] v1.0.1
    * 폴더 구조 변경
        * Assets/SmartDL/ → Assets/TOAST/SmartDL
        * `기존에 설치된 SmartDL 폴더를 삭제한 후 가져와야(import) 합니다.`

### 2019. 06. 12.
* [Unity Tool] v1.0.0
    * 배포

### 2019. 01. 29.
#### 기능 개선/변경
* [Console] 공통
    * 페이지의 전체 메시지에 다국어(영어, 일어) 반영

### 2018. 12. 27.
#### 버그 수정
* [Unity SDK] v1.5.6
    * 다운로드 취소 시 결과 콜백이 호출되지 않는 문제 수정

#### 기능 개선/변경
* [Console] 공통
    * 페이지의 전체 메시지에 표준어 검수 결과 반영
* [Unity SDK] v1.5.6
    * Common
        * [ResultCode 리뉴얼](/Game/Smart%20Downloader/ko/error-code)
        * [주의] 기존 SDK에서 업데이트할 경우 오류 발생
   * iOS
      * iOS 12 지원
   * Standalone(Windows)
      * DLL 이름 및 경로 변경
         * smartnative_x86.dll → x86/smartnative.dll
         * smartnative_x64.dll → x86_64/smartnative.dll

### 2018. 11. 27.
#### 버그 수정
* [Unity SDK] v1.5.5
    * IL2CPP 빌드 지원
    * 간헐적으로 macOS에서 IP 주소를 얻지 못하는 문제 수정

### 2018. 10. 23.
#### 기능 개선/변경
* [Unity SDK] v1.5.4
    * Unity 2018.2 지원
    * 경로 및 파일을 선택해서 다운로드하는 기능 제공
    * 다운로드 파일 크기 계산 개선
    * 예제 코드 네임스페이스 추가

#### 버그 수정
* [Unity SDK] v1.5.4
    * iOS에서 파일명에 한글 포함 시 다운로드되지 않는 문제 수정
    * 파일명과 디렉터리명에 일부 특수문자 포함 시 다운로드 되지 않는 문제 수정
* [Console] 서비스 관리
    * 업로드 하는 리소스 파일의 개수가 1만 개 이상일 경우 정상적으로 업로드되지 않는 문제 수정

### 2018. 07. 05.
#### 기능 개선/변경
* [Console] 공통
    * [빌드 배포] 버튼
        * 최신 빌드의 상태가 **배포 대기** 혹은 **배포 실패** 상태인 경우, **빌드 배포** 버튼을 활성화하도록 수정
* [Console] 서비스 목록
    * 최신 빌드 영역 수정
        * 기존: 업로드 일시, Last Uploader, 상태 데이터 표시
        * 수정: 빌드 배포 일시, 리소스 업로드 일시, 상태 데이터 표시. 서비스 목록의 상태 영역에서 **빌드 배포** 버튼 사용 가능

### 2018. 06. 26.
#### 기능 개선/변경
* [Console] 공통
    * 네트워크 연결이 끊어진 경우, 사용자가 알 수 있도록 팝업 추가
    * 문구 수정
        * 리소스 배포 URL -> 원본 서버 URL
        * 내부 CDN -> Smart Downloader CDN
        * 외부 CDN -> 고객사 CDN
* [Console] 서비스 관리
    * 빌드 업로드 / 배포 기능 분리
        * 기존 : 리소스 업로드 시, 즉시 업로드된 리소스가 유저에게 배포됨
        * 수정 : 리소스 업로드 후, 서비스 상세 보기에서 **빌드 배포** 버튼을 클릭해 업로드된 리소스 배포
    * 서비스 등록 마법사(wizard) 내 실행 시 리소스 파일 업로드와 CDN 등록의 작업 순서 변경
    * 서비스 배포 시 서비스 및 연동 CDN 변경이 불가능하도록 기능 추가
    * 서비스 상세 보기 내, 업로드 이력 보기를 배포 이력 보기로 변경

#### 버그 수정
* [Console] 서비스 관리
    * 리소스 업로드 중에 발생하는 일부 오류 수정
    * CDN 설정 중 발생하는 일부 오류 수정
    * 고객사 CDN의 URL 이 너무 긴 경우, 확인용 URL이 팝업창의 영역을 넘어가는 문제 수정
    * Explorer 에서 빌드 상세 정보 보기에서 가로, 세로 스크롤이 동시에 움직이는 현상 수정

### 2018. 06. 05.
#### 기능 개선/변경
* [Unity SDK] v1.5.3
    * 재시도 로직 추가
    * 연결 타임아웃 / 읽기 타임아웃 분리

### 2018. 04. 24.
#### 기능 개선/변경
* [Console] 공통.
    * 서버 내 오류 발생시 ERROR 페이지가 아닌 Service 목록 페이지로 이동한 후 오류 팝업이 나타나도록 기능 추가
* [Console] 서비스 관리
    * 하나의 서비스에서 Smart Downloader CDN을 중복으로 생성할 수 없도록 기능 추가

#### 버그 수정
* [Console] 서비스 관리
    * Mac용 Chrome에서 간혹 파일 업로드가 실패하는 오류 수정
    * 서비스를 사용하지 않을 때(disable) 파일 저장소나 CDN에서 발생하는 오류로 실패하는 현상 수정
* [Console] 모니터링
    * 서비스가 등록되지 않은 경우 모니터링 페이지에서 발생하는 오류 수정

### 2018. 04. 18.
#### 버그 수정
* [Unity SDK] v1.5.1
    * Unity 최적화 옵션 설정으로 발생하는 링크 오류 수정

### 2018. 03. 22.
#### 기능 개선/변경
* [Console] 서비스 관리
    * CDN 연동을 위한 입력 값 중, referers 항목에 여러 개의 도메인 정보(정규식 포함)를 입력할 수 있게 수정

#### 버그 수정
* [Console] 공통
    * 한국어 외의 다른 언어를 선택했을 때, 오류 페이지가 나타나는 현상 수정
    * 다른 탭에서 로그아웃되었을 때, 로그인 페이지가 웹 콘솔의 서비스 영역 내에 중복으로 생성되는 현상 수정
* [Console] 서비스 관리
    * 빌드 업로드 중에 브라우저를 닫거나, 새로 고침을 하는 경우 빌드 상태가 등록 중으로 지속되는 현상 수정
    * 빌드 상세 정보 조회 시 가로, 세로 스크롤바가 동시에 이동하는 현상 수정
* [Console] 모니터링.
    * 모니터링 페이지의 검색을 위한 서비스 목록이 차트 영역에 가려져 선택되지 않는 현상 수정
    * 모니터링 페이지에 생성되는 팝업 위에 검색 조건 필드가 나타나는 현상 수정
    * 지도 차트에서 특정 국가의 툴팁이 마우스 커서보다 한참 아랫부분에 생성되는 현상 수정
    * Internet Explorer 10/11, Microsoft Edge에서 발생하는 UI 오류 수정

### 2018. 02. 22.
#### 기능 개선/변경
* Smart Downloader 내 개별 단위인 <b>서비스</b> 추가
* [Console] 사용자 편의성 향상
    * 신규 빌드 업로드/배포 기능 추가
    * 빌드 배포 시 TOAST CDN을 사용할 수 있도록 기능 제공
    * 실시간/모니터링 지표 개선
    * 다운로드 오류 현황 지표 상세화
* [Unity SDK] v1.5.0 릴리스
    * Core 라이브러리의 의존도 제거
    * API 변경
        * 사용성 개선을 위한 API 변경
* [Jenkins Plugin] 신규 빌드 업로드 기능을 위한 Jenkins Plugin 제공

### 2017. 10. 26.
#### 기능 개선/변경
* [Unity SDK] v1.2.0 릴리스
    * 안정성 강화
        * 내부 Core SDK 의존도 제거
        * Native 라이브러리 의존도 감소

#### 버그 수정
* [Server] 인증 관련 버그 수정
    * 통합 앱키를 삭제해도 인증에 성공하는 버그 수정
    * 인증 실패 시 오류 메시지 변경

### 2017. 02. 23.
#### 기능 개선/변경
* [Console] 각 페이지에 접근할 수 있는 탭 추가
* [Console] 다운로드 상세 검색 시 검색 대상 데이터가 너무 많은 경우, 검색 항목을 다시 설정하도록 기능 수정
* [Console] 다운로드 상세 검색 시 다운로드 실패만 선택한 경우 '다운로드 시간/속도' 항목은 선택되지 않도록 수정
* [SDK][[Unity-1.1.0](/Download/#upcoming-products-smart-downloader)] 릴리스
    * class Name 변경(DLCSkin -> SmartDLUnitySkin).
    * 정적 API만 제공

### 2017. 01. 19.
#### 신규 서비스 출시
* Smart Downloader 서비스 출시
    * Smart Downloader는 게임에 필요한 리소스를 효율적으로 다운로드할 수 있는 서비스입니다.
    * 게임 다운로드 데이터를 기반으로 다양한 통계 데이터를 제공하고 있습니다.
