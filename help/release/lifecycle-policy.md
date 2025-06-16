---
title: 소프트웨어 수명 주기 정책
description: Adobe Commerce 릴리스에 대한 소프트웨어 지원 종료 관련 주요 일정에 대해 알아봅니다.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 2e81a28502d369bc8903e6b9e9154e693260234d
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 3%

---


# Adobe Commerce 라이프사이클 정책

Adobe Commerce 2.4.4 및 후속 릴리스의 경우:

- Adobe Commerce 라이프사이클 정책을 간소화하고 고객의 미션 크리티컬 요구 사항을 지원하기 위해 Adobe은 지원 기간을 Adobe Commerce 2.4.4 이상의 GA(General Availability) 날짜부터 3년으로 확대했습니다. Adobe은 3년의 지원 기간 동안 2.4.4 이상 릴리스에 대한 품질 수정 사항을 제공합니다. 고객은 [Adobe Commerce 지원](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)에 연락하거나 해당 버전이 여전히 품질 지원에 적합한 경우 셀프 서비스 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을(를) 통해 품질 수정 사항에 액세스할 수 있습니다. 다음 표에서는 Adobe Commerce 릴리스 라인에 대한 소프트웨어 지원 종료 날짜에 대해 설명합니다.

- Adobe은 3년의 지원 기간 동안 보안 패치 릴리스를 통해 보안 수정 사항을 제공합니다.

- 제로 데이 취약성과 같은 중요한 보안 문제의 경우, Adobe은 지원되는 버전의 모든 고객을 위해 최신 패치 또는 보안 패치 릴리스가 아닌 경우에도 [핫픽스](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)를 제공합니다. 핫픽스는 포괄적이지 않으며 최신 릴리스로 업그레이드하여 해결되는 모든 보안 문제를 해결하지는 않습니다.

- Adobe은 Adobe Commerce에 대한 3년간의 지원 기간 동안 수명이 종료될 수 있는 타사 서비스 및 소프트웨어 종속성(PHP 및 MySQL 등)에 대한 보안 및 품질 수정 사항을 제공하지 않습니다. 테스트되고 지원되는 타사 기술에 대한 전체 목록은 [시스템 요구 사항](../installation/system-requirements.md)을 참조하십시오.

- 버전 2.4.4 및 2.4.5를 사용하는 Adobe Commerce on Cloud 고객의 경우 Adobe에서 PHP 8.1 라이프타임 보안 수정 사항을 인프라에 자동으로 적용하므로 이러한 고객은 PHP 8.1 지원 종료의 영향을 받지 않습니다. Adobe Commerce 2.4.4 및 2.4.5를 사용하는 온-프레미스 고객은 필요한 경우 Adobe 지원 센터에 문의하여 PHP 8.1 라이프타임 보안 패치를 요청해야 합니다.

- Adobe은 고객이 보안 전용 패치 릴리스의 범위에서 Adobe Commerce에 대한 3년 지원 기간을 사용하는 동안 타사 서비스 및 소프트웨어 종속성과의 호환성을 제공하지만, 이전 버전과 호환되지 않는 변경 사항을 도입하지 않고도 가능한 경우에만 가능합니다.

## 확장 지원

Adobe은 고객이 가능한 한 빨리 업그레이드하도록 권장합니다. 그러나 업그레이드 계획 및 비즈니스 요구 사항에 맞게 보다 높은 유연성을 제공하기 위해 Adobe은 버전 2.4.4 및 2.4.5에서 Adobe Commerce 고객을 위해 추가 비용 없이 1년 지원 확장 기능을 제공합니다. 지원 확장에는 핵심 애플리케이션에 대한 품질 및 보안 패치가 최대 1년 동안 포함됩니다.

>[!NOTE]
>
>확장 지원은 Adobe Commerce 고객만 사용할 수 있습니다. Magento Open Source 코드 베이스에는 사용할 수 없습니다.

## 소프트웨어 지원 종료

| 릴리스 | 일반 가용성 | 정기 지원 종료<sup>1</sup> | 확장 지원 종료 | 종속 PHP 버전 | 종속 MariaDB 버전 |
|----------------------|----------------------|------------------------------------|-------------------------|-----------------------|---------------------------|
| Adobe Commerce 2.4.8 | 2025년 4월 8일 | 2028년 4월 11일 | 해당 사항 없음 | 8.3 및 8.4 | 11.4 |
| Adobe Commerce 2.4.7 | 2024년 4월 9일 | 2027년 4월 9일 | 해당 사항 없음 | 8.2 및 8.3 | 10.11<sup>3</sup> |
| Adobe Commerce 2.4.6 | 2023년 3월 14일 | 2026년 8월 11일<sup>2</sup> | 해당 사항 없음 | 8.1 및 8.2 | 10.11<sup>4</sup> |
| Adobe Commerce 2.4.5 | 2022년 8월 9일 | 2025년 8월 12일 | 2026년 8월 11일 | 8.1 | 10.6<sup>5</sup> |
| Adobe Commerce 2.4.4 | 2022년 4월 12일 | 2025년 4월 12일 | 2026년 4월 14일 | 8.1 | 10.6<sup>6</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> 소프트웨어 지원 종료에는 품질 수정 및 보안 수정 종료가 모두 포함됩니다.
>- <sup>2</sup> 2.4.5에 대한 확장 지원 종료에 맞춰 업데이트되었습니다.
>- <sup>3</sup> 2.4.7-p6 보안 패치부터 시작합니다.
>- <sup>4</sup> 2.4.6-p11 보안 패치부터 시작합니다.
>- <sup>5</sup> 2.4.5-p11 보안 패치부터 시작합니다.
>- <sup>6</sup> 2.4.4-p12 보안 패치부터 시작합니다.
>- [소프트웨어 수명 주기 정책](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)을 참조하세요.

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
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
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
   <td>정기 지원</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>확장 지원</td>
  </tr>
 </tbody>
</table>
