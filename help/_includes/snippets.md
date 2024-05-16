---
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---
# 코드 조각

## Commerce 전용 {#commerce-only}

>[!NOTE]
>
>다음 [!DNL Upgrade Compatibility Tool] 는 Adobe Commerce 인스턴스에만 사용할 수 있습니다.

<!-- Configuration guide snippets -->

## 파일 시스템 소유자 {#file-system-owner}

>[!WARNING]
>
>모든 Magento CLI 명령은 [파일 시스템 소유자](/help/configuration/cli/config-cli.md#prerequisites).

## 백업 명령 {#tip-backup-command}

>[!TIP]
>
>다음 `support:backup` 명령: _아님_ 에서 수행한 것과 동일한 코드 백업 `setup:backup` 명령입니다. 다음 `support:backup` 명령은 Adobe Commerce 지원에서 검사할 코드를 백업하기 위한 것입니다.

## Adobe Commerce 전용 {#ee-only}

>[!NOTE]
>
>이 기능은 Adobe Commerce 인스턴스에서만 사용할 수 있습니다.

## DB 분할 사용 안 함 {#deprecate-split-db}

>[!IMPORTANT]
>
>데이터베이스 분할 기능은 [더 이상 사용되지 않음](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) Adobe Commerce 버전 2.4.2에서. 다음을 참조하십시오 [분할 데이터베이스에서 단일 데이터베이스로 되돌리기](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## 이전 버전과 호환 불가능한 변경 사항 {#bics}

>[!NOTE]
>
>Adobe Commerce 릴리스에는 이전 버전과 호환 불가능한 변경 사항(BIC)이 포함될 수 있습니다. 이전 버전과 호환 불가능한 변경 사항을 검토하려면 [BIC 참조](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). 주요 이전 버전과 호환 불가능한 문제는에 설명되어 있습니다. [BIC 특징](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). 일부 릴리스에서는 주요 BIC가 제공되지 않습니다.

## CVE 알림 {#cve-notice}

>[!NOTE]
>
>2.3.2 릴리스부터 외부 파티가 보고하는 각 보안 버그와 함께 인덱싱된 CVE(Common Vulnerabilities and Exposes) 번호를 할당하고 게시합니다. 이를 통해 사용자는 배포에서 해결되지 않은 취약점을 보다 쉽게 식별할 수 있습니다. 다음에서 CVE 식별자에 대해 자세히 알아볼 수 있습니다. [CVE](https://cve.mitre.org/).

## 기타 릴리스 정보 {#other-release-info}

>[!NOTE]
>
>이 릴리스 노트에 설명된 개선 사항 및 버그 수정에 대한 코드가 Adobe Commerce과 번들로 제공되지만 이러한 프로젝트 중 일부(예: B2B, Page Builder 및 Progressive Web Application(PWA) Studio)도 독립적으로 릴리스됩니다. 이러한 프로젝트에 대한 버그 수정은 각 프로젝트에 대한 설명서에서 사용할 수 있는 별도의 프로젝트별 릴리스 정보에 설명되어 있습니다. 다음을 참조하십시오 [제품 릴리스 개요](/help/release/release-notes/overview.md).

## PHP 프로세스 제어 {#php-process-control}

인덱서를 병렬 모드로 실행하려면 먼저 프로세스 제어 지원(`pcntl`PHP의 . 다음을 참조하십시오 [설치](https://www.php.net/manual/en/pcntl.installation.php) PHP 설명서에서 참조하십시오.
