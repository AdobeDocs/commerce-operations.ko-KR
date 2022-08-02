---
title: 개발 시스템 설정
description: Commerce 응용 프로그램을 위한 개발 시스템을 설정하는 방법을 알아봅니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# 개발 시스템 설정

모든 개발 시스템에 대해 다음 내용이 참인 경우 원하는 개수의 개발 시스템이 있을 수 있습니다.

- 모두 Commerce 2.2 이상을 실행합니다
- 모든 상거래 코드는 빌드 및 프로덕션 시스템과 동일한 리포지토리의 소스 제어에 있습니다
- 각 개발 시스템은 다음 중 하나를 사용해야 합니다 [기본 모드](../bootstrap/application-modes.md#default-mode) 또는 [개발자 모드](../bootstrap/application-modes.md#developer-mode)
- 여기에 설명된 대로 파일 시스템 소유권 및 권한이 설정되어 있습니다. [개발, 빌드 및 운영 시스템을 위한 사전 요구 사항](../deployment/technical-details.md).
- 다음을 모두 확인합니다 _제외_ 소스 제어에서 다음을 수행합니다.

   - `vendor` 디렉토리(및 하위 디렉토리)
   - `generated` 디렉토리(및 하위 디렉토리)
   - `pub/static` 디렉토리(및 하위 디렉토리)
   - `app/etc/env.php` 파일

- 확인 `app/etc/config.php` is _포함_ 소스 제어

Git을 사용하는 경우 `.gitignore` 파일의 이전 버전들은 대부분 그대로 제공됩니다. 자세한 내용은 [`.gitignore` 참조](../reference/config-reference-gitignore.md).
