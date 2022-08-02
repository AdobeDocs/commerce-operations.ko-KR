---
title: 코드 컴파일러
description: 명령줄에서 코드 컴파일러를 실행하는 방법을 알아봅니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# 코드 컴파일러

{{file-system-owner}}

코드 컴파일에는 다음 항목이 포함되어 있습니다(특정 순서 없음).

- 애플리케이션 코드 생성(공장, 프록시)
- 영역 구성 집계(최적화됨) [종속성 주입](https://glossary.magento.com/dependency-injection) 영역별 구성
- 인터셉터 생성(인터셉터의 최적화된 코드 생성)
- 차단 캐시 생성
- 저장소 코드 생성(API에 대해 생성된 코드)
- 서비스 데이터 속성 생성(생성됨) [확장](https://glossary.magento.com/extension) 데이터 개체의 클래스

코드 컴파일 클래스는 [\Magento\Setup\Module\Di\App\Task\Operation][operation] 네임스페이스.

단일 테넌트 컴파일러를 실행하려면

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

Commerce 응용 프로그램을 설치하기 전에 코드를 컴파일하려면 다음을 수행하십시오.

경우에 따라 Commerce 응용 프로그램을 설치하기 전에 코드를 컴파일할 수 있습니다.

1. 모듈을 활성화합니다.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   를 사용하십시오 `[-c|--clear-static-content]` 지우기 옵션 [정적 콘텐츠](https://glossary.magento.com/static-content). 이전에 모듈을 활성화하거나 비활성화하고 이전에 모듈에 대해 생성된 정적 콘텐츠를 지워야 하는 경우에 필요합니다.

   자세한 내용은 [모듈 사용](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html).

1. 코드를 컴파일합니다.

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

데이터베이스 없이 코드를 컴파일하려면 [Magento 설치 없이 정적 보기 파일 배포](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
