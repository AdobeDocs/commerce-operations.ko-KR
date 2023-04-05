---
title: 관리자 URI 표시 또는 변경
description: Adobe Commerce 또는 Magento Open Source 관리 애플리케이션의 URI를 보고 수정하려면 다음 단계를 수행합니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# 관리자 URI 표시 또는 변경

이 명령을 실행하기 전에 [배포 구성 만들기 또는 업데이트](deployment.md).

## 관리 URI 표시

이 섹션에서는 명령줄을 사용하여 관리 Uniform Resource Identifier([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

명령 옵션:

```bash
bin/magento info:adminuri
```

다음은 샘플 결과입니다.

```terminal
Admin Panel URI: /admin_1wgrah
```

에서 관리 URI를 볼 수도 있습니다 `<magento_root>/app/etc/env.php`. 코드 조각은 다음과 같습니다.

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 관리 URL 변경

관리자 URI를 변경하려면 [`magento setup:config:set`](deployment.md) 명령.
