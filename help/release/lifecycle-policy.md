---
title: 소프트웨어 수명 주기 정책
description: Adobe Commerce 릴리스에 대한 소프트웨어 지원 종료 관련 주요 일정에 대해 알아봅니다.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
nudge: true
source-git-commit: ed2757282c079ea7399d4df92000f346aecfbdd8
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 1%

---


# Adobe Commerce 라이프사이클 정책

Adobe Commerce 라이프사이클 정책을 간소화하고 고객의 미션 크리티컬 요구 사항을 지원하기 위해 Adobe은 각 버전에 대한 일반 가용성(GA) 날짜로부터 3년의 표준 지원 기간을 제공하며 이 기간 동안 품질 수정 사항을 릴리스합니다. 각 릴리스에 대한 소프트웨어 지원 종료에 대한 날짜 및 자세한 내용은 [소프트웨어 지원 종료](#end-of-software-support) 표를 참조하십시오.

Adobe은 고객이 Adobe Commerce에 대해 3년 또는 연장된 지원 기간에 있는 동안 수명이 종료될 수 있는 타사 서비스 및 소프트웨어 종속성(PHP 및 MySQL 등)에 대한 보안 및 품질 수정 사항을 제공하지 않습니다. 테스트되고 지원되는 타사 기술에 대한 전체 목록은 [시스템 요구 사항](../installation/system-requirements.md)을 참조하십시오.

## 표준 지원

GA(General Availability) 날짜로부터 3년의 표준 지원 기간. 표준 지원에는 품질 수정 사항, 보안 패치 및 전체 Adobe Commerce On-call 지원이 포함됩니다.

- **품질 수정** - 고객은 [Adobe Commerce 지원](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)에 문의하거나 셀프서비스 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 통해 품질 수정 사항에 액세스할 수 있습니다.

- **보안 수정 사항** - Adobe은 3년 지원 기간 동안 누적 보안 패치와 비누적 [격리된 보안 패치 파일](versioning-policy.md#isolated-security-patch-file)을 통해 보안 수정 사항을 제공합니다.

- **핫픽스** - 제로 데이 취약성과 같은 중요한 보안 문제에 대해 Adobe은 지원되는 버전의 모든 고객에게 최신 패치 또는 보안 패치 릴리스가 아닌 경우에도 [핫픽스](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)을 제공합니다. 핫픽스는 포괄적이지 않으며 최신 릴리스로 업그레이드하여 해결되는 모든 보안 문제를 해결하지는 않습니다.

## 확장 지원

Adobe은 고객이 가능한 한 빨리 업그레이드하도록 권장합니다. 그러나 업그레이드 계획 및 비즈니스 요구 사항에 맞게 보다 높은 유연성을 제공하기 위해 Adobe은 버전 2.4.6 및 2.4.7에서 Adobe Commerce 고객을 위해 추가 비용 없이 1년간의 추가 지원을 제공합니다. 지원 확장에는 핵심 애플리케이션에 대한 품질 및 보안 패치가 포함됩니다. Adobe Commerce 2.4.4 및 2.4.5 버전에 대한 확장 지원은 계획대로 2026년 4월과 8월에 종료됩니다.

>[!NOTE]
>
>Adobe은 Adobe Commerce on Cloud에 대한 강제 버전 업그레이드 정책을 도입합니다. **2027년 6월 1일**&#x200B;부터 Adobe은 더 이상 지원되지 않는 Commerce 버전을 실행하는 클라우드 환경을 유지 관리하지 않으며 해당 버전을 해제할 수 있는 권한을 보유합니다. Cloud에서 실행하는 경우 릴리스 라인에 게시된 [확장 지원 종료](lifecycle-policy.md#end-of-support-dates) 날짜 이전에 지원되는 Adobe Commerce 버전으로 이동하거나 [!DNL Adobe Commerce as a Cloud Service]&#x200B;(으)로 마이그레이션해야 합니다. 적용 날짜, 영향을 받는 버전 및 지원되지 않는 버전에 남아 있는 경우 발생하는 상황에 대해서는 [클라우드 버전 업그레이드 시행 정책](version-upgrade-enforcement-policy.md)을 참조하십시오.

## 보안 전용 전환 기간

확장 지원이 2025년 또는 2026년에 종료된 버전 2.4.4, 2.4.5 및 2.4.6에만 사용할 수 있는 일회성 제한 전환 기간입니다. 보안 전용 전환 기간은 제한적인 격리된 보안 수정 사항만 제공합니다. Adobe Commerce 품질 수정 사항은 제공되지 않습니다. 이 기간은 표준 또는 확장 지원에 해당되지 않으며 더 이상 연장되지 않습니다. 장기적인 지원 계층이 아닌 마이그레이션 기간으로 간주합니다.

>[!IMPORTANT]
>
>보안 전용 전환 기간은 1회 예외입니다. 게시된 날짜 이후로는 연장되지 않습니다. 보안 전용 기간을 장기 지원 계층이 아닌 마이그레이션 시간으로 처리합니다.

## 지원 종료 날짜

다음 표는 클라우드 환경의 Adobe Commerce에 대한 새 버전 업그레이드 적용 날짜를 포함하여 각 Adobe Commerce 버전에 대한 전체 라이프사이클을 보여 줍니다.

| 릴리스 | 일반 가용성 | 표준 지원 종료 | 확장 지원 종료 | 보안 전용 기간 종료 | [버전 업그레이드 적용 날짜(클라우드만 해당)](version-upgrade-enforcement-policy.md) |
| --------- | ---------------------- | ------------------------ | ------------------------- |-----------------------------| ----------------------------------------------- |
| Adobe Commerce 2.4.9 | 2026년 5월 12일 | 2029년 5월 31일 | TBD | 해당 사항 없음 | TBD |
| Adobe Commerce 2.4.8 | 2025년 4월 8일 | 2028년 5월 31일 | TBD | 해당 사항 없음 | TBD |
| Adobe Commerce 2.4.7 | 2024년 4월 9일 | 2027년 5월 31일 | 2028년 5월 31일 | 해당 사항 없음 | 2028년 6월 1일 |
| Adobe Commerce 2.4.6 | 2023년 3월 14일 | 2026년 8월 11일 | 2027년 8월 30일 | 2028년 5월 31일 | 2028년 6월 1일 |
| Adobe Commerce 2.4.5 | 2022년 8월 9일 | 2025년 8월 12일 | 2026년 8월 12일 | 2027년 5월 31일 | 2027년 6월 1일 |
| Adobe Commerce 2.4.4 | 2022년 4월 12일 | 2025년 4월 12일 | 2026년 4월 14일 | 2027년 5월 31일 | 2027년 6월 1일 |

{style="table-layout:auto"}

## 지원 타임라인

지원 타임라인은 각 Adobe Commerce 릴리스 라인에 대한 지원 기간을 분기별로 매핑합니다. 정확한 종료 날짜는 이 항목의 앞에 제공된 표를 사용하십시오.

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="1"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
    <th colspan="4">2028</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>분기 3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>분기 3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>분기 3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>분기 3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>분기 3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>분기 3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>분기 3</td>
    <td>Q4</td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="5" style="background-color:#FFBF00"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="2"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**키**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;"></td>
   <td>표준 지원</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>확장 지원</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>확장된 보안 수정 사항</td>
  </tr>
 </tbody>
</table>

## 플랫폼 종속성

지원되는 Commerce 릴리스를 계속 사용하려면 지원되는 플랫폼 종속성도 필요합니다. Adobe은 Adobe Commerce에 대한 지원 기간이 3년이거나 연장된 상태에서 수명이 종료될 수 있는 MariaDB, OpenSearch, Redis, Valkey, RabbitMQ 등과 같은 타사 서비스 및 소프트웨어 종속성에 대한 보안 및 품질 수정 사항을 제공하지 않습니다. 자세한 내용은 [공유 권한 보안 및 운영 모델](../security-and-compliance/shared-responsibility.md)을 참조하세요.

적극적으로 지원되는 버전에 대한 모든 타사 종속성 및 플랫폼 서비스를 유지 관리할 책임이 있습니다. 테스트 및 지원되는 타사 기술의 전체 목록은 [시스템 요구 사항](../installation/system-requirements.md)을 참조하십시오.

>[!IMPORTANT]
>
>지원되지 않는 종속성 버전을 실행하면 Adobe에서 해결할 수 없는 클라우드 인스턴스의 보안 취약성이 발생할 수 있습니다. 이러한 경우 Adobe은 Adobe Commerce 버전 지원 상태에 관계없이 영향을 받는 소프트웨어 종속성을 업그레이드하거나 업그레이드할 수 없는 경우 인스턴스를 해제할 수 있는 권한을 보유합니다.

## PHP 수명 종료 및 PCI 규정 준수

사용자는 환경에서 사용되는 PHP 버전의 지원 상태를 모니터링할 책임이 있습니다.

이전 Commerce 릴리스 라인에서 사용된 다음 PHP 버전은 수명이 종료되었거나 도달하므로 PCI 규정 준수에 직접적인 영향을 미칩니다.

| PHP 버전 | 수명 종료 날짜 | 영향을 받는 Commerce 버전 | PCI 규정 준수 영향 |
| ------------- | ------------------ | ---------------------------- | ------------------------ |
| PHP 8.1 | 2025년 12월 31일 | 2.4.4, 2.4.5 및 2.4.6(여기서 PHP 8.1이 사용됨) | PCI 규정 준수 위험 — 수명 종료 날짜가 지난 후 PHP 8.1을 실행하면 PHP의 보안 취약점이 수정되지 않아 PCI 규정 준수가 위험해질 수 있습니다. 규정 준수 상태를 평가하고 업그레이드의 우선 순위를 지정합니다. |
| PHP 8.2 | 2026년 12월 31일 | 2.4.6 (여기서 PHP 8.2가 사용됨) | 2026년 말부터 PCI 규정 준수 위험 발생 — PCI 규정 준수를 유지하기 위해 2026년 말 이전에 업그레이드 또는 마이그레이션을 계획합니다. |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>**PCI 준수 알림:** PCI 준수는 판매자의 평가 책임입니다. Adobe은 영향을 받는 버전의 판매자는 자격 있는 보안 평가자와 상의하고 가능한 한 빨리 지원되는 Commerce 버전 및 지원되는 PHP 버전으로 이동하는 것을 우선시 할 것을 강력히 권장합니다. PHP 지원 타임라인은 [PHP 지원 버전](https://www.php.net/supported-versions.php) 및 [PHP 수명 종료](https://www.php.net/eol.php)를 참조하십시오.

## 업그레이드 및 마이그레이션 옵션

지원 종료 날짜가 가까워지거나 지난 버전을 사용 중인 경우 지금 조치를 취하십시오. 지원되지 않는 버전을 유지하면 보안 취약성, 규정 준수 문제 및 지원 손실의 위험이 스토어에 발생합니다. Adobe은 지원되는 릴리스로 이동할 수 있는 다음 경로를 제공합니다.

### 권장 경로: Adobe Commerce as a Cloud Service으로 마이그레이션

[!DNL Adobe Commerce as a Cloud Service]은(는) Adobe의 차세대 호스팅 상거래 플랫폼이며 모든 Adobe Commerce on Cloud 고객을 위해 Adobe이 권장하는 장기 도착지입니다.

- Adobe은 모든 인프라, 패치 및 업그레이드를 자동으로 관리합니다.
- 항상 지원되는 규정 준수 인프라스트럭처를 사용하고 있습니다. 서비스 종료 상황은 재발하지 않습니다.
- AI 기반 머천다이징, 구성 가능한 상점 아키텍처 및 기본 Adobe Experience Cloud 통합과 같은 Adobe의 최신 기능에 액세스할 수 있습니다.
- 반복되는 업그레이드 주기를 제거합니다.

Adobe 계정 팀에 문의하여 마이그레이션 평가를 시작합니다. 제품 개요는 [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview)을 참조하세요.

### 대체 경로: 지원되는 Adobe Commerce on cloud 또는 온프레미스 릴리스로 업그레이드

[!DNL Adobe Commerce as a Cloud Service]&#x200B;(으)로 즉시 마이그레이션할 수 없는 경우 Cloud 릴리스에서 현재 지원되는 최신 Adobe Commerce으로 업그레이드할 수 있습니다. 이렇게 하면 기존 Commerce on Cloud 배포 모델을 유지하면서 완전히 지원되는 최신 인프라 스택으로 이동합니다.

이 경로는 향후 업그레이드 의무를 없애지 않습니다. Adobe Commerce on Cloud 배포를 사용하는 고객은 릴리스 라인이 버전 업그레이드 적용 날짜에 도달하므로 계속 업그레이드해야 합니다.
