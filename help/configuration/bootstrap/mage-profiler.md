---
title: 프로파일링 활성화
description: MAGE 프로파일러가 분석 도구와 함께 사용할 수 있도록 하는 방법에 대해 자세히 알아보십시오.
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# 프로파일링 활성화

Commerce 프로파일링을 사용하여 다음과 같은 작업을 수행할 수 있습니다.

- 기본 제공 프로파일러를 사용하도록 설정합니다.

  Commerce에서 내장된 프로파일러를 사용하여 성능 분석과 같은 작업을 수행할 수 있습니다. 프로파일링의 특성은 사용하는 분석 도구에 따라 다릅니다. HTML을 비롯한 다양한 형식을 지원합니다. 프로파일러를 사용하면 프로파일러가 사용 및 구성임을 나타내는 `var/profiler.flag` 파일이 생성됩니다. 비활성화되면 이 파일은 삭제됩니다.

- Commerce 페이지에 종속성 그래프를 표시합니다.

  _종속성 그래프_&#x200B;은(는) 개체 종속성 및 해당 종속성과 해당 종속성에 대한 모든 종속성 목록입니다.

  일부 생성자에서 요청되었지만 사용되지 않은(즉, 메서드가 호출되지 않은) 개체인 _사용되지 않은 종속성_ 목록에 특히 관심이 있어야 합니다. 결과적으로 이러한 종속성을 만드는 데 소요되는 프로세서 시간과 메모리가 낭비됩니다.

Commerce은 [`Magento\Framework\Profiler`][profiler]에서 기본 기능을 제공합니다.

MAGE_PROFILER 변수 또는 명령줄을 사용하여 프로파일러를 활성화하고 구성할 수 있습니다.

## MAGE_PROFILER 설정

`MAGE_PROFILER`부트스트랩 매개 변수의 값을 설정[하는 방법으로 ](../bootstrap/set-parameters.md)의 값을 설정할 수 있습니다.

`MAGE_PROFILER`은(는) 다음 값을 지원합니다.

- `1`을(를) 사용하여 특정 프로파일러의 출력을 사용하도록 설정합니다.

  다음 값 중 하나를 사용하여 특정 프로파일러를 활성화할 수 있습니다.

   - `csvfile`을(를) 사용하는 [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - `2`을(를) 사용하는 빈 값을 포함한 다른 모든 값([`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html] 제외)

- 종속성 그래프를 사용하려면 `2`을(를) 사용하십시오.

  종속성 그래프는 일반적으로 페이지 하단에 표시됩니다. 다음 그림은 출력의 일부를 보여 줍니다.

  ![종속성 그래프](../../assets/configuration/depend-graphs.png)

## CLI 명령

CLI 명령을 사용하여 프로파일러를 활성화하거나 비활성화할 수 있습니다.

- `dev:profiler:enable <type>`은(는) 프로필러를 `type`/`html`(기본값) 또는 `csvfile`(으)로 활성화합니다. 활성화되면 플래그 파일 `var/profiler.flag`이(가) 만들어집니다.
- `dev:profiler:disable`이(가) 프로파일러를 사용하지 않도록 설정합니다. 비활성화되면 플래그 파일 `var/profiler.flag`이(가) 제거됩니다.

종속성 그래프를 활성화하려면 변수 옵션을 사용합니다.

**프로파일러를 사용하거나 사용하지 않도록 설정하려면**:

1. Commerce 서버에 로그인.
1. Commerce 설치 디렉토리로 변경합니다.
1. 파일 시스템 소유자로서 프로파일러를 활성화합니다.

   `html` 형식을 사용하여 프로파일러를 사용하도록 설정하고 플래그 파일을 만들려면:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   `csvfile` 형식을 사용하여 프로파일러를 사용하도록 설정하고 플래그 파일을 만들려면:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   출력이 `<project-root>/var/log/profiler.csv`에 저장됩니다. 페이지를 새로 고칠 때마다 `profiler.csv`이(가) 재정의됩니다.

   프로파일러를 비활성화하고 플래그 파일을 제거하려면 다음을 수행하십시오.

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
