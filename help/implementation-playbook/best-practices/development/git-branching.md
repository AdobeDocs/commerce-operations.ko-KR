---
title: Git 분기 우수 사례
description: 소스 코드 관리를 위한 다양한 분기 전략에 대해 알아봅니다.
feature: Best Practices
role: Developer
exl-id: 7d7736e8-7023-4315-9965-71866b0be5c3
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Git 분기 우수 사례

Source 코드는 개발 프로세스 동안 여러 안정성 단계를 거칩니다.

- 활성 개발
- 초기 코드 통합
- 품질 보증(QA)을 위한 코드 통합
- 최종 사용자 승인 테스트(UAT)를 위한 코드 통합
- 프로덕션 릴리스에 대한 최종 코드 통합

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 지점 관리

코드 변경 사항을 추적하고 배포 프로세스를 용이하게 하려면 각 개발 단계에 Git에 해당 분기가 있어야 합니다.

- **작업 분기** - 개발자가 기능 및 버그 수정과 같은 특정 작업을 구현하는 동안 개별 코드 변경 사항을 커밋하는 위치입니다.
- **개발 분기** - 자동화된 통합 테스트를 위해 여러 개발자가 개별 작업 분기의 변경 내용을 단일 개발 분기에 병합하는 경우입니다. 이 분기는 개발 환경에 배포됩니다.
- **QA 분기** - 개발이 완료되고 코드가 모든 자동화된 통합 테스트 및 코드 검토를 통과한 후 개발자가 변경 내용을 병합하는 경우입니다. 이 분기는 수동 QA 테스트를 위해 QA 환경에 배포됩니다.
- **안정적/UAT 분기** - 수동 QA 테스트를 통과한 후 코드가 병합되는 경우 이 분기는 사용자 승인 테스트를 위해 UAT 환경에 배포됩니다.
- **프로덕션/릴리스 분기** - UAT를 통과한 후 코드가 병합되는 경우. 이 분기는 릴리스용 프로덕션에 배포됩니다.

>[!TIP]
>
>클라우드 인프라 프로젝트의 Adobe Commerce에는 서로 다른 환경에 해당하는 특정 분기가 포함되어 있습니다. [Cloud Guide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=ko)에서 [Pro 프로젝트 워크플로](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html?lang=ko) 및 _Starter 프로젝트 워크플로_&#x200B;를 참조하십시오.

## 분기 전략

사용할 수 있는 몇 가지 분기 전략이 있습니다. 개발 팀과 프로젝트의 복잡성에 가장 적합한 전략을 선택하십시오.

자세한 내용은 다음 외부 리소스를 참조하십시오.

- [워크플로우 분기](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [분산 워크플로](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [소스 코드 분기 관리 패턴](https://martinfowler.com/articles/branching-patterns.html)
- [성공적인 Git 분기 모델](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub 흐름](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitLab 흐름](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
