---
title: '[!DNL Commerce Version Tool]'
description: Adobe Commerce용  [!DNL Commerce Version Tool] 에 대해 알아보고 공급업체/bin/patch-status를 사용하여 월별 보안 패치 상태를 확인하십시오.
TQID: 'https://experienceleague.adobe.com/9lDQtCrcCSIFjt3jUJkqCo-rMlIhhy3tPTtPyT4wt1Q'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 586
ht-degree: 0%

---

# [!DNL Commerce Version Tool]

Adobe Commerce의 월별 보안 패치는 비누적되며 순차적으로 적용해야 합니다. [!DNL Commerce Version Tool]&#x200B;([!DNL CVT])을(를) 사용하면 판매자가 설치한 월별 보안 패치, 누락된 패치 및 설치를 방지하는 CVE를 보고하여 패치 적용 범위를 확인할 수 있습니다.

>[!IMPORTANT]
>
>[!DNL CVT] 도구는 정보 제공용입니다. 패치를 적용하거나 패치를 되돌리거나 Adobe Commerce 소스 파일을 수정하지 않습니다. 패치 상태 보고를 지원하기 위해 캐시 파일, 임시 드라이-런 파일 및 감사-로그 항목을 쓸 수 있습니다.

## 도구 개요

[!DNL CVT] 도구는 월간 Adobe Commerce 보안 패치 각각에 포함된 독립 실행형 실행 파일입니다. 패치가 Adobe Commerce 설치에 적용되면 도구가 `vendor/bin/patch-status`에 설치됩니다. PHP 8.1 이상과 시스템 `patch` 바이너리가 필요합니다. Composer 패키지, 비표준 PHP 확장, Adobe Commerce 부트스트랩 또는 별도의 설치 단계가 필요하지 않습니다.

[!DNL CVT] 도구를 통해 다음을 수행할 수 있습니다.

- 지원되는 Adobe Commerce 설치에 대해 적용된 보안 패치를 검색합니다.
- 월별로 격리된 보안 패치 시퀀스에서 누락된 패치를 식별합니다.
- 패치 관련 CVE (Common Vulnerabilities and Exposes) 레코드에 대한 보호, 취약성 또는 알 수 없는 보안 상태를 보고합니다.
- 스캐너, 대시보드 및 규정 준수 보고를 위해 JSON 또는 CSV와 같이 시스템에서 읽을 수 있는 출력을 생성합니다.
- 지원되는 플랫폼 및 구성 요소에 대한 패치 상태를 감지합니다.

## 가용성

Adobe에서 패치 레지스트리 파일에 설치된 버전에 대한 패치 메타데이터를 제공할 때 [!DNL CVT] 도구는 다음 플랫폼 및 구성 요소에 대한 패치 상태 보고를 지원합니다.

| 플랫폼 또는 구성 요소 | 가용성 |
| --- | --- |
| Adobe Commerce 온-프레미스 | 지원됨 |
| [!DNL Magento Open Source] | 지원됨 |
| Adobe Commerce business-to-business (B2B) | 설치 시 지원됨 |
| Adobe Commerce 페이지 빌더 | 설치 시 지원됨 |
| Adobe Commerce 인벤토리 | 설치 시 지원됨 |
| `composer.lock`에서 추가 구성 요소가 검색되었습니다. | 패치 레지스트리 파일에 표시될 때 지원됨 |

{style="table-layout:auto"}

## 일반적인 사용 사례

다음을 수행해야 하는 경우 [!DNL CVT] 도구를 사용합니다.

- Adobe Commerce 설치에 필요한 격리된 보안 패치가 포함되어 있는지 확인합니다.
- 건너뜀 또는 불완전한 패치 세트가 CVE 커버리지를 불완전하게 유지하는지 확인합니다.
- 내부 보고 또는 자동화된 스캔을 위해 JSON 또는 CSV 출력을 생성합니다.
- 지원 요청을 열거나 수정을 계획하기 전에 패치 상태 정보를 제공합니다.

## 결과 사용 지침

[!DNL CVT] 도구 출력을 패치 계획 및 보안 검토를 지원하는 검색 데이터로 처리합니다.

다음 지침을 따르십시오.

- 안정적이고 지원되는 Adobe Commerce 설치에 대해 [!DNL CVT] 도구를 실행합니다.
- 보안 상태를 청구하기 전에 누락 및 알 수 없는 패치를 검토하십시오.
- 감사 및 자동화를 위해 JSON 또는 CSV 출력 유지.
- 스캔 출력을 보안 관련 운영 데이터로 처리합니다.
- 지원 또는 복구에 필요한 세부 정보만 공유합니다.

## 패치 감지

[!DNL CVT] 도구는 고정된 두 단계로 검색을 실행합니다. 두 단계 모두 패치 상태 보고서를 생성할 때 항상 실행됩니다.

- **작성기 검색:** 도구는 `composer.lock` 파일을 읽고 [!DNL Adobe Commerce] 기본 버전 및 설치된 구성 요소 영역을 확인합니다. 기본 버전을 감지할 수 없으면 `1` 코드로 종료됩니다.

- **시험 실행 감지:** 적용 가능한 각 패치에 대해 도구는 패치 변경 내용에 대한 시험 실행 검사를 사용하여 패치가 이미 적용되었는지, 적용되지 않았는지, 또는 패치 상태를 알 수 없는지 확인합니다. 이 도구는 이 검사 중에 패치 종속성을 처리하므로 결과가 설치된 구성 요소 버전을 반영하도록 합니다.

이 보고서에는 감지된 설치 및 설치된 구성 요소에 적용되는 패치만 포함됩니다. 툴이 적용 가능한 패치가 있는지 확인할 수 없는 경우 해당 패치를 알 수 없는 패치로 분류합니다.

## [!DNL CVT] 사용 시작

패치 상태 보고를 생성, 문제 해결 및 추적하려면 다음 항목을 사용하십시오.

- [패치 상태 보고서를 생성](generate-report.md)하여 [!DNL CVT] 도구를 실행하고, 명령 옵션을 검토하고, 보고서 결과를 해석합니다.
- 예기치 않은 결과 또는 명령 오류를 해결하기 위해 [[!DNL Commerce Version Tool] 문제 해결](troubleshooting.md).
- 릴리스 업데이트를 검토하려면 [[!DNL Commerce Version Tool] 릴리스 정보](release-notes.md)를 참조하세요.
