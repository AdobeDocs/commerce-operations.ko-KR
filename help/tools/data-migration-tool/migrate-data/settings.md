---
title: 데이터 마이그레이션 설정
description: ' [!DNL Data Migration Tool]을(를) 사용하여 Magento 1에서 Magento 2로 설정을 마이그레이션하는 방법을 알아봅니다.'
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 데이터 마이그레이션 설정

`Settings` 모드는 상점, 웹 사이트 및 배송, 결제 및 세금 설정과 같은 시스템 구성을 마이그레이션합니다. 데이터 마이그레이션 [순서](overview.md#migration-order)에 따라 먼저 설정을 마이그레이션해야 합니다.

시작하기 전에 다음 단계를 수행하여 준비하십시오.

1. 응용 프로그램 서버에 [파일 시스템 소유자](../../../installation/prerequisites/file-system/overview.md)(으)로 로그인합니다.

1. `/bin` 디렉터리로 변경하거나 시스템 `PATH`에 추가되었는지 확인하십시오.

>[!NOTE]
>
>Magento 2가 `default` 모드로 배포되었는지 확인하십시오. 개발자 모드에서는 마이그레이션 도구에서 유효성 검사 오류가 발생할 수 있습니다.


자세한 내용은 [첫 번째 단계](overview.md#first-steps) 섹션을 참조하십시오.

## settings migration 명령 실행

설정 마이그레이션을 시작하려면 다음을 실행합니다.

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

위치:

* `[-r|--reset]`은(는) 처음부터 마이그레이션을 시작하는 선택적 인수입니다. 이 인수를 사용하여 마이그레이션을 테스트할 수 있습니다

* `[-a|--auto]`은(는) 무결성 검사 오류가 발생할 때 마이그레이션이 중지되지 않도록 하는 선택적 인수입니다.

* `{<path to config.xml>}`은(는) 마이그레이션 도구의 [`config.xml`](../configure.md#configure-migration-in-vendor-folder) 파일에 대한 절대 파일 시스템 경로입니다. 이 인수는 필수입니다.

>[!NOTE]
>
>이 명령은 모든 구성 설정을 마이그레이션하지 않습니다. 계속하기 전에 Magento 2 관리자의 모든 설정을 확인하십시오.


설정이 성공적으로 전송되면 `Migration completed` 메시지가 표시됩니다.

## 사용자 정의 마이그레이션 규칙 구성

설정을 마이그레이션할 때 시스템 구성을 무시하거나 이름을 바꾸거나 변경할 수 있습니다. 이를 위해 `settings.xml` 파일에 사용자 지정 규칙을 지정하십시오.

1. [파일 시스템 소유자](../../../installation/prerequisites/file-system/overview.md)(으)로 응용 프로그램 서버에 로그인하거나 응용 프로그램 서버로 전환합니다.

1. 다음 디렉토리로 변경합니다.

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   예를들어 응용 프로그램이 `/var/www/html`에 설치된 경우 `settings.xml.dist` 파일은 다음 디렉터리 중 하나에 있습니다.

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. 제공된 샘플에서 `settings.xml` 파일을 만들려면 다음을 실행하십시오.

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. `settings.xml`에서 변경합니다.

1. 매핑할 설정 파일의 새 이름을 지정하려면 `path/to/config.xml` 파일에서 `<settings_map_file>` 태그를 변경하십시오.

자세한 내용은 도구 [사양](../technical-specification.md)의 [설정 마이그레이션 모드](../technical-specification.md#settings-migration-mode) 섹션을 참조하십시오.

## 다음 마이그레이션 단계

* [데이터 마이그레이션](data.md)
