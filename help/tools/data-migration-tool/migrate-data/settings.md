---
title: 데이터 마이그레이션 설정
description: 설정을 을 사용하여 Magento 1에서 Magento 2으로 마이그레이션하는 방법을 배웁니다. [!DNL Data Migration Tool].
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---


# 데이터 마이그레이션 설정

다음 `Settings` 모드는 배송, 결제 및 세금 설정과 같은 저장소, 웹 사이트 및 시스템 구성을 마이그레이션합니다. 데이터 마이그레이션에 따라 [주문](overview.md#migration-order)를 설정하는 경우 먼저 설정을 마이그레이션해야 합니다.

시작하기 전에 다음 단계를 수행하여 준비하십시오.

1. 애플리케이션 서버에 다음 형식으로 로그인합니다. [파일 시스템 소유자](../../../installation/prerequisites/file-system/overview.md).

1. 로 변경 `/bin` 디렉토리 또는 시스템에 추가되었는지 확인합니다. `PATH`.

>[!NOTE]
>
>Magento 2이 다음 위치에 배포되어 있는지 확인합니다. `default` 모드. 개발자 모드로 인해 마이그레이션 도구에서 유효성 검사 오류가 발생할 수 있습니다.


자세한 내용은 [첫 단계](overview.md#first-steps) 섹션을 참조하십시오.

## 설정 마이그레이션 명령 실행

설정 마이그레이션을 시작하려면 다음을 실행하십시오.

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

위치:

* `[-r|--reset]` 는 처음부터 마이그레이션을 시작하는 선택적 인수입니다. 이 인수를 사용하여 마이그레이션을 테스트할 수 있습니다

* `[-a|--auto]` 무결성 검사 오류가 발생할 때 마이그레이션이 중지되지 않도록 하는 선택적 인수입니다.

* `{<path to config.xml>}` 마이그레이션 도구의 절대 파일 시스템 경로입니다. [`config.xml`](../configure.md#configure-migration-in-vendor-folder) 파일; 이 인수는 필수입니다.

>[!NOTE]
>
>이 명령은 일부 구성 설정을 마이그레이션하지 않습니다. 계속하기 전에 Magento 2 관리자의 모든 설정을 확인하십시오.


다음 `Migration completed` 설정이 성공적으로 전송되면 메시지가 표시됩니다.

## 사용자 지정 마이그레이션 규칙 구성

설정을 마이그레이션할 때 시스템 구성을 무시하거나 이름을 바꾸거나 변경할 수 있습니다. 이를 위해 `settings.xml` 파일.

1. 애플리케이션 서버에 로그인하거나 [파일 시스템 소유자](../../../installation/prerequisites/file-system/overview.md).

1. 다음 디렉토리로 변경합니다.

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   예를 들어 애플리케이션이 `/var/www/html`, `settings.xml.dist` 파일이 다음 디렉터리 중 하나에 있습니다.

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. 을(를) 만들려면 `settings.xml` 제공된 샘플에서 파일을 실행하십시오.

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. 에서 변경 `settings.xml`.

1. 매핑을 위한 설정 파일의 새 이름을 지정하려면 `<settings_map_file>` 태그를에서 지정합니다. `path/to/config.xml` 파일.

자세한 내용은 [설정 마이그레이션 모드](../technical-specification.md#settings-migration-mode) 도구 섹션의 [사양](../technical-specification.md).

## 다음 마이그레이션 단계

* [데이터 마이그레이션](data.md)
