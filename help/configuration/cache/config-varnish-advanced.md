---
title: 고급 변명 구성
description: 상태 확인, 유예 및 saint 모드를 포함한 고급 변명 기능을 구성합니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 0%

---


# 고급 변명 구성

Varnish는 상거래 서버가 제대로 작동하지 않을 때 고객이 긴 지연 및 시간 초과를 경험하는 것을 방지하는 몇 가지 기능을 제공합니다. 이러한 기능은 `default.vcl` 파일. 이 항목에서는 Commerce가 관리자로부터 다운로드한 VCL(Varnish Configuration Language) 파일에서 제공하는 추가 사항에 대해 설명합니다.

자세한 내용은 [Varnish 참조 설명서](https://varnish-cache.org/docs/6.3/reference/index.html) varnish Configuration Language 사용에 대한 자세한 내용을 참조하십시오.

## 상태 검사

Varnish 상태 검사 기능은 Commerce 서버를 폴링하여 적시에 응답하는지 여부를 확인합니다. 정상적으로 응답하는 경우, TTL(Time to Live) 기간이 만료된 후 새 컨텐츠가 다시 생성됩니다. 그렇지 않으면 Varnish는 항상 오래된 컨텐츠를 제공합니다.

Commerce에서는 다음과 같은 기본 상태 검사를 정의합니다.

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

5초마다 이 상태 확인은 `pub/health_check.php` 스크립트. 이 스크립트는 서버, 각 데이터베이스 및 Redis(설치된 경우)의 가용성을 확인합니다. 스크립트는 2초 이내에 응답을 반환해야 합니다. 스크립트는 이러한 리소스 중 하나가 다운되었다고 판단되면 500 HTTP 오류 코드를 반환합니다. 이 오류 코드가 10번 중 6번 수신되면 백엔드가 비정상 상태로 간주됩니다.

다음 `health_check.php` 스크립트는 `pub` 디렉토리. 상거래 루트 디렉터리가 `pub`를 입력한 다음 `url` 매개 변수 `/pub/health_check.php` to `health_check.php`.

자세한 내용은 [바니스 상태 검사](https://varnish-cache.org/docs/6.3/users-guide/vcl-backends.html?highlight=health%20check#health-checks) 설명서.

## 유예 모드

유예 모드를 사용하면 Varnish가 TTL 값 이상을 캐시에 개체를 유지할 수 있습니다. 그런 다음 새 버전을 가져오는 동안 만료된(오래된) 컨텐츠를 제공할 수 있습니다. 이렇게 하면 트래픽 흐름이 개선되고 로드 시간이 줄어듭니다. 이 변수는 다음과 같은 상황에서 사용됩니다.

- 상거래 백엔드가 정상이지만 요청이 정상보다 오래 걸리는 경우
- 상거래 백엔드가 정상이 아닌 경우.

다음 `vcl_hit` 서브루틴은 캐시된 개체에 대한 요청에 응답하는 방법을 정의합니다.

### 상거래 백엔드가 정상인 경우

상태 확인에서 상거래 백엔드가 정상인지 확인하면 Varnish는 시간이 유예 기간에 남아 있는지 확인합니다. 기본 유예 기간은 300초이지만 머천트는 다음에 설명된 대로 관리자에서 값을 설정할 수 있습니다. [Varnish를 사용하도록 상거래 구성](configure-varnish-commerce.md). 유예 기간이 만료되지 않은 경우 Varnish는 오래된 콘텐츠를 전달하고 상거래 서버에서 개체를 비동기적으로 새로 고칩니다. 유예 기간이 만료된 경우 Varnish는 오래된 콘텐츠를 제공하고 Commerce 백엔드에서 개체를 동기적으로 새로 고침합니다.

Varnish에서 오래된 개체를 제공하는 최대 시간은 유예 기간(기본적으로 300초)과 TTL 값(기본적으로 86400초)의 합입니다.

기본 유예 기간을 `default.vcl` 파일에서 다음 줄을 편집합니다. `vcl_hit` 하위 루틴:

```conf
if (obj.ttl + 300s > 0s) {
```

### 상거래 백엔드가 정상이 아닌 경우

상거래 백엔드가 응답하지 않으면 Varnish는 3일 동안(또는 에 정의된 대로) 캐시에서 오래된 콘텐츠를 제공합니다 `beresp.grace`)과 나머지 TTL(기본적으로 1일)을 함께 사용할 수 있습니다. 단, 캐시된 컨텐츠를 수동으로 제거하지 않는 경우에는 이 작업이 수행됩니다.

## Saint 모드

Saint 모드에서는 구성 가능한 시간에 대해 비정상 백엔드를 제외합니다. 따라서 로드 밸런서로 Varnish를 사용할 때는 비정상 백엔드가 트래픽을 제공할 수 없습니다. Saint 모드는 유예 모드에서 사용하여 비정상 백엔드 서버를 복잡한 처리할 수 있습니다. 예를 들어 하나의 백엔드 서버가 비정상 상태인 경우 다시 시도를 다른 서버로 라우팅할 수 있습니다. 다른 모든 서버가 다운된 경우 오래된 캐시된 개체를 제공합니다. SAINT 모드 백엔드 호스트 및 일시 중단 기간은 `default.vcl` 파일.

상거래 사이트의 가용성에 영향을 주지 않고 유지 관리 및 업그레이드 작업을 수행하기 위해 상거래 인스턴스를 개별적으로 오프라인으로 가져오는 경우에도 SAINT 모드를 사용할 수 있습니다.

### Saint 모드 사전 요구 사항

한 컴퓨터를 기본 설치로 지정합니다. 이 컴퓨터에 Commerce, mySQL 데이터베이스 및 Varnish의 기본 인스턴스를 설치합니다.

다른 모든 컴퓨터에서 상거래 인스턴스는 기본 컴퓨터의 mySQL 데이터베이스에 액세스할 수 있어야 합니다. 보조 컴퓨터는 기본 상거래 인스턴스의 파일에도 액세스할 수 있어야 합니다.

또는 모든 시스템에서 정적 파일 버전 관리를 해제할 수 있습니다. 아래의 관리자에서 액세스할 수 있습니다 **스토어** > 설정 > **구성** > **고급** > **개발자** > **정적 파일 설정** > **정적 파일 서명** = **아니요**.

마지막으로 모든 상거래 인스턴스는 프로덕션 모드여야 합니다. Varnish가 시작되기 전에 각 인스턴스의 캐시를 지웁니다. 관리에서 **시스템** > 도구 > **캐시 관리** 을(를) 클릭합니다. **플러시 Magento 캐시**. 다음 명령을 실행하여 캐시를 지울 수도 있습니다.

```bash
bin/magento cache:flush
```

### 설치

Saint 모드는 기본 Varnish 패키지의 일부가 아닙니다. 버전은 따로 관리됩니다 `vmod` 다운로드하여 설치해야 합니다. 따라서 다음 문서에 설명된 대로 소스에서 Varnish를 다시 컴파일해야 합니다.

- [Varnish 6.4 설치](https://varnish-cache.org/docs/6.4/installation/install.html)
- [Varnish 6.0 설치](https://varnish-cache.org/docs/6.0/installation/install.html) (LTS)

다시 컴파일한 후 Saint 모드 모듈을 설치할 수 있습니다. 일반적으로 다음 단계를 수행합니다.

1. 에서 소스 코드 가져오기 [Varnish 모듈](https://github.com/varnish/varnish-modules). 0.9.x 버전에 소스 코드 오류가 포함되어 있으므로 Git 버전(마스터 버전)을 복제합니다.
1. autotools를 사용하여 소스 코드를 작성합니다.

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

자세한 내용은 [Varnish 모듈 컬렉션](https://github.com/varnish/varnish-modules) saint 모드 모듈 설치에 대한 자세한 정보.

### 샘플 VCL 파일

다음 코드 예제에서는 saint 모드를 활성화하기 위해 VCL 파일에 추가해야 하는 코드를 보여 줍니다. 배치 `import` 문 및 `backend` 정의 를 참조하십시오.

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
