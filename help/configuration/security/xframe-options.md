---
title: 클릭재킹 악용 방지
description: '''X-Frame-Options'' 헤더를 사용하여 페이지 렌더링을 제어함으로써 클릭재킹 악용을 방지합니다.'
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 클릭재킹 악용 방지

[X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) HTTP 요청 헤더를 상점 요청에 포함하여 [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) 사용을 방지하십시오.

`X-Frame-Options` 헤더를 사용하면 브라우저에서 `<frame>`, `<iframe>` 또는 `<object>`의 페이지를 렌더링할 수 있는지 여부를 다음과 같이 지정할 수 있습니다.

- `DENY`: 프레임에 페이지를 표시할 수 없습니다.
- `SAMEORIGIN`: (기본값) 페이지 자체와 동일한 원본의 프레임에서만 페이지를 표시할 수 있습니다.

>[!WARNING]
>
>Commerce에서 지원하는 브라우저에서 더 이상 지원하지 않으므로 `ALLOW-FROM <uri>` 옵션은 더 이상 사용되지 않습니다. [브라우저 호환성](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility)을 참조하세요.

>[!WARNING]
>
>보안상의 이유로 Adobe에서는 프레임에서 Commerce 스토어프론트를 실행하지 않는 것이 좋습니다.

## `X-Frame-Options` 구현

`<project-root>/app/etc/env.php`에서 `X-Frame-Options`의 값을 설정하십시오. 기본값은 다음과 같이 설정됩니다.

```php
'x-frame-options' => 'SAMEORIGIN',
```

`env.php` 파일에 대한 변경 내용을 적용하려면 다시 배포하십시오.

>[!TIP]
>
>`env.php` 파일을 편집하는 것이 관리자의 값을 설정하는 것보다 안전합니다.

## `X-Frame-Options`에 대한 설정 확인

설정을 확인하려면 모든 storefront 페이지에서 HTTP 헤더를 확인하십시오. 웹 브라우저 검사기를 사용하는 등 몇 가지 방법으로 이 작업을 수행할 수 있습니다.

다음 예제에서는 HTTP 프로토콜을 통해 Commerce 서버에 연결할 수 있는 모든 컴퓨터에서 실행할 수 있는 curl을 사용합니다.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

헤더에서 `X-Frame-Options` 값을 찾습니다.
