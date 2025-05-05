---
title: 온프레미스 설치 빠른 시작
description: 소유한 인프라에 Adobe Commerce을 설치하려면 다음 단계를 따르십시오.
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: 60db3da9154e76032c88d687b6b6e22d7b81f9ae
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 0%

---

# 온프레미스 설치 빠른 시작

이 페이지의 지침에서는 자체 호스팅 인프라에 Adobe Commerce을 설치하는 방법을 설명합니다. 기존 설치 업그레이드에 대한 지침은 [_업그레이드 안내서_](../upgrade/overview.md)&#x200B;를 참조하십시오.

Adobe은 [작성기](https://getcomposer.org/)를 사용하여 Adobe Commerce 구성 요소와 해당 종속성을 관리합니다. Composer를 사용하여 Adobe Commerce 메타패키지를 가져오면 다음과 같은 이점이 있습니다.

- 소스 코드로 번들로 묶지 않고 타사 라이브러리 재사용
- 강력한 종속성 관리 기능을 갖춘 구성 요소 기반 아키텍처를 사용하여 확장 충돌 및 호환성 문제 감소
- [PHP-Framework 상호 운용성 그룹(FIG)](https://www.php-fig.org/) 표준 준수
- 다른 구성 요소로 Magento Open Source 다시 패키지
- 프로덕션 환경에서 Adobe Commerce 소프트웨어 사용

>[!NOTE]
>
>Magento Open Source에 기여하는 개발자는 [git 기반](https://developer.adobe.com/commerce/contributor/guides/install/) 설치 방법을 사용해야 합니다.

## 전제 조건

계속하기 전에 다음을 수행해야 합니다.

- [필수 구성 요소 작업](system-requirements.md)을 모두 완료하십시오.
- [작성기 설치](https://getcomposer.org/download/).
- Adobe Commerce 작성기 저장소에 [인증 키](prerequisites/authentication-keys.md)를 가져옵니다.

## 파일 시스템 소유자로 로그인

[소유권 및 권한 개요](prerequisites/file-system/overview.md)에서 소유권, 권한 및 파일 시스템 소유자에 대해 알아봅니다.

파일 시스템 소유자로 전환하려면 다음을 수행하십시오.

1. 파일 시스템에 쓸 수 있는 권한이 있는 사용자로 애플리케이션 서버에 로그인하거나 이 사용자로 전환합니다.

   bash 셸을 사용하는 경우 다음 구문을 사용하여 파일 시스템 소유자로 전환하고 동시에 명령을 입력할 수 있습니다.

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   파일 시스템 소유자가 로그인을 허용하지 않는 경우 다음을 수행할 수 있습니다.

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 모든 디렉터리에서 CLI 명령을 실행하려면 `<app_root>/bin`을(를) 시스템 `PATH`에 추가하십시오.

   셸에 다른 구문이 있으므로 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables)과 같은 참조를 참조하십시오.

   CentOS용 샘플 bash 쉘:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   필요한 경우 다음과 같은 방법으로 명령을 실행할 수 있습니다.

   - `cd <app_root>/bin` 및 `./magento <command name>`(으)로 실행
   - `app_root>/bin/magento <command name>`
   - `<app_root>`은(는) 웹 서버 docroot의 하위 디렉터리입니다.

## 메타패키지 가져오기

Adobe Commerce 메타패키지를 가져오려면 다음을 수행하십시오.

1. 응용 프로그램 서버에 [파일 시스템 소유자](prerequisites/file-system/overview.md)(으)로 로그인하거나 응용 프로그램 서버로 전환합니다.
1. 웹 서버 docroot 디렉토리 또는 가상 호스트 docroot로 구성한 디렉토리로 변경합니다.
1. Commerce 메타패키지를 사용하여 작성기 프로젝트를 만듭니다.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   메시지가 표시되면 인증 키를 입력합니다. 공개 및 개인 키는 [Commerce Marketplace - 액세스 키](https://commercemarketplace.adobe.com/customer/account/login/)에서 만들고 구성합니다. `[!UICONTROL username]`에 대해 공개 키 값을 복사하여 붙여 넣으십시오. `[!UICONTROL password]`에 대해 개인 키 값을 복사하여 붙여 넣으십시오.

   >[!NOTE]
   >
   > Commerce 인증 키로 구성된 작성기 `[auth.json](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/authentication-keys)` 파일 또는 환경 변수를 사용하는 경우 인증 키를 입력하라는 메시지가 표시되지 않습니다.

   `Could not find package...` 또는 `...no matching package found`과(와) 같은 오류가 발생하면 명령에 오타가 없는지 확인하십시오. 그래도 오류가 발생하면 Adobe Commerce을 다운로드할 수 있는 권한이 없을 수 있습니다. 도움이 필요하면 [Adobe Commerce 지원](https://support.magento.com/hc/en-us)에 문의하십시오.

   자세한 오류에 대한 도움말을 보려면 [문제 해결](https://support.magento.com/hc/en-us/articles/360033818091)을 참조하세요.

### 예 - 마이너 릴리스

마이너 릴리스에는 새로운 기능, 품질 수정 사항 및 보안 수정 사항이 포함되어 있습니다. 작성기를 사용하여 부 릴리스를 지정합니다. 예를 들어 Adobe Commerce 2.4.6 메타패키지를 지정하려면 다음을 수행합니다.

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### 예 - 품질 패치

품질 패치에는 주로 기능 _및_ 보안 수정 사항이 포함되어 있습니다. 그러나 이전 버전과 호환되는 새로운 기능이 포함되어 있는 경우도 있습니다. 작성기를 사용하여 품질 패치를 다운로드합니다. 예를 들어 Adobe Commerce 2.4.6 메타패키지를 지정하려면 다음을 수행합니다.

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### 예 - 보안 패치

보안 패치에는 보안 수정 사항만 포함됩니다. 업그레이드 프로세스를 더 빠르고 쉽게 할 수 있도록 설계되었습니다.

보안 패치는 작성기 명명 규칙 `2.4.6-px`을(를) 사용합니다. 작성기를 사용하여 패치를 지정합니다. 예를 들어 Adobe Commerce 2.4.6-p1 메타패키지를 다운로드하려면 다음을 수행합니다.

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## 파일 권한 설정

Adobe Commerce을 설치하기 전에 웹 서버 그룹에 대한 읽기/쓰기 권한을 설정해야 합니다. 명령줄이 파일 시스템에 파일을 쓸 수 있도록 해야 합니다.

```bash
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## 애플리케이션 설치

Adobe Commerce을 설치하려면 명령줄을 사용해야 합니다.

이 예제에서는 설치 디렉터리 이름이 `magento2ee`이고 `db-host`이(가) 같은 컴퓨터(`localhost`)에 있으며 `db-name`, `db-user` 및 `db-password`이(가) 모두 `magento`이라고 가정합니다.

```bash
bin/magento setup:install \
--base-url=http://localhost/magento2ee \
--db-host=localhost \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=opensearch \
--opensearch-host=os-host.example.com \
--opensearch-port=9200 \
--opensearch-index-prefix=magento2 \
--opensearch-timeout=15
```

>[!TIP]
>
>`--backend-frontname` 옵션을 사용하여 관리자 URI를 사용자 지정할 수 있습니다. 그러나 Adobe은 이 옵션을 생략하고 설치 명령으로 무작위 URI를 자동으로 생성하도록 할 것을 권장합니다. 무작위 URI는 해커나 악성 소프트웨어가 악용하기 더 어렵다. 설치가 완료되면 콘솔에 URI가 표시됩니다.

>[!TIP]
>
>CLI 설치 옵션에 대한 자세한 설명은 [명령줄에서 응용 프로그램 설치](advanced.md)를 참조하십시오.

## 명령 요약

전체 명령 목록을 표시하려면 다음을 입력합니다.

```bash
bin/magento list
```

특정 명령에 대한 도움말을 보려면 다음을 입력합니다.

```bash
bin/magento help <command>
```

For example:

```bash
bin/magento help setup:install
```

```bash
bin/magento help cache:enable
```

다음 표에는 사용 가능한 명령이 요약되어 있습니다. 명령은 요약 양식으로만 표시됩니다. 명령에 대한 자세한 내용을 보려면 명령 열에서 링크를 클릭합니다.

| 명령 | 설명 | 전제 조건 |
|--- |--- |--- |
| `magento setup:install` | 응용 프로그램을 설치합니다. | 없음 |
| `magento setup:uninstall` | 응용 프로그램을 제거합니다. | 애플리케이션 설치됨 |
| `magento setup:upgrade` | 응용 프로그램을 업데이트합니다. | 배포 구성 |
| `magento maintenance:{enable/disable}` | 유지 관리 모드를 활성화하거나 비활성화합니다(유지 관리 모드에서는 제외 IP 주소만 관리자 또는 상점 앞에 액세스할 수 있음). | 애플리케이션 설치됨 |
| `magento setup:config:set` | 배포 구성을 만들거나 업데이트합니다. | 없음 |
| `magento module:{enable/disable}` | 모듈을 활성화하거나 비활성화합니다. | 없음 |
| `magento setup:store-config:set` | 기본 URL, 언어, 시간대 등 storefront 관련 옵션을 설정합니다. | 배포 구성 |
| `magento setup:db-schema:upgrade` | 데이터베이스 스키마를 업데이트합니다. | 배포 구성 |
| `magento setup:db-data:upgrade` | 데이터베이스 데이터를 업데이트합니다. | 배포 구성 |
| `magento setup:db:status` | 데이터베이스가 코드를 사용하여 최신 상태인지 확인합니다. | 배포 구성 |
| `magento admin:user:create` | 관리자 사용자를 만듭니다. | <br><br>배포 구성<br><br>최소 `Magento_User` 및 `Magento_Authorization` 모듈 사용<br><br>데이터베이스에 대해 사용자를 만들 수 있습니다. 가장 간단한 방법은 `bin/magento setup:upgrade`을(를) 사용하는 것입니다. |
| `magento list` | 사용 가능한 모든 명령을 나열합니다. | 없음 |
| `magento help` | 지정한 명령에 대한 도움말을 제공합니다. | 없음 |

### 일반 인수

다음 인수는 모든 명령에 공통됩니다. 이러한 명령은 응용 프로그램을 설치하기 전이나 후에 실행할 수 있습니다.

| 긴 버전 | 짧은 버전 | 의미 |
|--- |--- |--- |
| `--help` | `-h` | 모든 명령에 대한 도움말을 봅니다. 예: `./magento help setup:install` 또는 `./magento help setup:config:set`. |
| `--quiet` | `-q` | 자동 모드, 출력 없음. |
| `--no-interaction` | `-n` | 대화형 질문 없음. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 세부 정보 수준입니다. 예를 들어 `--verbose=3` 또는 `-vvv`은(는) 가장 자세한 출력인 디버그 자세한 정보를 표시합니다. 기본값은 `--verbose=1` 또는 `-v`입니다. |
| `--version` | `-V` | 이 응용 프로그램 버전 표시 |
| `--ansi` | 해당 사항 없음 | ANSI 출력 강제 실행 |
| `--no-ansi` | 해당 사항 없음 | ANSI 출력 비활성화 |

>[!NOTE]
>
>축하합니다! 빠른 설치를 완료했습니다. 고급 도움말이 더 필요하십니까? [고급 설치](advanced.md) 안내서를 확인하십시오.
