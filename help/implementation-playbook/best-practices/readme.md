---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---
# 모범 사례: 콘텐츠 만들기 워크플로

이 문서에서는 *[Adobe Commerce 구현 플레이북]의*&#x200B;모범 사례&#x200B;*(https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=ko* 콘텐츠에 대한 변경 또는 추가 사항을 요청하는 사용자 워크플로에 대해 설명합니다.

## 누가 요청을 만들 수 있습니까?

Adobe은 다음 그룹의 개인을 포함하되 이에 국한되지 않고 내부 및 외부 관련자의 요청을 수락합니다.

- Adobe 파트너
- Adobe CTAG(Customer Technical Advisory Group), 고객 지원, 고객 성공, 엔지니어링 팀

## 요청을 만드는 방법

**내부 관련자**&#x200B;이(가) COMDOX 프로젝트에서 Jira 문제를 열어 요청을 제출할 수 있습니다. **외부 관련자**&#x200B;이(가) 이 저장소에서 [GitHub 문제](https://github.com/AdobeDocs/commerce-operations.ko-KR/issues/new/choose)를 열어 요청을 제출할 수 있습니다.

다음 유형의 요청을 제출할 수 있습니다.

- 새 콘텐츠에 대한 아이디어
- 이미 게시된 콘텐츠에 대한 업데이트
- 관련자 또는 커뮤니티에서 제공한 새 콘텐츠 게시

## 전반적인 프로세스는 무엇입니까?


**Jira 티켓 또는 문제 만들기**—내부 이해 당사자가 COMDOX 프로젝트에서 Jira 티켓을 만듭니다. 외부 관련자가 GitHub 문제를 제출합니다. 팀이 컨텍스트를 이해하고 요청의 우선 순위를 정하는 데 도움이 되도록 Jira 또는 [GitHub 문제](https://github.com/AdobeDocs/commerce-operations.ko-KR/issues/new/choose)에 전체 세부 정보를 포함하십시오.

**Adobe 프로젝트 팀이 요청을 평가하고 우선 순위를 지정합니다**—팀은 정기적으로 요청을 모니터링하여 우선 순위를 결정하고 구현 플레이북 모범 사례에 포함할 요청된 변경 사항을 평가합니다. 예를 들어 팀은 새 모범 사례 주제를 만드는 대신 요청된 콘텐츠를 Experience League 또는 Adobe Developer 사이트의 기존 제품 설명서에 추가해야 한다고 결정할 수 있습니다.

요청에 제공된 정보가 충분하지 않으면 팀은 요청자에게 추가 정보를 요청합니다. 요청자가 14일 이내에 응답하지 않으면 팀은 요청을 닫습니다.

**콘텐츠 만들기 또는 업데이트**-콘텐츠 만들기 작업이 [Adobe Experience League 기여자 안내서](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html?lang=ko)에 설명된 프로세스에 따라 완료되었습니다. 요청에 따라 작업에는 새 콘텐츠를 Markdown으로 변환하거나, 항목을 만들거나, 기존 항목을 업데이트하는 작업이 포함될 수 있습니다.

**콘텐츠 검토, 승인 및 게시**-콘텐츠를 검토하고 [GitHub 가져오기 요청](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=ko#pull-requests)을 사용하여 항목을 만들거나 업데이트하는 동안 콘텐츠를 편집합니다. 모든 내용은 편집심사를 거쳐야 한다. 기술 검토는 선택 사항이며 콘텐츠에 따라 다릅니다. 기술적인 검토가 필요하지 않은 경우 편집심사만으로 프로세스를 계속한다. 이 프로세스는 콘텐츠가 승인될 때까지 여러 번 반복할 수 있습니다.

문서가 승인되면 가져오기 요청을 프로덕션 분기에 병합할 수 있습니다. 병합은 작성자가 수행해야 합니다. 주제가 병합되면 수동 프로세스를 사용하여 즉시 프로덕션에 게시하거나 다음에 게시 작업이 실행될 때 자동으로 게시할 수 있습니다. 게시 작업은 일반적으로 2시간마다 실행됩니다.

**새 콘텐츠 알림**-Adobe에서는 최근 게시되거나 업데이트된 주제에 대한 사용자 정보를 사용자에게 제공하기 위해 *모범 사례 개요* 주제에 대한 [새로운 기능](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=ko) 섹션을 제공합니다. Adobe은 마케팅 및 내부 커뮤니케이션과 같은 기존 채널을 사용하는 새로운 모범 사례 콘텐츠도 홍보합니다.

## 백로그 및 Kanban 보드

중복을 방지하기 위해 만들어지고 우선 순위가 지정된 요청이 COMDOX 프로젝트 및 [GitHub 문제 프로젝트](https://github.com/orgs/AdobeDocs/projects/6/views/1)의 Jira 백로그에 표시됩니다. 내부 이해 당사자는 Jira의 투표 시스템에 참여하여 필요하거나 관련성이 있다고 간주하는 요청에 대해 찬성할 것을 권장합니다. 투표는 또한 모범 사례 프로젝트 팀이 이해 당사자가 기대하고 가치 있는 콘텐츠 유형을 이해하는 데 도움이 됩니다. 우선 순위 지정 및 검토를 보류 중인 요청은 Kanban 보드의 활성 레인으로 이동될 때까지 백로그에 표시됩니다.

내부 사용자는 Kanban 보드에 액세스하여 작업 중인 컨텐츠와 진행 상황을 확인(및/또는 모니터링)할 수 있습니다. 활성 요청만 이 보드에 표시됩니다.
