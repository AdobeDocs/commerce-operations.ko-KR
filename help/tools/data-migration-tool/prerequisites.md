---
title: '''[!DNL Data Migration Tool] 전제 조건'
description: 을(를) 사용하기 전에 수행해야 할 작업을 알아봅니다. [!DNL Data Migration Tool] Magento 1과 Magento 2 간에 데이터를 전송합니다.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# [!DNL Data Migration Tool] 전제 조건

마이그레이션을 시작하기 전에 다음 요구 사항이 충족되는지 확인하십시오.

## Magento 시스템

* 다음을 충족하도록 Magento 2 시스템 설정 [시스템 요구 사항](../../installation/system-requirements.md).

   기존 Magento 1 시스템과 적어도 일치하는 토폴로지 및 설계를 사용하십시오.

* [설치 Magento 2](../../installation/overview.md).

## 크론

Magento 2 cron 작업을 시작하지 마십시오.

## 데이터베이스

* 설치 후 백업 또는 [덤프](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) 가능한 한 빨리 Magento 2 데이터베이스를 만듭니다. 마이그레이션에 실패한 경우 초기 데이터베이스 상태를 복원할 수 있습니다.

* 다음을 확인합니다. [!DNL Data Migration Tool] 은(는) Magento 1과 Magento 2 데이터베이스를 연결하는 네트워크 액세스 권한이 있습니다.

   마이그레이션 도구가 데이터베이스와 통신할 수 있도록 방화벽에서 포트를 엽니다.

* MySQL 계정에 Magento 데이터베이스에 액세스하는 데 필요한 모든 권한이 있는지 확인하십시오.

Magento 1 데이터베이스에 대해 바이너리 로깅이 활성화된 경우 [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL 시스템 변수 `1`또는 다음을 부여합니다. [SUPER 권한](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) 계정에 연결합니다.

* 마이그레이션 전에 Magento 2 저장소에 새 엔티티(제품, 카테고리 및 속성)를 만드는 것은 권장되지 않습니다. [!DNL Data Migration Tool] 는 이러한 새 엔티티를 Magento 1의 이전 엔티티로 덮어씁니다.

## 확장

Magento 1 확장 코드를 Magento 2로 마이그레이션합니다.

최신 확장 버전을 찾으려면 다음을 방문하십시오. [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) 또는 확장 공급자에게 문의하십시오.

다음을 사용할 수도 있습니다 [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
