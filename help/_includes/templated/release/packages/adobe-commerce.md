---
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '2192'
ht-degree: 0%

---
# Adobe Commerce 패키지

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce` value from the _data/names.yml file
 -->

Adobe Commerce은 작성기를 사용하여 PHP 패키지를 관리합니다.

다음 `composer.json` 파일은 패키지 목록을 선언하지만, `composer.lock` 파일에는 Adobe Commerce 또는 Magento Open Source 설치를 빌드하는 데 사용되는 패키지의 전체 목록(각 패키지의 전체 버전 및 해당 종속성)이 저장됩니다.

다음 참조 설명서는 `composer.lock` 파일 및 Adobe Commerce 2.4.5에 포함된 필수 패키지를 다룹니다.

## 종속성

`magento/product-enterprise-edition 2.4.5` 에는 다음과 같은 종속성이 있습니다.

```config
colinmollenhour/cache-backend-file: ~1.4.1
colinmollenhour/cache-backend-redis: 1.14.2
colinmollenhour/credis: 1.13.0
colinmollenhour/php-redis-session-abstract: ~1.4.5
composer/composer: ^1.9 || ^2.0, !=2.2.16
elasticsearch/elasticsearch: ~7.17.0
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
ext-gd: *
ext-hash: *
ext-iconv: *
ext-intl: *
ext-mbstring: *
ext-openssl: *
ext-pdo_mysql: *
ext-simplexml: *
ext-soap: *
ext-sodium: *
ext-spl: *
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.14
guzzlehttp/guzzle: ^7.4.2
laminas/laminas-captcha: ^2.12
laminas/laminas-code: ~4.5.0
laminas/laminas-db: ^2.15.0
laminas/laminas-dependency-plugin: ^2.2.0
laminas/laminas-di: ^3.7.0
laminas/laminas-escaper: ~2.10.0
laminas/laminas-eventmanager: ^3.5.0
laminas/laminas-feed: ^2.17.0
laminas/laminas-http: ^2.15.0
laminas/laminas-json: ^3.3.0
laminas/laminas-mail: ^2.16.0
laminas/laminas-mime: ^2.9.1
laminas/laminas-modulemanager: ^2.11.0
laminas/laminas-mvc: ^3.3.3
laminas/laminas-server: ^2.11.1
laminas/laminas-servicemanager: ^3.11.0
laminas/laminas-soap: ^2.10.0
laminas/laminas-stdlib: ^3.7.1
laminas/laminas-uri: ^2.9.1
laminas/laminas-validator: ^2.17.0
league/flysystem: ~2.4.5
league/flysystem-aws-s3-v3: ^2.4.3
lib-libxml: *
magento/composer: ~1.8.0
magento/composer-dependency-version-audit-plugin: ~0.1
magento/framework-foreign-key: 100.4.4
magento/magento-composer-installer: >=0.3.0
magento/magento2-ee-base: 2.4.5
magento/module-admin-gws: 100.4.5
magento/module-admin-gws-configurable-product: 100.4.2
magento/module-admin-gws-staging: 100.4.2
magento/module-advanced-catalog: 100.4.2
magento/module-advanced-checkout: 100.4.5
magento/module-advanced-rule: 100.4.2
magento/module-advanced-sales-rule: 100.4.2
magento/module-async-order: 100.4.1
magento/module-async-order-graph-ql: 100.4.0
magento/module-aws-s3-customer-custom-attributes: 100.4.2
magento/module-aws-s3-gift-card-import-export: 100.4.2
magento/module-aws-s3-scheduled-import-export: 100.4.2
magento/module-banner: 101.2.5
magento/module-banner-customer-segment: 100.4.3
magento/module-banner-graph-ql: 100.4.1
magento/module-bundle-import-export-staging: 100.4.2
magento/module-bundle-staging: 100.4.5
magento/module-catalog-event: 101.1.4
magento/module-catalog-import-export-staging: 100.4.2
magento/module-catalog-inventory-staging: 100.4.3
magento/module-catalog-permissions: 100.4.5
magento/module-catalog-permissions-graph-ql: 100.4.3
magento/module-catalog-rule-staging: 100.4.5
magento/module-catalog-staging: 100.4.5
magento/module-catalog-staging-graph-ql: 100.4.4
magento/module-catalog-url-rewrite-staging: 100.4.4
magento/module-checkout-address-search: 100.4.4
magento/module-checkout-address-search-gift-registry: 100.4.1
magento/module-checkout-staging: 100.4.4
magento/module-cms-staging: 100.4.5
magento/module-configurable-product-staging: 100.4.4
magento/module-custom-attribute-management: 100.4.4
magento/module-customer-balance: 100.4.5
magento/module-customer-balance-graph-ql: 100.4.2
magento/module-customer-custom-attributes: 100.4.5
magento/module-customer-finance: 100.4.2
magento/module-customer-segment: 102.1.5
magento/module-deferred-total-calculating: 100.4.0
magento/module-downloadable-staging: 100.4.4
magento/module-elasticsearch-catalog-permissions: 100.4.1
magento/module-elasticsearch-catalog-permissions-graph-ql: 100.4.0
magento/module-enterprise: 100.4.3
magento/module-gift-card: 101.3.5
magento/module-gift-card-account: 101.2.5
magento/module-gift-card-account-graph-ql: 100.4.3
magento/module-gift-card-graph-ql: 100.4.5
magento/module-gift-card-import-export: 100.4.2
magento/module-gift-card-staging: 100.4.2
magento/module-gift-message-staging: 100.4.2
magento/module-gift-registry: 101.2.5
magento/module-gift-registry-graph-ql: 100.4.1
magento/module-gift-wrapping: 101.2.4
magento/module-gift-wrapping-graph-ql: 100.4.2
magento/module-gift-wrapping-staging: 100.4.2
magento/module-google-optimizer-staging: 100.4.2
magento/module-google-tag-manager: 100.4.5
magento/module-grouped-product-staging: 100.4.3
magento/module-invitation: 100.4.4
magento/module-layered-navigation-staging: 100.4.2
magento/module-logging: 101.2.5
magento/module-login-as-customer-logging: 100.4.5
magento/module-login-as-customer-website-restriction: 100.4.3
magento/module-media-content-catalog-staging: 100.4.2
magento/module-msrp-staging: 100.4.3
magento/module-multiple-wishlist: 100.4.5
magento/module-multiple-wishlist-graph-ql: 100.4.1
magento/module-payment-staging: 100.4.2
magento/module-persistent-history: 100.4.2
magento/module-price-permissions: 100.4.1
magento/module-product-video-staging: 100.4.2
magento/module-promotion-permissions: 100.4.2
magento/module-quote-gift-card-options: 100.4.2
magento/module-quote-staging: 100.4.2
magento/module-reminder: 101.2.4
magento/module-remote-storage-commerce: 100.4.1
magento/module-resource-connections: 100.4.2
magento/module-review-staging: 100.4.2
magento/module-reward: 101.2.5
magento/module-reward-graph-ql: 100.4.4
magento/module-reward-staging: 100.4.2
magento/module-rma: 101.2.5
magento/module-rma-graph-ql: 100.4.4
magento/module-rma-staging: 100.4.2
magento/module-sales-archive: 101.0.3
magento/module-sales-rule-staging: 100.4.4
magento/module-scalable-checkout: 100.4.4
magento/module-scalable-inventory: 100.4.3
magento/module-scalable-oms: 100.4.3
magento/module-scheduled-import-export: 101.2.5
magento/module-search-staging: 100.4.3
magento/module-staging: 101.2.5
magento/module-staging-graph-ql: 100.4.2
magento/module-support: 101.2.4
magento/module-swat: 100.4.3
magento/module-target-rule: 101.2.5
magento/module-target-rule-graph-ql: 100.4.2
magento/module-versions-cms: 101.2.5
magento/module-versions-cms-page-cache: 100.4.1
magento/module-versions-cms-url-rewrite: 100.4.3
magento/module-versions-cms-url-rewrite-graph-ql: 100.4.1
magento/module-visual-merchandiser: 100.4.5
magento/module-website-restriction: 100.4.4
magento/module-weee-staging: 100.4.2
magento/module-wishlist-gift-card: 100.4.1
magento/module-wishlist-gift-card-graph-ql: 100.4.1
magento/page-builder-commerce: 1.7.2
magento/product-community-edition: 2.4.5
magento/security-package-ee: 1.0.0
magento/theme-adminhtml-spectrum: 100.4.0
magento/zendframework1: ~1.15.0
monolog/monolog: ^2.7
pelago/emogrifier: ^6.0.0
php: ~7.4.0||~8.1.0
php-amqplib/php-amqplib: ~3.2.0
phpseclib/mcrypt_compat: ~2.0.2
phpseclib/phpseclib: ~3.0.13
ramsey/uuid: ~4.2.0
symfony/console: ~4.4.0
symfony/process: ~4.4.0
tedivm/jshrink: ~1.4.0
tubalmartin/cssmin: 4.1.1
web-token/jwt-framework: ^v2.2.7
webonyx/graphql-php: ~14.11.6
wikimedia/less.php: ^3.0.0
```

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
      <a href="https://github.com/elastic/elasticsearch-php.git">elasticsearch/elasticsearch</a>
    </td>
    <td>라이브러리</td>
    <td>Elasticsearch용 PHP 클라이언트</td>
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
      <a href="https://github.com/adobe/stock-api-libphp.git">astock/stock-api-libphp</a>
    </td>
    <td>라이브러리</td>
    <td>Adobe Stock API 라이브러리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>라이브러리</td>
    <td>PHP용 AWS 공용 런타임</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>라이브러리</td>
    <td>PHP용 AWS SDK - PHP 프로젝트에서 Amazon Web Services 사용</td>
  </tr>
  <tr>
    <td>
      paypal/module braintree
    </td>
    <td>메타카지</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>라이브러리</td>
    <td>LESS Javascript 버전의 PHP 포트 http://lesscss.org (원래 Josh 슈미트에 의해 유지 관리됨)</td>
  </tr>
  </tbody>
</table>

### BSD-2-절

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
      <a href="https://github.com/Bacon/BaconQrCode.git">베이컨/베이컨-qr 코드</a>
    </td>
    <td>라이브러리</td>
    <td>BaconQrCode는 PHP용 QR 코드 생성기입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/beberlei/assert.git">베를레이/주장</a>
    </td>
    <td>라이브러리</td>
    <td>비즈니스 모델의 입력 유효성 검사를 위한 씬 검증 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprime/enum</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 7.1 열거형 구현</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpact/safe-writer</a>
    </td>
    <td>라이브러리</td>
    <td>경합 조건을 방지하기 위해 파일을 안전하게 작성하는 도구</td>
  </tr>
  </tbody>
</table>

### BSD-3-절

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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinmollenhour/cache-backend-file</a>
    </td>
    <td>magento module</td>
    <td>스톡 Zend_Cache_Backend_File 백엔드는 캐시된 항목 수가 증가함에 따라 태그를 사용하여 클리닝하는 성능이 매우 낮습니다. 이 백엔드는 많은 변경 사항을 수행하므로 특히 태그 클리닝에 대한 성능이 크게 향상됩니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>magento module</td>
    <td>태그를 완벽하게 지원하는 Redis를 사용하는 Zend_Cache 백엔드.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">collinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>라이브러리</td>
    <td>낙관적 잠금이 있는 Redis 기반 세션 핸들러</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>라이브러리</td>
    <td>웹 사이트를 스팸 및 악용으로부터 보호하는 무료 서비스인 reCAPTCHA용 클라이언트 라이브러리.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">라미나스/라미나스-캡차</a>
    </td>
    <td>라이브러리</td>
    <td>Figlet, 이미지, ReCaptcha 등을 사용하여 CAPTCHA를 생성하고 유효성을 검사합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">라미나스/라미나스 코드</a>
    </td>
    <td>라이브러리</td>
    <td>PHP Reflection API에 대한 확장, 정적 코드 스캔 및 코드 생성</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>라이브러리</td>
    <td>에서는 애플리케이션 코드 내에서 이 구성 데이터에 액세스할 수 있는 중첩 개체 속성 기반 사용자 인터페이스를 제공합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>라이브러리</td>
    <td>데이터베이스 추상화 계층, SQL 추상화, 결과 집합 추상화, RowDataGateway 및 TableDataGateway 구현</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-dependency-plugin.git">laminas/laminas-dependency-plugin</a>
    </td>
    <td>composer-plugin</td>
    <td>Zendframework 및 zfcampaign 패키지를 해당 Laminas Project에 상응하는 것으로 바꿉니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">라미나스/라미나스 디</a>
    </td>
    <td>라이브러리</td>
    <td>PSR-11 컨테이너에 대한 자동 종속성 주입</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">라미나나스/라미나스 이스케이프 처리자</a>
    </td>
    <td>라이브러리</td>
    <td>HTML, HTML 특성, JavaScript, CSS 및 URL을 안전하고 안전하게 이스케이프 처리합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">라미나스/라미나스-eventmanager</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 응용 프로그램 내에서 이벤트를 트리거하고 수신 대기합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">라미나스/라미나스 피드</a>
    </td>
    <td>라이브러리</td>
    <td>에서는 RSS 및 Atom 피드를 만들고 사용하는 기능을 제공합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP(Hyper-Text Transfer Protocol) 요청을 수행하기 위한 쉬운 인터페이스를 제공합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas/json</a>
    </td>
    <td>라이브러리</td>
    <td>에서는 기본 PHP를 JSON에 직렬화하고 JSON을 기본 PHP에 디코딩하는 편리한 방법을 제공합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">라미나스/라미나스 로더</a>
    </td>
    <td>라이브러리</td>
    <td>자동 로드 및 플러그인 로드 전략</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">라미나스/라미나스 메일</a>
    </td>
    <td>라이브러리</td>
    <td>텍스트 및 MIME 규격 다중 파트 전자 메일 메시지를 모두 작성 및 전송하는 일반화된 기능을 제공합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">라미나스/라미나스-mime</a>
    </td>
    <td>라이브러리</td>
    <td>MIME 메시지 및 부분 만들기 및 구문 분석</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">라미나스/라미나스-모듈마나거</a>
    </td>
    <td>라이브러리</td>
    <td>Laminas-mvc 애플리케이션을 위한 모듈식 애플리케이션 시스템</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">라미나스/라미나스-mvc</a>
    </td>
    <td>라이브러리</td>
    <td>MVC 애플리케이션, 컨트롤러 및 플러그인을 비롯한 Laminas의 이벤트 기반 MVC 레이어</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">라미나스/라미나스-recaptcha</a>
    </td>
    <td>라이브러리</td>
    <td>ReCaptcha 웹 서비스용 OOP 래퍼</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">라미나스/라미나스 라우터</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP 및 콘솔 애플리케이션을 위한 유연한 라우팅 시스템</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">라미나스/라미나스 서버</a>
    </td>
    <td>라이브러리</td>
    <td>반사 기반 RPC 서버 만들기</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">라미나스/라미나스 서비스 마나거</a>
    </td>
    <td>라이브러리</td>
    <td>공장 구동 종속성 주입 컨테이너</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">라미나스/라미나스 세션</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 세션 및 스토리지에 대한 객체 지향 인터페이스</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">라미나스/라미나스 비누</a>
    </td>
    <td>라이브러리</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">라미나스/라미나스-스트드립</a>
    </td>
    <td>라이브러리</td>
    <td>SPL 확장, 어레이 유틸리티, 오류 처리기 등</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">라미나스/라미나스 텍스트</a>
    </td>
    <td>라이브러리</td>
    <td>FIGlet 및 텍스트 기반 표 만들기</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">라미나스/라미나스-uri</a>
    </td>
    <td>라이브러리</td>
    <td>"URI(Uniform Resource Identifiers)" 조작 및 유효성 검사에 도움이 되는 구성 요소입니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">라미나스/라미나스 유효성 검사기</a>
    </td>
    <td>라이브러리</td>
    <td>광범위한 도메인에 대한 유효성 검사 클래스 및 유효성 검사기를 체인하여 복잡한 유효성 검사 기준을 만드는 기능</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">라미나스/라미나스 뷰</a>
    </td>
    <td>라이브러리</td>
    <td>다양한 뷰 레이어, 도움말 등을 지원하고 제공하는 유연한 뷰 레이어</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-zendframework-bridge.git">라미나스/라미나스-젠틀프레임워크 브리지</a>
    </td>
    <td>라이브러리</td>
    <td>별칭 기존 ZF 클래스 이름을 Laminas Project에 상당합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php 파서</a>
    </td>
    <td>라이브러리</td>
    <td>PHP로 작성된 PHP 파서</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshrink</a>
    </td>
    <td>라이브러리</td>
    <td>PHP로 빌드된 Javascript Minifier</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">투발마틴/cssmin</a>
    </td>
    <td>라이브러리</td>
    <td>YUI CSS 압축기의 PHP 포트</td>
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
      <a href="https://github.com/ezyang/htmlpurifier.git">에스양/html정수기</a>
    </td>
    <td>라이브러리</td>
    <td>PHP로 작성된 표준 준수 HTML 필터</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>라이브러리</td>
    <td>이전에 videlalbilla/php-amqplib입니다.  이 라이브러리는 AMQP 프로토콜의 순수 PHP 구현입니다. 그것은 시험적으로 시험되었습니다 [!DNL RabbitMQ].</td>
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
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree_php</a>
    </td>
    <td>라이브러리</td>
    <td>Braintree PHP 클라이언트 라이브러리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">벽돌/수학</a>
    </td>
    <td>라이브러리</td>
    <td>임의 정밀도 산술 라이브러리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">브릭/바레xporter</a>
    </td>
    <td>라이브러리</td>
    <td>var_export()의 강력한 대체 요소로서, __set_state() 없이 클로저와 개체를 내보낼 수 있습니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">christian-riesen/base32</a>
    </td>
    <td>라이브러리</td>
    <td>RFC 4648에 따른 Base32 인코더/디코더</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colinmollenhour/credens</a>
    </td>
    <td>라이브러리</td>
    <td>Credenis는 Redis 키-값 저장소에 대한 간단한 인터페이스로 더 나은 성능을 위해 사용할 수 있는 경우 phpredis 라이브러리를 래핑합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">composer/ca-bundle</a>
    </td>
    <td>라이브러리</td>
    <td>시스템 CA 번들에 대한 경로를 찾을 수 있도록 하며 Mozilla CA 번들에 대한 폴백이 포함되어 있습니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">작성기/작성기</a>
    </td>
    <td>라이브러리</td>
    <td>작성기는 PHP 프로젝트의 종속성을 선언, 관리 및 설치하는 데 도움이 됩니다. 그것은 당신이 어디에나 적절한 스택을 가질 수 있도록 해줍니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">composer/metadata-minifier</a>
    </td>
    <td>라이브러리</td>
    <td>메타데이터 축소 및 확장을 처리하는 작은 유틸리티 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">작성기/패키지</a>
    </td>
    <td>라이브러리</td>
    <td>유형이 안전한 preg_* 교체를 제공하는 PCRE 래핑 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">작성기/semver</a>
    </td>
    <td>라이브러리</td>
    <td>유틸리티, 버전 제한 구문 분석 및 유효성 검사를 제공하는 semver 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">작성기/spdx 라이선스</a>
    </td>
    <td>라이브러리</td>
    <td>SPDX 라이센스 목록 및 유효성 검사 라이브러리.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">composer/xdebug-handler</a>
    </td>
    <td>라이브러리</td>
    <td>Xdebug 없이 프로세스를 다시 시작합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">android/qr 코드</a>
    </td>
    <td>라이브러리</td>
    <td>Android QR 코드</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">에지무엘/구즐스트림</a>
    </td>
    <td>라이브러리</td>
    <td>elasticsearch-php에 사용할 가이즐/스트림(포기)의 포크</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">에지무엘/링php</a>
    </td>
    <td>라이브러리</td>
    <td>elasticsearch-php에 사용할 Guzle/RingPHP(포기) 포크</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/fgrosse/PHPASN1.git">fgrosse/phpasn1</a>
    </td>
    <td>라이브러리</td>
    <td>ITU-T X.690 인코딩 규칙을 사용하여 임의 ASN.1 구조를 인코딩하고 디코딩할 수 있는 PHP 프레임워크입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>라이브러리</td>
    <td>Guzzle은 PHP HTTP 클라이언트 라이브러리입니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/promises</a>
    </td>
    <td>라이브러리</td>
    <td>약속 라이브러리 추가</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>라이브러리</td>
    <td>일반적인 유틸리티 메서드도 제공하는 PSR-7 메시지 구현</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainbow/json 스키마</a>
    </td>
    <td>라이브러리</td>
    <td>json 스키마의 유효성을 검사할 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">리그/플라이시스템</a>
    </td>
    <td>라이브러리</td>
    <td>PHP용 파일 스토리지 추상화</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">league/flysystem-aws-s3-v3</a>
    </td>
    <td>라이브러리</td>
    <td>Flysystem용 AWS S3 파일 시스템 어댑터</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">league/mime 유형 탐지</a>
    </td>
    <td>라이브러리</td>
    <td>플라이시스템에 대한 MIME 유형 탐지</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">모노로그/모노로그</a>
    </td>
    <td>라이브러리</td>
    <td>파일, 소켓, 받은 편지함, 데이터베이스 및 다양한 웹 서비스에 로그를 전송합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>라이브러리</td>
    <td>JSON 문서에서 요소를 추출하는 방법을 선언적으로 지정합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragenie/constant_time_encoding</a>
    </td>
    <td>라이브러리</td>
    <td>RFC 4648 인코딩(Base-64, Base-32, Base-16)의 상시 구현</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragenie/random_compat</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 7의 random_bytes() 및 random_int()용 PHP 5.x polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">펠라고/이모화기</a>
    </td>
    <td>라이브러리</td>
    <td>CSS 스타일을 HTML 코드의 인라인 스타일 속성으로 변환합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">pgt/csxpath</a>
    </td>
    <td>라이브러리</td>
    <td>CSS 선택기를 XPath 쿼리로 변환합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>라이브러리</td>
    <td>최신 DOM API for PHP 프로젝트</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>라이브러리</td>
    <td>mcrypt 확장용 PHP 5.x-8.x polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>라이브러리</td>
    <td>PHP Secure Communications Library - RSA, AES, SSH2, SFTP, X.509 등의 순수 PHP 구현</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
    </td>
    <td>라이브러리</td>
    <td>일반 컨테이너 인터페이스(PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>라이브러리</td>
    <td>이벤트 처리를 위한 표준 인터페이스.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP 클라이언트를 위한 일반 인터페이스</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>라이브러리</td>
    <td>PSR-7 HTTP 메시지 팩토리의 공통 인터페이스</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP 메시지에 대한 일반 인터페이스</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>라이브러리</td>
    <td>라이브러리 로깅을 위한 공통 인터페이스</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>라이브러리</td>
    <td>getallheaders에 대한 다각형 채우기.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">ramsey/collection</a>
    </td>
    <td>라이브러리</td>
    <td>컬렉션을 나타내고 조작하기 위한 PHP 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>라이브러리</td>
    <td>UUID(Universally Unique Identifier)를 생성하고 사용하기 위한 PHP 라이브러리입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">반응/약속</a>
    </td>
    <td>라이브러리</td>
    <td>PHP용 CommonJS Promises/A의 간단한 구현</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/sabberworm/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>라이브러리</td>
    <td>PHP로 작성된 CSS 파일에 대한 파서</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>라이브러리</td>
    <td>JSON Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>라이브러리</td>
    <td>PHP에서 PHP로 전화할 때 PHAR 파일 형식 유틸리티</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>라이브러리</td>
    <td>PHP에 대한 AES 키 줄 바꿈.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/base64url.git">spomky-labs/base64url</a>
    </td>
    <td>라이브러리</td>
    <td>기본 64 URL 안전 인코딩/디코딩 PHP 라이브러리</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>라이브러리</td>
    <td>RFC 4226(HOTP 알고리즘) 및 RFC 6238(TOTP 알고리즘)에 따라 일회성 암호를 생성하고 Google Authenticator와 호환되는 PHP 라이브러리입니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>라이브러리</td>
    <td>모든 종류의 구성 값을 찾고, 로드하고, 결합하고, 자동으로 채우고, 확인할 수 있도록 도와줍니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>라이브러리</td>
    <td>아름답고 안정적인 명령줄 인터페이스를 쉽게 만들 수 있습니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css 선택기</a>
    </td>
    <td>라이브러리</td>
    <td>CSS 선택기를 XPath 표현식으로 변환</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/debug.git">symfony/debug</a>
    </td>
    <td>라이브러리</td>
    <td>PHP 코드 디버깅을 용이하게 하는 도구 제공</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependency-injection</a>
    </td>
    <td>라이브러리</td>
    <td>애플리케이션에서 객체가 구성되는 방식을 표준화하고 중앙 집중화할 수 있습니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symfony/deprecation-contracts</a>
    </td>
    <td>라이브러리</td>
    <td>사용 중단 알림을 트리거하는 일반 함수 및 규칙입니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>라이브러리</td>
    <td>오류를 관리하고 PHP 코드 디버깅을 용이하게 하는 도구를 제공합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>라이브러리</td>
    <td>이벤트를 발송하고 수신하여 애플리케이션 구성 요소가 서로 통신할 수 있도록 하는 도구를 제공합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher-contracts</a>
    </td>
    <td>라이브러리</td>
    <td>이벤트 발송 관련 일반 추상</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/filesystem</a>
    </td>
    <td>라이브러리</td>
    <td>파일 시스템에 대한 기본 유틸리티를 제공합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>라이브러리</td>
    <td>직관적인 유창한 인터페이스를 통해 파일 및 디렉토리 찾기</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">symfony/http-client-contracts</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP 클라이언트와 관련된 일반 추상</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http-foundation</a>
    </td>
    <td>라이브러리</td>
    <td>HTTP 사양에 대한 객체 지향 레이어를 정의합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http-kernel</a>
    </td>
    <td>라이브러리</td>
    <td>요청을 응답으로 변환하는 구조화된 프로세스를 제공합니다</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>라이브러리</td>
    <td>유형 함수를 위한 Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>라이브러리</td>
    <td>인텔 idn_to_ascii 및 idn_to_utf8 함수에 대한 Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>라이브러리</td>
    <td>인텔 Normalizer 클래스 및 관련 기능에 대한 Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>라이브러리</td>
    <td>Mbstring 확장을 위한 Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>라이브러리</td>
    <td>일부 PHP 7.2 이상의 기능을 낮은 PHP 버전으로 지원하는 Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>라이브러리</td>
    <td>일부 PHP 7.3 이상의 기능을 낮은 PHP 버전으로 지원하는 Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>라이브러리</td>
    <td>일부 PHP 8.0 이상의 기능을 낮은 PHP 버전으로 지원하는 Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>라이브러리</td>
    <td>일부 PHP 8.1 이상 기능을 낮은 PHP 버전으로 지원하는 Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symfony/process</a>
    </td>
    <td>라이브러리</td>
    <td>하위 프로세스에서 명령 실행</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/service contracts</a>
    </td>
    <td>라이브러리</td>
    <td>쓰기 서비스와 관련된 일반적인 요약</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>라이브러리</td>
    <td>임의의 PHP 변수를 통과하는 메커니즘을 제공합니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thecodingmachine/safe.git">컴퓨터/금고</a>
    </td>
    <td>라이브러리</td>
    <td>오류 시 FALSE를 반환하는 대신 예외를 throw하는 PHP 코어 함수</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony 번들</td>
    <td>PHP 및 Symfony 번들을 위한 JSON 개체 서명 및 암호화 라이브러리.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">웹 모차르트/어설션</a>
    </td>
    <td>라이브러리</td>
    <td>좋은 오류 메시지와 함께 메서드 입력/출력의 유효성을 검사하기 위한 어설션입니다.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
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
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2 모듈</td>
    <td>해당 없음</td>
  </tr>
  <tr>
    <td>
      temando/module-shipping-remover
    </td>
    <td>magento2 모듈</td>
    <td>Magento 2에서 Temando 멀티 캐리어 배송 확장 제거</td>
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
  <tr>
    <td>
      템만도/모듈 배송
    </td>
    <td>메타카지</td>
    <td>Magento 2용 Temando 멀티 캐리어 배송 확장</td>
  </tr>
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
      <a href="https://github.com/2tvenom/CBOREncode.git">2개 봉독/수기 코드</a>
    </td>
    <td>라이브러리</td>
    <td>PHP용 CBOR 인코더</td>
  </tr>
  </tbody>
</table>

### 독점

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

### 독점

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
    <td>magento2 모듈</td>
    <td>PayPal용 Gene Commerce가 Magento Braintree 2.2.0 모듈로부터 포크를 만듭니다.</td>
  </tr>
  </tbody>
</table>
