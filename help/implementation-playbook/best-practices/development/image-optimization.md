---
title: 더 반응형 사이트를 위해 이미지 최적화
description: 이미지를 최적화하는 단계에 대해 알아보고 Fastly 이미지 최적화를 사용하여 Adobe Commerce 사이트의 응답 시간을 최적화합니다.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---

# 더 반응형 사이트를 위해 이미지 최적화

Adobe Commerce on cloud infrastructure 배포의 경우 업로드하기 전에 이미지를 최적화하여 사이트 응답 시간을 개선합니다. 그런 다음 Fastly 이미지 최적화를 사용하여 이미지 전달 속도를 높이고 이미지 소스 세트의 유지 관리를 단순화합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

클라우드 인프라의 Adobe Commerce


## 이미지 최적화 및 압축

Commerce 사이트에 이미지를 업로드하기 전에 최적화하고 압축하여 성능과 보기 품질의 균형을 유지합니다. 이렇게 하면 공간이 늘어나고 페이지 로드 시간이 줄어듭니다.

- PNG 포맷은 단색의 넓은 영역이 있는 이미지에 대해 더 작은 크기의 이미지를 제공합니다.

- JPEG 형식은 다른 모든 이미지 유형에 대해 더 작은 크기의 이미지를 제공합니다. 가장 높은 압축을 사용합니다(눈에 띄는 성능 저하 없이). 이는 일반적으로 60~80%입니다.

## Fastly 이미지 최적화 활성화 및 구성

Adobe Commerce Cloud 프로젝트에 대한 Fastly 서비스를 설정한 후 이미지 최적화를 활성화하고 구성하는 방법에 대한 지침은 [Fastly 이미지 최적화](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html)를 참조하십시오.

## 추가 정보

- [빠르게 설정](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [잘못 최적화된 이미지로 인해 성능 문제가 발생할 수 있습니다](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
