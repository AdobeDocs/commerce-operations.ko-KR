---
title: '"[!DNL Upgrade Compatibility Tool] 보고서"'
description: 다음 단계에 따라 을(를) 실행합니다 [!DNL Upgrade Compatibility Tool] Adobe Commerce 프로젝트에서 확인하십시오.
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# 보고서

{{commerce-only}}

분석 결과, [!DNL Upgrade Compatibility Tool] 심각도, 오류 코드 및 오류 설명을 지정하는 각 파일에 대한 문제 목록이 포함된 보고서를 내보냅니다.

아래 예를 참조하십시오.

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

을(를) 확인합니다. [오류 메시지 참조](../upgrade-compatibility-tool/error-messages.md) 주제 를 참조하십시오.

이 보고서에는 다음과 같은 세부 요약이 포함되어 있습니다.

- *현재 버전*: 현재 설치된 버전입니다.
- *Target 버전*: 업그레이드할 버전입니다.
- *실행 시간*: 분석을 통해 보고서를 작성하는 데 걸린 시간(mm:ss)입니다.
- *업데이트가 필요한 모듈*: 호환성 문제가 있고 업데이트가 필요한 모듈의 비율입니다.
- *업데이트가 필요한 파일*: 호환성 문제가 있고 업데이트가 필요한 파일의 비율입니다.
- *총 위험 오류*: 발견된 중요한 오류 수입니다.
- *총 오류*: 발견된 오류 수입니다.
- *총 경고 수*: 찾은 경고 수

아래 예를 참조하십시오.

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>기본적으로 [!DNL Upgrade Compatibility Tool] 보고서를 다음 두 가지 형식으로 내보냅니다. `json` 및 `html`.

## JSON 파일

JSON 파일에는 출력에 표시된 것과 동일한 정보가 포함되어 있습니다.

- 식별된 문제 목록입니다.
- 분석 요약.

발생한 각 문제에 대해 보고서는 문제의 심각도와 설명과 같은 자세한 정보를 제공합니다.

이 보고서를 다른 출력 폴더로 내보내려면 다음을 실행하십시오.

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

여기서 인수는 다음과 같습니다.

- `<dir>`: Adobe Commerce 설치 디렉토리.
- `[=JSON-OUTPUT-PATH]`: 내보낼 경로 디렉토리 `.json` 출력 파일입니다.

>[!NOTE]
>
>출력 폴더의 기본 경로는 다음과 같습니다. `var/output/[TIME]-results.json`.

## HTML 보고서

HTML 파일에는 분석 요약 및 식별된 문제 목록도 포함되어 있습니다. 명령줄 인터페이스 또는 를 통해 도구를 실행하는 동안 HTML 보고서를 가져올 수 있습니다. [!DNL Site-Wide Analysis Tool].

![HTML 보고서 - 요약](../../assets/upgrade-guide/uct-html-summary.png)

에서 식별된 문제를 쉽게 탐색할 수 있습니다 [!DNL Upgrade Compatibility Tool] 분석:

![HTML 보고서 - 세부 정보](../../assets/upgrade-guide/uct-html-details.png)

HTML 보고서에는 4개의 차트도 포함되어 있습니다.

- **문제 심각도별 모듈**: 모듈별 심각도 분포를 표시합니다.
- **문제 심각도별 파일**: 파일별 심각도 배포를 표시합니다.
- **총 문제 횟수로 정렬된 모듈입니다**: 경고, 오류 및 위험 오류를 고려하여 가장 손상된 10개의 모듈을 표시합니다.
- **관련 크기 및 문제가 있는 모듈**: 모듈에 있는 파일이 많을수록 원이 커집니다. 모듈에 문제가 많을수록 원형이 더 나타납니다.

이러한 차트를 사용하면 가장 손상된 부품과 업그레이드를 수행하는 데 더 많은 작업이 필요한 부품을 한눈에 파악할 수 있습니다.

![HTML 보고서 - 다이어그램](../../assets/upgrade-guide/uct-html-diagrams.png)

최소 문제 수준에 따라 보고서에 표시되는 문제를 필터링할 수 있습니다. 기본값은 입니다. `WARNING`.

오른쪽 상단 모서리에는 필요에 따라 다른 드롭다운을 선택할 수 있는 드롭다운이 있습니다. 식별된 문제 목록은 그에 따라 필터링됩니다.

![HTML 보고서 - 드롭다운 사용](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

낮은 문제 수준의 문제는 제거되지만 알림이 표시되므로 모듈별로 식별된 문제가 항상 인식됩니다.

또한 다이어그램은 `Modules with relative sizes and issues`: `min-issue-level` 원래 설정

다른 결과를 보려면, `--min-issue-level` 선택 사항입니다.

![HTML 보고서 - 버블 차트 다이어그램](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

이 보고서를 다른 출력 폴더로 내보내려면 다음을 수행하십시오.

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

여기서 인수는 다음과 같습니다.

- `<dir>`: {{site.data.var.ee}} 설치 디렉터리입니다.
- `[=HTML-OUTPUT-PATH]`: 내보낼 경로 디렉토리 `.html` 출력 파일입니다.

>[!NOTE]
>
> 출력 폴더의 기본 경로는 다음과 같습니다. `var/output/[TIME]-results.html`.
