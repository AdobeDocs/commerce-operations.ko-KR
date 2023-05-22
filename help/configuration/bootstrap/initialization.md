---
title: 응용 프로그램 초기화 및 부트스트랩
description: Commerce 애플리케이션의 초기화 및 부트스트랩 논리에 대해 읽어보십시오.
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# 초기화 및 부트스트랩 개요

Commerce 응용 프로그램을 실행하기 위해에서 다음 작업이 구현됩니다. [pub/index.php][index]:

- 포함 [app/bootstrap.php][bootinitial]오류 처리, 자동 로더 초기화, 프로파일링 옵션 설정 및 기본 시간대 설정과 같은 필수 초기화 루틴을 수행합니다.
- 의 인스턴스 만들기 [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- 상거래 애플리케이션 인스턴스 만들기: [\Magento\Framework\AppInterface][app-face]
- 상거래 실행

## Bootstrap 실행 논리

[부트스트랩 객체][bootinitial] 다음 알고리즘을 사용하여 Commerce 응용 프로그램을 실행합니다.

1. 오류 핸들러를 초기화합니다.
1. 다음을 생성합니다. [오브젝트 관리자][object] 및 모든 곳에서 사용되고 환경의 영향을 받는 기본 공유 서비스. 환경 매개 변수는 이러한 개체에 올바르게 삽입됩니다.
1. 유지 관리 모드가 _아님_ enabled; 그렇지 않으면 가 종료됩니다.
1. Commerce 응용 프로그램이 설치되었다고 주장합니다. 그렇지 않으면 가 종료됩니다.
1. 상거래 응용 프로그램을 시작합니다.

   응용 프로그램을 시작하는 동안 발견되지 않은 모든 예외는 `catchException()` 예외를 처리하는 데 사용할 수 있는 메서드. 후자는 다음 중 하나를 반환해야 합니다. `true` 또는 `false`:

   - If `true`: Commerce에서 예외를 처리했습니다. 다른 건 할 필요 없어
   - If `false`: (또는 다른 빈 결과) Commerce가 예외를 처리하지 않았습니다. 부트스트랩 객체는 기본 예외 처리 서브루틴을 수행합니다.

1. 응용 프로그램 개체에서 제공한 응답을 보냅니다.

   >[!INFO]
   >
   >Commerce 응용 프로그램이 설치되어 있고 유지 관리 모드에 있지 않다는 주장은 의 기본 동작입니다. `\Magento\Framework\App\Bootstrap` 클래스. 부트스트랩 객체를 작성할 때 진입점 스크립트를 사용하여 수정할 수 있습니다.

   부트스트랩 객체를 수정하는 샘플 진입점 스크립트:

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## 기본 예외 처리

부트스트랩 객체는 다음과 같이 Commerce 애플리케이션이 catch되지 않은 예외를 처리하는 방법을 지정합니다.

- 위치 [개발자 모드](../bootstrap/application-modes.md#developer-mode)를 입력하면 예외를 있는 그대로 표시합니다.
- 다른 모든 모드에서 은 예외를 로그하고 일반 오류 메시지를 표시하려고 합니다.
- 오류 코드로 Commerce 종료 `1`

## 진입점 애플리케이션

다음과 같은 진입점 응용 프로그램(즉, 웹 서버에서 디렉터리 인덱스로 사용하는 Commerce에서 정의한 응용 프로그램)이 있습니다.

### HTTP 진입점

[\Magento\Framework\App\Http][http] 는 다음과 같이 작동합니다.

1. 다음을 결정합니다. [응용 프로그램 영역](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. 컨트롤러 작업을 찾고 실행하기 위해 프런트 컨트롤러 및 라우팅 시스템을 시작합니다.
1. HTTP 응답 개체를 사용하여 컨트롤러 작업에서 얻은 결과를 반환합니다.
1. 오류 처리(다음 우선 순위 순서로):

   1. 을 사용하는 경우 [개발자 모드](../bootstrap/application-modes.md#developer-mode):
      - Commerce 응용 프로그램이 설치되지 않은 경우 설치 마법사로 리디렉션합니다.
      - Commerce 응용 프로그램이 설치된 경우 오류 및 HTTP 상태 코드 500(내부 서버 오류)을 표시합니다.
   1. Commerce 애플리케이션이 유지 관리 모드인 경우 HTTP 상태 코드 503(서비스 사용 불가)과 함께 사용자에게 친숙한 &quot;서비스 사용 불가&quot; 랜딩 페이지를 표시합니다.
   1. Commerce 애플리케이션이 _아님_ 설치되었습니다. 설치 마법사로 리디렉션합니다.
   1. 세션이 유효하지 않으면 홈 페이지로 리디렉션합니다.
   1. 다른 응용 프로그램 초기화 오류가 있는 경우 HTTP 상태 코드 404(찾을 수 없음)와 함께 사용자에게 친숙한 &quot;페이지를 찾을 수 없음&quot; 페이지를 표시합니다.
   1. 다른 모든 오류에서 HTTP 응답 503이 있는 사용자에게 친숙한 &quot;서비스 사용할 수 없음&quot; 페이지를 표시하고 오류 보고서를 생성하고 해당 ID를 페이지에 표시합니다.

### 정적 리소스 진입점

[\Magento\Framework\App\StaticResource][static-resource] 는 정적 리소스(예: CSS, JavaScript 및 이미지)를 검색하기 위한 애플리케이션입니다. 리소스를 요청할 때까지 정적 리소스로 작업을 연기합니다.

>[!INFO]
>
>정적 보기 파일의 진입점은 [프로덕션 모드](application-modes.md#production-mode) 서버에서 잠재적인 사용을 방지하기 위해. 프로덕션 모드에서 Commerce 애플리케이션은 모든 필수 리소스가에 존재할 것으로 예상합니다. `<your Commerce install dir>/pub/static` 디렉토리.

기본 또는 개발자 모드에서 존재하지 않는 정적 리소스에 대한 요청은 해당하는 사용자가 지정한 재작성 규칙에 따라 정적 진입점으로 리디렉션됩니다 `.htaccess`.
요청이 진입점으로 리디렉션되면 Commerce 애플리케이션은 검색된 매개변수를 기반으로 요청된 URL을 구문 분석하고 요청된 리소스를 찾습니다.

- 위치 [개발자](application-modes.md#developer-mode) 모드에서 파일의 콘텐츠가 반환되어 리소스를 요청할 때마다 반환된 콘텐츠가 최신 상태가 됩니다.
- 위치 [기본값](application-modes.md#default-mode) 모드에서는 검색된 리소스가 게시되므로 이전에 요청한 URL에서 액세스할 수 있습니다.

   정적 리소스에 대한 모든 향후 요청은 서버에서 정적 파일과 동일한 방식으로 처리됩니다. 즉, 진입점을 포함하지 않습니다. 게시된 파일을 원본 파일과 동기화해야 하는 경우 `pub/static` 디렉토리가 제거됩니다. 따라서 파일이 다음 요청과 함께 자동으로 다시 게시됩니다.

### 미디어 리소스 진입점

[Magento\MediaStorage\App\Media][media] 데이터베이스에서 미디어 리소스(즉, 미디어 스토리지에 업로드된 모든 파일)를 검색합니다. 데이터베이스가 미디어 스토리지로 구성될 때마다 사용됩니다.

`\Magento\Core\App\Media` 구성된 데이터베이스 저장소에서 미디어 파일을 찾아서 `pub/static` 디렉토리에서 컨텐츠를 반환합니다. 오류가 발생하면 콘텐츠가 없는 헤더에서 HTTP 404(찾을 수 없음) 상태 코드를 반환합니다.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
