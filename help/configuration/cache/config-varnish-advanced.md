---
title: 고급 바니시 구성
description: 상태 확인, 유예 및 saint 모드를 비롯한 Adobe Commerce의 고급 바니시 기능을 구성하는 방법에 대해 알아봅니다. VCL 최적화 기술을 살펴보십시오.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 0%

---

# 고급 바니시 구성

Vannish는 Commerce 서버가 제대로 작동하지 않을 때 고객이 긴 지연 및 시간 초과를 겪지 않도록 하는 몇 가지 기능을 제공합니다. 이러한 기능은 `default.vcl` 파일에서 구성할 수 있습니다. 이 항목에서는 Commerce이 관리자로부터 다운로드한 VCL(Varnish 구성 언어) 파일에 제공하는 추가 기능에 대해 설명합니다.

바니시 구성 언어 사용에 대한 자세한 내용은 [바니시 참조 설명서](https://varnish-cache.org/docs/index.html)를 참조하십시오.

## 상태 검사

니스 상태 검사 기능은 Commerce 서버를 폴링하여 적시에 응답하는지 여부를 확인합니다. 정상적으로 응답하는 경우 TTL(Time to Live) 기간이 만료된 후 새 콘텐츠가 다시 생성됩니다. 그렇지 않은 경우, 바니쉬는 항상 진부한 내용물을 제공합니다.

Commerce은 다음과 같은 기본 상태 검사를 정의합니다.

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

이 상태 검사는 5초마다 `pub/health_check.php` 스크립트를 호출합니다. 이 스크립트는 서버, 각 데이터베이스 및 Redis(설치된 경우)의 가용성을 확인합니다. 스크립트는 2초 이내에 응답을 반환해야 합니다. 스크립트가 이러한 리소스가 모두 다운된 것으로 판단되면 500 HTTP 오류 코드를 반환합니다. 이 오류 코드가 10번 시도 중 6번 시도에서 수신되면 백엔드가 비정상으로 간주됩니다.

`health_check.php` 스크립트가 `pub` 디렉터리에 있습니다. Commerce 루트 디렉터리가 `pub`인 경우 `url` 매개 변수의 경로를 `/pub/health_check.php`에서 `health_check.php`(으)로 변경해야 합니다.

자세한 내용은 [바니시 상태 검사](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks) 설명서를 참조하십시오.

## 유예 모드

유예 모드를 사용하면 Vannish에서 객체를 TTL 값 이상으로 캐시에 유지할 수 있습니다. 그런 다음 새 버전을 가져오는 동안 바니시가 만료된(오래된) 콘텐츠를 제공할 수 있습니다. 이렇게 하면 트래픽 흐름이 개선되고 로드 시간이 줄어듭니다. 다음과 같은 경우에 사용됩니다.

- Commerce 백엔드가 정상이지만 요청이 평소보다 오래 걸리는 경우
- Commerce 백엔드가 정상이 아닌 경우.

`vcl_hit` 서브루틴은 Vannish가 캐시된 개체에 대한 요청에 응답하는 방식을 정의합니다.

### Commerce 백엔드가 정상 상태인 경우

상태 검사에서 Commerce 백엔드가 정상으로 확인되면 Vannish는 유예 기간에 시간이 남아 있는지 확인합니다. 기본 유예 기간은 300초이지만 판매자는 [바니시를 사용하도록 Commerce 구성](configure-varnish-commerce.md)에 설명된 대로 관리자의 값을 설정할 수 있습니다. 유예 기간이 만료되지 않은 경우 Vannish는 오래된 콘텐츠를 전달하고 Commerce 서버에서 개체를 비동기적으로 새로 고칩니다. 유예 기간이 만료된 경우 Vannish는 오래된 콘텐츠를 제공하고 Commerce 백엔드에서 개체를 동기적으로 새로 고칩니다.

Varnish가 오래된 오브젝트를 제공하는 최대 시간은 유예 기간(기본적으로 300초)과 TTL 값(기본적으로 86400초)의 합입니다.

`default.vcl` 파일 내에서 기본 유예 기간을 변경하려면 `vcl_hit` 서브루틴에서 다음 줄을 편집하십시오.

```conf
if (obj.ttl + 300s > 0s) {
```

### Commerce 백엔드가 정상이 아닌 경우

Commerce 백엔드가 응답하지 않으면 Vannish는 캐시된 콘텐츠를 수동으로 삭제하지 않는 한 3일 동안(또는 `beresp.grace`에서 정의된 대로) 캐시에서 오래된 콘텐츠와 나머지 TTL(기본적으로 1일)을 제공합니다.

## Saint 모드

Saint 모드에서는 구성 가능한 시간 동안 비정상 백엔드가 제외됩니다. 따라서 Vannish를 로드 밸런서로 사용할 때는 비정상 백엔드가 트래픽을 제공할 수 없습니다. Saint 모드를 유예 모드와 함께 사용하여 비정상 백엔드 서버를 복잡하게 처리할 수 있습니다. 예를 들어 한 백엔드 서버가 비정상인 경우 다시 시도는 다른 서버로 라우팅될 수 있습니다. 다른 모든 서버가 다운된 경우 오래된 캐시된 개체를 제공합니다. saint 모드 백 엔드 호스트 및 일시 중단 기간은 `default.vcl` 파일에 정의되어 있습니다.

Commerce 사이트의 가용성에 영향을 주지 않고 유지 관리 및 업그레이드 작업을 수행하기 위해 Commerce 인스턴스를 개별적으로 오프라인으로 전환할 때도 SAINT 모드를 사용할 수 있습니다.

### Saint 모드 사전 요구 사항

한 대의 시스템을 기본 설치로 지정합니다. 이 컴퓨터에 Commerce의 주 인스턴스, mySQL 데이터베이스 및 Vannish를 설치합니다.

다른 모든 컴퓨터에서 Commerce 인스턴스는 기본 컴퓨터의 mySQL 데이터베이스에 액세스할 수 있어야 합니다. 보조 시스템은 기본 Commerce 인스턴스의 파일에 액세스할 수도 있습니다.

또는 모든 컴퓨터에서 정적 파일 버전 관리를 해제할 수 있습니다. 이 기능은 **스토어** > 설정 > **구성** > **고급** > **개발자** > **정적 파일 설정** > **정적 파일에 서명** = **아니요**&#x200B;의 관리자로부터 액세스할 수 있습니다.

마지막으로, 모든 Commerce 인스턴스는 프로덕션 모드에 있어야 합니다. Vannish가 시작되기 전에 각 인스턴스의 캐시를 지우십시오. 관리에서 **시스템** > 도구 > **캐시 관리**(으)로 이동한 다음 **Magento 캐시 플러시**&#x200B;를 클릭합니다. 다음 명령을 실행하여 캐시를 지울 수도 있습니다.

```bash
bin/magento cache:flush
```

### 설치

Saint 모드는 기본 Varnish 패키지의 일부가 아닙니다. 다운로드하여 설치해야 하는 별도의 버전 `vmod`입니다. 따라서 현재 사용 중인 Varnish 버전에 대한 [설치 지침](https://varnish-cache.org/docs/index.html)에 설명된 대로 Varnish를 소스에서 다시 컴파일해야 합니다.

다시 컴파일한 후 Saint 모드 모듈을 설치할 수 있습니다. 일반적으로 다음 단계를 수행합니다.

1. [바니시 모듈](https://github.com/varnish/varnish-modules)에서 소스 코드를 가져옵니다. 0.9.x 버전에 소스 코드 오류가 포함되어 있으므로 Git 버전(마스터 버전)을 복제합니다.
1. 자동 도구를 사용하여 소스 코드 작성:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Saint 모드 모듈 설치에 대한 자세한 내용은 [Varnish 모듈 컬렉션](https://github.com/varnish/varnish-modules)을 참조하십시오.

### 샘플 VCL 파일

다음 코드 예제에서는 saint 모드를 활성화하기 위해 VCL 파일에 추가해야 하는 코드를 보여 줍니다. `import` 문 및 `backend` 정의를 파일의 맨 위에 놓습니다.

```cpp
import saintmode;
import directors;

backend default1 {
    .host = "192.168.0.1";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

backend default2 {
    .host = "192.168.0.2";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

sub vcl_init {
    # Instantiate sm1, sm2 for backends tile1, tile2
    # with 10 blacklisted objects as the threshold for marking the
    # whole backend sick.
    new sm1 = saintmode.saintmode(default1, 10);
    new sm2 = saintmode.saintmode(default2, 10);

    # Add both to a director. Use sm0, sm1 in place of tile1, tile2.
    # Other director types can be used in place of random.
    new magedirector = directors.random();
    magedirector.add_backend(sm1.backend(), 1);
    magedirector.add_backend(sm2.backend(), 1);
}

sub vcl_backend_fetch {
    # Get a backend from the director.
    # When returning a backend, the director will only return backends
    # saintmode says are healthy.
    set bereq.backend = magedirector.backend();
}

sub vcl_backend_response {
    if (beresp.status >= 500) {
        # This marks the backend as sick for this specific
        # object for the next 20s.
        saintmode.blacklist(20s);
        # Retry the request. This will result in a different backend
        # being used.
        return (retry);
    }
}
```
