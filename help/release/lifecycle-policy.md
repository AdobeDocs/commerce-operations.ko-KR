---
title: 소프트웨어 수명 주기 정책
description: Adobe Commerce 릴리스에 대한 소프트웨어 지원 종료 관련 주요 일정에 대해 알아봅니다.
source-git-commit: ffa8b957828833d2c3f9bc79c31dc3fa2c6035a5
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 8%

---


# Adobe Commerce 라이프사이클 정책

Adobe Commerce 2.4 및 후속 릴리스의 경우:

- 라이프사이클 정책을 보다 효율적으로 수행하기 위해 Adobe은 PHP 버전이 기반으로 하는 지원 날짜가 끝날 때까지 2.4 릴리스 라인에 품질 수정 사항을 제공합니다. 고객은 연락하여 품질 수정 사항에 액세스할 수 있습니다 [Adobe Commerce 지원](https://developer.adobe.com/commerce/contributor/community/support/) 또는 셀프 서비스를 통해 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}(해당 버전이 여전히 품질 지원을 받을 수 있는 경우) Adobe Commerce 릴리스 라인에 대한 소프트웨어 지원 종료 날짜는 아래 표를 참조하십시오.

- Adobe은 고객의 버전이 여전히 품질 지원을 받을 수 있는 경우에도 최신 패치 또는 보안 패치 릴리스를 통해서만 보안 수정 사항을 제공합니다. 품질 수정 사항과 달리 보안 수정 사항은 지원되는 부 릴리스 내에서 이전 부 릴리스 또는 이전 패치 릴리스로 지원할 수 없습니다.

- 0일 취약점과 같은 중요한 보안 문제에 대해 Adobe은 다음을 제공합니다 [핫픽스](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) 최신 패치 또는 보안 패치 릴리스가 아닌 경우에도 지원되는 버전의 모든 고객에 대해 해당됩니다. 최신 릴리스로 업그레이드하여 해결할 수 있는 모든 보안 문제를 해결하지는 않는 핫픽스 가 다목적 문제가 아니며,

## 소프트웨어 지원 종료

| 릴리스 | 릴리스 날짜 | 소프트웨어 지원 종료<sup>1</sup> | 종속 PHP 버전 |
| -------------------------------- | ----------------- | ----------------------------------- | --------------------------- |
| Adobe Commerce 2.3 | 2018년 11월 28일 | 2022년 9월 8일<sup>2개</sup> | PHP 7.3 및 7.4<sup>3</sup> |
| Adobe Commerce 2.4.0-2.4.3 | 2020년 7월 28일 | 2022년 11월 28일 | PHP 7.4 |
| Adobe Commerce 2.4.4-2.4.6 | 2022년 4월 12일 | 2024년 11월 25일 | PHP 8.1 |

<sup>1 소프트웨어 지원 종료에는 품질 수정 사항 및 보안 수정 사항 종료가 모두 포함되어 있습니다.</sup><br>
<sup>2 2.3에 대한 소프트웨어 지원 종료 날짜는 2022년 9월 8일로 연장되어 2022년 3월 8일에 GA되는 2.4.4 릴리스로 업그레이드할 수 있는 시간이 더 늘어납니다.</sup><br>
<sup>3 2.3.0-2.3.6은 PHP 7.3에 따라 다릅니다. 2.3.7은 PHP 7.4에 따라 다릅니다.</sup>

>[!NOTE]
>
>자세한 내용은 [소프트웨어 수명 주기 정책](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table>
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022년</th>
    <th colspan="4">2023년</th>
    <th colspan="4">2024년</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>상거래</td>
    <td>PHP</td>
    <td>1분기</td>
    <td>2분기</td>
    <td>3분기</td>
    <td>4분기</td>
    <td>1분기</td>
    <td>2분기</td>
    <td>3분기</td>
    <td>4분기</td>
    <td>1분기</td>
    <td>2분기</td>
    <td>3분기</td>
    <td>4분기</td>
  </tr>
  <tr>
    <td>2.4.0 - 2.4.3</td>
    <td style="text-align:center">7.4</td>
    <td colspan="3" style="background-color:#67ac68;"></td>
    <td style="background-color:#cd3c3c;">11월</td>
    <td colspan="8" ></td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td rowspan="2" style="text-align:center">8.1</td>
    <td></td>
    <td colspan="10" style="background-color:#67ac68;">3월</td>
    <td rowspan="2" style="background-color:#cd3c3c;">11월</td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="9" style="background-color:#67ac68;">8월</td>
  </tr>
</tbody>
</table>

## 키

<table>
  <thead>
   <tr>
    <th></th>
    <th></th>
   </tr>
  </thead>
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">지원됨</td>
   <td>Adobe에서 완전히 테스트하고 지원되는 버전입니다.</td>
  </tr>
  <tr>
   <td style="background-color:#cd3c3c;">소프트웨어 지원 종료</td>
   <td>소프트웨어 지원 종료에 도달한 버전입니다.</td>
  </tr>
 </tbody>
</table>
