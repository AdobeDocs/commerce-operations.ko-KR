---
user-guide-title: 구성 안내서
user-guide-description: Adobe Commerce 애플리케이션 기능 및 서비스를 구성합니다.
feature: Configuration
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---


# 구성 안내서 {#configuration-guide}

+ [개요](overview.md)
+ 일반 설정 {#setup}
   + [응용 프로그램 초기화 및 부트스트랩](bootstrap/initialization.md)
   + [애플리케이션 모드](bootstrap/application-modes.md)
   + [Bootstrap 매개 변수](bootstrap/set-parameters.md)
   + [프로파일링](bootstrap/mage-profiler.md)
   + [기본 디렉터리 경로](bootstrap/mage-directory.md)
+ 배포 {#deployment}
   + [배포 개요](deployment/overview.md)
   + [단일 컴퓨터 배포](deployment/single-machine.md)
   + [파이프라인 배포](deployment/technical-details.md)
   + [전제 조건](deployment/prerequisites.md)
   + [개발 시스템 설정](deployment/development-system.md)
   + [시스템 설정 빌드](deployment/build-system.md)
   + [프로덕션 시스템 설정](deployment/production-system.md)
   + [파일 시스템 액세스 권한](deployment/file-system-permissions.md)
   + 예제 {#examples}
      + [공유 구성 사용](deployment/example-shared-configuration.md)
      + [CLI 명령 사용](deployment/example-using-cli.md)
      + [환경 변수 사용](deployment/example-environment-variables.md)
+ 캐시 {#cache}
   + [캐싱 개요](cache/caching-overview.md)
   + [캐시 유형](cache/cache-types.md)
   + [캐시 옵션](cache/cache-options.md)
   + [L2 캐시](cache/level-two-cache.md)
   + Redis {#redis}
      + [Redis 구성](cache/config-redis.md)
      + [기본 캐시에 Redis 사용](cache/redis-pg-cache.md)
      + [세션 스토리지에 Redis 사용](cache/redis-session.md)
   + {#varnish} 바니시
      + [니스 개요](cache/config-varnish.md)
      + [니스 설치](cache/config-varnish-install.md)
   + [웹 서버](cache/config-varnish-server.md)
   + [Commerce 애플리케이션 구성](cache/configure-varnish-commerce.md)
   + [고급 바니시 구성](cache/config-varnish-advanced.md)
   + [캐시 지우기](cache/use-varnish-cache.md)
   + [여러 Varnish 인스턴스를 지우는 캐시](cache/use-multiple-varnish-cache.md)
   + [바니시 구성 확인](cache/config-varnish-final.md)
   + [바니시 ESI 차단](cache/use-varnish-esi.md)
   + [정적 콘텐츠 캐시](cache/static-content-signing.md)
+ 명령줄 {#cli}
   + [명령줄 도구](cli/config-cli.md)
   + [일반 명령](cli/common-cli-commands.md)
   + [로깅 활성화](cli/enable-logging.md)
   + [캐시 관리](cli/manage-cache.md)
   + [인덱서 관리](cli/manage-indexers.md)
   + [cron 작업 구성](cli/configure-cron-jobs.md)
   + [컴파일 코드](cli/code-compiler.md)
   + [작업 모드](cli/set-mode.md)
   + [메시지 큐 소비자 시작](cli/start-message-queues.md)
   + [URN 형광펜](cli/urn-highlighter.md)
   + [종속성 보고서](cli/dependency-reports.md)
   + [로컬라이제이션](cli/localization.md)
   + 구성 관리 {#configuration-management}
      + [값 설정](cli/set-configuration-values.md)
      + [내보내기 설정](cli/export-configuration.md)
      + [데이터 가져오기](cli/import-configuration.md)
   + 정적 보기 {#static-view}
      + [배포 전략](cli/static-view-file-strategy.md)
      + [정적 보기 파일 배포](cli/static-view-file-deployment.md)
   + [심볼릭 링크 만들기](cli/create-symlinks.md)
   + [단위 테스트 실행](cli/unit-tests.md)
   + [레이아웃 파일 변환](cli/convert-layout-files.md)
   + [성능 테스트를 위한 데이터 생성](cli/generate-data.md)
   + [지원 유틸리티 실행(Commerce 전용)](cli/run-support-utilities.md)
+ 구성 파일 {#files}
   + [배포용 구성 파일](reference/deployment-files.md)
   + [구성 유형](reference/config-create-types.md)
   + [모듈 파일](reference/module-files.md)
   + [모듈 출력](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [기티그노르](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ 구성 경로 {#paths}
   + [일반](reference/config-reference-general.md)
   + [B2B 확장](reference/config-reference-b2b.md)
   + [카탈로그](reference/config-reference-catalog.md)
   + [고객](reference/config-reference-customers.md)
   + [결제 방법](reference/config-reference-payment.md)
   + [판매](reference/config-reference-sales.md)
   + [서비스](reference/config-reference-services.md)
   + [중요 및 시스템별 설정](reference/config-reference-sens.md)
   + [구성 설정 재정의](reference/override-config-settings.md)
+ 크론 작업 {#crons}
   + [크론 작업 및 그룹](cron/custom-cron.md)
   + [cron 참조 사용자 지정](cron/custom-cron-reference.md)
   + [사용자 정의 cron 작업 구성](cron/custom-cron-tutorial.md)
+ 로그 {#logs}
   + [사용자 지정된 로그](logs/custom-logging.md)
   + [로거 인터페이스](logs/logger-interface.md)
   + [데이터베이스 작업 기록](logs/database-activity.md)
   + [사용자 지정 로그 파일에 쓰기](logs/custom-log-files.md)
+ 메시지 큐 {#message-queues}
   + [메시지 큐 프레임워크](queues/message-queue-framework.md)
   + [메시지 대기열 관리](queues/manage-message-queues.md)
   + [Amazon MQ 설정](queues/aws-mq.md)
   + [소비자](queues/consumers.md)
+ 여러 사이트 {#multi-sites}
   + [여러 사이트 및 보기](multi-sites/ms-overview.md)
   + [데이터베이스 엔티티 증가 ID](multi-sites/change-increment-id.md)
   + [관리자에서 설정](multi-sites/ms-admin.md)
   + [Nginx 설정](multi-sites/ms-nginx.md)
   + [Apache 설정](multi-sites/ms-apache.md)
+ 검색 엔진 {#search}
   + [검색 엔진 개요](search/overview-search.md)
   + [검색 엔진 구성](search/configure-search-engine.md)
   + [정지어로 필터링](search/search-stopwords.md)
+ 보안 {#security}
   + [보안 개요](security/overview.md)
   + [암호 해싱](security/password-hashing.md)
   + [캐시 중독](security/cache-poisoning.md)
   + [보안 크론 PHP](security/secure-cron-php.md)
   + [보안 TXT](security/security-txt.md)
   + [재킹 사용을 클릭합니다.](security/xframe-options.md)
+ 저장소 {#storage}
   + [데이터베이스 프로파일러](storage/db-profiler.md)
   + 원격 저장소 {#remote-storage}
      + [원격 스토리지 모듈](remote-storage/remote-storage.md)
      + [AWS S3 버킷](remote-storage/remote-storage-aws-s3.md)
      + [이미지 크기 조정](remote-storage/remote-storage-image-resize.md)
      + [클라우드용 원격 스토리지](remote-storage/cloud-support.md)
   + 세션 저장소 {#session-storage}
      + [세션 저장소 위치](storage/sessions.md)
      + [세션 스토리지용 memcached](storage/memcached.md)
      + [CentOS에서 memcached](storage/memcache-centos.md)
      + [우분투에서 memcached](storage/memcache-ubuntu.md)
   + 데이터베이스 {#split-db} 분할
      + [데이터베이스 분할 개요](storage/multi-master.md)
      + [자동 구성](storage/multi-master-masterdb.md)
      + [수동 구성](storage/multi-master-manual.md)
      + [분할 데이터베이스 확인](storage/multi-master-verify.md)
      + [데이터베이스 복제](storage/multi-master-replication.md)
      + [단일 데이터베이스로 되돌리기](storage/revert-split-database.md)
+ [운영 안내서로 돌아가기](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)