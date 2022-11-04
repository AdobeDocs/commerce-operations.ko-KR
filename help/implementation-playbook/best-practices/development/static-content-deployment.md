---
title: 정적 콘텐츠 배포 우수 사례
description: Adobe Commerce 또는 Magento Open Source 스토어에 정적 콘텐츠가 표시되지 않는 문제를 방지하는 방법을 배웁니다.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---


# 정적 콘텐츠 배포 우수 사례

이 문서에서는 정적 콘텐츠를 웹 사이트에서 사용할 수 없는 문제를 방지하기 위해 Adobe Commerce의 정적 콘텐츠 배포(SCD) 우수 사례에 대해 설명합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

* Adobe Commerce on cloud 인프라
* Adobe Commerce 온-프레미스
* Magento Open Source

## 우수 사례

웹 사이트에서 정적 콘텐츠를 사용할 수 없는 문제를 방지하려면 다음 우수 사례에 따라 정적 콘텐츠가 올바르게 구성되고 배포되었는지 확인하십시오.

1. 배포 지침을 따라야 합니다.
   * Adobe Commerce 온-프레미스 및 Magento Open Source(모든 버전)에 대해서는 [배포 개요](../../../configuration/deployment/overview.md) 개발자 설명서에서 를 참조하십시오.
   * 클라우드 인프라(모든 버전)의 Adobe Commerce에 대해서는 [클라우드 배포 프로세스](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) 및 [정적 콘텐츠 배포 전략](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) 개발자 설명서에서 를 참조하십시오.

1. 클라우드 인프라(모든 버전)의 Adobe Commerce에 대해 Ece-Tools가 최신 릴리스에 있는지 확인하십시오. 다음을 참조하십시오. [Ece-tools 버전 업데이트](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) 개발자 설명서에서 를 참조하십시오.
1. 클라우드 인프라(모든 버전)의 Adobe Commerce에 대해 정적 콘텐츠가 배포 단계가 아니라 빌드 단계 동안 배포되었는지 확인합니다. 다음을 참조하십시오. [저장소 설정에 대한 구성 관리 - 정적 콘텐츠 배포 성능](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) 개발자 설명서에서 를 참조하십시오.
1. 오랫동안 실행되는 크론 작업이 없는지 확인하고 오랫동안 실행되는 크론 프로세스를 종료하십시오. 장기 실행 크론 작업이 CPU 리소스를 차지하며 배포 시간을 크게 늘릴 수 있습니다.
1. Adobe Commerce 온-프레미스 및 Magento Open Source(모든 버전)의 경우, `php` CLI의 프로세스는 `pub/static` 디렉토리. 그렇지 않으면 정적 콘텐츠 배포에서 해당 디렉터리에 파일을 쓸 수 없는 문제가 발생할 수 있습니다. 자세한 내용: [파일 시스템 액세스 권한](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) 개발자 설명서에서 를 참조하십시오.
1. 다음을 확인합니다. `generated` 디렉터리가 빌드에 걸쳐 공유 디렉터리가 아닙니다. 그렇지 않으면 빌드가 임의로 실패할 수 있습니다. 자세한 내용:
   * Adobe Commerce 온-프레미스 및 Magento Open Source(모든 버전): [기술 세부 정보](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) 개발자 설명서에서 를 참조하십시오.
   * 클라우드 인프라의 Adobe Commerce(모든 버전): [배포 프로세스 - 2단계: 빌드](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) 개발자 설명서에서 를 참조하십시오.

1. SCD 전략을 확인합니다. 다음 *빠른 속도* 전략은 기본값입니다. 자세한 내용:
   * Adobe Commerce 온-프레미스 및 Magento Open Source(모든 버전): [정적 파일 배포 전략](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) 개발자 설명서에서 를 참조하십시오.
   * 클라우드 인프라의 Adobe Commerce(모든 버전): [변수 배포 - SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) 개발자 설명서에서 를 참조하십시오.

## 추가 정보

개발자 설명서에서:

* [정적 컨텐츠 컨테이너](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [정적 콘텐츠 서명](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [변수 배포 - STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [배포 흐름](../../../performance/deployment-flow.md)
* [다운타임 없이 구축](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [클라우드 배포 최적화](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)

