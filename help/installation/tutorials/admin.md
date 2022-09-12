---
title: 관리자 계정 만들기, 편집 또는 잠금 해제
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source 관리 애플리케이션의 관리자 계정을 관리합니다.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---


# 관리자 계정 만들기, 편집 또는 잠금 해제

이 명령을 사용하려면 먼저 다음을 수행해야 합니다.

- [배포 구성 만들기](deployment.md)
- [최소한 Magento_Authorization 및 Magento_User 모듈을 사용합니다](manage-modules.md)
- 만들기 [데이터베이스 스키마](https://glossary.magento.com/database-schema)

>[!NOTE]
>
>데이터베이스를 만드는 가장 간단한 방법은 명령을 사용하는 것입니다 `magento setup:upgrade`.

## 관리자 만들기 또는 편집

이 명령을 사용하여 관리자를 만들거나 기존 관리자를 편집합니다.

>[!NOTE]
>
>관리자를 편집하는 경우 `first name`, `last name`, 및 `password` 편집할 수 있습니다.

명령 사용:

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

여기서 다음 표에서 매개 변수와 값을 정의합니다.

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--admin-firstname` | 관리자 사용자의 이름입니다. | 예 |
| `--admin-lastname` | 관리자 사용자의 성입니다. | 예 |
| `--admin-email` | 관리자 사용자의 전자 메일 주소입니다. | 예 |
| `--admin-user` | 관리자 사용자 이름. | 예 |
| `--admin-password` | 관리자 사용자 암호입니다. 암호는 길이가 7자 이상이어야 하며 하나 이상의 영문자와 하나 이상의 숫자 문자를 포함해야 합니다. <br><br>더 길고 복잡한 암호를 사용하는 것이 좋습니다. 암호 문자열에 리터럴 해석(예: 백슬래시 또는 공백)이 필요한 특수 문자가 포함되어 있는 경우, 암호를 단일 인용으로 묶습니다. | 예 |
| `--magento-init-params` | 명령에 추가하여 응용 프로그램 초기화 매개변수를 사용자 정의합니다.<br/><br/>예: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 아니요 |

사용 예:

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```terminal
Created Magento administrator user named j.doe
```

필요한 매개 변수를 지정하지 않으면 CLI에서 해당 매개 변수에 대해 묻습니다.

```bash
bin/magento admin:user:create
```

```terminal
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```terminal
Created Magento administrator user named John
```

다음 예제 업데이트 `first name`, `last name`, 및 `password` 의 `j.doe` 관리자:

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```terminal
Created Magento administrator user named j.doe
```

## 관리자 계정 잠금 해제

일반적으로 여러 번 잘못된 로그인을 시도하여 잠긴 관리자의 계정을 잠금 해제하려면 이 명령을 사용합니다.

```bash
bin/magento admin:user:unlock {username}
```

관리자의 사용자 이름을 지정해야 합니다. 예:

```bash
bin/magento admin:user:unlock admin
```

```terminal
The user account "admin" has been unlocked
```

계정의 잠금이 해제되지 않았거나 문제가 있는 경우 다음 메시지가 표시됩니다.

```terminal
The user account "admin" was not locked or could not be unlocked
```

사용자가 관리자이고, 사용자가 활성 상태이며, 계정이 잠겨 있는지 확인합니다. 관리자에서 잠긴 사용자 목록을 보려면 관리자로 로그인하고 **시스템** > **권한** > **잠긴 사용자**.

계정이 없으면 다음 메시지가 표시됩니다.

```terminal
Couldn't find the user account "bob"
```
