---
title: 관리자 URI 표시 또는 변경
description: Adobe Commerce 관리 애플리케이션의 URI를 보고 수정하려면 다음 단계를 따르십시오.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---

# 관리자 URI 표시 또는 변경

이 명령을 실행하기 전에 [배포 구성을 만들거나 업데이트](deployment.md)해야 합니다.

## 관리자 URI 표시

이 섹션에서는 명령줄을 사용하여 Admin Uniform Resource Identifier([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))를 표시하는 방법에 대해 설명합니다.

명령 옵션:

```shell
bin/magento info:adminuri
```

샘플 결과는 다음과 같습니다.

```text
Admin Panel URI: /admin_1wgrah
```

`<magento_root>/app/etc/env.php`에서 관리자 URI를 볼 수도 있습니다. 코드 조각은 다음과 같습니다.

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 관리자 URL 변경

관리자 URI를 변경하려면 [`magento setup:config:set`](deployment.md) 명령을 사용하십시오.
