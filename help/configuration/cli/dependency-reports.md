---
title: 종속성 보고서
description: Adobe Commerce의 모듈, 순환 및 프레임워크 종속성을 보여 주는 종속성 보고서를 만드는 방법을 알아봅니다. 분석 및 보고 도구를 살펴봅니다.
exl-id: b7a32fe1-71c5-495f-8276-242503fb50ae
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# 종속성 보고서

{{file-system-owner}}

다음 유형의 보고서를 실행할 수 있습니다.

- **모듈 종속성**: 모듈 간의 총 종속성 수와 해당 종속성이 하드 또는 소프트 종속성인지 여부를 표시합니다.
- **순환 종속성**: 각 모듈에 대한 전체 종속성 체인 수와 순환 종속성 수 및 목록을 표시합니다.
- **프레임워크 종속성**: 모듈별 Commerce 프레임워크에 대한 총 종속성 수를 표시합니다(각 라이브러리에 대한 프레임워크 항목의 총 수 포함).

주석의 종속성도 종속성입니다.

## 종속성 보고서 실행

명령 옵션:

```bash
bin/magento info:dependencies:{show-modules|show-modules-circular|show-framework} [-d|--directory="<path>"] [-o|--output="<path and filename"]
```

다음 표에서는 이 명령의 옵션, 매개 변수 및 값에 대해 설명합니다.

| 매개 변수 | 값 | 필수? |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- | --------- |
| `show-modules` | 모듈 종속성 보고서입니다. | 예 |
| `show-modules-circular` | 순환 종속성 보고서. | 예 |
| `show-framework` | 프레임워크 종속성 보고서입니다. | 예 |
| `-d --directory` | 보고서 데이터 검색을 시작할 기본 디렉토리 경로. | 아니요 |
| `-o --output` | 보고서에 대한 쉼표로 구분된 값(csv) 출력 파일의 절대 파일 시스템 경로 및 파일 이름을 지정합니다. | 아니요 |

디렉터리나 파일 이름이 인수로 전달되지 않으면 다음 응용 프로그램 루트가 기본 디렉터리로 사용되고 다음 기본 파일 이름이 사용됩니다.

| 명령 | 파일 이름 |
| ----------------------------------------------------- | ----------------------------------- |
| `bin/magento info:dependencies:show-modules` | `modules-dependencies.csv` |
| `bin/magento info:dependencies:show-modules-circular` | `modules-circular-dependencies.csv` |
| `bin/magento info:dependencies:show-framework` | `framework-dependencies.csv` |

### 샘플 모듈 종속성 보고서

다음은 샘플 모듈 종속성 보고서에 대한 출력의 일부입니다.

```
"","All","Hard","Soft"
"Total number of dependencies","602","587","15"

"Dependencies for each module:","All","Hard","Soft"
"magento/module-cron","2","2","0"
" -- magento/module-config","","1","0"
" -- magento/module-store","","1","0"

"magento/module-catalog-rule","8","8","0"
" -- magento/module-store","","1","0"
" -- magento/module-rule","","1","0"
" -- magento/module-catalog","","1","0"
" -- magento/module-customer","","1","0"
" -- magento/module-backend","","1","0"
" -- magento/module-eav","","1","0"
" -- magento/module-indexer","","1","0"
" -- magento/module-import-export","","1","0"
```

### 샘플 순환 종속성 보고서

다음은 샘플 순환 종속성 보고서에 대한 출력의 일부입니다.

```
"Circular dependencies:","Total number of chains"
"","848"

"Circular dependencies for each module:",""
"magento/module-config","70"
"magento/module-config->magento/module-store->magento/module-directory->magento/module-config"
"magento/module-config->magento/module-store->magento/module-config"
"magento/module-config->magento/module-cron->magento/module-config"
"magento/module-config->magento/module-email->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-theme->magento/module-customer->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-reports->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-theme->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-log->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-catalog-inventory->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-theme->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-payment->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-themeax->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-catalog-rule->magento/module-rule->magento/module-eav->magento/module-config"
```

### 샘플 프레임워크 종속성 보고서

다음은 샘플 프레임워크 종속성 보고서에 대한 출력의 일부입니다.

```
"Dependencies of framework:","Total number"
"","111"

"Dependencies for each module:",""
"Magento\Cron","1"
" -- Magento\Framework","143"

"Magento\CatalogRule","1"
" -- Magento\Framework","234"

"Magento\Webapi","2"
" -- Magento\Framework","347"
" -- Magento\Server","1"

"Magento\Checkout","1"
" -- Magento\Framework","759"

"Magento\Reports","1"
" -- Magento\Framework","553"
```
