---
title: 관리자 URI 표시 또는 변경
description: Adobe Commerce 또는 Magento Open Source 관리 애플리케이션의 URI를 보고 수정하려면 다음 단계를 따르십시오.
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# 관리자 URI 표시 또는 변경

이 명령을 실행하기 전에 다음을 수행해야 합니다 [배포 구성 만들기 또는 업데이트](deployment.md).

## 관리자 URI 표시

이 섹션에서는 명령줄을 사용하여 Admin Uniform Resource Identifier( 를 표시하는 방법에 대해 설명합니다.[URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

명령 옵션:

```bash
bin/magento info:adminuri
```

샘플 결과는 다음과 같습니다.

```terminal
Admin Panel URI: /admin_1wgrah
```

에서 관리자 URI를 볼 수도 있습니다. `<magento_root>/app/etc/env.php`. 코드 조각은 다음과 같습니다.

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 관리자 URL 변경

관리자 URI를 변경하려면 [`magento setup:config:set`](deployment.md) 명령입니다.
