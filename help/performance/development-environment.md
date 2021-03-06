---
title: 개발 환경 Recommendations
description: 로컬 Adobe Commerce 또는 Magento Open Source 개발 환경을 설정하기 위한 성능 권장 사항에 대해 알아봅니다.
source-git-commit: 87b353b408ecd7f55cea5b4775a0c8523952abc0
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# 개발 환경 권장 사항

이 페이지에서는 상거래 개발 환경에 대한 권장 사항을 제공합니다.

## 비활성화하지 않고 캐시를 지웁니다.

많은 개발자들이 자신의 개발자 인스턴스에서 모든 캐시를 비활성화하는 경향이 있습니다. 모든 캐시를 사용하지 않도록 설정하지 않고 캐시를 청소하는 것이 좋습니다. [!DNL Commerce] 다음 경우에 보다 효율적으로 실행 [캐시 정리] 완전히 비활성화하는 대신 대부분의 캐시 유형은 개발 중에 거의 무효화되지 않습니다.

만약 [캐시 비활성화]에서는 개발 인스턴스에서 페이지 및 블록 캐시만 비활성화하는 것이 좋습니다. 테스트 중에 모든 캐시를 사용하도록 설정해야 합니다.

## 개발 모드에서 피하는 명령

개발 모드에서는 컴파일, 코드 생성 및 정적 컨텐츠 배포에 대한 명령을 실행하지 마십시오. 이 명령은 프로덕션 모드에서만 사용하도록 빌드되었습니다.

**실행 안 함** 개발 모드에서 프로덕션 명령:

* `setup:di:compile` 자동 생성된 클래스와 최적화된 구성 캐시를 생성합니다.

   ```bash
   bin/magento setup:di:compile
   ```

   개발 모드에서 Magento은 주문형 생성을 수행합니다. 실행할 필요가 없습니다. 클래스의 서명을 수정하고 자동 생성된 클래스를 다시 생성해야 하는 경우 `factories/proxies/interceptors`또는 _생성_ 폴더를 입력합니다.

* `setup:static-content:deploy` 저장소에 대한 정적 콘텐츠를 배포합니다.

   ```bash
   bin/magento setup:static-content:deploy
   ```

   개발 모드에서 Magento은 온디맨드 방식으로 수행합니다. 실행할 필요가 없습니다.

## 가상 컴퓨터의 일반 페이지 로드 시간

VM에서 개발하고 Magento 페이지를 로드하는 데 2초 이상 걸리는 경우 환경 설정을 검토하십시오.

<!-- Link definitions -->

[캐시 정리]: https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cache.html#config-cli-subcommands-cache-clean
[캐시 비활성화]: https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cache.html#config-cli-subcommands-cache-en
