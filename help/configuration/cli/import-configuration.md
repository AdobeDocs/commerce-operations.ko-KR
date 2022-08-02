---
title: 구성 파일에서 데이터 가져오기
description: 구성 파일에서 Adobe Commerce 구성 설정을 가져옵니다.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---


# 구성 설정 가져오기

{{file-system-owner}}

Commerce 2.2를 사용하여 프로덕션 시스템을 설정하는 경우 [파이프라인 배포 모델](../deployment/technical-details.md): _가져오기_ 구성 설정 `config.php` 및 `env.php` 데이터베이스에 추가합니다.
이러한 설정에는 구성 경로 및 값, 웹 사이트, 저장소, 보기 및 테마가 포함됩니다.

웹 사이트, 저장, 보기 및 테마를 가져온 후에는 제품 속성을 만들고 제품 속성을 프로덕션 시스템의 웹 사이트, 저장소 및 저장소 보기에 적용할 수 있습니다.

>[!INFO]
>
>다음 `bin/magento app:config:import` 명령은 환경 변수에 저장된 구성을 처리하지 않습니다.

## 가져오기 명령

프로덕션 시스템에서 다음 명령을 실행하여 구성 파일에서 데이터를 가져옵니다(`config.php` 및 `env.php`) 를 데이터베이스에 추가합니다.

```bash
bin/magento app:config:import [-n, --no-interaction]
```

선택 사항 사용 `[-n, --no-interaction]` 상호 작용 없이 데이터를 가져올 플래그입니다.

을 입력하면 `bin/magento app:config:import` 선택적 플래그가 없으면 변경 사항을 확인해야 합니다.

예를 들어 구성 파일에 하나의 새 웹 사이트와 하나의 새 저장소가 포함된 경우 다음 메시지가 표시됩니다.

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

가져오기를 계속하려면 를 입력합니다. `yes`.

배포 구성 파일에 가져올 데이터가 있으면 다음과 유사한 메시지가 표시됩니다.

```terminal
Start import:
Some information about importing
```

배포 구성 파일에 가져올 데이터가 없으면 다음과 유사한 메시지가 표시됩니다.

```terminal
Start import:
Nothing to import
```

## 가져오는 내용

다음 섹션에서는 가져오는 데이터에 대해 자세히 설명합니다.

### 시스템 구성

상거래 코드에서는 `system` 의 배열 `config.php` 또는 `env.php` 파일을 데이터베이스로 가져오는 대신 이전 및 사후 처리 작업이 필요하므로 파일을 가져옵니다.

예를 들어, 구성 경로의 값 `web/secure/base_url` 다음 방법으로 유효성을 검사해야 함 [백엔드](https://glossary.magento.com/backend) 모델.

#### 백엔드 모델

백엔드 모델은 시스템 구성에서 변경 사항을 처리하는 메커니즘입니다.
에서 백엔드 모듈을 정의합니다 `<module_name>/adminhtml/system.xml`.

모든 백엔드 모델은 [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) 클래스 이름을 지정합니다.

백엔드 모델을 가져올 때 구성 값을 저장하지 않습니다.

### 웹 사이트, 저장소 및 저장소 그룹 구성

다음 유형의 구성을 가져옵니다.
(이러한 구성은 `scopes` 의 배열 `config.php`)

- `websites`: 웹 사이트 관련 구성
- `groups`: 관련 구성 저장
- `stores`: 보기 관련 구성 저장

이전 구성은 다음 모드로 가져올 수 있습니다.

- `create`: `config.php` 새 엔터티 포함(`websites`, `groups`, `stores`)
- `update`: `config.php` 포함 엔티티(`websites`, `groups`, `stores`)
- `delete`: `config.php` does _not_ 엔티티 포함(`websites`, `groups`, `stores`)

>[!INFO]
>
>루트는 가져오지 않습니다 [카테고리](https://glossary.magento.com/category) 와(과) 관련이 있습니다. 상거래를 사용하여 루트 카테고리를 스토어에 연결해야 합니다 [관리](https://glossary.magento.com/admin).

### 테마 구성

테마 구성에는 상거래 시스템에 등록된 모든 테마가 포함되어 있습니다. 데이터는 `theme` 데이터베이스 테이블. (테마 구성은 `themes` 의 배열 `config.php`)

#### 테마 데이터 구조

배열의 키는 전체 테마 경로입니다. `area` + `theme path`

For example, `frontend/Magento/luma`.
`frontend` 는 영역이며 `Magento/luma` is [테마](https://glossary.magento.com/theme) 경로.

배열 값은 테마에 대한 데이터입니다. 코드, 제목, 경로, 상위 id

전체 예:

```php?start_inline=1
'frontend/Magento/luma' =>
   array (
      'parent_id' => 'Magento/blank',
      'theme_path' => 'Magento/luma',
      'theme_title' => 'Magento Luma',
      'is_featured' => '0',
      'area' => 'frontend',
      'type' => '0',
      'code' => 'Magento/luma',
),
```

>[!INFO]
>
>- _테마 등록_. 테마 데이터가 `config.php` 그러나 테마의 소스 코드가 파일 시스템에 없으면 테마가 무시됩니다(즉, 등록되지 않음).
>- _테마 제거_. 테마가 `config.php` 그러나 소스 코드가 파일 시스템에 있으면 테마는 제거되지 않습니다.

