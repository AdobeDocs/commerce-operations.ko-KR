---
source-git-commit: 6752688390a8bea98b49d235515f094386d88bd4
workflow-type: tm+mt
source-wordcount: '3444'
ht-degree: 0%

---
# Magento Open Source 패키지

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

Magento Open Source은 Composer를 사용하여 PHP 패키지를 관리합니다.

`composer.json` 파일은 패키지 목록을 선언하지만, `composer.lock` 파일은 Magento Open Source 설치를 빌드하는 데 사용되는 패키지의 전체 목록(각 패키지 및 해당 종속 항목의 전체 버전)을 저장합니다.

다음 참조 설명서는 `composer.lock` 파일에서 생성되며 Magento Open Source 2.4.8에 포함된 필수 패키지에 대해 설명합니다.

## 종속성

`magento/product-community-edition 2.4.8`에 다음 종속성이 있습니다.

- adobe-commerce/os-extensions-metapackage: 1.0.1
- colinmollenhour/cache-backend-file: ^1.4
- colinmollenhour/cache-backend-redis: ^1.16
- colinmollenhour/credis: ^1.15
- colinmollenhour/php-redis-session-abstract: ^2.0
- 작성기/작성기: ^2.0, !=2.2.16
- duosecurity/duo_api_php: ^1.1
- duosecurity/duo_universal_php: ^1.0
- elasticsearch/elasticsearch: ^8.15
- ext-bcmath: *
- ext-ctype: *
- ext-curl: *
- ext-dom: *
- ext-ftp: *
- ext-gd: *
- ext-hash: *
- ext-iconv: *
- ext-intl: *
- ext-mbstring: *
- ext-openssl: *
- ext-pdo_mysql: *
- ext-simplexml: *
- ext-soap: *
- ext-sodium: *
- ext-xsl: *
- ext-zip: *
- ezyang/htmlclearer: ^4.17
- guzzlehttp/guzzle: ^7.5
- laminas/laminas-captcha: ^2.18
- laminas/laminas-code: ^4.13
- laminas/laminas-di: ^3.15
- laminas/laminas-escaper: ^2.13
- laminas/laminas-eventmanager: ^3.11
- laminas/laminas 피드: ^2.22
- 라미나스/라미나스 필터: ^2.33
- laminas/laminas-http: ^2.15
- laminas/laminas-i18n: ^2.17
- laminas/laminas-modulemanager: ^2.11
- laminas/laminas-mvc: ^3.6
- laminas/laminas-permissions-acl: ^2.10
- laminas/laminas-servicemanager: ^3.16
- laminas/laminas-soap: ^2.10
- laminas/laminas-stdlib: ^3.11
- laminas/laminas-uri: ^2.9
- laminas/laminas-validator: ^2.23
- league/flysystem: ^3.0
- league/flysystem-aws-s3-v3: ^3.0
- lib-libxml: *
- magento/composer: ^1.10.1-beta1
- magento/composer-dependency-version-audit-plugin: ^0.1
- magento/framework: 103.0.8
- magento/framework-amqp: 100.4.6
- magento/framework-bulk: 101.0.4
- magento/framework-message-queue: 100.4.8
- magento/inventory-metapackage: 1.2.8
- magento/language-de_de: 100.4.0
- magento/language-en_us: 100.4.0
- magento/language-es_es: 100.4.0
- magento/language-fr_fr: 100.4.0
- magento/language-nl_nl: 100.4.0
- magento/language-pt_br: 100.4.0
- magento/language-zh_hans_cn: 100.4.0
- magento/magento-composer-installer: >=0.4.0
- magento/magento-zf-db: ^3.21.0
- magento/magento2 베이스: 2.4.8
- [magento/module-admin-analytics](https://developer.adobe.com/commerce/php/module-reference/module-admin-analytics/): 100.4.7
- [magento/module-admin-notification](https://developer.adobe.com/commerce/php/module-reference/module-admin-notification/): 100.4.7
- [magento/module-advanced-pricing-import-export](https://developer.adobe.com/commerce/php/module-reference/module-advanced-pricing-import-export/): 100.4.8
- [magento/module-advanced-search](https://developer.adobe.com/commerce/php/module-reference/module-advanced-search/): 100.4.6
- [magento/module-amqp](https://developer.adobe.com/commerce/php/module-reference/module-amqp/): 100.4.5
- [magento/module-analytics](https://developer.adobe.com/commerce/php/module-reference/module-analytics/): 100.4.8
- [magento/module-application-performance-monitor](https://developer.adobe.com/commerce/php/module-reference/module-application-performance-monitor/): 100.4.1
- [magento/module-application-performance-monitor-new-relic](https://developer.adobe.com/commerce/php/module-reference/module-application-performance-monitor-new-relic/): 100.4.1
- [magento/module-async-config](https://developer.adobe.com/commerce/php/module-reference/module-async-config/): 100.4.1
- [magento/module-asynchronous-operations](https://developer.adobe.com/commerce/php/module-reference/module-asynchronous-operations/): 100.4.8
- [magento/module-authorization](https://developer.adobe.com/commerce/php/module-reference/module-authorization/): 100.4.8
- [magento/module-aws-s3](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3/): 100.4.6
- [magento/module-backend](https://developer.adobe.com/commerce/php/module-reference/module-backend/): 102.0.8
- [magento/module-backup](https://developer.adobe.com/commerce/php/module-reference/module-backup/): 100.4.8
- [magento/module-bundle](https://developer.adobe.com/commerce/php/module-reference/module-bundle/): 101.0.8
- [magento/module-bundle-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-bundle-graph-ql/): 100.4.8
- [magento/module-bundle-import-export](https://developer.adobe.com/commerce/php/module-reference/module-bundle-import-export/): 100.4.7
- [magento/module-cache-invalidate](https://developer.adobe.com/commerce/php/module-reference/module-cache-invalidate/): 100.4.6
- [magento/module-captcha](https://developer.adobe.com/commerce/php/module-reference/module-captcha/): 100.4.8
- [magento/module-cardinal-commerce](https://developer.adobe.com/commerce/php/module-reference/module-cardinal-commerce/): 100.4.6
- [magento/module-catalog](https://developer.adobe.com/commerce/php/module-reference/module-catalog/): 104.0.8
- [magento/module-catalog-analytics](https://developer.adobe.com/commerce/php/module-reference/module-catalog-analytics/): 100.4.5
- [magento/module-catalog-cms-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-cms-graph-ql/): 100.4.4
- [magento/module-catalog-customer-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-customer-graph-ql/): 100.4.7
- [magento/module-catalog-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-graph-ql/): 100.4.8
- [magento/module-catalog-import-export](https://developer.adobe.com/commerce/php/module-reference/module-catalog-import-export/): 101.1.8
- [magento/module-catalog-inventory](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory/): 100.4.8
- [magento/module-catalog-inventory-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory-graph-ql/): 100.4.5
- [magento/module-catalog-rule](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule/): 101.2.8
- [magento/module-catalog-rule-configurable](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-configurable/): 100.4.7
- [magento/module-catalog-rule-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-graph-ql/): 100.4.5
- [magento/module-catalog-search](https://developer.adobe.com/commerce/php/module-reference/module-catalog-search/): 102.0.8
- [magento/module-catalog-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite/): 100.4.8
- [magento/module-catalog-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite-graph-ql/): 100.4.6
- [magento/module-catalog-widget](https://developer.adobe.com/commerce/php/module-reference/module-catalog-widget/): 100.4.8
- [magento/module-checkout](https://developer.adobe.com/commerce/php/module-reference/module-checkout/): 100.4.8
- [magento/module-checkout-agreements](https://developer.adobe.com/commerce/php/module-reference/module-checkout-agreements/): 100.4.7
- [magento/module-checkout-agreements-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-checkout-agreements-graph-ql/): 100.4.4
- [magento/module-cms](https://developer.adobe.com/commerce/php/module-reference/module-cms/): 104.0.8
- [magento/module-cms-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-cms-graph-ql/): 100.4.5
- [magento/module-cms-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-cms-url-rewrite/): 100.4.7
- [magento/module-cms-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-cms-url-rewrite-graph-ql/): 100.4.6
- [magento/module-compare-list-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-compare-list-graph-ql/): 100.4.4
- [magento/module-config](https://developer.adobe.com/commerce/php/module-reference/module-config/): 101.2.8
- [magento/module-configurable-import-export](https://developer.adobe.com/commerce/php/module-reference/module-configurable-import-export/): 100.4.6
- [magento/module-configurable-product](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product/): 100.4.8
- [magento/module-configurable-product-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-graph-ql/): 100.4.8
- [magento/module-configurable-product-sales](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-sales/): 100.4.5
- [magento/module-contact](https://developer.adobe.com/commerce/php/module-reference/module-contact/): 100.4.7
- [magento/module-contact-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-contact-graph-ql/): 100.4.1
- [magento/module-cookie](https://developer.adobe.com/commerce/php/module-reference/module-cookie/): 100.4.8
- [magento/module-cron](https://developer.adobe.com/commerce/php/module-reference/module-cron/): 100.4.8
- [magento/module-csp](https://developer.adobe.com/commerce/php/module-reference/module-csp/): 100.4.7
- [magento/module-currency-symbol](https://developer.adobe.com/commerce/php/module-reference/module-currency-symbol/): 100.4.6
- [magento/module-customer](https://developer.adobe.com/commerce/php/module-reference/module-customer/): 103.0.8
- [magento/module-customer-analytics](https://developer.adobe.com/commerce/php/module-reference/module-customer-analytics/): 100.4.5
- [magento/module-customer-downloadable-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-downloadable-graph-ql/): 100.4.4
- [magento/module-customer-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-graph-ql/): 100.4.8
- [magento/module-customer-import-export](https://developer.adobe.com/commerce/php/module-reference/module-customer-import-export/): 100.4.8
- [magento/module-deploy](https://developer.adobe.com/commerce/php/module-reference/module-deploy/): 100.4.8
- [magento/module-developer](https://developer.adobe.com/commerce/php/module-reference/module-developer/): 100.4.8
- [magento/module-dhl](https://developer.adobe.com/commerce/php/module-reference/module-dhl/): 100.4.7
- [magento/module-directory](https://developer.adobe.com/commerce/php/module-reference/module-directory/): 100.4.8
- [magento/module-directory-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-directory-graph-ql/): 100.4.6
- [magento/module-downloadable](https://developer.adobe.com/commerce/php/module-reference/module-downloadable/): 100.4.8
- [magento/module-downloadable-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-graph-ql/): 100.4.8
- [magento/module-downloadable-import-export](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-import-export/): 100.4.7
- [magento/module-eav](https://developer.adobe.com/commerce/php/module-reference/module-eav/): 102.1.8
- [magento/module-eav-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-eav-graph-ql/): 100.4.5
- [magento/module-elasticsearch](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch/): 101.0.8
- [magento/module-elasticsearch-8](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-8/): 101.0.0
- [magento/module-email](https://developer.adobe.com/commerce/php/module-reference/module-email/): 101.1.8
- [magento/module-encryption-key](https://developer.adobe.com/commerce/php/module-reference/module-encryption-key/): 100.4.6
- [magento/module-fedex](https://developer.adobe.com/commerce/php/module-reference/module-fedex/): 100.4.6
- [magento/module-gift-message](https://developer.adobe.com/commerce/php/module-reference/module-gift-message/): 100.4.7
- [magento/module-gift-message-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-message-graph-ql/): 100.4.6
- [magento/module-google-adwords](https://developer.adobe.com/commerce/php/module-reference/module-google-adwords/): 100.4.5
- [magento/module-google-analytics](https://developer.adobe.com/commerce/php/module-reference/module-google-analytics/): 100.4.4
- [magento/module-google-gtag](https://developer.adobe.com/commerce/php/module-reference/module-google-gtag/): 100.4.3
- [magento/module-google-optimizer](https://developer.adobe.com/commerce/php/module-reference/module-google-optimizer/): 100.4.7
- [magento/module-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql/): 100.4.8
- [magento/module-graph-ql-cache](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql-cache/): 100.4.5
- [magento/module-graph-ql-new-relic](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql-new-relic/): 100.4.1
- [magento/module-graph-ql-resolver-cache](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql-resolver-cache/): 100.4.1
- [magento/module-grouped-catalog-inventory](https://developer.adobe.com/commerce/php/module-reference/module-grouped-catalog-inventory/): 100.4.5
- [magento/module-grouped-import-export](https://developer.adobe.com/commerce/php/module-reference/module-grouped-import-export/): 100.4.6
- [magento/module-grouped-product](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product/): 100.4.8
- [magento/module-grouped-product-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product-graph-ql/): 100.4.8
- [magento/module-import-export](https://developer.adobe.com/commerce/php/module-reference/module-import-export/): 101.0.8
- [magento/module-indexer](https://developer.adobe.com/commerce/php/module-reference/module-indexer/): 100.4.8
- [magento/module-instant-purchase](https://developer.adobe.com/commerce/php/module-reference/module-instant-purchase/): 100.4.7
- [magento/module-integration](https://developer.adobe.com/commerce/php/module-reference/module-integration/): 100.4.8
- [magento/module-integration-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-integration-graph-ql/): 100.4.1
- [magento/module-jwt-framework-adapter](https://developer.adobe.com/commerce/php/module-reference/module-jwt-framework-adapter/): 100.4.4
- [magento/module-jwt-user-token](https://developer.adobe.com/commerce/php/module-reference/module-jwt-user-token/): 100.4.3
- [magento/module-layered-navigation](https://developer.adobe.com/commerce/php/module-reference/module-layered-navigation/): 100.4.8
- [magento/module-login-as-customer](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer/): 100.4.8
- [magento/module-login-as-customer-admin-ui](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-admin-ui/): 100.4.8
- [magento/module-login-as-customer-api](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-api/): 100.4.7
- [magento/module-login-as-customer-assistance](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-assistance/): 100.4.7
- [magento/module-login-as-customer-frontend-ui](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-frontend-ui/): 100.4.7
- [magento/module-login-as-customer-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-graph-ql/): 100.4.5
- [magento/module-login-as-customer-log](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-log/): 100.4.6
- [magento/module-login-as-customer-page-cache](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-page-cache/): 100.4.7
- [magento/module-login-as-customer-quote](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-quote/): 100.4.6
- [magento/module-login-as-customer-sales](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-sales/): 100.4.7
- [magento/module-marketplace](https://developer.adobe.com/commerce/php/module-reference/module-marketplace/): 100.4.6
- [magento/module-media-content](https://developer.adobe.com/commerce/php/module-reference/module-media-content/): 100.4.6
- [magento/module-media-content-api](https://developer.adobe.com/commerce/php/module-reference/module-media-content-api/): 100.4.7
- [magento/module-media-content-catalog](https://developer.adobe.com/commerce/php/module-reference/module-media-content-catalog/): 100.4.6
- [magento/module-media-content-cms](https://developer.adobe.com/commerce/php/module-reference/module-media-content-cms/): 100.4.6
- [magento/module-media-content-synchronization](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization/): 100.4.7
- [magento/module-media-content-synchronization-api](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization-api/): 100.4.6
- [magento/module-media-content-synchronization-catalog](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization-catalog/): 100.4.5
- [magento/module-media-content-synchronization-cms](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization-cms/): 100.4.5
- [magento/module-media-gallery](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery/): 100.4.7
- [magento/module-media-gallery-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-api/): 101.0.7
- [magento/module-media-gallery-catalog](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-catalog/): 100.4.5
- [magento/module-media-gallery-catalog-integration](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-catalog-integration/): 100.4.5
- [magento/module-media-gallery-catalog-ui](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-catalog-ui/): 100.4.5
- [magento/module-media-gallery-cms-ui](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-cms-ui/): 100.4.5
- [magento/module-media-gallery-integration](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-integration/): 100.4.7
- [magento/module-media-gallery-metadata](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-metadata/): 100.4.6
- [magento/module-media-gallery-metadata-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-metadata-api/): 100.4.5
- [magento/module-media-gallery-renditions](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-renditions/): 100.4.6
- [magento/module-media-gallery-renditions-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-renditions-api/): 100.4.5
- [magento/module-media-gallery-synchronization](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-synchronization/): 100.4.7
- [magento/module-media-gallery-synchronization-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-synchronization-api/): 100.4.6
- [magento/module-media-gallery-synchronization-metadata](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-synchronization-metadata/): 100.4.4
- [magento/module-media-gallery-ui](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-ui/): 100.4.7
- [magento/module-media-gallery-ui-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-ui-api/): 100.4.6
- [magento/module-media-storage](https://developer.adobe.com/commerce/php/module-reference/module-media-storage/): 100.4.7
- [magento/module-message-queue](https://developer.adobe.com/commerce/php/module-reference/module-message-queue/): 100.4.8
- [magento/module-msrp](https://developer.adobe.com/commerce/php/module-reference/module-msrp/): 100.4.7
- [magento/module-msrp-configurable-product](https://developer.adobe.com/commerce/php/module-reference/module-msrp-configurable-product/): 100.4.5
- [magento/module-msrp 그룹화된 제품](https://developer.adobe.com/commerce/php/module-reference/module-msrp-grouped-product/): 100.4.5
- [magento/module-multishipping](https://developer.adobe.com/commerce/php/module-reference/module-multishipping/): 100.4.8
- [magento/module-mysql-mq](https://developer.adobe.com/commerce/php/module-reference/module-mysql-mq/): 100.4.6
- [magento/module-new-relic-reporting](https://developer.adobe.com/commerce/php/module-reference/module-new-relic-reporting/): 100.4.6
- [magento/module-newsletter](https://developer.adobe.com/commerce/php/module-reference/module-newsletter/): 100.4.8
- [magento/module-newsletter-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-newsletter-graph-ql/): 100.4.5
- [magento/module-offline-payments](https://developer.adobe.com/commerce/php/module-reference/module-offline-payments/): 100.4.6
- [magento/module-offline-shipping](https://developer.adobe.com/commerce/php/module-reference/module-offline-shipping/): 100.4.7
- [magento/module-open-search](https://developer.adobe.com/commerce/php/module-reference/module-open-search/): 100.4.2
- [magento/module-order-cancellation](https://developer.adobe.com/commerce/php/module-reference/module-order-cancellation/): 100.4.1
- [magento/module-order-cancellation-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-order-cancellation-graph-ql/): 100.4.1
- [magento/module-order-cancellation-ui](https://developer.adobe.com/commerce/php/module-reference/module-order-cancellation-ui/): 100.4.1
- [magento/module-page-cache](https://developer.adobe.com/commerce/php/module-reference/module-page-cache/): 100.4.8
- [magento/module-payment](https://developer.adobe.com/commerce/php/module-reference/module-payment/): 100.4.8
- [magento/module-payment-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-payment-graph-ql/): 100.4.3
- [magento/module-paypal](https://developer.adobe.com/commerce/php/module-reference/module-paypal/): 101.0.8
- [magento/module-paypal-captcha](https://developer.adobe.com/commerce/php/module-reference/module-paypal-captcha/): 100.4.5
- [magento/module-paypal-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-paypal-graph-ql/): 100.4.6
- [magento/module-persistent](https://developer.adobe.com/commerce/php/module-reference/module-persistent/): 100.4.8
- [magento/module-product-alert](https://developer.adobe.com/commerce/php/module-reference/module-product-alert/): 100.4.7
- [magento/module-product-video](https://developer.adobe.com/commerce/php/module-reference/module-product-video/): 100.4.8
- [magento/module-quote](https://developer.adobe.com/commerce/php/module-reference/module-quote/): 101.2.8
- [magento/module-quote-analytics](https://developer.adobe.com/commerce/php/module-reference/module-quote-analytics/): 100.4.7
- [magento/module-quote-bundle-options](https://developer.adobe.com/commerce/php/module-reference/module-quote-bundle-options/): 100.4.4
- [magento/module-quote-configurable-options](https://developer.adobe.com/commerce/php/module-reference/module-quote-configurable-options/): 100.4.4
- [magento/module-quote-downloadable-links](https://developer.adobe.com/commerce/php/module-reference/module-quote-downloadable-links/): 100.4.4
- [magento/module-quote-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-quote-graph-ql/): 100.4.8
- [magento/module-related-product-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-related-product-graph-ql/): 100.4.5
- [magento/module-release-notification](https://developer.adobe.com/commerce/php/module-reference/module-release-notification/): 100.4.6
- [magento/module-remote-storage](https://developer.adobe.com/commerce/php/module-reference/module-remote-storage/): 100.4.6
- [magento/module-reports](https://developer.adobe.com/commerce/php/module-reference/module-reports/): 100.4.8
- [magento/module-require-js](https://developer.adobe.com/commerce/php/module-reference/module-require-js/): 100.4.4
- [magento/module-review](https://developer.adobe.com/commerce/php/module-reference/module-review/): 100.4.8
- [magento/module-review-analytics](https://developer.adobe.com/commerce/php/module-reference/module-review-analytics/): 100.4.5
- [magento/module-review-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-review-graph-ql/): 100.4.4
- [magento/module-robots](https://developer.adobe.com/commerce/php/module-reference/module-robots/): 101.1.4
- [magento/module-rss](https://developer.adobe.com/commerce/php/module-reference/module-rss/): 100.4.6
- [magento/module-rule](https://developer.adobe.com/commerce/php/module-reference/module-rule/): 100.4.7
- [magento/module-sales](https://developer.adobe.com/commerce/php/module-reference/module-sales/): 103.0.8
- [magento/module-sales-analytics](https://developer.adobe.com/commerce/php/module-reference/module-sales-analytics/): 100.4.5
- [magento/module-sales-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-sales-graph-ql/): 100.4.8
- [magento/module-sales-inventory](https://developer.adobe.com/commerce/php/module-reference/module-sales-inventory/): 100.4.5
- [magento/module-sales-rule](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule/): 101.2.8
- [magento/module-sales-rule-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule-graph-ql/): 100.4.1
- [magento/module-sales-sequence](https://developer.adobe.com/commerce/php/module-reference/module-sales-sequence/): 100.4.5
- [magento/module-sample-data](https://developer.adobe.com/commerce/php/module-reference/module-sample-data/): 100.4.6
- [magento/module-search](https://developer.adobe.com/commerce/php/module-reference/module-search/): 101.1.8
- [magento/module-security](https://developer.adobe.com/commerce/php/module-reference/module-security/): 100.4.8
- [magento/module-send-friend](https://developer.adobe.com/commerce/php/module-reference/module-send-friend/): 100.4.6
- [magento/module-send-friend-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-send-friend-graph-ql/): 100.4.4
- [magento/module-shipping](https://developer.adobe.com/commerce/php/module-reference/module-shipping/): 100.4.8
- [magento/module-sitemap](https://developer.adobe.com/commerce/php/module-reference/module-sitemap/): 100.4.7
- [magento/module-store](https://developer.adobe.com/commerce/php/module-reference/module-store/): 101.1.8
- [magento/module-store-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-store-graph-ql/): 100.4.6
- [magento/module-swagger](https://developer.adobe.com/commerce/php/module-reference/module-swagger/): 100.4.7
- [magento/module-swagger-webapi](https://developer.adobe.com/commerce/php/module-reference/module-swagger-webapi/): 100.4.4
- [magento/module-swagger-webapi-async](https://developer.adobe.com/commerce/php/module-reference/module-swagger-webapi-async/): 100.4.4
- [magento/module-swatches](https://developer.adobe.com/commerce/php/module-reference/module-swatches/): 100.4.8
- [magento/module-swatches-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-swatches-graph-ql/): 100.4.6
- [magento/module-swatches-layered-navigation](https://developer.adobe.com/commerce/php/module-reference/module-swatches-layered-navigation/): 100.4.4
- [magento/module-tax](https://developer.adobe.com/commerce/php/module-reference/module-tax/): 100.4.8
- [magento/module-tax-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-tax-graph-ql/): 100.4.4
- [magento/module-tax-import-export](https://developer.adobe.com/commerce/php/module-reference/module-tax-import-export/): 100.4.7
- [magento/module-theme](https://developer.adobe.com/commerce/php/module-reference/module-theme/): 101.1.8
- [magento/module-theme-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-theme-graph-ql/): 100.4.5
- [magento/module-translation](https://developer.adobe.com/commerce/php/module-reference/module-translation/): 100.4.8
- [magento/module-ui](https://developer.adobe.com/commerce/php/module-reference/module-ui/): 101.2.8
- [magento/module-ups](https://developer.adobe.com/commerce/php/module-reference/module-ups/): 100.4.8
- [magento/module-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-url-rewrite/): 102.0.7
- [magento/module-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-url-rewrite-graph-ql/): 100.4.7
- [magento/module-user](https://developer.adobe.com/commerce/php/module-reference/module-user/): 101.2.8
- [magento/module-usps](https://developer.adobe.com/commerce/php/module-reference/module-usps/): 100.4.7
- [magento/module-variable](https://developer.adobe.com/commerce/php/module-reference/module-variable/): 100.4.6
- [magento/module-vault](https://developer.adobe.com/commerce/php/module-reference/module-vault/): 101.2.8
- [magento/module-vault-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-vault-graph-ql/): 100.4.4
- [magento/module-version](https://developer.adobe.com/commerce/php/module-reference/module-version/): 100.4.5
- [magento/module-webapi](https://developer.adobe.com/commerce/php/module-reference/module-webapi/): 100.4.7
- [magento/module-webapi-async](https://developer.adobe.com/commerce/php/module-reference/module-webapi-async/): 100.4.6
- [magento/module-webapi-security](https://developer.adobe.com/commerce/php/module-reference/module-webapi-security/): 100.4.5
- [magento/module-weee](https://developer.adobe.com/commerce/php/module-reference/module-weee/): 100.4.8
- [magento/module-weee-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-weee-graph-ql/): 100.4.5
- [magento/module-widget](https://developer.adobe.com/commerce/php/module-reference/module-widget/): 101.2.8
- [magento/module-wishlist](https://developer.adobe.com/commerce/php/module-reference/module-wishlist/): 101.2.8
- [magento/module-wishlist-analytics](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-analytics/): 100.4.6
- [magento/module-wishlist-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-graph-ql/): 100.4.8
- magento/page-builder: 1.7.5
- magento/security-package: 1.1.7
- magento/theme-adminhtml-backend: 100.4.8
- magento/theme-frontend-blank: 100.4.8
- magento/theme-frontend-luma: 100.4.8
- magento/zend-cache: ^1.16
- magento/zend-db: ^1.16
- magento/zend-pdf: ^1.16
- 독백/독백: ^3.6
- opensearch-project/opensearch-php: ^2.3
- pelago/emogrifier: ^7.0
- php: ~8.2.0||~8.3.0|~8.4.0
- php-amqplib/php-amqplib: ^3.2
- phpseclib/mcrypt_compat: ^2.0
- phpseclib/phpseclib: ^3.0
- psr/log: ^2 || ^3
- ramsey/uuid: ^4.2
- symfony/console: ^6.4
- symfony/intl: ^6.4
- 교감/메일 받는 사람: ^6.4
- symfony/mime: ^6.4
- symfony/process: ^6.4
- symfony/string: ^6.4
- tedivm/jshrink: ^1.4
- tubalmartin/cssmin: ^4.1
- 웹 토큰/jwt 프레임워크: ^3.4
- webonyx/graphql-php: ^15.0
- wikimedia/less.php: ^5.0

## 타사 라이선스

### Apache-2.0, LGPL-2.1 전용

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php">opensearch-project/opensearch-php</a>
    </td>
    <td>라이브러리</td>
    <td>OpenSearch용 PHP 클라이언트</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/adobe/stock-api-libphp">astock/stock-api-libphp</a>
    </td>
    <td>라이브러리</td>
    <td>Adobe Stock API 라이브러리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php">aws/aws-crt-php</a>
    </td>
    <td>라이브러리</td>
    <td>PHP용 AWS 공용 런타임</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php">aws/aws-sdk-php</a>
    </td>
    <td>라이브러리</td>
    <td>PHP용 AWS SDK - PHP 프로젝트에서 Amazon Web Services 사용</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api">원격 분석 열기/api</a>
    </td>
    <td>라이브러리</td>
    <td>OpenTelemetry PHP용 API입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context">원격 분석 열기/컨텍스트</a>
    </td>
    <td>라이브러리</td>
    <td>OpenTelemetry PHP에 대한 컨텍스트 구현입니다.</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>메타패키지</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php">wikimedia/less.php</a>
    </td>
    <td>라이브러리</td>
    <td>LESS 프로세서의 PHP 포트</td>
  </tr>
  </tbody>
</table>

### - 조항

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode">베이컨/베이컨-qr-코드</a>
    </td>
    <td>라이브러리</td>
    <td>BaconQrCode는 PHP용 QR 코드 생성기입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum">dasprid/enum</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 7.1 enum 구현</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer">webimpress/safe-writer</a>
    </td>
    <td>라이브러리</td>
    <td>경합 조건을 피하기 위해 파일을 안전하게 작성하는 도구</td>
  </tr>
  </tbody>
</table>

### - 조항

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File">colinmollenhour/cache-backend-file</a>
    </td>
    <td>Magento 모듈</td>
    <td>Stock Zend_Cache_Backend_File 백엔드는 캐시된 항목의 수가 증가하면 사용할 수 없게 되기 때문에 태그로 정리하는 성능이 매우 낮습니다. 이 백엔드는 특히 태그 정리를 위해 많은 변경 사항을 적용하여 큰 성능 향상을 가져옵니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>라이브러리</td>
    <td>낙관적 잠금을 사용하는 Redis 기반 세션 처리기</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php">duosecurity/duo_universal_php</a>
    </td>
    <td>라이브러리</td>
    <td>듀오 유니버설 SDK의 PHP 구현입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt">firebase/php-jwt</a>
    </td>
    <td>라이브러리</td>
    <td>PHP에서 JSON 웹 토큰(JWT)을 인코딩하고 디코딩하는 간단한 라이브러리입니다. 현재 사양을 준수해야 합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha">laminas/laminas-captcha</a>
    </td>
    <td>라이브러리</td>
    <td>Figlet, 이미지, ReCaptcha 등을 사용하여 CAPTCHA를 생성하고 확인합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code">laminas/laminas-code</a>
    </td>
    <td>라이브러리</td>
    <td>PHP Reflection API, 정적 코드 스캔 및 코드 생성에 대한 확장</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config">laminas/laminas-config</a>
    </td>
    <td>라이브러리</td>
    <td>는 응용 프로그램 코드 내에서 이 구성 데이터에 액세스하기 위한 중첩된 개체 속성 기반 사용자 인터페이스를 제공합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di">laminas/laminas-di</a>
    </td>
    <td>라이브러리</td>
    <td>PSR-11 컨테이너에 대한 자동 종속성 삽입</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper">laminas/laminas-escaper</a>
    </td>
    <td>라이브러리</td>
    <td>HTML, HTML 속성, JavaScript, CSS 및 URL을 안전하고 안전하게 이스케이프 처리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager">laminas/laminas-eventmanager</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 응용 프로그램 내에서 이벤트를 트리거하고 수신</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed">라미나/라미나 피드</a>
    </td>
    <td>라이브러리</td>
    <td>에서는 RSS 및 Atom 피드를 만들고 소비하는 기능을 제공합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter">laminas/laminas-filter</a>
    </td>
    <td>라이브러리</td>
    <td>프로그래밍 방식으로 데이터 및 파일 필터링 및 정규화</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http">laminas/laminas-http</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP(Hyper-Text Transfer Protocol) 요청을 수행할 수 있는 간편한 인터페이스 제공</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n">laminas/laminas-i18n</a>
    </td>
    <td>라이브러리</td>
    <td>애플리케이션에 대한 번역을 제공하고 국제화된 값을 필터링하고 검증합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json">laminas/laminas-json</a>
    </td>
    <td>라이브러리</td>
    <td>는 기본 PHP를 JSON으로 serialize하고 JSON을 기본 PHP로 decoding하는 편리한 방법을 제공합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader">laminas/laminas-loader</a>
    </td>
    <td>라이브러리</td>
    <td>자동 로드 및 플러그인 로드 전략</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager">laminas/laminas-modulemanager</a>
    </td>
    <td>라이브러리</td>
    <td>Laminas-mvc 응용 프로그램용 모듈식 응용 시스템</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc">laminas/laminas-mvc</a>
    </td>
    <td>라이브러리</td>
    <td>MVC 응용 프로그램, 컨트롤러 및 플러그인을 포함한 Laminas의 이벤트 기반 MVC 계층</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl">laminas/laminas-permissions-acl</a>
    </td>
    <td>라이브러리</td>
    <td>권한 관리를 위한 가볍고 유연한 ACL(액세스 제어 목록) 구현 제공</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha">laminas/laminas-recaptcha</a>
    </td>
    <td>라이브러리</td>
    <td>ReCaptcha 웹 서비스에 대한 OOP 래퍼</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router">laminas/laminas-router</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP 및 콘솔 애플리케이션을 위한 유연한 라우팅 시스템</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server">laminas/laminas-server</a>
    </td>
    <td>라이브러리</td>
    <td>리플렉션 기반 RPC 서버 만들기</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager">laminas/laminas-servicemanager</a>
    </td>
    <td>라이브러리</td>
    <td>공장 구동 의존 주입 용기</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session">laminas/laminas-session</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 세션 및 스토리지에 대한 객체 지향 인터페이스</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap">laminas/laminas-soap</a>
    </td>
    <td>라이브러리</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib">laminas/laminas-stdlib</a>
    </td>
    <td>라이브러리</td>
    <td>SPL 확장, 배열 유틸리티, 오류 처리기 등</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text">laminas/laminas-text</a>
    </td>
    <td>라이브러리</td>
    <td>FIGlets 및 텍스트 기반 표 만들기</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator">laminas/laminas-translator</a>
    </td>
    <td>라이브러리</td>
    <td>Laminas-i18n의 Translator 구성 요소용 인터페이스</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri">laminas/laminas-uri</a>
    </td>
    <td>라이브러리</td>
    <td>"URI(Uniform Resource Identifier)"를 조작하고 확인하는 데 도움이 되는 구성 요소</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator">laminas/laminas-validator</a>
    </td>
    <td>라이브러리</td>
    <td>다양한 도메인에 대한 유효성 검사 클래스 및 복잡한 유효성 검사 기준을 만들기 위한 유효성 검사기 체인 기능</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view">laminas/laminas-view</a>
    </td>
    <td>라이브러리</td>
    <td>여러 보기 레이어, 도우미 등을 지원하고 제공하는 유연한 보기 레이어</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum">marc-mabe/php-enum</a>
    </td>
    <td>라이브러리</td>
    <td>기본 PHP를 사용한 열거형의 간단하고 빠른 구현</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser">nikic/php-parser</a>
    </td>
    <td>라이브러리</td>
    <td>PHP로 작성된 PHP 파서</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha">phpfui/recaptcha</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 8.4 이상용 Google의 reCAPTCHA용 클라이언트 라이브러리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink">tedivm/jshrink</a>
    </td>
    <td>라이브러리</td>
    <td>PHP에 내장된 Javascript 축소기</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port">tubalmartin/cssmin</a>
    </td>
    <td>라이브러리</td>
    <td>YUI CSS 압축기의 PHP 포트</td>
  </tr>
  </tbody>
</table>

### BSD-3-조항-수정

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>Magento 모듈</td>
    <td>태그에 대한 모든 지원을 제공하는 Redis를 사용하는 Zend_Cache 백엔드.</td>
  </tr>
  </tbody>
</table>

### ISC

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/paragonie/sodium_compat">파라고니/나트륨_호환</a>
    </td>
    <td>라이브러리</td>
    <td>libsodium의 순수 PHP 구현; 존재하는 경우 PHP 확장을 사용합니다.</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1 이상

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/ezyang/htmlpurifier">ezyang/htmlclearer</a>
    </td>
    <td>라이브러리</td>
    <td>PHP로 작성된 표준 준수 HTML 필터</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib">php-amqplib/php-amqplib</a>
    </td>
    <td>라이브러리</td>
    <td>이전 videalvaro/php-amqplib.  이 라이브러리는 AMQP 프로토콜의 순수한 PHP 구현입니다. RabbitMQ에 대해 테스트되었습니다.</td>
  </tr>
  </tbody>
</table>

### MIT

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/braintree/braintree_php">braintree/braintree_php</a>
    </td>
    <td>라이브러리</td>
    <td>Braintree PHP 클라이언트 라이브러리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math">brick/math</a>
    </td>
    <td>라이브러리</td>
    <td>임의 정밀도 산술 라이브러리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter">brick/varexporter</a>
    </td>
    <td>라이브러리</td>
    <td>var_export()에 대한 강력한 대체 요소로, __set_state() 없이 닫기와 객체를 내보낼 수 있습니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32">christian-riesen/base32</a>
    </td>
    <td>라이브러리</td>
    <td>RFC 4648에 따른 Base32 인코더/디코더</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis">colinmollenhour/credis</a>
    </td>
    <td>라이브러리</td>
    <td>Credis는 성능 향상을 위해 사용 가능한 경우 Phpredis 라이브러리를 래핑하는 Redis 키-값 저장소에 대한 간단한 인터페이스입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle">composer/ca-bundle</a>
    </td>
    <td>라이브러리</td>
    <td>시스템 CA 번들에 대한 경로를 찾을 수 있도록 하고, Mozilla CA 번들에 대한 대체를 포함합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator">composer/class-map-generator</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 코드를 스캔하고 클래스 맵을 생성하는 유틸리티입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer">작성기/작성기</a>
    </td>
    <td>라이브러리</td>
    <td>Composer를 사용하면 PHP 프로젝트의 종속성을 선언하고, 관리하고, 설치할 수 있습니다. 어디에나 올바른 스택을 유지할 수 있습니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier">작성기/메타데이터 축소기</a>
    </td>
    <td>라이브러리</td>
    <td>메타데이터 축소 및 확장을 처리하는 작은 유틸리티 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre">작성기/pcre</a>
    </td>
    <td>라이브러리</td>
    <td>PCRE 래핑 라이브러리로, 유형에 맞는 프레그_* 대체 기능을 제공합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver">작성기/semver</a>
    </td>
    <td>라이브러리</td>
    <td>유틸리티, 버전 제약 조건 구문 분석 및 유효성 검사를 제공하는 Semver 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses">작성기/spdx 라이선스</a>
    </td>
    <td>라이브러리</td>
    <td>SPDX 라이선스 목록 및 유효성 검사 라이브러리.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler">작성기/xdebug-handler</a>
    </td>
    <td>라이브러리</td>
    <td>Xdebug 없이 프로세스를 다시 시작합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer">doctrine/lexer</a>
    </td>
    <td>라이브러리</td>
    <td>하향식 재귀 하강 파서에서 사용할 수 있는 PHP Doctrine 렉서 라이브러리.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator">egulias/email-validator</a>
    </td>
    <td>라이브러리</td>
    <td>여러 RFC에 대한 이메일 유효성 검사를 위한 라이브러리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php">탄력적/전송</a>
    </td>
    <td>라이브러리</td>
    <td>Elastic 제품용 HTTP 전송 PHP 라이브러리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php">elasticsearch/elasticsearch</a>
    </td>
    <td>라이브러리</td>
    <td>Elasticsearch용 PHP 클라이언트</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code">endroid/qr-code</a>
    </td>
    <td>라이브러리</td>
    <td>엔드로이드 QR 코드</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams">ezimuel/guzzlestreams</a>
    </td>
    <td>라이브러리</td>
    <td>elasticsearch-php와 함께 사용할 구글/스트림 (중단됨)의 포크</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp">ezimuel/ringphp</a>
    </td>
    <td>라이브러리</td>
    <td>Elasticsearch-php와 함께 사용할 Guzzle/RingPHP (포크)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle">guzzlehttp/guzzle</a>
    </td>
    <td>라이브러리</td>
    <td>Guzzle은 PHP HTTP 클라이언트 라이브러리입니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises">guzzlehttp/promises</a>
    </td>
    <td>라이브러리</td>
    <td>Guzzle 약속 라이브러리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7">guzzlehttp/psr7</a>
    </td>
    <td>라이브러리</td>
    <td>일반적인 유틸리티 메서드를 제공하는 PSR-7 메시지 구현</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema">justinrainbow/json-schema</a>
    </td>
    <td>라이브러리</td>
    <td>JSON 스키마의 유효성을 검사하는 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem">league/flysystem</a>
    </td>
    <td>라이브러리</td>
    <td>PHP용 파일 스토리지 추상화</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3">league/flysystem-aws-s3-v3</a>
    </td>
    <td>라이브러리</td>
    <td>Flysystem용 AWS S3 파일 시스템 어댑터</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local">league/flysystem-local</a>
    </td>
    <td>라이브러리</td>
    <td>Flysystem용 로컬 파일 시스템 어댑터.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection">league/mime-type-detection</a>
    </td>
    <td>라이브러리</td>
    <td>Flysystem에 대한 MIME 유형 감지</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog">모노로그/모노로그</a>
    </td>
    <td>라이브러리</td>
    <td>파일, 소켓, 받은 편지함, 데이터베이스 및 다양한 웹 서비스에 로그를 보냅니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php">mtdowling/jmespath.php</a>
    </td>
    <td>라이브러리</td>
    <td>JSON 문서에서 요소를 추출하는 방법을 선언적으로 지정</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding">paragonie/constant_time_encoding</a>
    </td>
    <td>라이브러리</td>
    <td>RFC 4648 인코딩의 일정 시간 구현(Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat">paragonie/random_compat</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 7의 random_bytes() 및 random_int()에 대한 PHP 5.x polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier">pelago/emogrifier</a>
    </td>
    <td>라이브러리</td>
    <td>CSS 스타일을 HTML 코드의 인라인 스타일 속성으로 변환합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery">php-http/discovery</a>
    </td>
    <td>Composer-plug</td>
    <td>PSR-7, PSR-17, PSR-18 및 HTTPlug 구현을 찾아서 설치합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug">php-http/httplug</a>
    </td>
    <td>라이브러리</td>
    <td>HTTPlug, PHP용 HTTP 클라이언트 추상화</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise">php-http/promise</a>
    </td>
    <td>라이브러리</td>
    <td>비동기 HTTP 요청에 사용된 Promise</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath">phpgt/cssxpath</a>
    </td>
    <td>라이브러리</td>
    <td>CSS 선택기를 XPath 쿼리로 변환합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom">phpgt/dom</a>
    </td>
    <td>라이브러리</td>
    <td>최신 DOM API.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc">phpgt/propfunc</a>
    </td>
    <td>라이브러리</td>
    <td>속성 접근자 및 변경자 함수.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat">phpseclib/mcrypt_compat</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 5.x-8.x polyfill for mcrypt extension</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib">phpseclib/phpseclib</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 보안 통신 라이브러리 - RSA, AES, SSH2, SFTP, X.509 등의 순수 PHP 구현.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache">psr/cache</a>
    </td>
    <td>라이브러리</td>
    <td>라이브러리 캐싱을 위한 공통 인터페이스</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock">psr/clock</a>
    </td>
    <td>라이브러리</td>
    <td>시계를 읽기 위한 공통 인터페이스.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container">psr/container</a>
    </td>
    <td>라이브러리</td>
    <td>공통 컨테이너 인터페이스 (PHP 그림 PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher">psr/event-dispatcher</a>
    </td>
    <td>라이브러리</td>
    <td>이벤트 처리를 위한 표준 인터페이스입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client">psr/http-client</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP 클라이언트용 공통 인터페이스</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory">psr/http-factory</a>
    </td>
    <td>라이브러리</td>
    <td>PSR-17: PSR-7 HTTP 메시지 팩토리에 대한 일반 인터페이스</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message">psr/http-message</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP 메시지에 대한 일반 인터페이스</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log">psr/log</a>
    </td>
    <td>라이브러리</td>
    <td>라이브러리 로깅을 위한 공통 인터페이스</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders">롤루피/getallheaders</a>
    </td>
    <td>라이브러리</td>
    <td>getallheaders에 대한 폴리필.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection">ramsey/collection</a>
    </td>
    <td>라이브러리</td>
    <td>컬렉션을 나타내고 조작하기 위한 PHP 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid">ramsey/uuid</a>
    </td>
    <td>라이브러리</td>
    <td>UUID(범용 고유 식별자)를 생성하고 사용하기 위한 PHP 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise">반응/약속</a>
    </td>
    <td>라이브러리</td>
    <td>PHP용 CommonJS Promises/A의 간단한 구현</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser">sabberworm/php-css-parser</a>
    </td>
    <td>라이브러리</td>
    <td>PHP로 작성된 CSS 파일용 파서</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint">seld/jsonlint</a>
    </td>
    <td>라이브러리</td>
    <td>JSON 린터</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils">seld/phar-utils</a>
    </td>
    <td>라이브러리</td>
    <td>PHAR 파일 형식 유틸리티, PHP가 당신을 호출 할 때</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler">seld/signal-handler</a>
    </td>
    <td>라이브러리</td>
    <td>쉬운 교차 플랫폼 개발을 위해 신호가 지원되지 않는 곳에서 자동으로 실패하는 간단한 unix 신호 처리기</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap">spomky-labs/aes-key-wrap</a>
    </td>
    <td>라이브러리</td>
    <td>PHP용 AES Key Wrap.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp">spomky-labs/otphp</a>
    </td>
    <td>라이브러리</td>
    <td>RFC 4226(HOTP 알고리즘) 및 RFC 6238(TOTP 알고리즘)에 따라 1회 암호를 생성하고 Google Authenticator와 호환되는 PHP 라이브러리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework">spomky-labs/pki-framework</a>
    </td>
    <td>라이브러리</td>
    <td>공개 키 인프라 관리를 위한 PHP 프레임워크입니다. X.509 공개 키 인증서, 속성 인증서, 인증 요청 및 인증 경로 유효성 검사로 구성됩니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config">symfony/config</a>
    </td>
    <td>라이브러리</td>
    <td>모든 종류의 구성 값을 찾고, 로드하고, 결합하고, 자동으로 채우고, 유효성을 검사하는 데 도움이 됩니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console">심포니/콘솔</a>
    </td>
    <td>라이브러리</td>
    <td>아름답고 테스트 가능한 명령줄 인터페이스 생성 용이</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector">symfony/css-selector</a>
    </td>
    <td>라이브러리</td>
    <td>CSS 선택기를 XPath 표현식으로 변환</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection">symfony/dependency-injection</a>
    </td>
    <td>라이브러리</td>
    <td>애플리케이션에서 객체가 구성되는 방식을 표준화하고 중앙 집중화할 수 있습니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts">교감/사용 중단 계약</a>
    </td>
    <td>라이브러리</td>
    <td>사용 중단 알림을 트리거하는 일반 함수 및 규칙</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler">symfony/error-handler</a>
    </td>
    <td>라이브러리</td>
    <td>오류를 관리하고 PHP 코드를 쉽게 디버깅할 수 있는 도구를 제공합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher">symfony/event-dispatcher</a>
    </td>
    <td>라이브러리</td>
    <td>이벤트를 발송하고 이벤트를 수신하여 애플리케이션 구성 요소 간에 통신할 수 있는 도구를 제공합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts">symfony/event-dispatcher-contracts</a>
    </td>
    <td>라이브러리</td>
    <td>이벤트 발송과 관련된 일반 요약</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem">symfony/filesystem</a>
    </td>
    <td>라이브러리</td>
    <td>파일 시스템의 기본 유틸리티 제공</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder">symfony/finder</a>
    </td>
    <td>라이브러리</td>
    <td>직관적인 유창한 인터페이스를 통해 파일 및 디렉터리 찾기</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client">symfony/http-client</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP 리소스를 동기식으로 또는 비동기식으로 가져오는 강력한 방법 제공</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts">symfony/http-client-contracts</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP 클라이언트와 관련된 일반 추상화</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation">symfony/http-foundation</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP 사양에 대한 개체 지향 레이어를 정의합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel">symfony/http-kernel</a>
    </td>
    <td>라이브러리</td>
    <td>요청을 응답으로 변환하는 구조화된 프로세스를 제공합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl">symfony/intl</a>
    </td>
    <td>라이브러리</td>
    <td>ICU 라이브러리의 로컬라이제이션 데이터에 대한 액세스를 제공합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer">심포니/메일 받는 사람</a>
    </td>
    <td>라이브러리</td>
    <td>이메일 전송 지원</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime">symfony/mime</a>
    </td>
    <td>라이브러리</td>
    <td>MIME 메시지 조작 허용</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype">symfony/polyfill-ctype</a>
    </td>
    <td>라이브러리</td>
    <td>ctype 함수에 대한 교감 폴리필</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme">교감/폴리필-국제-자소</a>
    </td>
    <td>라이브러리</td>
    <td>국제 자소_* 함수에 대한 교감 폴리필</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn">symfony/polyfill-intl-idn</a>
    </td>
    <td>라이브러리</td>
    <td>국제 전화 번호 idn_to_ascii 및 idn_to_utf8 함수에 대한 동종 폴리필</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer">교감/폴리필-intl-normalizer</a>
    </td>
    <td>라이브러리</td>
    <td>국제 표준화 클래스 및 관련 함수에 대한 Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring">symfony/polyfill-mbstring</a>
    </td>
    <td>라이브러리</td>
    <td>Mbstring 확장에 대한 Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73">symfony/polyfill-php73</a>
    </td>
    <td>라이브러리</td>
    <td>일부 PHP 7.3+ 기능을 더 낮은 PHP 버전으로 지원하는 Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80">symfony/polyfill-php80</a>
    </td>
    <td>라이브러리</td>
    <td>일부 PHP 8.0+ 기능을 더 낮은 PHP 버전으로 지원하는 Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81">symfony/polyfill-php81</a>
    </td>
    <td>라이브러리</td>
    <td>일부 PHP 8.1+ 기능을 더 낮은 PHP 버전으로 지원하는 Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82">symfony/polyfill-php82</a>
    </td>
    <td>라이브러리</td>
    <td>일부 PHP 8.2+ 기능을 더 낮은 PHP 버전으로 지원하는 Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83">symfony/polyfill-php83</a>
    </td>
    <td>라이브러리</td>
    <td>일부 PHP 8.3+ 기능을 더 낮은 PHP 버전으로 지원하는 Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process">심포니/프로세스</a>
    </td>
    <td>라이브러리</td>
    <td>하위 프로세스에서 명령 실행</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts">심포니/서비스 계약</a>
    </td>
    <td>라이브러리</td>
    <td>쓰기 서비스와 관련된 일반적인 추상화</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string">symfony/string</a>
    </td>
    <td>라이브러리</td>
    <td>문자열에 개체 지향 API를 제공하고 바이트, UTF-8 코드 포인트 및 자소 클러스터를 통합 방식으로 처리합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper">symfony/var-dumper</a>
    </td>
    <td>라이브러리</td>
    <td>임의의 PHP 변수를 통과하기 위한 메커니즘을 제공합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter">symfony/var-exporter</a>
    </td>
    <td>라이브러리</td>
    <td>직렬화할 수 있는 PHP 데이터 구조를 일반 PHP 코드로 내보낼 수 있습니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml">symfony/yaml</a>
    </td>
    <td>라이브러리</td>
    <td>YAML 파일을 로드하고 덤프합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework">웹 토큰/jwt 프레임워크</a>
    </td>
    <td>교향다발</td>
    <td>PHP 및 Symfony 번들을 위한 JSON 개체 서명 및 암호화 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php">webonyx/graphql-php</a>
    </td>
    <td>라이브러리</td>
    <td>GraphQL 참조 구현의 PHP 포트</td>
  </tr>
  </tbody>
</table>

### OSL-3.0, AFL-3.0

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-customer-balance
    </td>
    <td>Magento2-모듈</td>
    <td>해당 사항 없음</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card
    </td>
    <td>Magento2-모듈</td>
    <td>해당 사항 없음</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card-account
    </td>
    <td>Magento2-모듈</td>
    <td>해당 사항 없음</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
    </td>
    <td>Magento2-모듈</td>
    <td>해당 사항 없음</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>Magento2-모듈</td>
    <td>해당 사항 없음</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-reward
    </td>
    <td>Magento2-모듈</td>
    <td>해당 사항 없음</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### PHP

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode">2tvenom/cborencode</a>
    </td>
    <td>라이브러리</td>
    <td>PHP용 CBOR 인코더</td>
  </tr>
  </tbody>
</table>

### 소유

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-core
    </td>
    <td>Magento2-모듈</td>
    <td>Gene Commerce for PayPal의 Magento Braintree 2.2.0 모듈 포크.</td>
  </tr>
  </tbody>
</table>
