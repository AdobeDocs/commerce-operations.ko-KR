---
title: 데이터베이스 스키마 만들기
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source에 대한 데이터베이스를 만듭니다.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---

# 데이터베이스 스키마 만들기

이 명령을 실행하기 전에 다음을 수행해야 합니다 [배포 구성 만들기 또는 업데이트](deployment.md).

## 데이터베이스 구성 및 데이터 추가

명령 사용:

```bash
bin/magento setup:db-schema:upgrade
```

데이터베이스 상태를 보려면 다음을 입력합니다.

```bash
bin/magento setup:db:status
```
