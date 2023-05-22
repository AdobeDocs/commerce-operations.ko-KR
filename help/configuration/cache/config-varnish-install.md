---
title: 니스 설치
description: Varnish 설치에 대한 조언을 참조하십시오.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# 니스 설치

Varnish 소프트웨어를 설치하는 것은 이 안내서의 범위를 벗어납니다. Vannish 설치에 대한 자세한 내용은 다음을 참조하십시오.

- [설치 안내서](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [니시 설치 가이드](https://www.varnish-cache.org/docs)
- [바니쉬 설치 방법 (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>이 항목은 CentOS 및 Apache 2.4의 Varnish용으로 작성되었습니다. 다른 환경에서 바니시를 설정하는 경우 일부 명령이 다를 수 있습니다. 자세한 내용은 이전 설명서를 참조하십시오.
>
>saint 모드와 같은 Vmod(Varnish 모듈)를 설치하려면 패키지에서 설치하는 대신 코드를 컴파일하여 Varnish를 설치해야 합니다. 다음을 참조하십시오 [Saint 모드](config-varnish-advanced.md#saint-mode) 을 참조하십시오.

## 니시 버전 확인

터미널을 열고 다음 명령을 입력하여 Varnish 버전을 표시합니다.

```bash
varnishd -V
```

샘플은 다음과 같습니다.

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

계속하기 전에 버전이 6.x인지 확인하십시오. 6.x 이전 버전을 실행 중인 경우 지원되는 버전으로 업그레이드해야 합니다. 자세한 내용은 Varnish 설치 설명서를 참조하십시오.
