---
title: 데이터베이스 프로파일러 구성
description: 데이터베이스 프로파일러에 대한 출력을 구성하는 방법에 대한 예를 참조하십시오.
contributor_name: Atish Goswami
contributor_link: http://atishgoswami.com
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# 데이터베이스 프로파일러 구성

Commerce 데이터베이스 프로파일러는 각 쿼리의 시간 및 적용된 매개 변수를 포함하여 페이지에 구현된 모든 쿼리를 표시합니다.

## 1단계: 배포 구성 수정

수정 `<magento_root>/app/etc/env.php` 에 다음 참조를 추가하려면 [데이터베이스 프로파일러 클래스](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

예는 다음과 같습니다.

```php?start_inline=1
 'db' =>
  array (
    'table_prefix' => '',
    'connection' =>
    array (
      'default' =>
      array (
        'host' => 'localhost',
        'dbname' => 'magento',
        'username' => 'magento',
        'password' => 'magento',
        'model' => 'mysql4',
        'engine' => 'innodb',
        'initStatements' => 'SET NAMES utf8;',
        'active' => '1',
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
      ),
    ),
  ),
```

## 2단계: 출력 구성

Commerce 응용 프로그램 부트스트랩 파일에서 출력을 구성합니다. 아마 `<magento_root>/pub/index.php` 웹 서버 가상 호스트 구성에 있을 수도 있습니다.

다음 예제에서는 3열 테이블의 결과를 표시합니다.

- 총 시간(페이지에서 모든 쿼리를 실행하는 총 시간 표시)
- SQL(모든 SQL 쿼리를 표시합니다.) 행 헤더에 쿼리 개수가 표시됩니다.)
- 쿼리 매개 변수(각 SQL 쿼리에 대한 매개 변수를 표시합니다.)

출력을 구성하려면 다음에 다음을 추가합니다. `$bootstrap->run($app);` 부트스트랩 파일의 줄:

```php?start_inline=1
/** @var \Magento\Framework\App\ResourceConnection $res */
$res = \Magento\Framework\App\ObjectManager::getInstance()->get('Magento\Framework\App\ResourceConnection');
/** @var Magento\Framework\DB\Profiler $profiler */
$profiler = $res->getConnection('read')->getProfiler();
echo "<table cellpadding='0' cellspacing='0' border='1'>";
echo "<tr>";
echo "<th>Time <br/>[Total Time: ".$profiler->getTotalElapsedSecs()." secs]</th>";
echo "<th>SQL [Total: ".$profiler->getTotalNumQueries()." queries]</th>";
echo "<th>Query Params</th>";
echo "</tr>";
foreach ($profiler->getQueryProfiles() as $query) {
    /** @var Zend_Db_Profiler_Query $query*/
    echo '<tr>';
    echo '<td>', number_format(1000 * $query->getElapsedSecs(), 2), 'ms', '</td>';
    echo '<td>', $query->getQuery(), '</td>';
    echo '<td>', json_encode($query->getQueryParams()), '</td>';
    echo '</tr>';
}
echo "</table>";
```

## 3단계: 결과 보기

결과를 보려면 상점 또는 관리자로 이동합니다. 샘플은

![예제 데이터베이스 프로파일러 결과](../../assets/configuration/db-profiler-results.png)
