---
title: 소프트웨어 수명 주기 정책
description: Adobe Commerce 릴리스에 대한 소프트웨어 지원 종료 관련 주요 일정에 대해 알아봅니다.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 7df5edf2acba706fb01f58cc3749c4a2bf136fc5
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 5%

---


# Adobe Commerce 라이프사이클 정책

Adobe Commerce 2.4.4 및 후속 릴리스의 경우:

- Adobe Commerce 라이프사이클 정책을 간소화하고 고객의 미션 크리티컬 요구 사항을 지원하기 위해 Adobe은 지원 기간을 Adobe Commerce 2.4.4 이상의 GA(General Availability) 날짜부터 3년으로 확대했습니다. Adobe은 3년의 지원 기간 동안 2.4.4 이상 릴리스에 대한 품질 수정 사항을 제공합니다. 고객은 [Adobe Commerce 지원](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html)에 연락하거나 해당 버전이 여전히 품질 지원에 적합한 경우 셀프 서비스 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을(를) 통해 품질 수정 사항에 액세스할 수 있습니다. Adobe Commerce 릴리스 라인에 대한 소프트웨어 지원 종료 날짜는 아래 표를 참조하십시오.

- Adobe은 3년의 지원 기간 동안 보안 패치 릴리스를 통해 보안 수정 사항을 제공합니다.

- 제로 데이 취약성과 같은 중요한 보안 문제의 경우, 최신 패치 또는 보안 패치 릴리스가 아니더라도 지원되는 버전의 모든 고객을 위해 Adobe에서 [핫픽스](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)를 제공합니다. 핫픽스는 다목적 서비스가 아니며 최신 릴리스로 업그레이드하여 수정되는 모든 보안 문제를 해결하지는 않습니다.

- Adobe은 고객이 Adobe Commerce에 대한 3년의 지원 기간을 사용하는 동안 수명이 종료될 수 있는 타사 서비스 및 소프트웨어 종속성(PHP 및 MySQL 등)에 대한 보안 및 품질 수정 사항을 제공하지 않습니다. 테스트되고 지원되는 타사 기술에 대한 전체 목록은 [시스템 요구 사항](../installation/system-requirements.md)을 참조하십시오.

- Adobe은 고객이 보안 전용 패치 릴리스의 범위에서 Adobe Commerce에 대한 지원 기간 3년을 진행하는 동안 타사 서비스 및 소프트웨어 종속성과의 호환성을 제공하지만, 이전 버전과 호환되지 않는 변경 사항을 도입하지 않고도 가능한 경우에만 가능합니다.

## 소프트웨어 지원 종료

| 릴리스 | 일반 가용성 | 소프트웨어 지원 종료<sup>1</sup> | 종속 PHP 버전 | 종속 MariaDB 버전 |
|----------------------|----------------------|-------------------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 2024년 4월 9일 | 2027년 4월 9일 | 8.2 및 8.3 | 10.6 |
| Adobe Commerce 2.4.6 | 2023년 3월 14일 | 2026년 3월 14일 | 8.1 및 8.2 | 10.6 |
| Adobe Commerce 2.4.5 | 2022년 8월 9일 | 2025년 8월 9일 | 8.1 | 10.5<sup>2</sup> |
| Adobe Commerce 2.4.4 | 2022년 4월 12일 | 2025년 4월 24일 | 8.1 | 10.5<sup>3</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> 소프트웨어 지원 종료에는 품질 수정 및 보안 수정 종료가 모두 포함됩니다.
>- <sup>2</sup> 2.4.5-p8 보안 패치부터 시작합니다.
>- <sup>3</sup> 2.4.4-p9 보안 패치부터 시작합니다.
>- [소프트웨어 수명 주기 정책](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)을 참조하세요.

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
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
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="8"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**키**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">지원됨</td>
   <td>Adobe Commerce용 보안 및 품질 패치</td>
  </tr>
  <!-- <tr>
   <td style="background-color:#cd3c3c;">End of software support</td>
   <td>Version that has reached end of software support.</td>
  </tr>
 </tbody> -->
</table>
