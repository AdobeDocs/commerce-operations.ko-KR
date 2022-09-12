---
title: 데이터베이스 스키마 만들기
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source의 데이터베이스를 만듭니다.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# 데이터베이스 스키마 만들기

이 명령을 실행하기 전에 [배포 구성 만들기 또는 업데이트](deployment.md).

## 데이터베이스 구성 및 데이터 추가

명령 사용:

```bash
bin/magento setup:db-schema:upgrade
```

데이터베이스의 상태를 보려면

```bash
bin/magento setup:db:status
```
