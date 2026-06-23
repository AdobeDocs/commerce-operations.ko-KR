---
title: 니스 설치
description: Adobe Commerce 캐싱을 위한 Vanish 설치 요구 사항에 대해 알아봅니다. 설치 리소스 및 설치 지침을 살펴보십시오.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
badgePaas: label="온-프레미스" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce 온-프레미스 프로젝트에만 적용됩니다."
autotag-review: '2026-06-22T21:26:58.525Z'
TQID: 'https://experienceleague.adobe.com/Cvy4Qsi-5Fom1t5wqNlq1SiSs4Bb8-DPsWrGfapWfSc'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 189
ht-degree: 0%

---

# 니스 설치

{{varnish-config-cloud}}

바니시를 설치하는 것은 이 안내서의 범위를 벗어납니다. 이 항목에서는 지원되는 바니시 버전 및 바니시 뒤에서 실행되는 Adobe Commerce 원본 서버를 가정합니다. 이 안내서의 예제에서는 nginx를 원본 웹 서버로 사용합니다.

- [설치 안내서](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [니시 설치 가이드](https://www.varnish-cache.org/docs)
- [바니쉬 설치 방법 (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>saint 모드와 같은 Vmod(Varnish 모듈)를 설치하려면 패키지에서 설치하는 대신 코드를 컴파일하여 Varnish를 설치해야 합니다. 자세한 내용은 [SAINT 모드](config-varnish-advanced.md#saint-mode)를 참조하십시오.

## 니시 버전 확인

터미널을 열고 다음 명령을 입력하여 Varnish 버전을 표시합니다.

```shell
varnishd -V
```

계속하기 전에 [Adobe Commerce에서 설치된 버전의 바니시를 지원](../../installation/system-requirements.md)하는지 확인하십시오. 지원되지 않는 버전을 실행 중인 경우 지원되는 버전으로 업그레이드해야 합니다. 자세한 내용은 Varnish 설치 설명서를 참조하십시오.
