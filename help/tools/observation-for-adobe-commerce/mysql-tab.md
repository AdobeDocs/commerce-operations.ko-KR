---
title: 다음 [!UICONTROL MySQL] 탭
description: 에 대해 알아보기 [!UICONTROL MySQL] 탭 / [!DNL Observation for Adobe Commerce].
exl-id: 1d8dd07c-15fd-4ffd-ad10-0d886bf1579e
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '2030'
ht-degree: 0%

---

# 다음 [!UICONTROL MySQL] 탭

## [!UICONTROL MySQL% free storage by node]

![노드별 MySQL% 사용 가능 스토리지](../../assets/tools/observation-for-adobe-commerce/mysql-tab-1.jpg)

MySQL에 할당된 스토리지의 스토리지가 MySQL에서 부족하여 많은 문제가 발생합니다(`datadir` MySQL 구성 설정, 기본값은 `/data/mysql`) 또는 `tmpdir` 공간이 부족합니다. 기본값 `tmpdir` (MySQL 설정): `/tmp`. 다음 **[!UICONTROL MySQL% free storage by node]** 프레임이 다음을 봅니다. `/, /tmp` (별도의 마운트로 정의된 경우) 및 `/data/mysql` 사용 가능한 스토리지 비율. MySQL 버전 5.7(MariaDB 버전 10.2)에서 시작, 압축되지 않음 `tmp` 테이블에 작성됨 `tmp` 테이블스페이스의 `/data/mysql` 파일의 디렉터리(ibtmp1). 이 파일은 기본적으로 제한 없이 자동으로 확장됩니다. 테이블스페이스이므로 크기가 줄어들지 않고 MySQL이 다시 시작될 때 12MB로 재설정됩니다.

## [!UICONTROL MySQL Connections by Node]

![노드별 MySQL 연결](../../assets/tools/observation-for-adobe-commerce/mysql-tab-2.jpg)

다음 **[!UICONTROL MySQL Connections by Node]** 프레임은 데이터베이스 노드 중단 또는 대량 연결 기간을 나타냅니다.

## [!UICONTROL MySQL Node Summary]

![MySQL 노드 요약](../../assets/tools/observation-for-adobe-commerce/mysql-tab-3.jpg)

다음 **[!UICONTROL MySQL Node Summary]** 이 표에서는 소프트웨어 버전 및 인스턴스 유형(크기)과 같은 데이터베이스 노드 세부 정보를 보여 줍니다.

## [!UICONTROL Galera Number of Nodes in cluster]

![클러스터의 노드 수](../../assets/tools/observation-for-adobe-commerce/mysql-tab-4.jpg)

다음 **[!UICONTROL Galera Number of Nodes in cluster]** 프레임은 MySQL 로그의 정보를 표시합니다. 노드가 클러스터에 참여하고 나갈 때 선택한 기간에 대한 메시지만 표시됩니다. 노드가 일정 기간 전에 클러스터를 떠나면 해당 기간 동안 메시지가 존재하지 않습니다. 데이터베이스에 노드가 부족할 수 있다고 의심되는 경우 시간대를 더 긴 기간으로 확장하여 추가 정보를 볼 수 있는지 확인합니다. 기간 중에 의 모든 노드보다 작음을 나타내는 정보가 있는 경우 [!DNL Galera] 클러스터에서 기간을 확장하여 노드가 클러스터를 떠난 시기를 확인할 수 있는지 확인합니다.

## [!UICONTROL MySQL shutdowns and starts]

![MySQL이 종료되고 시작됩니다](../../assets/tools/observation-for-adobe-commerce/mysql-tab-5.jpg)

다음 **[!UICONTROL MySQL shutdowns and starts]** frame은 노드가 종료되면 감지합니다. 다음 [!DNL Galera] 노드가 제거되고 다음에서 자동 제거됩니다. [!DNL Galera] 노드. 이렇게 하면 일반적으로 MySQL 서비스가 다시 시작됩니다.

## [!UICONTROL Galera log]

![갈레라 로그](../../assets/tools/observation-for-adobe-commerce/mysql-tab-6.jpg)

다음 **[!UICONTROL Galera log]** frame은 다음에 대한 MySQL 로그의 특정 신호 수를 보여줍니다. [!DNL Galera] 노드, 해당 상태 및 의 상태 변경 [!DNL Galera] 클러스터.

* &#39;%1047 WSREP에서 아직 &#39;node_not_prep_for_use&#39;(응용 프로그램 사용%&#39;)에 대한 노드를 준비하지 않았습니다.
* &#39;%\[ERROR\] WSREP: wsrep_sst_xtrabackup-v2%&#39;에서 &#39;xtrabackup_read_fail&#39;로 읽지 못했습니다.
* &#39;%\[ERROR\] WSREP: &#39;xtrabackup_compl_w_err&#39;로 표시되는 동안 오류가 발생하여 프로세스가 완료되었습니다. wsrep_sst_xtrabackup-v2 %&#39;
* &#39;%\[ERROR\] WSREP: rbr 쓰기 실패%&#39;)를 &#39;rbr_write_fail&#39;로 함
* &#39;%self-leave%&#39;)을(를) &#39;susp_node&#39;로 설정
* &#39;%members = 3/3 (joined/total)%&#39;) as&#39;3of3&#39;
* &#39;%members = 2/3 (joined/total)%&#39;) as&#39;2of3&#39;
* &#39;%members = 2/2%&#39;)을(를) &#39;2of2&#39;(으)로 설정
* &#39;%members = 1/2%&#39;)을(를) &#39;1of2&#39;(으)로 설정
* &#39;%members = 1/3%&#39;)을(를) &#39;1of3&#39;으로 설정
* &#39;%members = 1/1%&#39;)을(를) &#39;1of1&#39;(으)로 설정
* &#39;%\[참고\] /usr/sbin/mysqld(mysqld 10.%&#39;)를 &#39;sql_restart&#39;로
* &#39;%Quorum: 완료 상태:%&#39;인 노드가 없음) &#39;no_node_count&#39;
* &#39;%WSREP: 멤버 0%&#39;)이 &#39;mem_0&#39;이 되었습니다.
* &#39;%WSREP: 멤버 1.0%&#39;)이 &#39;mem_1&#39;인 경우
* &#39;%WSREP: 멤버 2%&#39;) as&#39;mem2&#39;
* &#39;%WSREP: 그룹과 동기화됨, 연결 준비%&#39;)이 &#39;준비&#39;입니다.
* &#39;%/usr/sbin/mysqld, 버전:%&#39;)을 &#39;mysql_restart_mysql.slow&#39;로 설정합니다.
* &#39;%\[참고\] WSREP: 새 클러스터 보기: 전역 상태:%&#39;) as &#39;galera_cluster_view_chng&#39;

## [!UICONTROL Galera Log by Host]

![Galera Log by Host](../../assets/tools/observation-for-adobe-commerce/mysql-tab-7.jpg)

다음 **[!UICONTROL Galera Log by Host]** 프레임은 와(과) 동일합니다. **[!UICONTROL Galera log]** 프레임(노드별로 분류되어 문제 해결에 도움이 된다는 점을 제외)

## [!UICONTROL Database performance]

![데이터베이스 성능](../../assets/tools/observation-for-adobe-commerce/mysql-tab-8.jpg)

다음 **[!UICONTROL Database performance]** frame은 특정 요청 동안의 데이터베이스 성능을 보여 줍니다. 그래프 아래의 색상이 지정된 아이콘에서 각 지표를 클릭하여 볼 수 있습니다. 에서 호출된 많은 지표 [New Relic을 사용하여 MySQL 데이터베이스 성능 모니터링](https://newrelic.com/blog/how-to-relic/how-to-monitor-mysql) 이 프레임에서 찾을 수 있습니다.

* average(query.queriesPerSecond)
* average(query.slowQueriesPerSecond)
* average(db.createdTmpDiskTablesPerSecond)
* average(db.createdTmpFilesPerSecond)
* average(db.tablesLocksWaitedPerSecond)
* average(db.innodb.rowLockTimeAvg)
* average(db.innodb.rowLockWaitsPerSecond)

## [!UICONTROL Transaction Database Call Count]

![트랜잭션 데이터베이스 호출 수](../../assets/tools/observation-for-adobe-commerce/mysql-tab-9.jpg)

다음 **[!UICONTROL Transaction Database Call Count]** frame은 각 트랜잭션 패싯에 의해 수행된 데이터베이스 호출 수를 보여줍니다. 이는 진술이 아닌 행 중심적인 것으로 보인다.

## [!UICONTROL Cron_schedule table updates]

![Cron_schedule 테이블 업데이트](../../assets/tools/observation-for-adobe-commerce/mysql-tab-10.jpg)

다음 **[!UICONTROL Cron_schedule table updates]** frame은 선택한 기간 동안 cron_schedule 테이블에 대한 데이터베이스 업데이트의 최대 기간을 표시합니다.

## [!UICONTROL Slow Query Traces]

![느린 쿼리 추적](../../assets/tools/observation-for-adobe-commerce/mysql-tab-11.jpg)

다음 **[!UICONTROL Slow Query Traces]** 프레임에는 느린 쿼리 추적이 있는 테이블 및 요청 유형이 표시됩니다. 5초 이상 걸리는 쿼리 트랜잭션에 대해 느린 쿼리 추적이 만들어집니다. 업데이트 쿼리는 이 프레임에서 가장 중요합니다. 다음에서 테이블을 업데이트하는 경우: `UPDATE`, `DELETE`, 및 `INSERT` 문은 일정 기간 동안 테이블을 잠글 수 있습니다.

균일 `SELECT` 문은 FOR UPDATE와 함께 사용할 경우 행을 잠글 수 있습니다.

## [!UICONTROL Datastore Operations tables]

![데이터 저장소 작업 테이블](../../assets/tools/observation-for-adobe-commerce/mysql-tab-12.jpg)

## [!UICONTROL Cron table change]

![크론 테이블 변경](../../assets/tools/observation-for-adobe-commerce/mysql-tab-13.jpg)

다음 **[!UICONTROL Cron table change]** frame은 &quot;cron job에 대한 잠금을 획득할 수 없습니다:&quot; 오류 메시지와 함께 특정 PHP 메모리 오류 및 `cron_schedule` 테이블. 다음과 같은 경우 `cron_schedule` 테이블이 잠겨 있습니다(예: `DELETE` 쿼리가 실행 중입니다). 다른 cron이 실행되지 않도록 차단합니다.

## [!UICONTROL Deadlocks]

![교착 상태](../../assets/tools/observation-for-adobe-commerce/mysql-tab-14.jpg)

다음 **[!UICONTROL Deadlocks]** frame은 MySQL 로그에서 구문 분석된 다음 문자열을 살펴봅니다.

* &#39;%PHP 심각한 오류: 허용되는 메모리 크기(%&#39;)를 php_mem_error로 표시
* &#39;%get lock; 트랜잭션을 다시 시작해 보십시오. 쿼리: DELETE 출처: \`cron_schedule%&#39;) as cron_sched_lock_del
* &#39;% lock for cron job: indexer_reindex_all_invalid%&#39;) as &#39;lock_indexer_reindex_all_invalid%&#39;
* &#39;% cron job에 대한 잠금: cron_schedule%&#39;)을 &#39;lock_cron_schedule&#39;로
* &#39;% lock for cron job:%&#39;) as &#39;total_cron_lock&#39;
* &#39;%일반 오류: 1205 잠금 대기 시간 제한 초과%&#39;)를 &#39;sql_1205_lock&#39;으로 설정합니다.
* &#39;%ERROR 1213 (40001): lock%&#39;을(를) &#39;sql_1213_lock&#39;으로 가져오는 동안 교착 상태가 발견되었습니다.
* &#39;%SQLSTATE[40001]: 직렬화 실패: 1213 교착 상태 발견%) as &#39;sql_1213_lock2&#39;
* &#39;% lock for cron job: indexer_update_all_views%&#39;) as &#39;lock_indexer_update_all_views&#39;
* &#39;% lock for cron job: sales_grid_order_invoice_async_insert%&#39;) as &#39;lock_sales_grid_order_invoice_async_insert&#39;,
* &#39;% cron 작업에 대한 잠금: staging_remove_updates%&#39;)이 &#39;lock_staging_remove_updates&#39;로 표시됨
* &#39;% lock for cron job: sales_grid_order_shipment_async_insert%&#39;) as &#39;lock_sales_grid_order_shipment_async_insert&#39;
* &#39;% cron job에 대한 잠금: amazon_payments_process_queued_reffers%&#39;) as &#39;lock_amazon_payments_process_queued_reffers&#39;
* &#39;% cron job에 대한 잠금: sales_send_order_shipment_emails%&#39;) as &#39;lock_sales_send_order_shipment_emails&#39;
* &#39;% cron 작업에 대한 잠금: staging_synchronize_entities_period%&#39;)이 &#39;lock_staging_synchronize_entities_period&#39;입니다.
* &#39;% lock for cron job: indexer_clean_all_changelogs%&#39;) as &#39;lock_indexer_clean_all_changelogs&#39;
* &#39;% cron job에 대한 잠금: magento_targetrule_index_reindex%&#39;)이 &#39;lock_magento_targetrule_index_reindex&#39;인 경우
* &#39;% cron 작업 잠금: newsletter_send_all%&#39;) as &#39;lock_newsletter_send_all&#39;
* &#39;% cron 작업 잠금: newsletter_send_all%&#39;) as &#39;lock_newsletter_send_all&#39;
* &#39;% cron job에 대한 잠금: sales_send_order_emails%&#39;) as &#39;lock_sales_send_order_emails&#39;
* &#39;% cron job에 대한 잠금: sales_send_order_creditmemo_emails%&#39;) as &#39;lock_sales_send_order_creditmemo_emails&#39;
* &#39;% lock for cron job: sales_grid_order_creditmemo_async_insert%&#39;) as &#39;lock_sales_grid_order_creditmemo_async_insert&#39;
* &#39;% cron job: bulk_cleanup%&#39;)을 &#39;lock_bulk_cleanup&#39;으로 설정
* &#39;% cron job: flush_preview_quotas%&#39;) &quot;lock_flush_preview_quotas&quot;(cron job: flush_preview_quotas)&quot;
* &#39;% cron job에 대한 잠금: sales_send_order_invoice_emails%&#39;) as &#39;lock_sales_send_order_invoice_emails&#39;
* &#39;% cron job에 대한 잠금: sales_send_order_invoice_emails%&#39;) as &#39;lock_sales_send_order_invoice_emails&#39;
* &#39;% cron 작업 잠금: captcha_delete_expired_images%&#39;) as &#39;lock_captcha_delete_expired_images&#39;
* &#39;% cron job: magento_newrelicreporting_cron%&#39;) as &#39;lock_magento_newrelicreporting_cron&#39;
* &#39;% cron job에 대한 잠금: oldecated_authentication_failures_cleanup%&#39;)을 &#39;lock_oldecated_authentication_failures_cleanup&#39;으로 설정
* &#39;% cron job: send_notification%&#39;)을 &#39;lock_send_notification&#39;으로 설정
* &#39;% cron job에 대한 잠금: magento_giftcardaccount_generage_codes_pool%&#39;)을 &#39;lock_magento_giftcardaccount_generage_codes_pool&#39;로
* &#39;% cron job: catalog_product_frontend_actions_flush%&#39;)을 &#39;lock_catalog_product_frontend_actions_flush&#39;로 잠금
* &#39;% cron 작업 잠금: mysqlmq_clean_messages%&#39;)을 &#39;mysqlmq_clean_messages&#39;로 표시
* &#39;% cron 작업에 대한 잠금: catalog_product_attribute_value_synchronize%&#39;)을(를) &#39;lock_catalog_product_attribute_value_synchronize&#39;(으)로
* &#39;% lock for cron job: ddg_automation_importer%&#39;) as &#39;lock_ddg_automation_importer&#39;
* &#39;% lock for cron job: ddg_automation_reviews_and_wishlist%&#39;) as &#39;lock_ddg_automation_reviews_and_wishlist&#39;
* &#39;% cron 작업 잠금: captcha_delete_old_attempts%&#39;) as &#39;lock_captcha_delete_old_attempts&#39;
* &#39;% cron job에 대한 잠금: catalog_product_old_price_values_cleanup%&#39;)을 &#39;lock_catalog_product_old_price_values_cleanup&#39;으로 표시
* &#39;% cron 작업에 대한 잠금: consumer_runner%&#39;)을 &#39;lock_consumer_runner&#39;로 표시
* &#39;% cron 작업 잠금: ddg_automation_customer_subscriber_guest_sync%&#39;) as &#39;lock_ddg_automation_customer_subscriber_guest_sync&#39;
* &#39;% cron 작업 잠금: get_amazon_capture_updates%&#39;) as &#39;lock_get_amazon_capture_updates&#39;
* &#39;% cron 작업 잠금: get_amazon_authorization_updates%&#39;) as &#39;lock_send_get_amazon_authorization_updates&#39;
* &#39;% cron job에 대한 잠금: temando_process_platform_events%&#39;) as &#39;lock_temando_process_platform_events&#39;
* &#39;% lock for cron job: ddg_automation_status%&#39;) as &#39;lock_ddg_automation_status&#39;
* &#39;% lock for cron job: ddg_automation_status%&#39;) as &#39;lock_ddg_automation_status&#39;
* &#39;% cron job: sales_clean_orders%&#39;)을 &#39;lock_sales_clean_orders&#39;로 잠금
* &#39;% cron 작업에 대한 잠금: catalog_index_refresh_price%&#39;)을 &#39;lock_catalog_index_refresh_price&#39;로
* &#39;% cron job에 대한 잠금: magento_reward_balance_warning_notification%&#39;)이 &#39;lock_magento_reward_balance_warning_notification&#39;으로 설정됨
* &#39;% cron job 잠금: analytics_update%&#39;) as &#39;lock_analytics_update&#39;
* &#39;% cron job: messagequeue_clean_oldeted_locks%&#39;)을(를) &#39;lock_messagequeue_clean_oldeted_locks&#39;로 설정합니다.
* &#39;% cron job: messagequeue_clean_oldeted_locks%&#39;)을(를) &#39;lock_messagequeue_clean_oldeted_locks&#39;로 설정합니다.
* &#39;% cron 작업에 대한 잠금: staging_apply_version%&#39;)을(를) &#39;lock_staging_apply_version&#39;(으)로
* &#39;% cron job: magento_reward_expire_points%&#39;)를 &#39;lock_magento_reward_expire_points&#39;로 잠금
* &#39;% cron job: yotpo_yotpo_orders_sync%&#39;) as &#39;lock_yotpo_yotpo_orders_sync&#39;
* &#39;% cron job에 대한 잠금: catalog_event_status_checker%&#39;) as &#39;lock_catalog_event_status_checker&#39;
* &#39;% lock for cron job: ddg_automation_campaign%&#39;) as &#39;lock_ddg_automation_campaign&#39;
* &#39;% cron job: visitor_clean%&#39;)을 &#39;lock_visitor_clean&#39;으로 설정
* &#39;% lock for cron job: scconnector_verify_website%&#39;)을 &#39;lock_scconnector_verify_website&#39;로 설정
* &#39;% cron job에 대한 잠금: ddg_automation_email_templates%&#39;) as &#39;lock_ddg_automation_email_templates&#39;
* &#39;% cron job에 대한 잠금: aggregate_sales_report_order_data%&#39;)을 &#39;lock_aggregate_sales_report_order_data&#39;로 표시
* &#39;% cron 작업 잠금: ddg_automation_catalog_sync%&#39;) as &#39;lock_ddg_automation

## [!UICONTROL DB Statistics]

![DB 통계](../../assets/tools/observation-for-adobe-commerce/mysql-tab-15.jpg)

다음 **[!UICONTROL DB Statistics]** 프레임은 초당 삭제, 쓰기, 행 읽기, 업데이트 및 느린 쿼리를 표시합니다.

## [!UICONTROL Request frequency]

![요청 빈도](../../assets/tools/observation-for-adobe-commerce/mysql-tab-16.jpg)

## [!UICONTROL Database Errors]

![데이터베이스 오류](../../assets/tools/observation-for-adobe-commerce/mysql-tab-17.jpg)

다음 **[!UICONTROL Database Errors]** 프레임에는 다양한 데이터베이스가 표시됩니다. [경고 및 오류](https://mariadb.com/kb/en/mariadb-error-codes/):

* &#39;%임시 테이블에 할당된 메모리 크기가 &#39;temp_tbl_buff_pool&#39;인 innodb_buffer_pool_size%의 20%를 초과합니다.
* &#39;%\[ERROR\] WSREP: rbr 쓰기 실패%&#39;)를 &#39;rbr_write_fail&#39;로 함
* &#39;%mysqld: Disk full%&#39;)이(가) &#39;disk_full&#39;인 경우
* &#39;%Error number 28%&#39;)을(를) &#39;err_28&#39;(으)로
* &#39;%rollback%&#39;)을 &#39;rollback&#39;으로
* &#39;%Foreign KEY 제약 조건이 테이블%&#39;에 대해 실패했습니다.) &#39;foreign_key_constraint&#39;(으)로
* &#39;%Error_code: 1114%&#39;) as &#39;sql_1114_full&#39;%CRITICAL: SQLSTATE[HY000] [2006] MySQL Server가 없어짐(%))을 &#39;sql_gone&#39;(으)로
* &#39;%SQLSTATE[HY000] [1040년] &#39;%&#39;)가 &#39;sql_1040&#39;인 경우
* &#39;%중요: SQLSTATE[HY000] [2002]%&#39;)를 &#39;sql_2002&#39;로 변환
* &#39;%SQLSTATE[08S01]:%&#39;)를 &#39;sql_1047&#39;로
* &#39;%[경고] Aborted connection%&#39;)가 &#39;aborted_conn&#39;으로 표시됨
* &#39;%SQLSTATE[23000]: 무결성 제약 조건 위반: %&#39;)을 &#39;sql_23000&#39;으로
* &#39;%1205 대기 시간 제한%&#39;)을(를) &#39;sql_1205&#39;(으)로 설정
* &#39;%SQLSTATE[HY000] [1049년] 알 수 없는 데이터베이스%)가 &#39;sql_1049&#39;인 경우
* &#39;%SQLSTATE[42S02]: 기본 테이블 또는 뷰를 찾을 수 없음:%) as &#39;sql_42S02&#39;
* &#39;%General 오류: 1114%&#39;)을(를) &#39;sql_1114&#39;(으)로
* &#39;%SQLSTATE[40001]%&#39;)를 &#39;sql_1213&#39;으로
* &#39;%SQLSTATE[42S22]: 열을 찾을 수 없음: 1054 알 수 없는 열%&#39;)를 &#39;sq1_1054&#39;로 지정
* &#39;%SQLSTATE[42000]: 구문 오류 또는 액세스 위반:%&#39;) as&#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]: 카디널리티 위반:%&#39;)을 &#39;sql_1241&#39;로 지정
* &#39;%SQLSTATE[22003]:%&#39;)를 &#39;sql_22003&#39;로
* &#39;%SQLSTATE[HY000] [9000] IP 주소(%&#39;)를 &#39;sql_9000&#39;으로 설정한 클라이언트
* &#39;%SQLSTATE[HY000]: 일반 오류: 2014%&#39;)가 &#39;sql_2014&#39;인 경우
* &#39;%1927 연결이 끊어졌습니다.%&#39;) &#39;sql_1927&#39;(으)로
* &#39;%1062 \[ERROR\] InnoDB:%&#39;)이(가) &#39;sql_1062_e&#39;인 경우
* &#39;&#39;%[참고] WSREP: 디스크로 메모리 맵을 플러시하는 중...%) &quot;mem_map_flush&quot;로 설정
* &#39;%Internal MariaDB 오류 코드: 1146%&#39;)을(를) &#39;sql_1146&#39;(으)로 설정
* &#39;%내부 MariaDB 오류 코드: 1062%&#39;) as &#39;sql_1062&#39; * &#39;%1062 [경고] InnoDB:%)를 &#39;sql_1062_w&#39;로
* &#39;%Internal MariaDB 오류 코드: 1064%&#39;)을(를) &#39;sql_1064&#39;(으)로 설정
* &#39;%InnoDB: &#39;%&#39; 파일에서 어설션 오류가 발생했습니다. &#39;%Assertion_err&#39;(으)로 표시됨
* &#39;%mysqld_safe 현재 실행 중인 프로세스 수: 0%&#39;)가 &#39;mysql_oom&#39;인 경우
* &#39;%\[ERROR\] mysqld got signal%&#39;)이(가) &#39;mysql_sigterm&#39;(으)로 표시됨
* &#39;%1452%&#39;를 &#39;sql_1452&#39;로 추가할 수 없습니다.
* &#39;%ERROR 1698%&#39;)을(를) &#39;sql_1698&#39;(으)로
* &#39;%SQLSTATE[HY000]: 일반 오류: 3%&#39;)가 &#39;cnt_wrt_tmp&#39;인 경우
* &#39;%일반 오류: 1 %&#39;)을(를) &#39;sql_syntax&#39;로 지정했습니다.
* &#39;%42S22%&#39;)을(를) &#39;sql_42S22&#39;로 함
* &#39;%InnoDB: 오류(중복 키)%&#39;)가 로그 시계열에서 &#39;innodb_dup_key&#39;로 표시됨

## [!UICONTROL DB Error Table]

![DB 오류 테이블](../../assets/tools/observation-for-adobe-commerce/mysql-tab-18.jpg)

다음 **[!UICONTROL DB Error Table]** frame은 와 동일한 정보를 표시합니다. **[!UICONTROL Database Errors]** 프레임이지만 노드별로 표 형식으로 볼 수 있습니다. 다음을 참조하십시오 [MariaDB 오류 코드](https://mariadb.com/kb/en/mariadb-error-codes/) 추가 정보.

## [!UICONTROL Database Traces]

![데이터베이스 추적](../../assets/tools/observation-for-adobe-commerce/mysql-tab-19.jpg)

다음 **[!UICONTROL Database Traces]** 프레임은 선택한 타임라인에서 유형별 데이터베이스 추적을 보여 줍니다.

## [!UICONTROL Database processes]

![데이터베이스 프로세스](../../assets/tools/observation-for-adobe-commerce/mysql-tab-20.jpg)

다음 **[!UICONTROL Database processes]** frame은 데이터베이스 프로세스, 환경 및 노드 식별자를 보여 줍니다.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![노드별 MySQL 비휴지 스레드](../../assets/tools/observation-for-adobe-commerce/mysql-tab-21.jpg)

다음 **[!UICONTROL MySQL Non-Sleeping Threads by Node]** 프레임에는 데이터베이스에 대한 연결 스레드가 표시됩니다. 이 프레임에는 활성 스레드가 표시됩니다.

## [!UICONTROL MySQL Running and Sleeping Threads by environment]

![환경별 MySQL 실행 및 대기 중인 스레드](../../assets/tools/observation-for-adobe-commerce/mysql-tab-22.jpg)

다음 **[!UICONTROL MySQL Running and Sleeping Threads by environment]** frame은 데이터베이스에 대한 활성 연결과 절전 모드 연결을 모두 표시합니다. 느린 쿼리가 절전 모드로 전환된 데이터베이스에 대한 연결이 있는 경우 절전 모드 연결이 있습니다. 대기 중인 연결은 잠긴 행 또는 테이블에 의해 차단되는 데이터베이스 쿼리일 수 있습니다. 이러한 수면 연결은 또한 PHP 작업자 연결을 보유하고 있습니다.

## [!UICONTROL MySQL mem used by node]

![노드에서 사용하는 MySQL 메모리](../../assets/tools/observation-for-adobe-commerce/mysql-tab-23.jpg)

다음 **[!UICONTROL MySQL mem used by node]** frame은 MySQL의 노드 메모리 사용을 보여 줍니다. 더 큰 사이트에서, 이 프레임은 사용된 GBs의 메모리를 갖는 연속 막대일 수 있다.

## [!UICONTROL Database mysql-slow.log]

![데이터베이스 mysql-slow.log](../../assets/tools/observation-for-adobe-commerce/mysql-tab-24.jpg)

다음 **[!UICONTROL Database mysql-slow.log]** frame은에 있는 쿼리 문 유형을 표시합니다. `mysql-slow.log` 파일을 선택한 기간에 걸쳐 만듭니다.
