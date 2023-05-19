---
title: Adobe Commerce 제거 또는 재설치
description: Adobe Commerce 및 Magento Open Source의 온-프레미스 설치를 제거하고 다시 설치하려면 다음 단계를 따르십시오.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Adobe Commerce 제거 또는 재설치

이 명령을 사용하기 전에 다음을 수행해야 합니다 [응용 프로그램 설치](../tutorials/install.md).

## 애플리케이션 업데이트

응용 프로그램을 갱신하려면

* 아카이브에서 소프트웨어를 설치했거나 &#39;composer-create-project&#39;를 사용한 경우 [업그레이드 안내서](../../upgrade/overview.md).
* 기여 개발자인 경우(즉, 다음을 사용한 경우) `git clone`), 다음을 참조하십시오. [애플리케이션 업데이트](../../upgrade/developer/git-installs.md).

## 응용 프로그램 다시 설치

명령줄에서 응용 프로그램을 다시 설치하는 방법은 역할에 따라 다릅니다.

* 아카이브에서 소프트웨어를 설치했거나 &#39;composer-create-project&#39;를 사용한 경우 [설치 종속성 업데이트](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* 기여 개발자인 경우(즉, `git clone`), 다음을 참조하십시오. [설치 종속성 업데이트](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## 응용 프로그램 제거

응용 프로그램을 제거하면 데이터베이스가 삭제 및 복원되고 배포 구성이 제거되며 아래의 디렉터리가 지워집니다. `var`.

응용 프로그램을 제거하려면 다음 명령을 입력합니다.

```bash
bin/magento setup:uninstall
```

성공적으로 제거되었음을 확인하는 메시지가 표시됩니다.

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## 필요한 경우 생성된 파일 보관

기본적으로, `bin/magento setup:upgrade` 컴파일된 코드와 캐시를 지웁니다. 일반적으로 다음을 사용합니다 `bin/magento setup:upgrade` 구성 요소와 각 구성 요소를 업데이트하려면 서로 다른 컴파일된 클래스가 필요할 수 있습니다.

그러나 일부 상황(특히 프로덕션에 배포)에서는 시간이 걸릴 수 있으므로 컴파일된 코드를 지우지 않는 것이 좋습니다. (캐시가 아직 지워졌습니다.) 데이터베이스 스키마 및 데이터를 업데이트하려면 *없이* 컴파일된 코드를 지우고 다음을 입력합니다.

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>선택 사항 `--keep-generated` 이 옵션은 숙련된 시스템 통합자가 제한된 상황에서 사용해야 합니다 *전용*. 이 옵션은 다음과 같아야 합니다 *절대 안 함* 개발 환경에서 사용합니다. 이 선택적 매개 변수를 잘못 사용하면 코드를 실행하는 동안 오류가 발생할 수 있습니다.

## 애플리케이션 설치

* [명령줄을 사용하여 설치](../advanced.md)
