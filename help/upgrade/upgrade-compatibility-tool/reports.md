---
title: '[!DNL Upgrade Compatibility Tool]개 보고서'
description: 다음 단계에 따라 Adobe Commerce 프로젝트에서  [!DNL Upgrade Compatibility Tool] 을(를) 실행합니다.
exl-id: a2272339-46d6-443b-bd53-286b72f13d4e
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# 보고서

{{commerce-only}}

분석 결과 [!DNL Upgrade Compatibility Tool]은(는) 심각도, 오류 코드 및 오류 설명을 지정하는 각 파일에 대한 문제 목록이 포함된 보고서를 내보낼 수 있습니다. [!DNL Upgrade Compatibility Tool]에서 보고서를 두 가지 형식으로 내보냅니다.

- [JSON 파일](reports.md#json-file).
- [HTML 보고서](reports.md#html-report).

보고서의 다음 명령줄 인터페이스 예를 참조하십시오.

```
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

이 보고서에서 생성할 수 있는 다양한 오류에 대한 자세한 내용은 [오류 메시지 참조](../upgrade-compatibility-tool/error-messages.md) 항목을 확인하십시오.

이 보고서에는 다음을 보여주는 자세한 요약도 포함되어 있습니다.

- *현재 버전*: 현재 설치된 버전입니다.
- *대상 버전*: 업그레이드할 버전입니다.
- *실행 시간*: 분석이 보고서를 작성하는 데 걸린 시간(mm:ss).
- *업데이트가 필요한 모듈*: 호환성 문제가 있고 업데이트가 필요한 모듈의 비율입니다.
- *업데이트가 필요한 파일*: 호환성 문제가 있고 업데이트가 필요한 파일의 비율입니다.
- *총 중대 오류*: 발견된 중대 오류 수입니다.
- *총 오류*: 발견된 오류 수
- *총 경고*: 발견된 경고 수.
- *메모리 피크 사용*: 실행 중에 [!DNL Upgrade Compatibility Tool]의 최대 메모리 양에 도달했습니다.

다음 명령줄 인터페이스 예를 참조하십시오.

```
 ----------------------------- ----------------- 
  Current version               2.4.1            
  Target version                2.4.4            
  Execution time                1m:8s            
  Modules that require update   71.67% (43/60)   
  Files that require update     18.05% (96/532)  
  Total critical issues         24               
  Total errors                  159              
  Total warnings                53               
  Memory peak usage             902.00 MB        
 ----------------------------- ----------------- 
```

## JSON 파일

명령줄 인터페이스에서 [!DNL Upgrade Compatibility Tool]을(를) 실행하는 동안 JSON 파일 출력을 가져올 수 있습니다. `JSON` 파일에 [!DNL Upgrade Compatibility Tool] 출력에 표시된 것과 동일한 정보가 포함되어 있습니다.

- 식별된 문제 목록.
- 분석 요약입니다.

발견된 각 문제에 대해, 보고서는 문제의 심각도 및 설명과 같은 자세한 정보를 제공합니다.

이 `JSON` 파일을 다른 출력 폴더로 내보내려면 다음을 수행하십시오.

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

여기서 인수는 다음과 같습니다.

- `<dir>`: Adobe Commerce 설치 디렉터리.
- `[=JSON-OUTPUT-PATH]`: `JSON` 출력 파일을 내보낼 경로 디렉터리입니다.

>[!NOTE]
>
> 출력 폴더의 기본 경로는 `var/output/[TIME]-results.json`입니다.

## HTML 보고서

명령줄 인터페이스 또는 [!DNL Site-Wide Analysis Tool]을(를) 통해 도구를 실행하는 동안 HTML 보고서를 가져올 수 있습니다. HTML 보고서에는 다음도 포함되어 있습니다.

- 식별된 문제 목록.
- 분석 요약입니다.

![HTML 보고서 - 요약](../../assets/upgrade-guide/uct-html-summary.png)

[!DNL Upgrade Compatibility Tool] 분석 중에 식별된 문제를 쉽게 탐색할 수 있습니다.

보고서에 표시된 문제를 최소 문제 수준에 따라 필터링할 수 있습니다(기본값은 `WARNING`).

오른쪽 상단 모서리에는 다른 수준을 선택할 수 있는 드롭다운이 있습니다. 식별된 문제 목록은 그에 따라 필터링됩니다.

![HTML 보고서 - 드롭다운 사용](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> 문제 수준이 낮은 문제는 제거되지만 알림을 받게 되므로 모듈별로 식별된 문제를 항상 알 수 있습니다.

HTML 보고서에는 네 개의 다른 차트가 포함됩니다.

- **문제 심각도별 모듈**: 모듈별 심각도 분포를 표시합니다.
- **문제 심각도별 파일**: 파일별 심각도 분포를 표시합니다.
- **총 문제 수로 정렬된 모듈**: 경고, 오류 및 심각한 오류를 고려하여 가장 많이 손상된 10개의 모듈을 표시합니다.
- **상대적인 크기 및 문제가 있는 모듈**: 모듈에 포함된 파일이 많을수록 원이 커집니다. 모듈에 문제가 많을수록 해당 원이 더 빨간색으로 표시됩니다.

이러한 차트를 통해 가장 많이 손상된 모듈과 업그레이드를 수행하는 데 더 많은 작업이 필요한 모듈을 식별할 수 있습니다.

![HTML 보고서 - 다이어그램](../../assets/upgrade-guide/uct-html-diagrams.png)

HTML 보고서 다이어그램도 이에 따라 업데이트됩니다. `Modules with relative sizes and issues`은(는) 원래 설정된 `min-issue-level`과(와) 함께 생성됩니다.

`Modules with relative sizes and issues` 다이어그램에 대해 다른 결과를 보려면 `--min-issue-level` 옵션에 대해 다른 값을 제공하는 명령을 다시 실행해야 합니다.

![HTML 보고서 - 버블 차트 다이어그램](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

이 HTML 보고서를 다른 출력 폴더로 내보내려면 다음을 수행하십시오.

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

여기서 인수는 다음과 같습니다.

- `<dir>`: Adobe Commerce 설치 디렉터리.
- `[=HTML-OUTPUT-PATH]`: `.html` 출력 파일을 내보낼 경로 디렉터리입니다.

>[!NOTE]
>
> 출력 폴더의 기본 경로는 `var/output/[TIME]-results.html`입니다.
