---
source-git-commit: 102fee9672c75c94c7d18d47562338f8eff97f11
workflow-type: tm+mt
source-wordcount: '451'
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
>이 보안 패치를 설치한 후 Adobe Commerce B2B 판매자도 최신 호환 가능한 B2B 보안 패치 릴리스로 업데이트해야 합니다. [B2B 릴리스 정보](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes)를 참조하세요.

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
