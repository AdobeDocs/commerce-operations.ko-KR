---
title: 구현 개발 단계
description: Adobe Commerce 프로젝트의 개발 단계에 대한 구현 모범 사례에 대해 알아봅니다.
source-git-commit: c717d45525c7893fa2c38183326534e0fa4ee0c6
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# 개발 단계

개발 단계에는 다음 활동이 포함됩니다.

- 로컬 및 스테이징 환경 설정
- 스프린트 계획
- 티켓 실행
- 문제 해결
- 코드 검토, 병합 및 테스트
- 스프린트 검토
- 고객 승인

다음 섹션에는 개발 단계에 대한 우수 사례 정보가 포함되어 있습니다.

## 애플리케이션 개발

### 코드 검토, 병합 및 테스트

- 지침 및 표준

<!--Assets not yet integrated
  - [Development best practices](https://wiki.corp.adobe.com/x/nT4ykw)
  - [Code Review](https://wiki.corp.adobe.com/x/qT4ykw)
  - [Debugging Magento 2](https://wiki.corp.adobe.com/x/nz4ykw) (wiki)
-->
- [CSS 및 JS 파일 최적화](optimize-css-js-files.md)
- [비공개 콘텐츠 블록에 대한 우수 사례](private-content-block-configuration.md)

- 사용자 지정 코드 추가
   - [확장 개발자를 위한 우수 사례](https://developer.adobe.com/commerce/php/best-practices/)

<!--Assets not yet integrated

  - [Best practices for theme development](https://wiki.corp.adobe.com/pages/viewpage.action?spaceKey=MAGPS&title=Best+Practices+for+Theme+Development)
  - [Module basis](https://wiki.corp.adobe.com/x/kz4ykw) (wiki) — Develop custom modules
  - [Exception Handling](https://wiki.corp.adobe.com/x/nz4ykw)
  - [Custom code copyrights](https://wiki.corp.adobe.com/x/lj4ykw)
- Source control and package management - wiki articles
  - [Code management - Git vs. Composer](https://wiki.corp.adobe.com/x/pz4ykw)
  - [Git branching strategy](https://wiki.corp.adobe.com/display/MAGPS/Git+Branching+Strategy)
  - [Composer development](https://wiki.corp.adobe.com/x/mD4ykw)
  - [Composer patching](https://wiki.corp.adobe.com/x/mj4ykw)
  - [Composer project structure](https://wiki.corp.adobe.com/x/mT4ykw)
  - [Composer tips and tricks](https://wiki.corp.adobe.com/x/lz4ykw)
-->

## 플랫폼 및 서비스

- [이미지 최적화를 위한 기본 사용](image-optimization.md)

### 로컬 및 스테이징 환경 설정

- [클라우드 인프라 개발 워크플로우](https://devdocs.magento.com/cloud/architecture/pro-develop-deploy-workflow.html) - 클라우드 안내서에서 추가됨

## 코드, 병합, 테스트

- [빌드 및 배포에 대한 우수 사례](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices)
- [정적 콘텐츠 배포 - 클라우드](static-content-deployment.md)
- [CSS 및 JS 파일 최적화](optimize-css-js-files.md)
- [응답형 사이트를 위한 이미지 최적화](image-optimization.md)
- [클라우드 인프라&#x200B;에 대한 Adobe Commerce 우수 사례 문제 해결](troubleshooting.md)
- [데이터베이스 테이블을 수정하는 시기와 방법을 &#x200B; 알아봅니다](modifying-core-and-third-party-tables.md)
