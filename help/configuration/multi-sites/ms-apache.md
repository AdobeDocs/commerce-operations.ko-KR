---
title: Apache를 사용하여 여러 웹 사이트 설정
description: Apache를 사용하여 여러 웹 사이트를 설정하려면 이 자습서를 따르십시오.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---


# Apache를 사용하여 여러 웹 사이트 설정

우리는 다음과 같이 가정합니다.

필요한 경우 기존 `index.php` 웹 사이트 또는 [저장소 보기](https://glossary.magento.com/store-view) 을 추가하고 다음을 추가합니다.

- 개발 시스템(랩톱, 가상 시스템 등)에서 작업 중입니다.

   호스팅된 환경에 여러 웹 사이트를 배포하는 데 추가 작업이 필요할 수 있습니다. 자세한 내용은 호스팅 공급자에게 문의하십시오.

   클라우드 인프라에서 Adobe Commerce을 설정하려면 추가 작업이 필요합니다. 이 항목에서 설명한 작업을 완료하면 [여러 웹 사이트 또는 저장소 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 에서 _Commerce on Cloud Infrastructure 안내서_.

- 웹 사이트당 하나의 가상 호스트를 사용합니다. 가상 호스트 구성 파일은 `/etc/httpd/httpd.conf`

   다른 운영 체제에 있는 Apache의 다른 버전은 가상 호스트를 다르게 설정합니다. 자세한 내용은 [Apache 설명서](https://httpd.apache.org/docs/2.4/vhosts) 가상 호스트를 설정하는 방법을 모를 경우 네트워크 관리자에게 문의하십시오.

- 상거래 소프트웨어는 `/var/www/html/magento2`
- 기본값이 아닌 두 개의 웹 사이트가 있습니다.

   - `french.mysite.mg` 웹 사이트 코드 포함 `french` 보기 코드 저장 `fr`
   - `german.mysite.mg` 웹 사이트 코드 포함 `german` 보기 코드 저장 `de`

## Apache를 사용하여 여러 웹 사이트를 설정하는 로드맵

여러 저장소를 설정하는 작업은 다음 작업으로 구성됩니다.

1. [웹 사이트, 저장소 및 저장소 보기 설정](ms-admin.md) 관리자.
1. 만들기 [Apache 가상 호스트](#step-2-create-apache-virtual-hosts) 상거래 웹 사이트당.

## 1단계: 관리자로부터 웹 사이트 만들기, 저장 및 보기 저장

자세한 내용은 [관리자에서 여러 웹 사이트, 저장소 및 보기 저장 설정](ms-admin.md).

## 2단계: Apache 가상 호스트 만들기

이 섹션에서는 다음에 대한 값을 설정하는 방법을 설명합니다 `MAGE_RUN_TYPE` 및 `MAGE_RUN_CODE` Apache 서버 변수 사용 `SetEnvIf` 가상 호스트

에 대한 자세한 정보 `SetEnvIf`다음을 참조하십시오.

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Apache 가상 호스트를 만들려면**:

1. 을 사용하는 사용자 `root` 권한, 텍스트 편집기에서 가상 호스트 구성 파일을 엽니다.

   예를 들어 를 엽니다. `/etc/httpd/conf/httpd.conf`

1. 다음으로 시작하는 섹션을 찾습니다. `<VirtualHost *:80>`.
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

1. 변경 내용을 `httpd.conf` 텍스트 편집기를 종료합니다.
1. Apache를 다시 시작합니다.

   - CentOS: `service httpd restart`
   - 우분투: `service apache2 restart`

## 사이트 확인

저장소 URL에 대해 DNS를 설정하지 않은 경우, 의 호스트에 정적 경로를 추가해야 합니다 `hosts` 파일:

1. 운영 체제 찾기 `hosts` 파일.
1. 정적 경로를 형식으로 추가합니다.

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
>- 호스팅된 환경에 여러 웹 사이트를 배포하는 데 추가 작업이 필요할 수 있습니다. 자세한 내용은 호스팅 공급자에게 문의하십시오.
>- 클라우드 인프라에서 Adobe Commerce을 설정하려면 추가 작업이 필요합니다. 참조 [여러 클라우드 웹 사이트 또는 저장소 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 에서 _Commerce on Cloud Infrastructure 안내서_.


### 문제 해결

- 프랑스어 및 독일어 사이트가 404를 반환하지만 관리자가 로드되는 경우 작업을 완료했는지 확인하십시오 [6단계: 기본 URL에 스토어 코드 추가](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- 모든 URL이 404를 반환하는 경우 웹 서버를 다시 시작했는지 확인하십시오.
- Admin Console이 제대로 작동하지 않는 경우 가상 호스트를 올바르게 설정했는지 확인하십시오.
