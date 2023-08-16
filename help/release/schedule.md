---
title: 릴리스 일정
description: Adobe의 Adobe Commerce를 위한 중요 새 기능 릴리스의 발표 계획에 대해 알아봅니다.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 12b4f619673414f18d9697450e867681c6cb3194
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 1%

---

# 릴리스 일정

Adobe은 제품 업그레이드를 단순하고 예측 가능하게 만드는 동시에 얼리어답터에게 향상된 기능과 새로운 기능을 보다 빠르게 제공할 수 있도록 적절한 균형을 찾기 위해 지속적으로 노력하고 있습니다(참조) [버전 관리 정책](versioning-policy.md)). 이 예약의 목적은 Adobe이 실질적인 새 기능의 릴리스를 발표할 계획인 날짜를 제공하는 것입니다. 이러한 기능은 1년 내내 달라질 수 있습니다. 그러나 Adobe은 이 페이지에 지정된 날짜 사이에 확장성 도구, 인프라 및 SaaS 제품(서비스)에 대한 개선 사항을 정기적으로 지속적으로 릴리스합니다.

Adobe 릴리스 [패치](versioning-policy.md#patch-release) 코어 Adobe Commerce PHP 애플리케이션의 지원되는 각 릴리스 라인의 경우. 패치 릴리스는 핵심 코드 베이스를 업그레이드하여 플랫폼을 안전하고 안정적이며 성능을 유지할 수 있는 기회입니다. 기능은 코어 코드베이스에 독립적이며 다음을 통해 사용할 수 있습니다. [외부 모듈, 확장, 도구 또는 웹 서비스](versioning-policy.md#extensibility-infrastructure-and-services-release).

>[!NOTE]
>
>2024년부터 Adobe은 더 이상 패치에 대한 &quot;프리릴리스&quot; 액세스를 제공하지 않습니다. 대신 2.4.7 이상의 경우 Adobe Commerce 고객은 다음을 사용할 수 있습니다 [베타 릴리스](beta.md) 테스트 및 개발을 위해 사전 일반 가용성 코드에 액세스합니다. 다음 2023년 릴리스에 대한 프리릴리스 액세스가 계속 예약되어 있습니다.
>
> - 2023년 8월 8일 프리릴리스 액세스는 2023년 7월 25일입니다
> - 2023년 10월 10일 프리릴리스 액세스는 2023년 9월 26일입니다

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
      <td colspan="3"><strong>범례</strong>:
         <ul>
            <li><strong><img alt="B2B 기능 아이콘" src="../assets/icons/enterprise.svg"></img> B2B</strong>—Adobe Commerce용 B2B 확장의 새로운 기능, 개선 사항 및 버그 수정 사항.</li>
            <li><strong><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> 확장성</strong>—새로운 개발자 도구 및 서비스로 패치 릴리스와 별도로 제공되는 프로세스 종료 확장성 예: 관리자 UI SDK, 상업용 Adobe I/O 이벤트 및 API Mesh.</li>
            <li><strong><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> 인프라</strong>—Adobe Commerce on Cloud Infrastructure 및 Cloud Tools Suite for Commerce 패키지의 새로운 기능 및 개선 사항으로, Cloud Platform에서 Adobe Commerce 설치 및 업그레이드를 배포하고 관리하도록 설계되었습니다.</li>
            <li><strong><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> 패치</strong>—보안, 규정 준수, 성능 및 높은 우선 순위 품질 수정 사항이 포함된 핵심 Adobe Commerce PHP 애플리케이션 업데이트입니다.</li>
            <li><strong><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> 서비스</strong>- 패치 릴리스와 별도로 제공되는 새로운 SaaS 기능입니다. 예를 들어 Catalog Service, Live Search 및 Product Recommendations이 있습니다.</li>
         </ul>
      </td>
   </tr>
</tfoot>
<tbody>
  <tr>
    <td>2023년 8월 8일</td>
    <td><img alt="B2B 기능 아이콘" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">확장성</a><br><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">인프라</a><br><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">서비스</a></td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">보안 패치</a>: 2.4.6-p2, 2.4.5-p4, 2.4.4-p5</td>
  </tr>
  <tr>
    <td>2023년 10월 10일</td>
    <td><img alt="B2B 기능 아이콘" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">확장성</a><br><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">인프라</a><br><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">서비스</a></td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">베타 패치</a>: 2.4.7-Beta2<br> <img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">보안 패치</a>: 2.4.6-p3, 2.4.5-p5, 2.4.4-p6</td>
  </tr>
  <tr>
    <td>2024년 2월 13일</td>
    <td><img alt="B2B 기능 아이콘" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">확장성</a><br><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">인프라</a><br><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">서비스</a></td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">보안 패치</a>: 2.4.6-p4, 2.4.5-p6, 2.4.4-p7</td>
  </tr>
  <tr>
    <td>2024년 3월 19일</td>
    <td>—</td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">베타 패치</a>: 2.4.7-베타3</td>
  </tr>
  <tr>
    <td>2024년 4월 9일</td>
    <td><img alt="B2B 기능 아이콘" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">확장성</a><br><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">인프라</a><br><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">서비스</a></td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md"><strong>Adobe Commerce 2.4.7</a></strong>:<ul><li>성능 향상</li><li>품질 개선 사항</li><li>향상된 보안 기능</li><li>타사 종속성 업데이트</li></ul><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">보안 패치</a>: 2.4.6-p5, 2.4.5-p7, 2.4.4-p8</td>
  </tr>
  <tr>
    <td>2024년 6월 11일</td>
    <td><img alt="B2B 기능 아이콘" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">확장성</a><br><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">인프라</a><br><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">서비스</a></td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">보안 패치</a>: 2.4.7-p1, 2.4.6-p6, 2.4.5-p8, 2.4.4-p9</td>
  </tr>
  <tr>
    <td>2024년 8월 13일</td>
    <td><img alt="B2B 기능 아이콘" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">확장성</a><br><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">인프라</a><br><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">서비스</a></td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">보안 패치</a>: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10</td>
  </tr>
  <tr>
    <td>2024년 10월 8일</td>
    <td><img alt="B2B 기능 아이콘" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="확장성 기능 아이콘" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">확장성</a><br><img alt="인프라 기능 아이콘" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">인프라</a><br><img alt="서비스 기능 아이콘" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">서비스</a></td>
    <td><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">베타 패치</a>: 2.4.8-beta1<br><img alt="패치 릴리스 아이콘" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">보안 패치</a>: 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11</td>
  </tr>
</tbody>
</table>
