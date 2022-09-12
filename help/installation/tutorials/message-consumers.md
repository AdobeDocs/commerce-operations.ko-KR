---
title: 메시지 소비자 구성
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source 메시지 큐 소비자의 동작을 구성합니다.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---


# 메시지 소비자 구성

이 명령을 실행하기 전에 다음을 수행해야 합니다 *또는* 반드시 [애플리케이션 설치](../advanced.md):

* [배포 구성 만들기 또는 업데이트](deployment.md)
* [데이터베이스 스키마 만들기](database.md)

## 소비자 동작 구성

소비자 행동 구성은 설정 함수 내에 키/값 쌍을 전송하여 수행됩니다.

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 매개 변수 설명

{{$include /help/_includes/cli-consumers.md}}
