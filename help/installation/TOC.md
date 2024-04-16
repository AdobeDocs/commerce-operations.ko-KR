---
user-guide-title: 설치 안내서
user-guide-description: 온-프레미스 배포용 Adobe Commerce을 설치하는 방법에 대해 알아봅니다.
feature: Install
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 2%

---


# 설치 안내서 {#installation-guide}

- [개요](overview.md)
- [시스템 요구 사항](system-requirements.md)
- 전제 조건 {#prerequisites}
   - [개요](prerequisites/overview.md)
   - 파일 시스템 {#file-system}
      - [개요](prerequisites/file-system/overview.md)
      - [권한 구성](prerequisites/file-system/configure-permissions.md)
   - 웹 서버 {#web-server}
      - [Ngix](prerequisites/web-server/nginx.md)
      - [Apache](prerequisites/web-server/apache.md)
   - 데이터베이스 서버 {#database-server}
      - [MySQL](prerequisites/database/mysql.md)
      - [원격 연결](prerequisites/database/mysql-remote.md)
   - 검색 엔진 {#search-engine}
      - [개요](prerequisites/search-engine/overview.md)
      - [AWS OpenSearch](prerequisites/search-engine/aws-opensearch.md)
      - [Nginx 구성](prerequisites/search-engine/configure-nginx.md)
      - [Apache 구성](prerequisites/search-engine/configure-apache.md)
   - [PHP](prerequisites/php-settings.md)
   - [메시지 브로커](prerequisites/rabbitmq.md)
   - [보안](prerequisites/security.md)
   - [인증 키](prerequisites/authentication-keys.md)
   - [Adobe Commerce](prerequisites/commerce.md)
   - [옵션 소프트웨어](prerequisites/optional-software.md)
- [빠른 시작 설치](composer.md)
- [고급 설치](advanced.md)
- 설치 후 단계 {#next-steps}
   - [설치 확인](next-steps/verify.md)
   - [애플리케이션 구성](next-steps/configuration.md)
   - [마스크 설정(선택 사항)](next-steps/set-umask.md)
   - 샘플 데이터 설치(선택 사항) {#sample-data}
      - [개요](sample-data/overview.md)
      - [작성기 패키지 다운로드](sample-data/composer-packages.md)
      - [Git 저장소 복제](sample-data/git-repositories.md)
      - [모듈 제거 또는 업데이트](sample-data/remove-or-update.md)
- Tutorials {#tutorials}
   - [파일 시스템, 미디어 및 데이터베이스 백업 및 롤백](tutorials/backup.md)
   - [데이터베이스 상태 확인](tutorials/database-status.md)
   - [메시지 소비자 행동 구성](tutorials/message-consumers.md)
   - [잠금 공급자 구성](tutorials/lock-provider.md)
   - [스토어 구성](tutorials/store.md)
   - [관리자 계정 만들기, 편집 또는 잠금 해제](tutorials/admin.md)
   - [배포 구성 만들기 또는 업데이트](tutorials/deployment.md)
   - [데이터베이스 스키마 만들기](tutorials/database.md)
   - [관리자 URI 표시 또는 변경](tutorials/admin-uri.md)
   - [유지 관리 모드 활성화 또는 비활성화](tutorials/maintenance-mode.md)
   - [모듈 활성화 또는 비활성화](tutorials/manage-modules.md)
   - [확장 설치](tutorials/extensions.md)
   - [Commerce 설치](tutorials/install.md)
   - [보안을 향상하도록 docroot 수정](tutorials/docroot.md)
   - [언어 패키지 제거](tutorials/language-packages.md)
   - [모듈 제거](tutorials/uninstall-modules.md)
   - [Commerce 제거 또는 재설치](tutorials/uninstall.md)
   - [테마 제거](tutorials/themes.md)
   - [데이터베이스 스키마 업그레이드](tutorials/database-upgrade.md)
- [운영 안내서로 돌아가기](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
