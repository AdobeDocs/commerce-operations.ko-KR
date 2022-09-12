---
title: 온-프레미스 설치 보안
description: Adobe Commerce 또는 Magento Open Source 온프레미스 설치의 보안 자세를 개선하는 방법에 대해 알아봅니다.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# 온-프레미스 설치 보안

[보안 Enhanced Linux(SELinux)](https://selinuxproject.org/page/Main_Page) CentOS 및 Ubuntu 관리자를 사용하여 서버에 대한 액세스 제어를 강화합니다. SELinux를 사용하는 경우 *및* Apache는 다른 호스트에 대한 연결을 시작해야 합니다. 이 섹션에서 설명한 명령을 실행해야 합니다.

>[!NOTE]
>
>Adobe에 SELinux 사용에 대한 권장 사항이 없습니다. 필요한 경우 보안 강화를 위해 사용할 수 있습니다. SELinux를 사용하는 경우 제대로 구성해야 합니다. 그렇지 않으면 Adobe Commerce 및 Magento Open Source이 예기치 않게 작동할 수 있습니다. SELinux를 사용하도록 선택하는 경우 다음과 같은 리소스를 참조하십시오. [CentOS Wiki](https://wiki.centos.org/HowTos/SELinux) 을 입력하여 통신을 활성화할 규칙을 설정합니다.

## Apache를 사용한 설치 제안

SELinux를 사용하도록 선택하는 경우, *보안 컨텍스트* 다음과 같은 일부 디렉토리

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

위의 명령은 Apache 웹 서버에서만 작동합니다. 다양한 구성 및 보안 요구 사항으로 인해 이러한 명령이 모든 상황에서 작동한다고 보장하지는 않습니다. 자세한 내용은 다음을 참조하십시오.

* [페이지](https://linux.die.net/man/8/httpd_selinux)
* [서버 랩](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## 서버 간 통신 활성화

Apache와 데이터베이스 서버가 동일한 호스트에 있는 경우, 를 사용하는 통합을 사용하려면 다음 명령을 사용하십시오 `curl` (예) Paypal 및 USPS).
Apache가 SELinux가 활성화된 다른 호스트에 대한 연결을 시작하도록 하려면,

1. SELinux가 활성화되어 있는지 확인하려면 다음 명령을 사용하십시오.

   ```bash
   getenforce
   ```

   `Enforcing` SELinux가 실행 중인지 확인하기 위해 가 표시됩니다.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * 우분투: `setsebool -P apache2_can_network_connect=1`

## 방화벽에서 포트 열기

보안 요구 사항에 따라 방화벽에서 포트 80 및 기타 포트를 열어야 할 수 있습니다. 네트워킹 보안의 민감한 특성상 계속 진행하기 전에 IT 부서에 문의하는 것이 좋습니다. 다음은 몇 가지 추천 참조입니다.

* 우분투: [Ubuntu 설명서 페이지](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [CentOS 방법](https://wiki.centos.org/HowTos/Network/IPTables).
