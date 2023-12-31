# Readarr 설정
이 페이지에서는 Readarr에서 사용 가능한 모든 설정과 작동 방식을 설명합니다. 이 페이지는 포괄적인 "Readarr 설정 방법"이 아닙니다. 그런 정보가 필요한 경우 [빠른 시작](/readarr/quick-start-guide) 페이지를 참조하십시오.

# 메뉴 옵션
설정 페이지로 이동하려면 왼쪽 메뉴에서 설정을 선택하십시오. 다음 하위 메뉴 옵션을 사용할 수 있습니다:

![settings_1_menu.png](/assets/readarr/settings_1_menu.png)

또한 각 개별 설정 페이지에는 메뉴 상단에 일부 옵션이 있습니다:

![settings_2_topmenu.png](/assets/readarr/settings_2_topmenu.png)

- 고급 옵션 숨기기/보이기는 아래에서 "(고급 옵션)"으로 표시된 항목에 중요합니다. 그렇지 않으면 표시되지 않습니다. 이러한 메뉴 항목은 스크린샷에서 주황색으로 표시됩니다.

- 화면을 떠나기 전에 변경 사항을 저장해야 합니다. 디스크 아이콘을 클릭하여 저장합니다. 변경 사항이 없으면 "변경 사항 없음"이 표시되고 회색으로 표시됩니다.

# 미디어 관리

> 이 설정 중 일부는 "고급 설정 표시"를 통해서만 볼 수 있습니다. 이는 상단 바의 검색 바 아래에 있습니다{.is-info}

## 루트 폴더

- 구성된 루트 폴더(라이브러리 폴더) 목록이 표시됩니다.
- 새로운 루트 폴더를 추가하려면 <kb>+</kb> 버튼을 클릭하거나 기존 카드를 클릭하여 편집할 수 있습니다.

### 루트 폴더 설정

- 이름 - UI 목적을 위한 루트 폴더의 이름
- 경로 - 책 라이브러리가 포함된 폴더, 즉 Readarr에서 본 최종 대상입니다.
  - 다운로드 클라이언트가 파일을 저장하는 위치와 달라야 합니다.
  - 도커와 Calibre 통합을 사용하는 경우, 마운트는 도서 폴더와 동일해야 합니다.

{#calibre}

- Calibre 특정 설정 (Calibre 사용이 활성화된 경우에만)
  - Calibre 사용 - Calibre 콘텐츠 서버를 사용하여 루트 폴더를 관리할 수 있도록 활성화/비활성화합니다.

> \* 기존 루트 폴더에서는 이 기능을 **활성화할 수 없습니다**.
> \* Calibre를 사용하는 기존 루트 폴더에서는 이 기능을 **비활성화할 수 없습니다**.
> \* Calibre 콘텐츠 서버가 필요하며 Calibre 웹이나 Calibre와는 호환되지 않습니다.
> \* Calibre 통합에서 하드링크는 작동하지 않습니다.
> \* Calibre에서 `콘텐츠 서버에 액세스하려면 사용자 이름과 암호를 요구` 옵션이 활성화되어 있어야 합니다.
> \* Calibre에서 `콘텐츠 서버에 액세스하려면 사용자 이름과 암호를 요구` 옵션이 활성화되어 있지 않으면 `익명 사용자는 변경을 할 수 없습니다`라는 오류가 발생합니다.
{.is-warning}

- Calibre 호스트 - Calibre 콘텐츠 서버의 호스트 IP/도메인
- Calibre 포트 - Calibre 콘텐츠 서버가 수신 대기 중인 포트
- (고급) Calibre URL 기본값 - Calibre URL에 접두사 추가 (예: `http://[호스트]:[포트]/[URL 기본값]`)
- Calibre 사용자 이름 - Calibre 콘텐츠 서버에 액세스하는 데 사용할 사용자 이름
- Calibre 암호 - Calibre 콘텐츠 서버에 액세스하는 데 사용할 암호
- Calibre 라이브러리 - Calibre 콘텐츠 서버 라이브러리 이름. 기본값은 비워 둡니다.
- 형식으로 변환 - (선택 사항) Calibre 콘텐츠 서버에게 다른 형식으로 변환하도록 요청하는 쉼표로 구분된 목록입니다.
  - 현재 옵션 목록은 앱 내의 (i) 아이콘을 확인하십시오.
  - 옵션: MOBI, EPUB, AZW3, DOCX, FB2, HTMLZ, LIT, LRF, PDB, PDF, PMLZ, RB, RTF, SNB, TCR, TXT, TXTZ, ZIP
- Calibre 출력 프로필 - 사용할 Calibre 콘텐츠 서버 출력 프로필 선택
  - 출력 프로필은 Calibre 콘텐츠 서버 변환 시스템에게 생성된 문서를 지정된 장치에 맞게 최적화하는 방법을 알려줍니다(예: 장치 화면 크기에 맞게 이미지 크기 조정). 일부 경우에는 출력 프로필을 사용하여 특정 장치에 대한 출력을 최적화할 수 있지만, 이는 거의 필요하지 않습니다.
- SSL 사용 - Calibre 콘텐츠 서버에 대한 SSL(HTTPS) 사용 활성화 또는 비활성화
- 모니터 - 이 폴더에서 감지된 책에 대한 모니터링 옵션 구성
  - 모든 책 - 모든 책 모니터링
  - 미래 책 - 아직 출시되지 않은 책 모니터링
  - 누락된 책 - 파일이 없거나 아직 출시되지 않은 책 모니터링
  - 기존 책 - 파일이 있거나 아직 출시되지 않은 책 모니터링
  - 첫 번째 책 - 첫 번째 책 모니터링. 다른 모든 책은 무시됩니다.
  - 최신 책 - 최신 책 및 미래 책 모니터링
  - 없음 - 명시적으로 추가하지 않는 한 책은 모니터링되지 않습니다.
- 품질 프로필 - 이 폴더에서 감지된 책 및 작가의 기본 품질 프로필
- 메타데이터 프로필 - 이 폴더에서 감지된 작가에 대해 사용할 메타데이터 프로필 선택. 명시적으로 추가되거나 감지된 책만 로드하려면 "없음"을 선택하십시오.
- 기본 Readarr 태그 - 이 폴더에서 감지된 작가에 대한 기본 태그

> Windows 사용자가 아닌 경우:
> \* NFS 마운트를 사용하는 경우 `nolock`이 활성화되어 있는지 확인하십시오.
> \* SMB 마운트를 사용하는 경우 `nobrl`이 활성화되어 있는지 확인하십시오.
{.is-warning}

## 원격 경로 매핑

- 원격 경로 매핑은 원격 경로를 찾아서 로컬 경로로 대체하는 기능입니다. 이는 주로 mergerfs 등을 사용한 병합된 로컬/원격 설정 또는 애플리케이션과 다운로드 클라이언트 또는 Calibre가 동일한 서버에 없는 경우에 사용됩니다.
- 자세한 내용은 [다운로드 클라이언트 => 원격 경로 매핑](#remote-path-mappings-1) 섹션을 참조하십시오. `<Download Client>`를 `<Calibre>`로 바꾸십시오.

## 책 파일 이름 지정

![bookfilenaming.png](/assets/readarr/bookfilenaming.png)

**Calibre 통합을 사용하는 경우, 책 파일 이름을 지정할 수 없습니다. Calibre가 대신 처리합니다. Calibre를 사용하지 않는 경우에만 이러한 설정을 변경해야 합니다.**

> Readarr가 베타 버전인 동안 Calibre를 사용하는 경우, Calibre에서 의도하지 않은 버그가 발생할 수 있으므로 Readarr에서 이름 바꾸기를 비활성화하는 것이 좋습니다. `{.is-info}

일반적으로 사용되는 이름 지정 체계는 다음과 같습니다:

- 표준 책 형식
  - `{Book Title}\{Author Name}` - `{Book Title}`은 `Cujo`라는 폴더와 그 하위 디렉토리에 `Stephen King - Cujo.m4b`라는 이름의 파일이 포함됩니다.

- 작가 폴더 형식
  - `{Author Name}`은 `Stephen King`이라는 결과를 출력합니다.

## 책 이름 지정

- 책 이름 변경 - 이 옵션을 해제하면(체크 박스에 체크하지 않음) 이름 변경이 비활성화된 경우 기존 파일 이름을 사용합니다.
  - 체크하지 않은 경우:
    - 다운로드 클라이언트 가져오기
      - 다운로드 클라이언트의 릴리스 제목을 사용합니다.
    - 수동(임시) 가져오기: 원본 파일 이름

> 책 이름 변경을 체크하지 않으면 아래의 이름 지정이 적용되지 않습니다. Readarr에게 아무런 이름 변경도 원하지 않는다고 알렸기 때문에 책은 작가 폴더로 직접 가져와집니다.
{.is-info}

> Calibre를 사용하는 경우에는 적용되지 않습니다. Calibre는 자체적인 내부 스키마를 사용하여 파일/폴더 이름을 처리합니다.
{.is-info}

- 잘못된 문자 대체 - 비활성화된 경우 Readarr는 잘못된 문자를 제거합니다. 활성화된 경우 Readarr는 잘못된 문자를 대체합니다. 예: `\ # / $ * < >` 등

### 표준 책 형식

- 이름 지정 선택

- 드롭다운 상자(오른쪽 상단)
  - 왼쪽 상자 - 공백 처리
    - `공백 ( )` - 이름에 공백 사용(기본값)
    - `마침표 (.)` - 이름에 공백 대신 마침표 사용
    - `밑줄 (_)` - 이름에 공백 대신 밑줄 사용
    - `대시 (-)` - 이름에 공백 대신 대시 사용
  - 오른쪽 상자 - 대소문자 처리
    - `기본 대소문자` - 제목을 대문자와 소문자로 만듭니다(~camel-case) (기본값)
    - `대문자` - 제목을 모두 대문자로 만듭니다.
    - `소문자` - 제목을 모두 소문자로 만듭니다.

### 작가

- `{Author Name}` = 작가 이름
- `{Author NameThe}` = 작가 이름, The
- `{Author CleanName}` = 작가 이름
- `{Author SortName}` = Name, Author
- `{Author Disambiguation}` = 동일한 이름을 가진 여러 작가에 대한 구분을 위해 GoodReads에서 사용되는 작가 이름

### 책

- `{Book Title}` = 책 제목!: 부제목!
- `{Book TitleThe}` = 책 제목!, The: 부제목!
- `{Book CleanTitle}` = 책 제목: 부제목
- `{Book TitleNoSub}` = 책 제목!
- `{Book TitleTheNoSub}` = 책 제목!, The
- `{Book CleanTitleNoSub}` = 책 제목
- `{Book Subtitle}` = 부제목!
- `{Book SubtitleThe}` = 부제목!, The
- `{Book CleanSubtitle}` = 부제목
- `{Book Disambiguation}` = 책 이름! (GoodReads에서 사용되는 구분 제목)
- `{Book Series}` = 시리즈 제목
- `{Book SeriesPosition}` = 1
- `{Book SeriesTitle}` = 시리즈 제목 #1
- `{PartNumber:0}` 또는 `{PartNumber:0}` = 2
- `{PartNumber:00}` = 02
- `{PartCount}` 또는 `{PartCount:0} = 9
- `{PartCount:00}` = 09

### 출시일

- `{Release Year}` = 2016
- `{Release YearFirst}` = 2015
- `{Edition Year}` = 2016

### 품질

- `{Quality Full}` = AZW3 Proper
- `{Quality Title}` = AZW3

### 미디어 정보

- `{MediaInfo AudioCodec}` = MP3
- `{MediaInfo AudioChannels}` = 2.0
- `{MediaInfo AudioBitRate}` = 320kbps
- `{MediaInfo AudioBitsPerSample}` = 24bit
- `{MediaInfo AudioSampleRate}` = 44.1kHz

### 기타

- `{Release Group}` = Rls Grp
- `{Preferred Words}` = iNTERNAL

### 원본

- `{Original Title}` = Author.Name.Book.Name.2018.AZW3-EVOLVE
- `{Original Filename}` = 01-book name

> 원본 파일 이름은 권장되지 않습니다. 이는 원래 파일 이름 그대로이며 t1i0p3s7i8yuti와 같이 난독화될 수 있습니다. 원본 제목은 릴리스 이름이므로 대신 사용해야 합니다.
{.is-info}
  
## 작가 폴더 형식

- (고급 옵션) 여기에서 작가 폴더 이름의 명명 규칙을 설정합니다.

> Calibre를 사용하는 경우에는 적용되지 않습니다. Calibre는 자체적인 내부 스키마를 사용하여 파일/폴더 이름을 처리합니다.
{.is-info}

### 작가

- `{Author Name}` = 작가 이름
- `{Author NameThe}` = 작가 이름, The
- `{Author CleanName}` = 작가 이름
- `{Author SortName}` = Name, Author
- `{Author Disambiguation}` = 동일한 이름을 가진 여러 작가에 대한 구분을 위해 GoodReads에서 사용되는 작가 이름

## 폴더

![mm_folders.png](/assets/readarr/mm_folders.png)
  
- (고급 옵션) 빈 작가 폴더 생성 - 새 작가가 추가될 때 빈 작가 폴더를 생성하려면 상자를 선택합니다.
- (고급 옵션) 빈 작가 폴더 삭제 - 책이 없는 경우 빈 작가 폴더를 삭제하려면 상자를 선택합니다.
  
> 두 상자 중 하나를 선택할 수 있지만, 두 상자를 모두 선택해서는 안 됩니다. {.is-warning}

> Calibre를 사용하는 경우에는 적용되지 않습니다. Calibre는 자체적인 내부 스키마를 사용하여 파일/폴더 이름을 처리합니다.
{.is-info}

## 가져오기
  
![mm_importing.png](/assets/readarr/mm_importing.png)
  
- (고급 옵션) 무료 공간 확인 건너뛰기 - 가져오기 전에 무료 공간 확인을 건너뛰려면 이 옵션을 활성화합니다.
- (고급 옵션) 최소 무료 공간 - 가져오기가 중지되기 전에 드라이브가 가져야 하는 최소 무료 공간을 입력합니다.
- (고급 옵션) 복사 대신 하드링크 사용 - 이 옵션을 선택하면 복사 대신 하드링크를 사용합니다(토렌트의 경우). 이는 기본적으로 활성화되어 있습니다.
  
> 가능한 경우 이를 사용하는 것이 좋습니다. 하드링크를 사용하려면 소스/대상이 동일한 파일 시스템(드라이브, 파티션) 및 마운트 포인트에 있어야 합니다. [자세한 내용은 TRaSH의 하드링크 가이드를 참조하세요](https://trash-guides.info/hardlinks/)
  
- 추가 파일 가져오기 - 가져올 때 책 폴더 내에 있는 지정된 추가 파일을 가져옵니다.
- (고급 옵션) 추가 파일 가져오기 - 추가 파일 가져오기가 활성화된 경우 가져올 확장자의 쉼표로 구분된 목록을 입력합니다.

> 오디오북에 Readarr을 사용하는 경우 이 목록에 .cue를 추가해야 합니다. 이 파일에는 챕터 정보가 포함되어 있습니다!
{.is-info}
  
## 파일 관리
  
  ![mm_filemgmt.png](/assets/readarr/mm_filemgmt.png)

- 삭제된 책 무시 - Readarr의 루트 폴더에서 삭제되거나 접근할 수 없는 책을 모니터링하지 않도록 이 옵션을 선택합니다.
- 적절한 파일 및 리팩 다운로드 - 자동으로 적절한 파일 및 리팩을 업그레이드할지 여부를 설정합니다. 리팩/리팩 대신 우선 순위 단어 점수를 기준으로 정렬하려면 `선호하지 않음`을 사용하세요.
  - 선호 및 업그레이드 - 리팩과 리팩을 비-리팩 및 비-리팩보다 높은 순위로 취급합니다. 새로운 리팩과 리팩을 현재 릴리스의 업그레이드로 취급하지 않습니다.
  - 자동으로 업그레이드하지 않음 - 리팩과 리팩을 비-리팩 및 비-리팩보다 높은 순위로 취급합니다. 새로운 리팩과 리팩을 현재 릴리스의 업그레이드로 취급하지 않습니다.
  - 선호하지 않음 - 이렇게 하면 리팩과 리팩이 무시됩니다. [선호 단어](#릴리스-프로필)로 해당 사항을 관리해야 합니다.
  
> \* `PROPER` - 이전 릴리스에 문제가 있음을 의미합니다. PROPER로 태그된 다운로드는 해당 문제가 해당 릴리스에서 해결되었음을 보여줍니다. 이는 원래 릴리스를 출시하지 않은 그룹에 의해 수행됩니다.
> \* `REPACK` - 이전 릴리스에 문제가 있으며 원래 그룹에 의해 수정되었습니다. REPACK로 태그된 다운로드는 해당 문제가 해당 릴리스에서 해결되었음을 보여줍니다. 이는 원래 릴리스를 출시한 그룹에 의해 수행됩니다.
{.is-info}

- (고급 옵션) 파일 변경 감지를 위해 루트 폴더 감시 - 루트 폴더에 변경 사항이 감지되면 다시 스캔하도록 이 옵션을 선택합니다.
- (고급 옵션) 새로 고침 후 작가 폴더 다시 스캔 - 작가를 새로 고침한 후 작가 폴더를 언제 다시 스캔할지 선택합니다.
  - 항상 - 이는 작업 일정에 따라 작가 폴더를 다시 스캔합니다.
  - 수동 새로 고침 후 - 디스크를 수동으로 다시 스캔해야 합니다.
  - 절대로 - 그대로입니다. 작가 폴더를 다시 스캔하지 않습니다.
- (고급 옵션) 지문 인식 허용 - 책 매칭의 정확도를 높이기 위해 지문 인식을 어떻게 처리할지 선택합니다. 이는 CPU/디스크 시간을 소비합니다.
  - 항상 - 가능한 경우 항상 지문 인식을 사용합니다.
  - 새로 가져온 항목에만 - 새로 가져온 릴리스에만 지문 인식을 사용합니다.
  - 절대로 - 그대로입니다. 지문 인식을 사용하지 않습니다.
- (고급 옵션) 파일 날짜 변경 - 가져오기/다시 스캔 시 파일 날짜를 변경합니다.
  - 없음 - Readarr은 지정된 파일 브라우저에 표시되는 날짜를 변경하지 않습니다.
  - 책 출시 날짜 - 책이 출시된 날짜입니다.
- (고급 옵션) 휴지통 - 책 파일이 영구적으로 삭제되는 대신 여기에 이동합니다.
- (고급 옵션) 휴지통 정리 - 파일이 영구적으로 삭제되기 전에 얼마나 오래 있어야 하는지 설정합니다.

> 휴지통을 사용하는 것이 매우 권장됩니다. 파일을 삭제하는 것은 쉽지만 휴지통을 사용하면 파일을 복구하기 쉽습니다.
{.is-warning}

# 권한

- 권한 설정 - 파일 가져오기/이름 바꾸기 시 `chmod`를 실행해야 합니까?
  - 폴더에 chmod 적용 - 가져오기/이름 바꾸기 시 미디어 폴더와 파일에 대해 8진수를 적용합니다.

> 드롭다운 상자에는 사용할 수 있는 매우 일반적으로 사용되는 권한의 미리 설정된 목록이 있습니다. 그러나 원하는 경우 수동으로 폴더 8진수를 입력할 수 있습니다.
{.is-info}

> 이는 `Readarr`를 실행하는 사용자가 파일의 소유자인 경우에만 작동합니다. 다운로드 클라이언트가 올바른 권한을 설정하도록 하는 것이 좋습니다.
{.is-warning}

- chown 그룹 - 그룹 이름 또는 GID를 입력하세요. 원격 파일 시스템의 경우 GID를 사용하세요.

> 이는 `Readarr`를 실행하는 사용자가 파일의 소유자인 경우에만 작동합니다. 다운로드 클라이언트가 올바른 권한을 설정하도록 하는 것이 좋습니다.
{.is-warning}

# 프로필

## 품질 프로필

품질 프로필은 라이브러리의 책에 대해 허용되는 형식을 결정하는 데 사용됩니다.
  
![qualityprofile.png](/assets/readarr/qualityprofile.png)

- 다운로드할 책의 품질에 대한 프로필을 설정하세요.

> 기존 프로필을 선택하거나 추가 프로필을 추가할 때 새 창이 나타납니다.
> 참고: 파란색 상자가 있는 품질은 해당 프로필의 미디어가 계속해서 업그레이드될 품질입니다.
{.is-info}

- 플러스 아이콘 (<kb>+</kb>) - 새 품질 프로필 생성

- 이름 - 생성 중인 품질 프로필에 대한 **고유한** 이름을 입력하세요.
- 업그레이드 허용 - 이 옵션을 선택하고 특정 책의 첫 번째 릴리스로 `EPUB`을 다운로드하도록 지정한 후 나중에 `AZW3`을 업로드할 수 있는 경우 `Upgrade Until`에서 더 나은 품질로 자동 업그레이드됩니다.
  - Upgrade Until - 이 품질에 도달하면 Readarr은 더 이상 책을 다운로드하지 않습니다.

> 참고: 이는 `Qualities` 섹션에서 `AZW3`이 `EPUB`보다 높은 경우에만 적용됩니다.
{.is-warning}

- 품질 - 목록에서 높은 순서대로 나열된 품질입니다. 사용 가능한 상태와 관계없이 더 선호되는 품질이 높은 순서대로 나열됩니다. 동일한 그룹 내의 품질은 동일합니다. 선택된(활성화된) 품질만 원하는(허용된) 것입니다.
  - 그룹 편집 - 일부 품질은 목록의 크기를 줄이기 위해 그룹화됩니다. 가장 대표적인 예는 `WebDL`과 `WebRip`입니다. 이들은 매우 유사하며 일반적으로 유사한 비트율을 가집니다. 그룹을 편집할 때 각 그룹 내에서의 우선 순위를 변경할 수 있습니다.

  - [품질 보기](#품질-정의)

> 기본적으로 품질은 "최악"(아래)에서 "최고"(위)로 설정됩니다.
{.is-info}

## 메타데이터 프로필

메타데이터 프로필은 새 작가가 추가될 때 GoodReads에서 어떤 책을 해당 작가의 하위에 추가할지 결정하는 데 사용됩니다.

- 플러스 아이콘 (<kb>+</kb>) - 새 메타데이터 프로필 생성

![metaprofiles.png](/assets/readarr/metaprofiles.png)
  
- 이름 - 메타데이터 프로필에 대한 **고유한** 이름을 입력하세요.
- 최소 인기도 - 작가에게 책을 추가하기 위해 책이 가져야 하는 최소 인기도를 입력하세요.

> 이 값을 너무 높게 설정하면 책이 Readarr에 추가되지 않을 수 있지만, 너무 낮게 설정하면 모호한 출판물이 표시될 수 있습니다.
{.is-warning}

> 이 값을 정확히 `10000000000`으로 설정하여 `None`과 동등한 프로필을 만들 수 있지만, 다른 판별 및 책 필터링은 허용됩니다. `None`은 메타데이터 필터를 적용하지 않으며 외국판을 받을 수 있습니다.
{.is-info}

- 최소 페이지 - 작가에게 추가할 책이 가져야 하는 최소 페이지 수를 입력하세요.
- 출시 날짜가 없는 책 건너뛰기 - 출시 날짜가 없는 책을 건너뛰도록 설정합니다.
- ISBN 또는 ASIN이 없는 책 건너뛰기 - ISBN 또는 ASIN 번호가 없는 책을 건너뛰도록 설정합니다.
- 일부 책 및 세트 건너뛰기 - 일부 책 및 세트를 건너뛰도록 설정합니다.
- 보조 시리즈 책 건너뛰기 - 보조 시리즈 책을 건너뛰도록 설정합니다.
- 허용되는 언어 - ISO 639-3 언어 코드의 쉼표로 구분된 목록이나 책에 대한 허용되는 언어에 대해 'null'을 입력하세요.
- 포함하지 않아야 할 내용 - 책 제목에 포함되지 않아야 하는 단어나 구를 입력하세요.
  
> 여러 메타데이터 프로필을 만들고 필요에 따라 각 작가에 별도의 프로필을 적용할 수 있습니다. 그러나 특정 작가에 대해 단일 메타데이터 프로필만 적용할 수 있습니다.
{.is-info}
  
## 릴리스 프로필

릴리스 프로필은 인덱서 릴리스 이름이 다운로드에 적합한지 여부를 결정하는 데 사용됩니다.

![releaseprofiles.png](/assets/readarr/releaseprofiles.png)  
  
- 프로필 활성화 - 이 프로필을 활성화하려면 확인란을 선택하세요.
- 포함해야 할 내용 - 유효한 것으로 간주하려면 릴리스 이름에 반드시 포함되어야 하는 단어나 구를 추가하세요.
- 포함하지 않아야 할 내용 - 유효한 것으로 간주하려면 릴리스 이름에 반드시 포함되지 않아야 하는 단어나 구를 추가하세요.
- 선호하는(단어) - 더 선호되거나 덜 선호되는 용어 또는 정규식을 점수(양수 및 음수)와 함께 추가할 수 있습니다. 예를 들어, "unabridged"를 양수 점수로 선호할 수 있습니다.
  
> 기존 파일보다 선호하는 단어 점수가 높은 릴리스는 항상 업그레이드입니다!
{.is-info}
  
- 이름 변경 시 선호 단어 포함 - 선호하는 단어(또는 정규식 일치)를 `{Preferred Words}` 파일 이름 할당 토큰에 포함하려면 이 확인란을 선택하세요.
  
> 파일 이름에 `{Preferred Words}`를 포함하고 있으며 이를 사용하는 경우 이 확인란을 선택해야 합니다. 그렇지 않으면 다운로드 루프에 빠질 수 있습니다.
{.is-warning}

- 인덱서 - 이 드롭다운에서 이 릴리스 프로필을 단일 인덱서로 제한할 수 있습니다. 거의 항상 `(any)`로 남겨두어야 합니다.
- 태그 - 동일한 태그를 가진 작가에게 이 태그를 적용할 수 있도록 하려면 여기에 태그를 입력하세요. 여기에 태그를 적용하지 않으면 이 프로필은 모든 작가에 적용됩니다.

## 지연 프로필

- 지연 프로필을 사용하면 Readarr이 선호하는 기준과 일치하는 릴리스를 찾을 때까지 다운로드되는 릴리스 수를 줄일 수 있습니다.
- 프로토콜 - 이는 사용자가 선호하는 다운로드 프로토콜(Usenet 또는 BitTorrent)에 따라 `Usenet` 또는 `Torrent`일 수 있습니다.
- Usenet 지연 - 다운로드가 시작되기 전에 기다릴 분의 수를 설정합니다.
- Torrent 지연 - 다운로드가 시작되기 전에 기다릴 분의 수를 설정합니다.
- 최고 품질인 경우 바이패스 - 우선 프로토콜에 가장 높은 품질 프로필이 있는 경우 지연을 우회합니다.
- 태그 - 이 지연 프로필에 태그를 지정하면 이 규칙에 따라 플레이할 수 있는 특정 책에 태그를 지정할 수 있습니다.
- 렌치 아이콘 - 이를 편집할 수 있습니다.
- 플러스 아이콘 (<kb>+</kb>) - 새 지연 프로필 생성

### 사용 예

일부 미디어는 출시 후 몇 시간 내에 다양한 품질의 여러 릴리스를 받을 수 있으며, 지연 프로필을 사용하지 않으면 Readarr은 모든 릴리스를 다운로드하려고 시도할 수 있습니다. 지연 프로필을 사용하면 Readarr은 처음 몇 시간 동안의 릴리스를 무시할 수 있습니다.

지연 프로필은 Usenet 또는 BitTorrent 중 하나를 강조하려는 경우에도 유용합니다. (예: 예제 3 참조)

### 지연 프로필 작동 방식

타이머는 Readarr이 책에 대한 릴리스를 감지하는 즉시 시작됩니다. 이 릴리스는 큐에 나타나며 지연을 나타내는 시계 아이콘이 표시됩니다.

> 시계는 릴리스가 업로드된 시간이 아닌 Readarr이 해당 릴리스를 감지한 시간부터 시작됩니다. {.is-info}

지연 기간 동안 새로운 릴리스가 발생하면 Readarr이 이를 알립니다. 지연 타이머가 만료되면 Readarr은 품질 기준과 가장 일치하는 단일 릴리스를 다운로드합니다.

타이머 기간은 Usenet과 토렌트마다 다를 수 있습니다. 각 프로필은 하나 이상의 태그와 연결할 수 있어 특정 프로필을 특정 책에 적용할 수 있습니다. 태그가 지정되지 않은 지연 프로필은 기본값으로 간주되며 특정 태그가 없는 모든 책에 적용됩니다.

> 지연 프로필은 인덱서가 릴리스를 업로드한 타임스탬프부터 시작합니다. 이는 설정한 분 수보다 오래된 콘텐츠는 지연 프로필 설정에 영향을 받지 않으며 즉시 다운로드됩니다. 또한 **수동 검색**으로 찾은 콘텐츠(비 RSS 피드 검색)는 지연 프로필 설정을 무시합니다.
{.is-warning}

#### 예제

- 각 예제에서 사용자가 다음과 같은 품질 프로필을 활성화했다고 가정합니다: EPUB 이상은 허용되며 MOBI가 품질 기준 * AZW3이 가장 높은 순위 품질입니다.

##### 예제 1

- 이 간단한 예에서 프로필은 Usenet과 Torrent 모두에 대해 120분(2시간) 지연이 설정되어 있습니다.

- 오후 11:00에 Readarr이 첫 번째 책에 대한 첫 번째 릴리스를 감지하고 10:50에 업로드된 것으로 나타납니다. 120분 타이머가 시작됩니다. 오전 12:50에 Readarr은 지난 2시간 동안 찾은 모든 릴리스를 평가하고 MOBI가 가장 좋은 품질이므로 다운로드합니다.

- 오전 3:00에 MOBI로 된 다른 릴리스가 2:46에 인덱서에 추가되었습니다. 120분 타이머가 다시 시작됩니다. 오전 4:46에 가장 좋은 릴리스가 다운로드됩니다. 이제 품질 기준에 도달했으므로 책은 업그레이드할 수 없으며 Readarr은 새로운 릴리스를 찾지 않습니다.

- 언제든지 AZW3 릴리스가 발견되면 가장 높은 순위 품질이므로 즉시 다운로드됩니다. 현재 활성화된 지연 타이머가 있으면 취소됩니다.

##### 예제 2

- 이 예제에서는 Usenet과 토렌트에 대해 다른 타이머가 설정되어 있습니다. Usenet에는 120분 타이머가 설정되어 있고 BitTorrent에는 180분 타이머가 설정되어 있습니다.

- 오후 11:00에 Readarr이 첫 번째 책에 대한 첫 번째 릴리스를 감지하고 10:15에 인덱서에 추가된 것으로 나타납니다. 오전 12:15에 Readarr은 지난 2시간 동안 찾은 모든 릴리스를 평가하고 허용 가능한 Usenet 릴리스가 있다면 가장 좋은 릴리스를 다운로드하고 타이머가 종료됩니다. 그렇지 않으면 Readarr은 오전 12:15에 가장 좋은 릴리스를 다운로드하며 어느 소스에서 나왔든 상관하지 않습니다.

##### 예제 3

- 지연 프로필의 일반적인 사용 사례 중 하나는 다른 프로토콜(Usenet 또는 BitTorrent)보다 우선시하려는 경우입니다. 예를 들어, Usenet에 아무런 업로드가 없는 경우에만 BitTorrent 릴리스를 다운로드하려는 경우입니다.

- BitTorrent에는 60분 타이머가 설정되어 있고 Usenet에는 0분 타이머가 설정되어 있습니다.

- 첫 번째로 감지된 릴리스가 Usenet에서 온 경우 Readarr은 즉시 다운로드합니다.

- 첫 번째 릴리스가 BitTorrent에서 온 경우 Readarr은 60분 타이머를 설정합니다. 그 동안 품질 기준에 부합하는 Usenet 릴리스가 감지되면 BitTorrent 릴리스는 무시되고 Usenet 릴리스가 다운로드됩니다.

- Completed Download Handling - Remove - If enabled, Readarr will remove the completed downloads from your download client after importing them. This option is available for both Usenet and Torrents.
- Remove Imported Downloads - If enabled, Readarr will remove the imported downloads from your download client after importing them. This option is available for both Usenet and Torrents.
- Failed Download Handling - If enabled, Readarr will handle failed downloads differently. By default, failed downloads are left in the download client's history and not imported. If this option is enabled, failed downloads will be removed from the download client's history.
- Remove Failed Downloads - If enabled, Readarr will remove the failed downloads from your download client's history. This option is available for both Usenet and Torrents.
- Remove Completed Downloads - If enabled, Readarr will remove the completed downloads from your download client's history. This option is available for both Usenet and Torrents.
- Remove Deleted Downloads - If enabled, Readarr will remove the deleted downloads from your download client's history. This option is available for both Usenet and Torrents.

> Note: It is important to configure your download client's settings correctly to ensure that Readarr can communicate with it and access the downloaded files.

- Readarr는 다운로드 요청을 클라이언트에 보내고, 다운로드 클라이언트 설정에서 구성한 레이블 또는 카테고리 이름과 연결합니다.
- Readarr는 해당 카테고리 이름을 사용하는 다운로드 클라이언트의 활성 다운로드를 모니터링합니다. 이는 다운로드 클라이언트의 API를 통해 모니터링됩니다.
- 다운로드가 완료되면, Readarr는 다운로드 클라이언트가 보고한 최종 파일 위치를 알게 됩니다. 이 파일 위치는 미디어 폴더와 별도로 어디에 있든 상관없습니다.
- Readarr는 완료된 파일 위치에서 비디오 파일을 스캔합니다. 비디오 파일 이름을 구문 분석하여 책과 일치시킵니다. 그렇게 할 수 있다면, 파일 이름을 지정된 사양에 따라 변경하고 지정된 라이브러리 폴더로 이동합니다.
- 다운로드에서 남은 파일은 휴지통이나 재활용통에 보내집니다.

BitTorrent 클라이언트를 사용하여 다운로드하는 경우, 프로세스는 약간 다릅니다:

- 완료된 파일은 시드를 할 수 있도록 원래 위치에 남겨집니다. 파일이 할당된 라이브러리 폴더로 가져올 때 Readarr는 파일을 하드링크로 만들려고 시도하거나 하드링크를 지원하지 않는 경우 복사(이중 공간 사용)로 대체합니다.
- 설정에서 "완료된 다운로드 처리 - 제거" 옵션이 활성화되어 있는 경우, Readarr는 원본 파일과 토렌트를 삭제하도록 토렌트 클라이언트에 요청하지만, 이는 클라이언트가 시딩이 완료되었고, 토렌트가 동일한 카테고리에 있는 경우에만 발생합니다. Readarr에서 지원하는 시딩 목표에 도달하고 토렌트가 일시 중지된 경우에만 이 작업이 수행됩니다.

### 다운로드 실패 처리

- 실패한 다운로드 처리는 SABnzbd와 NZBGet에만 호환됩니다.
- 실패한 다운로드 처리는 토렌트에는 적용되지 않으며, 이와 관련된 기능을 추가할 계획도 없습니다.

- 실패한 다운로드 처리 프로세스를 구성하는 여러 구성 요소가 있습니다:

- 다운로더 확인:
  - 대기열 - 암호로 보호된(암호화된) 릴리스를 실패로 표시한 다운로더의 대기열을 확인합니다.
  - 기록 - 복구할 충분한 양이 없거나 추출에 실패한 등 실패한 다운로드의 기록을 확인합니다.
- Readarr는 실패한 다운로드를 찾으면 다음과 같은 작업을 수행합니다:
  - Readarr의 기록에 실패 이벤트를 추가합니다.
  - 실패한 다운로드를 다운로드 클라이언트에서 제거하여 공간을 확보하고 다운로드된 파일을 지웁니다(선택 사항).
  - 대체 파일을 검색하기 시작합니다(선택 사항).
  - 차단 목록은 nzbs가 실패할 때 자동으로 건너뛸 수 있도록 해줍니다. 이는 Readarr에 의해 해당 nzb가 더 이상 자동으로 다운로드되지 않음을 의미합니다(수동 검색을 통해 여전히 다운로드할 수 있음).
  - Readarr에서 실패 다운로드의 동작을 제어하는 2개의 고급 옵션이 있습니다(현재 모두 기본 설정이 켜져 있음).

- 재다운로드 - 실패 후 동일한 파일을 검색할지 여부를 제어합니다.
- (고급 옵션) 제거 - 실패가 감지되면 다운로드 클라이언트에서 다운로드를 자동으로 제거해야 하는지 여부

## 원격 경로 매핑

- 원격 경로 매핑은 원격 경로를 찾아서 로컬 경로로 바꾸는 무식한 방식으로 작동합니다. 이는 주로 mergerfs 또는 유사한 병합된 로컬/원격 설정 또는 응용 프로그램과 다운로드 클라이언트가 동일한 서버에 없는 경우에 사용됩니다.
- 원격 경로 매핑은 다운로드 클라이언트가 완료된 데이터의 경로를 보고하는 방식에 따라 다른 서버에 있거나 \*Arr가 해당 폴더를 처리하지 않는 방식으로 사용됩니다.
- 일반적으로 원격 경로 매핑은 다운로드 클라이언트가 Linux에 있고 \*Arr가 Windows에 있는 경우 또는 그 반대인 경우에만 필요합니다. 원격 경로 매핑은 Docker 및 Native 클라이언트를 혼합하거나 원격 서버를 사용하는 경우에도 필요할 수 있습니다.
- 원격 경로 매핑은 무식한 검색/대체입니다(원격 값을 찾아서 지정된 호스트에 대한 로컬 값으로 대체합니다).
- 잘못된 경로에 대한 오류 메시지에 REPLACED 값이 포함되어 있지 않은 경우, 경로 매핑이 예상한 대로 작동하지 않습니다. 일반적인 해결 방법은 매핑을 추가하고 제거하는 것입니다.
- [원격 경로 매핑에 대한 자세한 정보는 TRaSH의 튜토리얼을 참조하십시오](https://trash-guides.info/Radarr/Radarr-remote-path-mapping/)

> \*Arr와 다운로드 클라이언트 모두 Docker 컨테이너인 경우 원격 경로 매핑이 필요한 경우는 드물지만, [Docker 가이드](/docker-guide)를 검토하거나 [TRaSH의 튜토리얼](https://trash-guides.info/hardlinks)을 따르는 것이 좋습니다.
{.is-info}

# 가져오기 목록

> 지원되는 목록 유형에 대한 정보는 [더 많은 정보 (지원)](/readarr/supported#lists) 페이지에서 찾을 수 있습니다.
{.is-info}

가져오기 목록을 사용하면 GoodReads 책장이나 다른 사용자로부터 자동으로 Readarr에 항목을 추가할 수 있습니다. 이는 Readarr 데이터베이스에 예상치 못한 항목을 많이 추가할 수 있으므로 주의해서 사용하십시오.

![importlists.png](/assets/readarr/importlists.png)

## 가져오기 목록

현재 보유한 목록을 표시하고 새 목록을 추가할 수 있습니다. 목록 추가에 대한 자세한 내용은 아래에서 자세히 설명합니다.

## 가져오기 목록 제외

여기에 있는 항목은 목록에서 추가되지 않도록 제외되었으며, 어떤 목록에서도 추가되지 않습니다. 항목을 제거하려면 해당 항목을 클릭하십시오.

## 가져오기 목록 추가

<kb>+</kb>를 클릭한 후 추가할 목록 유형을 선택합니다:

![addlist.png](/assets/readarr/addlist.png)

이 예에서는 GoodReads 책장 목록을 추가하려고 합니다.

![bookshelflist.png](/assets/readarr/bookshelflist.png)

- 이름 - 이 목록에 대한 이름을 입력합니다.
- 자동 추가 활성화 - 목록에 있는 항목을 자동으로 Readarr에 추가하도록 설정하려면 활성화합니다.

> 이렇게 하면 해당 작가의 모든 책과 모든 책이 Readarr에 추가됩니다!

- 모니터링 - 추가된 항목에 대한 모니터링 수준을 선택합니다. 유효한 옵션은 `없음`, `선택한 책`, `모든 작가의 책`입니다. 모든 책은 Readarr에 추가되지만 이 선택에 따라 모니터링 또는 모니터링 해제됩니다.
- 새 항목 검색 - 추가된 항목이 목록에서 추가될 때 누락된 모니터링 항목에 대한 검색을 Readarr에 시작하도록 설정하려면 활성화합니다. 많은 작가/모니터링 책을 추가하는 경우 시스템에 과부하를 줄 수 있습니다!
- 루트 폴더 - 이 목록에서 추가된 작가를 위한 루트 폴더를 선택합니다.
- 품질 프로필 - 이 목록에서 추가된 작가를 위한 품질 프로필을 선택합니다.
- 메타데이터 프로필 - 이 목록에서 추가된 작가를 위한 메타데이터 프로필을 선택합니다.
- Readarr 태그 - 이 목록에서 추가된 작가에 적용되는 태그를 선택합니다.

> 여기에 서술적인 태그를 추가하는 것이 매우 권장됩니다. 그렇지 않으면 이 목록이 Readarr에 이 항목을 추가한 것을 알 수 없으며, 한 번 추가된 후에는 이 정보를 다시 얻을 수 없습니다! 이 정보는 기록되지 않습니다!

목록은 기본적으로 매일 24시간마다 동기화되지만, `설정` => `작업` 페이지에서 수동으로 트리거할 수 있습니다. 이 프로세스를 그보다 더 빠르게 자동화할 수는 없습니다.

# 연결

> 지원되는 연결 유형에 대한 정보는 [더 많은 정보 (지원)](/readarr/supported#notifications) 페이지에서 찾을 수 있습니다.
{.is-info}

## 연결

연결은 Readarr가 외부와 통신하는 방법입니다.

- <kb>+</kb> 버튼을 누르면 다양한 엔드포인트를 구성할 수 있는 새 창이 나타납니다.

- 지원되는 알림 및 연결 목록은 [더 많은 정보 (지원)](/readarr/supported#notifications) 페이지에 있습니다.

## 연결 트리거

- 다운로드 시 - 책이 다운로드 가능하고 다운로드 클라이언트로 전송된 경우 알림을 받습니다.
- 릴리스 가져오기 시 - 책이 성공적으로 가져올 때 알림을 받습니다.
- 업그레이드 시 - 책이 더 나은 품질로 업그레이드될 때 알림을 받습니다.
- 다운로드 실패 시 - 책 다운로드가 실패한 경우 알림을 받습니다(유즈넷 전용).
- 가져오기 실패 시 - 책 다운로드가 가져오기에 실패한 경우 알림을 받습니다.
- 이름 변경 시 - 책이 이름을 변경할 때 알림을 받습니다.
- 작가 삭제 시 - 작가가 삭제될 때 알림을 받습니다.
- 책 삭제 시 - 책이 삭제될 때 알림을 받습니다.
- 책 파일 삭제 시 - 책 파일이 삭제될 때 알림을 받습니다.
- 업그레이드를 위한 책 파일 삭제 시 - 업그레이드를 위해 책 파일이 삭제될 때 알림을 받습니다.
- 책 다시 태그 시 - 책이 다시 태그될 때 알림을 받습니다.
- 건강 문제 시 - 건강 점검 실패 시 알림을 받습니다.
  - 건강 경고 포함 - 오류 외에도 건강 경고에 대한 알림을 받습니다.

# 메타데이터

{#write-metadata-to-book-files}

> 지원되는 메타데이터 소비자에 대한 정보는 [더 많은 정보 (지원)](/readarr/supported#metadata) 페이지에서 찾을 수 있습니다.
{.is-info}

이 페이지에서는 메타데이터 태그/커버를 생성/업데이트할 수 있습니다.

![metadata.png](/assets/readarr/metadata.png)

## Calibre 메타데이터

Calibre를 사용하여 전자책 컬렉션을 관리하는 경우 이 옵션을 사용하여 제어합니다.

- Calibre로 메타데이터 보내기
  - 모든 파일; GoodReads와 동기화 유지 - 모든 파일에 태그를 작성하고 GoodReads가 업데이트되면 업데이트합니다.
  - 모든 파일; 초기 가져오기만 - 모든 파일에 태그를 한 번 작성하고 GoodReads가 업데이트되면 업데이트하지 않습니다.
  - 새로운 다운로드만 - 새로운 다운로드만 가져올 때만 태그를 작성합니다.
- 표지 업데이트 - Calibre 콘텐츠 서버가 Readarr와 동일한 책 표지를 사용하도록 설정합니다.
- 책 파일에 메타데이터 포함 - Calibre 콘텐츠 서버가 책 파일에 메타데이터를 작성하고 포함하도록 설정합니다.

## 오디오 파일에 메타데이터 작성

오디오북을 사용하는 경우 이 옵션을 사용하여 제어합니다.

- 오디오 파일에 메타데이터 태그 작성
  - 모든 파일; GoodReads와 동기화 유지 - 모든 파일에 태그를 작성하고 GoodReads가 업데이트되면 업데이트합니다.
  - 모든 파일; 초기 가져오기만 - 모든 파일에 태그를 한 번 작성하고 GoodReads가 업데이트되면 업데이트하지 않습니다.
  - 새로운 다운로드만 - 새로운 다운로드만 가져올 때만 태그를 작성합니다.
- 기존 태그 제거 - Readarr에서 추가한 태그를 제외한 모든 태그를 파일에서 제거하도록 설정합니다.

# 태그

- Readarr의 태그 섹션은 Readarr의 다른 측면을 연결하는 데 사용됩니다.
- 태그는 다음과 같은 경우에 특히 유용합니다:

  - 릴리스 프로필
  - 인덱서
  - 가져오기 목록

- 태그는 릴리스 프로필, 인덱서, 가져오기 목록 및 작가/책을 연결하는 데 사용할 수 있습니다.
- 예를 들어:
  - 특정 작가/책이 특정 인덱서만 사용하도록 하려면 태그를 만들고 해당 작가/책과 인덱서에 태그를 할당합니다.
  - 특정 가져오기 목록이 특정 릴리스 프로필만 사용하도록 하려면 태그를 만들고 해당 가져오기 목록과 릴리스 프로필에 태그를 할당합니다.

> 가져오기 목록에는 위에서 언급한 내용 외에도 서술적인 태그를 추가하는 것이 매우 권장됩니다.

> 참고: 태그는 "품질 프로필", "메타데이터 프로필" 또는 기타 위에서 언급하지 않은 측면에는 영향을 주지 않습니다.
{.is-info}

# 일반

이 페이지는 다른 섹션에서 다루지 않는 일반적인 Readarr 설정을 위한 것입니다.

## 호스트

![genhost.png](/assets/readarr/genhost.png)

- 바인드 주소 - 유효한 IP4 주소 또는 모든 인터페이스에 대한 '*'입니다.
  - 0.0.0.0 또는 `*` - 모든 주소가 연결할 수 있음
  - 127.0.0.1 또는 localhost - 로컬호스트 응용 프로그램만 연결할 수 있음
  - 다른 IP(예: 1.2.3.4) - 해당 IP(1.2.3.4)만 연결할 수 있음
- 포트 번호 - Readarr의 웹UI에 액세스하기 위해 사용할 포트 번호

> 참고: Docker를 사용하는 경우이 설정을 건드리지 마십시오.
{.is-warning}

- URL 기본값 - 리버스 프록시 지원을 위한 것으로 기본값은 비어 있습니다.

> 참고: 리버스 프록시를 사용하는 경우(예: mydomain.com/readarr), URL 기본값에 '/readarr'을 입력해야 합니다.
{.is-info}

- SSL 활성화 - SSL 자격 증명을 가지고 Readarr와의 통신을 보안하려면 이 옵션을 활성화합니다.

> 참고: 이해하지 못하는 경우에는 사용하지 마십시오.
{.is-warning}

## 보안

![gensecurity.png](/assets/readarr/gensecurity.png)

- 인증 - Readarr에 액세스하기 위해 인증하는 방법을 선택합니다.
  - 없음 - Readarr에 액세스하기 위한 인증이 없습니다. 일반적으로 네트워크의 유일한 사용자이거나 Readarr에 액세스할 이유가 없는 네트워크에 있는 경우에 선택합니다.
  - 기본(브라우저 팝업) - Readarr에 액세스할 때 작은 팝업이 나타나고 사용자 이름과 비밀번호를 입력할 수 있도록 합니다.
  - 양식(로그인 페이지) - Readarr에 로그인할 수 있도록 일반적인 로그인 화면이 있는 옵션입니다.
- API 키 - 다른 프로그램이 통신하거나 Readarr가 다른 프로그램과 통신하도록 하는 방법입니다. 이 키는 액세스 권한이 없는 잘못된 사람에게 제공되면 라이브러리에 여러 가지 문제를 일으킬 수 있습니다. 이것이 로그에서 API 키가 삭제되는 이유입니다.
- 인증서 유효성 검사 - HTTPS 인증서 유효성 검사의 엄격성을 변경합니다.
  - 활성화 - 모든 HTTPS 인증서를 유효성 검사합니다(권장됨).
  - 로컬 주소에 대해 비활성화 - 로컬호스트 및 LAN을 제외한 모든 HTTPS 인증서를 유효성 검사하지 않습니다.
  - 비활성화 - 어떤 HTTPS 인증서도 유효성 검사하지 않습니다.

## 프록시

![genproxy.png](/assets/readarr/genproxy.png)

- 프록시 - Readarr가 가져오고 검색하는 정보를 프록시를 통해 실행하도록 설정할 수 있습니다. 토렌트 파일을 다운로드할 수 없는 국가에 있는 경우 유용할 수 있습니다.

- 프록시 사용 - 프록시를 사용하려면 활성화합니다.
- 프록시 유형 - 프록시 유형을 선택합니다(HTTPS, Socks4 또는 Socks5).
- 호스트 이름 - 프록시 호스트 이름을 입력합니다(http/https 또는 기타 프로토콜을 포함하지 마십시오).
- 포트 - 프록시 포트를 입력합니다.
- 사용자 이름 - 해당되는 경우 프록시 사용자 이름을 입력합니다.
- 비밀번호 - 해당되는 경우 프록시 비밀번호를 입력합니다.
- 무시할 주소 - 프록시를 우회할 주소를 쉼표로 구분하여 입력합니다.
- 로컬 주소에 대해 프록시 우회 - 로컬 주소에 대해 프록시를 우회하도록 확인란을 선택합니다.

## 로깅

![genlogging.png](/assets/readarr/genlogging.png)

- 로그 레벨 - 가장 유용한 문제 해결 도구 중 하나입니다.
  - 정보 - Readarr가 정보를 수집하는 가장 기본적인 방법으로, 로그에는 매우 적은 양의 정보가 포함됩니다. 이 로그 파일에는 치명적인 오류, 오류, 경고 및 정보 항목이 포함됩니다.
  - 디버그 - 디버그는 정보에 포함된 모든 정보와 유용한 추가 정보를 포함합니다. 이 로그 파일에는 치명적인 오류, 오류, 경고, 정보 및 디버그 항목이 포함됩니다.
  - 추적 - Readarr의 가장 고급 및 자세한 로깅으로, 추적은 정보와 디버그에서 수집한 모든 정보와 더 많은 정보를 포함합니다. Discord나 Reddit에서 문제 해결을 위해 요청될 때 가장 일반적으로 요청되는 로그 유형입니다. 도움이 필요한 경우 로그를 추적으로 선택하고 문제가 발생하는 작업을 다시 수행하여 로그를 캡처하십시오. 이 로그 파일에는 치명적인 오류, 오류, 경고, 정보, 디버그 및 추적 항목이 포함됩니다.

## 분석

![genanalytics.png](/assets/readarr/genanalytics.png)

- 분석 - 익명의 사용 및 오류 정보를 Readarr 서버(Servarr)로 보냅니다. 이에는 브라우저 정보, 사용하는 Readarr WebUI 페이지, 오류 보고 및 OS 및 런타임 버전 정보가 포함됩니다. 이 정보를 사용하여 기능 및 버그 수정을 우선 순위로 정할 것입니다.

## 업데이트

![genupdates.png](/assets/readarr/genupdates.png)

- (고급 옵션) 브랜치 - 실행 중인 Readarr 브랜치입니다.
  - [자세한 내용은 이 FAQ 항목을 참조하십시오](/readarr/faq#how-do-i-update-readarr)
- 자동 - 업데이트를 자동으로 다운로드하고 설치합니다. 여전히 시스템: 업데이트에서 설치할 수 있습니다. 참고: Windows 사용자는 항상 자동으로 업데이트됩니다.
- 메커니즘 - Readarr 내장 업데이터 또는 스크립트를 사용합니다.
  - 내장 - Readarr의 내장 업데이터를 사용합니다.
  - 스크립트 - Readarr에 업데이트 스크립트를 실행하도록 합니다.
  - Docker - Docker 내부에서 Readarr를 업데이트하지 않고 새로운 업데이트가 포함된 새 이미지를 가져옵니다.
- 스크립트 - 메커니즘이 스크립트로 설정된 경우에만 표시됩니다. 업데이트 스크립트의 경로를 입력합니다.
- 업데이트 프로세스 - Readarr는 업데이트 파일을 다운로드하고 무결성을 확인한 다음 임시 위치에 압축을 풀고 선택한 방법을 호출합니다. 업데이트 프로세스는 Readarr가 실행되는 동일한 사용자로 실행되며, Readarr 파일을 업데이트하고 중지/시작할 수 있는 권한이 필요합니다.
- 내장 - 내장 메서드는 Readarr 파일과 설정을 백업하고 Readarr를 중지한 다음 설치를 업데이트하고 Readarr를 시작합니다. 시스템이 Readarr의 중지를 처리하지 못하고 자동으로 다시 시작하려고 시도하는 경우 스크립트 대신 사용하는 것이 좋습니다. 실패한 경우 이전 버전의 Readarr가 다시 시작됩니다.
- 스크립트 - 스크립트는 내장 업데이터와 동일한 작업을 처리해야 합니다. 서비스 중지 및 시작(Upstart/Launchd 등)을 처리해야 하는 경우 여기에서 수행해야 합니다.

## 백업

![genbackups.png](/assets/readarr/genbackups.png)

- 백업 섹션을 사용하여 Readarr가 백업을 처리하는 방법을 지정할 수 있습니다.

- 폴더 - 백업 위치를 선택할 수 있습니다. Docker에서는 컨테이너가 볼 수 있는 것으로 제한됩니다. 경로는 appdata 폴더를 기준으로 상대 경로입니다. 필요한 경우 appdata 폴더 외부로 백업할 수 있는 절대 경로를 설정할 수 있습니다.
- 간격 - 얼마나 자주 Readarr가 백업을 만들어야 하는지 설정합니다.
- 보존 기간 - 각 백업을 유지할 기간을 설정합니다. 새로운 백업이 생성되면 가장 오래된 백업이 제거됩니다.

기본적으로 백업은 매주 7일마다 수행되며, 최근 4개의 백업이 유지됩니다.

# UI (사용자 인터페이스)

이 페이지에서는 사용자 인터페이스 디스플레이 옵션을 사용자 정의할 수 있습니다.

## 캘린더

![uicalendar.png](/assets/readarr/uicalendar.png)

- 주의 첫 번째 날 - 주의 첫 번째 날을 선택할 수 있습니다.
- 주 열 머리글 - 열의 머리글을 선택할 수 있습니다.

## 날짜

![caldates.png](/assets/readarr/caldates.png)

- 짧은 날짜 형식 - Readarr에서 짧은 날짜를 어떻게 표시하길 원하십니까?
- 긴 날짜 형식 - Readarr에서 긴 형식의 날짜를 어떻게 표시하길 원하십니까?
- 시간 형식 - 12시간 형식 또는 24시간 형식을 원하십니까?
- 상대적인 날짜 표시 - Readarr에서 상대적인 날짜(오늘/어제/등) 또는 절대적인 날짜를 표시하길 원하십니까?

## 스타일

![calstyle.png](/assets/readarr/calstyle.png)

- 색각이상자 모드 사용 - 색각이상자 사용자가 색상으로 구분된 정보를 더 잘 구별할 수 있도록 스타일을 변경합니다.

## 언어

![callanguage.png](/assets/readarr/callanguage.png)

- UI 언어 - 응용 프로그램 UI에서 사용할 언어를 선택합니다.