---
title: 업그레이드 호환성 도구 개발자 정보
description: API 색인 통합을 사용하여 업그레이드 호환성 도구를 사용자 지정합니다.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---


# 업그레이드 호환성 도구 개발자 정보

이 주제에서는 Adobe Commerce 코드와 함께 긴밀하게 작업하고 업그레이드 호환성 도구에 대한 자세한 정보를 알고 싶은 개발자를 위한 정보를 제공합니다. You can use this knowledge to customize the tool&#39;s components.

## Adobe Commerce API 색인 통합

Adobe Commerce API index integration is an internal integration solution that encompasses a set of tools to explore Adobe Commerce extensions developed by Adobe, Adobe Commerce Partners, and third-party vendors based on static code analysis.

Adobe Commerce API 색인과의 통합은 다음을 통해 수행됩니다.

`sut\Domain\MRay\MRayInterface`

를 통해 구현됩니다 `config/services.yaml` 파일. 이 값은 메서드의 응답이 있는 위치를 결정합니다 `api()` 및 `modules()` 에서 가져옵니다.

설치에 따라 응답을 사용자 지정하려면 이 파일을 편집합니다. 에 지정된 값 바꾸기 `sut\Domain\MRay\MRayInterface`:

### 사용자 지정 값의 예

`sut\Domain\MRay\MRayInterface : "@sut_mray_mock"`

이전 예에서는 업그레이드 호환성 도구에서 `@sut_mray_mock` 로서의 `MRayInterface` 구현 을 참조하십시오. 의 응답 `api()` 및 `modules()` 메서드는 다음 파일에서 가져옵니다.

- `dev/mray_mock_files/api.json`
- `dev/mray_mock_files/modules.json`

>[!NOTE]
>
>를 변경할 때 `services.yaml` 파일, 삭제 `var/cache/` 폴더를 삭제하여 변경 사항을 올바르게 적용할 수 있습니다.

## 단위 테스트

단위 테스트를 실행하려면 다음 명령 중 하나를 실행합니다.

- `vendor/bin/phpunit tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist --testsuite=unit-tests`

## 통합 테스트

통합 테스트를 실행하려면 다음 명령 중 하나를 실행합니다.

- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist tests/integration`
- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist --testsuite=integration-tests`

## 수락 테스트

1. Before executing acceptance tests, you must set the Adobe Commerce URL in the `phpunit` configuration file.
1. 기본값 복사 `tests/acceptance/phpunit.xml` 파일(.dist 접미사 제외)
1. 변경 `TESTS_BASE_URL` 테스트할 Adobe Commerce URL을 가리킵니다.
1. To run the acceptance tests, execute one of the following commands:

   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml tests/acceptance`
   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml --testsuite=acceptance-tests`

## GraphQL 단위 테스트 및 ESLint 코드 분석

### Requirements

>[!NOTE]
>
>You must have Node.js on your system, see the [Node.js documentation](https://nodejs.dev/learn/how-to-install-nodejs).

다음은 MacOS 시스템에 대한 지침입니다.

1. 터미널을 열고 프로젝트의 루트 디렉토리로 이동합니다.
1. 프로젝트 종속성 설치:

   ```bash
   npm install
   ```

### GraphQL 단위 테스트

다음 [Jest](https://jestjs.io/docs/getting-started) 프레임워크는 다음 JS 단위 테스트를 만드는 데 사용됩니다.

테스트 내용 `dev/tests/Js`.

테스트를 위한 문자열 스키마가 내에 있습니다 `dev/tests/Acceptance/_files/graphql_schemas`.

단위 테스트 실행 또는 `jest` 아래와 같이 변경하는 것을 의미합니다.

```bash
./node_modules/.bin/jest --verbose --rootDir=dev/tests/Js/
```

### ESLint 코드 분석

[ESLint](https://eslint.org/docs/user-guide/getting-started) 는 코드를 보다 일관성 있게 만들고 버그를 방지하기 위해 JavaScript 코드에서 발견되는 문제 패턴을 식별하는 정적 코드 분석 도구입니다.

실행 `eslint` 다음과 같이 코드를 분석할 수 있습니다.

```bash
./node_modules/.bin/eslint -c dev/tests/Static/.eslintrc --rulesdir vendor/magento/magento-coding-standard/eslint/rules path/to/analyse
```

## 복잡성 점수

다음 **복잡성 점수** 는 현재 버전에서 새 버전으로 업그레이드하는 것이 얼마나 어려운지 나타내는 그림입니다. 숫자가 낮으면 업그레이드가 더 수월함을 나타냅니다.

>[!NOTE]
>
>복잡도 점수는 0에서 ∞ 사이입니다.

이 점수는 분석에서 추출된 결과를 기반으로 합니다.

- 식별된 문제 수
- 식별된 문제 심각도

The Upgrade Compatibility Tool calculates this score according to the complexity score formula below.

### Complexity score formula

`Complexity Score = (Critical issues * 3) + (Errors *2) + Warnings`

>[!WARNING]
>
>These are absolute values.
