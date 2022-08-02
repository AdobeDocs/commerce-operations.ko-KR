---
title: 배포를 위한 사전 요구 사항
description: 개발, 빌드 또는 프로덕션 시스템에 Commerce를 배포하기 위한 사전 요구 사항 목록을 참조하십시오.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# 개발, 빌드 및 프로덕션 시스템을 위한 사전 요구 사항

개발, 빌드 및 운영 시스템에서 파일 권한 및 소유권은 일관되어야 합니다. 이 작업을 수행하려면 다음 중 하나를 수행해야 합니다.

- 다음을 모두 수행합니다.

   - 동일한 설정 [파일 시스템 소유자](https://glossary.magento.com/magento-file-system-owner) 모든 시스템의 사용자 이름
   - 웹 서버가 모든 시스템에서 동일한 사용자로 실행되는지 확인하십시오
   - 파일 시스템 소유자가 모든 시스템의 웹 서버 그룹에 있는지 확인합니다

- 다음 지침을 사용하여 필요에 따라 각 시스템에 대한 상거래 파일 시스템 권한 및 소유권을 변경합니다.

   - 개발 및 빌드: [사전 설치 소유권 및 권한 설정(사용자 2명)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - 프로덕션: [개발 및 프로덕션의 상거래 소유권 및 권한](file-system-permissions.md)

>[!INFO]
>
>이 방법을 선택하는 경우 빌드 시스템에서 코드를 가져올 때마다 파일 시스템 권한 및 소유권을 설정해야 합니다(파일 시스템 소유자 또는 웹 서버 사용자가 빌드 시스템에서 다른 경우).
