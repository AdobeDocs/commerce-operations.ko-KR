---
title: 모듈 활성화 또는 비활성화
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source 모듈을 관리합니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---


# 모듈 활성화 또는 비활성화

이 명령에는 필수 구성 요소가 없습니다.

## 모듈 상태

다음 명령을 사용하여 사용 가능한 모듈 및 사용 불가능한 모듈을 나열합니다.

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

위치

* `--enabled` 모든 활성화된 모듈을 나열합니다.
* `--disabled` 비활성화된 모듈을 모두 나열합니다.
* `<module-list>` 는 상태를 확인할 모듈의 공백으로 구분된 목록입니다. 모듈 이름에 특수 문자가 포함되어 있으면 이름을 작은 따옴표나 큰 따옴표로 묶습니다.

## 모듈 활성화, 비활성화

사용 가능한 모듈을 활성화하거나 비활성화하려면 다음 명령을 사용하십시오.

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

위치

* `<module-list>` 는 활성화하거나 비활성화할 모듈의 공백으로 구분된 목록입니다. 모듈 이름에 특수 문자가 포함되어 있으면 이름을 작은 따옴표나 큰 따옴표로 묶습니다.
* `--all` 모든 모듈을 동시에 활성화하거나 비활성화합니다.
* `-f` 또는 `--force` 종속성 없이 모듈을 활성화하거나 비활성화하도록 강제합니다. 이 옵션을 사용하기 전에 [모듈 활성화 및 비활성화 정보](#about-enabling-and-disabling-modules).
* `-c` 또는 `--clear-static-content` 청소기 [생성된 정적 보기 파일](../../configuration/cli/static-view-file-deployment.md).

   정적 보기 파일을 지우지 못하면 이름이 같은 파일이 여러 개 있고 모든 파일을 지우지 않는 경우 문제가 발생할 수 있습니다.

   즉, [정적 파일 대체](../../configuration/cli/static-view-file-deployment.md) 정적 파일을 지우지 않고 이름이 지정된 파일이 두 개 이상 있는 경우 `logo.svg` 다른 폴백으로 인해 잘못된 파일이 표시될 수 있습니다.

예를 들어 `Magento_Weee` 을 입력합니다.

```bash
bin/magento module:disable Magento_Weee
```

모듈 활성화 및 비활성화에 대한 자세한 내용은 [모듈 활성화 및 비활성화 정보](#about-enabling-and-disabling-modules).

## 데이터베이스 업데이트

하나 이상의 모듈을 활성화한 경우 다음 명령을 실행하여 데이터베이스를 업데이트합니다.

```bash
bin/magento setup:upgrade
```

그런 다음 캐시를 지웁니다.

```bash
bin/magento cache:clean
```

## 모듈 활성화 및 비활성화 정보

Adobe Commerce 및 Magento Open Source을 사용하면 현재 사용 가능한 모듈을 활성화하거나 비활성화할 수 있습니다. 즉, Adobe 제공 모듈이나 현재 사용 가능한 타사 모듈입니다.

특정 모듈에는 다른 모듈에 대한 종속성이 있습니다. 이 경우 모듈이 다른 모듈에 종속되어 있으므로 모듈을 활성화하거나 비활성화하지 못할 수 있습니다.

또한 *충돌* 둘 다 동시에 사용할 수 없는 모듈입니다.

예:

* 모듈 A는 모듈 B에 따라 다릅니다. 모듈 A를 먼저 비활성화하지 않으면 모듈 B를 비활성화할 수 없습니다.

* 모듈 A는 모듈 B에 따라 다르며, 둘 다 비활성화되어 있습니다. 모듈 A를 활성화하려면 먼저 모듈 B를 활성화해야 합니다.

* 모듈 A가 모듈 B와 충돌합니다. 모듈 A와 모듈 B를 비활성화하거나, 두 모듈을 비활성화하되 *사용할 수 없음* 모듈 A와 모듈 B를 동시에 활성화합니다.

* 종속성은 `require` Adobe Commerce 및 Magento Open Source의 필드 `composer.json` 각 모듈에 대한 파일입니다. 분쟁은 `conflict` 모듈의 필드 `composer.json` 파일. 이 정보를 사용하여 종속성 그래프를 작성합니다. `A->B` 은 모듈 A가 모듈 B에 따라 달라짐을 의미합니다.

* A *종속성 체인* 는 모듈에서 다른 모듈로의 경로입니다. 예를 들어, 모듈 A가 모듈 B에 종속되고 모듈 B가 모듈 C에 종속되면 종속성 체인은 다음과 같습니다 `A->B->C`.

다른 모듈에 종속된 모듈을 활성화하거나 비활성화하려고 하면 종속성 그래프가 오류 메시지에 표시됩니다.

>[!NOTE]
>
>A모듈이 가능해요 `composer.json` 는 모듈 B와의 충돌을 선언하지만, 반대의 경우는 선언하지 않습니다.

*명령줄 전용:* 종속성에 관계없이 모듈을 활성화하거나 비활성화하려면 선택 사항을 사용합니다 `--force` 변합니다.

>[!NOTE]
>
>사용 `--force` 저장소를 비활성화하고 관리자 액세스에 문제가 발생할 수 있습니다.
