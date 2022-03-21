---
title: 서비스 수준 계약
description: 서비스 수준 계약 및 SLA를 사용하여 Adobe Commerce 구현을 지원하는 방법에 대해 알아봅니다.
exl-id: 5da42dfa-e165-4142-a863-6f3ce7689478
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---

# SLA(서비스 수준 계약)

서비스 수준 계약(SLA)은 서비스 제공자로부터 고객이 기대하는 서비스 수준을, 해당 서비스를 측정하기 위한 간단한 지표와, 합의된 서비스 수준을 달성하지 못할 경우 보상 또는 처벌을 제공합니다.

다양한 유형의 사고 위험에 대한 SLA는 계약, 유지 관리 및 측정될 수 있습니다. 또한, 응답 유형은 고객이 필요로 하는 서비스 수준에 따라 여러 표준(Gold, Platinum)을 가질 수 있습니다.

다음 표에서는 여러 서비스 수준이 있는 일반적인 SLA 지표 분류를 설명합니다.

<table>
<thead>
  <tr>
    <th>문제 유형</th>
    <th>영향</th>
    <th>예</th>
    <th colspan="2">지원되는 영업시간 동안 응답/복원 시간</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="3"></td>
    <td>금</td>
    <td>백금</td>
  </tr>
  <tr>
    <td>P1</td>
    <td>중요한 영향</td>
    <td>서비스가 중단되거나 사용할 수 없음</td>
    <td>1시간/4시간</td>
    <td>1시간/4시간</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>서비스를 사용할 수 없습니다.</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>최종 사용자 기반에서 서비스를 사용할 수 없습니다.</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P2</td>
    <td>높은 영향</td>
    <td>서비스가 심각하게 손상됨</td>
    <td>2시간/12시간</td>
    <td>2시간/8시간</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>서비스 성능이 저하됨</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>서비스를 사용할 수 있지만 심각한 오류 메시지 발생</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P3</td>
    <td>중간 영향</td>
    <td>서비스가 부분적으로 손상됨</td>
    <td>8시간/16시간</td>
    <td>8시간/12시간</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>오류 메시지가 생성되었으며 최종 사용자에게 영향을 주지 않습니다.</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>고객 실행에서 사용되는 기능에 대한 질문</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## 적용 범위 옵션

커밋된 SLA에 대한 적용 범위는 다양한 서비스 유형에 따라 달라집니다. 일반적으로 Gold 및 Platinum 지원 서비스의 범위는 다음과 같습니다.

![SLA 적용 범위를 보여주는 정보 그래픽](../../assets/playbooks/sla-coverage-options.svg)
