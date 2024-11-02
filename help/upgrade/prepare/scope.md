---
title: 업그레이드 범위 이해
description: Adobe Systems Commerce 사용자 정의 모듈 또는 서드파티 확장에 영향을 줄 수 있는 릴리스의 이전 버전과 호환되지 않는 변경 사항에 대해 알아봅니다.
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# 업그레이드 범위 이해

[릴리스 정보](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview) 검토하여 서드파티 및 사용자 지정 모듈에 영향을 줄 수 있는 개선 사항, 버그 수정 및 알려진 문제 포함하여 릴리스의 범위 이해합니다.

## 이전 버전과 호환되지 않는 변경 사항

Adobe Commerce 릴리스에는 이전 버전과 호환 불가능한 변경 사항이 포함될 수 있습니다. 이전 버전과 호환 불가능한 변경 사항 설명서를 검토하고 다음을 참조하십시오.

- **[주요 변경 내용 강조 표시](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/)**—중요한 영향을 미치는 변경 내용으로 서드파티 모듈이 계속 작동하도록 하려면 자세한 설명과 특수 지침이 필요합니다.
- **[부분 변경 참조](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)**—클래스, API 멤버십, 데이터베이스, 종속성 삽입, 인터페이스, 레이아웃, 시스템 및 XSD에 대한 부분 변경 사항을 설명하는 코드 베이스에서 생성된 참조 설명서입니다.

## 타사 확장

Adobe Commerce Marketplace의 새 호환성 정책은 _모든_ 나열된 확장이 GA 날짜로부터 30일 이내에 최신 릴리스 버전과 호환되도록 합니다. 따라서 가능하면 Marketplace를 통해 서드파티 확장을 가져오는 것이 중요합니다.

## 사용자 정의 모듈

모든 사용자 지정 모듈은 업그레이드하려는 대상 버전에 대해 확인해야 합니다. 이는 업그레이드에 소요되는 시간과 자원이 가장 많은 프로세스입니다. 사용자 정의 모듈을 평가할 때는 이전 버전과 호환되지 않는 변경 사항을 찾고 컨트롤러 분해와 같은 새로운 방법을 알고 있어야 합니다. 이에 대한 자세한 내용은 [릴리스 정보](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview)를 참조하세요. 또한 모듈 개발을 위해 [모범 사례](https://developer.adobe.com/commerce/php/best-practices/extensions/)를 따르고 있는지 확인하십시오.

## [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool]은(는) 인스턴스를 분석하여 잠재적인 업그레이드 문제를 분석하는 명령줄 도구입니다. 설치한 현재 버전과 업그레이드하려는 버전 사이의 문제를 확인합니다.

이 도구 도구를 사용하면 팀 내에서 업그레이드의 범위 및 영향을 이해하는 데 필요한 노력이 줄어듭니다. 업그레이드할 때 일반적인 코드 문제를 방지하는 데 도움이 되며 식별된 문제를 해결하는 방법에 대한 명확한 지침을 제공합니다. 또한 성공적인 업그레이드를 보장하는 데 필요한 가장 중요 문제의 우선 순위를 지정하여 업그레이드 시 시간과 비용을 모두 절약할 수 있습니다.

시작하려면 [!DNL Upgrade Compatibility Tool]다음 섹션을 참조하십시오. [!DNL Upgrade Compatibility Tool] [기술 세부 사항 및 고급 사용 사례에 대해서는 안내서](../upgrade-compatibility-tool/overview.md) 를 참조하십시오.

### 도구 다운로드

Composer를 사용하여 도구 다운로드. PHP 7.3 이상, 최소 2GB RAM, Node.js(GraphQL 호환성을 확인하는 경우) 및 Adobe Systems Commerce 라이선스가 필요합니다.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### 도구 실행

인스턴스 분석하고 오류, 경고 및 중요 문제를 확인하려면 다음을 수행합니다.

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> `<dir>` 인수는 코드베이스가 저장되는 디렉토리입니다. 이 `-c` 옵션은 코드 베이스를 지정된 버전과 비교합니다.

팀 해결해야 할 가장 중요 문제를 식별하려면:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

이 명령에 사용할 몇 가지 추가 옵션은 다음과 같습니다.

- `--ignore-current-version-compatibility-issues` - 현재 버전에 대해 알려진 모든 심각한 문제, 오류 및 경고를 표시하지 않습니다. 업그레이드하려는 버전에 대한 오류만 제공합니다.

- `--min-issue-level`—업그레이드와 관련하여 가장 중요한 문제만 우선 순위를 지정하는 데 도움이 되도록 최소 문제 수준을 설정할 수 있습니다. 심각도의 오름차순으로 경고, 오류 및 위험 옵션이 표시됩니다.

- `-m | [=MODULE-PATH]`—특정 공급업체, 모듈 또는 디렉터리만 분석하려는 경우 경로를 옵션으로 지정할 수도 있습니다.

- `--vanilla-dir` - 비표준 기능 구현 또는 사용자 지정에 대한 핵심 코드를 확인할 수 있습니다. 이것들은 미리 청소하는 것이 중요하다. 참조를 위해 버전의 바닐라 인스턴스가 자동으로 다운로드됩니다.

  >[!NOTE]
  >
  > 이 작업은 도구의 `core:code:changes` 명령으로 수행할 수도 있습니다.

### 출력 분석

[!DNL Upgrade Compatibility Tool]은(는) 영향을 받는 코드 또는 모듈, 심각도 및 발생하는 모든 문제에 대한 문제 설명을 식별하는 JSON 파일을 내보냅니다. 또한 복잡도 점수가 있는 요약 보고서를 출력하므로 팀이 최신 버전으로 업그레이드하는 데 필요한 사항을 대략적으로 이해할 수 있습니다. 복잡성 점수가 낮을수록 업그레이드를 쉽게 수행할 수 있습니다.

다음 출력은 요약 보고서의 예를 보여줍니다.

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### 팁과 조언

도구 내에서 식별된 모든 문제는 특정 오류 코드와 함께 보고서에 나열됩니다. 오류 메시지 참조](../upgrade-compatibility-tool/error-messages.md)를 [사용하여 각 문제에 대한 자세한 내용을 확인할 수 있습니다. 또한 Adobe Systems 는 수정 단계를 계획할 수 있도록 각 문제 유형의 문제를 해결하기 위한 제안 사항을 제공합니다.

보고서를 사용하여 업그레이드를 위해 코드를 업데이트하는 데 필요한 작업량을 예측할 수 있습니다. 경험을 기반으로 식별된 총 문제 수와 문제의 심각도를 기반으로 업그레이드에 필요한 노력을 예상할 수 있습니다. 명령줄 도구 이므로 자동화된 테스트 및 코드 검사 도구 모음에 통합하고 JSON 출력을 사용하여 보고서를 생성할 수 있습니다.

향후 업그레이드 결과를 이전 결과와 비교할 수 있도록 각 업그레이드 프로젝트의 결과를 저장하는 것이 좋습니다. 계속해서 사용하면 도구에서 제공하는 요약 보고서에서만 다음 버전으로 업그레이드하는 데 필요한 작업 수준을 파악할 수 있습니다.

또한 업그레이드 작업을 수행하는 동안 도구를 정기적으로 실행하여 진행 상황을 확인하는 것이 좋습니다. 문제를 수정하면 문제 수가 줄어듭니다. 이는 팀이 작업을 분배하는 최상의 방법을 결정하는 데에도 도움이 됩니다.

[!DNL Upgrade Compatibility Tool]은(는) 지속적으로 개선되며 향후 릴리스에는 문제를 최대한 빨리 해결하는 데 도움이 되는 자동 수정 등의 기능이 포함됩니다. 2022년 1월에 발표된 최신 개선 사항에는 업그레이드 시 더 많은 노력이 필요할 수 있는 영역을 빠르게 식별하는 데 도움이 되는 PHP 8.1 호환성 테스트 및 HTML 시각화 기능이 포함되어 있습니다.
