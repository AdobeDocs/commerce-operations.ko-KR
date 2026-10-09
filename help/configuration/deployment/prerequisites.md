---
title: 배포 사전 요구 사항
description: 개발, 빌드 또는 프로덕션 시스템에 Commerce을 배포하기 위한 사전 요구 사항 목록을 참조하십시오.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
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
source-wordcount: '162'
ht-degree: 0%
---
# 개발, 빌드 및 프로덕션 시스템을 위한 사전 요구 사항

개발, 구축 및 운영 시스템 전반에서 파일 사용 권한과 소유권이 일관되어야 합니다. 이 작업을 수행하려면 다음 중 하나를 수행해야 합니다.

- 다음 모든 항목을 참조하십시오.

  - 모든 시스템에서 동일한 파일 시스템 소유자 사용자 이름 설정
  - 웹 서버가 모든 시스템에서 동일한 사용자로 실행되는지 확인합니다.
  - 파일 시스템 소유자가 모든 시스템의 웹 서버 그룹에 있는지 확인합니다.

- 다음 지침을 사용하여 필요에 따라 각 시스템에 대한 Commerce 파일 시스템 권한 및 소유권을 변경합니다.

  - 개발 및 빌드: [사전 설치 소유권 및 권한 설정(사용자 2명)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
  - 프로덕션: [개발 및 프로덕션의 Commerce 소유권 및 권한](file-system-permissions.md)

>[!INFO]
>
>이 방법을 선택하는 경우 빌드 시스템에서 코드를 가져올 때마다(빌드 시스템에서 파일 시스템 소유자나 웹 서버 사용자가 다른 경우) 파일 시스템 권한 및 소유권을 설정해야 합니다.
