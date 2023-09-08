---
title: Sonarr 원하는 것
description: 
published: true
date: 2021-11-29T22:12:55.806Z
tags: sonarr, needs-love, wanted
editor: markdown
dateCreated: 2021-06-10T01:40:02.329Z
---

# 원하는 것

Wanted => Missing 섹션에는 아직 다운로드되지 않은 디스크에 없는 모니터링 대상 에피소드의 목록이 포함되어 있습니다.

> 이 목록에는 디스크에 완전히 없는 에피소드만 포함됩니다. 디스크에 존재하지만 자르기 프로필이 충족되지 않은 에피소드는 포함되지 않습니다.
{.is-info}

- "선택된 항목 검색" - 여기에서 색인기를 사용하여 특정 에피소드를 검색할 수 있습니다.

- "선택된 항목 모니터링 해제" - 여기에서 특정 에피소드를 선택하고 관심이 없어진 경우 모니터링을 해제할 수 있습니다.

- "모두 검색" - 여기를 선택하면 모든 현재 누락된 에피소드에 대해 모든 색인기에 검색 요청이 전송됩니다. 누락된 에피소드가 몇 개인지 알려주는 경고가 포함된 대화 상자가 표시됩니다. 이는 색인기가 API 호출을 제한하는 경우에 특히 유용합니다.

> 이 검색 프로세스는 Sonarr를 다시 시작하지 않고는 시작된 후에 취소할 수 없습니다.
{.is-info}

페이지 상단에는 `수동 가져오기`가 있으며, Sonarr에서 이미 존재하는 시리즈에 대해 Sonarr이 액세스할 수 있는 임의의 위치에서 미디어 파일을 임의로 가져올 수 있습니다.

- 자동 이동은 Sonarr에서 파일을 시리즈/에피소드에 자동으로 매칭하려고 시도하며, 파일을 라이브러리 폴더로 이동시킵니다. 복사 또는 하드링크가 아닙니다.
- 대화식 가져오기를 통해 일치 항목을 검토하고 필요에 따라 다양한 사양을 조정할 수 있습니다. 파일을 `이동`하거나 `복사/하드링크`할 수 있는 옵션(왼쪽 하단)을 제공합니다. 필요에 따라 올바른 옵션을 선택하십시오.

  > 디렉토리에 100개 이상의 파일이 있는 경우 Sonarr은 해당 디렉토리를 재귀적으로 검색하지 않거나 파일을 구문 분석하고 일치시키지 않습니다. {.is-info}

# 자르기 프로필 미충족

Wanted => Cutoff Unmet 섹션에는 아직 자르기를 충족하지 못한 에피소드의 목록이 포함되어 있습니다. 자르기는 프로필 내에서 설정됩니다.

자르기는 비디오 파일의 품질이 충분히 좋다고 Sonarr에게 알리고 더 나은 품질을 계속해서 찾지 않기를 원하는 지점입니다.

이 페이지에서는 여러 가지 옵션이 제공됩니다.
![wanted-cut-off-unmet.png](/assets/sonarr/wanted-cut-off-unmet.png)

1. 선택된 항목 검색 - 목록에서 에피소드를 선택하여 기존 파일의 업그레이드 여부를 자동으로 검색할 수 있습니다.
1. 선택된 항목 모니터링 해제 - 목록에서 특정 에피소드를 선택하여 Sonarr에게 해당 에피소드의 업그레이드를 더 이상 찾지 않도록 알릴 수 있습니다.
1. 모두 검색 - 목록이 크기에 따라 (위험할 수 있음) Sonarr에게 자르기를 충족하지 못한 모든 파일을 검색하도록 지시합니다. 목록이 크지 않은 경우 유용할 수 있습니다.
1. 필터 - 결과를 필터링할 수 있습니다. 특정 에피소드나 시리즈를 검색하려는 경우 유용합니다.