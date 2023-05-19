---
title: cron 작업 구성 및 실행
description: cron 작업을 관리하는 방법을 알아봅니다.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---

# cron 작업 구성

{{file-system-owner}}

여러 상거래 기능을 사용하려면 적어도 1개의 cron 작업이 필요하며, 이는 향후 활동이 발생하도록 예약합니다. 이러한 활동의 일부 목록은 다음과 같습니다.

- 카탈로그 가격 규칙
- 뉴스레터
- Google 사이트 맵 생성 중
- 고객 경고/알림(제품 가격 변경, 제품 재입고)
- 리인덱싱
- 개인 판매(Adobe Commerce만 해당)
- 환율 자동 업데이트
- 모든 상거래 이메일(주문 확인 및 트랜잭션 포함)

>[!WARNING]
>
>더 이상 실행할 수 없습니다. `dev/tools/cron.sh` 스크립트가 제거되었기 때문입니다.

>[!INFO]
>
>Commerce는 색인화를 비롯한 여러 중요한 시스템 기능에 대한 적절한 cron 작업 구성에 따라 달라집니다. 이를 제대로 설정하지 못한다는 것은 Commerce가 예상대로 작동하지 않는다는 것을 의미한다.

UNIX 시스템은 다음을 사용하여 특정 사용자가 수행할 작업을 예약합니다. _crontab_: cron daemon에 유효한 데몬에게 &quot;이 날짜에 이 명령을 실행합니다&quot;라고 지시하는 지침이 포함된 파일입니다. 각 사용자에는 자체 crontab이 있으며, 지정된 crontab의 명령은 해당 쿠키를 소유한 사용자로 실행됩니다.

웹 브라우저에서 크론을 실행하려면 다음을 참조하십시오. [브라우저에서 실행할 cron.php 보안](../security/secure-cron-php.md).

## Commerce crontab 만들기 또는 제거

이 섹션에서는 Commerce cron tab(즉, Commerce cron 작업에 대한 구성)을 만들거나 제거하는 방법에 대해 설명합니다.

다음 _crontab_ cron 작업을 실행하는 데 사용되는 구성입니다.

Commerce 응용 프로그램에서는 다른 구성으로 실행할 수 있는 cron 작업을 사용합니다. PHP 명령줄 구성은 인덱서를 다시 인덱싱하고 이메일을 생성하며 사이트 맵을 생성하는 일반적인 cron 작업을 제어합니다.

>[!WARNING]
>
>- 설치 및 업그레이드 중 문제가 발생하지 않도록 PHP 명령줄 구성과 PHP 웹 서버 플러그인 구성에 동일한 PHP 설정을 적용하는 것이 좋습니다. 자세한 내용은 [필수 PHP 설정](../../installation/prerequisites/php-settings.md).
>- 다중 노드 시스템에서 crontab은 한 노드에서만 실행할 수 있습니다. 성능 또는 확장성과 관련된 이유로 둘 이상의 웹 노드를 설정한 경우에만 적용됩니다.


### Commerce crontab 만들기

버전 2.2부터 Commerce에서 crontab을 만듭니다. Commerce 파일 시스템 소유자를 위해 구성된 crontab에 Commerce crontab을 추가합니다. 즉, 다른 확장 또는 애플리케이션에 대한 crontab을 이미 설정한 경우 Commerce crontab을 추가합니다.

Commerce 크론탭이 내부에 있습니다. `#~ MAGENTO START` 및 `#~ MAGENTO END` crontab의 댓글.

Commerce crontab을 만들려면 다음을 수행하십시오.

1. 로 로그인하거나 로 전환합니다 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. Commerce 설치 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   bin/magento cron:install [--force]
   ```

사용 `--force` 기존 crontab을 다시 작성합니다.

>[!INFO]
>
>- `magento cron:install` 내부에 기존 crontab을 다시 쓰지 않음 `#~ MAGENTO START` 및 `#~ MAGENTO END` crontab의 댓글.
>- `magento cron:install --force` 상거래 댓글 이외의 cron 작업에는 영향을 주지 않습니다.


crontab을 보려면 다음 명령을 파일 시스템 소유자로 입력합니다.

```bash
crontab -l
```

샘플은 다음과 같습니다.

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>다음 `update/cron.php` 파일이 Commerce 2.4.0에서 제거되었습니다. 이 파일이 설치에 있으면 안전하게 제거할 수 있습니다.
>
>에 대한 모든 참조 `update/cron.php` 및 `bin/magento setup:cron:run` crontab&#39;에서도 제거해야 합니다.

### Commerce crontab 제거

Commerce 응용 프로그램을 제거하기 전에만 Commerce crontab을 제거해야 합니다.

Commerce crontab을 제거하려면:

1. 다음으로 로그인하거나 다음으로 전환 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. Commerce 설치 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>이 명령은 외부 cron 작업에 영향을 주지 않습니다. `#~ MAGENTO START` 및 `#~ MAGENTO END` crontab의 댓글.

## 명령줄에서 cron 실행

명령 옵션:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

위치 `--group` 실행할 cron 그룹을 지정합니다(모든 그룹에 대해 cron을 실행하려면 이 옵션 생략).

인덱싱 cron 작업을 실행하려면 다음을 입력합니다.

```bash
bin/magento cron:run --group index
```

기본 cron 작업을 실행하려면 다음을 입력합니다.

```bash
bin/magento cron:run --group default
```

사용자 지정 cron 작업 및 그룹을 설정하려면 다음을 참조하십시오. [사용자 정의 cron 작업 및 cron 그룹 구성](../cron/custom-cron.md).

>[!INFO]
>
>실행할 작업을 처음 검색하는 경우 및 작업을 직접 실행하는 경우 cron 을 두 번 실행해야 합니다. 두 번째 cron 실행은 다음 날짜 또는 그 이후에 수행되어야 합니다. `scheduled_at` 모든 작업의 시간.

## 로깅

모두 `cron` 작업 정보가 다음에서 이동됨: `system.log` 별도의 항목으로 `cron.log`.
기본적으로 cron 정보는 `<install_directory>/var/log/cron.log`.
cron 작업의 모든 예외가 다음으로 기록됨 `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

로그인하는 것 외에 `cron.log`:

- 실패한 작업 `ERROR` 및 `MISSED` 상태는 다음 위치에 기록됩니다. `<install_directory>/var/log/support_report.log`.

- 이(가) 있는 작업 `ERROR` 상태는 항상 다음으로 기록됨 `CRITICAL` 위치: `<install_directory>/var/log/exception.log`.

- 이(가) 있는 작업 `MISSED` 상태가 다음으로 기록됨 `INFO` 다음에서 `<install_directory>/var/log/debug.log` 디렉터리(개발자 모드만 해당).

>[!INFO]
>
>모든 cron 데이터도 `cron_schedule` 전자 상거래 데이터베이스의 테이블입니다. 이 표에서는 다음을 포함하여 cron 작업 기록을 제공합니다.
>
>- 작업 ID 및 코드
>- 상태
>- 만든 날짜
>- 예약된 날짜
>- 실행된 날짜
>- 완료 날짜
>
>테이블에서 레코드를 보려면 명령줄의 Commerce 데이터베이스에 로그인하고 를 입력합니다 `SELECT * from cron_schedule;`.
