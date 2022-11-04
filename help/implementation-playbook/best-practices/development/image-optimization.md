---
title: 응답형 사이트를 위한 이미지 최적화
description: 이미지를 최적화하고 실제 이미지 최적화를 사용하여 Adobe Commerce 사이트에서 응답 시간을 최적화하는 단계를 알아봅니다.
role: Developer, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# 응답형 사이트를 위한 이미지 최적화

클라우드 인프라 배포의 Adobe Commerce에 대해 이미지를 업로드하기 전에 최적화하여 사이트 응답 시간을 개선하십시오. 그런 다음 실제 이미지 최적화를 사용하여 이미지 전달을 가속화하고 이미지 소스 세트의 유지 관리를 간소화합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

Adobe Commerce on cloud 인프라


## 이미지 최적화 및 압축

상거래 사이트에 이미지를 업로드하기 전에 최적화 및 압축하여 시청 품질과 성능 균형을 맞춥니다. 이렇게 하면 공간이 증가하고 페이지 로드 시간이 줄어듭니다.

- PNG 포맷은 넓은 영역의 단색 이미지에 더 작은 크기의 이미지를 제공합니다.

- JPEG 형식은 다른 모든 이미지 유형에 대해 작은 크기의 이미지를 제공합니다. 가장 높은 압축(눈에 띄는 저하 없이)을 사용합니다. 보통 60~80%입니다.

## 실제 이미지 최적화 활성화 및 구성

Adobe Commerce Cloud 프로젝트에 대한 기본 서비스를 설정한 후에는 다음을 참조하십시오 [실제 이미지 최적화](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) 이미지 최적화를 활성화하고 구성하는 지침을 참조하십시오.

## 추가 정보

- [기본 설정](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [최적화된 이미지가 잘못 최적화되면 성능 문제가 발생할 수 있습니다](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
