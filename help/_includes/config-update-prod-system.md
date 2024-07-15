---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# 프로덕션 시스템 업데이트

**프로덕션 시스템을 업데이트하려면**:

1. 운영 시스템에 파일 시스템 소유자로 로그인합니다.
1. 애플리케이션 루트로 변경하고 유지 관리 모드를 활성화합니다.

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   IP 주소 허용 목록 설정 기능과 같은 추가 옵션을 보려면 [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md)을(를) 참조하십시오.

1. 다음과 같이 `app/etc/env.php`에서 `cron_run`을(를) `false`(으)로 설정하여 실행 중인 큐 작업자를 중지합니다.

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. 구성을 업데이트합니다.

   ```bash
   bin/magento app:config:import
   ```

1. 마지막으로 모든 활성 소비자 프로세스를 `kill`합니다.

   ```bash
   kill <PID>
   ```

   여기서 `PID`은(는) 삭제할 프로세스 ID입니다. 예:

   ```bash
   kill 1234
   ```

1. 소스 제어에서 코드를 가져옵니다.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. 구성을 업데이트합니다.

   ```bash
   bin/magento app:config:import
   ```

1. 캐시를 정리합니다.

   ```bash
   bin/magento cache:clean
   ```

1. 유지 관리 모드를 종료합니다.

   ```bash
   bin/magento maintenance:disable
   ```
