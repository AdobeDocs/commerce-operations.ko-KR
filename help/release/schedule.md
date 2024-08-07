---
title: 릴리스 일정
description: Adobe의 Adobe Commerce를 위한 새 기능 릴리스의 발표 계획에 대해 알아봅니다.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: e9ef167f5425407f6b1850f0dd913d5d3e2bd628
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 2%

---

# 릴리스 일정

Adobe은 조기 채택자에게 향상된 기능과 새로운 기능을 더 빨리 제공하면서 제품 업그레이드를 단순하고 예측 가능하게 만드는 것 사이의 올바른 균형을 찾기 위해 지속적으로 노력하고 있습니다([버전 관리 정책](versioning-policy.md) 참조). 이 예약의 목적은 Adobe이 실질적인 새 기능의 릴리스를 발표할 계획인 날짜를 제공하는 것입니다. 이러한 기능은 1년 내내 달라질 수 있습니다. 그러나 Adobe은 이 페이지에 지정된 날짜 사이에 확장성 도구, 인프라 및 SaaS 제품(서비스)에 대한 개선 사항을 정기적으로 지속적으로 릴리스합니다.

핵심 Adobe Commerce PHP 응용 프로그램의 지원되는 각 릴리스 라인에 대해 Adobe 릴리스 [패치](versioning-policy.md#patch-release)을(를) 합니다. 패치 릴리스는 핵심 코드 베이스를 업그레이드하여 플랫폼을 안전하고 안정적이며 성능을 유지할 수 있는 기회입니다. 기능은 코어 코드 베이스에 관계 없이 [외부 모듈, 확장, 도구 또는 웹 서비스](versioning-policy.md#extensibility-infrastructure-and-services-release)를 통해 사용할 수 있습니다.

>[!NOTE]
>
>2024년부터 Adobe은 더 이상 패치에 대한 &quot;프리릴리스&quot; 액세스를 제공하지 않습니다. 대신 2.4.7 이상의 경우 Adobe Commerce 고객은 [베타 릴리스](beta.md)를 사용하여 테스트 및 개발 목적으로 사전 일반 가용성 코드에 액세스할 수 있습니다.

다음 표에는 예약된 릴리스에 대한 날짜가 나와 있습니다(날짜는 변경될 수 있음).

<table>
<thead>
  <tr>
    <th>일반 가용성</th>
    <th>기능</th>
    <th>PHP 코어</th>
  </tr>
</thead>
<tfoot>
   <tr>
      <td colspan="3"><strong>범례</strong>
         <ul>
           <li><strong><img alt="B2B 기능 아이콘" src="../assets/icons/enterprise.svg"></img> B2B</strong>—Adobe Commerce용 B2B 확장에 대한 새로운 기능, 개선 사항 및 버그 수정 사항입니다. B2B 확장 릴리스에 대한 자세한 내용은 <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B 릴리스 정보</a>를 참조하십시오.</li>
            <li><strong><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> 확장성</strong>—패치 릴리스와 독립적으로 제공되는 프로세스 외부 확장성을 위한 새로운 개발자 도구 및 서비스입니다. 예: 관리자 UI SDK, Commerce용 Adobe I/O 이벤트 및 API Mesh.</li>
            <li><strong><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> 인프라</strong> - 클라우드 플랫폼에서 Adobe Commerce 설치 및 업그레이드를 배포하고 관리하도록 디자인된 클라우드 인프라 및 Commerce용 Cloud Tools Suite Package의 Adobe Commerce에 대한 새로운 기능 및 개선 사항입니다.</li>
            <li><strong><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> 패치</strong>—보안, 규정 준수, 성능 및 우선 순위가 높은 품질 수정 사항이 포함된 핵심 Adobe Commerce PHP 응용 프로그램에 대한 업데이트입니다.</li>
            <li><strong><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> 서비스</strong>—패치 릴리스와 독립적으로 제공되는 새로운 SaaS 기능입니다. 예를 들어 Catalog Service, Live Search 및 Product Recommendations이 있습니다.</li>
         </ul>
      </td>
   </tr>
</tfoot>
<tbody>
  <tr>
    <td>2024년 2월 13일</td>
    <td><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">확장성</a><br><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">인프라</a><br><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">서비스</a></td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">보안 패치</a>: 2.4.6-p4, 2.4.5-p6, 2.4.4-p7</td>
  </tr>
  <tr>
    <td>2024년 3월 12일</td>
    <td>—</td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">Beta 패치</a>: 2.4.7-beta3</td>
  </tr>
  <tr>
    <td>2024년 4월 9일</td>
    <td><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">확장성</a><br><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">인프라</a><br><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">서비스</a></td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md"><strong>Adobe Commerce 2.4.7</a></strong>:<ul><li>성능 향상</li><li>품질 개선 사항</li><li>향상된 보안 기능</li><li>타사 종속성 업데이트</li></ul><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">보안 패치</a>: 2.4.6-p5, 2.4.5-p7, 2.4.4-p8</td>
  </tr>
  <tr>
    <td>2024년 6월 11일</td>
    <td><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">확장성</a><br><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">인프라</a><br><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">서비스</a></td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">보안 패치</a>: 2.4.7-p1, 2.4.6-p6, 2.4.5-p8, 2.4.4-p9</td>
  </tr>
  <tr>
    <td>2024년 8월 13일</td>
    <td><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">확장성</a><br><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">인프라</a><br><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">서비스</a></td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">보안 패치</a>: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10</td>
  </tr>
  <tr>
    <td>2024년 10월 8일</td>
    <td><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">확장성</a><br><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">인프라</a><br><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">서비스</a></td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">Beta 패치</a>: 2.4.8-beta1<br><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">보안 패치</a>: 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11</td>
  </tr>
</tbody>
</table>
