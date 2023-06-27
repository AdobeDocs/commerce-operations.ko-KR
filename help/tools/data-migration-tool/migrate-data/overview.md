---
title: 마이그레이션 개요
description: 를 사용하여 Magento 1에서 Magento 2로 데이터 마이그레이션을 시작하는 방법에 대해 알아봅니다. [!DNL Data Migration Tool].
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# 마이그레이션 개요

마이그레이션을 시작하기 전에 모든 Magento 1 cron 작업을 중지하십시오.

마이그레이션 프로세스 중에 성공적인 마이그레이션을 위해 다음 일반 규칙을 따르십시오.

1. **금지** order management(운송, 송장 생성 및 대변 메모)를 제외하고 Magento 1 관리자를 변경합니다.
1. **금지** 모든 코드 변경
1. **금지** Magento 2 관리자 및 상점 첫 화면에서 변경

>[!TIP]
>
>Magento 1 상점 내 모든 작업이 허용됩니다.

## 실행 [!DNL Data Migration Tool]

이 섹션에서는 다음을 실행하는 방법을 보여줍니다. [!DNL Data Migration Tool] 설정, 데이터 또는 증분 변경 사항을 마이그레이션하기 위해.

### 첫 단계

1. 파일 시스템에 쓸 수 있는 권한이 있는 사용자로 애플리케이션 서버에 로그인하거나 이 사용자로 전환합니다. 다음을 참조하십시오 [파일 시스템 소유자로 전환](../../../installation/prerequisites/file-system/overview.md).

   bash 셸을 사용하는 경우 다음 구문을 사용하여 파일 시스템 소유자로 전환하고 동시에 명령을 입력할 수 있습니다.

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   파일 시스템 소유자가 로그인을 허용하지 않는 경우 다음을 수행할 수 있습니다.

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 디렉토리에서 Magento 명령을 실행하려면 `<magento_root>/bin` 내 시스템으로 `PATH`.

   셸의 구문이 다르므로 다음과 같은 참조를 참조하십시오 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   CentOS용 샘플 bash 쉘:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   필요한 경우 다음과 같은 방법으로 명령을 실행할 수 있습니다.

   - `cd <magento_root>/bin` 다음 계정으로 실행 `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` 는 웹 서버 docroot의 하위 디렉토리입니다.

### 명령 구문

다음은 일반적인 명령 예입니다.

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

위치:

- `<mode>` 다음과 같을 수 있습니다. [`settings`](settings.md), [`data`](data.md), 또는 [`delta`](delta.md)
- `[-r|--reset]` 는 처음부터 마이그레이션을 시작하는 선택적 인수입니다. 이 인수는 마이그레이션 테스트에 사용할 수 있습니다.
- `[-a|--auto]` 는 무결성 검사 오류가 발생할 때 마이그레이션이 중지되지 않도록 하는 선택적 인수입니다.
- `{<path to config.xml>}` 는 의 절대 파일 시스템 경로입니다. `config.xml`; 이 인수는 필수입니다.

>[!NOTE]
>
>로그가 다음에 작성됨 `<magento_root>/var/` 디렉토리.


## 마이그레이션 순서

만든 시간 [!DNL Data Migration Tool], 다음과 같은 데이터 전송 시퀀스를 가정합니다.

1. [설정](settings.md)
1. [데이터](data.md)
1. [변경 사항](delta.md)

동일한 순서로 데이터를 마이그레이션하는 것이 좋습니다.
