---
title: 구성 설정 내보내기
description: Adobe Commerce 구성 설정을 구성 파일(구성 덤프라고도 함)로 내보냅니다.
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# 구성 설정 내보내기

Commerce 2.2 이상 [파이프라인 배포 모델](../deployment/technical-details.md)에서는 시스템 간에 일관된 구성을 유지할 수 있습니다. 개발 시스템의 관리에서 설정을 구성한 후 다음 명령을 사용하여 이러한 설정을 구성 파일로 내보냅니다.

```bash
bin/magento app:config:dump {config-types}
```

_config_types_&#x200B;은(는) 덤프할 구성 형식의 공백으로 구분된 목록입니다. 사용 가능한 형식에는 `scopes`, `system`, `themes` 및 `i18n`이(가) 있습니다. 구성 유형을 지정하지 않으면 명령은 모든 시스템 구성 정보를 덤프합니다.

다음 예제에서는 범위 및 테마만 덤프합니다.

```bash
bin/magento app:config:dump scopes themes
```

명령 실행 결과 다음 구성 파일이 업데이트됩니다.

- `app/etc/config.php`

  모든 Commerce 인스턴스에 대한 공유 구성 파일입니다.
소스 제어에 포함시켜 개발, 빌드 및 프로덕션 시스템 간에 공유할 수 있도록 합니다.

  [config.php 참조](../reference/config-reference-configphp.md)를 참조하십시오.

- `app/etc/env.php`

  이는 환경별 구성 파일입니다.
여기에는 개별 환경에 대한 민감하고 시스템별 설정이 포함되어 있습니다.

  이 파일을 소스 제어에 포함시키지 _마십시오_.

  [env.php 참조](../reference/config-reference-envphp.md)를 참조하십시오.

## 중요 또는 시스템별 설정

`env.php`에 기록된 중요한 설정을 설정하려면 [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) 명령을 사용하십시오.

구성 값은 모듈의 [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) 파일에서 [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific)을(를) 참조하여 중요하거나 시스템별로 지정됩니다.

`config_types`을(를) 사용할 때 추가 시스템 설정을 내보내려면 [`bin/magento config:set`](set-configuration-values.md#set-values) 명령을 사용하는 것이 좋습니다.
