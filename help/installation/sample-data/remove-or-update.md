---
title: 샘플 데이터 모듈 제거 또는 업데이트
description: 다음 단계에 따라 Adobe Commerce 및 Magento Open Source 샘플 데이터 모듈을 관리합니다.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# 샘플 데이터 모듈 제거 또는 업데이트

이 항목에서는 다음 방법을 설명합니다.

* [샘플 데이터 모듈 제거](#remove-sample-data-modules) Adobe Commerce 또는 Magento Open Source 설치 `composer.json`. 이 옵션은 다음을 수행합니다 *아님* 데이터베이스에서 샘플 데이터를 제거합니다.

* [샘플 데이터 업데이트 준비](#prepare-to-update-sample-data) (예: Magento 응용 프로그램을 업데이트하기 전).

## 샘플 데이터 모듈 제거

다음 명령을 입력합니다.

```bash
bin/magento sampledata:remove
```

샘플 데이터 모듈의 전체 목록은 다음과 같습니다.

Adobe Commerce 및 Magento Open Source:

* `magento/module-bundle-sample-data`
* `magento/module-catalog-rule-sample-data`
* `magento/module-catalog-sample-data`
* `magento/module-cms-sample-data`
* `magento/module-configurable-sample-data`
* `magento/module-customer-sample-data`
* `magento/module-downloadable-sample-data`
* `magento/module-grouped-product-sample-data`
* `magento/module-msrp-sample-data`
* `magento/module-offline-shipping-sample-data`
* `magento/module-product-links-sample-data`
* `magento/module-review-sample-data`
* `magento/module-sales-rule-sample-data`
* `magento/module-sales-sample-data`
* `magento/module-sample-data`
* `magento/module-swatches-sample-data`
* `magento/module-tax-sample-data`
* `magento/module-theme-sample-data`
* `magento/module-widget-sample-data`
* `magento/module-wishlist-sample-data`
* `magento/sample-data-media`

Adobe Commerce만:

* `magento/module-customer-balance-sample-data`
* `magento/module-gift-card-sample-data`
* `magento/module-gift-registry-sample-data`
* `magento/module-multiple-wishlist-sample-data`
* `magento/module-target-rule-sample-data`

## 샘플 데이터 업데이트 준비

이 명령을 사용하면 Adobe Commerce 또는 Magento Open Source을 업데이트하기 전에 샘플 데이터를 업데이트할 수 있습니다.

업데이트할 샘플 데이터를 준비하려면 다음 명령을 입력합니다.

```bash
bin/magento sampledata:reset
```

그 이후에, [애플리케이션 업데이트](../tutorials/uninstall.md#update-the-application).
