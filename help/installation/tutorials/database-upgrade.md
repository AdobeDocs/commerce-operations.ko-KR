---
title: 데이터베이스 스키마 및 데이터 업그레이드
description: Adobe Commerce 데이터베이스 스키마를 업그레이드하려면 다음 단계를 따르십시오.
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# 데이터베이스 스키마 및 데이터 업그레이드

이 명령을 사용하기 전에 [응용 프로그램을 설치](../advanced.md)해야 합니다.

## 데이터베이스 스키마 및 데이터 업그레이드

데이터베이스 스키마나 데이터를 변경하는 작업을 수행할 때마다 이 섹션에서 설명한 명령을 실행하여 해당 항목을 업데이트해야 합니다. 이유 목록의 일부는 다음과 같습니다.

* 명령줄을 사용하여 응용 프로그램을 업그레이드했습니다.
* 명령줄을 사용하여 구성 요소를 설치 또는 업데이트했습니다
* 명령줄을 사용하여 구성 요소를 활성화하거나 비활성화했습니다

>[!NOTE]
>
>*component*&#x200B;은(는) 모듈, 테마 또는 언어 팩일 수 있습니다. 구성 요소가 Commerce Marketplace에서 제공되는지 여부는 중요하지 않습니다.

1. 업그레이드를 시작합니다.

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   여기서 `--keep-generated`은(는) [정적 보기 파일](../../configuration/cli/static-view-file-deployment.md)을(를) 업데이트하지 않는 선택적 인수입니다. 이 선택적 인수는 숙련된 시스템 통합자가 제한된 상황에서 *only*&#x200B;를 사용하는 것입니다. [프로덕션 모드](../../configuration/bootstrap/application-modes.md#production-mode)에서 *전용*&#x200B;을 사용해야 합니다. [개발자 모드](../../configuration/bootstrap/application-modes.md#developer-mode)에서 *사용할 수 없습니다*.

1. 캐시를 정리합니다.

   ```bash
   bin/magento cache:clean
   ```
