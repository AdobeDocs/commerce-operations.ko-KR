---
source-git-commit: e625670e741c0669050ab758d4f87c5ca06fe3df
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---
# 코드 조각

## Commerce 전용 {#commerce-only}

>[!NOTE]
>
>[!DNL Upgrade Compatibility Tool]은(는) Adobe Commerce 인스턴스에만 사용할 수 있습니다.

<!-- Configuration guide snippets -->

## 파일 시스템 소유자 {#file-system-owner}

>[!WARNING]
>
>모든 Magento CLI 명령은 [파일 시스템 소유자](/help/configuration/cli/config-cli.md#prerequisites)에서 실행해야 합니다.

## 백업 명령 {#tip-backup-command}

>[!TIP]
>
>`support:backup` 명령은 _명령에 의해 수행된 것과 동일한 코드 백업입니다_ not`setup:backup`. `support:backup` 명령은 Adobe Commerce 지원에서 검사할 코드를 백업하기 위한 것입니다.

## B2B 패치 {#b2b-patches}

>[!NOTE]
>
>이 보안 패치를 설치한 후 Adobe Commerce B2B 판매자도 최신 호환 가능한 B2B 보안 패치 릴리스로 업데이트해야 합니다. [B2B 릴리스 정보](https://experienceleague.adobe.com/ko/docs/commerce-admin/b2b/release-notes)를 참조하세요.

## Adobe Commerce 전용 {#ee-only}

>[!NOTE]
>
>이 기능은 Adobe Commerce 인스턴스에서만 사용할 수 있습니다.

## DB 분할 사용 안 함 {#deprecate-split-db}

>[!IMPORTANT]
>
>데이터베이스 분할 기능은 Adobe Commerce 버전 2.4.2에서 [사용되지 않음](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157)되었습니다. [분할 데이터베이스에서 단일 데이터베이스로 되돌리기](/help/configuration/storage/revert-split-database.md)를 참조하십시오.

<!-- End of Configuration guide snippets -->

## 이전 버전과 호환 불가능한 변경 사항 {#bics}

>[!NOTE]
>
>Adobe Commerce 릴리스에는 이전 버전과 호환 불가능한 변경 사항(BIC)이 포함될 수 있습니다. 이전 버전과 호환되지 않는 변경 내용을 검토하려면 [BIC 참조](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)를 참조하십시오. 이전 버전과 호환되지 않는 주요 문제는 [BIC 하이라이트](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/)에 설명되어 있습니다. 일부 릴리스에서는 주요 BIC가 제공되지 않습니다.

## Alpha 면책조항 {#alpha}

>[!IMPORTANT]
>
>[Alpha](/help/release/versioning-policy.md#alpha-patch-release) 릴리스는 불완전할 수 있으며 결함이 있을 수 있습니다. 어떠한 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe은 Adobe 지원 서비스 또는 다른 방법을 통해 Alpha 릴리스를 유지, 수정, 업데이트, 변경, 수정 또는 지원할 의무가 없습니다. 고객은 Alpha 릴리스 또는 관련 설명서나 자료의 올바른 기능이나 성능에 의존해서는 안 됩니다. Alpha 릴리스의 사용은 전적으로 고객 자신의 책임입니다.

## Beta 면책조항 {#beta}

>[!IMPORTANT]
>
>Beta 릴리스에는 결함이 포함될 수 있으며 어떤 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe은 베타 릴리스를 유지, 수정, 업데이트, 변경, 수정 또는 기타 지원(Adobe 지원 서비스 또는 기타 서비스)할 의무가 없습니다. 고객은 베타 릴리스 및/또는 관련 설명서나 자료의 올바른 기능이나 성능에 어떠한 의존도 하지 말고 주의해야 합니다. 따라서 Beta 릴리스를 사용하는 것은 전적으로 고객 자신의 책임입니다.

## CVE 알림 {#cve-notice}

>[!NOTE]
>
>2.3.2 릴리스부터 외부 파티가 보고하는 각 보안 버그와 함께 인덱싱된 CVE(Common Vulnerabilities and Exposes) 번호를 할당하고 게시합니다. 이를 통해 사용자는 배포에서 해결되지 않은 취약점을 보다 쉽게 식별할 수 있습니다. [CVE](https://cve.mitre.org/)에서 CVE 식별자에 대해 자세히 알아볼 수 있습니다.

## 기타 릴리스 정보 {#other-release-info}

>[!NOTE]
>
>이 릴리스 노트에 설명된 개선 사항 및 버그 수정에 대한 코드가 Adobe Commerce과 번들로 제공되지만 이러한 프로젝트 중 일부(예: B2B, Page Builder 및 Progressive Web Applications(PWA) Studio)도 독립적으로 릴리스됩니다. 이러한 프로젝트에 대한 버그 수정은 각 프로젝트에 대한 설명서에서 사용할 수 있는 별도의 프로젝트별 릴리스 정보에 설명되어 있습니다. [제품 릴리스 개요](/help/release/release-notes/overview.md)를 참조하세요.

## PHP 프로세스 제어 {#php-process-control}

병렬 모드에서 인덱서를 실행하려면 먼저 PHP에서 프로세스 제어 지원(`pcntl`)을 사용하도록 설정해야 합니다. PHP 설명서에서 [설치](https://www.php.net/manual/en/pcntl.installation.php)를 참조하십시오.

## 사용자 지정 패치 {#custom-patches-disclaimer}

>[!IMPORTANT]
>
>Adobe은 이 방법을 사용하여 Adobe에서 제공하는 공식 패치를 적용할 수 없습니다. 다음의 방법을 사용하십시오. 공식 패치를 적용하려면 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko){target="_blank"}을(를) 사용합니다. 사용자 정의 패치를 배포하기 전에 항상 포괄적인 테스트를 수행하십시오.

## 2025년 10월 보안 패치 백포트 {#oct-2025-backports}

<!--These fixes were backported to 2.4.8-pe, 2.4.7-p8, and 2.4.6-p13-->

* **TinyMCE에서 Hugerte.org로 마이그레이션**

  TinyMCE 5 및 6에 대한 지원 종료 및 TinyMCE 7과의 라이선스 비호환성으로 인해 Adobe Commerce WYSIWYG 편집기의 현재 구현은 TinyMCE에서 오픈 소스 [HugeRTE 편집기](https://hugerte.org/)&#x200B;(으)로 마이그레이션됩니다.

  이러한 마이그레이션은 Adobe Commerce이 오픈 소스 라이센싱을 준수하도록 하며 알려진 TinyMCE 6 취약점을 방지하고 판매자와 개발자에게 현대적이고 지원되는 편집 환경을 제공합니다.

* **Apache ActiveMQ Artemis STOMP 프로토콜에 대한 지원이 추가되었습니다**

  STOMP(Simple Text Oriented Messaging Protocol)를 통해 ActiveMQ Artemis 오픈 소스 메시지 브로커에 대한 지원을 추가했습니다. 안정적이고 확장 가능한 메시징 시스템을 제공하여 STOMP 기반 통합을 위한 유연성을 제공합니다. [Commerce 구성 가이드](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework#apache-activemq-artemis-stomp)에서 *Apache ActiveMQ Artemis*&#x200B;을(를) 참조하십시오.

## 체크아웃 페이지가 static.min.js 및 mixins.min.js를 로드하지 못했습니다. {#checkout-page-fails-to-load-static-min-js-and-mixins-min-js}

최근 CSP/SRI 변경 후에는 JavaScript 번들링 및 축소가 프로덕션 모드에서 모두 활성화될 때 체크아웃 페이지가 static.min.js 및 mixins.min.js를 로드하지 않습니다. 따라서 RequireJS mixins가 실행되지 않고 체크아웃 녹아웃 템플릿을 확인하지 못합니다(예: `"Failed to load the 'Magento_Checkout/shipping' template requested by 'checkout.steps.shipping-step.shippingAddress'"`).

**해결 방법**:

* JavaScript 번들 비활성화 또는
* JavaScript 번들링을 활성화한 상태로 유지하는 경우 JavaScript 축소를 비활성화합니다.

>[!IMPORTANT]
>
>CSP를 비활성화하거나 프로덕션에서 SRI 보호를 제거하지 마십시오. 플러그인 수준 우회는 핫픽스를 위한 마지막 수단으로만 사용해야 하며 보안 팀에서 검토해야 합니다.

**핫픽스**:

이 문제를 해결하는 핫픽스가 가능한 한 빨리 릴리스됩니다. 업데이트를 위해 이 릴리스 정보 페이지를 모니터링하십시오.
