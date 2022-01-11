---
title: 업그레이드 호환성 도구 사전 요구 사항
description: '시스템이 Adobe Commerce 프로젝트용 업그레이드 호환성 도구를 실행하는 데 필요한 요구 사항을 충족하는지 확인합니다. '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# 업그레이드 호환성 도구 사전 요구 사항

업그레이드 호환성 도구를 실행하면 수행해야 하는 작업을 식별할 수 있습니다 **이전** Adobe Commerce 버전 업그레이드

업그레이드 호환성 도구를 실행하기 위한 최소 요구 사항은 다음과 같습니다.

| **요구 사항** | **제한** |
|----------------|-----------------|
| PHP 버전 | >= 7.3 |
| 작성기 | 없음 |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`, 또는 `>=16.0.0`) |
| 메모리 제한 | 최소 2GB RAM |
| Adobe Commerce 액세스 키 | 없음 |
| Adobe Commerce(오픈 소스 또는 엔터프라이즈) | 없음 |

모든 운영 체제에서 업그레이드 호환성 도구를 실행할 수 있습니다. Adobe Commerce 인스턴스가 있는 업그레이드 호환성 도구를 실행할 필요가 없습니다.

Adobe Commerce 인스턴스의 소스 코드에 액세스하려면 업그레이드 호환성 도구가 필요합니다. 예를 들어 한 서버에 설치하고 다른 서버에 Adobe Commerce 설치 시 가리킬 수 있습니다. 자세한 내용은 [설치](../upgrade-compatibility-tool/install.md) 주제 를 참조하십시오.
