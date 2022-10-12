---
title: 클라우드 기반의 상거래를 위한 원격 스토리지
description: 클라우드 인프라에서 Adobe Commerce을 위한 원격 스토리지를 설정하는 방법에 대한 지침을 참조하십시오.
source-git-commit: 9a5993c9a65ad210f1a9682734730f235bbc3d44
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Commerce on Cloud 인프라를 위한 원격 스토리지 구성

클라우드 인프라 프로젝트에서 Adobe Commerce과 함께 원격 스토리지 솔루션을 사용하도록 선택하는 경우 [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) 의 지침 _명백히_ AWS S3에서 실제 이미지 최적화가 작동하는지 확인하는 설명서입니다.

다음 사항에 대비하십시오. [강력한 자격 증명](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#cloud-fastly-creds). Pro 프로젝트에서 SSH를 사용하여 서버에 연결하고 `/mnt/shared/fastly_tokens.txt` 파일. 스테이징 및 프로덕션 환경에는 고유한 자격 증명이 있습니다. 각 환경에 대한 자격 증명을 받아야 합니다.

다음 작업으로 클라우드 프로젝트에 대한 원격 저장소를 계속 설정합니다.

1. 구성 [강력한 백엔드 통합](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. 에 대한 VCL 논리 만들기 [AWS S3 인증](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. 에 대한 VCL 논리 만들기 [AWS S3 버킷에 대한 백엔드 요청](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
