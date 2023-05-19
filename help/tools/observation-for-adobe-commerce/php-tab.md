---
title: 다음 [!UICONTROL PHP] 탭
description: 에 대해 알아보기 [!UICONTROL PHP] 탭 / [!DNL Observation for Adobe Commerce].
exl-id: 0989a7f5-75b0-4fb5-ac5e-2618603bf548
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# 다음 [!UICONTROL PHP] 탭

다음 **PHP** 탭은 PHP 문제에 대한 심층적인 분석을 제공하기 위해 PHP 프로세스 문제를 보여줍니다.

## [!UICONTROL PHP active process details]

![PHP 활성 프로세스 세부 정보](../../assets/tools/php-active-process-details.jpg)

다음 **[!UICONTROL PHP active process details]** frame은 선택한 기간에 걸쳐 php-fpm을 포함한 PHP 프로세스를 보여 줍니다.

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![PHP 프로세스 로드](../../assets/tools/php-process-load.jpg)

다음 **[!UICONTROL PHP process load (# of PHP processes and % of CPU load)]** frame은 선택한 기간 동안 PHP-FPM 프로세스에서 CPU 로드를 보여 줍니다.

## [!UICONTROL PHP Memory detail]

![PHP 메모리 세부 사항](../../assets/tools/php-memory-detail.jpg)

다음 **[!UICONTROL PHP Memory detail]** frame은 선택한 기간에 걸쳐 PHP 프로세스의 메모리 사용을 보여줍니다.

## [!UICONTROL PHP CPU Utilization]

![PHP CPU 사용률](../../assets/tools/php-cpu-utilization.jpg)

다음 **[!UICONTROL PHP CPU Utilization]** frame은 선택한 기간 동안 PHP 프로세스의 CPU 사용률을 보여 줍니다.

## [!UICONTROL PHP Process states]

![PHP 프로세스 상태](../../assets/tools/php-process-states-image-1.jpg)

다음 **[!UICONTROL PHP Process states]** frame은 선택한 기간에 걸쳐 PHP 프로세스 상태를 표시합니다. PHP 프로세스가 종료되고 다시 시작하면 표시됩니다. 다시 시작하지 않는 종료된 PHP 프로세스에 주의하십시오.

* &#39;%NOTICE: 종료 중 ...%&#39;)을(를) &#39;php_term&#39;으로 설정합니다.
* &#39;% 알림: 종료하는 중입니다. 안녕히 가세요!%&#39;)를 &#39;php_exit&#39;로 변환
* &#39;% 알림: fpm이 실행 중입니다, pid%&#39;)을(를) &#39;fpm_start&#39;로 함
* &#39;%NOTICE: connections%&#39;)를 &#39;php_ready&#39;로 처리

## [!UICONTROL PHP Errors]

![PHP 오류](../../assets/tools/php-errors-image-1.jpg)

다음 **[!UICONTROL PHP Errors]** frame은 선택한 기간 전체에 걸쳐 PHP 작업자 오류 수를 보여 줍니다. 구문 분석되어 표시되는 오류 메시지는 다음과 같습니다.

* &#39;%worker_connections가 &#39;worker&#39;로 충분하지 않음(%)
* &#39;%PHP 치명적인 오류: 메모리 크기가 허용되었습니다!%&#39;)를 &#39;mem_size&#39;로
* &#39;%exited on signal 11 (SIGSEGV)%&#39;) as &#39;sig_11&#39;
* &#39;%가 신호 7(SIGBUS)%&#39;)에서 &#39;sig_7&#39;(으)로 종료됨
* &#39;%increase pm.start_servers%&#39;) as &#39;pmstart_serv&#39;
* &#39;%max_children%&#39;)을(를) &#39;max_children_cnt&#39;로
* &#39;%PHP 심각한 오류: &#39;%&#39;(으)로 허용된 메모리 크기(mem_exhst_coun&#39;)
* &#39;%pool%&#39;에 대한 메모리를 할당할 수 없습니다.) &#39;opc_mem_count&#39;
* &#39;%Warning interned string buffer overflow%&#39;)를 &#39;opc_str_buf&#39;로 지정합니다.
* &#39;%Illegal string offsetl%&#39;)을(를) &#39;opc_sv_comments&#39;로 지정했습니다.
* &#39;%PHP 치명적인 오류: RedisException: connection%&#39;에서 &#39;php_exc&#39;(으)로 표시되는 읽기 오류

## [!UICONTROL PHP processes count]

![PHP 프로세스 수](../../assets/tools/php-processes-count.jpg)

다음 **[!UICONTROL PHP processes count]** frame은 선택한 기간에 걸쳐 PHP 프로세스 수를 보여 줍니다.

## [!UICONTROL Database Errors]

![데이터베이스 오류](../../assets/tools/php-tab-database-errors.jpg)

다음 **[!UICONTROL Database Errors]** 프레임에는 선택한 기간에 걸친 데이터베이스 오류가 표시됩니다. 구문 분석된 오류에는 다음이 포함됩니다.

* &#39;%임시 테이블에 할당된 메모리 크기가 &#39;temp_tbl_buff_pool&#39;인 innodb_buffer_pool_size%의 20%보다 큽니다.
* &#39;%\[ERROR\] WSREP: rbr 쓰기 실패%&#39;)를 &#39;rbr_write_fail&#39;로 함
* &#39;%mysqld: Disk full%&#39;)이(가) &#39;disk_full&#39;인 경우
* &#39;%Error number 28%&#39;)을(를) &#39;err_28&#39;(으)로
* &#39;%rollback%&#39;)을 &#39;rollback&#39;으로
* &#39;%Foreign KEY 제약 조건이 테이블%&#39;에 대해 실패했습니다.) &#39;foreign_key_constraint&#39;(으)로
* &#39;%Error_code: 1114%&#39;)을(를) &#39;sql_1114_full&#39;로 함
* &#39;%중요: SQLSTATE[HY000] [2006] MySQL Server가 없어짐(%))을 &#39;sql_gone&#39;(으)로
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
* &#39;%SQLSTATE[42000]: 구문 오류 또는 액세스 위반:%&#39;) as &#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]: 카디널리티 위반:%&#39;)을 &#39;sql_1241&#39;로 지정
* &#39;%SQLSTATE[22003]:%&#39;)를 &#39;sql_22003&#39;로
* &#39;%SQLSTATE[HY000] [9000] IP 주소(%&#39;)를 &#39;sql_9000&#39;으로 설정한 클라이언트
* &#39;%SQLSTATE[HY000]: 일반 오류: 2014%&#39;)가 &#39;sql_2014&#39;인 경우
* &#39;%1927 연결이 끊어졌습니다.%&#39;) &#39;sql_1927&#39;(으)로
* &#39;%1062 \[ERROR\] InnoDB:%&#39;)이(가) &#39;sql_1062_e&#39;인 경우
* &#39;%[참고] WSREP: 디스크로 메모리 맵을 플러시하는 중...%) &quot;mem_map_flush&quot;로 설정
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
* &#39;%InnoDB: 오류(중복 키)%&#39;)가 &#39;innodb_dup_key&#39;입니다.

## [!UICONTROL Database traces]

![데이터베이스 추적](../../assets/tools/php-tab-database-traces.jpg)

다음 **[!UICONTROL Database traces]** 프레임에는 데이터베이스 추적 정보가 표시됩니다. 이 프레임은 선택한 타임라인에 대한 APM 트랜잭션 요약 보기에 맞춰 조정됩니다.

## [!UICONTROL Database mysql-slow.log]

![데이터베이스 mysql-slow.log](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

다음 **[!UICONTROL Database mysql-slow.log]** frame은에 있는 쿼리 문 유형을 표시합니다. `mysql-slow.log` 파일을 선택한 기간에 걸쳐 만듭니다.
