---
title: 프로파일링 활성화
description: MAGE 프로파일러를 분석 도구에 사용할 수 있도록 하는 방법에 대해 자세히 알아보십시오.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# 프로파일링 활성화

상거래 프로파일링을 사용하여 다음을 수행할 수 있습니다.

- 기본 제공 프로파일러를 사용하도록 설정합니다.

   Commerce와 함께 기본 제공 프로파일러를 사용하여 성능 분석과 같은 작업을 수행할 수 있습니다. 프로파일링의 특성은 사용하는 분석 도구에 따라 달라집니다. Adobe는 HTML을 포함하여 다양한 형식을 지원합니다. 프로파일러를 활성화하면 `var/profiler.flag` 파일에서는 프로파일러를 사용하도록 설정하고 구성을 나타냅니다. 비활성화하면 이 파일이 삭제됩니다.

- 상거래 페이지에 종속성 그래프를 표시합니다.

   A _종속성 그래프_ 는 객체 종속성 목록과 모든 해당 종속성, 이러한 종속성에 대한 모든 종속성 목록입니다.

   당신은 그 목록에 특히 관심이 있어야 한다 _사용되지 않는 종속성_- 일부 생성자에서 요청되어 생성된 개체이지만 사용되지 않은 개체입니다(즉, 호출된 메서드가 없음). 따라서 이러한 종속성을 만드는 데 프로세서 시간과 메모리가 낭비됩니다.

Commerce에서는 의 기본 기능을 제공합니다 [`Magento\Framework\Profiler`][profiler].

MAGE_PROFILER 변수 또는 명령줄을 사용하여 프로파일러를 활성화하고 구성할 수 있습니다.

## MAGE_PROFILER 설정

다음 값을 설정할 수 있습니다. `MAGE_PROFILER` 에 설명된 방법 중 하나로 [부트스트랩 매개 변수의 값 설정](../bootstrap/set-parameters.md).

`MAGE_PROFILER` 은 다음 값을 지원합니다.

- `1` 특정 프로파일러의 출력을 사용하도록 설정하려면

   다음 값 중 하나를 사용하여 특정 프로파일러를 활성화할 수 있습니다.

   - `csvfile` 사용 [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - 다른 값(제외) `2`) 내의 아무 곳에나 삽입할 수 있습니다 [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` 종속성 그래프를 활성화

   종속성 그래프는 일반적으로 페이지 하단에 표시됩니다. 다음 그림은 출력의 일부를 보여 줍니다.

   ![종속성 그래프](../../assets/configuration/depend-graphs.png)

## CLI 명령

CLI 명령을 사용하여 프로파일러를 활성화하거나 비활성화할 수 있습니다.

- `dev:profiler:enable <type>` 프로파일러를 `type` 의 `html` (기본값) 또는 `csvfile`. 활성화되면 플래그 파일 `var/profiler.flag` 가 만들어집니다.
- `dev:profiler:disable` 프로파일러를 비활성화합니다. 비활성화하면 플래그 파일이 `var/profiler.flag` 가 제거되었습니다.

종속성 그래프를 활성화하려면 변수 옵션을 사용합니다.

**프로파일러를 활성화 또는 비활성화하려면**:

1. Commerce 서버에 로그인합니다.
1. 상거래 설치 디렉토리로 변경합니다.
1. 파일 시스템 소유자로서 프로파일러를 사용하도록 설정합니다.

   유형을 사용하여 프로파일러를 활성화하려면 `html` 그리고 플래그 파일을 만듭니다.

   ```bash
   bin/magento dev:profiler:enable html
   ```

   유형을 사용하여 프로파일러를 활성화하려면 `csvfile` 그리고 플래그 파일을 만듭니다.

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   출력은 `<project-root>/var/log/profiler.csv`. 다음 `profiler.csv` 이 새로 고칠 때마다 무시됩니다.

   프로파일러를 비활성화하고 플래그 파일을 제거하려면

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
