---
title: X-Frame-Options 헤더
description: X-Frame-Options를 사용하여 페이지 렌더링을 제어합니다.
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# X-Frame-Options 헤더

을 방지하는 데 도움이 됩니다 [클릭재킹](https://owasp.org/www-community/attacks/Clickjacking) 악용, 다음을 사용할 옵션을 추가했습니다. [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) storefront에 대한 요청의 HTTP 요청 헤더입니다.

다음 `X-Frame-Options` 헤더를 사용하면 브라우저에서 페이지를 렌더링할 수 있는지 여부를 지정할 수 있습니다. `<frame>`, `<iframe>`, 또는 `<object>` 다음과 같이:

- `DENY`: 프레임에 페이지를 표시할 수 없습니다.
- `SAMEORIGIN`: (기본값) 페이지 자체와 동일한 원점의 프레임에만 페이지를 표시할 수 있습니다.

>[!WARNING]
>
>다음 `ALLOW-FROM <uri>` 옵션은 Commerce에서 지원하는 브라우저에서 더 이상 지원하지 않으므로 더 이상 사용되지 않습니다. 다음을 참조하십시오 [브라우저 호환성](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>보안상의 이유로 Adobe에서는 프레임에서 Commerce 저장소를 실행하지 않는 것이 좋습니다.

## 구현 `X-Frame-Options`

다음에 대한 값 설정 `X-Frame-Options` 위치: `<project-root>/app/etc/env.php`. 기본값은 다음과 같이 설정됩니다.

```php
'x-frame-options' => 'SAMEORIGIN',
```

를 변경할 수 있도록 재배포 `env.php` 적용할 파일입니다.

>[!TIP]
>
>를 편집하는 것이 더 안전합니다. `env.php` 파일 : 관리자에서 값을 설정하는 데 사용됩니다.

## 에 대한 설정 확인 `X-Frame-Options`

설정을 확인하려면 모든 storefront 페이지에서 HTTP 헤더를 확인하십시오. 웹 브라우저 검사기를 사용하는 등 몇 가지 방법으로 이 작업을 수행할 수 있습니다.

다음 예제에서는 HTTP 프로토콜을 통해 Commerce 서버에 연결할 수 있는 모든 컴퓨터에서 실행할 수 있는 curl을 사용합니다.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

다음 항목을 찾습니다. `X-Frame-Options` 머리글의 값입니다.
