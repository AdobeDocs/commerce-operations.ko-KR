---
title: 니스 설치
description: Varnish 설치에 대한 조언을 참조하십시오.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# 니스 설치

Varnish 소프트웨어를 설치하는 것은 이 안내서의 범위를 벗어납니다. Vannish 설치에 대한 자세한 내용은 다음을 참조하십시오.

- [설치 안내서](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [바니시 설치 가이드](https://www.varnish-cache.org/docs)
- [바니시(Tecmint)를 설치하는 방법](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>이 항목은 CentOS 및 Apache 2.4의 Varnish용으로 작성되었습니다. 다른 환경에서 바니시를 설정하는 경우 일부 명령이 다를 수 있습니다. 자세한 내용은 이전 설명서를 참조하십시오.
>
>saint 모드와 같은 Vmod(Varnish 모듈)를 설치하려면 패키지에서 설치하는 대신 코드를 컴파일하여 Varnish를 설치해야 합니다. 자세한 내용은 [SAINT 모드](config-varnish-advanced.md#saint-mode)를 참조하십시오.

## 니시 버전 확인

터미널을 열고 다음 명령을 입력하여 Varnish 버전을 표시합니다.

```bash
varnishd -V
```

계속하기 전에 [Adobe Commerce에서 설치된 버전의 바니시를 지원](../../installation/system-requirements.md)하는지 확인하십시오. 지원되지 않는 버전을 실행 중인 경우 지원되는 버전으로 업그레이드해야 합니다. 자세한 내용은 Varnish 설치 설명서를 참조하십시오.
