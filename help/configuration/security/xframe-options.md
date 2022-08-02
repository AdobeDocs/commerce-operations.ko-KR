---
title: X-Frame-Options 헤더
description: X-Frame-Options를 사용하여 페이지 렌더링을 제어합니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# X-Frame-Options 헤더

예방하려면 [클릭 추적](https://owasp.org/www-community/attacks/Clickjacking) 유용한 정보, [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) 스토어에 대한 요청의 HTTP 요청 헤더입니다.

다음 `X-Frame-Options` 헤더를 사용하면 브라우저에서 페이지를 렌더링할 수 있는지 여부를 지정할 수 있습니다 `<frame>`, `<iframe>`, 또는 `<object>` 아래와 같이 변경하는 것을 의미합니다.

- `DENY`: 프레임에 페이지를 표시할 수 없습니다.
- `SAMEORIGIN`: (기본값) 페이지 자체와 동일한 원점의 프레임에만 페이지를 표시할 수 있습니다.

>[!WARNING]
>
>다음 `ALLOW-FROM <uri>` 커머스 지원 브라우저가 이 옵션을 더 이상 지원하지 않으므로 이 선택 사항이 더 이상 사용되지 않습니다. 자세한 내용은 [브라우저 호환성](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>보안상의 이유로 Adobe은 프레임에서 상거래 저장소를 실행하지 않는 것을 강력히 권장합니다.

## 구현 `X-Frame-Options`

값 설정 `X-Frame-Options` in `<magento_root>/app/etc/env.php`. 기본값은 다음과 같습니다.

```php
'x-frame-options' => 'SAMEORIGIN',
```

>[!TIP]
>
>를 편집하는 것은 더 안전합니다 `env.php` 파일에서 로 설정하는 것이 아니라, 관리자에서 값을 설정하는 것입니다.

## 설정 확인 `X-Frame-Options`

설정을 확인하려면 저장소 전면 페이지에서 HTTP 헤더를 봅니다. 웹 브라우저 관리자를 사용하는 등 여러 가지 방법으로 이 작업을 수행할 수 있습니다.

다음 예제에서는 HTTP 프로토콜을 통해 Commerce 서버에 연결할 수 있는 모든 컴퓨터에서 실행할 수 있는 curl을 사용합니다.

다음 명령을 사용합니다.

```bash
curl -I -v --location-trusted '<your storefront URL>'
```

을(를) 찾습니다. `X-Frame-Options` 값을 지정한 경우 이해할 수 있도록 해줍니다.
