---
title: Apache를 사용하여 여러 웹 사이트 설정
description: Apache를 사용하여 여러 웹 사이트를 설정하려면 이 자습서를 따르십시오.
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# Apache를 사용하여 여러 웹 사이트 설정

다음과 같이 가정합니다.

필요한 경우 웹 사이트 또는 스토어 보기에 대한 기존 `index.php` 진입점 스크립트를 복사하고 다음에 추가하십시오.

- 개발 컴퓨터(랩톱, 가상 컴퓨터 등)에서 작업 중입니다.

  호스팅 환경에서 여러 웹 사이트를 배포하려면 추가 작업이 필요할 수 있습니다. 자세한 내용은 호스팅 공급자에게 문의하십시오.

  클라우드 인프라에서 Adobe Commerce을 설정하려면 추가 작업이 필요합니다. 이 항목에서 설명한 작업을 완료하면 _Commerce on Cloud Infrastructure 안내서_&#x200B;의 [여러 웹 사이트 또는 스토어 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=ko)을 참조하십시오.

- 웹 사이트당 하나의 가상 호스트를 사용합니다. 가상 호스트 구성 파일은 `/etc/httpd/httpd.conf`입니다.

  다른 운영 체제에 있는 다른 버전의 Apache는 가상 호스트를 다르게 설정합니다. 가상 호스트를 설정하는 방법을 잘 모를 경우 [Apache 설명서](https://httpd.apache.org/docs/2.4/vhosts) 또는 네트워크 관리자에게 문의하십시오.

- Commerce 소프트웨어가 `/var/www/html/magento2`에 설치되어 있습니다.
- 기본 이외의 두 개의 웹 사이트가 있습니다.

   - `french.mysite.mg`(웹 사이트 코드 `french` 및 스토어 보기 코드 `fr` 포함)
   - `german.mysite.mg`(웹 사이트 코드 `german` 및 스토어 보기 코드 `de` 포함)

## Apache를 사용하여 여러 웹 사이트를 설정하는 로드맵

여러 스토어를 설정하는 작업은 다음 작업으로 구성됩니다.

1. 관리자의 [웹 사이트, 스토어 및 스토어 보기 설정](ms-admin.md).
1. Commerce 웹 사이트당 하나의 [Apache 가상 호스트](#step-2-create-apache-virtual-hosts)를 만듭니다.

## 1단계: 관리자에서 웹 사이트, 스토어 및 스토어 보기 만들기

[관리에서 여러 웹 사이트, 스토어 및 스토어 보기 설정](ms-admin.md)을 참조하십시오.

## 2단계: Apache 가상 호스트 생성

이 섹션에서는 가상 호스트에서 Apache 서버 변수 `SetEnvIf`을(를) 사용하여 `MAGE_RUN_TYPE` 및 `MAGE_RUN_CODE`에 대한 값을 설정하는 방법에 대해 설명합니다.

`SetEnvIf`에 대한 자세한 내용은 다음을 참조하십시오.

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Apache 가상 호스트를 만들려면**:

1. `root` 권한이 있는 사용자는 텍스트 편집기에서 가상 호스트 구성 파일을 여십시오.

   예: `/etc/httpd/conf/httpd.conf` 열기

1. `<VirtualHost *:80>`(으)로 시작하는 섹션을 찾습니다.
1. 기존 가상 호스트 뒤에 다음 가상 호스트를 만듭니다.

   ```conf
   <VirtualHost *:80>
      ServerName          mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          french.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "french"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          german.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "german"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   ```

1. 변경 내용을 `httpd.conf`에 저장하고 텍스트 편집기를 종료합니다.
1. Apache 다시 시작:

   - CentOS: `service httpd restart`
   - 우분투: `service apache2 restart`

## 사이트 확인

스토어의 URL에 대해 DNS를 설정하지 않은 경우 `hosts` 파일의 호스트에 정적 경로를 추가해야 합니다.

1. 운영 체제 `hosts` 파일을 찾습니다.
1. 정적 경로를 다음 형식으로 추가합니다.

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. 브라우저에서 다음 URL 중 하나로 이동합니다.

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- 호스팅 환경에서 여러 웹 사이트를 배포하려면 추가 작업이 필요할 수 있습니다. 자세한 내용은 호스팅 공급자에게 문의하십시오.
>- 클라우드 인프라에서 Adobe Commerce을 설정하려면 추가 작업이 필요합니다. _Commerce on Cloud Infrastructure 안내서_&#x200B;의 [여러 클라우드 웹 사이트 또는 스토어 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=ko)을 참조하십시오.

### 문제 해결

- 프랑스어 및 독일어 사이트가 404를 반환하지만 관리자가 로드되는 경우 [6단계: 기본 URL에 스토어 코드를 추가](ms-admin.md#step-6-add-the-store-code-to-the-base-url)를 완료했는지 확인하십시오.
- 모든 URL이 404를 반환하는 경우 웹 서버를 다시 시작했는지 확인하십시오.
- 관리자가 제대로 작동하지 않는 경우 가상 호스트를 제대로 설정했는지 확인하십시오.
