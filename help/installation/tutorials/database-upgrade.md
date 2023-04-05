---
title: 데이터베이스 스키마 및 데이터 업그레이드
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source 데이터베이스 스키마를 업그레이드하십시오.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# 데이터베이스 스키마 및 데이터 업그레이드

이 명령을 사용하기 전에 [애플리케이션 설치](../advanced.md).

## 데이터베이스 스키마 및 데이터 업그레이드

데이터베이스 스키마나 데이터가 변경되는 작업을 수행할 때마다 이 섹션에 설명된 명령을 실행하여 업데이트해야 합니다. 다음과 같은 이유 중 일부 목록이 있습니다.

* 명령줄을 사용하여 응용 프로그램을 업그레이드했습니다
* 명령줄을 사용하여 구성 요소를 설치하거나 업데이트했습니다
* 명령줄을 사용하여 구성 요소를 활성화하거나 비활성화했습니다

>[!NOTE]
>
>A *구성 요소* 모듈, 테마 또는 언어 팩일 수 있습니다. 구성 요소가 Commerce Marketplace에서 오는지 여부는 중요하지 않습니다.

1. 업그레이드를 시작합니다.

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   위치 `--keep-generated` 은 업데이트하지 않는 선택적 인수입니다 [정적 보기 파일](../../configuration/cli/static-view-file-deployment.md). 이 선택적 인수는 사용하기 위한 것입니다 *전용* 숙련된 시스템 통합자가 제한된 환경에서 사용해야 합니다 *전용* in [프로덕션 모드](../../configuration/bootstrap/application-modes.md#production-mode). 그래야 합니다 *not* 에서 사용 [개발자 모드](../../configuration/bootstrap/application-modes.md#developer-mode).

1. 캐시 정리:

   ```bash
   bin/magento cache:clean
   ```
