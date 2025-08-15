---
title: 관리자 계정 만들기, 편집 또는 잠금 해제
description: Adobe Commerce 관리 애플리케이션의 관리자 계정을 관리하려면 다음 단계를 따르십시오.
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 관리자 계정 만들기, 편집 또는 잠금 해제

이 명령을 사용하려면 먼저 다음을 수행해야 합니다.

- [배포 구성 만들기](deployment.md)
- [최소 Magento_Authorization 및 Magento_User 모듈 활성화](manage-modules.md)
- 데이터베이스 스키마 만들기

>[!NOTE]
>
>데이터베이스를 만드는 가장 간단한 방법은 `magento setup:upgrade` 명령을 사용하는 것입니다.

## 관리자 만들기 또는 편집

이 명령을 사용하여 관리자를 생성하거나 기존 관리자를 편집합니다.

>[!NOTE]
>
>관리자를 편집하는 경우 `first name`, `last name` 및 `password`만 편집할 수 있습니다.

명령 사용:

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

여기서 다음 표는 매개 변수와 값을 정의합니다.

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--admin-firstname` | 관리자 사용자의 이름입니다. | 예 |
| `--admin-lastname` | 관리자 사용자의 성. | 예 |
| `--admin-email` | 관리자 사용자의 이메일 주소입니다. | 예 |
| `--admin-user` | 관리자 사용자 이름. | 예 |
| `--admin-password` | 관리자 사용자 암호입니다. 암호는 길이가 7자 이상이어야 하며 최소 하나의 영문자와 최소 하나의 숫자를 포함해야 합니다. <br><br>보다 길고 복잡한 암호를 사용하는 것이 좋습니다. 암호 문자열에 리터럴 해석이 필요한 특수 문자(예: 백슬래시 또는 공백)가 포함된 경우 암호를 작은 따옴표로 묶습니다. | 예 |
| `--magento-init-params` | 응용 프로그램 초기화 매개 변수를 사용자 지정하는 명령에 추가하십시오.<br/><br/>예: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 아니요 |

사용의 예:

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```
Created Magento administrator user named j.doe
```

필요한 매개 변수를 지정하지 않으면 애플리케이션이 CLI에서 매개 변수에 대해 묻습니다.

```bash
bin/magento admin:user:create
```

```
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```
Created Magento administrator user named John
```

다음 예제는 `first name` 관리 사용자의 `last name`, `password` 및 `j.doe`을(를) 업데이트합니다.

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```
Created Magento administrator user named j.doe
```

## 관리자 계정 잠금 해제

이 명령을 사용하면 일반적으로 여러 번 잘못된 로그인을 시도하여 잠긴 관리자의 계정을 잠금 해제할 수 있습니다.

```bash
bin/magento admin:user:unlock {username}
```

관리자의 사용자 이름을 지정해야 합니다. 예:

```bash
bin/magento admin:user:unlock admin
```

```
The user account "admin" has been unlocked
```

계정이 잠금 해제되지 않았거나 문제가 있는 경우 다음 메시지가 표시됩니다.

```
The user account "admin" was not locked or could not be unlocked
```

사용자가 관리자이고, 사용자가 활성 상태이며, 계정이 잠겨 있는지 확인합니다. 관리자의 잠긴 사용자 목록을 보려면 관리자로 로그인하고 **시스템** > **권한** > **잠긴 사용자**&#x200B;를 클릭하십시오.

계정이 존재하지 않으면 다음 메시지가 표시됩니다.

```
Couldn't find the user account "bob"
```
