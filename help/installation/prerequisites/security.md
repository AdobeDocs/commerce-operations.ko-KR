---
title: 온-프레미스 설치 보안
description: Adobe Commerce 또는 Magento Open Source 온프레미스 설치의 보안 자세를 개선하는 방법에 대해 알아봅니다.
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# 온-프레미스 설치 보안

[보안 강화 Linux(SELinux)](https://selinuxproject.org/page/Main_Page) 이를 통해 CentOS 및 Ubuntu 관리자는 서버에 대한 액세스 제어를 강화할 수 있습니다. SELinux를 사용하는 경우 *및* Apache는 다른 호스트에 대한 연결을 시작해야 하며, 이 섹션에서 설명한 명령을 실행해야 합니다.

>[!NOTE]
>
>Adobe은 SELinux 사용에 대한 권장 사항이 없습니다. 원할 경우 향상된 보안을 위해 사용할 수 있습니다. SELinux를 사용하는 경우 올바르게 구성해야 합니다. 그렇지 않으면 Adobe Commerce 및 Magento Open Source이 예기치 않게 작동할 수 있습니다. SELinux를 사용하려면 [CentOS 위키](https://wiki.centos.org/HowTos/SELinux) 통신 활성화를 위한 규칙을 설정합니다.

## Apache에 설치하기 위한 제안 사항

SELinux를 사용하도록 선택하면 *보안 컨텍스트* 다음과 같은 일부 디렉토리:

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

위의 명령은 Apache 웹 서버에서만 작동합니다. 다양한 구성과 보안 요구 사항으로 인해 이러한 명령이 모든 상황에서 작동하도록 보장하지는 않습니다. 자세한 내용은 다음을 참조하십시오.

* [매뉴얼 페이지](https://linux.die.net/man/8/httpd_selinux)
* [서버 랩](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## 서버 간 통신 사용

Apache와 데이터베이스 서버가 동일한 호스트에 있는 경우 를 사용하는 통합을 사용하려면 다음 명령을 사용하십시오 `curl` (예: Paypal 및 USPS).
SELinux가 활성화된 상태에서 Apache가 다른 호스트에 대한 연결을 시작하려면 다음을 수행하십시오.

1. SELinux가 활성화되어 있는지 확인하려면 다음 명령을 사용합니다.

   ```bash
   getenforce
   ```

   `Enforcing` 를 표시하여 SELinux가 실행 중인지 확인합니다.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * 우분투: `setsebool -P apache2_can_network_connect=1`

## 방화벽에서 포트 열기

보안 요구 사항에 따라 방화벽에서 포트 80 및 기타 포트를 열어야 할 수도 있습니다. 네트워킹 보안의 민감한 특성 때문에 Adobe은 계속하기 전에 IT 부서에 문의하는 것이 좋습니다. 다음은 몇 가지 제안된 참조입니다.

* 우분투: [Ubuntu 설명서 페이지](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [CentOS 방법](https://wiki.centos.org/HowTos/Network/IPTables).
