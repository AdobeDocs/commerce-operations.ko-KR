---
title: 개발 환경 권장 사항
description: Adobe Commerce의 개발 환경 권장 사항에 대해 알아봅니다. 구현 지침 및 최적화 전략을 살펴보십시오.
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# 개발 환경 권장 사항

이 페이지에서는 Commerce 개발 환경에 대한 권장 사항을 제공합니다.

## 비활성화 대신 캐시 정리

많은 개발자가 개발자 인스턴스에서 모든 캐시를 비활성화하는 경향이 있습니다. 모든 캐시를 비활성화하지 않고 캐시만 정리하는 것이 좋습니다. 캐시를 완전히 사용하지 않도록 설정하는 대신 [!DNL Commerce]정리할 때[ ](../configuration/cli/manage-cache.md#clean-and-flush-cache-types)이(가) 더 효율적으로 실행됩니다. 대부분의 캐시 유형은 개발 중에 무효화되는 경우가 거의 없습니다.

[캐시를 비활성화](../configuration/cli/manage-cache.md#enable-or-disable-cache-types)하는 경우 개발 인스턴스에서는 페이지 및 블록 캐시만 비활성화하는 것이 좋습니다. 테스트 중에 모든 캐시를 활성화해야 합니다.

## 개발 모드에서 피해야 하는 명령

개발 모드에서 컴파일, 코드 생성 및 정적 콘텐츠 배포에 대한 명령을 실행하지 마십시오. 이 명령은 프로덕션 모드에서만 사용하도록 빌드되었습니다.

개발 모드에서 **프로덕션 명령을 실행하지 않음**:

* `setup:di:compile`은(는) 자동 생성된 클래스와 최적화된 구성 캐시를 생성합니다.

  ```bash
  bin/magento setup:di:compile
  ```

  개발 모드에서 Magento은 주문형 생성을 수행하므로 실행할 필요가 없습니다. 클래스의 서명을 수정했으며 자동 생성된 `factories/proxies/interceptors`을(를) 다시 생성해야 하는 경우 해당 클래스 또는 _생성된_ 폴더를 제거하십시오.

* `setup:static-content:deploy`이(가) 저장소에 대한 정적 콘텐츠를 배포합니다.

  ```bash
  bin/magento setup:static-content:deploy
  ```

  개발 모드에서 Magento은 온디맨드로 수행하므로 실행할 필요가 없습니다.

## 가상 컴퓨터의 일반 페이지 로드 시간

VM에서 개발하고 Magento 페이지를 로드하는 데 2초 이상 걸리는 경우 환경 설정을 검토하십시오.
