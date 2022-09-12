---
title: 크론 작업 구성 및 실행
description: cron 작업을 관리하는 방법을 알아봅니다.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---


# 크론 작업 구성

{{file-system-owner}}

몇 가지 상거래 기능에는 나중에 활동을 스케줄링하는 하나 이상의 충돌 작업이 필요합니다. 이러한 활동의 일부 목록은 다음과 같습니다.

- 카탈로그 가격 규칙
- 뉴스레터
- Google 사이트 맵 생성
- 고객 경고/알림(제품 가격 변경, 제품 다시 재고)
- 재인덱싱
- 비공개 판매(Adobe Commerce만 해당)
- 통화 환율 자동 갱신
- 모든 상거래 전자 메일(주문 확인 및 트랜잭션 포함)

>[!WARNING]
>
>더 이상 실행할 수 없습니다 `dev/tools/cron.sh` 스크립트가 제거되었기 때문입니다.

>[!INFO]
>
>상거래는 색인을 포함하여 많은 중요한 시스템 기능에 대한 적절한 cron 작업 구성에 따라 달라집니다. 제대로 설정하지 않으면 상거래가 예상대로 작동하지 않습니다.

UNIX 시스템은 _crontab_- cron 데몬에 대한 지침이 포함된 파일이며, 이 날짜에서 이 명령을 &quot;이 시간에 실행&quot;하도록 데몬에 지시합니다. 각 사용자에게는 자체 crontab이 있고, 지정된 crontab의 명령은 해당 crontab을 소유한 사용자로 실행됩니다.

웹 브라우저에서 크론을 실행하려면 다음을 참조하십시오 [브라우저에서 실행할 cron.php 보안](../security/secure-cron-php.md).

## 상거래 crontab을 만들거나 제거합니다

이 섹션에서는 상거래 cron 작업 구성인 상거래 cron 탭을 만들거나 제거하는 방법에 대해 설명합니다.

다음 _crontab_ 은 cron 작업을 실행하는 데 사용되는 구성입니다.

상거래 응용 프로그램은 다른 구성으로 실행할 수 있는 크론 작업을 사용합니다. PHP 명령줄 구성은 인덱서를 다시 색인화하고 전자 메일을 생성하고 사이트 맵을 생성하는 일반 크론 작업을 제어합니다.

>[!WARNING]
>
>- 설치 및 업그레이드 중에 문제가 발생하지 않도록 PHP 명령줄 구성과 PHP 웹 서버 플러그 인의 구성 모두에 동일한 PHP 설정을 적용하는 것이 좋습니다. 자세한 내용은 [필수 PHP 설정](../../installation/prerequisites/php-settings.md).
>- 다중 노드 시스템에서 crontab은 하나의 노드에서만 실행할 수 있습니다. 성능 또는 확장성과 관련된 이유로 둘 이상의 웹 노드를 설정하는 경우에만 적용됩니다.


### 상거래 crontab 만들기

버전 2.2부터 Commerce에서 크론탭을 만듭니다. 상거래 파일 시스템 소유자의 구성된 crontab에 상거래 crontab을 추가합니다. 다시 말해, 다른 확장이나 응용 프로그램에 대한 crontab을 이미 설정한 경우 거기에 상거래 crontab을 추가합니다.

Commerce Crontab이 내부에 있습니다. `#~ MAGENTO START` 및 `#~ MAGENTO END` crontab에 있는 주석.

전자 상거래 crontab을 생성하려면

1. 로 로그인하거나 로 전환합니다. [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 상거래 설치 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   bin/magento cron:install [--force]
   ```

사용 `--force` 기존 crontab을 다시 작성하려면 다음을 수행하십시오.

>[!INFO]
>
>- `magento cron:install` 내에서 기존 crontab을 다시 작성하지 않습니다. `#~ MAGENTO START` 및 `#~ MAGENTO END` crontab에 있는 주석.
>- `magento cron:install --force` 은 상거래 주석 이외의 핵심 작업에는 영향을 주지 않습니다.


crontab을 보려면 파일 시스템 소유자로 다음 명령을 입력합니다.

```bash
crontab -l
```

샘플은

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>다음 `update/cron.php` 파일이 Commerce 2.4.0에서 제거되었습니다. 설치 시 이 파일이 있으면 파일을 안전하게 제거할 수 있습니다.
>
>에 대한 모든 참조 `update/cron.php` 및 `bin/magento setup:cron:run` crontab에서도 제거해야 합니다.

### 상거래 crontab 제거

Commerce 응용 프로그램을 제거하기 전에만 Commerce crontab을 제거해야 합니다.

상거래 crontab을 제거하려면

1. 로 로그인하거나 로 전환합니다. [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 상거래 설치 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>이 명령은 외부 크론 작업에 영향을 주지 않습니다 `#~ MAGENTO START` 및 `#~ MAGENTO END` crontab에 있는 주석.

## 명령줄에서 cron 실행

명령 옵션:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

여기서 `--group` 실행할 cron 그룹을 지정합니다(모든 그룹에 대해 cron을 실행하려면 이 옵션을 생략함).

색인화 크론 작업을 실행하려면 다음을 입력합니다.

```bash
bin/magento cron:run --group index
```

기본 로그온 작업을 실행하려면 다음을 입력합니다.

```bash
bin/magento cron:run --group default
```

사용자 지정 아이콘 작업 및 그룹을 설정하려면 다음을 참조하십시오 [사용자 지정 아이콘 작업 및 크론 그룹 구성](../cron/custom-cron.md).

>[!INFO]
>
>다음 작업을 두 번 실행해야 합니다. 작업을 직접 실행하는 작업을 처음으로 검색하는 시간 및 두 번째 시간 두 번째 크론 실행은 `scheduled_at` 모든 작업에 대한 시간

## 로깅

모두 `cron` 작업 정보가 `system.log` 별개의 `cron.log`.
기본적으로 cron 정보는 `<install_directory>/var/log/cron.log`.
기준 작업의 모든 예외는 `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

로그인했을 뿐만 아니라 `cron.log`:

- 작업 실패 `ERROR` 및 `MISSED` 상태는 `<install_directory>/var/log/support_report.log`.

- 작업 `ERROR` 상태는 항상 `CRITICAL` in `<install_directory>/var/log/exception.log`.

- 작업 `MISSED` 상태가 `INFO` 에서 `<install_directory>/var/log/debug.log` 디렉토리(개발자 모드만).

>[!INFO]
>
>모든 크론 데이터는에 기록됩니다 `cron_schedule` 표(상거래 데이터베이스)를 참조하십시오. 이 표에는 다음을 포함한 크론 작업 내역이 나와 있습니다.
>
>- 작업 ID 및 코드
>- 상태
>- 만든 날짜
>- 예약된 날짜
>- 실행된 날짜
>- 종료 날짜
>
>테이블에서 레코드를 보려면 명령줄에서 Commerce 데이터베이스에 로그인하고 를 입력합니다. `SELECT * from cron_schedule;`.
