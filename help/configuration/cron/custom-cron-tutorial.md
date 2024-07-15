---
title: 사용자 정의 cron 작업 및 cron 그룹 구성(튜토리얼)
description: 이 단계별 자습서를 사용하여 사용자 지정 cron 작업을 만듭니다.
exl-id: d8efcafc-3ae1-4c2d-a8ad-4a806fb48932
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 0%

---

# 사용자 정의 cron 작업 구성

이 단계별 자습서에서는 샘플 모듈에서 사용자 지정 cron 작업 및 선택적으로 cron 그룹을 만드는 방법을 보여줍니다. 이미 있는 모듈을 사용하거나 [`magento2-samples` 저장소][samples]의 샘플 모듈을 사용할 수 있습니다.

cron 작업을 실행하면 cron 작업의 이름이 `custom_cron`인 행이 `cron_schedule` 테이블에 추가됩니다.

또한 cron 그룹을 선택적으로 만드는 방법을 보여 줍니다. 이 그룹은 Commerce 애플리케이션 기본값 이외의 설정으로 사용자 지정 cron 작업을 실행하는 데 사용할 수 있습니다.

이 자습서에서는 다음과 같이 가정합니다.

- Commerce 응용 프로그램이 `/var/www/html/magento2`에 설치되어 있습니다.
- Commerce 데이터베이스 사용자 이름과 암호가 모두 `magento`입니다.
- [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 모든 작업을 수행합니다.

## 1단계: 샘플 모듈 가져오기

사용자 지정 cron 작업을 설정하려면 샘플 모듈이 필요합니다. `magento-module-minimal` 모듈이 권장됩니다.

이미 샘플 모듈이 있는 경우, 샘플 모듈을 사용할 수 있습니다. 이 단계와 다음 단계를 건너뛰고 3단계: cron을 실행할 클래스 만들기 를 계속 진행하십시오.

**샘플 모듈을 가져오려면**:

1. [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 Commerce 서버에 로그인하거나 (으)로 전환합니다.
1. Commerce 애플리케이션 루트에 없는 디렉토리(예: 홈 디렉토리)로 변경합니다.
1. [`magento2-samples` 리포지토리][samples]을(를) 복제합니다.

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   `Permission denied (publickey).` 오류로 인해 명령이 실패하면 [GitHub.com에 SSH 공개 키를 추가][git-ssh]해야 합니다.

1. 샘플 코드를 복사할 디렉토리를 만듭니다.

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 샘플 모듈 코드를 복사합니다.

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 파일이 제대로 복사되었는지 확인합니다.

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   다음 결과가 표시됩니다.

   ```terminal
   drwxrwsr-x.   4 magento_user apache  4096 Oct 30 13:19 .
   drwxrwsr-x. 121 magento_user apache  4096 Oct 30 13:19 ..
   -rw-rw-r--.   1 magento_user apache   372 Oct 30 13:19 composer.json
   drwxrwsr-x.   2 magento_user apache  4096 Oct 30 13:19 etc
   -rw-rw-r--.   1 magento_user apache 10376 Oct 30 13:19 LICENSE_AFL.txt
   -rw-rw-r--.   1 magento_user apache 10364 Oct 30 13:19 LICENSE.txt
   -rw-rw-r--.   1 magento_user apache  1157 Oct 30 13:19 README.md
   -rw-rw-r--.   1 magento_user apache   270 Oct 30 13:19 registration.php
   drwxrwsr-x.   3 magento_user apache  4096 Oct 30 13:19 Test
   ```

1. Commerce 데이터베이스 및 스키마 업데이트:

   ```bash
   bin/magento setup:upgrade
   ```

1. 캐시를 정리합니다.

   ```bash
   bin/magento cache:clean
   ```

## 2단계: 샘플 모듈 확인

계속하기 전에 샘플 모듈이 등록되고 활성화되어 있는지 확인합니다.

1. 다음 명령을 실행합니다.

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. 모듈이 활성화되어 있는지 확인합니다.

   ```terminal
   Module is enabled
   ```

>[!TIP]
>
>출력에 `Module does not exist`이(가) 표시되면 [단계 1](#step-1-get-a-sample-module)을(를) 주의 깊게 검토하십시오. 코드가 올바른 디렉토리에 있는지 확인합니다. 맞춤법 및 대/소문자가 중요합니다. 다른 내용이 있으면 모듈이 로드되지 않습니다. `magento setup:upgrade`을(를) 실행하는 것도 잊지 마십시오.

## 3단계: cron을 실행할 클래스 만들기

이 단계에서는 cron 작업을 만드는 간단한 클래스를 보여 줍니다. 클래스는 `cron_schedule` 테이블이 성공적으로 설정되었음을 확인하는 행만 씁니다.

클래스를 만들려면 다음 작업을 수행하십시오.

1. 클래스의 디렉토리를 만들고 해당 디렉토리로 변경합니다.

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. 해당 디렉터리에 다음 내용이 포함된 `Test.php` 파일을 만들었습니다.

   ```php
   <?php
   namespace Magento\SampleMinimal\Cron;
   
   use Psr\Log\LoggerInterface;
   
   class Test {
       protected $logger;
   
       public function __construct(LoggerInterface $logger) {
           $this->logger = $logger;
       }
   
      /**
       * Write to system.log
       *
       * @return void
       */
       public function execute() {
           $this->logger->info('Cron Works');
       }
   }
   ```

## 4단계: `crontab.xml` 만들기

`crontab.xml` 파일은 사용자 지정 cron 코드를 실행하는 일정을 설정합니다.

`/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` 디렉터리에 다음과 같이 `crontab.xml`을(를) 만듭니다.

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

이전 `crontab.xml`은(는) 분당 한 번씩 `Magento/SampleMinimal/Cron/Test.php` 클래스를 실행하므로 행이 `cron_schedule` 테이블에 추가됩니다.

크론 예약을 관리자에서 구성할 수 있도록 하려면 시스템 구성 필드의 구성 경로를 사용합니다.

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <config_path>system/config/path</config_path>
        </job>
    </group>
</config>
```

여기서 `system/config/path`은(는) 모듈의 `etc/adminhtml/system.xml`에 정의된 시스템 구성 경로입니다.

## 5단계: 정리 컴파일 및 캐시

다음 명령을 사용하여 코드를 컴파일합니다.

```bash
bin/magento setup:di:compile
```

다음 명령을 사용하여 캐시를 정리합니다.

```bash
bin/magento cache:clean
```

## 6단계: cron 작업 확인

이 단계에서는 `cron_schedule` 데이터베이스 테이블에서 SQL 쿼리를 사용하여 사용자 지정 cron 작업을 확인하는 방법을 보여 줍니다.

cron을 확인하려면:

1. Commerce cron 작업 실행:

   ```bash
   bin/magento cron:run
   ```

1. `magento cron:run` 명령을 두 번 또는 세 번 입력하십시오.

   명령을 처음 입력하면 작업이 대기열에 추가되고, 그 후에 cron 작업이 실행됩니다. _최소_ 명령을 두 번 입력해야 합니다.

1. 다음과 같이 SQL 쿼리 `SELECT * from cron_schedule WHERE job_code like '%custom%'`을(를) 실행합니다.

   1. `mysql -u magento -p` 입력
   1. `mysql>` 프롬프트에서 `use magento;`을(를) 입력하십시오.
   1. `SELECT * from cron_schedule WHERE job_code like '%custom%';` 입력

      결과는 다음과 유사해야 합니다.

      ```terminal
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. (선택 사항) 메시지가 Commerce의 시스템 로그에 기록되는지 확인합니다.

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   다음과 같은 항목이 한 개 이상 표시됩니다.

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   이러한 메시지는 `Test.php`의 `execute` 메서드에서 가져옵니다.

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

SQL 명령 및 시스템 로그에 항목이 없으면 `magento cron:run` 명령을 몇 번 더 실행하고 기다리십시오. 데이터베이스를 업데이트하는 데 시간이 걸릴 수 있습니다.

## 7단계 (선택 사항): 사용자 정의 cron 그룹 설정

이 단계에서는 사용자 지정 cron 그룹을 선택적으로 설정하는 방법을 보여 줍니다. 사용자 지정 cron 작업을 다른 cron 작업과 다른 일정(일반적으로 분당 한 번)으로 실행하거나 여러 사용자 지정 cron 작업을 다른 설정으로 실행하려면 사용자 지정 cron 그룹을 설정해야 합니다.

사용자 지정 cron 그룹을 설정하려면:

1. 텍스트 편집기에서 `crontab.xml` 열기
1. `<group id="default">`을(를) `<group id="custom_crongroup">`(으)로 변경
1. 텍스트 편집기를 종료합니다.
1. 다음 내용으로 `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml`을(를) 만듭니다.

   ```xml
   <?xml version="1.0"?>
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
       <group id="custom_crongroup">
           <schedule_generate_every>1</schedule_generate_every>
           <schedule_ahead_for>4</schedule_ahead_for>
           <schedule_lifetime>2</schedule_lifetime>
           <history_cleanup_every>10</history_cleanup_every>
           <history_success_lifetime>60</history_success_lifetime>
           <history_failure_lifetime>600</history_failure_lifetime>
           <use_separate_process>1</use_separate_process>
       </group>
   </config>
   ```

옵션의 의미에 대한 설명은 [cron 참조 사용자 지정](custom-cron-reference.md)을 참조하십시오.

## 8단계: 사용자 정의 cron 그룹 확인

이 _선택 사항_ 단계는 관리자를 사용하여 사용자 지정 크론 그룹을 확인하는 방법을 보여 줍니다.

사용자 지정 cron 그룹을 확인하려면:

1. 사용자 지정 그룹에 대해 Commerce cron job을 실행합니다.

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   명령을 두 번 이상 실행합니다.

1. 캐시를 정리합니다.

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. 관리자로 관리자에 로그인합니다.
1. **스토어** > **설정** > **구성** > **고급** > **시스템**&#x200B;을 클릭합니다.
1. 오른쪽 창에서 **Cron**&#x200B;을 확장합니다.

   크론 그룹은 다음과 같이 표시됩니다.

   ![사용자 지정 크론 그룹](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
