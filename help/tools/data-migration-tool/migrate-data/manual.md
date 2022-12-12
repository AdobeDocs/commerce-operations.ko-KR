---
title: 수동 마이그레이션이 필요한 데이터
description: Magento 1에서 Magento 2 데이터 마이그레이션으로 수동으로 마이그레이션해야 하는 데이터와 그 방법을 알아봅니다.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# 수동 마이그레이션이 필요한 데이터

수동으로 마이그레이션해야 하는 데이터에는 네 가지 유형이 있습니다.

* 미디어

* [상점](https://glossary.magento.com/storefront) 디자인

* [관리](https://glossary.magento.com/admin) 사용자 계정

* ACL(액세스 제어 목록)

## 미디어

이 섹션에서는 미디어 파일을 수동으로 마이그레이션하는 방법을 설명합니다.

### 데이터베이스에 저장된 미디어 파일

>[!WARNING]
>
>데이터베이스 미디어 저장 방법은 Magento 2.4.3부터 사용되지 않습니다.


이 섹션은 사용자에게 적용됩니다 *전용* 미디어 파일을 Magento 데이터베이스에 저장하는 경우 이 단계는 먼저 수행해야 합니다 [데이터 마이그레이션](data.md):

1. 관리자로 Magento 1 관리 패널에 로그인합니다.

1. 클릭 **시스템** > **구성** > 고급 > **시스템**.

1. 오른쪽 창에서 **미디어에 대한 스토리지 구성**.

1. 에서 **미디어 데이터베이스 선택** 목록에서 이름을 클릭합니다 [미디어 저장소](https://glossary.magento.com/media-storage) 데이터베이스.

1. 클릭 **동기화**.

그런 다음 Magento 2 관리 패널에서 동일한 단계를 반복합니다.

### 파일 시스템의 미디어 파일

모든 미디어 파일(제품, 카테고리, [WYSIWYG](https://glossary.magento.com/wysiwyg) 편집자 등)은 `<your Magento 1 install dir>/media` to `<your Magento 2 install dir>/pub/media`.

하지만, *not* 복사 `.htaccess` Magento 1에 있는 파일 `media` 폴더를 입력합니다. Magento 2에는 자체 코드가 있습니다 `.htaccess` 그건 보존되어야 합니다.

## Storefront 디자인

* 파일(CSS, JS, 템플릿, [XML](https://glossary.magento.com/xml) 레이아웃) 위치 및 서식을 변경했습니다.

* [레이아웃](https://glossary.magento.com/layout) 데이터베이스에 저장된 업데이트. 의 Magento 1 관리자를 통해 배치됨 [CMS](https://glossary.magento.com/cms) 페이지, CMS 위젯, [카테고리](https://glossary.magento.com/category) 페이지 및 제품 페이지

## ACL(액세스 제어 목록)

모두 수동으로 다시 만들어야 합니다.

* 웹 서비스 API(SOAP, XML-RPC 및 REST)에 대한 자격 증명

* 관리자 사용자 계정을 액세스 권한과 연관시킵니다.

>[!NOTE]
>
>를 사용하여 데이터베이스 엔티티의 시간대를 조정할 수 있습니다 `\Migration\Handler\Timezone` 핸들러. 자세한 내용은 [후속 작업](follow-up.md) 섹션을 참조하십시오.
