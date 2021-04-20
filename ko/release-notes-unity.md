## Game > Smart Downloader > 릴리스 노트 > Unity SDK


### 2021. 04. 13.
#### 기능 개선/변경
* v1.6.8
    * 제외된 리소스 제거 옵션 추가
        * API 추가
            * DownloadConfig.ClearUnusedResources
    * DownloadConfig API 개선
        * API 변경
            * DownloadConfig.CheckOption (Obsolete) → DownloadConfig.UseStreamingAssets, DownloadConfig.PatchCompareFunction 사용
    * 실패율 정보를 확인을 위한 로그 개선


### 2020. 08. 11.
#### 기능 개선/변경
* v1.6.7
    * 리소스 검사 로직 개선
    * 리소스 검사 옵션 추가
        * API 추가
            * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA_AND_LOCAL_SCAN
    * 압축 해제 기능 제외
        * API 변경
            * ResultCode.ERROR_UNZIP (Obsolete)


### 2020. 07. 14.
#### 기능 개선/변경
* v1.6.6
    * 디스크 여유 공간 확인 방법 개선


### 2020. 06. 23.
#### 버그 수정
* v1.6.5
    * 실행환경에 따라 OverflowException이 발생하는 오류 수정


### 2020. 05. 12.
#### 기능 개선/변경
* v1.6.4
    * 리소스 검사 옵션 추가
        * API 변경
            * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA 추가

### 2020. 04. 28.
#### 기능 개선/변경
* v1.6.3
    * Streaming Assets 지원
        * Streaming Assets 리소스와 업로드 된 리소스를 비교 다운로드 기능 추가
        * API 변경
            * DownloadConfig.CheckAndroidObb (Obsolete) → DownloadConfig.CheckOption


### 2020. 03. 10.
#### 기능 개선/변경
* v1.6.2
    * Android - Split Application Binary(OBB) 지원
        * OBB에 포함된 Streaming Assets 리소스와 업로드된 리소스를 비교 다운로드 기능 추가
        * API 추가
            * DownloadConfig.CheckAndroidObb

### 2020. 01. 21.
#### 버그 수정
* v1.6.1
    * 다운로드 검사할 파일이 없는 경우 발생하던 예외 수정


### 2019. 12. 24.
#### 기능 개선/변경
* v1.6.0
    * 사전 다운로드 용량을 확인하기 위해 API 추가(CheckDownload)
    * API 변경
        * DownloadResult.IsSuccessful (Obsolete) → DownloadResult.Code
        * ProgressInfo.TotalFileNumber (Obsolete) → ProgressInfo.TotalFileCount
        * ProgressInfo.TotalReceivedBytes (Obsolete) → ProgressInfo.DownloadedBytes


### 2019. 10. 29.
#### 기능 개선/변경
* v1.5.9
    * 통계 지표 개선

### 2019. 07. 29.
#### 버그 수정
* v1.5.8
    * 특정 Android에서 다운로드 완료 처리 중 크래시가 발생하던 현상 수정


### 2019. 06. 25.
#### 기능 개선/변경
* v1.5.7
    * About 메뉴 추가
    * 전체 리소스 다운로드 시 다운로드할 리소스가 하나도 없는 경우 결과 코드를 성공(SUCCESS_NO_DIFFERENCE)으로 전달
    * 폴더 구조 변경
        * Assets/SmartDL/ → Assets/TOAST/SmartDL
        * `기존에 설치된 SmartDL 폴더를 삭제한 후 가져와야(import) 합니다.`

### 2018. 12. 27.
#### 버그 수정
* v1.5.6
    * 다운로드 취소 시 결과 콜백이 호출되지 않는 문제 수정

#### 기능 개선/변경
* v1.5.6
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
* v1.5.5
    * IL2CPP 빌드 지원
    * 간헐적으로 macOS에서 IP 주소를 얻지 못하는 문제 수정


### 2018. 10. 23.
#### 기능 개선/변경
* v1.5.4
    * Unity 2018.2 지원
    * 경로 및 파일을 선택해서 다운로드하는 기능 제공
    * 다운로드 파일 크기 계산 개선
    * 예제 코드 네임스페이스 추가

#### 버그 수정
* v1.5.4
    * iOS에서 파일명에 한글 포함 시 다운로드되지 않는 문제 수정
    * 파일명과 디렉터리명에 일부 특수문자 포함 시 다운로드 되지 않는 문제 수정



### 2018. 06. 05.
#### 기능 개선/변경
* v1.5.3
    * 재시도 로직 추가
    * 연결 타임아웃 / 읽기 타임아웃 분리


### 2018. 04. 18.
#### 버그 수정
* v1.5.1
    * Unity 최적화 옵션 설정으로 발생하는 링크 오류 수정


### 2018. 02. 22.
#### 기능 개선/변경
* Smart Downloader 내 개별 단위인 <b>서비스</b> 추가
* v1.5.0 릴리스
    * Core 라이브러리의 의존도 제거
    * API 변경
        * 사용성 개선을 위한 API 변경


### 2017. 10. 26.
#### 기능 개선/변경
* v1.2.0 릴리스
    * 안정성 강화
        * 내부 Core SDK 의존도 제거
        * Native 라이브러리 의존도 감소

### 2017. 02. 23.
#### 기능 개선/변경
* v1.1.0 릴리스
    * class Name 변경(DLCSkin -> SmartDLUnitySkin).
    * 정적 API만 제공

### 2017. 01. 19.
#### 신규 서비스 출시
* Smart Downloader 서비스 출시
    * Smart Downloader는 게임에 필요한 리소스를 효율적으로 다운로드할 수 있는 서비스입니다.
    * 게임 다운로드 데이터를 기반으로 다양한 통계 데이터를 제공하고 있습니다.