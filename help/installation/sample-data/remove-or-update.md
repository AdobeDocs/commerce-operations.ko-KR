---
title: 샘플 데이터 모듈 제거 또는 업데이트
description: 다음 단계에 따라 Adobe Commerce 및 Magento Open Source 샘플 데이터 모듈을 관리합니다.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# 샘플 데이터 모듈 제거 또는 업데이트

이 항목에서는 다음 방법을 설명합니다.

* [샘플 데이터 모듈 제거](#remove-sample-data-modules) Adobe Commerce 또는 Magento Open Source 설치에서 `composer.json`. 이 옵션은 *not* 데이터베이스에서 샘플 데이터를 제거합니다.

* [샘플 데이터 업데이트 준비](#prepare-to-update-sample-data) (예를 들어 Magento 애플리케이션을 업데이트하기 전에)

## 샘플 데이터 모듈 제거

다음 명령을 입력합니다.

```bash
bin/magento sampledata:remove
```

다음은 샘플 데이터 모듈의 전체 목록입니다.

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

Adobe Commerce 전용:

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

그 후에 [애플리케이션 업데이트](../tutorials/uninstall.md#update-the-application).
