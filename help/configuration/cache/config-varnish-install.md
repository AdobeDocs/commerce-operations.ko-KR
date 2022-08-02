---
title: Varnish 설치
description: Varnish 설치에 대한 조언을 참조하십시오.
source-git-commit: 688db9fcc9cd196d1560e49719b03ef32d13870d
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Varnish 설치

Varnish 소프트웨어 설치는 이 안내서의 범위를 벗어납니다. Varnish 설치에 대한 자세한 내용은 다음을 참조하십시오.

- [설치 wiki](http://wiki.mikejung.biz/Varnish)
- [Varnish 설치 가이드](https://www.varnish-cache.org/docs)
- [Varnish(Techmint) 설치 방법](http://www.tecmint.com/install-varnish-cache-web-accelerator)

>[!INFO]
>
>이 항목은 CentOS와 Apache 2.4의 Varnish에 대해 작성됩니다. 다른 환경에서 Varnish를 설정하는 경우 일부 명령이 다를 수 있습니다. 자세한 내용은 이전 설명서를 참조하십시오.
>
>saint 모드와 같은 Varnish 모듈(vmods)을 설치하려면 패키지에서 설치하는 대신 코드를 컴파일하여 Varnish를 설치해야 합니다. 자세한 내용은 [Saint 모드](config-varnish-advanced.md#saint-mode) 자세한 내용

## Varnish 버전 확인

터미널을 열고 다음 명령을 입력하여 Varnish 버전을 표시합니다.

```bash
varnishd -V
```

샘플은

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

계속하기 전에 버전이 6.x인지 확인하십시오. 6.x 이하 버전을 실행 중인 경우 지원되는 버전으로 업그레이드해야 합니다. 자세한 내용은 Varnish 설치 설명서를 참조하십시오.
