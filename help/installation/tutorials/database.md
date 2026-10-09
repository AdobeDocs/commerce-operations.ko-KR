---
title: 데이터베이스 스키마 만들기
description: 다음 단계에 따라 Adobe Commerce 프로젝트용 데이터베이스를 만듭니다.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%
---
# 데이터베이스 스키마 만들기

이 명령을 실행하기 전에 [배포 구성을 만들거나 업데이트](deployment.md)해야 합니다.

## 데이터베이스 구성 및 데이터 추가

명령 사용:

```shell
bin/magento setup:db-schema:upgrade
```

데이터베이스 상태를 보려면 다음을 입력합니다.

```shell
bin/magento setup:db:status
```
