---
title: 모듈 활성화 또는 비활성화
description: Adobe Commerce 모듈을 관리하려면 다음 단계를 따르십시오.
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# 모듈 활성화 또는 비활성화

이 명령에는 필수 구성 요소가 없습니다.

## 모듈 상태

다음 명령을 사용하여 사용 및 사용 안 함 모듈을 나열합니다.

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

위치

* `--enabled`은(는) 활성화된 모든 모듈을 나열합니다.
* `--disabled`은(는) 비활성화된 모든 모듈을 나열합니다.
* `<module-list>`은(는) 상태를 확인할 공백으로 구분된 모듈 목록입니다. 모듈 이름에 특수 문자가 포함되어 있으면 이름을 작은따옴표나 큰따옴표로 묶습니다.

>[!NOTE]
>
>클라우드 프로젝트에서 모듈을 직접 활성화하거나 비활성화할 수 없습니다. 이러한 명령을 로컬로 실행한 다음 환경의 `app/etc/config.php` 파일에 변경 내용을 푸시해야 합니다. [Pro 프로젝트 워크플로: 배포 워크플로](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow)를 참조하십시오.

## 모듈 활성화, 비활성화

사용 가능한 모듈을 활성화하거나 비활성화하려면 다음 명령을 사용하십시오.

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

위치

* `<module-list>`은(는) 사용하거나 사용하지 않도록 설정할 공백으로 구분된 모듈 목록입니다. 모듈 이름에 특수 문자가 포함되어 있으면 이름을 작은따옴표나 큰따옴표로 묶습니다.
* `--all`에서 모든 모듈을 동시에 사용하거나 사용하지 않도록 설정할 수 있습니다.
* 의존성에도 불구하고 모듈을 강제로 사용하거나 사용하지 않도록 설정하는 `-f` 또는 `--force`. 이 옵션을 사용하기 전에 [모듈 사용 및 사용 안 함 정보](#about-enabling-and-disabling-modules)를 참조하세요.
* `-c` 또는 `--clear-static-content`이(가) [생성된 정적 보기 파일을 정리](../../configuration/cli/static-view-file-deployment.md)합니다.

  같은 이름의 파일이 여러 개 있고 모두 지우지 않으면 정적 보기 파일을 지우지 못할 경우 문제가 발생할 수 있습니다.

  즉, [정적 파일 대체](../../configuration/cli/static-view-file-deployment.md) 규칙 때문에 정적 파일을 지우지 않고 이름이 다른 `logo.svg`이(가) 두 개 이상 있으면 대체(fallback)로 인해 잘못된 파일이 표시될 수 있습니다.

예를 들어 `Magento_Weee` 모듈을 비활성화하려면 다음을 입력합니다.

```bash
bin/magento module:disable Magento_Weee
```

모듈 사용 및 사용 안 함에 대한 중요한 정보는 [모듈 사용 및 사용 안 함 정보](#about-enabling-and-disabling-modules)를 참조하십시오.

## 데이터베이스 업데이트

하나 이상의 모듈을 활성화한 경우 다음 명령을 실행하여 데이터베이스를 업데이트합니다.

```bash
bin/magento setup:upgrade
```

그런 다음 캐시를 정리합니다.

```bash
bin/magento cache:clean
```

## 모듈 활성화 및 비활성화 정보

Adobe Commerce을 사용하면 현재 사용 가능한 모듈, 즉 Adobe에서 제공하는 모듈 또는 현재 사용 가능한 타사 모듈을 활성화하거나 비활성화할 수 있습니다.

특정 모듈에는 다른 모듈에 대한 종속성이 있습니다. 이 경우 다른 모듈에 대한 종속성이 있으므로 모듈을 활성화하거나 비활성화하지 못할 수 있습니다.

또한 동시에 둘 다 활성화할 수 없는 *충돌하는* 모듈이 있을 수 있습니다.

예:

* 모듈 A는 모듈 B에 종속됩니다. 먼저 모듈 A를 비활성화하지 않으면 모듈 B를 비활성화할 수 없습니다.

* 모듈 A는 모두 비활성화된 모듈 B에 종속됩니다. 모듈 A를 활성화하려면 먼저 모듈 B를 활성화해야 합니다.

* 모듈 A가 모듈 B와 충돌합니다. 모듈 A와 모듈 B를 사용하지 않도록 설정할 수도 있고, 둘 중 하나를 사용하지 않도록 설정할 수도 있지만 *모듈 A와 모듈 B를 동시에 사용할 수 없습니다*.

* 각 모듈에 대한 Adobe Commerce `require` 파일의 `composer.json` 필드에 종속성이 선언되었습니다. 모듈 `conflict` 파일의 `composer.json` 필드에 충돌이 선언되었습니다. 종속성 그래프를 만드는 데 이 정보를 사용합니다. `A->B`은(는) 모듈 A가 모듈 B에 종속됨을 의미합니다.

* *종속성 체인*&#x200B;은(는) 모듈에서 다른 모듈로의 경로입니다. 예를 들어 모듈 A가 모듈 B에 종속되고 모듈 B가 모듈 C에 종속되는 경우 종속성 체인은 `A->B->C`입니다.

다른 모듈에 종속된 모듈을 활성화하거나 비활성화하려고 하면 종속성 그래프가 오류 메시지에 표시됩니다.

>[!NOTE]
>
>모듈 A의 `composer.json`이(가) 모듈 B와 충돌을 선언할 수 있지만 반대로 선언할 수는 없습니다.

*명령줄만:* 종속성과 관계없이 모듈을 사용하도록 설정하거나 사용하지 않도록 설정하려면 선택적 `--force` 인수를 사용하십시오.

>[!NOTE]
>
>`--force`을(를) 사용하면 스토어가 비활성화되어 관리자에 액세스하는 데 문제가 발생할 수 있습니다.
