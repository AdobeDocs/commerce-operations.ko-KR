---
title: 샘플 데이터 개요
description: Adobe Commerce 및 Magento Open Source 프로젝트에 샘플 데이터를 사용하는 방법에 대해 알아봅니다.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# 샘플 데이터 개요

샘플 데이터는 제품, 카테고리, 고객 등록 등을 갖춘 Luma 테마를 기반으로 스토어프론트를 제공합니다. 이것은 상거래 상점 과 같은 기능을 하며 관리자를 사용하여 가격, 인벤토리 및 프로모션 요금제 규칙을 조작할 수 있습니다.

Commerce 소프트웨어를 설치하기 전이나 후에 샘플 데이터를 설치할 수 있습니다. 샘플 데이터를 완료하면에 설명된 대로 제거하거나 새로 설치할 수 있습니다. [샘플 데이터 모듈을 제거하거나 샘플 데이터 업데이트](remove-or-update.md).

>[!WARNING]
>
>샘플 데이터는 제거할 수 없습니다. 샘플 데이터는 Adobe Commerce 및 Magento Open Source 작동 방식에 대해서만 학습하는 것이 좋습니다. 샘플 데이터를 설치한 시스템에서 개발을 수행하지 마십시오.

다음 방법 중 하나로 선택적 샘플 데이터를 설치할 수 있습니다.

| 설치 방법 | 설명 | 필수 스킬 레벨 |
|--- |--- |--- |
| 작성기 사용 | [실행 `magento sampledata:deploy` 응용 프로그램의 루트를 수정하려면 `composer.json`](composer-packages.md) 샘플 데이터 모듈을 활성화합니다. | 작성기 지식이 필요하며 Commerce 파일 시스템에 액세스해야 합니다. |
| 저장소 복제 | [GitHub 리포지토리 복제](git-repositories.md) 샘플 데이터 저장소를 연결한 다음 서로 연결합니다. | 기여 개발자만 해당. 다른 모든 사용자는 이전 방법 중 하나를 사용해야 합니다. |
