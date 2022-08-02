---
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '97'
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
