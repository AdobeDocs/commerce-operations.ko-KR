---
title: '"[!DNL Data Migration Tool] 전제 조건'
description: '"을 사용하기 전에 필요한 작업을 알아보십시오 [!DNL Data Migration Tool] Magento 1과 Magento 2 사이의 데이터를 전송하는 방법"'
source-git-commit: 87298a6dfd783fed264f275495a3ad72374eb9f6
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# [!DNL Data Migration Tool] 전제 조건

마이그레이션을 시작하기 전에 다음 요구 사항이 충족되었는지 확인하십시오.

## Magento 2 시스템

* Magento 2 시스템이 [시스템 요구 사항](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html).

   기존 Magento 1 시스템과 적어도 일치하는 토폴로지 및 디자인을 사용합니다.

* [Magento 2 설치](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html).

## 크론

Magento 2 cron 작업을 시작하지 마십시오.

## 데이터베이스

* 설치 후 또는 백업 [덤프](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) 가능한 한 빨리 Magento 2 데이터베이스를 사용하십시오. 마이그레이션이 실패할 경우 초기 데이터베이스 상태를 복원할 수 있습니다.

* 다음을 확인합니다. [!DNL Data Migration Tool] Magento 1 및 Magento 2 데이터베이스를 연결하기 위한 네트워크 액세스 권한이 있습니다.

   마이그레이션 도구가 데이터베이스와 통신할 수 있도록 방화벽에서 포트를 엽니다.

* MySQL 계정에 Magento 데이터베이스에 액세스하는 데 필요한 모든 권한이 있는지 확인하십시오.

Magento 1 데이터베이스에 대해 이진 로깅이 활성화된 경우 전역 [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL 시스템 변수를에 `1`, 또는 [수퍼 권한](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) 참조하십시오.

* 마이그레이션하기 전에 Magento 2에 새 엔터티(제품, 카테고리 및 특성)를 만들면 [!DNL Data Migration Tool] 는 새 엔티티를 Magento 1의 이전 엔티티로 덮어씁니다.

## 확장

Magento 1 확장 코드를 Magento 2으로 마이그레이션합니다.

최신 확장 버전을 찾으려면 를 방문하십시오. [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) 또는 확장 공급자에게 문의하십시오.

를 사용할 수도 있습니다 [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
