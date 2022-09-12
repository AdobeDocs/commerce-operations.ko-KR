---
title: 샘플 데이터 Git 리포지토리 복제
description: Git 리포지토리를 복제하여 Adobe Commerce 및 Magento Open Source 샘플 데이터를 설치하려면 다음 단계를 따르십시오.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---


# 샘플 데이터 Git 리포지토리 복제

이 항목에서는 Magento Open Source GitHub 리포지토리를 복제한 경우 샘플 데이터를 복제하고 추가하는 방법에 대해 설명합니다. 이 방법은 기여 개발자(즉, Magento Open Source 코드 베이스에 기여하려고 하는 개발자)에게만 해당됩니다.

기여 개발자가 아닌 경우, 페이지 왼쪽의 목차 항목에 표시되는 다른 옵션 중 하나를 선택합니다.

기여 개발자는 이 샘플 데이터 설치 방법을 사용할 수 있습니다 *전용* true인 경우:

* Magento Open Source 사용
* 사용자 [GitHub 리포지토리 복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>다음 중 하나에서 샘플 데이터를 사용할 수 있습니다 `develop` 분기(더 최신) 또는 릴리즈된 분기(예: `2.4` (안정적임). 릴리스된 분기가 더 안정적이기 때문에 사용하는 것이 좋습니다. 저장소에 코드를 기여하고 가장 최근 코드가 필요한 경우 `develop` 분기 선택한 분기에 관계없이 다음을 수행해야 합니다 [복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) Magento Open Source GitHub 리포지토리의 해당 분기. 예를 들어 `develop` 분기는 사용할 수 있습니다 *전용* Magento Open Source 사용 `develop` 분기

## 샘플 데이터 리포지토리 복제

이 섹션에서는 샘플 데이터 저장소를 복제하여 샘플 데이터를 설치하는 방법을 설명합니다. 다음 방법 중 하나로 샘플 데이터 저장소를 복제할 수 있습니다.

* 을 사용하여 복제 [SSH 프로토콜](#clone-with-ssh)
* 을 사용하여 복제 [HTTPS 프로토콜](#clone-with-https)

### SSH로 복제

SSH 프로토콜을 사용하여 샘플 데이터 GitHub 리포지토리를 복제하려면 다음을 수행하십시오.

1. 웹 브라우저에서 [샘플 데이터 저장소](https://github.com/magento/magento2-sample-data).
1. 분기 이름 옆에 있는 를 클릭합니다. **SSH** 참조하십시오.
1. 클릭 **클립보드에 복사**

   다음 그림은 예를 보여줍니다.

   ![SSH를 사용하여 GitHub 리포지토리 복제](../../assets/installation/install_mage2_clone-ssh.png)

1. 웹 서버의 docroot 디렉토리로 변경합니다.

   보통 우분투에게, `/var/www` 그리고 CentOS는 `/var/www/html`.

1. Enter 키 `git clone` 그리고 이전에 얻은 값을 붙여넣습니다.

   예는 다음과 같습니다.

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. 서버가 복제될 때까지 기다립니다.

   >[!NOTE]
   >
   >다음 오류가 표시되면 다음을 확인하십시오 [ssh 키 공유](https://docs.github.com/articles/generating-ssh-keys/) gitHub 사용:<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. 기본 분기에서 사용한 분기에 해당하는 샘플 데이터 저장소 분기를 체크 아웃해야 합니다 `magento2` 저장소.

   For example:

   를 사용한 경우 `2.4-develop` Magento Open Source GitHub 리포지토리의 분기, 샘플 데이터 분기는 `2.4-develop`.

   를 사용한 경우 `2.4.3` Magento Open Source GitHub 리포지토리의 분기, 샘플 데이터 분기는 `2.4.3`.

   올바른 분기를 체크 아웃하려면 샘플 데이터 저장소의 루트 디렉토리에서 다음 명령을 실행합니다(이 경우 `2.4.3` 분기):

   ```bash
   git checkout 2.4.3
   ```

1. 다음으로 변경 `<app_root>`.
1. 샘플 데이터가 제대로 작동하도록 복제한 파일 간에 심볼 링크를 만들려면 다음 명령을 입력합니다.

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. 명령이 완료될 때까지 기다립니다.

1. 자세한 내용은 [파일 시스템 권한 및 소유권 설정](#set-file-system-ownership-and-permissions).

1. 다음 명령을 실행합니다.

   ```bash
   bin/magento setup:upgrade
   ```

### HTTPS를 사용하여 복제

HTTPS 프로토콜을 사용하여 샘플 데이터 GitHub 리포지토리를 복제하려면 다음을 수행하십시오.

1. 웹 브라우저에서 [샘플 데이터 저장소](https://github.com/magento/magento2-sample-data).
1. 페이지 오른쪽의 아래에서 **복제 URL** 필드 **HTTPS**.
1. 클릭 **클립보드에 복사**.

   다음 그림은 예를 보여줍니다.

   ![HTTPS를 사용하여 GitHub 리포지토리 복제](../../assets/installation/install_mage2_clone-https.png)

1. 웹 서버의 docroot 디렉토리로 변경합니다.

   보통 우분투에게, `/var/www` 그리고 CentOS는 `/var/www/html`.

1. Enter 키 `git clone` 그리고 이전에 얻은 값을 붙여넣습니다.

   예는 다음과 같습니다.

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. 서버가 복제될 때까지 기다립니다.
1. 기본 분기에서 사용한 분기에 해당하는 샘플 데이터 저장소 분기를 체크 아웃해야 합니다 `magento2` 저장소.

   예:

   를 사용한 경우 `2.4-develop` Magento Open Source GitHub 리포지토리의 분기, 샘플 데이터 분기는 `2.4-develop`.

   를 사용한 경우 `2.4.3` Magento Open Source GitHub 리포지토리의 분기, 샘플 데이터 분기는 `2.4.3`.

   올바른 분기를 체크 아웃하려면 샘플 데이터 저장소의 루트 디렉토리에서 다음 명령을 실행합니다(이 경우 `2.4.3` 분기):

   ```bash
   git checkout 2.4.3
   ```

1. 다음으로 변경 `<magento_root>`.
1. 샘플 데이터가 제대로 작동하도록 복제한 파일 간에 심볼 링크를 만들려면 다음 명령을 입력합니다.

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
>샘플 데이터를 설치하는 경우 *after* Adobe Commerce 또는 Magento Open Source을 설치하는 경우 다음 명령을 실행하여 데이터베이스와 스키마를 업데이트해야 합니다.
>
>
```bash
><magento_root>/bin/magento setup:upgrade
>```

## 파일 시스템 소유권 및 권한 설정

왜냐하면 `php build-sample-data.php` 스크립트는 샘플 데이터 저장소와 Magento Open Source 저장소 간에 symlink를 만들며 샘플 데이터 저장소에서 파일 시스템 권한 및 소유권을 설정해야 합니다. 이렇게 하지 않으면 상점 액세스에 오류가 발생합니다.

샘플 데이터 리포지토리에 대한 파일 시스템 권한 및 소유권을 설정하려면 다음을 수행하십시오.

1. 샘플 데이터 복제 디렉토리로 변경합니다.
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

## 샘플 데이터 설치 완료

{{$include /help/_includes/sample-data-complete.md}}
