---
title: '"다음 [!UICONTROL PHP] tab"'
description: 에 대해 알아보기 [!UICONTROL PHP] [!DNS Observation for Adobe Commerce] 탭.
source-git-commit: f71fc3b2a66a4cc0b0d7865138184135e4a874e0
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# 다음 [!UICONTROL PHP] 탭

다음 **PHP** 탭에는 PHP 문제에 대한 심층적인 분석을 제공하기 위한 PHP 프로세스 문제가 표시됩니다.

## [!UICONTROL PHP active process details]

![PHP 활성 프로세스 세부 정보](../../assets/tools/php-active-process-details.jpg)

다음 **[!UICONTROL PHP active process details]** 프레임은 선택한 기간에 대해 php-fpm을 포함한 PHP 프로세스를 표시합니다.

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![PHP 프로세스 로드](../../assets/tools/php-process-load.jpg)

이 프레임은 선택한 기간의 PHP-FPM 프로세스에서 CPU 로드를 보여 줍니다.

## [!UICONTROL PHP Memory detail]

![PHP 메모리 세부 사항](../../assets/tools/php-memory-detail.jpg)

다음 **[!UICONTROL PHP Memory detail]** 프레임은 선택한 기간 동안 PHP 프로세스의 메모리 사용을 보여 줍니다.

## [!UICONTROL PHP CPU Utilization]

![PHP CPU 사용률](../../assets/tools/php-cpu-utilization.jpg)

다음 **[!UICONTROL PHP CPU Utilization]** 프레임은 선택한 기간 동안의 PHP 프로세스의 CPU % 활용률을 보여줍니다.

## [!UICONTROL PHP Process states]

![PHP 프로세스 상태](../../assets/tools/php-process-states-image-1.jpg)

다음 **[!UICONTROL PHP Process states]** 프레임은 선택한 기간에 대한 PHP 프로세스 상태를 표시합니다. PHP 프로세스가 종료되고 다시 시작될 때 표시됩니다. 다시 시작을 표시하지 않는 PHP 프로세스가 종료되었습니다.

* &#39;%알림: 종료 중...%&#39;) &#39;php_term&#39;
* &#39;% 알림: 나가세요, 안녕!%&#39;) &#39;php_exit&#39;
* &#39;% 알림: fpm이 실행 중이면 pid%&#39;)가 &#39;fpm_start&#39;로 설정됩니다.
* &#39;%알림: &#39;php_ready&#39;로 &#39;connections%&#39;를 처리할 준비가 되었습니다.

## [!UICONTROL PHP Errors]

![PHP 오류](../../assets/tools/php-errors-image-1.jpg)

다음 **[!UICONTROL PHP Errors]** 프레임은 선택한 기간 동안의 PHP 작업자 오류 수를 표시합니다. 구문 분석되고 표시되는 오류 메시지는 다음과 같습니다.

* &#39;%worker_connections%&#39;이(가) &#39;worker&#39;로 부족합니다.
* &#39;%PHP 오류: 허용되는 메모리 크기입니다!%&#39;) &#39;mem_size&#39;
* &#39;%s이(가) 신호 11(SIGSEGV)%&#39;에서 &#39;sig_11&#39;으로 종료되었습니다.
* &#39;%s이(가) 신호 7(SIGBUS)%&#39;)에서 &#39;sig_7&#39;으로 종료되었습니다.
* &#39;%increase pm.start_servers%&#39;) as &#39;pmstart_serv&#39;
* &#39;%max_children%&#39;) as &#39;max_children_cnt&#39;
* &#39;%PHP 오류: &#39;mem_exhst_coupn&#39;으로 허용되는 메모리 크기(%)
* &#39;%opc_mem_count&#39;로서 &#39;pool%&#39;에 메모리를 할당할 수 없습니다.&#39;
* &#39;%Warning Interned 문자열 버퍼 오버플로%&#39;)(&#39;opc_str_buf&#39;)
* &#39;%opc_sv_comments&#39;(으)로 잘못된 문자열 offsetl%&#39;
* &#39;%PHP 오류: 발견되지 않은 RedisException: &#39;php_exc&#39;로 &#39;connection%&#39;에 대한 읽기 오류

## [!UICONTROL PHP processes count]

![PHP 프로세스 수](../../assets/tools/php-processes-count.jpg)

다음 **[!UICONTROL PHP processes count]** 프레임은 선택한 기간에 걸쳐 PHP 프로세스의 수를 표시합니다.

## [!UICONTROL Database Errors]

![데이터베이스 오류](../../assets/tools/php-tab-database-errors.jpg)

다음 **[!UICONTROL Database Errors]** 프레임은 선택한 기간에 대한 데이터베이스 오류를 보여줍니다. 구문 분석된 오류는 다음과 같습니다.

* &#39;%임시 테이블에 할당된 메모리 크기가 innodb_buffer_pool_size%&#39;의 20%를 넘습니다.) &#39;temp_tbl_buff_pool&#39;
* &#39;%\[오류\] WSREP: rbr write fail%&#39;) &#39;rbr_write_fail&#39;
* &#39;%myqld: 디스크 전체%)(&#39;disk_full&#39;)
* &#39;%오류 번호 28%&#39;)이 &#39;err_28&#39;입니다.
* &#39;%rollback%&#39;) &#39;rollback&#39;으로 사용
* &#39;%Foreign key 제약 조건이 table%&#39;에 대해 실패합니다.) &#39;foreign_key_constraint&#39;
* &#39;%Error_code: 1114%) 로서의 &#39;sql_1114_full&#39;
* &#39;%중요: SQLSTATE[HY000] [2006년] MySQL 서버가 &#39;sql_gone&#39;으로 사라짐%)
* &#39;%SQLSTATE[HY000] [1040년] &#39;sql_1040&#39;에 너무 많은 연결%&#39;)
* &#39;%중요: SQLSTATE[HY000] [2002년]%&#39;) &#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%&#39;) &#39;sql_1047&#39;
* &#39;%[경고] &#39;aborted_conn&#39;으로 &#39;aborted connection%&#39;)
* &#39;%SQLSTATE[23000]: 무결성 제약 조건 위반:%&#39;) &#39;sql_23000&#39;
* &#39;%1205 잠금 대기 시간 초과%&#39;) as &#39;sql_1205&#39;
* &#39;%SQLSTATE[HY000] [1049년] 알 수 없는 데이터베이스%) as &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]: 기본 테이블 또는 뷰를 찾을 수 없음:%) as &#39;sql_42S02&#39;
* &#39;%일반 오류: 1114%) 로서의 &#39;sql_1114&#39;
* &#39;%SQLSTATE[40001]%&#39;) &#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22]: 열을 찾을 수 없음: 1054 알 수 없는 열%) as &#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000]: 구문 오류 또는 액세스 위반:%) as &#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]: 카디널리티 위반:%) as &#39;sql_1241&#39;
* &#39;%SQLSTATE[22003]:%&#39;) &#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000년] &#39;sql_9000&#39;(IP 주소%)이 있는 클라이언트
* &#39;%SQLSTATE[HY000]: 일반 오류: (2014%) &#39;sql_2014&#39;)
* &#39;%1927 연결이 &#39;%&#39;)(으)로 &#39;sql_1927&#39;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) as &#39;sql_1062_e&#39;
* &#39;%[참고] WSREP: 메모리 맵을 디스크에 플러싱..%&#39;) &#39;mem_map_flush&#39;
* &#39;%Internal MariaDB 오류 코드: 1146%) 로서의 &#39;sql_1146&#39;
* &#39;%Internal MariaDB 오류 코드: &#39;sql_1062&#39;(으)로 1062%) ・ &#39;%1062 [경고] InnoDB:%) as &#39;sql_1062_w&#39;
* &#39;%Internal MariaDB 오류 코드: 1064%) 로서의 &#39;sql_1064&#39;
* &#39;%InnoDB: &#39;assertion_err&#39;(% 파일의 검증 실패)
* &#39;%mysqld_safe 현재 실행 중인 프로세스 수: 0%&#39;) &#39;mysql_oom&#39;
* &#39;%\[ERROR\] myqld는 signal%&#39;)를 &#39;mysql_sigterm&#39;으로 지정했습니다.
* &#39;%1452&#39;)을 &#39;sql_1452&#39;로 추가할 수 없습니다.
* &#39;%ERROR 1698%&#39;) as &#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000]: 일반 오류: 3%&#39;) &#39;cnt_wrt_tmp&#39;
* &#39;%일반 오류: 1%&#39;) &#39;sql_syntax&#39;
* &#39;%42S22%&#39;) as &#39;sql_42S22&#39;
* &#39;%InnoDB: &#39;innodb_dup_key&#39;로서 오류(중복 키)%&#39;)

## [!UICONTROL Database traces]

![데이터베이스 추적](../../assets/tools/php-tab-database-traces.jpg)

다음 **[!UICONTROL Database traces]** 프레임에는 데이터베이스 추적 정보가 표시됩니다. 이 프레임은 선택한 타임라인에 대한 APM 트랜잭션 요약 보기에 맞춥니다.

## [!UICONTROL Database mysql-slow.log]

![데이터베이스 mysql-slow.log](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

다음 **[!UICONTROL Database mysql-slow.log]** 프레임에는 `mysql-slow.log` 선택한 기간에 파일을 작성합니다.
