---
title: 코드 컴파일러
description: 명령줄에서 코드 컴파일러를 실행하는 방법에 대해 알아봅니다.
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# 코드 컴파일러

{{file-system-owner}}

코드 컴파일에는 다음이 포함됩니다(특정 순서 없음).

- 애플리케이션 코드 생성(팩토리, 프록시)
- 영역 구성 집계(영역당 최적화된 종속성 삽입 구성)
- 인터셉터 생성(인터셉터의 최적화된 코드 생성)
- 차단 캐시 생성
- 저장소 코드 생성(API에 대해 생성된 코드)
- 서비스 데이터 속성 생성(데이터 객체에 대해 생성된 확장 클래스)

[\Magento\Setup\Module\Di\App\Task\Operation][operation] 네임스페이스에서 코드 컴파일 클래스를 찾을 수 있습니다.

단일 테넌트 컴파일러를 실행하려면

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

Commerce 응용 프로그램을 설치하기 전에 코드를 컴파일하려면 다음을 수행하십시오.

경우에 따라 Commerce 애플리케이션을 설치하기 전에 코드를 컴파일할 수 있습니다.

1. 모듈을 활성화합니다.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   정적 콘텐츠를 지우려면 `[-c|--clear-static-content]` 옵션을 사용하십시오. 이는 이전에 모듈을 활성화했거나 비활성화했으며 모듈에 대해 이전에 생성된 정적 콘텐츠를 지워야 하는 경우 필요합니다.

   [모듈 사용](../../installation/tutorials/manage-modules.md)을 참조하세요.

1. 코드를 컴파일합니다.

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

데이터베이스 없이 코드를 컴파일하려면 [Magento을 설치하지 않고 정적 보기 파일 배포](../cli/static-view-file-deployment.md)를 참조하십시오.

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
