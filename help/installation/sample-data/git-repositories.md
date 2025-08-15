---
title: 샘플 데이터 Git 저장소 복제
description: 다음 단계에 따라 Git 저장소를 복제하여 Adobe Commerce 샘플 데이터를 설치합니다.
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# 샘플 데이터 Git 저장소 복제

이 항목에서는 Magento Open Source GitHub 저장소를 복제한 경우 샘플 데이터를 복제하고 추가하는 방법에 대해 설명합니다. 이 메서드는 기여 개발자(즉, Magento Open Source 코드 베이스에 기여하려는 개발자)만을 위한 것입니다.

기여 개발자가 아닌 경우 페이지 왼쪽의 목차에 표시되는 다른 옵션 중 하나를 선택합니다.

다음에 해당하는 경우 기여 개발자는 이 방법으로 샘플 데이터를 설치할 수 있습니다. *only*:

* Magento Open Source 사용
* [GitHub 리포지토리를 복제했습니다](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>`develop` 분기(최신) 또는 릴리스된 분기(예: `2.4`(안정적인))에서 샘플 데이터를 사용할 수 있습니다. 안정적이므로 출시된 지점을 사용하는 것이 좋습니다. 저장소에 코드를 제공하는 중이며 최신 코드가 필요한 경우 `develop` 분기를 사용하십시오. 선택한 분기와 관계없이 Magento Open Source GitHub 저장소의 해당 분기를 [복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)해야 합니다. 예를 들어 `develop` 분기에 대한 샘플 데이터는 Magento Open Source *분기에서* only`develop` 사용할 수 있습니다.

## 샘플 데이터 리포지토리 복제

이 섹션에서는 샘플 데이터 저장소를 복제하여 샘플 데이터를 설치하는 방법에 대해 설명합니다. 다음 방법 중 하나로 샘플 데이터 저장소를 복제할 수 있습니다.

* [SSH 프로토콜](#clone-with-ssh)을 사용하여 복제
* [HTTPS 프로토콜](#clone-with-https)(으)로 복제

### SSH로 복제

SSH 프로토콜을 사용하여 샘플 데이터 GitHub 리포지토리를 복제하려면 다음을 수행합니다.

1. 웹 브라우저에서 [샘플 데이터 저장소](https://github.com/magento/magento2-sample-data)&#x200B;(으)로 이동합니다.
1. 분기 이름 옆에 있는 목록에서 **SSH**&#x200B;을(를) 클릭합니다.
1. **클립보드에 복사**&#x200B;를 클릭합니다.

   다음 그림은 예를 보여 줍니다.

   ![SSH를 사용하여 GitHub 리포지토리 복제](../../assets/installation/install_mage2_clone-ssh.png)

1. 웹 서버의 docroot 디렉토리로 변경합니다.

   일반적으로 우분투의 경우 `/var/www`이고 CentOS의 경우 `/var/www/html`입니다.

1. `git clone`을(를) 입력하고 이전에 얻은 값을 붙여넣습니다.

   예제는 다음과 같습니다.

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. 서버에서 저장소가 복제될 때까지 기다립니다.

   >[!NOTE]
   >
   >다음 오류가 표시되면 [SSH 키를 공유](https://docs.github.com/articles/generating-ssh-keys/)하여 GitHub를 사용하도록 합니다.<br>

   ```
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. 주 `magento2` 리포지토리에서 사용한 분기와 일치하는 샘플 데이터 리포지토리의 분기를 체크 아웃해야 합니다.

   For example:

   Magento Open Source GitHub 리포지토리의 `2.4-develop` 분기를 사용한 경우 샘플 데이터 분기는 `2.4-develop`이어야 합니다.

   올바른 분기를 체크 아웃하려면 샘플 데이터 저장소의 루트 디렉터리에서 다음 명령을 실행합니다(`2.4-develop` 분기가 필요하다고 가정).

   ```bash
   git checkout 2.4-develop
   ```

1. `<app_root>`(으)로 변경합니다.
1. 샘플 데이터가 제대로 작동하도록 클론한 파일 사이에 심볼 링크를 만들려면 다음 명령을 입력합니다.

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. 명령이 완료될 때까지 기다립니다.

1. [파일 시스템 권한 및 소유권 설정](#set-file-system-ownership-and-permissions)을 참조하십시오.

1. 다음 명령을 실행합니다.

   ```bash
   bin/magento setup:upgrade
   ```

### HTTPS로 복제

HTTPS 프로토콜을 사용하여 샘플 데이터 GitHub 저장소를 복제하려면 다음을 수행하십시오.

1. 웹 브라우저에서 [샘플 데이터 저장소](https://github.com/magento/magento2-sample-data)&#x200B;(으)로 이동합니다.
1. 페이지 오른쪽의 **복제 URL** 필드 아래에서 **HTTPS**&#x200B;을(를) 클릭합니다.
1. **클립보드에 복사**&#x200B;를 클릭합니다.

   다음 그림은 예를 보여 줍니다.

   ![HTTPS를 사용하여 GitHub 리포지토리 복제](../../assets/installation/install_mage2_clone-https.png)

1. 웹 서버의 docroot 디렉토리로 변경합니다.

   일반적으로 우분투의 경우 `/var/www`이고 CentOS의 경우 `/var/www/html`입니다.

1. `git clone`을(를) 입력하고 이전에 얻은 값을 붙여넣습니다.

   예제는 다음과 같습니다.

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. 서버에서 저장소가 복제될 때까지 기다립니다.
1. 주 `magento2` 리포지토리에서 사용한 분기와 일치하는 샘플 데이터 리포지토리의 분기를 체크 아웃해야 합니다.

   For example:

   Magento Open Source GitHub 리포지토리의 `2.4-develop` 분기를 사용한 경우 샘플 데이터 분기는 `2.4-develop`이어야 합니다.

   올바른 분기를 체크 아웃하려면 샘플 데이터 저장소의 루트 디렉터리에서 다음 명령을 실행합니다(`2.4-develop` 분기가 필요하다고 가정).

   ```bash
   git checkout 2.4-develop
   ```

1. `<magento_root>`(으)로 변경합니다.
1. 샘플 데이터가 제대로 작동하도록 클론한 파일 사이에 심볼 링크를 만들려면 다음 명령을 입력합니다.

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   For example,

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. 명령이 완료될 때까지 기다립니다.
1. 다음 섹션을 참조하십시오.

>[!WARNING]
>
>Adobe Commerce을 설치하는 *after* 샘플 데이터를 설치하는 경우 다음 명령도 실행하여 데이터베이스 및 스키마를 업데이트해야 합니다.
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## 파일 시스템 소유권 및 권한 설정

`php build-sample-data.php` 스크립트는 샘플 데이터 저장소와 Magento Open Source 저장소 사이에 심볼릭 링크를 만들기 때문에 샘플 데이터 저장소에서 파일 시스템 사용 권한 및 소유권을 설정해야 합니다. 이렇게 하지 않으면 상점에 액세스하는 동안 오류가 발생합니다.

샘플 데이터 저장소에서 파일 시스템 권한 및 소유권을 설정하려면 다음을 수행합니다.

1. 샘플 데이터 클론 디렉토리로 변경합니다.
1. 소유권 설정:

   ```bash
   chown -R :<your web server group name> .
   ```

   일반적인 예:

   * CentOS: `chown -R :apache .`

   * 우분투: `chown -R :www-data .`

1. 권한 설정:

   ```bash
   find . -type d -exec chmod g+ws {} +
   ```

1. 정적 파일 지우기:

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## 샘플 데이터 설치를 완료합니다

{{$include /help/_includes/sample-data-complete.md}}
