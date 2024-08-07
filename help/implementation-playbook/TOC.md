---
user-guide-title: 구현 플레이북
user-guide-description: 성공적인 Adobe Commerce 사이트에 대한 계획 수립 및 구현을 위한 전략에 대해 알아봅니다.
mini-toc-levels: 3
source-git-commit: 36a2a86cbafab1e4913573b1c8431524ba43dc6a
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 12%

---


# 구현 플레이북 {#implementation-playbook}

- [개요](overview.md)
- Commerce {#intro}
   - [Adobe Commerce 정보](intro/about-commerce.md)
   - [플랫폼 개발 원칙](intro/platform-development.md)
- 프로젝트 범위 {#project-scope}
   - [지식은 힘이다](project-scope/knowledge.md)
   - [주요 이해 당사자](project-scope/key-stakeholders.md)
   - [프로세스 및 타임라인](project-scope/process-timeline.md)
   - [결과물](project-scope/deliverables.md)
   - [요구 사항 확인 목록](project-scope/requirement-checklists.md)
- 개발 {#development}
   - [플랫폼 도구](development/platform-tools.md)
   - [프로젝트 관리 도구](development/project-management-tools.md)
   - [프로젝트 구현 방법론](development/delivery.md)
   - [품질 관리](development/quality-control.md)
- 계획 및 거버넌스 {#planning}
   - [게재 및 계획 접근 방식](planning/delivery.md)
   - [책임 및 소유권](planning/ownership.md)
   - [프로젝트 거버넌스](planning/governance.md)
- 아키텍처 및 통합 {#architecture}
   - [Enterprise 참조](architecture/enterprise-blueprint.md)
   - 전역 참조 아키텍처 {#global-reference-architecture}
      - [개요](architecture/global-reference/overview.md)
      - [예시](architecture/global-reference/examples.md)
      - 작성기 개발 {#composer}
         - [개요](architecture/global-reference/composer/overview.md)
         - [프로젝트 구조](architecture/global-reference/composer/project-structure.md)
         - [팁과 트릭](architecture/global-reference/composer/tips-and-tricks.md)
- 인프라 및 배포 {#infrastructure}
   - [개요](infrastructure/overview.md)
   - 자체 호스팅 {#self-hosting}
      - [개요](infrastructure/self-hosting/overview.md)
      - [온-프레미스 인프라](infrastructure/self-hosting/on-premises.md)
      - [보안 개념](infrastructure/self-hosting/security-concepts.md)
      - [원격 분석 및 도구 모니터링](infrastructure/self-hosting/monitoring-tools.md)
      - [재해 복구 아이디어](infrastructure/self-hosting/disaster-recovery-ideas.md)
      - [성능 팁](infrastructure/self-hosting/performance-tips.md)
   - 클라우드 인프라 {#cloud}
      - [개요](infrastructure/cloud/overview.md)
      - [지역](infrastructure/cloud/regions.md)
      - [기술](infrastructure/cloud/technology.md)
      - [보안 및 규정 준수](infrastructure/cloud/security.md)
   - 성능 최적화 {#performance}
      - [일반적인 문제](infrastructure/performance/optimization.md)
      - [벤치마크](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- 시작 준비 {#launch}
   - [개요](launch/overview.md)
   - [실행 전 단계](launch/pre-launch-steps.md)
   - [시작 단계](launch/launch-steps.md)
   - [Post-launch 단계](launch/post-launch-steps.md)
- {#maintenance} 유지 관리 및 지원
   - [개요](maintenance/overview.md)
   - [Managed Services Adobe](maintenance/adobe-managed-services.md)
- 모범 사례 {#best-practices}
   - [개요](best-practices/phases.md)
   - {#planning} 계획 중
      - [개요](best-practices/planning/overview.md)
      - [카탈로그 관리](best-practices/planning/catalog-management.md)
      - [사이트, 스토어 및 스토어 보기 구성](best-practices/planning/sites-stores-store-views.md)
      - [보고 구성](best-practices/planning/reporting-configuration.md)
      - [클라우드 배포를 위한 데이터베이스 &#x200B; 구성](best-practices/planning/database-on-cloud.md)
      - [MySQL 구성](best-practices/planning/mysql-configuration.md)
      - [Redis 서비스 구성](best-practices/planning/redis-service-configuration.md)
      - [OPcache 메모리 크기](best-practices/planning/opcache-memory-size.md)
      - [Realpath 캐시 크기](best-practices/planning/realpath-cache-size.md)
      - [확장](best-practices/planning/extensions.md)
      - [파트너 에스컬레이션](best-practices/planning/partner-escalation.md)
      - [결제 저장 처리](best-practices/planning/payment-processing-storage.md)
   - 개발 {#development}
      - [개요](best-practices/development/overview.md)
      - [일반 모범 사례](best-practices/development/general.md)
      - [코드 관리](best-practices/development/code-management.md)
      - [코드 검토](best-practices/development/code-review.md)
      - [디버깅](best-practices/development/debugging.md)
      - [예외 처리](best-practices/development/exception-handling.md)
      - [Git 분기](best-practices/development/git-branching.md)
      - [카탈로그 이미지 크기 조정](best-practices/development/catalog-image-resizing.md)
      - [이미지 최적화](best-practices/development/image-optimization.md)
      - [문제 해결](best-practices/development/troubleshooting.md)
      - [CSS 및 JS 파일 최적화](best-practices/development/optimize-css-js-files.md)
      - [비공개 콘텐츠 블록](best-practices/development/private-content-block-configuration.md)
      - [정적 콘텐츠 배포](best-practices/development/static-content-deployment.md)
      - [데이터베이스 테이블 수정](best-practices/development/modifying-core-and-third-party-tables.md)
      - [코어 및 타사 코드 수정](best-practices/development/modifying-core-and-third-party-code.md)
   - {#launch} 시작
      - [개요](best-practices/launch/overview.md)
      - [웹 크롤러 구성](best-practices/launch/robots-txt.md)
      - [사이트 및 인프라 보안](best-practices/launch/security-best-practices.md)
   - 유지 관리 {#maintenance}
      - [개요](best-practices/maintenance/overview.md)
      - [감사 프론트엔드 성능](best-practices/maintenance/frontend-performance.md)
      - [백엔드 성능 최적화](best-practices/maintenance/backend-performance.md)
      - [인덱서 구성](best-practices/maintenance/indexer-configuration.md)
      - [규모에 맞게 패치](best-practices/maintenance/patching-at-scale.md)
      - [주문 처리](best-practices/maintenance/order-processing-configuration.md)
      - [데이터베이스 성능 문제 해결](best-practices/maintenance/resolve-database-performance-issues.md)
      - [보안 인시던트에 응답](best-practices/maintenance/respond-to-security-incident.md)
      - [프로덕션 사이트에 대한 관리자 업데이트 예약](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [서비스 업데이트](best-practices/maintenance/update-services.md)
      - [업그레이드 체크리스트](best-practices/maintenance/upgrade-checklist.md)
      - [MariaDB에 대한 업그레이드 사전 요구 사항](best-practices/maintenance/mariadb-upgrade.md)
- [운영 안내서로 돌아가기](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
