---
title: 구성 값 설정
description: 구성 값을 설정하고 관리자에서 잠긴 값을 변경하는 방법을 알아봅니다.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1038'
ht-degree: 0%

---

# 구성 값 설정

{{file-system-owner}}

이 항목에서는 다음 작업에 사용할 수 있는 고급 구성 명령에 대해 설명합니다.

- 명령줄에서 구성 옵션을 설정합니다.
- 필요한 경우 관리자에서 구성 옵션의 값을 변경할 수 없도록 모든 구성 옵션을 잠급니다
- 관리자에서 잠긴 구성 옵션 변경

이러한 명령을 사용하여 수동으로 또는 스크립트를 사용하여 Commerce 구성을 설정할 수 있습니다. 해당 구성 옵션을 고유하게 식별하는 `/` 구분 문자열인 _구성 경로_&#x200B;을(를) 사용하여 구성 옵션을 설정합니다. 다음 참조에서 구성 경로를 찾을 수 있습니다.

- [중요한 시스템별 구성 경로 참조](../reference/config-reference-sens.md)
- [결제 구성 경로 참조](../reference/config-reference-payment.md)
- [일반 구성 경로 참조](../reference/config-reference-general.md)
- [Commerce Enterprise B2B 확장 구성 경로 참조](../reference/config-reference-b2b.md)

다음 시간에 값을 설정할 수 있습니다.

- Commerce을 설치하기 전에 기본 범위만 유효한 범위이므로 이 범위에 대한 구성 값을 설정할 수 있습니다.

- Commerce을 설치한 후 모든 웹 사이트 또는 스토어 보기 범위에 대한 구성 값을 설정할 수 있습니다.

다음 명령을 사용합니다.

- `bin/magento config:set`이(가) 구성 경로로 민감하지 않은 구성 값을 설정합니다.
- `bin/magento config:sensitive:set`은(는) 구성 경로로 중요한 구성 값을 설정합니다.
- `bin/magento config:show`에 저장된 구성 값이 표시됩니다. 암호화된 설정 값은 별표로 표시됩니다.

## 전제 조건

구성 값을 설정하려면 다음 중 하나 이상을 알고 있어야 합니다.

- 구성 경로
- 특정 범위에 대한 구성 값을 설정하려면 범위 코드를 알고 있어야 합니다.

  기본 범위에 대한 구성 값을 설정하려면 아무 작업도 수행하지 않아도 됩니다.

### 구성 경로 찾기

다음 참조를 참조하십시오.

- [중요한 시스템별 구성 경로 참조](../reference/config-reference-sens.md)
- [결제 구성 경로 참조](../reference/config-reference-payment.md)
- [기타 구성 경로 참조](../reference/config-reference-general.md)
- [Commerce Enterprise B2B 확장 구성 경로 참조](../reference/config-reference-b2b.md)

### 범위 코드 찾기

범위 코드는 Commerce 데이터베이스 또는 Commerce 관리자에서 찾을 수 있습니다.

**관리에서 범위 코드를 찾으려면**:

1. 웹 사이트를 보고 보기를 저장할 수 있는 사용자로 관리자에 로그인합니다.
1. **[!UICONTROL Stores]** > 설정 > **[!UICONTROL All Stores]**&#x200B;을(를) 클릭합니다.
1. 오른쪽 창에서 웹 사이트 또는 스토어 보기의 이름을 클릭하여 해당 코드를 확인합니다.

   다음 그림은 샘플 웹 사이트 코드를 보여 줍니다.

   ![관리자로부터 웹 사이트 또는 스토어 보기 코드 가져오기](../../assets/configuration/website-code.png)

1. [값 설정](#set-values)을 계속합니다.

**데이터베이스에서 범위 코드를 찾으려면**:

웹 사이트 및 스토어 보기의 범위 코드는 각각 `store_website` 및 `store` 테이블의 Commerce 데이터베이스에 저장됩니다.

1. Commerce 데이터베이스에 연결합니다.

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. 다음 명령을 입력합니다.

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   샘플 결과는 다음과 같습니다.

   ```
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   `code` 열의 값을 사용합니다.

1. 다음 섹션을 계속합니다.

## 값 설정

**시스템별 구성 값을 설정하려면**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**중요한 구성 값을 설정하려면**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

다음 표에서는 `set` 명령 매개 변수에 대해 설명합니다.

| 매개 변수 | 설명 |
| --- | --- |
| `--scope` | 구성의 범위입니다. 가능한 값은 `default`, `website` 또는 `store`입니다. 기본값은 `default`입니다. |
| `--scope-code` | 구성의 범위 코드(웹 사이트 코드 또는 스토어 보기 코드) |
| `-e or --lock-env` | 관리자 권한에서 편집할 수 없도록 값을 잠그거나 관리자 권한에서 이미 잠긴 설정을 변경합니다. 이 명령은 값을 `<Commerce base dir>/app/etc/env.php` 파일에 씁니다. |
| `-c or --lock-config` | 관리자 권한에서 편집할 수 없도록 값을 잠그거나 관리자 권한에서 이미 잠긴 설정을 변경합니다. 이 명령은 값을 `<Commerce base dir>/app/etc/config.php` 파일에 씁니다. 두 옵션을 모두 지정하면 `--lock-config` 옵션이 `--lock-env`을(를) 덮어씁니다. |
| `path` | _필수_. 구성 경로 |
| `value` | _필수_. 구성의 값 |

>[!INFO]
>
>Commerce 2.2.4부터 `--lock-env` 및 `--lock-config` 옵션이 `--lock` 옵션을 대체합니다.
>
>`--lock-env` 또는 `--lock-config` 옵션을 사용하여 값을 설정하거나 변경하는 경우 Admin 또는 Storefront에 액세스하기 전에 [`bin/magento app:config:import` 명령](../cli/import-configuration.md)을(를) 사용하여 설정을 가져와야 합니다.

잘못된 구성 경로를 입력하면 이 명령은 오류를 반환합니다

```text
The "wrong/config/path" does not exist
```

자세한 내용은 다음 섹션 중 하나를 참조하십시오.

- [관리자에서 편집할 수 있는 구성 값 설정](#set-configuration-values-that-can-be-edited-in-the-admin)
- [관리자에서 편집할 수 없는 구성 값 설정](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### 관리자에서 편집할 수 있는 구성 값 설정

`bin/magento config:set` _없이_ `--lock-env` 또는 `--lock-config`을(를) 사용하여 데이터베이스에 값을 씁니다. 이 방법으로 설정한 값은 관리자에서 편집할 수 있습니다.

스토어 기본 URL을 설정하는 몇 가지 예는 다음과 같습니다.

기본 범위의 기본 URL을 설정합니다.

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

`base` 웹 사이트의 기본 URL 설정:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

`test` 저장소 보기의 기본 URL을 설정합니다.

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### 관리자에서 편집할 수 없는 구성 값 설정

다음과 같이 `--lock-env` 옵션을 사용하는 경우 명령은 구성 값을 `<Commerce base dir>/app/etc/env.php`에 저장하고 이 값을 편집하는 필드를 관리자에서 사용할 수 없게 합니다.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Commerce이 설치되어 있지 않은 경우 `--lock-env` 옵션을 사용하여 구성 값을 설정할 수 있습니다. 그러나 기본 범위에 대한 값만 설정할 수 있습니다.

>[!INFO]
>
>`env.php` 파일은 시스템별로 다릅니다. 다른 시스템으로 전송하면 안 됩니다. 이 옵션을 사용하여 데이터베이스의 구성 값을 덮어쓸 수 있습니다. 예를들어 다른 시스템에서 데이터베이스 덤프를 가져와서 `base_url` 및 다른 값을 덮어쓰면 데이터베이스를 수정할 필요가 없습니다.

다음과 같이 `--lock-config` 옵션을 사용하면 구성 값이 `<Commerce base dir>/app/etc/config.php`에 저장됩니다. 관리자에서 이 값을 편집하기 위한 필드가 비활성화됩니다.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Commerce이 설치되어 있지 않은 경우 `--lock-config`을(를) 사용하여 구성 값을 설정할 수 있습니다. 그러나 기본 범위에 대한 값만 설정할 수 있습니다.

>[!INFO]
>
>동일한 구성 값을 사용하도록 다른 시스템에 `config.php`을(를) 전송할 수 있습니다. 예를 들어 테스트 시스템이 있는 경우 동일한 `config.php`을(를) 사용하면 동일한 구성 값을 다시 설정할 필요가 없습니다.

## 구성 설정 값 표시

명령 옵션:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

위치

- `--scope`은(는) 구성 범위입니다(기본값, 웹 사이트, 스토어). 기본값은 `default`입니다.
- `--scope-code`은(는) 구성의 범위 코드(웹 사이트 코드 또는 스토어 보기 코드)입니다.
- `path`은(는) first_part/second_part/third_part/etc 형식의 구성 경로입니다(_필수_).

>[!INFO]
>
>`bin/magento config:show` 명령은 [암호화된 값](../reference/config-reference-sens.md)의 값을 일련의 별표로 표시합니다. `**&#x200B;**&#x200B;**`.

### 예시

**저장된 구성을 모두 표시하려면**:

```bash
bin/magento config:show
```

결과:

```
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**`base` 웹 사이트에 대해 저장된 모든 구성을 표시하려면**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

결과:

```
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**기본 범위의 기본 URL을 표시하려면**:

```bash
bin/magento config:show web/unsecure/base_url
```

결과:

```
web/unsecure/base_url - http://example.com/
```

**`base` 웹 사이트의 기본 URL을 표시하려면**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

결과:

```
web/unsecure/base_url - http://example-for-website.com/
```

**`default` 저장소의 기본 URL을 표시하려면**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

결과:

```
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>범위 코드에는 문자(a-z 또는 A-Z), 숫자(0-9) 및 밑줄(_)만 포함될 수 있습니다. 또한 첫 번째 문자는 문자여야 합니다. 웹 사이트 또는 스토어 보기를 만들 때 대문자 또는 대소문자를 사용하는 경우, 환경 변수를 통해 구성 설정을 재정의할 수 있도록 내부적으로 일치는 대소문자를 구분하지 않습니다. [환경 변수를 사용하여 구성 설정을 재정의](../reference/override-config-settings.md#environment-variables)를 참조하십시오.

