---
title: 사용자 지정 크론 작업 및 크론 그룹 참조
description: 크론 그룹을 사용하여 크론을 사용자 지정하는 방법을 알아봅니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---


# 기준 참조 사용자 정의

이 항목은 사용자 정의 모듈에 대한 crontab 및 선택적으로 cron 그룹을 설정하는 데 도움이 됩니다. 사용자 지정 모듈에서 작업을 주기적으로 예약해야 하는 경우 해당 모듈에 대한 crontab을 설정해야 합니다. A _crontab_ 는 cron 작업 구성입니다.

선택적으로 사용자 지정 그룹을 설정할 수 있으며, 이 그룹 중 다른 클론 작업과 독립적으로 해당 그룹에 정의된 크론 작업을 실행할 수 있습니다.

단계별 자습서는 다음을 참조하십시오 [사용자 지정 아이콘 작업 및 콘 그룹 구성(튜토리얼)](custom-cron-tutorial.md).

크론 작업에 대한 개요는 다음을 참조하십시오 [크론 작업 구성](../cli/configure-cron-jobs.md).

## 크론 그룹 구성

이 섹션에서는 사용자 지정 모듈에 대한 cron 그룹을 선택적으로 만드는 방법을 설명합니다. 이 작업을 수행하지 않아도 되는 경우 다음 섹션을 계속 진행합니다.

A _클론 그룹_ 는 한 번에 두 개 이상의 프로세스에 대해 쉽게 크론을 실행할 수 있는 논리 그룹입니다. 대부분의 상거래 모듈은 `default` cron 그룹; 일부 모듈은 `index` 그룹에 속해 있어야 합니다.

사용자 지정 모듈에 대한 크론을 구현하는 경우 `default` 그룹 또는 다른 그룹 중에서 선택할 수 있습니다.

**모듈에 대한 크론 그룹을 구성하려면**:

만들기 `crontab.xml` 모듈 디렉토리에 있는 파일:

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

한 그룹의 경우 파일에는 다음 내용이 있어야 합니다.

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
| `group_name` | 크론 그룹의 이름입니다. 그룹 이름은 고유해야 하지 않습니다. 한 번에 한 그룹에 대해 크론을 실행할 수 있습니다. |
| `job_name` | 이 cron 작업에 대한 고유 ID입니다. |
| `classpath` | 인스턴스화할 클래스(클래스 경로). |
| `method` | 의 메서드 `classpath` 호출 |
| `time` | 예약 형식으로 표시합니다. 일정이 상거래 데이터베이스 또는 다른 저장소에 정의된 경우 이 매개 변수를 생략합니다. |

결과 `crontab.xml` 두 그룹의 경우 다음과 같습니다.

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

예를 들어 [Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### 크론 그룹 옵션 지정

새 그룹을 선언할 수 있으며, `cron_groups.xml` 다음 위치에 있습니다.

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

아래는 의 예입니다 `cron_groups.xml` 파일:

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
| `schedule_generate_every` | 일정을 작성하는 빈도(분)는 `cron_schedule` 테이블. |
| `schedule_ahead_for` | 예약에 미리 쓴 시간(분) `cron_schedule` 테이블. |
| `schedule_lifetime` | 크론 작업을 시작해야 하거나 크론 작업이 누락된 것으로 간주되는 시간(분)입니다(&quot;너무 늦게&quot;실행되어야 함). |
| `history_cleanup_every` | 크론 기록이 데이터베이스에 유지되는 시간(분)입니다. |
| `history_success_lifetime` | 완료된 cron 작업의 레코드가 데이터베이스에 유지됩니다(분). |
| `history_failure_lifetime` | 실패한 크론 작업의 레코드가 데이터베이스에 유지되는 시간(분) |
| `use_separate_process` | 별도의 php 프로세스에서 이 클론 그룹의 작업을 실행합니다. |

## 크론 작업 비활성화

크론 작업에는 `disable` 우리가 가지고 있는 것과 같은 기능 [참관자](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). 그러나 다음 기술을 사용하여 크론 작업을 비활성화할 수 있습니다. `schedule` 절대 일어나지 않을 날짜를 포함하는 시간.

예를 들어 `visitor_clean` 에 정의된 cron 작업 `Magento_Customer` 모듈:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

를 비활성화하려면 `visitor_clean` cron 작업, 사용자 지정 모듈 만들기 및 다시 작성 `visitor_clean` cron 작업 `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

이제, `visitor_clean` cron 작업은 절대 발생하지 않는 날짜에 2월 30일에 실행되도록 설정되었습니다.
