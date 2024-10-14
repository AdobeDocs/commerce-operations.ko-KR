---
source-git-commit: 00b8e1bb5ee259763ddb2c52065cee2af98641e0
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---
# 2024년 10월 Adobe Commerce 2.4.7 베타 하이라이트

## 강조 표시

이번 Adobe Commerce 릴리스에는 몇 가지 중요한 보안 수정 사항 및 플랫폼 개선 사항이 포함되어 있습니다.

### 보안

이 릴리스의 다음과 같은 보안 개선 사항은 최신 보안 모범 사례와 호환됩니다.

>[!NOTE]
>
>보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)을 참조하십시오.

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>설정</strong></td>
            <td>이번 릴리스에는 다음과 같은 보안 설정 개선 사항이 포함됩니다.
              <ul>
                <li><strong>암호화 키 순환</strong>: 이제 암호화 키를 변경하는 데 새 CLI 명령을 사용할 수 있습니다. 자세한 내용은 <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102">암호화 키 순환 문제 해결: CVE-2024-34102</a> 기술 문서를 참조하십시오.<!-- AC-12589 --></li>
                <li><strong>OTP(일회용 암호) 설정</strong>: 이 업데이트는 2.4.7에서 <a href="https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value">이전 버전과 호환되지 않는 변경</a>으로 인해 발생한 오류를 해결하는 데 필요합니다. 이제 <strong>[!UICONTROL OTP Window]</strong> 필드에 대한 설명에 설정에 대한 정확한 설명이 있으며 기본값이 <code>1</code>에서 <code>29</code>(으)로 변경되었습니다.<!-- AC-11762 --></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### 플랫폼

이 릴리스에 대한 다음의 플랫폼 업그레이드는 Adobe Commerce이 최신 상거래 환경의 요구 사항을 충족할 수 있는 강력하고 안정적인 플랫폼으로 남을 수 있도록 합니다.

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>데이터베이스</strong></td>
            <td><a href="/help/release/lifecycle-policy.md">지원 수명 주기 정책</a>에 따라 Adobe Commerce은 이제 다음 데이터베이스 기술의 LTS(장기 지원) 버전과 호환됩니다.
              <ul>
                <li><strong>MariaDB 11.4 LTS</strong> <em>_(2029년까지 지원됨)_</em>: 이전 버전(MariaDB 10.6)은 2026년에 사용이 종료되므로 시스템 무결성 및 성능을 유지하기 위해 이 업그레이드가 필수적입니다. Adobe MariaDB 10.6은 여전히 지원되지만 Adobe Commerce 2.4.8로 업그레이드할 때 MariaDB 11.4로 업그레이드하는 것이 좋습니다.</li>
                <li><strong>MySQL 8.4 LTS</strong> <em>_(2032년까지 지원됨)_</em>: 이전 버전(MySQL 8.0)은 2026년에 사용이 종료되므로 시스템 무결성 및 성능을 유지하기 위해 이 업그레이드가 필수적입니다. Adobe MySQL 8.0은 여전히 지원되지만 Adobe Commerce 2.4.8로 업그레이드할 때 MySQL 8.4로 업그레이드하는 것이 좋습니다</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>PHP</strong></td>
            <td>이 릴리스에는 다음과 같은 PHP 개선 사항이 포함됩니다.
            <ul>
              <li><strong>PHP 8.1</strong>: 이 릴리스는 Adobe Commerce 2.4.8에 대한 PHP 8.1 호환성을 제거합니다. Adobe Commerce 2.4.8로 업그레이드하기 전에 PHP 8.3으로 업그레이드해야 합니다.</li>
              <li><strong>PHP 8.2</strong>: PHP 8.2의 중요한 변경 사항 중 하나는 null을 허용하지 않는 내부 함수 매개 변수에 null을 전달하는 것을 더 이상 사용하지 않는 것입니다. 이 릴리스는 핵심 플랫폼 구성 요소에서 더 이상 사용되지 않는 PHP 8.1 기능을 다루고 PHP 8.2와의 호환성을 보장합니다.</li>
              <li><strong>PHPUnit 10</strong>: 이 릴리스는 몇 가지 중요한 문제를 해결하고 호환성을 향상시키며 Adobe Commerce 테스트 프레임워크가 최신 업계 표준에 부합하도록 합니다. Adobe은 사용자 정의가 있는 모든 Commerce Marketplace 공급업체와 고객에게 단위 및 통합 테스트가 9가 아닌 PHPUnit 10에서 실행되는지 확인하는 것을 권장합니다.</li>
            </ul>
            </td>
        </tr>
        <tr>
            <td><strong>구성 요소</strong></td>
            <td>플랫폼 안정성 및 성능을 개선하기 위해 다음 타사 <a href="/help/release/packages/adobe-commerce.md">구성 요소 및 종속성</a>이(가) 안정적인 최신 버전으로 업데이트되었습니다.
              <ul>
                <li>jquery/validate 1.20.x</li>
                <li>moment.js 2.30.1</li>
                <li>monolog/monolog 3.x</li>
                <li>monolog/Require.js 2.3.7</li>
                <li>TinyMCE 7.x</li>
                <li>wikimedia/less.php 5.x</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>검색</strong></td>
            <td>Adobe Commerce은 이제 OpenSearch 2.x에 최적화되었으며 더 이상 Elasticsearch과 호환되지 않습니다. 모든 Elasticsearch 7 및 8 모듈과 클래스는 이제 코드 베이스에서 사용되지 않습니다. Adobe은 지속적인 지원 및 호환성을 보장하기 위해 온-프레미스 및 클라우드 인프라 배포에 대해 OpenSearch로 전환할 것을 강력히 권장합니다. <a href="/help/upgrade/prepare/opensearch-migration.md">OpenSearch로 마이그레이션</a>을 참조하십시오.
              <ul>
                <li>이제 관리 구성에서 Elasticsearch 7 및 Elasticsearch 8 옵션에 "(더 이상 사용되지 않음)"이라는 레이블이 지정됩니다.</li>
                <li>사용자가 관리자 구성에서 Elasticsearch을 검색 엔진으로 선택하면 Commerce에 <em>을(를) 알리는 알림이 표시됩니다."이 검색 엔진 옵션은 더 이상 Adobe에서 지원되지 않습니다. 대신 검색 엔진으로 OpenSearch를 사용하는 것이 좋습니다."</em></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### 성능

이번 릴리스에는 다음과 같은 성능 개선 사항이 포함됩니다.

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>인덱서</strong></td>
            <td>새 버전의 Adobe Commerce을 설치하거나 이전 버전에서 업그레이드할 때 모든 인덱서의 기본 <a href="/help/implementation-playbook/best-practices/maintenance/indexer-configuration.md#set-indexers-to-update-on-schedule">인덱서 모드</a>은(는) 이제 [!UICONTROL **Update by Schedule**]입니다. 새 기본값은 인덱서가 권장 구성에 있도록 하여 시스템 성능을 향상시키고 잠재적 문제를 줄입니다.</td>
        </tr>
    </tbody>
</table>

### 품질

이번 릴리스에는 다음과 같은 품질 개선 사항이 포함됩니다.

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>인벤토리</strong></td>
           <td>이제 시스템은 InventoryIndexer에서 도입한 카탈로그에서 이전에 숨겨진 종속성을 사용하지 않고 작동하므로 제품 생성, 표시 모드 전환, 재고 상태 변경 및 기타 관련 기능이 예상대로 작동하는지 확인할 수 있습니다. 이전에는 이렇게 숨겨진 종속성이 서로 다른 엔터티가 동기화되고 인덱서가 서로 다른 엔터티를 사용함에 따라 일치하지 않는 문제가 발생했습니다.</td>
        </tr>
        <tr>
            <td><strong>주문 수</strong></td>
            <td>혼동을 최소화하기 위해 <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#notes-for-this-order">주문 세부 정보</a> 페이지에서 [!UICONTROL **Submit Comment**] 단추 레이블이 [!UICONTROL **Update**](으)로 변경되었습니다.</td>
        </tr>
    </tbody>
</table>

### GraphQL

이번 릴리스에는 다음과 같은 GraphQL 개선 사항이 포함됩니다.

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>일반 개선 사항</strong></td>
           <td>이번 릴리스에는 다음과 같은 일반적인 GraphQL API 개선 사항이 포함되어 있습니다.
             <ul>
               <li><!--LYNX-401--><strong>StoreConfig</strong>: <code>grouped_product_image</code> 및 <code>configurable_product_image</code> 필드를 <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-StoreConfig"><code>StoreConfig</code></a> 형식에 추가했습니다.</li>
              <li><!--LYNX-387--><strong>CartItemPrices</strong>: 정확한 가격 표시 및 할인 계산을 지원하기 위해 <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> 형식에 다음 새 필드를 추가했습니다.
                <ul>
                  <li><code>original_item_price</code></li>
                  <li><code>original_row_total</code></li>
                  <li><code>row_total_including_catalog_discounts_only</code></li>
                </ul>
              </li>
              <li><!--LYNX-451--><strong>CartPrices</strong>: <code>grand_total_excluding_tax</code> 필드를 <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartPrices"><code>CartPrices</code></a> 형식에 추가하여 명확한 세금 포함 가격을 제공했습니다.</li>
              <li><!--LYNX-542--><strong>updateCartItems 돌연변이</strong>: <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-updateCartItems"><code>updateCartItems</code></a> 돌연변이를 업데이트하여 예외 대신 오류 세부 정보와 함께 성공 응답을 반환했습니다. 사용자 알림의 명확성을 개선하기 위해 오류 매핑이 개선되었습니다.</li>
              <li><!--LYNX-522--><strong>recaptchaV3Config 쿼리</strong>: <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-recaptchaV3Config"><code>recaptchaV3Config</code></a> 쿼리에 <code>theme</code> 필드를 도입했습니다. 이 필드에서는 reCaptcha 렌더링에 사용할 테마의 이름을 지정할 수 있습니다.</li>
              <li><!--LYNX-540--><strong>ProductInterface</strong>: 재고 수준 세부 정보를 제공하기 위해 <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-ProductInterface"><code>ProductInterface</code></a>에 <code>quantity</code> 필드를 도입했습니다. 관리자 설정에 따라 사용 가능한 재고 또는 null이 표시됩니다.</li>
               <li><!--LYNX-460--><strong>번들 제품</strong>: 정확한 가격 및 통화 정보를 보장하도록 번들 제품에 대한 가격 표시가 수정되었습니다.</li>
               <li><!--LYNX-547--><strong>수량</strong>: 수량 알림이 충분하지 않거나 사용할 수 없는 경우 메시지를 수정했습니다.</li>
               <li><!--LYNX-541--><strong>InsufficientStockError 형식</strong>: 재고 수준이 부족한 경우를 처리하기 위해 새 <code>InsufficientStockError</code> 형식을 추가했습니다. 새로운 오류 유형을 지원하도록 스키마를 조정하여 오류 보고 기능을 개선했습니다.</li>
               <li><!--LYNX-476--><strong>재고 금액</strong>: 사용 가능한 재고 금액을 포함하도록 오류 메시지를 개선했습니다. 주문 업데이트 중에 스톡 수준에 대한 명확한 통찰력을 사용자에게 제공합니다.</li>
               <li><!--LYNX-377--><strong>요청된 수량</strong>: <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemInterface"><code>CartItemInterface</code></a>에 <code>not_available_message</code>을(를) 추가했습니다.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>고객 관리</strong></td>
           <td>이번 릴리스에는 다음과 같은 고객 관리 개선 사항이 포함됩니다.
             <ul>
               <li><!--LYNX-391--><strong>generateCustomerToken 돌연변이</strong>: 확인되지 않은 전자 메일에 대한 특정 메시지를 제공하기 위해 <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-generateCustomerToken"><code>generateCustomerToken</code></a> 돌연변이에서 개선된 오류 처리입니다. 향상된 사용자 지침 및 오류 해결을 지원합니다.</li>
               <li><!--LYNX-390--><strong>resendConfirmationEmail 돌연변이</strong>: 이메일 확인을 다시 보내기 위해 새 <code>resendConfirmationEmail</code> 돌연변이를 추가했습니다.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>주문 관리</strong></td>
           <td>이번 릴리스에는 다음과 같은 사용자 주문 관리 개선 사항이 포함됩니다.
             <ul>
              <li><!--LYNX-470--><strong>첫 번째 주문 날짜</strong>: <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrders"><code>CustomerOrders</code></a> 형식에 새 <code>date_of_first_order</code> 필드를 추가했습니다.</li>
              <li><!--LYNX-468--><strong>OrderAddress</strong>: 사용자 지정 특성을 포함하도록 <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderAddress"><code>OrderAddress</code></a> 형식을 확장하여 순서 세부 정보 표시 기능을 개선했습니다. 주문 확인 페이지에 추가 정보를 표시할 수 있습니다.</li>
              <li><!--LYNX-458--><strong>guestOrder 및 guestOrderByToken 쿼리</strong>: 사용자 지정 주소 특성을 포함하도록 <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrder"><code>guestOrder</code></a> 및 <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrderByToken"><code>guestOrderByToken</code></a> 쿼리를 업데이트하여 새 계정에 대한 전체 주소 정보를 확인했습니다.</li>
              <li><!--LYNX-450--><strong>CustomerOrder 형식</strong>: <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> 형식에 <code>is_virtual</code> 필드를 추가하여 가상 제품 식별을 지원합니다. 가상 제품과 실제 제품을 구별하여 주문 처리를 강화합니다.</li>
              <li><!--LYNX-449--><strong>orderItemPrices</strong>: 가격에 대한 새 필드가 여러 개 있는 <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderItemInterface"><code>OrderItemInterface</code></a>에 <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a>과(와) 유사한 <code>OrderItemPrices</code> 형식을 추가했습니다.</li>
              <li><!--LYNX-448--><strong>게스트 주문 병합</strong>: 전자 메일 일치를 기반으로 게스트 주문을 고객 계정과 병합하는 개선된 API 기능입니다. 재방문 고객을 위한 주문 관리를 간소화합니다.</li>
              <li><!-- LYNX-523: --><strong>available_actions 필드</strong>: 더 나은 주문 관리를 위해 <code>available_actions</code> 필드를 포함하도록 <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> 형식을 확장했습니다. 'available_actions' 필드는 해당 주문에서 수행할 수 있는 작업을 나열하는 열거형에 매핑됩니다.</li>
              <li><!-- LYNX-524 --><strong>CustomerOrder 형식</strong>: <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> 형식에 <code>customer_info</code> 필드를 추가했습니다. 이 필드에는 고객 이름에 대한 세부 정보를 정의하는 및 <code>OrderCustomerInfo</code>이(가) 필요합니다.</li>
              <li><!--LYNX-519--><strong>주문 취소에 대한 오류 코드</strong>: <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CancelOrderOutput"><code>CancelOrderOutput</code></a> 형식에 자세한 오류 코드를 추가했습니다. 주문 취소 프로세스에 대한 오류 처리 및 사용자 피드백이 개선되었습니다.</li>
              <li><!--LYNX-515--><strong>게스트 사용자가 주문에 대한 반품을 만들 수 있도록 설정</strong>: 게스트 주문 반품을 지원하도록 <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-requestReturn"><code>requestReturn</code></a> 돌연변이를 조정했습니다.</li>
              <li><!--LYNX-505--><strong>confirmCancelOrder 돌연변이</strong>: 게스트 사용자의 주문 취소를 용이하게 하기 위해 새로운 <code>confirmCancelOrder</code> 돌연변이를 추가했습니다.</li>
             </ul>
           </td>
        </tr>
    </tbody>
</table>
