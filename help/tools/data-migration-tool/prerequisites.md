---
title: '[!DNL Data Migration Tool]개 필수 구성 요소'
description: ' [!DNL Data Migration Tool] 을(를) 사용하여 Magento 1과 Magento 2 간에 데이터를 전송하기 전에 수행해야 하는 작업에 대해 알아봅니다.'
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# [!DNL Data Migration Tool]개 필수 구성 요소

마이그레이션을 시작하기 전에 다음 요구 사항이 충족되는지 확인하십시오.

## Magento 시스템

* [시스템 요구 사항](../../installation/system-requirements.md)을 충족하도록 Magento 2 시스템을 설정하십시오.

  적어도 기존 Magento 1 시스템과 일치하는 토폴로지 및 디자인을 사용하십시오.

* [Magento 2](../../installation/overview.md)을(를) 설치합니다.

## 크론

Magento 2 cron 작업을 시작하지 마십시오.

## 데이터베이스

* 설치 후 가능한 한 빨리 Magento 2 데이터베이스를 백업하거나 [dump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)하십시오. 마이그레이션에 실패한 경우 초기 데이터베이스 상태를 복원할 수 있습니다.

* [!DNL Data Migration Tool]에 Magento 1 및 Magento 2 데이터베이스에 연결할 수 있는 네트워크 액세스 권한이 있는지 확인하십시오.

  마이그레이션 도구가 데이터베이스와 통신할 수 있도록 방화벽에서 포트를 엽니다.

* MySQL 계정에 Magento 데이터베이스에 액세스하는 데 필요한 모든 권한이 있는지 확인하십시오.

Magento 1 데이터베이스에 대해 바이너리 로깅이 활성화된 경우 전역 [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL 시스템 변수를 `1`(으)로 설정하거나 계정에 [SUPER 권한](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super)을(를) 부여하십시오.

* [!DNL Data Migration Tool]이(가) 이러한 새 엔터티를 Magento 1의 이전 엔터티로 덮어쓰므로 마이그레이션 전에 Magento 2 저장소에 새 엔터티(제품, 카테고리 및 특성)를 만들지 않는 것이 좋습니다.

## 확장

Magento 1 확장 코드를 Magento 2로 마이그레이션합니다.

최신 확장 버전을 찾으려면 [!DNL [Commerce Marketplace]](https://commercemarketplace.adobe.com//)을(를) 방문하거나 확장 공급자에게 문의하십시오.

[!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md)을(를) 사용할 수도 있습니다.
