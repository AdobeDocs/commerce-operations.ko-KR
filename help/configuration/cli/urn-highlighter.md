---
title: URN 형광펜
description: IDE에서 URN 강조 표시를 설정하는 방법을 알아봅니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# URN 형광펜 개요

{{file-system-owner}}

상거래 코드는 모든 XSD 스키마를 [URN(Uniform Resource Name)](https://www.ietf.org/rfc/rfc2141.txt). 코드를 개발하고 XSD를 참조해야 하는 경우 이 명령은 URN을 인식하고 강조 표시하도록 통합 개발자 환경(IDE)을 구성합니다. 이렇게 하면 개발이 더 쉬워집니다.

기본적으로 PhpStorm과 같은 IDE는 URN을 인식하도록 구성되어 있지 않으므로 다음과 같이 빨간색 텍스트로 표시됩니다.

![URN을 인식할 수 있도록 PhpStorm이 구성되지 않았습니다.](../../assets/configuration/urn-before.png)

다음 `bin/magento dev:urn-catalog:generate` 명령을 사용하면 IDE(현재 PhpStorm 및 Visual Studio Code만)에서 다음과 같이 URN을 인식하고 강조 표시할 수 있습니다.

![IDE에서 URN을 인식하도록 설정](../../assets/configuration/urn-after.png)

특히 이 명령은 다음과 같은 PhpStorm 구성을 생성합니다.

![PhpStorm 구성 예](../../assets/configuration/urn-settings.png)

## IDE 구성

현재 PhpStorm 및 Visual Studio 코드만 지원됩니다.

명령 구문:

```bash
bin/magento dev:urn-catalog:generate <path>
```

위치 `<path>` PhpStorm의 경로입니다. `misc.xml` 파일. 프로젝트 루트와 상대적인 위치에 있습니다. 일반적으로 `<path>` is `.idea/misc.xml`.

>[!INFO]
>
>스키마 및 DTD를 최신 상태로 유지하려면 `dev:urn-catalog:generate` 를 포함하는 상거래 2 모듈을 추가, 수정 또는 제거할 때마다 명령 `*.xsd` 파일.
