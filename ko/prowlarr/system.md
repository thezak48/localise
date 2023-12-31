# 상태

## 건강 상태

이 페이지에는 건강 상태 확인 오류 목록이 포함되어 있습니다. 이 건강 상태 확인은 Prowlarr에서 주기적으로 수행되며 특정 이벤트에서 수행됩니다. 결과적으로 발생한 경고 및 오류는 여기에 나열되어 이를 해결하는 방법에 대한 안내를 제공합니다.

### 시스템 경고

#### 브랜치가 유효한 릴리스 브랜치가 아닙니다

- 설정한 브랜치가 유효한 릴리스 브랜치가 아닙니다. 업데이트를 받을 수 없습니다. [현재 릴리스 브랜치](/prowlarr/faq#how-do-i-update-prowlarr) 중 하나로 변경하십시오.

#### 현재 설치된 SQLite 버전이 지원되지 않습니다

- Prowlarr은 데이터를 SQLite 데이터베이스에 저장합니다. 시스템에 설치된 SQLite3 라이브러리가 너무 오래되었습니다. Prowlarr은 적어도 버전 3.9.0 이상을 필요로 합니다. Prowlarr은 SQLite3 업그레이드 패키지에 포함되어 있을 수도 있고 포함되어 있지 않을 수도 있는 `libSQLite3.so`를 사용합니다.

#### 새로운 업데이트가 사용 가능합니다

- 축하합니다. 개발자들이 새로운 업데이트를 릴리스했습니다. 이는 일반적으로 멋진 새로운 기능과 버그 수정을 의미합니다 (맞죠?). 자동 업데이트가 활성화되어 있지 않으므로 플랫폼에서 업데이트하는 방법을 찾아야 합니다. 시스템 => 업데이트 페이지에서 설치 버튼을 누르는 것이 좋은 시작점이 될 것입니다.

> 현재 버전이 14일 이내인 경우에는 이 경고가 표시되지 않습니다.
{.is-info}

#### 사용자가 시작 폴더를 쓸 수 없기 때문에 업데이트를 설치할 수 없습니다

- 이는 Prowlarr이 자체 업데이트를 수행할 수 없음을 의미합니다. Prowlarr을 수동으로 업데이트하거나 Prowlarr의 시작 디렉토리(설치 디렉토리)의 권한을 설정하여 Prowlarr이 자체 업데이트를 수행할 수 있도록 해야 합니다.

#### 업데이트를 삭제하지 않기 위해 업데이트가 불가능합니다

- Prowlarr은 운영 체제의 AppData 폴더가 일반적으로 C:\ProgramData(Windows) 또는 ~/.config(linux)에 위치한 디렉토리 내에 있는 것으로 감지했습니다.

- 현재 AppData 및 시작 디렉토리를 확인하려면 System => Info를 참조하십시오.
- 이는 데이터 손실 위험 없이 Prowlarr이 자체 업데이트를 수행할 수 없음을 의미합니다.
- Linux에서는 Prowlarr을 실행하는 사용자의 홈 디렉토리를 변경하고 현재 ~/.config/Prowlarr 디렉토리의 내용을 복사해야 합니다. 이렇게 하면 데이터베이스가 보존됩니다.

#### 브랜치는 이전 버전을 위한 것입니다

- 설정/일반에서 설정한 업데이트 브랜치는 이전 버전의 Prowlarr을 위한 것이므로 시스템/업데이트 피드에서 올바른 업데이트 정보를 볼 수 없고 새로운 업데이트를 받을 수 없을 수 있습니다.

#### signalR에 연결할 수 없습니다

- signalR은 동적 UI 업데이트를 처리합니다. 따라서 브라우저가 서버의 signalR에 연결할 수 없으면 UI에서 실시간 업데이트를 볼 수 없습니다.

- 가장 일반적인 경우는 역방향 프록시나 클라우드플레어의 사용입니다.
  - 클라우드플레어는 웹소켓을 활성화해야 합니다.
  - Nginx는 다음과 같은 추가 설정이 필요합니다:

```nginx
 proxy_http_version 1.1;
 proxy_set_header Upgrade $http_upgrade;
 proxy_set_header Connection $http_connection;
```

> nginx 문서에서 제안하는대로 proxy_set_header Connection "Upgrade";를 포함하지 않도록 주의하십시오. 이는 작동하지 않습니다.
> <https://github.com/aspnet/AspNetCore/issues/17081> 참조
{.is-warning}

- Apache2 역방향 프록시의 경우 다음 모듈을 활성화해야 합니다: proxy, proxy_http 및 proxy_wstunnel. 그런 다음 다음 웹소켓 터널 지시문을 vhost 구성에 추가하십시오:

```none
RewriteEngine On
RewriteCond %{HTTP:Upgrade} =websocket [NC]
RewriteRule /(.*) ws://127.0.0.1:9696/$1 [P,L]
```

역방향 프록시가 하위 디렉토리에 있는 경우 RewriteRule에 기본 경로를 포함해야 합니다. 예를 들어:

```none
RewriteRule /prowlarr/(.*) ws://127.0.0.1:9696/prowlarr/$1 [P,L]
```

Prowlarr이 역방향 프록시와 동일한 컴퓨터에서 실행되지 않는 경우 127.0.0.1을 Prowlarr 앱의 적절한 IP 주소/DNS 이름으로 바꾸십시오.

- Caddy (V1)의 경우 다음을 사용하십시오:

> 참고: prowlarr 구성에 웹소켓 지시문을 추가해야 합니다{.is-info}

```none
 proxy /prowlarr 127.0.0.1:9696 {
     websocket
     transparent
 }
```

#### 구성된 프록시 호스트의 IP 주소를 확인할 수 없습니다

- 프록시 설정을 검토하고 정확한지 확인하십시오.
- 프록시가 실행 중이고 작동 가능한지 확인하십시오.

#### 프록시 테스트 실패

- 구성된 프록시가 테스트에 실패했습니다. 제공된 HTTP 오류를 검토하거나 자세한 내용은 로그를 확인하십시오.

#### 시스템 시간이 1일 이상 차이가 납니다

- 시스템 시간이 1일 이상 차이가 납니다. 시간이 수정될 때까지 예약된 작업이 올바르게 실행되지 않을 수 있습니다.
- 시스템 시간을 검토하고 권위 있는 시간 서버와 동기화되어 있는지 확인하십시오.

### 다운로드 클라이언트

#### 사용 가능한 다운로드 클라이언트가 없습니다

- Prowlarr이 미디어를 다운로드할 수 있도록 올바르게 구성된 활성화된 다운로드 클라이언트가 필요합니다. Prowlarr은 다양한 다운로드 클라이언트를 지원하므로 요구 사항과 가장 일치하는 클라이언트를 결정해야 합니다. 이미 다운로드 클라이언트를 설치했다면 Prowlarr에서 사용하도록 구성하고 카테고리를 생성해야 합니다. 설정 => 다운로드 클라이언트를 참조하십시오.

#### 다운로드 클라이언트와 통신할 수 없습니다

- Prowlarr이 구성된 다운로드 클라이언트와 통신할 수 없었습니다. 다운로드 클라이언트가 작동 중인지 확인하고 URL을 다시 확인하십시오. 이는 인증 오류일 수도 있습니다.
- 일반적으로 올바르게 구성되지 않은 다운로드 클라이언트로 인해 발생합니다. 일반적으로 확인할 수 있는 사항은 다음과 같습니다.
- 다운로드 클라이언트의 IP 주소(동일한 물리적인 기계에 있는 경우 일반적으로 127.0.0.1)
- 다운로드 클라이언트가 사용하는 포트 번호(기본 포트 번호로 입력되어 있지만 변경한 경우 Prowlarr에도 동일한 포트 번호를 입력해야 함)
- 로컬 네트워크에서 Prowlarr 인스턴스와 다운로드 클라이언트를 모두 사용하는 경우 SSL 암호화가 켜져 있지 않은지 확인하십시오. 자세한 내용은 SSL FAQ 항목을 참조하십시오.
- rutorrent를 사용하는 경우 https를 사용하도록 특별한 설정 변경이 필요합니다.

#### 다운로드 클라이언트를 사용할 수 없습니다

- 하나 이상의 다운로드 클라이언트가 Prowlarr의 요청에 응답하지 않습니다. 따라서 Prowlarr은 일반적으로 1분 주기로 사용되는 활성 다운로드를 추적하고 완료된 다운로드를 가져오는 데 사용되는 다운로드 클라이언트에 대한 쿼리를 일시적으로 중지합니다. 그러나 Prowlarr은 여전히 다운로드를 클라이언트로 보내려고 시도하지만 대부분 실패할 것입니다.
- 실패의 원인을 확인하기 위해 System=>Logs를 검사해야 합니다.
- 이 다운로드 클라이언트를 더 이상 사용하지 않는 경우 Prowlarr에서 비활성화하여 오류를 방지할 수 있습니다.

#### 잘못된 다운로드 클라이언트 설정

- 다운로드 클라이언트가 파일을 다운로드하는 위치가 문제를 일으키고 있습니다. 자세한 정보는 로그를 확인하십시오. 이는 권한 문제이거나 Windows에서 Linux로 또는 Linux에서 Windows로 이동하려고 할 때 원격 경로 매핑이 없는 경우가 있습니다.

### 인덱서

#### 인덱서에 정의가 없습니다

- 인덱서(들)에는 기존 정의(파일)가 없습니다. 이는 인덱서가 더 이상 지원되지 않고 제거되었거나 Cardigann YML 정의에 더 이상 액세스할 수 없는 경우가 일반적입니다.

#### 인덱서가 오래되었습니다

- 인덱서(들)의 정의가 오래되었고 최신 상태가 아닙니다. 이에는 다음 두 가지 원인이 있습니다.

##### 코드 변경으로 인한 오래됨

- 코드 변경으로 인해 현재 구성된 인덱서(들)는 오래되었습니다. 인덱서를 제거하고 다시 추가하여 문제를 해결하십시오.
- 이는 일반적으로 API를 변환하거나 YML을 C#으로 또는 그 반대로 변환하는 경우에 발생합니다.

##### 사이트 제거로 인한 오래됨

- 특정 사이트는 Prowlarr이나 Jackett에서 제거되도록 요청될 수 있습니다. 이러한 사이트는 오래되었다고 표시될 수 있습니다.
  - [TVVault](https://github.com/Prowlarr/Prowlarr/issues/573) in [Prowlarr #700](https://github.com/Prowlarr/Prowlarr/pull/700)
  - Audiobookbay가 Prowlarr이 API에 액세스하지 않도록 요청했습니다.
  - Ebookbay가 Prowlarr이 API에 액세스하지 않도록 요청했습니다.
  - Rarbg가 [2023-05-31에 종료](https://torrentfreak.com/iconic-torrent-site-rarbg-shuts-down-all-content-releases-stop-230531/)되었습니다.

#### 활성화된 인덱서가 없습니다

- Prowlarr은 새로운 릴리스를 발견하기 위해 인덱서가 필요합니다. 인덱서를 추가하는 방법에 대한 지침은 위키를 참조하십시오.

#### 인덱서가 실패로 인해 사용할 수 없습니다

- Prowlarr이 인덱서 중 하나에 대한 요청에 응답하지 못했습니다. Prowlarr은 인덱서에서 응답을 받지 못했을 때(이는 DNS, 프록시/VPN 연결, 인증 또는 인덱서 문제로 인한 것일 수 있음) 또는 인덱서에서 nzb/torrent 파일을 가져오지 못했을 때 이 메커니즘이 트리거됩니다. 문제의 종류를 확인하기 위해 로그를 검사하십시오.
- 해당 인덱서를 비활성화하여 경고를 방지할 수 있습니다.
- 인덱서를 다시 확인하려면 인덱서에서 테스트를 실행하십시오. 건강 상태 확인 경고가 즉시 사라지지 않을 수 있습니다.

#### 인덱서 VIP 만료 예정

- VIP 구독 또는 인덱서의 혜택이 Prowlarr에서 구성한 만료 날짜를 기준으로 다음 7일 이내에 만료됩니다.

#### 인덱서 VIP 만료됨

- VIP 구독 또는 인덱서의 혜택이 Prowlarr에서 구성한 만료 날짜를 기준으로 만료되었습니다.

### 애플리케이션

#### 애플리케이션을 사용할 수 없습니다

- Prowlarr이 애플리케이션 중 하나를 사용하려고 시도하는 동안 오류가 발생했습니다. 재시도를 제한하기 위해 Prowlarr은 일시적으로 애플리케이션을 사용하지 않을 것입니다(최대 24시간까지). 이는 Prowlarr이 애플리케이션에서 응답을 받지 못했을 때(일반적으로 DNS, 연결, 인증 또는 애플리케이션 문제) 트리거됩니다. 문제의 종류를 확인하기 위해 로그를 검사하십시오.
- 이 경고를 방지하려면 해당 애플리케이션을 비활성화하십시오.
- 애플리케이션에서 테스트를 실행하여 Prowlarr이 애플리케이션을 다시 확인하도록 하십시오. 건강 상태 확인 경고가 즉시 사라지지 않을 수 있습니다.

## 디스크 공간

이 섹션에서는 사용 가능한 디스크 공간을 표시합니다.
도커에서는 일반적으로 도커 이미지 내에서 사용 가능한 공간을 표시합니다.

## 정보

현재 Prowlarr 설치에 대한 정보를 제공합니다.

## 자세한 정보

홈 페이지: Prowlarr의 홈 페이지
위키: 이미 여기에 있습니다
Reddit: r/prowlarr
Discord: Discord에 참여하세요
기부: 기부하고 싶으시다면 여기를 클릭하세요
Sonarr에 기부: 시작한 프로젝트에 기부하고 싶으시다면 여기를 클릭하세요
소스: GitHub
기능 요청: 멋진 아이디어가 있다면 여기에 제출하세요

# 작업

## 예약된 작업

이 페이지에는 Prowlarr이 실행하는 모든 예약된 작업이 나열됩니다.

- 애플리케이션 업데이트 확인 - 이 작업은 UI에 표시된 일정에 따라 실행되며 Prowlarr이 가장 최신 버전인지 확인한 다음 업데이트 스크립트를 트리거하여 Prowlarr을 업데이트합니다. 설정 => 업데이트를 참조하십시오.

> 참고: Docker에서는 이 작업이 컨테이너를 업데이트하지 않습니다. 새 이미지를 다운로드해야 합니다.
{.is-warning}

- 백업 - 이 작업은 Prowlarr의 데이터베이스를 일정에 따라 백업합니다. 자세한 내용은 여기에서 확인할 수 있습니다. 백업에 대한 자세한 정보는 System => 백업을 참조하십시오.
- 건강 상태 확인 - 건강 상태 확인은 UI에 표시된 일정에 따라 실행되며 Prowlarr의 전반적인 건강 상태를 확인합니다. 가능한 건강 관련 문제 목록은 Health Checks 위키 항목을 참조하십시오.
- 정리 - UI에 표시된 일정에 따라 이 작업은 모든 먼지를 제거하고 바닥을 쓸고 진공청소기를 사용하여 바닥을 닦으며 깔끔하게 접힌 메모를 작성합니다. 하지만 쓰레기는 치우지 않습니다. 그건 충분히 지불받지 못했기 때문입니다.
- 메시지 정리 - UI에 표시된 일정에 따라 이 작업은 Prowlarr 왼쪽 하단에 나타나는 메시지를 정리합니다.
  
> 이러한 모든 작업은 각 작업의 가장 오른쪽에 있는 아이콘을 클릭하여 예약된 시간 외에 수동으로 실행할 수 있습니다.
{.is-info}

## 대기열

대기열에서는 예정된 작업과 최근 실행된 작업의 기록 및 소요 시간을 표시합니다.

# 백업

> 이 섹션은 버튼과 페이지의 전반적인 목적에 대해 더 자세히 설명합니다.
> 그러나 Prowlarr 인스턴스를 백업/복원하는 방법을 찾고 있다면 [FAQ](/prowlarr/faq)를 참조하세요.
{.is-info}

백업 섹션에서는 이전 백업이 표시됩니다(백업을 하지 않은 새로 설치한 경우 제외).
  
여기에서 화면 상단에 두 가지 옵션이 제공됩니다.

- 지금 백업 - 이 옵션을 선택하면 Prowlarr 데이터베이스의 수동 백업이 트리거됩니다.
- 백업 복원 - 이 옵션을 선택하면 이전 백업에서 복원하기 위한 새로운 화면이 열립니다.
파일 선택을 선택하면 브라우저에서 Prowlarr Zip 백업을 복원하기 위한 대화 상자가 열립니다.
  
마지막으로, 이전 백업이 있고 Prowlarr에서 다운로드하여 표준 위치 이외의 위치에 저장하려는 경우 이 파일 중 하나를 선택하여 다운로드할 수 있습니다.
각 이전 다운로드의 오른쪽에는 두 가지 옵션이 있습니다.

- 하나 - 이전 백업에서 복원하기 위해 - 이 옵션을 선택하면 이 백업에서 복원하려는지 확인하기 위해 새 창이 열립니다.
- 둘 - 이전 백업 삭제하기

# 업데이트

업데이트 화면에는 최근 5개의 업데이트와 현재 버전이 표시됩니다.
이 페이지에서는 개발자의 업데이트 노트도 표시되어 Prowlarr에 추가되거나 수정된 내용을 알려줍니다 (환호!)
  
> 유지 보수 릴리스에는 버그 수정 및 기타 다양한 개선 사항이 포함됩니다. 자세한 내용은 커밋 기록을 확인하세요.
{.is-info}

# 이벤트

이벤트 탭에서는 Prowlarr 내에서 발생한 사항을 확인할 수 있습니다. 이는 일부 경미한 문제를 진단하는 데 사용될 수 있습니다. 그러나 이는 로깅에서 설명하는 추적 로그를 대체하지 않습니다. 이벤트는 INFO 로그와 동등합니다.

- 구성 요소 - 이 열은 Prowlarr 내에서 트리거된 구성 요소를 나타냅니다.
- 메시지 - 이 열은 이전 열에서 전송된 메시지를 나타냅니다.
- 기어 아이콘 - 이 옵션을 사용하면 페이지당 표시되는 구성 요소/메시지 수를 변경할 수 있습니다(기본값은 50입니다).
- 페이지 상단의 옵션
  - 새로 고침 - 이 옵션을 선택하면 현재 페이지를 새로 고쳐 새 이벤트 로그를 가져옵니다.
  - 지우기 - 이 옵션을 선택하면 현재 이벤트 로그를 지우고 처음부터 시작할 수 있습니다.

# 로그 파일

이 페이지에서는 Prowlarr에 대해 현재 사용 가능한 로그 파일을 다운로드하고 확인할 수 있습니다.

맨 위 행에는 로그 파일을 제어할 수 있는 여러 옵션이 있습니다.

- 가장 왼쪽 상단에 있는 드롭다운에서 로그 파일과 업데이터 로그 파일로 전환할 수 있습니다.
  - 로그 파일 - 지원 문제의 핵심입니다. 로그 파일에 대한 자세한 내용은 여기에서 찾을 수 있습니다.
  - 업데이터 로그 파일 - Prowlarr의 업데이터 스크립트와 관련된 로그 파일이 표시됩니다.

> 도커를 사용하는 경우 이 항목은 비어 있을 것입니다. 새 도커 이미지를 다운로드하여 업데이트해야 합니다.
{.is-info}

- 새로 고침 - 이 옵션을 선택하면 현재 페이지를 새로 고쳐 새로 생성된 로그를 표시합니다.
- 삭제 - 이 옵션을 선택하면 모든 로그를 지우고 처음부터 시작할 수 있습니다.
- 파일 이름 - 이는 로그와 연결된 파일 이름을 표시합니다.
- 마지막 작성 시간 - 이는 특정 로그 파일이 작성된 로컬 시간입니다.
  - Prowlarr은 각각 1MB로 제한된 롤링 로그 파일을 사용합니다. 현재 로그 파일은 항상 prowlarr.txt이며, 다른 파일의 경우 prowlarr.0.txt가 다음으로 최신 파일입니다(숫자가 높을수록 오래된 파일입니다). 즉, 이 로그 파일에는 `fatal`, `error`, `warn`, `info` 항목이 포함됩니다.
  - 디버그 로그 레벨이 활성화된 경우 추가적인 prowlarr.debug.txt 롤링 로그 파일이 있을 수 있으며, 최대 51개의 파일이 있습니다. 이 로그 파일에는 `fatal`, `error`, `warn`, `info`, `debug` 항목이 포함됩니다. 일반적으로 약 40시간 정도를 커버합니다.
  - 추적 로그 레벨이 활성화된 경우 추가적인 prowlarr.trace.txt 롤링 로그 파일이 있을 수 있으며, 최대 51개의 파일이 있습니다. 이 로그 파일에는 `fatal`, `error`, `warn`, `info`, `debug`, `trace` 항목이 포함됩니다. 추적 로그는 대부분 몇 시간 정도를 커버합니다.