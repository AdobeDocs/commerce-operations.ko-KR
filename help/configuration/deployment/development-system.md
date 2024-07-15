---
title: 개발 시스템 설정
description: Commerce 애플리케이션용 개발 시스템을 설정하는 방법을 알아봅니다.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# 개발 시스템 설정

개발 시스템 전체에 대해 다음과 같은 조건이 충족되는 경우 원하는 수만큼 개발 시스템을 보유할 수 있습니다.

- 모두 Commerce 2.2 이상을 실행합니다.
- 모든 Commerce 코드는 빌드 및 프로덕션 시스템과 동일한 저장소에서 소스 제어하에 있습니다
- 각 개발 시스템은 [기본 모드](../bootstrap/application-modes.md#default-mode) 또는 [개발자 모드](../bootstrap/application-modes.md#developer-mode)를 사용해야 합니다.
- [개발, 빌드 및 프로덕션 시스템에 대한 필수 구성 요소](../deployment/technical-details.md)에서 설명한 대로 파일 시스템 소유권 및 사용 권한이 설정되어 있습니다.
- 소스 제어에서 다음 항목이 모두 _제외됨_&#x200B;인지 확인하십시오.

   - `vendor` 디렉터리(및 하위 디렉터리)
   - `generated` 디렉터리(및 하위 디렉터리)
   - `pub/static` 디렉터리(및 하위 디렉터리)
   - `app/etc/env.php`개 파일

- 소스 제어에 `app/etc/config.php`이(가) _포함_&#x200B;되어 있는지 확인하십시오.

Git을 사용하는 경우 `.gitignore` 파일이 이전 파일의 대부분을 제공합니다. [`.gitignore` 참조](../reference/config-reference-gitignore.md)을(를) 참조하십시오.
