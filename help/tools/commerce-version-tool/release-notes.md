---
title: '[!DNL Commerce Version Tool] 릴리스 정보'
description: 새 패치 상태 보고, CVE 보호 상태, CSV 출력 및 캐시 동작을 포함한  [!DNL Commerce Version Tool] 릴리스에 대해 알아봅니다.
feature: Release Notes
TQID: 'https://experienceleague.adobe.com/38I3U5y9rmurP5gVhalfUq7DlcUb-JpF5eUam1nwEyk'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 180
ht-degree: 2%

---

# [!DNL Commerce Version Tool] 릴리스 정보

이 릴리스 노트는 [!DNL Commerce Version Tool]&#x200B;([!DNL CVT])의 업데이트에 대해 설명합니다.

## 버전 1.0.0 — 2026년 6월 {#version-1-0-0}

### 새로운 기능

- **패치 상태 보고** - 월간 Adobe Commerce 보안 패치가 적용되거나 누락되었거나 Adobe Commerce 설치에 대해 분류할 수 없는 항목을 보고합니다.
- **CVE 보호 상태** - 패치 결과를 CVE별 보호 상태 값 `PROTECTED`, `VULNERABLE`, `UNKNOWN` 및 `NOT_APPLICABLE`에 매핑합니다.
- **다중 구성 요소 지원** - Adobe Commerce B2B(business-to-business), Adobe Commerce Page Builder, Adobe Commerce Inventory 및 패치 레지스트리 파일에 표시되는 기타 구성 요소를 포함하여 `composer.lock`에서 설치된 Adobe Commerce 구성 요소를 검색합니다.
- **JSON 및 CSV 출력** - 프로그래밍 방식 사용에 대한 JSON 출력 및 스프레드시트, 스캐너, 대시보드 및 규정 준수 도구에 대한 CSV 출력을 기본적으로 제공합니다.
- **오프라인 캐시 동작** - 각 가져오기 성공 후 패치 레지스트리 파일을 로컬로 캐시합니다. 원격 레지스트리를 사용할 수 없는 경우 [!DNL CVT] 도구는 캐시된 레지스트리를 경고와 함께 사용할 수 있습니다.
- **번들 게재** - 월별 Adobe Commerce 보안 패치 파일 내에 제공됩니다. 패치를 적용하면 별도의 설치 단계 없이 `vendor/bin/patch-status`에 [!DNL CVT]이(가) 설치됩니다.

## 관련 항목

- [소개](intro.md)
- [패치 상태 보고서 생성](generate-report.md)
- [문제 해결](troubleshooting.md)
