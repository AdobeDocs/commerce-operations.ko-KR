---
title: Adobe Commerce 제거 또는 다시 설치
description: 다음 단계에 따라 Adobe Commerce 및 Magento Open Source의 온-프레미스 설치를 제거하고 다시 설치합니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# Adobe Commerce 제거 또는 다시 설치

이 명령을 사용하기 전에 [애플리케이션 설치](../tutorials/install.md).

## 애플리케이션 업데이트

응용 프로그램을 업데이트하려면

* 보관 위치에서 소프트웨어를 설치했거나 &#39;composer-create-project&#39;를 사용한 경우 [업그레이드 안내서](../../upgrade/overview.md).
* 기여 개발자(즉, 사용자가 `git clone`). [애플리케이션 업데이트](../../upgrade/developer/git-installs.md).

## 응용 프로그램 다시 설치

명령줄에서 응용 프로그램을 다시 설치하는 방법은 역할에 따라 다릅니다.

* 보관 위치에서 소프트웨어를 설치했거나 &#39;composer-create-project&#39;를 사용한 경우 [설치 종속성 업데이트](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* 기여 개발자(즉, `git clone`). [설치 종속성 업데이트](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## 응용 프로그램 제거

응용 프로그램을 제거하면 데이터베이스가 삭제 및 복원되고, 배포 구성이 제거되고, `var`.

응용 프로그램을 제거하려면 다음 명령을 입력합니다.

```bash
bin/magento setup:uninstall
```

다음 메시지가 표시되어 제거에 성공했는지 확인합니다.

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## 필요에 따라 생성된 파일 보관

기본적으로 `bin/magento setup:upgrade` 컴파일된 코드와 캐시를 지웁니다. 일반적으로 `bin/magento setup:upgrade` 구성 요소 및 각 구성 요소를 업데이트하려면 서로 다른 컴파일된 클래스가 필요할 수 있습니다.

그러나 일부 경우(특히 프로덕션에 배포) 시간이 걸릴 수 있으므로 컴파일된 코드를 지우지 않을 수 있습니다. (캐시가 아직 지워졌습니다.) 데이터베이스 스키마 및 데이터를 업데이트하려면 *사용 안 함* 컴파일된 코드를 지우려면 다음을 입력하십시오.

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>선택 사항입니다 `--keep-generated` 선택 사항은 숙련된 시스템 통합자가 제한된 환경에서 사용해야 합니다 *전용*. 이 옵션은 *절대* 개발 환경에서 사용됩니다. 이 선택적 매개 변수를 잘못 사용하면 코드 실행 중에 오류가 발생할 수 있습니다.

## 응용 프로그램 설치

* [명령줄을 사용하여 설치](../advanced.md)
