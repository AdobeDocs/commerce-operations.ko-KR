---
title: 개발 시스템 설정
description: Commerce 애플리케이션용 개발 시스템을 설정하는 방법에 대해 알아봅니다.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# 개발 시스템 설정

개발 시스템 전체에 대해 다음과 같은 조건이 충족되는 경우 원하는 수만큼 개발 시스템을 보유할 수 있습니다.

- 모두 Commerce 2.2 이상을 실행합니다.
- 모든 상거래 코드는 빌드 및 프로덕션 시스템과 동일한 저장소에서 소스를 제어합니다
- 각 개발 시스템은 다음 중 하나를 사용해야 합니다. [기본 모드](../bootstrap/application-modes.md#default-mode) 또는 [개발자 모드](../bootstrap/application-modes.md#developer-mode)
- 에 설명된 대로 파일 시스템 소유권 및 권한이 설정되어 있습니다. [개발, 빌드 및 프로덕션 시스템의 사전 요구 사항](../deployment/technical-details.md).
- 다음 사항을 모두 확인합니다. _제외됨_ 소스 제어에서:

   - `vendor` 디렉터리(및 하위 디렉터리)
   - `generated` 디렉터리(및 하위 디렉터리)
   - `pub/static` 디렉터리(및 하위 디렉터리)
   - `app/etc/env.php` 파일

- 다음을 확인하십시오. `app/etc/config.php` 은(는) _포함됨_ 소스 제어에서

Git을 사용하는 경우 `.gitignore` 파일은 이전 파일의 대부분을 제공합니다. 다음을 참조하십시오. [`.gitignore` 참조](../reference/config-reference-gitignore.md).
