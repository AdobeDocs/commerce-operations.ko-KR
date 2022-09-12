---
title: 샘플 데이터 개요
description: Adobe Commerce 및 Magento Open Source 프로젝트에 샘플 데이터를 사용하는 방법에 대해 알아봅니다.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# 샘플 데이터 개요

샘플 데이터는 제품, 카테고리, 고객 등록 등이 포함된 Luma 테마를 기반으로 스토어를 제공합니다. 이 기능은 커머스 스토어프런트와 마찬가지로 작동하며 관리자를 사용하여 가격, 재고 및 판촉 가격 규칙을 조작할 수 있습니다.

상거래 소프트웨어를 설치하기 전이나 후에 샘플 데이터를 설치할 수 있습니다. 샘플 데이터로 작업을 마치면 해당 데이터를 제거하거나, 에 설명된 대로 새로 설치할 수 있습니다. [샘플 데이터 모듈 제거 또는 샘플 데이터 업데이트](remove-or-update.md).

>[!WARNING]
>
>샘플 데이터는 제거할 수 없습니다. Adobe Commerce 및 Magento Open Source 작동 방식에 대해 알아보려면 샘플 데이터만 사용하는 것이 좋습니다. 샘플 데이터를 설치한 시스템에서 개발을 수행하지 마십시오.

다음 방법 중 하나로 선택적 샘플 데이터를 설치할 수 있습니다.

| 설치 방법 | 설명 | 필수 기술 수준 |
|--- |--- |--- |
| 작성기 사용 | [실행 `magento sampledata:deploy` 응용 프로그램의 루트를 수정하려면 `composer.json`](composer-packages.md) 샘플 데이터 모듈을 활성화하려면 | Composer 지식과 상거래 파일 시스템에 대한 액세스 권한이 필요합니다. |
| 리포지토리 복제 | [GitHub 리포지토리 복제](git-repositories.md) 샘플 데이터 저장소를 연결한 다음 서로 연결합니다. | 기여 개발자에게만 해당됩니다. 다른 모든 사용자는 앞의 방법 중 하나를 사용해야 합니다. |
