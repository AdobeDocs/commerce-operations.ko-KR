---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---
# 우수 사례: 컨텐츠 만들기 워크플로우

이 문서에서는 *[우수 사례](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html)* 의 컨텐츠 *Adobe Commerce 구현 Playbook*.

## 누가 요청을 만들 수 있습니까?

Adobe은 다음 그룹의 개인을 포함하여 내부 및 외부 이해 관계자 모두의 요청을 수락합니다.

- Adobe 파트너
- Adobe CTAG(고객 기술 자문 그룹), 고객 지원, 고객 성공, 엔지니어링 팀

## 요청을 만드는 방법

**내부 이해 관계자** 은 COMDOX 프로젝트에서 Jira 문제를 열어 요청을 제출할 수 있습니다. **외부 이해 관계자** 열어서 요청을 제출할 수 있음 [GitHub 문제](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) 이 저장소에 있는 중입니다.

다음 유형의 요청을 제출할 수 있습니다.

- 새 컨텐츠에 대한 아이디어
- 이미 게시된 콘텐츠 업데이트
- 이해 관계자 또는 커뮤니티에서 제공한 새 컨텐츠 게시

## 전반적인 프로세스는 무엇입니까?


**Jira 티켓 또는 문제 만들기**- 내부 이해 관계자가 COMDOX 프로젝트에서 Jira 티켓을 만듭니다. 외부 이해 관계자가 GitHub 문제를 제출합니다. Jira 또는 [GitHub 문제](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) 팀이 컨텍스트를 이해하고 요청의 우선 순위를 지정하는 데 도움이 됩니다.

**Adobe 프로젝트 팀은 요청을 평가하고 우선 순위를 둡니다**- 팀은 정기적으로 요청을 모니터링하여 우선 순위를 결정하고 구현 Playbook 우수 사례에 포함하기 위해 요청된 변경 사항을 평가합니다. 예를 들어, 팀이 새 우수 사례 항목을 만드는 대신 요청된 컨텐츠를 Experience League 또는 Adobe Developer 사이트의 기존 제품 설명서에 추가하도록 할 수 있습니다.

요청에 충분한 정보가 제공되지 않으면 팀이 요청자로부터 추가 정보를 요청합니다. 요청자가 14일 이내에 응답하지 않으면 팀이 요청을 닫습니다.

**컨텐츠 만들기 또는 업데이트**-컨텐츠 작성 작업은 [Adobe Experience League 기여자 안내서](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). 요청에 따라 작업에서 새 컨텐츠를 Markdown으로 변환하거나 항목을 만들거나 기존 항목을 업데이트하는 작업이 포함될 수 있습니다.

**컨텐츠 검토, 승인 및 게시**-컨텐츠를 검토 및 편집하기 위해 [GitHub 가져오기 요청](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). 모든 컨텐츠는 편집 검토를 거쳐야 합니다. 기술 검토는 선택 사항이며 컨텐츠에 따라 다릅니다. 기술 검토가 필요하지 않으면 편집 검토만 수행하면 프로세스가 계속됩니다. 이 프로세스는 컨텐츠가 승인될 때까지 여러 번 반복할 수 있습니다.

문서가 승인되면 끌어오기 요청을 프로덕션 분기에 병합할 수 있습니다. 병합은 작성자가 수행해야 합니다. 주제가 병합되면 수동 프로세스를 사용하여 즉시 프로덕션에 게시하거나 다음에 게시 작업이 실행될 때 자동으로 게시할 수 있습니다. 게시 작업은 일반적으로 두 시간마다 실행됩니다.

**새 컨텐츠 알림**-Adobe은 *새로운 기능* 섹션에 [우수 사례 개요](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) 최근에 게시되었거나 업데이트된 주제에 대해 사용자에게 계속 알려주는 주제입니다. 또한 Adobe은 마케팅 및 내부 통신과 같은 기존 채널을 사용하여 새로운 우수 사례 콘텐츠를 홍보할 예정입니다.

## 백로그 및 간판 보드

중복을 방지하기 위해 만들고 우선 순위가 지정된 요청은 COMDOX 프로젝트의 Jira 백로그에 표시됩니다. [GitHub 문제 프로젝트](https://github.com/orgs/AdobeDocs/projects/6/views/1). 내부 이해관계자들은 그들이 필요하거나 관련성이 있다고 생각하는 요청을 투표하기 위해 Jira에서 투표 시스템에 참여하는 것을 권장받습니다. 또한 투표는 우수 사례 프로젝트 팀이 이해 관계자가 기대하는 컨텐츠 유형과 가치를 이해하는 데 도움이 됩니다. 우선 순위 지정 및 검토 중인 요청은 간판 보드의 활성 차로로 이동될 때까지 백로그에 표시됩니다.

내부 사용자가 간판 보드를 액세스하여 작업 중인 컨텐츠와 수행된 진행 상황을 확인(및/또는 모니터링)할 수 있습니다. 이 보드에는 활성 요청만 표시됩니다.
