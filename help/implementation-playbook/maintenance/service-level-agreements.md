---
title: Service Level Agreements
description: Learn about service level agreements and how to use them to support your Adobe Commerce implementation.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
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
    <th>Issue Type</th>
    <th>영향</th>
    <th>예</th>
    <th colspan="2">Response/Restoration time during supported business hours</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="3"></td>
    <td>금</td>
    <td>Platinum</td>
  </tr>
  <tr>
    <td>P1</td>
    <td>Critical Impact</td>
    <td>Service down or unusable</td>
    <td>1 hour / 4hours</td>
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
    <td>Service is unusable across end user base</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P2</td>
    <td>High Impact</td>
    <td>Service severely impaired</td>
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
    <td>Medium Impact</td>
    <td>Service partially impaired</td>
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
    <td>Questions about features used in customer launch</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## 적용 범위 옵션

커밋된 SLA에 대한 적용 범위는 다양한 서비스 유형에 따라 달라집니다. 일반적으로 Gold 및 Platinum 지원 서비스의 범위는 다음과 같습니다.

![SLA 적용 범위를 보여주는 정보 그래픽](../../assets/playbooks/sla-coverage-options.svg)
