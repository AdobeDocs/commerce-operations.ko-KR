---
title: 구성 파일에서 데이터 가져오기
description: 구성 파일에서 Adobe Commerce 구성 설정을 가져옵니다.
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# 구성 설정 가져오기

{{file-system-owner}}

Commerce 2.2를 사용하여 프로덕션 시스템을 설정하는 경우 [파이프라인 배포 모델](../deployment/technical-details.md), 다음을 수행해야 합니다. _가져오기_ 다음에서 구성 설정 `config.php` 및 `env.php` 을 데이터베이스에 추가합니다.
이러한 설정에는 구성 경로 및 값, 웹 사이트, 스토어, 스토어 조회수 및 테마가 포함됩니다.

웹 사이트, 스토어, 스토어 보기 및 테마를 가져온 후 제품 속성을 만들고 프로덕션 시스템의 웹 사이트, 스토어 및 스토어 보기에 적용할 수 있습니다.

>[!INFO]
>
>다음 `bin/magento app:config:import` 명령은 환경 변수에 저장된 구성을 처리하지 않습니다.

## 가져오기 명령

프로덕션 시스템에서 다음 명령을 실행하여 구성 파일에서 데이터를 가져옵니다(`config.php` 및 `env.php`)를 데이터베이스에 추가합니다.

```bash
bin/magento app:config:import [-n, --no-interaction]
```

선택 사항 사용 `[-n, --no-interaction]` 상호 작용 없이 데이터를 가져오는 플래그.

를 입력한 경우 `bin/magento app:config:import` 선택적 플래그가 없으면 변경 사항을 확인해야 합니다.

예를 들어 구성 파일에 새 웹 사이트와 새 저장소가 하나씩 포함되어 있으면 다음 메시지가 표시됩니다.

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

가져오기를 계속하려면 을(를) 입력합니다. `yes`.

배포 구성 파일에 가져올 데이터가 포함된 경우 다음과 유사한 메시지가 표시됩니다.

```terminal
Start import:
Some information about importing
```

배포 구성 파일에 가져올 데이터가 없으면 다음과 유사한 메시지가 표시됩니다.

```terminal
Start import:
Nothing to import
```

## 우리가 가져오는 것

다음 섹션에서는 가져오는 데이터에 대해 자세히 설명합니다.

### 시스템 구성

Commerce는에서 값을 직접 사용합니다. `system` 배열에서 `config.php` 또는 `env.php` 사전/사후 처리 작업이 필요하므로 파일을 데이터베이스로 가져오지 않습니다.

예: 구성 경로 값 `web/secure/base_url` 는 백엔드 모델을 사용하여 확인해야 합니다.

#### 백엔드 모델

백엔드 모델은 시스템 구성의 변경 사항을 처리하는 메커니즘입니다.
에서 백엔드 모듈을 정의합니다. `<module_name>/adminhtml/system.xml`.

모든 백엔드 모델은 [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) 클래스.

백엔드 모델을 가져올 때는 구성 값이 저장되지 않습니다.

### 웹 사이트, 스토어 및 스토어 그룹 구성

다음 유형의 구성을 가져옵니다.
(이러한 구성은 `scopes` 배열 위치 `config.php`.)

- `websites`: 웹 사이트 관련 구성
- `groups`: 관련 구성 저장
- `stores`: 보기 관련 구성 저장

위의 구성은 다음 모드로 가져올 수 있습니다.

- `create`: `config.php` 새 엔티티 포함(`websites`, `groups`, `stores`)가 프로덕션 환경에 없는 경우
- `update`: `config.php` 엔티티 포함(`websites`, `groups`, `stores`)를 조정할 수 있습니다
- `delete`: `config.php` 다음과 같음 _아님_ 엔티티 포함(`websites`, `groups`, `stores`) 프로덕션 환경에 있음

>[!INFO]
>
>스토어와 관련된 루트 카테고리는 가져오지 않습니다. Commerce 관리자를 사용하여 스토어와 루트 카테고리를 연결해야 합니다.

### 테마 구성

테마 구성에는 상거래 시스템에 등록된 모든 테마가 포함됩니다. 데이터는 `theme` 데이터베이스 테이블. (테마 구성은 `themes` 배열 위치 `config.php`.)

#### 테마 데이터 구조

배열의 핵심은 전체 테마 경로입니다. `area` + `theme path`

For example, `frontend/Magento/luma`.
`frontend` 영역 및 `Magento/luma` 테마 경로입니다.

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
>- _테마 등록_. 테마 데이터가에 정의된 경우 `config.php` 그러나 테마의 소스 코드가 파일 시스템에 없으면 테마는 무시됩니다(즉, 등록되지 않음).
>- _테마 제거_. 에 테마가 없는 경우 `config.php` 그러나 소스 코드가 파일 시스템에 있으면 테마가 제거되지 않습니다.
