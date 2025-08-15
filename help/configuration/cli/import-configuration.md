---
title: 구성 파일에서 데이터 가져오기
description: 구성 파일에서 Adobe Commerce 구성 설정을 가져옵니다.
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# 구성 설정 가져오기

{{file-system-owner}}

Commerce 2.2 [파이프라인 배포 모델](../deployment/technical-details.md)을 사용하여 프로덕션 시스템을 설정하는 경우 _및_&#x200B;에서 데이터베이스로 구성 설정을 `config.php`가져오기`env.php`해야 합니다.
이러한 설정에는 구성 경로 및 값, 웹 사이트, 스토어, 스토어 조회수 및 테마가 포함됩니다.

웹 사이트, 스토어, 스토어 보기 및 테마를 가져온 후 제품 속성을 만들고 프로덕션 시스템의 웹 사이트, 스토어 및 스토어 보기에 적용할 수 있습니다.

>[!INFO]
>
>`bin/magento app:config:import` 명령은 환경 변수에 저장된 구성을 처리하지 않습니다.

## 가져오기 명령

프로덕션 시스템에서 다음 명령을 실행하여 구성 파일(`config.php` 및 `env.php`)에서 데이터베이스로 데이터를 가져옵니다.

```bash
bin/magento app:config:import [-n, --no-interaction]
```

선택적 `[-n, --no-interaction]` 플래그를 사용하여 상호 작용 없이 데이터를 가져옵니다.

선택적 플래그 없이 `bin/magento app:config:import`을(를) 입력하면 변경 내용을 확인해야 합니다.

예를 들어 구성 파일에 새 웹 사이트와 새 저장소가 하나씩 포함되어 있으면 다음 메시지가 표시됩니다.

```
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

가져오기를 계속하려면 `yes`을(를) 입력하십시오.

배포 구성 파일에 가져올 데이터가 포함된 경우 다음과 유사한 메시지가 표시됩니다.

```
Start import:
Some information about importing
```

배포 구성 파일에 가져올 데이터가 없으면 다음과 유사한 메시지가 표시됩니다.

```
Start import:
Nothing to import
```

## 우리가 가져오는 것

다음 섹션에서는 가져오는 데이터에 대해 자세히 설명합니다.

### 시스템 구성

Commerce에서는 사전 및 사후 처리 작업이 필요하므로 `system` 또는 `config.php` 파일에서 `env.php` 배열의 값을 데이터베이스로 가져오지 않고 직접 사용합니다.

예를 들어 백엔드 모델을 사용하여 구성 경로 `web/secure/base_url`의 값을 확인해야 합니다.

#### 백엔드 모델

백엔드 모델은 시스템 구성의 변경 사항을 처리하는 메커니즘입니다.
`<module_name>/adminhtml/system.xml`에서 백 엔드 모듈을 정의합니다.

모든 백 엔드 모델은 [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) 클래스를 확장해야 합니다.

백엔드 모델을 가져올 때는 구성 값이 저장되지 않습니다.

### 웹 사이트, 스토어 및 스토어 그룹 구성

다음 유형의 구성을 가져옵니다.
(이러한 구성은 `scopes`의 `config.php` 배열 아래에 있습니다.)

- `websites`: 웹 사이트 관련 구성
- `groups`: 관련 구성을 저장합니다.
- `stores`: 저장소 보기 관련 구성

위의 구성은 다음 모드로 가져올 수 있습니다.

- `create`: `config.php`에 프로덕션 환경에 없는 새 엔터티(`websites`, `groups`, `stores`)가 있습니다.
- `update`: `config.php`에 프로덕션 환경과 다른 엔터티(`websites`, `groups`, `stores`)가 있습니다.
- `delete`: `config.php`은(는) 프로덕션 환경에 있는 엔터티(_,_, `websites`)를 `groups`포함하지 않습니다`stores`

>[!INFO]
>
>스토어와 관련된 루트 카테고리는 가져오지 않습니다. Commerce 관리를 사용하여 루트 카테고리를 스토어와 연결해야 합니다.

### 테마 구성

테마 구성에는 Commerce 시스템에 등록된 모든 테마가 포함됩니다. 데이터는 `theme` 데이터베이스 테이블에서 직접 가져옵니다. (테마 구성이 `themes`의 `config.php` 배열에 있습니다.)

#### 테마 데이터 구조

배열의 키는 전체 테마 경로입니다. `area` + `theme path`

예: `frontend/Magento/luma`.
`frontend`은(는) 영역이고 `Magento/luma`은(는) 테마 경로입니다.

배열의 값은 코드, 제목, 경로, 상위 ID 등 테마에 대한 데이터입니다.

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
>- _테마 등록_. 테마 데이터가 `config.php`에 정의되어 있지만 테마의 소스 코드가 파일 시스템에 없으면 테마가 무시됩니다(즉, 등록되지 않음).
>- _테마 제거_. 테마가 `config.php`에 없지만 소스 코드가 파일 시스템에 있으면 테마가 제거되지 않습니다.
