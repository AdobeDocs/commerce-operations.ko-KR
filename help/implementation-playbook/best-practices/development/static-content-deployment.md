---
title: 정적 콘텐츠 배포 우수 사례
description: 정적 콘텐츠가 Adobe Commerce 상점 첫 화면에 표시되지 않는 문제를 방지하는 방법을 알아봅니다.
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# 정적 콘텐츠 배포 우수 사례

이 문서에서는 웹 사이트에서 정적 콘텐츠를 사용할 수 없는 문제를 방지하는 데 도움이 되는 Adobe Commerce의 정적 콘텐츠 배포(SCD) 모범 사례에 대해 설명합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

* 클라우드 인프라의 Adobe Commerce
* Adobe Commerce 온-프레미스

## 우수 사례

웹 사이트에서 정적 콘텐츠를 사용할 수 없는 문제가 발생하지 않도록 하려면 다음 모범 사례에 따라 정적 콘텐츠가 올바르게 구성 및 배포되었는지 확인하십시오.

1. 배포 지침을 따라야 합니다.
   * Adobe Commerce 온-프레미스(모든 버전)의 경우 [배포 개요](../../../configuration/deployment/overview.md) 개발자 설명서에서 확인할 수 있습니다.
   * 클라우드 인프라의 Adobe Commerce(모든 버전)에 대해서는 다음을 참조하십시오. [클라우드 배포 프로세스](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) 및 [정적 콘텐츠 배포 전략](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) 개발자 설명서에서 확인할 수 있습니다.

1. 클라우드 인프라(모든 버전)의 Adobe Commerce의 경우 ece-tools가 최신 릴리스에 포함되는지 확인하십시오. 다음을 참조하십시오. [ece-tools 버전 업데이트](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) 개발자 설명서에서 확인할 수 있습니다.
1. 클라우드 인프라(모든 버전)의 Adobe Commerce의 경우 정적 컨텐츠가 배포 단계가 아닌 빌드 단계에서 배포되었는지 확인하십시오. 다음을 참조하십시오. [저장소 설정에 대한 구성 관리 - 정적 콘텐츠 배포 성능](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) 개발자 설명서에서 확인할 수 있습니다.
1. 장기 실행 크론 작업이 없는지 확인하고 장기 실행 크론 프로세스를 중단하십시오. 장기 실행 크론 작업은 CPU 리소스를 소모하고 배포 시간을 크게 늘릴 수 있습니다.
1. Adobe Commerce 온-프레미스(모든 버전)의 경우 `php` cli의 프로세스는 `pub/static` 디렉토리. 그렇지 않으면 정적 콘텐츠 배포에서 해당 디렉터리에 파일을 쓸 수 없는 문제가 발생할 수 있습니다. 추가 정보: [파일 시스템 액세스 권한](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) 개발자 설명서에서 확인할 수 있습니다.
1. 다음을 확인합니다. `generated` 디렉터리가 빌드에서 공유 디렉터리가 아닙니다. 그렇지 않으면 빌드가 임의로 실패할 수 있습니다. 추가 정보:
   * Adobe Commerce 온-프레미스(모든 버전): [기술 세부 정보](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) 개발자 설명서에서 확인할 수 있습니다.
   * 클라우드 인프라의 Adobe Commerce(모든 버전): [배포 프로세스 - 2단계: 빌드](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) 개발자 설명서에서 확인할 수 있습니다.

1. SCD 전략을 확인합니다. 다음 *빠름* 전략은 기본값입니다. 추가 정보:
   * Adobe Commerce 온-프레미스(모든 버전): [정적 파일 배포 전략](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) 개발자 설명서에서 확인할 수 있습니다.
   * 클라우드 인프라의 Adobe Commerce(모든 버전): [변수 배포 - SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) 개발자 설명서에서 확인할 수 있습니다.

## 추가 정보

개발자 설명서에서:

* [정적 콘텐츠 컨테이너](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [정적 콘텐츠 서명](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [변수 배포 - STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [배포 흐름](../../../performance/deployment-flow.md)
* [다운타임 없는 배포](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [클라우드 배포 최적화](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)
