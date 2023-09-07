# 테이블 목차

- [테이블 목차](#테이블-목차)
- [상태](#상태)
  - [건강 상태](#건강-상태)
    - [시스템 경고](#시스템-경고)
      - [브랜치가 유효한 릴리스 브랜치가 아닙니다](#브랜치가-유효한-릴리스-브랜치가-아닙니다)
      - [.NET 버전으로 업데이트](#net-버전으로-업데이트)
        - [도커 설치 수정](#도커-설치-수정)
        - [FreeBSD 설치 수정](#freebsd-설치-수정)
        - [독립 설치 수정](#독립-설치-수정)
      - [현재 설치된 mono 버전이 오래되어 더 이상 지원되지 않습니다](#현재-설치된-mono-버전이-오래되어-더-이상-지원되지-않습니다)
      - [현재 설치된 SQLite 버전은 지원되지 않습니다](#현재-설치된-sqlite-버전은-지원되지-않습니다)
      - [데이터베이스 무결성 검사 실패](#데이터베이스-무결성-검사-실패)
      - [새로운 업데이트가 사용 가능합니다](#새로운-업데이트가-사용-가능합니다)
      - [사용자가 시작 폴더에 대한 쓰기 권한이 없어 업데이트를 설치할 수 없습니다](#사용자가-시작-폴더에-대한-쓰기-권한이-없어-업데이트를-설치할-수-없습니다)
      - [업데이트를 방지하기 위해 업데이트 중에 AppData를 삭제하지 않습니다](#업데이트를-방지하기-위해-업데이트-중에-appdata를-삭제하지-않습니다)
      - [브랜치는 이전 버전을 위한 것입니다](#브랜치는-이전-버전을-위한-것입니다)
      - [signalR에 연결할 수 없습니다](#signalr에-연결할-수-없습니다)
        - [Nginx](#nginx)
        - [Apache2](#apache2)
        - [Caddy](#caddy)
      - [구성된 프록시 호스트의 IP 주소를 확인할 수 없습니다](#구성된-프록시-호스트의-ip-주소를-확인할-수-없습니다)
      - [프록시 테스트 실패](#프록시-테스트-실패)
      - [시스템 시간이 1일 이상 차이가 납니다](#시스템-시간이-1일-이상-차이가-납니다)
      - [PTP 인덱서 설정이 오래되었습니다](#ptp-인덱서-설정이-오래되었습니다)
      - [Mono 및 x86 빌드가 종료됩니다](#mono-및-x86-빌드가-종료됩니다)
    - [다운로드 클라이언트](#다운로드-클라이언트)
      - [사용 가능한 다운로드 클라이언트가 없습니다](#사용-가능한-다운로드-클라이언트가-없습니다)
      - [다운로드 클라이언트와 통신할 수 없습니다](#다운로드-클라이언트와-통신할-수-없습니다)
      - [다운로드 클라이언트를 사용할 수 없습니다](#다운로드-클라이언트를-사용할-수-없습니다)
      - [완료된 다운로드 처리 활성화](#완료된-다운로드-처리-활성화)
      - [Docker 잘못된 원격 경로 매핑](#docker-잘못된-원격-경로-매핑)
      - [루트 폴더로 다운로드](#루트-폴더로-다운로드)
      - [잘못된 다운로드 클라이언트 설정](#잘못된-다운로드-클라이언트-설정)
      - [잘못된 원격 경로 매핑](#잘못된-원격-경로-매핑)
      - [권한 오류](#권한-오류)
      - [원격 파일이 처리 중간에 제거되었습니다](#원격-파일이-처리-중간에-제거되었습니다)
      - [원격 경로가 사용되고 가져오기에 실패했습니다](#원격-경로가-사용되고-가져오기에-실패했습니다)
    - [완료/실패한 다운로드 처리](#완료실패한-다운로드-처리)
      - [완료된 다운로드 처리가 비활성화되었습니다](#완료된-다운로드-처리가-비활성화되었습니다)
    - [인덱서](#인덱서)
      - [자동 검색이 활성화된 인덱서가 없습니다. Radarr는 자동 검색 결과를 제공하지 않습니다](#자동-검색이-활성화된-인덱서가-없습니다-radarr는-자동-검색-결과를-제공하지-않습니다)
      - [RSS 동기화가 활성화된 인덱서가 없습니다. Radarr는 새로운 릴리스를 자동으로 가져오지 않습니다](#rss-동기화가-활성화된-인덱서가-없습니다-radarr는-새로운-릴리스를-자동으로-가져오지-않습니다)
      - [인덱서가 활성화되지 않았습니다](#인덱서가-활성화되지-않았습니다)
    - [활성화된 인덱서가 검색을 지원하지 않습니다](#활성화된-인덱서가-검색을-지원하지-않습니다)
      - [대화식 검색이 활성화된 인덱서가 없습니다](#대화식-검색이-활성화된-인덱서가-없습니다)
      - [인덱서가 실패로 인해 사용할 수 없습니다](#인덱서가-실패로-인해-사용할-수-없습니다)
      - [Jackett 모든 엔드포인트가 사용되었습니다](#jackett-모든-엔드포인트가-사용되었습니다)
        - [해결 방법](#해결-방법)
    - [영화 폴더](#영화-폴더)
      - [루트 폴더가 없습니다](#루트-폴더가-없습니다)
    - [영화](#영화)
      - [영화가 TMDb에서 제거되었습니다](#영화가-tmdb에서-제거되었습니다)
      - [목록이 실패로 인해 사용할 수 없습니다](#목록이-실패로-인해-사용할-수-없습니다)
    - [알림](#알림)
    - [슬랙 알림으로 Discord 사용](#슬랙-알림으로-discord-사용)
  - [디스크 공간](#디스크-공간)
  - [정보](#정보)
  - [추가 정보](#추가-정보)
- [작업](#작업)
  - [스케줄된 작업](#스케줄된-작업)
  - [대기열](#대기열)
- [백업](#백업)
- [업데이트](#업데이트)
- [이벤트](#이벤트)
- [로그 파일](#로그-파일)

# 상태

## 건강 상태

- 이 페이지에는 Radarr에서 주기적으로 수행되는 건강 상태 확인 오류 목록이 포함되어 있습니다. 이 건강 상태 확인은 Radarr에서 주기적으로 수행되며 특정 이벤트에서 수행됩니다. 결과적으로 발생한 경고 및 오류는 여기에 나열되어 해결 방법을 제공하기 위해 나열됩니다.

### 시스템 경고

#### 브랜치가 유효한 릴리스 브랜치가 아닙니다

- 설정한 브랜치가 유효한 릴리스 브랜치가 아닙니다. 업데이트를 받을 수 없습니다. [현재 릴리스 브랜치](/radarr/faq#how-do-i-update-radarr) 중 하나로 변경하십시오.

#### .NET 버전으로 업데이트

{#update-to-net-core-version}

- 최신 버전의 Radarr은 .NET6 이상을 대상으로 합니다. Mono 빌드는 v4부터 제공되지 않으며 더 이상 지원되지 않습니다. v3.2.2는 레거시 Mono 빌드를 지원하는 Radarr의 마지막 버전입니다. 이전 Mono 빌드 중 하나를 실행 중이지만 플랫폼이 .NET을 지원합니다.

아래 항목을 참조하여 지원되지 않는, 생명 주기가 종료된 Mono 버전에서 지원되는 .NET으로 전환하는 방법을 확인하십시오.

- [도커 설치 수정](#fixing-docker-installs)
- [FreeBSD 설치 수정](#fixing-freebsd-installs)
- [독립 설치 수정](#fixing-standalone-installs)
{.links-list}

##### 도커 설치 수정

- 도커 유지 관리자에게 맞는 브랜치가 올바른지 확인하고 컨테이너를 다시 가져오십시오.

##### FreeBSD 설치 수정

- 간단히 Radarr 포트를 `pkg update && pkg upgrade`로 업데이트하십시오.
- (선택 사항) mono 패키지를 제거하려면 삭제하십시오.

##### 독립 설치 수정

다음과 같은 오류가 발생하는 경우:

```none
Cannot open assembly '/opt/Radarr/Radarr': File does not contain a valid CIL image
```

- 다음 단계 전에 기존 구성을 백업하십시오.
- 이는 Linux 호스트에서만 발생해야 합니다. Microsoft의 .NET 런타임 또는 SDK를 설치하지 마십시오.
- 이를 해결하려면 아키텍처에 맞는 올바른 빌드를 다운로드하고 기존 이진 파일(응용 프로그램)을 삭제한 다음 방금 다운로드한 .tar.gz의 내용물로 기존 바이너리(내용물 또는 /opt/Radarr 폴더)를 대체해야 합니다. 그런 다음 서비스 파일을 업데이트하여 mono를 사용하지 않도록 설정하십시오.

> 기존 바이너리 위에 다운로드를 바로 풀어 헤치지 마십시오.
> 먼저 이전 것을 삭제해야 합니다.
{.is-warning}

- 아래는 mono 설치를 제거하고 .NET 설치로 대체하는 커뮤니티에서 개발한 스크립트입니다. 기여 및 수정은 환영합니다.
- 이 스크립트는 `master` Radarr 브랜치에서 실행되는 것으로 가정합니다. 필요한 경우 변수를 업데이트하십시오.
- 이 스크립트는 Radarr가 사용자로 실행되는 사용자의 홈 디렉터리가라고 가정합니다. 필요한 경우 변수를 업데이트하십시오.
- 이 스크립트는 Radarr가 `/opt/Radarr`에 설치되었다고 가정합니다. 필요한 경우 변수를 업데이트하십시오.

```bash
#!/bin/bash
## 사용자 변수
installdir="/opt/Radarr"
APPUSER="radarr"
branch="master"
## /사용자 변수
app="radarr"
ARCH=$(dpkg --print-architecture)
# \*arr 중지
sudo systemctl stop $app
# 아키텍처 가져오기
dlbase="https://$app.servarr.com/v1/update/$branch/updatefile?os=linux&runtime=netcore"
case "$ARCH" in
"amd64") DLURL="${dlbase}&arch=x64" ;;
"armhf") DLURL="${dlbase}&arch=arm" ;;
"arm64") DLURL="${dlbase}&arch=arm64" ;;
*)
    echo_error "지원되지 않는 아키텍처입니다"
    exit 1
    ;;
esac
echo "다운로드 중..."
wget --content-disposition "$DLURL"
tar -xvzf ${app^}.*.tar.gz
echo "설치 파일 다운로드 및 추출 완료"
echo "기존 설치 이동 중"
sudo mv "$installdir/" "$installdir.old/"
echo "설치 중..."
sudo mv "${app^}" "$installdir"
sudo chown $APPUSER:$APPUSER -R $installdir
sudo sed -i "s|ExecStart=/usr/bin/mono --debug /opt/${app^}/${app^}.exe|ExecStart=/opt/${app^}/${app^}|g" /etc/systemd/system/$app.service
sudo sed -i "s|ExecStart=/usr/bin/mono /opt/${app^}/${app^}.exe|ExecStart=/opt/${app^}/${app^}|g" /etc/systemd/system/$app.service
sudo systemctl daemon-reload
echo "앱 설치 완료"
sudo rm -rf "$installdir.old/"
rm -rf "${app^}.*.tar.gz"
sudo systemctl start $app
```

#### 현재 설치된 mono 버전이 오래되어 더 이상 지원되지 않습니다

- Radarr는 .NET으로 작성되었으며 매우 오래된 ARM 프로세서에서 실행하려면 Mono가 필요합니다. Radarr의 최소 요구 사항은 Mono 5.20입니다.

> Radarr 버전 4.0부터 Mono는 더 이상 지원되지 않습니다
{.is-warning}

#### 현재 설치된 SQLite 버전은 지원되지 않습니다

- Radarr는 데이터를 SQLite 데이터베이스에 저장합니다. 시스템에 설치된 SQLite3 라이브러리가 너무 오래되었습니다. Radarr는 최소한 3.9.0 버전을 필요로 합니다.

> Radarr는 SQLite3 업그레이드 패키지에 포함되어 있는 `libSQLite3.so`를 사용합니다. 이 패키지에 포함되어 있지 않을 수도 있습니다.
{.is-info}

#### 데이터베이스 무결성 검사 실패

- 데이터베이스가 [SQLite Pragma Integrity Check](https://www.sqlite.org/pragma.html#pragma_integrity_check)에 실패하여 일부 손상이 있습니다.
- `Radarr.db`가 손상된 경우 [이 FAQ 항목](/radarr/faq#i-am-getting-an-error-database-disk-image-is-malformed)을 참조하십시오.
- `logs.db`가 손상된 경우: Radarr를 중지하고 `logs.db` 및 `logs.wal` 파일을 삭제하십시오.
- 둘 다 손상된 경우 위의 해당 프로세스를 검토하십시오.

#### 새로운 업데이트가 사용 가능합니다

- 개발자가 새로운 업데이트를 릴리스했습니다. 일반적으로 멋진 새로운 기능과 버그 수정이 포함되어 있습니다 (맞죠?). 자동 업데이트가 활성화되어 있지 않으므로 직접 업데이트하는 방법을 찾아야 합니다. 시스템 => 업데이트 페이지에서 설치 버튼을 누르는 것이 좋은 시작점입니다.

> 현재 버전이 14일 이내인 경우에는 이 경고가 표시되지 않습니다
{.is-info}

#### 사용자가 시작 폴더에 대한 쓰기 권한이 없어 업데이트를 설치할 수 없습니다

- 이는 Radarr가 자체 업데이트를 수행할 수 없다는 것을 의미합니다. Radarr를 수동으로 업데이트하거나 Radarr의 시작 디렉토리(설치 디렉토리)의 권한을 설정하여 Radarr가 자체 업데이트할 수 있도록 해야 합니다.

#### 업데이트를 방지하기 위해 업데이트 중에 AppData를 삭제하지 않습니다

- Radarr가 운영 체제의 AppData 폴더가 일반적으로 C:\ProgramData(Windows) 또는 ~/.config(Linux)에 있는 디렉토리 내에 있는 디렉토리에 위치한 것을 감지했습니다.

- 현재의 AppData 및 시작 디렉토리를 확인하려면 System => Info를 참조하십시오.
- 이는 데이터 손실 위험을 감수하지 않고는 자체 업데이트할 수 없다는 것을 의미합니다.
- Linux의 경우 Radarr를 실행하는 사용자의 홈 디렉토리를 변경하고 현재의 ~/.config/Radarr 디렉토리의 내용물을 보존하려면 홈 디렉토리를 변경하고 다운로드한 .tar.gz의 내용물로 기존 바이너리(응용 프로그램)를 대체해야 합니다.

#### 브랜치는 이전 버전을 위한 것입니다

- 설정/일반에서 설정한 업데이트 브랜치는 이전 버전의 Radarr을 위한 것이므로 시스템/업데이트 피드에서 올바른 업데이트 정보를 볼 수 없으며 새로운 업데이트를 받을 수 없을 수 있습니다.

#### signalR에 연결할 수 없습니다

- signalR은 동적 UI 업데이트를 제어합니다. 따라서 브라우저가 서버에 signalR에 연결할 수 없으면 UI에서 실시간 업데이트를 볼 수 없습니다.
- 가장 일반적인 경우는 리버스 프록시나 클라우드플레어를 사용하는 경우입니다.
- Cloudflare는 웹소켓을 활성화해야 합니다.

##### Nginx

- Nginx에는 다음과 같은 추가 구성이 필요합니다.

```nginx
 proxy_http_version 1.1;
 proxy_set_header Upgrade $http_upgrade;
 proxy_set_header Connection $http_connection;
```

> nginx 문서에서 제안하는 대로 proxy_set_header Connection "Upgrade";를 포함하지 마십시오. 이렇게 하면 작동하지 않습니다.
> <https://github.com/aspnet/AspNetCore/issues/17081>을 참조하십시오.
{.is-warning}

##### Apache2

Apache2 리버스 프록시를 사용하려면 다음 모듈을 활성화해야 합니다: proxy, proxy_http 및 proxy_wstunnel. 그런 다음 다음 웹소켓 터널 지시문을 vhost 구성에 추가하십시오.

```none
RewriteEngine On
RewriteCond %{HTTP:Upgrade} =websocket [NC]
RewriteRule /(.*) ws://127.0.0.1:7878/$1 [P,L]
```

리버스 프록시가 하위 디렉터리에 있는 경우 RewriteRule에 기본 경로를 포함해야 합니다. 예:

```none
RewriteRule /radarr/(.*) ws://127.0.0.1:7878/radarr/$1 [P,L]
```

Radarr가 리버스 프록시와 동일한 컴퓨터에서 실행되지 않는 경우 127.0.0.1을 Radarr 앱의 적절한 IP 주소/DNS 이름으로 바꾸십시오.

##### Caddy

Caddy (V1)의 경우 다음을 사용하십시오:
참고: radarr 구성에 웹소켓 지시문을 추가해야 합니다.

```none
 proxy /radarr 127.0.0.1:7878 {
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

- 시스템 시간이 1일 이상 차이가 납니다. 시스템 시간이 수정될 때까지 예약된 작업이 올바르게 실행되지 않을 수 있습니다.
- 시스템 시간을 검토하고 권위 있는 시간 서버에 동기화되어 있는지 확인하십시오.

#### PTP 인덱서 설정이 오래되었습니다

- 다음 PassThePopcorn 인덱서에는 오래된 설정이 있으며 업데이트해야 합니다.

#### Mono 및 x86 빌드가 종료됩니다

- Mono 및 x86 빌드는 v4부터 더 이상 지원되지 않습니다. 이 오류가 발생하면 애플리케이션의 mono 버전 또는 x86 버전을 실행 중입니다. 이러한 레거시 버전의 개발 지원이 점점 어려워지기 때문에 이러한 버전의 지원을 중단하고 앞으로 릴리스하지 않을 예정입니다. 따라서 x86이나 mono를 필요로 하지 않는 지원되는 운영 체제로 업그레이드하는 것이 좋습니다. 필요한 경우 Docker를 사용할 수도 있습니다.

### 다운로드 클라이언트

#### 사용 가능한 다운로드 클라이언트가 없습니다

- Radarr가 미디어를 다운로드하려면 올바르게 구성된 활성화된 다운로드 클라이언트가 필요합니다. Radarr는 다양한 다운로드 클라이언트를 지원하므로 요구 사항과 가장 일치하는 클라이언트를 결정해야 합니다. 이미 다운로드 클라이언트를 설치한 경우 Radarr에서 사용하도록 구성하고 카테고리를 만들어야 합니다. 설정 => 다운로드 클라이언트를 참조하십시오.

#### 다운로드 클라이언트와 통신할 수 없습니다

- Radarr가 구성된 다운로드 클라이언트와 통신할 수 없습니다. 다운로드 클라이언트가 작동 중인지 확인하고 URL을 다시 확인하십시오. 이는 인증 오류일 수도 있습니다.
- 일반적으로 올바르게 구성되지 않은 다운로드 클라이언트로 인해 발생합니다. 일반적으로 확인할 수 있는 사항은 다음과 같습니다.
  - 다운로드 클라이언트의 IP 주소(같은 기계의 경우 일반적으로 127.0.0.1)
  - 다운로드 클라이언트가 사용하는 포트 번호(기본 포트 번호로 채워져 있지만 변경한 경우 Radarr에도 동일한 포트 번호를 입력해야 함)
  - 로컬 네트워크에서 Radarr 인스턴스와 다운로드 클라이언트를 모두 사용하는 경우 SSL 암호화를 비활성화했는지 확인하십시오. 자세한 내용은 SSL FAQ 항목을 참조하십시오.
  - 시스템에서 IPv6를 비활성화했는지 확인하십시오.
  - DNS 서버(예: pihole)가 쿼리를 제한하지 않는지 확인하십시오.

#### 다운로드 클라이언트를 사용할 수 없습니다

- 하나 이상의 다운로드 클라이언트가 Radarr의 요청에 응답하지 않습니다. 따라서 Radarr는 일반적으로 1분마다 실행되는 다운로드 클라이언트에 대한 쿼리를 일시적으로 중지합니다. 이는 일반적으로 활성 다운로드를 추적하고 완료된 다운로드를 가져오는 데 사용됩니다. 그러나 Radarr는 계속해서 다운로드를 클라이언트에 보내려고 할 것이지만 대부분 실패할 것입니다.
- 실패 원인을 확인하려면 System=>Logs를 검토하십시오.
- 더 이상 해당 다운로드 클라이언트를 사용하지 않는 경우 Radarr에서 비활성화하여 오류를 방지하십시오.

#### 완료된 다운로드 처리 활성화

- Radarr는 완료된 다운로드 처리를 사용하여 다운로드 클라이언트가 다운로드한 파일을 가져올 수 있도록 해야 합니다. 완료된 다운로드 처리를 활성화하는 것이 좋습니다. (완료된 다운로드 처리는 새로운 사용자를 위해 기본적으로 활성화됩니다.)

#### Docker 잘못된 원격 경로 매핑

- 이 오류는 일반적으로 다운로드 클라이언트나 Radarr 내에서 잘못된 도커 경로와 관련이 있습니다.

- 예를 들어:
  - 다운로드 클라이언트: 다운로드 경로: /mnt/user/downloads:/downloads
  - Radarr: 다운로드 경로: /mnt/user/downloads:/data
- 이 예에서 다운로드 클라이언트는 다운로드를 /downloads에 저장하므로 Radarr에 완료된 영화가 /downloads에 있다고 알립니다. 그런 다음 Radarr는 "좋아요, /downloads를 확인해 보겠습니다"라고 말합니다. 그러나 Radarr에서는 /downloads 경로를 할당하지 않았으므로 /data 경로를 할당했습니다. 따라서 이 오류가 발생합니다.
- 이 문제를 해결하는 가장 쉬운 방법은 일관성입니다. 다운로드 클라이언트에서 하나의 체계를 사용하는 것입니다.

- Team Radarr는 단순히 /data를 사용하는 것을 권장합니다.
  - 다운로드 클라이언트: /mnt/user/data/downloads:/data/downloads
  - Radarr: /mnt/user/data:/data

- 이제 다운로드 클라이언트에서 다운로드를 어디에 저장할지 지정할 수 있습니다. 이는 클라이언트에 따라 다릅니다. "네, 다운로드 클라이언트는 /data/torrents(또는 usenet)/movies에 파일을 저장하십시오."라고 말할 수 있습니다. 그리고 Radarr는 완료된 다운로드 클라이언트에서 Radarr로 파일을 가져올 때 "/data에 접근할 수 있고 /torrents(또는 usenet)/movies를 볼 수 있습니다."라고 말할 것입니다.
- [Docker 가이드](/docker-guide)와 TRaSH의 [Hardlinks 및 Instant Moves (Atomic-Moves)](https://trash-guides.info/hardlinks/)에 대한 많은 글이 있습니다. 이 가이드는 하드링크와 원자적 이동에 중점을 두지만 컨테이너와 경로 매핑이 작동하는 방식이 이러한 토론의 핵심입니다.

- 자세한 내용은 [TRaSH의 원격 경로 가이드](https://trash-guides.info/Radarr/Radarr-remote-path-mapping/)를 참조하십시오.

#### 루트 폴더로 다운로드

{#downloads-in-root-folder}

- 응용 프로그램 내에서 루트 폴더는 구성된 미디어 라이브러리 폴더로 정의됩니다. 이는 마운트의 루트 폴더가 아닙니다. 다운로드 클라이언트가 루트(라이브러리) 폴더로 완료되거나 완료된 다운로드를 이동하고 있습니다.
- 이는 자주 문제를 일으키며 데이터 손실을 포함할 수 있으므로 수행해서는 안 됩니다. 이를 수정하려면 다운로드 클라이언트를 변경하여 루트 폴더에 다운로드하지 않도록 설정하십시오. '다운로드' 클라이언트의 카테고리가 루트 폴더로 설정되어 있는 경우 또는 NZBGet/SABnzbd가 정렬을 사용하고 루트 폴더로 정렬하는 경우도 포함됩니다.
- 구성된 루트 폴더(라이브러리 폴더)는 [설정 => 미디어 관리 => 루트 폴더](/radarr/settings/#root-folders)에서 찾을 수 있습니다.
- 예를 들어 다운로드가 `\data\downloads`로 이동하는 경우 루트 폴더를 `\data\downloads`로 설정한 경우입니다.
- 루트 폴더와 라이브러리 폴더는 별도로 설정해야 합니다. 라이브러리 폴더에 다운로드 클라이언트가 다운로드한 파일을 가져와서 라이브러리로 가져올 것입니다. 다운로드 클라이언트가 라이브러리로 이동하거나 다운로드할 필요가 없습니다.
- 올바른 경로 설정에 대한 자세한 내용은 [Docker 가이드](/docker-guide)와 TRaSH의 [Hardlinks 및 Instant Moves (Atomic-Moves) 가이드](https://trash-guides.info/hardlinks/)를 참조하십시오. 도커 및 비도커에 대한 개념은 이러한 토론의 핵심입니다.

> 다운로드 클라이언트가 다운로드한 파일이나 다운로드 클라이언트의 폴더와 루트/라이브러리 폴더는 별도로 설정해야 합니다. \*Arr는 다운로드 클라이언트의 폴더에서 파일을 가져와 라이브러리로 가져올 것입니다. 다운로드 클라이언트는 라이브러리로 이동하거나 다운로드하지 않아야 합니다.
{.is-warning}

#### 잘못된 다운로드 클라이언트 설정

- 다운로드 클라이언트가 파일을 다운로드하는 위치가 문제를 일으키고 있습니다. 자세한 내용은 로그를 확인하십시오. 이는 권한 문제이거나 Windows에서 Linux로 또는 Linux에서 Windows로 이동하려고 시도하고 있는 경우일 수 있습니다.

#### 잘못된 원격 경로 매핑

- 다운로드 클라이언트가 파일을 다운로드하는 위치가 문제를 일으키고 있습니다. 자세한 내용은 로그를 확인하십시오. 이는 권한 문제이거나 Windows에서 Linux로 또는 Linux에서 Windows로 이동하려고 시도하고 있는 경우일 수 있습니다. 자세한 내용은 [TRaSH의 원격 경로 가이드](https://trash-guides.info/Radarr/Radarr-remote-path-mapping/)를 참조하십시오.

#### 권한 오류

- Radarr 또는 radarr 사용자가 다운로드 클라이언트가 파일을 다운로드하는 위치에 액세스할 수 없습니다. 일반적으로 권한 문제입니다.

#### 원격 파일이 처리 중간에 제거되었습니다

- 원격 경로 매핑을 통해 액세스할 수 있는 파일이 처리가 완료되기 전에 제거된 것으로 보입니다.

#### 원격 경로가 사용되고 가져오기에 실패했습니다

- 자세한 내용은 로그를 확인하십시오. 문제를 해결하려면 [문제 해결 가이드](/radarr/faq)를 참조하십시오.

### 완료/실패한 다운로드 처리

#### 완료된 다운로드 처리가 비활성화되었습니다

- (이 경고는 완료된 다운로드 처리 기능이 구현되기 전에 기존 사용자를 위해 생성됩니다. 기존 구성과의 호환성을 보장하기 위해 이 기능은 기본적으로 비활성화되어 있습니다.)
- 완료된 다운로드 처리를 사용하는 것이 좋습니다. 완료된 다운로드 처리를 사용하면 다양한 다운로드 클라이언트의 압축 해제 및 후 처리 로직과의 호환성이 높아집니다. 이를 통해 Radarr는 다운로드 클라이언트가 준비되었다고 보고할 때까지 다운로드를 가져올 수 있습니다.
- 완료된 다운로드 처리를 사용하려면 다음을 확인해야 합니다. * 경고: 완료된 다운로드 처리는 다운로드 클라이언트와 Radarr이 동일한 기계에 있어야 합니다. 완료될 파일의 경로를 다운로드 클라이언트에서 직접 가져오기 때문입니다. 그렇지 않으면 원격 매핑이 필요합니다.

### 인덱서

#### 자동 검색이 활성화된 인덱서가 없습니다. Radarr는 자동 검색 결과를 제공하지 않습니다

- 간단히 말해서 자동 검색을 허용하는 인덱서가 없습니다.
- 설정 => 인덱서로 이동하여 자동 검색을 허

## 큐

- 큐에서는 실행 중인 작업과 예정된 작업을 확인할 수 있으며, 최근 실행된 작업의 기록과 해당 작업에 걸린 시간도 확인할 수 있습니다.

# 백업

> Radarr 인스턴스를 백업/복원하는 방법을 찾고 있다면 [여기](/radarr/faq)를 클릭하세요.
{.is-info}

- 백업 섹션에서는 이전 백업들을 확인할 수 있습니다(백업을 한 번도 하지 않은 새로운 설치인 경우를 제외하고).
  
- 지금 백업 - 이 옵션을 선택하면 Radarr 데이터베이스의 수동 백업이 트리거됩니다.
- 백업 복원 - 이 옵션을 선택하면 이전 백업에서 복원하기 위한 새로운 화면이 열립니다.
  - 파일 선택 - 이 옵션을 선택하면 브라우저에서 Radarr Zip 백업을 복원하기 위한 대화 상자가 열립니다.
  
- 이전 백업이 있고 Radarr에서 다운로드하여 표준 위치가 아닌 다른 위치에 저장하려는 경우, 이 파일 중 하나를 선택하여 다운로드할 수 있습니다.
- 이전 다운로드 옆에는 두 가지 옵션이 있습니다.
  - 복원 (시계 아이콘) - 이전 백업에서 복원하기 위해 - 이 옵션을 선택하면 복원하려는 백업을 확인하기 위한 새 창이 열립니다.
  - 삭제 (휴지통 아이콘) - 이전 백업을 삭제하기 위해

# 업데이트

- 업데이트 화면에서는 최근 5개의 업데이트와 현재 사용 중인 버전이 표시됩니다.
- 이 페이지에서는 개발자가 Radarr에 수정 또는 추가한 내용을 알려주는 업데이트 노트도 표시됩니다.

> 유지 보수 릴리스에는 버그 수정 및 기타 다양한 개선 사항이 포함됩니다. 자세한 내용은 커밋 기록을 확인하세요.
{.is-info}

# 이벤트

- 이벤트 탭에서는 Radarr 내에서 발생한 사항을 확인할 수 있습니다. 이는 일부 경미한 문제를 진단하는 데 사용될 수 있습니다. 그러나 이는 로깅에서 설명하는 추적 로그를 대체하지는 않습니다.

> 이벤트는 INFO 로그와 동등합니다. {.is-info}

- 구성 요소 - 이 열은 Radarr 내에서 트리거된 구성 요소를 알려줍니다.
- 메시지 - 이 열은 이전 열에서의 구성 요소로부터 전송된 메시지를 알려줍니다.
- 기어 아이콘 - 이 옵션을 사용하면 페이지당 표시되는 구성 요소/메시지 수를 변경할 수 있습니다(기본값은 50입니다).
- 페이지 상단의 옵션
  - 새로 고침 - 이 옵션을 선택하면 현재 페이지를 새로 고쳐 새로운 이벤트 로그를 가져옵니다.
  - 지우기 - 이 옵션을 선택하면 현재 이벤트 로그를 지우고 처음부터 시작할 수 있습니다.

# 로그 파일

- 이 페이지에서는 Radarr에 대해 현재 사용 가능한 로그 파일을 다운로드하고 확인할 수 있습니다.

- 맨 위 행에는 로그 파일을 제어할 수 있는 여러 옵션이 있습니다.

- 가장 왼쪽 상단에 있는 드롭다운에서 로그 파일과 업데이터 로그 파일로 전환할 수 있습니다.
  - 로그 파일 - 지원 문제의 핵심입니다. 로그 파일에 대한 자세한 내용은 여기에서 확인할 수 있습니다.
  - 업데이터 로그 파일 - Radarr의 업데이터 스크립트와 관련된 로그 파일을 표시합니다.

> 도커를 사용 중인 경우 이 옵션은 비어 있을 것입니다. 새로운 도커 이미지를 다운로드하여 업데이트해야 합니다.
{.is-info}

- 새로 고침 - 이 옵션을 선택하면 현재 페이지를 새로 고쳐 새로 생성된 로그를 표시합니다.
- 삭제 - 이 옵션을 선택하면 모든 로그를 지우고 처음부터 시작할 수 있습니다.
- 파일 이름 - 이는 로그와 관련된 파일 이름을 표시합니다.
- 마지막 작성 시간 - 이는 특정 로그 파일이 작성된 로컬 시간입니다.
  - Radarr는 각각 1MB로 제한된 롤링 로그 파일을 사용합니다. 현재 로그 파일은 항상 radarr.txt이며, 다른 파일들은 radarr.0.txt부터 시작하여 숫자가 높을수록 오래된 파일입니다. 총 51개의 로그 파일이 있습니다. 이 로그 파일에는 `fatal`, `error`, `warn`, `info` 항목이 포함됩니다.
  - 디버그 로그 레벨이 활성화되어 있는 경우, 추가적인 radarr.debug.txt 롤링 로그 파일이 있을 수 있습니다. 최대 51개의 파일이 있습니다. 이 로그 파일에는 `fatal`, `error`, `warn`, `info`, `debug` 항목이 포함됩니다. 보통 약 40시간 정도를 커버합니다.
  - 추적 로그 레벨이 활성화되어 있는 경우, 추가적인 radarr.trace.txt 롤링 로그 파일이 있을 수 있습니다. 최대 51개의 파일이 있습니다. 이 로그 파일에는 `fatal`, `error`, `warn`, `info`, `debug`, `trace` 항목이 포함됩니다. 추적 로그의 자세함으로 인해 최대 몇 시간 정도만 커버합니다.