---
user-guide-title: 구현 플레이북
user-guide-description: 성공적인 Adobe Commerce 사이트에 대한 계획 수립 및 구현을 위한 전략에 대해 알아봅니다.
mini-toc-levels: 3
source-git-commit: 86149bbe268a573f94e8bdb34974403459e46909
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 6%

---


# 구현 플레이북 {#implementation-playbook}

- [개요](overview.md)
- 상거래 {#intro}
   - [Adobe Commerce 정보](intro/about-commerce.md)
   - [플랫폼 개발 원칙](intro/platform-development.md)
- 프로젝트 범위 {#project-scope}
   - [지식은 힘이다](project-scope/knowledge.md)
   - [주요 이해 관계자](project-scope/key-stakeholders.md)
   - [프로세스 및 타임라인](project-scope/process-timeline.md)
   - [결과물](project-scope/deliverables.md)
   - [요구 사항 확인 목록](project-scope/requirement-checklists.md)
- 개발 {#development}
   - [플랫폼 도구](development/platform-tools.md)
   - [프로젝트 관리 도구](development/project-management-tools.md)
   - [프로젝트 구현 방식](development/delivery.md)
   - [품질 관리](development/quality-control.md)
- 계획 및 거버넌스 {#planning}
   - [전달 및 계획 방식](planning/delivery.md)
   - [책임 및 소유권](planning/ownership.md)
   - [프로젝트 거버넌스](planning/governance.md)
- 아키텍처 및 통합 {#architecture}
   - [기능](architecture/capabilities.md)
   - [통합 전략](architecture/integration-strategy.md)
   - [확장성 전략](architecture/extensibility-strategy.md)
   - [통합 옵션](architecture/integration-options.md)
   - [글로벌 참조 아키텍처](architecture/global-reference.md)
   - 헤드리스 커머스 {#headless}
      - [이점](architecture/headless/benefits.md)
      - [헤드리스로 여정](architecture/headless/journey-to-headless.md)
      - [마이크로서비스](architecture/headless/microservices.md)
      - [헤드리스의 진화](architecture/headless/evolution.md)
      - [연결된 상점 전면 아키텍처](architecture/headless/legacy-storefront.md)
      - [헤드리스 아키텍처](architecture/headless/adobe-commerce.md)
- 인프라 및 배포 {#infrastructure}
   - [개요](infrastructure/overview.md)
   - [온프레미스 인프라](infrastructure/on-premises.md)
   - 클라우드 인프라 {#cloud}
      - [개요](infrastructure/cloud/overview.md)
      - [지역](infrastructure/cloud/regions.md)
      - [기술](infrastructure/cloud/technology.md)
      - [환경](infrastructure/cloud/environments.md)
      - [관리 서비스](infrastructure/cloud/managed-services.md)
      - [보안 및 규정 준수](infrastructure/cloud/security.md)
   - 성능 최적화 {#performance}
      - [일반적인 문제](infrastructure/performance/optimization.md)
      - [벤치마크](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- 시작 준비 {#launch}
   - [개요](launch/overview.md)
   - [사전 실행 단계](launch/pre-launch-steps.md)
   - [시작 단계](launch/launch-steps.md)
   - [출시 후 단계](launch/post-launch-steps.md)
- 유지 관리 및 지원 {#maintenance}
   - [개요](maintenance/overview.md)
   - [Adobe Managed Services](maintenance/adobe-managed-services.md)
- 우수 사례 {#best-practices}
   - [개요](best-practices/phases.md)
   - 계획 {#planning}
      - [개요](best-practices/planning/overview.md)
      - [사이트, 저장소 및 저장소 보기 구성](best-practices/planning/sites-stores-store-views.md)
      - [보고 구성](best-practices/planning/reporting-configuration.md)
      - [클라우드 배포를 위한 데이터베이스 &#x200B; 구성](best-practices/planning/database-on-cloud.md)
      - [MySQL 슬레이브 연결 &#x200B; 구성](best-practices/planning/configure-mysql-slave-connection-on-cloud.md)
      - [MySQL 트리거 사용](best-practices/planning/mysql-triggers-usage.md)
      - [Redis 서비스 구성](best-practices/planning/redis-service-configuration.md)
      - [OPcache 메모리 크기](best-practices/planning/opcache-memory-size.md)
      - [Realpath 캐시 크기](best-practices/planning/realpath-cache-size.md)
      - [카테고리](best-practices/planning/category-limits.md)
      - [제품](best-practices/planning/product-sku-limits.md)
      - [제품 변형](best-practices/planning/product-variations.md)
      - [제품 옵션](best-practices/planning/product-options.md)
      - [제품 속성](best-practices/planning/product-attributes-and-options.md)
      - [제품 목록 페이지 매김](best-practices/planning/product-listing-pagination.md)
      - [제품 장바구니 제한](best-practices/planning/product-cart.md)
      - [프로모션](best-practices/planning/product-cart-promotions.md)
      - [확장](best-practices/planning/extensions.md)
      - [파트너 문제 제기](best-practices/planning/partner-escalation.md)
      - [결제 스토리지 처리](best-practices/planning/payment-processing-storage.md)
   - 개발 {#development}
      - [개요](best-practices/development/overview.md)
      - [이미지 최적화](best-practices/development/image-optimization.md)
      - [문제 해결](best-practices/development/troubleshooting.md)
      - [CSS 및 JS 파일 최적화](best-practices/development/optimize-css-js-files.md)
      - [비공개 콘텐츠 블록](best-practices/development/private-content-block-configuration.md)
      - [정적 콘텐츠 배포](best-practices/development/static-content-deployment.md)
   - Launch {#launch}
      - [개요](best-practices/launch/overview.md)
      - [Adobe 보안 알림 서비스](best-practices/launch/security-notification-service.md)
      - [robots.txt 파일 구성](best-practices/launch/robots-txt.md)
      - [보안 사고 방지 및 대응](best-practices/launch/prevent-respond-security-incident.md)
   - 유지 관리 {#maintenance}
      - [개요](best-practices/maintenance/overview.md)
      - [프런트 엔드 성능 감사](best-practices/maintenance/frontend-performance.md)
      - [인덱서 구성](best-practices/maintenance/indexer-configuration.md)
      - [주문 처리](best-practices/maintenance/order-processing-configuration.md)
      - [프로덕션 사이트에서 관리 업데이트 예약](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [서비스 업데이트](best-practices/maintenance/update-services.md)
      - [업그레이드 검사 목록](best-practices/maintenance/upgrade-checklist.md)
      - [데이터베이스 성능 문제 &#x200B; 해결](best-practices/maintenance/resolve-database-performance-issues.md)
      - [Adobe Commerce 2.3.5 MariaDB용 업그레이드 사전 &#x200B; 요구 사항](best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
