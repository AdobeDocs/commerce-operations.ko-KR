---
title: 메시지 소비자 구성
description: 다음 단계에 따라 Adobe Commerce 메시지 대기열 소비자의 동작을 구성합니다.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# 메시지 소비자 구성

이 명령을 실행하기 전에 다음 *또는*&#x200B;을(를) 수행해야 합니다. [응용 프로그램을 설치](../advanced.md)해야 합니다.

* [배포 구성 만들기 또는 업데이트](deployment.md)
* [데이터베이스 스키마 만들기](database.md)

## 소비자 행동 구성

소비자 행동은 설정 함수 내에서 키/값 쌍을 전송하여 구성합니다.

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 매개 변수 설명

{{$include /help/_includes/cli-consumers.md}}
