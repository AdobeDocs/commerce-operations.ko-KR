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

이 명령을 사용하기 전에 다음을 수행해야 합니다 [응용 프로그램 설치](../advanced.md).

## 데이터베이스 스키마 및 데이터 업그레이드

데이터베이스 스키마나 데이터를 변경하는 작업을 수행할 때마다 이 섹션에서 설명한 명령을 실행하여 해당 항목을 업데이트해야 합니다. 이유 목록의 일부는 다음과 같습니다.

* 명령줄을 사용하여 응용 프로그램을 업그레이드했습니다.
* 명령줄을 사용하여 구성 요소를 설치 또는 업데이트했습니다
* 명령줄을 사용하여 구성 요소를 활성화하거나 비활성화했습니다

>[!NOTE]
>
>A *구성 요소* 는 모듈, 테마 또는 언어 팩일 수 있으며 구성 요소가 Commerce Marketplace에서 제공되는지 여부는 중요하지 않습니다.

1. 업그레이드를 시작합니다.

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   위치 `--keep-generated` 는 업데이트되지 않는 선택적 인수입니다 [정적 보기 파일](../../configuration/cli/static-view-file-deployment.md). 이 선택적 인수는 사용하기 위한 것입니다 *전용* 숙련된 시스템 통합업체의 제한된 상황. 사용해야 합니다. *전용* 위치: [프로덕션 모드](../../configuration/bootstrap/application-modes.md#production-mode). 다음과 같아야 합니다. *아님* 다음에서 사용: [개발자 모드](../../configuration/bootstrap/application-modes.md#developer-mode).

1. 캐시를 정리합니다.

   ```bash
   bin/magento cache:clean
   ```
