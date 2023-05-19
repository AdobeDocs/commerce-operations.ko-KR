---
title: 사용자 정의 cron 작업 및 cron 그룹 참조
description: 크론 그룹을 사용하여 크론을 사용자 지정하는 방법에 대해 알아봅니다.
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# cron 참조 사용자 지정

이 항목은 사용자 정의 모듈에 대한 크론탭 및 선택적으로 크론 그룹을 설정하는 데 도움이 됩니다. 사용자 정의 모듈이 작업을 정기적으로 예약해야 하는 경우 해당 모듈에 대한 crontab을 설정해야 합니다. A _crontab_ 은(는) cron 작업 구성입니다.

필요한 경우 사용자 정의 그룹을 설정할 수 있으며, 이를 통해 다른 cron 작업과 독립적으로 해당 그룹에 정의된 cron 작업을 실행할 수 있습니다.

단계별 자습서는 를 참조하십시오. [사용자 지정 cron 작업 및 cron 그룹 구성(튜토리얼)](custom-cron-tutorial.md).

cron 작업에 대한 개요는 를 참조하십시오. [cron 작업 구성](../cli/configure-cron-jobs.md).

## cron 그룹 구성

이 섹션에서는 사용자 정의 모듈에 대한 cron 그룹을 선택적으로 만드는 방법에 대해 설명합니다. 이 작업을 수행하지 않아도 되는 경우 다음 섹션을 계속합니다.

A _크론 군_ 는 한 번에 두 개 이상의 프로세스에 대해 cron 을 쉽게 실행할 수 있도록 해주는 논리 그룹입니다. 대부분의 상거래 모듈은 `default` cron 그룹, 일부 모듈은 `index` 그룹입니다.

사용자 지정 모듈에 대한 cron을 구현하는 경우 `default` 그룹 또는 다른 그룹.

**모듈에 대한 cron 그룹을 구성하려면**:

만들기 `crontab.xml` 모듈 디렉터리에 있는 파일:

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

한 그룹의 경우 파일에는 다음 내용이 포함되어야 합니다.

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="<group_name>">
        <job name="<job_name>" instance="<classpath>" method="<method>">
            <schedule><time></schedule>
        </job>
    </group>
</config>
```

위치:

| 값 | 설명 |
|---|---|
| `group_name` | 크론 그룹의 이름입니다. 그룹 이름이 고유할 필요는 없습니다. 한 번에 한 그룹에 대해 cron 을 실행할 수 있습니다. |
| `job_name` | 이 cron 작업에 대한 고유 ID. |
| `classpath` | 인스턴스화할 클래스(클래스 경로). |
| `method` | 의 메서드 `classpath` 전화를 겁니다. |
| `time` | cron 형식으로 예약합니다. 일정이 Commerce 데이터베이스 또는 다른 저장소에 정의된 경우 이 매개 변수를 생략합니다. |

결과 `crontab.xml` 두 개의 그룹을 사용하면 다음과 같이 표시될 수 있습니다.

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="<job_1_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_2_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
    <group id="index">
        <job name="<job_3_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_4_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

예를 들어 다음을 참조하십시오. [Magento_고객 crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Cron 그룹 옵션 지정

새 그룹을 선언하고 저장소 보기 범위에서 실행되는 구성 옵션을 지정할 수 있습니다. `cron_groups.xml` 파일, 위치:

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

다음은 의 예입니다 `cron_groups.xml` 파일:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
    <group id="<group_name>">
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

위치:

| 옵션 | 설명 |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | 에 일정을 작성하는 빈도(분) `cron_schedule` 테이블. |
| `schedule_ahead_for` | 에 일정을 작성하는 사전 시간(분) `cron_schedule` 테이블. |
| `schedule_lifetime` | cron 작업을 시작해야 하거나 cron 작업을 누락된 것으로 간주해야 하는 시간(분)입니다(&quot;너무 늦어&quot; 실행할 수 없음). |
| `history_cleanup_every` | cron history 가 데이터베이스에 보관되는 시간 (분) |
| `history_success_lifetime` | 성공적으로 완료된 cron 작업의 레코드가 데이터베이스에 유지되는 시간(분)입니다. |
| `history_failure_lifetime` | 실패한 cron 작업 레코드가 데이터베이스에 유지되는 시간(분)입니다. |
| `use_separate_process` | 별도의 php 프로세스에서 이 cron 그룹의 작업을 실행하십시오. |

## cron 작업 비활성화

Cron 작업에 `disable` 다음과 같은 기능 [관찰자](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). 그러나 다음 기술을 사용하여 cron 작업을 비활성화할 수 있습니다. `schedule` 절대 일어나지 않을 날짜가 포함된 시간.

예를 들어 을 비활성화합니다. `visitor_clean` 에 정의된 cron 작업 `Magento_Customer` 모듈:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

을(를) 비활성화하려면 `visitor_clean` cron job, 사용자 정의 모듈 생성 및 재작성 `visitor_clean` cron job `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

이제 `visitor_clean` cron 작업이 2월 30일 00:00에 실행되도록 설정되었습니다. 이 작업은 절대 발생하지 않습니다.
