---
source-git-commit: 74cb55f4552bc1b2dace37d9a6f7e68939d1c262
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---
# 코드 조각

## 상거래 전용 {#commerce-only}

>[!NOTE]
>
>다음 [!DNL Upgrade Compatibility Tool] Adobe Commerce 인스턴스에만 사용할 수 있습니다.

<!-- Configuration guide snippets -->

## 파일 시스템 소유자 {#file-system-owner}

>[!WARNING]
>
>모든 Magento CLI 명령은 [파일 시스템 소유자](/help/configuration/cli/config-cli.md#prerequisites).

## 백업 명령 {#tip-backup-command}

>[!TIP]
>
>다음 `support:backup` 명령 _not_ 에 의해 수행된 동일한 코드 백업 `setup:backup` 명령. 다음 `support:backup` 명령은 Adobe Commerce 지원 센터에서 검사할 코드를 백업하기 위한 것입니다.

## Adobe Commerce 전용 {#ee-only}

>[!NOTE]
>
>이 기능은 Adobe Commerce 인스턴스에만 사용할 수 있습니다.

## DB 분할이 사용되지 않음 {#deprecate-split-db}

>[!IMPORTANT]
>
>데이터베이스 분할 기능은 [사용되지 않음](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) Adobe Commerce 버전 2.4.2에서 지원됩니다. 자세한 내용은 [분할 데이터베이스에서 단일 데이터베이스로 되돌리기](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## 호환되지 않는 변경 사항 {#bics}

>[!NOTE]
>
>Adobe Commerce 및 Magento Open Source 릴리스에는 이전 버전과 호환되지 않는 변경 사항(BIC)이 포함되어 있을 수 있습니다. 호환되지 않는 변경 사항을 검토하려면 다음을 참조하십시오 [BIC 참조](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). 다음과 같은 주요 하위 호환 문제는 [빅 밝은 영역](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). 모든 릴리스에서 주요 BIC를 도입하는 것은 아닙니다.

## CVE 알림 {#cve-notice}

>[!NOTE]
>
>2.3.2 릴리스부터 외부 당사자가 Adobe에 보고한 각 보안 버그와 함께 인덱싱된 공통 취약점 및 노출(CVE) 번호를 지정하고 게시합니다. 이를 통해 사용자는 배포에서 해결되지 않은 취약점을 보다 쉽게 식별할 수 있습니다. 에서 CVE 식별자에 대해 자세히 알아볼 수 있습니다 [CVE](https://cve.mitre.org/).
