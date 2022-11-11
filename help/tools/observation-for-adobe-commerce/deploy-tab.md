---
title: "다음 [!UICONTROL Deploy] tab"
description: 에 대해 알아보기 [!UICONTROL Deploy] 탭 [!DNL Observation for Adobe Commerce].
source-git-commit: b95a35ee64cd8e844a51a9ff699eceb9c3a9266c
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 0%

---

# 다음 [!UICONTROL Deploy] 탭

이 탭은 배포 문제의 문제와 원인을 빠르게 격리하기 위한 것입니다.

## [!UICONTROL Deploy log Deployment Troubleshooter]

![로그 배포 문제 해결사 배포](../../assets/tools/observation-for-adobe-commerce/deploy-tab-1.jpg)

다음 **[!UICONTROL Deploy log Deployment Troubleshooter]** 프레임은 선택한 시간대에서 발생한 배포 로그 이벤트 수를 보여줍니다. 배포 활동에 대한 요약 보기를 제공하고 개수별로 배포의 복잡성을 판별하기 위한 것입니다. 로깅된 메시지가 많을수록 일반적으로 배포가 더 복잡합니다.

## [!UICONTROL Deploy State]

![배포 상태](../../assets/tools/observation-for-adobe-commerce/deploy-tab-2.jpg)

다음 **[!UICONTROL Deploy State]** 프레임은 선택한 기간에 발생한 배포 이벤트를 보여줍니다. 이 프레임에 대한 파서가 다음과 같은 특정 신호를 찾고 있습니다.

* &#39;%알림: generate command%&#39;를 &#39;start_gen&#39;으로 시작하는 중
* &#39;%git apply /app/vendor/magento/ece-tools/patches%&#39;(apply_patches)
* &#39;%설정 플래그: .static_content_deploy%&#39;) as &#39;SCD&#39;
* &#39;%알림: &#39;generate command completed%&#39;) as &#39;gen_compl&#39;
* &#39;%알림: 배포를 시작합니다.%&#39;) &#39;start_deploy&#39;
* &#39;%알림: 배포 완료%)(deploy_compl&#39;)
* &#39;%알림: 배포 후 시작.%&#39;) &#39;start_pdeploy&#39;
* &#39;%알림: 배포 후 완료%) &#39;배포&#39;로
* &#39;%deploy-complete%&#39;) as &#39;cl_deploy_compl&#39;

## [!UICONTROL Deploy Log Detail]

![배포 로그 세부 정보](../../assets/tools/observation-for-adobe-commerce/deploy-tab-3.jpg)

다음 **[!UICONTROL Deploy Log Detail]** 프레임은 선택한 기간 동안 발생한 배포 로그 메시지 요약 정보를 보여줍니다. 프레임이 배포 로그에서 다음 문자열에 대한 구문 분석을 수행합니다.

* &#39;%알림: 배포를 시작합니다.%&#39;) &#39;start_play&#39;
* &#39;%정보: 시나리오 시작: scenario/deploy.xml%&#39;) as &#39;start_scenario&#39;
* &#39;%알림: &#39;strt_predply&#39;로 &#39;사전 배포%&#39; 시작
* &#39;% 정보: 패치 로그 파일%)을 &#39;rstr_ptch_log&#39;로 복원
* &#39;%정보: 캐시 구성을 업데이트하는 중입니다.%&#39;) &#39;updt_cach_config&#39; 사용
* &#39;%정보: &#39;redis_sec_conn_set&#39;으로 Redis 슬레이브 연결% 설정
* &#39;%정보: &#39;scd_build_hk&#39;(빌드 후크, 이전 컨텐츠% 정리) 중에 정적 콘텐츠 배포가 수행되었습니다.
* &#39;%정보: &#39;clr_pub_static&#39;(pub/static%)으로 지우기
* &#39;%NFO: &#39;clr_redis_cach&#39;로 redis 캐시 지우기:%)
* &#39;%정보: var/cache directory%&#39;를 &#39;clr_var_cach&#39;로 지우고 있습니다.
* &#39;% 알림: 유지 관리 모드%)를 &#39;enable_maint_mode&#39;로 사용
* &#39;%정보: cron%)를 &#39;disable_cron&#39;으로 사용 안 함
* &#39;%정보: &#39;kill_cron_try&#39;로 실행 중인 cron job과 소비자 프로세스%) 제거
* &#39;%정보: 실행 중인 Magento 크론 및 소비자 프로세스를 찾을 수 없습니다.%)(&#39;no_cron_fnd&#39;,
* %알림: &#39;validate_config&#39;로 구성% 유효성 검사 중
* &#39;%관리자 데이터는 초기 설치 중에 관리자 사용자를 만들려면 필수 &#39;%no_admin&#39;)으로 만듭니다.
* &#39;%recommended PHP 버전은 constraint%&#39;을 &#39;php_ver_constraint&#39;로 충족했습니다.
* &#39;%경고: 제공된 제안:%&#39;)을 &#39;fix_config_sug&#39;로 사용하여 구성을 수정합니다.
* &#39;%경고: [2003년] 오류 보고에 대한 디렉터리 중첩 수준 값이 구성되지 않았습니다.%&#39;) as&#39;nest_err_reporting&#39;
* &#39;%알림: 유효성 검사 종료%) &#39;end_validation&#39;로
* &#39;%알림: 업데이트를 시작하는 중입니다.%&#39;) &#39;start_update&#39;
* &#39;%정보: env.php를 업데이트하는 중입니다.%&#39;) &#39;update_php_env&#39;
* &#39;%정보: env.php DB 연결 구성을 업데이트하는 중입니다.%&#39;) &#39;update_php_env_db&#39;
* &#39;%정보: env.php AMQP 구성%&#39;를 &#39;update_php_env_amqp&#39;로 업데이트하는 중
* &#39;%정보: 검색 엔진 설정: &#39;set_elastic7&#39;으로 변경됨
* &#39;%elastic_ver_EOL&#39;으로 &#39;%elastic Search 6.5.4가 EOL%&#39;을 전달했습니다.
* &#39;%정보: 검색 엔진 설정: elasticsearch6%&#39;) &#39;set_elastic6&#39;
* &#39;%정보: &#39;update_url&#39;로 보안 및 비보안 URL%&#39; 업데이트
* &#39;%정보: 설치 업그레이드를 실행하고 있습니다.%&#39;) &#39;setup_upgrade_run&#39;
* &#39;%정보: 배포 후 후크를 사용하도록 설정되었습니다. &#39;post_hook_enabled&#39;로 Cron 사용, 캐시 정리 및 사전 경고 작업이 연기됨%)
* &#39;%알림: 유지 관리 모드가 비활성화됩니다.%&#39;) &#39;main_mode_disabled&#39;
* &#39;%정보: &#39;scenario_finished&#39;)로 &#39;scenario_finished&#39;
* &#39;%경고: 명령 유지 관리:오류가 발생하여 사용을 마쳤습니다. &#39;enable_maintenance_fail&#39;(maintenance flag file%&#39;) 작성
* &#39;%MySQL Server가 &#39;MySQL_has_gone_away&#39;로 제거됨&#39;

## [!UICONTROL Post Deploy Log Detail]

![배포 로그 세부 정보 게시](../../assets/tools/observation-for-adobe-commerce/deploy-tab-4.jpg)

다음 **[!UICONTROL Post Deploy Log Detail]** 프레임은 선택한 시간대에 발생한 배포 후 로그 세부 정보를 보여줍니다. 이 프레임은 다음 문자열을 포함하는 특정 로그 메시지에 중점을 둡니다.

* &#39;%Disabled_maint_mode&#39;(&#39;%Disabled maintenance mode%&#39;)로 사용 안 함
* &#39;%정보: 시나리오 시작: scenario/post-deploy.xml%&#39;) as &#39;start_pstdply_scenario&#39;
* &#39;% 알림: &#39;val_config&#39;로 구성% 유효성 검사 중
* &#39;% 알림: &#39;end_val_config&#39;로서 유효성 검사 종료%&#39;)
* &#39;%정보: cron%&#39;을 &#39;cron_enabled&#39;로 사용
* &#39;% 정보: 중요한 파일의 백업을 만듭니다.%&#39;) &#39;file_backup&#39;
* &#39;%정보: &#39;file_backup_success&#39;로 성공적으로 백업% 작성
* &#39;%정보: 페이지 준비 시작(%) &#39;pg_aunup_start&#39;로
* &#39;%정보: &#39;abled_up_pg&#39;로 페이지 준비:%&#39;)
* &#39;%오류: 준비 실패:%) &#39;warning_up_pg_err&#39;로
* &#39;% 정보: &#39;scenario_finished&#39;)로 &#39;scenario_finished&#39;

## [!UICONTROL Cloud Log Detail]

![클라우드 로그 세부 정보](../../assets/tools/observation-for-adobe-commerce/deploy-tab-5.jpg)

다음 **[!UICONTROL Cloud Log Detail]** 프레임은 선택한 일정 동안 발생한 클라우드 로그 세부 사항을 보여줍니다. 다음 문자열은 구문 분석되고 아래의 &#39;AS&#39; 레이블로 반환됩니다.

* &#39;%DEBUG: /bin/bash -c &quot;set -o pipeffail; php .&#39;start_update&#39;로 &#39;bin/magento setup:upgrade%&#39;)
* &#39;%스키마 만들기/업데이트:%&#39;)을 &#39;schema_updates&#39;로 사용
* &#39;%가져올 항목이 없습니다.%&#39;) &#39;mod_import_finish&#39;
* &#39;%알림: 업데이트 종료.%&#39;) &#39;update_finished&#39;
* &#39;%DEBUG: 실행 단계: deploy-static-content%&#39;) as &#39;scd_run&#39;
* &#39;% 알림: 정적 콘텐츠 배포를 건너뜁니다. 주문형 SCD가 활성화되어 있습니다.%&#39;) &#39;scd_ondemand&#39;
* &#39;%정보: 지우기%&#39;) as&#39;clr_dirs&#39;
* &#39;%DEBUG: &quot;deploy-static-content&quot; finished%&#39;) as &#39;scd_finished&#39;
* &#39;%알림: 정적 콘텐츠 압축을 건너뜁니다. 주문형 SCD가 활성화되어 있습니다.%&#39;) &#39;scd_compression_run&#39;,
* &#39;%정보: var/cache directory%&#39;를 &#39;clr_var_cach&#39;로 지우고 있습니다.
* &#39;%DEBUG: &#39;compress-static-content&quot; finished%&#39;) 단계 &#39;scd_compression_finished&#39;
* &#39;%DEBUG: 실행 단계: deploy_complete%&#39;) &#39;deploy_finished&#39;
* &#39;%정보: 배포 후 후크를 사용하도록 설정되었습니다. Cron 사용, 캐시 청소 및 준비 작업이 배포 후 단계로 연기됩니다.%&#39;) &#39;Post_deploy_hook_enabled&#39;
* &#39;%알림: 유지 관리 모드가 비활성화됩니다.%&#39;) &#39;main_mode_disabled&#39;
* &#39;%정보: &#39;scenario_finished&#39;)로 &#39;scenario_finished&#39;
* &#39;post_deploy_start&#39;(%post-deploy.xml%&#39;)
* &#39;%알림: &#39;validate_config&#39;로 구성% 유효성 검사 중
* &#39;%경고: [2003년] 오류 보고에 대한 디렉터리 중첩 수준 값이 구성되지 않았습니다.%&#39;) as&#39;nest_err_reporting&#39;
* &#39;%알림: 유효성 검사 종료%) &#39;end_validation&#39;로
* &#39;%정보: Enable cron%&#39;)를 &#39;enable_cron&#39;으로 사용
* &#39;%정보: &#39;create_backup&#39;으로 중요한 파일 백업 만들기%)
* &#39;%DEBUG: &quot;backup&quot; finished%&quot;) &#39;backup_finished&#39; 단계
* &#39;%정보: 페이지 준비 시작(%)) &#39;Untenup_start&#39;로
* &#39;%오류: 준비 실패:%) &#39;warning_up_fail&#39;로
* &#39;%DEBUG: &quot;Warming-up&quot; finished%&quot;)를 &#39;Warming_finished&#39;로 설정합니다.
* &#39;% 디버그: 단계 &quot;time-to-first-byte&quot; finished%&#39;) as &#39;ttfb_finished&#39;
* &#39;%정보: &#39;post_deploy_finished&#39;로서 시나리오(%)&#39;)
* &#39;%DEBUG: 실행 단계: pre_build%) as &#39;run_pre-build&#39;
* &#39;%DEBUG: 플래그 .static_content_deploy가 이미 삭제됨%)(&#39;scd_flag_del&#39;)
* &#39;%DEBUG: &quot;pre-build&quot; finished%&quot;) as &#39;pre-build_completed&#39;
* &#39;%알림: &#39;apply_patches&#39;로 패치 적용
* &#39;%s&#39;이(가) &#39;patches_applied&#39;로 적용되었습니다.
* &#39;%DEBUG: &#39;apply_patches_complete&#39;로 &quot;apply-patches&quot; finished%&#39; 단계
* &#39;quick_strategy_deploy&#39;로 &#39;%Deploy(%)&#39;
* &#39;% 알림: &#39;di_compilation_start&#39;로 ID compilation%&#39;를 실행 중입니다.
* &#39;%알림: &#39;di_compilation_finished&#39;로 ID compilation% 실행 종료&#39;
* &#39;%알림: &#39;gen_frsh_static_content&#39;로 새 정적 콘텐츠 생성
* `%magento 설정:static-content:deploy%&#39;) &#39;scd_executing&#39;
* &#39;%알림: &#39;gen_frsh_static_cont_finished&#39;로 새 정적 콘텐츠 생성 종료&#39;
* &#39;%정보: 시나리오 시작: scenario/build/transfer.xml%&#39;) as &#39;start_transferxml&#39;
* &#39;%정보: 실행 중인 cron jobs%) &#39;kill_crons&#39;로 종료하려고 함
* &#39;%정보: &#39;clear_redis_cache&#39;로 redis 캐시 지우기:%)
* &#39;%정보: db가 존재하는지 및 hastable%)를 &#39;db_check&#39;로 확인하는 중
* &#39;%경고: [2010년] Elasticsearch 서비스는 인프라 계층에 설치되지만 검색 엔진으로 사용되지 않습니다.%&#39;) as&#39;es_not_used&#39;
* &#39;%알림: 업데이트를 시작하는 중입니다.%&#39;) &#39;starting_update&#39;
* &#39;%정보: 검색 엔진 설정: mysql%&#39;) &#39;mysql_search&#39;
* &#39;%SQLSTATE[HY000] [2006년] &#39;mysql_gone&#39;으로 사용 중인 MySQL Server가 &quot;%&quot;)

## [!UICONTROL Count of modules imported during deploy]

![배포 중에 가져온 모듈 수](../../assets/tools/observation-for-adobe-commerce/deploy-tab-6.jpg)

다음 **[!UICONTROL Count of modules imported during deploy]** 프레임은 선택한 시간대에 대해 배포 중에 가져온 모듈 수를 보여줍니다.

## [!UICONTROL Deployed module list]

![배포된 모듈 목록](../../assets/tools/observation-for-adobe-commerce/deploy-tab-7.jpg)

다음 **[!UICONTROL Deployed module list]** 프레임은 선택한 시간대에 배포된 모듈을 표시합니다.

