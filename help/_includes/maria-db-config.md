---
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---
# MariaDB 구성 설정

MariaDB 10.4 및 10.6에서 리인덱싱하는 것은 이전 MariaDB 또는 MySQL 버전에 비해 시간이 더 걸립니다. 리인덱싱을 빠르게 수행하려면 다음 MariaDB 구성 매개 변수를 설정하는 것이 좋습니다.

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/docs/server/server-management/variables-and-modes/server-system-variables#optimizer_use_condition_selectivity)

MariaDB 10.6으로 업그레이드한 후 인덱싱과 관련이 없는 성능 저하가 발생하는 경우 [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) 설정을 사용하도록 설정하는 것이 좋습니다. 예: `--query-cache-type=ON`.

클라우드 인프라 프로젝트에서 Adobe Commerce을 업그레이드하기 전에 MariaDB를 업그레이드해야 할 수도 있습니다([MariaDB 업그레이드 모범 사례](../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md) 참조).

For example:

* Adobe Commerce 2.4.6(MariaDB 버전 10.5.1 이상)
* Adobe Commerce 2.3.5(MariaDB 버전 10.3 이하)

이러한 권장 사항 외에 다음 매개 변수를 구성하는 방법에 대해서는 데이터베이스 관리자에게 문의하십시오.

>[!NOTE]
>
>이러한 설정은 온-프레미스 배포에서만 사용할 수 있습니다. 클라우드 인프라의 Adobe Commerce 고객은 이러한 설정에 액세스할 수 없습니다.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
