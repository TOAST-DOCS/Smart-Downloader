## Game > Smart Downloader > 릴리스 노트 > Unity SDK

### 1.7.0 (2021.09.14) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.7.0.unitypackage)

#### 버그 수정
* DLL 오류 수정

### 1.6.9 (2021.07.27) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.9.unitypackage)

#### 기능 개선/변경
* Unity 최소 지원 버전을 2018.4.0으로 변경
* Unity 2020.2 이후 버전에서 발생하는 Warning 제거


### 1.6.8 (2021.04.13) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.8.unitypackage)

#### 기능 개선/변경
* 제외된 리소스 제거 옵션 추가
    * API 추가
        * DownloadConfig.ClearUnusedResources
* DownloadConfig API 개선
    * API 변경
        * DownloadConfig.CheckOption (Obsolete) → DownloadConfig.UseStreamingAssets, DownloadConfig.PatchCompareFunction 사용
* 실패율 정보를 확인을 위한 로그 개선


### 1.6.7 (2020.08.11) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.7.unitypackage)

#### 기능 개선/변경
* 리소스 검사 로직 개선
* 리소스 검사 옵션 추가
    * API 추가
        * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA_AND_LOCAL_SCAN
* 압축 해제 기능 제외
    * API 변경
        * ResultCode.ERROR_UNZIP (Obsolete)


### 1.6.6 (2020.07.14) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.6.unitypackage)

#### 기능 개선/변경
* 디스크 여유 공간 확인 방법 개선


### 1.6.5 (2020.06.23) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.5.unitypackage)

#### 버그 수정
* 실행환경에 따라 OverflowException이 발생하는 오류 수정


### 1.6.4 (2020.05.12) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.4.unitypackage)

#### 기능 개선/변경
* 리소스 검사 옵션 추가
    * API 변경
        * PatchCheckOption.CHECK_LIST_WITH_SAVED_DATA 추가

### 1.6.3 (2020.04.28) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.3.unitypackage)

#### 기능 개선/변경
* Streaming Assets 지원
    * Streaming Assets 리소스와 업로드 된 리소스를 비교 다운로드 기능 추가
    * API 변경
        * DownloadConfig.CheckAndroidObb (Obsolete) → DownloadConfig.CheckOption


### 1.6.2 (2020.03.10) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.2.unitypackage)

#### 기능 개선/변경
* Android - Split Application Binary(OBB) 지원
    * OBB에 포함된 Streaming Assets 리소스와 업로드된 리소스를 비교 다운로드 기능 추가
    * API 추가
        * DownloadConfig.CheckAndroidObb

### 1.6.1 (2020.01.21) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.1.unitypackage)

#### 버그 수정
* 다운로드 검사할 파일이 없는 경우 발생하던 예외 수정


### 1.6.0 (2019.12.24) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.6.0.unitypackage)

#### 기능 개선/변경
* 사전 다운로드 용량을 확인하기 위해 API 추가(CheckDownload)
* API 변경
    * DownloadResult.IsSuccessful (Obsolete) → DownloadResult.Code
    * ProgressInfo.TotalFileNumber (Obsolete) → ProgressInfo.TotalFileCount
    * ProgressInfo.TotalReceivedBytes (Obsolete) → ProgressInfo.DownloadedBytes


### 1.5.9 (2019.10.29) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.9.unitypackage)

#### 기능 개선/변경
* 통계 지표 개선

### 1.5.8 (2019.07.29) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.8.unitypackage)

#### 버그 수정
* 특정 Android에서 다운로드 완료 처리 중 크래시가 발생하던 현상 수정


### 1.5.7 (2019.06.25) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.7.unitypackage)

#### 기능 개선/변경
* About 메뉴 추가
* 전체 리소스 다운로드 시 다운로드할 리소스가 하나도 없는 경우 결과 코드를 성공(SUCCESS_NO_DIFFERENCE)으로 전달
* 폴더 구조 변경
    * Assets/SmartDL/ → Assets/TOAST/SmartDL
    * `기존에 설치된 SmartDL 폴더를 삭제한 후 가져와야(import) 합니다.`

### 1.5.6 (2018.12.27) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.6.unitypackage)

#### 버그 수정
* 다운로드 취소 시 결과 콜백이 호출되지 않는 문제 수정

#### 기능 개선/변경
* Common
    * [ResultCode 리뉴얼](/Game/Smart%20Downloader/ko/error-code)
    * [주의] 기존 SDK에서 업데이트할 경우 오류 발생
* iOS
    * iOS 12 지원
* Standalone(Windows)
    * DLL 이름 및 경로 변경
        * smartnative_x86.dll → x86/smartnative.dll
        * smartnative_x64.dll → x86_64/smartnative.dll


### 1.5.5 (2018.11.27) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.5.unitypackage)

#### 버그 수정
* IL2CPP 빌드 지원
* 간헐적으로 macOS에서 IP 주소를 얻지 못하는 문제 수정


### 1.5.4 (2018.10.23) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.4.unitypackage)

#### 기능 개선/변경
* Unity 2018.2 지원
* 경로 및 파일을 선택해서 다운로드하는 기능 제공
* 다운로드 파일 크기 계산 개선
* 예제 코드 네임스페이스 추가

#### 버그 수정
* iOS에서 파일명에 한글 포함 시 다운로드되지 않는 문제 수정
* 파일명과 디렉터리명에 일부 특수문자 포함 시 다운로드 되지 않는 문제 수정



### 1.5.3 (2018.06.05) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.3.unitypackage)

#### 기능 개선/변경
* 재시도 로직 추가
* 연결 타임아웃 / 읽기 타임아웃 분리


### 1.5.1 (2018.04.18) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.1.unitypackage)

#### 버그 수정
* Unity 최적화 옵션 설정으로 발생하는 링크 오류 수정


### 1.5.0 (2018.02.22) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.5.0.unitypackage)

#### 기능 개선/변경
* Smart Downloader 내 개별 단위인 <b>서비스</b> 추가
* Core 라이브러리의 의존도 제거
* API 변경
    * 사용성 개선을 위한 API 변경


### 1.2.0 (2017.10.26) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/Smart-downloader-1.2.0.unitypackage)

#### 기능 개선/변경
* 안정성 강화
    * 내부 Core SDK 의존도 제거
    * Native 라이브러리 의존도 감소

### 1.1.0 (2017.02.23) [SDK 다운로드](https://static.toastoven.net/toastcloud/sdk_download/Smart%20Downloader/SmartDownloaderSDK_v1.1.0.unitypackage)

#### 기능 개선/변경
* class Name 변경(DLCSkin -> SmartDLUnitySkin).
* 정적 API만 제공

