---
title: 정적 콘텐츠 배포 우수 사례
description: 정적 콘텐츠가 Adobe Commerce 상점 첫 화면에 표시되지 않는 문제를 방지하는 방법을 알아봅니다.
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# 정적 콘텐츠 배포 우수 사례

이 문서에서는 웹 사이트에서 정적 콘텐츠를 사용할 수 없는 문제를 방지하는 데 도움이 되는 Adobe Commerce의 정적 콘텐츠 배포(SCD) 모범 사례에 대해 설명합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

* 클라우드 인프라의 Adobe Commerce
* Adobe Commerce 온-프레미스

## 우수 사례

웹 사이트에서 정적 콘텐츠를 사용할 수 없는 문제가 발생하지 않도록 하려면 다음 모범 사례에 따라 정적 콘텐츠가 올바르게 구성 및 배포되었는지 확인하십시오.

1. 배포 지침을 따라야 합니다.
   * Adobe Commerce 온-프레미스(모든 버전)의 경우 개발자 설명서에서 [배포 개요](../../../configuration/deployment/overview.md)를 참조하세요.
   * 클라우드 인프라(모든 버전)의 Adobe Commerce에 대해서는 개발자 설명서에서 [클라우드 배포 프로세스](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) 및 [정적 콘텐츠 배포 전략](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/static-content)을 참조하십시오.

1. 클라우드 인프라(모든 버전)의 Adobe Commerce의 경우 ece-tools가 최신 릴리스에 포함되는지 확인하십시오. 개발자 설명서에서 [ece-tools 버전 업데이트](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package)를 참조하십시오.
1. 클라우드 인프라(모든 버전)의 Adobe Commerce의 경우 정적 컨텐츠가 배포 단계가 아닌 빌드 단계에서 배포되었는지 확인하십시오. 개발자 설명서에서 [저장소 설정에 대한 구성 관리 - 정적 콘텐츠 배포 성능](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/store-settings#cloud-confman-scd-over)을 참조하세요.
1. 장기 실행 크론 작업이 없는지 확인하고 장기 실행 크론 프로세스를 중단하십시오. 오래 실행되는 cron 작업은 CPU 리소스를 사용하게 되며 잠재적으로 배포 시간을 크게 늘릴 수 있습니다.
1. Adobe Commerce 온-프레미스(모든 버전)의 경우 CLI의 `php` 프로세스가 `pub/static` 디렉터리에 액세스할 수 있는지 확인하십시오. 그렇지 않으면 정적 콘텐츠 배포에서 해당 디렉터리에 파일을 쓸 수 없는 문제가 발생할 수 있습니다. 자세한 내용은 개발자 설명서에서 [파일 시스템 액세스 권한](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html)을 참조하십시오.
1. `generated` 디렉터리가 빌드의 공유 디렉터리가 아닌지 확인하십시오. 그렇지 않으면 빌드가 임의로 실패할 수 있습니다. 추가 정보:
   * Adobe Commerce 온-프레미스(모든 버전): 개발자 설명서에서 [기술 세부 정보](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html).
   * 클라우드 인프라의 Adobe Commerce(모든 버전): 개발자 설명서의 [배포 프로세스 - 2단계: 빌드](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#cloud-deploy-over-phases-build).

1. SCD 전략을 확인합니다. *빠른* 전략이 기본값입니다. 추가 정보:
   * Adobe Commerce 온-프레미스(모든 버전): 개발자 설명서에서 [정적 파일 배포 전략](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html).
   * 클라우드 인프라의 Adobe Commerce(모든 버전): 개발자 설명서에서 [변수 배포 - SCD\_STRATEGY](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#scd_strategy).

## 추가 정보

개발자 설명서에서:

* [정적 콘텐츠 컨테이너](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [정적 콘텐츠 서명](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [변수 배포 - STATIC\_CONTENT\_SYMLINK](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#static_content_symlink)
* [배포 흐름](../../../performance/deployment-flow.md)
* [다운타임 없는 배포](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)
* [클라우드 배포 최적화](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/optimization)
