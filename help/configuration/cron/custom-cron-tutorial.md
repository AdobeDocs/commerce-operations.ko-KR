---
title: 사용자 지정 크론 작업 및 크론 그룹 구성(튜토리얼)
description: 이 단계별 자습서를 사용하여 사용자 지정 크론 작업을 만듭니다.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---


# 사용자 지정 아이콘 작업 구성

이 단계별 자습서에서는 샘플 모듈에서 사용자 지정 크론 작업과 선택적으로 크론 그룹을 만드는 방법을 보여줍니다. 이미 사용 중인 모듈을 사용하거나 Adobe에서 제공하는 샘플 모듈을 사용할 수 있습니다 [`magento2-samples` 저장소][samples].

크론 작업을 실행하면 행에 `cron_schedule` cron 작업의 이름이 있는 표, `custom_cron`.

또한 전자 상거래 애플리케이션 기본값 이외의 설정으로 사용자 지정 전자 상거래 작업을 실행하는 데 사용할 수 있는 전자 상거래 그룹을 선택적으로 만드는 방법을 보여 줍니다.

이 자습서에서는 다음을 가정합니다.

- 상거래 응용 프로그램은에 설치됩니다. `/var/www/html/magento2`
- 상거래 데이터베이스 사용자 이름과 암호가 모두 `magento`
- 모든 작업을 [파일 시스템 소유자](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)

## 1단계: 샘플 모듈 가져오기

사용자 지정 크론 작업을 설정하려면 샘플 모듈이 필요합니다. 다음 사항을 제안합니다 `magento-module-minimal` 모듈.

이미 샘플 모듈이 있다면 사용할 수 있습니다. 이 단계 및 다음 단계를 건너뛰고 3단계를 계속 진행합니다. 크론을 실행할 클래스를 만듭니다.

**샘플 모듈을 가져오려면**:

1. Commerce 서버에 로그인하거나 [파일 시스템 소유자](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 상거래 응용 프로그램 루트(예: 홈 디렉토리)에 없는 디렉토리로 변경합니다.
1. 복제 [`magento2-samples` 저장소][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   오류로 인해 명령이 실패하는 경우 `Permission denied (publickey).`: [gitHub.com에 SSH 공개 키 추가][git-ssh].

1. 샘플 코드를 복사할 디렉토리를 만듭니다.

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 샘플 모듈 코드를 복사합니다.

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 올바르게 복사된 파일을 확인합니다.

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

1. 전자 상거래 데이터베이스 및 스키마 업데이트:

   ```bash
   bin/magento setup:upgrade
   ```

1. 캐시 정리:

   ```bash
   bin/magento cache:clean
   ```

## 2단계: 샘플 모듈 확인

계속하기 전에 샘플 모듈이 등록되어 있고 활성화되어 있는지 확인하십시오.

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
>출력에 `Module does not exist`, 검토 [1단계](#step-1-get-a-sample-module) 주의 깊게 코드가 올바른 디렉토리에 있는지 확인합니다. 철자와 사례가 중요합니다. 다른 항목이 있으면 모듈이 로드되지 않습니다. 또한 실행 을 잊지 마십시오 `magento setup:upgrade`.

## 3단계: 크론을 실행할 클래스 만들기

이 단계에서는 크론 작업을 만드는 간단한 클래스를 보여 줍니다. 클래스는 `cron_schedule` 성공적으로 설정되었는지 확인하는 테이블입니다.

클래스를 만들려면

1. 클래스에 대한 디렉토리를 만들고 해당 디렉토리로 변경합니다.

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. 이름이 인 파일을 만들었습니다. `Test.php` 다음 내용이 있는 해당 디렉토리에서 다음을 수행합니다.

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

## 4단계: 만들기 `crontab.xml`

다음 `crontab.xml` 파일에서 사용자 지정 cron 코드를 실행할 일정을 설정합니다.

만들기 `crontab.xml` 다음과 같습니다. `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` 디렉토리:

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

이전 `crontab.xml` 실행 `Magento/SampleMinimal/Cron/Test.php` 분당 한 번 클래스를 사용하면 `cron_schedule` 테이블.

관리자로부터 cron 일정을 구성할 수 있도록 시스템 구성 필드의 구성 경로를 사용합니다.

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

위치, `system/config/path` 는 에 정의된 시스템 구성 경로입니다. `etc/adminhtml/system.xml` 섹션에 있는 마지막 항목이 될 필요가 없습니다.

## 5단계: 컴파일 및 캐시 정리

다음 명령을 사용하여 코드를 컴파일합니다.

```bash
bin/magento setup:di:compile
```

다음 명령을 사용하여 캐시를 정리합니다.

```bash
bin/magento cache:clean
```

## 6단계: 크론 작업 확인

이 단계는 의 SQL 쿼리를 사용하여 사용자 지정 크론 작업을 확인하는 방법을 보여 줍니다 `cron_schedule` 데이터베이스 테이블.

크론을 확인하려면:

1. 전자 상거래 충돌 작업 실행:

   ```bash
   bin/magento cron:run
   ```

1. 을(를) 입력합니다. `magento cron:run` 2, 3번 명령하라.

   명령을 처음 입력할 때 이 명령은 작업을 대기열로 처리합니다. 그런 다음 cron 작업이 실행됩니다. 명령을 입력해야 합니다 _적어도_ 두 번

1. SQL 쿼리 실행 `SELECT * from cron_schedule WHERE job_code like '%custom%'` 아래와 같이 변경하는 것을 의미합니다.

   1. Enter 키 `mysql -u magento -p`
   1. 에서 `mysql>` 프롬프트, 입력 `use magento;`
   1. Enter 키 `SELECT * from cron_schedule WHERE job_code like '%custom%';`

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

1. (선택 사항) 메시지가 상거래 시스템 로그에 기록되는지 확인합니다.

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   다음과 같은 항목이 하나 이상 표시됩니다.

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   이러한 메시지는 `execute` 메서드 `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

SQL 명령 및 시스템 로그에 항목이 없으면 `magento cron:run` 몇 번 더 명령하고 기다려라. 데이터베이스를 업데이트하는 데 시간이 걸릴 수 있습니다.

## 7단계(선택 사항): 사용자 지정 아이콘 그룹 설정

이 단계는 선택적으로 사용자 지정 cron 그룹을 설정하는 방법을 보여줍니다. 사용자 지정 크론 작업을 다른 크론 작업과 다른 일정(일반적으로 분당 한 번)에서 실행하거나 여러 사용자 지정 크론 작업을 다른 설정으로 실행하려면 사용자 지정 크론 그룹을 설정해야 합니다.

사용자 지정 아이콘 그룹을 설정하려면 다음을 수행하십시오.

1. 열기 `crontab.xml` 텍스트 편집기에서 을 참조하십시오.
1. 변경 `<group id="default">` to `<group id="custom_crongroup">`
1. 텍스트 편집기를 종료합니다.
1. 만들기 `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` 다음 내용으로 채우십시오.

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

옵션의 의미에 대한 설명은 다음을 참조하십시오 [기준 참조 사용자 정의](custom-cron-reference.md).

## 8단계: 사용자 지정 클라우드 그룹 확인

이 _옵션_ 단계는 관리자를 사용하여 사용자 지정 cron 그룹을 확인하는 방법을 보여줍니다.

사용자 지정 계정 그룹을 확인하려면:

1. 사용자 지정 그룹에 대한 전자 상거래 충돌 작업 실행:

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   명령을 두 번 이상 실행합니다.

1. 캐시 정리:

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. 관리자로 관리자에게 로그인합니다.
1. 클릭 **스토어** > **설정** > **구성** > **고급** > **시스템**.
1. 오른쪽 창에서 **크론**.

   크론 그룹이 다음과 같이 표시됩니다.

   ![사용자 지정 클라우드 그룹](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
