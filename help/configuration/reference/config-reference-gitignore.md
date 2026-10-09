---
title: .gitigore 참조
description: Adobe Commerce 프로젝트의 .gignore 목록에 파일을 추가하는 방법을 알아봅니다. 버전 제어 관리 및 파일 제외 모범 사례를 살펴보십시오.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
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
source-wordcount: '65'
ht-degree: 0%
---
# .gitigore 참조

Magento Open Source에 기본 `.gitignore` 파일이 포함되어 있습니다. [최신 Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) 파일을 참조하십시오. `.gitignore` 목록에 있는 파일을 추가해야 하는 경우 커밋을 준비할 때 `-f`(강제) 옵션을 사용할 수 있습니다.

```shell
git add <path/filename> -f
```
