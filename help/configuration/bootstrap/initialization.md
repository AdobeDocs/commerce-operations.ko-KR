---
title: 애플리케이션 초기화 및 부트스트랩
description: Commerce 응용 프로그램의 초기화 및 부트스트랩 로직에 대해 읽어 보십시오.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---


# 초기화 및 부트스트랩 개요

상거래 응용 프로그램을 실행하려면 다음 작업이에 구현됩니다 [pub/index.php][index]:

- 포함 [app/bootstrap.php][bootinitial]- 오류 처리, 자동 로더 초기화, 프로파일링 옵션 설정 및 기본 시간대 설정과 같은 필수 초기화 루틴을 수행합니다.
- 의 인스턴스 만들기 [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- 전자 상거래 응용 프로그램 인스턴스 만들기: [\Magento\Framework\AppInterface][app-face]
- 상거래 실행

## Bootstrap 실행 논리

[부트스트랩 개체][bootinitial] 다음 알고리즘을 사용하여 Commerce 응용 프로그램을 실행합니다.

1. 오류 처리기를 초기화합니다.
1. 를 생성합니다. [개체 관리자][object] 및 어디에서나 사용되고 환경의 영향을 받는 기본 공유 서비스. 환경 매개 변수가 이러한 객체에 제대로 삽입됩니다.
1. 유지 관리 모드가 _not_ 활성화됨 그렇지 않으면 가 종료됩니다.
1. 상거래 응용 프로그램이 설치되어 있다고 가정합니다. 그렇지 않으면 가 종료됩니다.
1. 상거래 애플리케이션을 시작합니다.

   애플리케이션 실행 중에 발견되지 않은 모든 예외가 의 Commerce로 자동 전달됩니다 `catchException()` 예외를 처리하는 데 사용할 수 있는 메서드입니다. 후자도 반환해야 합니다 `true` 또는 `false`:

   - If `true`: 전자 상거래 처리 예외가 발생했습니다. 더 이상 할 필요가 없습니다.
   - If `false`: (또는 다른 빈 결과) Commerce에서 예외를 처리하지 않았습니다. 부트스트랩 개체는 기본 예외 처리 하위 루틴을 수행합니다.

1. 응용 프로그램 개체에서 제공하는 응답을 보냅니다.

   >[!INFO]
   >
   >Commerce 응용 프로그램이 설치되고 유지 관리 모드가 아닌 것을 확인하는 것은 `\Magento\Framework\App\Bootstrap` 클래스 이름을 지정합니다. 부트스트랩 개체를 만들 때 시작 지점 스크립트를 사용하여 수정할 수 있습니다.

   부트스트랩 개체를 수정하는 샘플 시작 지점 스크립트:

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

부트스트랩 개체는 상거래 응용 프로그램에서 처리할 수 없는 예외를 다음과 같이 처리하는 방법을 지정합니다.

- in [개발자 모드](../bootstrap/application-modes.md#developer-mode)는 예외를 있는 그대로 표시합니다.
- 다른 모드에서는 는 예외를 기록하고 일반 오류 메시지를 표시합니다.
- 오류 코드와 함께 상거래를 종료합니다. `1`

## 시작 지점 애플리케이션

다음과 같은 시작 지점 응용 프로그램(즉, 웹 서버에서 디렉터리 인덱스로 사용하는 상거래에 의해 정의된 응용 프로그램)이 있습니다.

### HTTP 시작 지점

[\Magento\Framework\App\Http][http] 는 다음과 같이 작동합니다.

1. 을(를) 결정합니다 [애플리케이션 영역](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. 컨트롤러 작업을 찾아 실행하기 위해 앞면 컨트롤러 및 라우팅 시스템을 시작합니다.
1. HTTP 응답 개체를 사용하여 컨트롤러 작업에서 얻은 결과를 반환합니다.
1. 오류 처리(다음 우선순위 순서로):

   1. 사용 중인 경우 [개발자 모드](../bootstrap/application-modes.md#developer-mode):
      - 상거래 응용 프로그램이 설치되어 있지 않으면 설치 마법사로 리디렉션합니다.
      - 상거래 응용 프로그램이 설치되어 있으면 오류 및 HTTP 상태 코드 500(내부 서버 오류)을 표시합니다.
   1. 상거래 응용 프로그램이 유지 관리 모드에 있는 경우 HTTP 상태 코드 503(서비스를 사용할 수 없음)이 있는 사용자에게 친숙한 &quot;서비스를 사용할 수 없음&quot; 랜딩 페이지를 표시합니다.
   1. 상거래 애플리케이션이 _not_ 설치된 경우 설치 마법사로 리디렉션합니다.
   1. 세션이 잘못된 경우 홈 페이지로 리디렉션합니다.
   1. 다른 응용 프로그램 초기화 오류가 있는 경우 HTTP 상태 코드 404(찾을 수 없음)가 있는 사용자에게 친숙한 &quot;페이지를 찾을 수 없음&quot; 페이지를 표시합니다.
   1. 다른 오류 시 HTTP 응답 503이 있는 사용자에게 친숙한 &quot;서비스를 사용할 수 없음&quot; 페이지를 표시하고 오류 보고서를 생성하고 해당 ID를 페이지에 표시합니다.

### 정적 리소스 진입점

[\Magento\Framework\App\StaticResource][static-resource] 정적 리소스(예: CSS, JavaScript 및 이미지)를 검색하기 위한 애플리케이션입니다. 리소스가 요청될 때까지 정적 리소스로 작업을 연기합니다.

>[!INFO]
>
>정적 보기 파일의 진입점은 [프로덕션 모드](application-modes.md#production-mode) 잠재적인 서버 공격을 방지합니다. 프로덕션 모드에서는 Commerce 응용 프로그램은 필요한 모든 리소스가 `<your Commerce install dir>/pub/static` 디렉토리.

기본 또는 개발자 모드에서는 존재하지 않는 정적 리소스에 대한 요청이 적절하게 지정된 재작성 규칙에 따라 정적 시작 지점으로 리디렉션됩니다 `.htaccess`.
요청이 시작 지점으로 리디렉션되면 상거래 애플리케이션은 검색된 매개 변수를 기반으로 요청된 URL을 구문 분석하고 요청된 리소스를 찾습니다.

- in [개발자](application-modes.md#developer-mode) 모드에서는 리소스가 요청될 때마다 반환된 컨텐츠가 최신 상태로 표시되도록 파일의 컨텐츠가 반환됩니다.
- in [기본](application-modes.md#default-mode) 모드에서는 이전에 요청한 URL로 액세스할 수 있도록 검색된 리소스가 게시됩니다.

   향후 정적 리소스에 대한 모든 요청은 서버에서 정적 파일과 동일하게 처리됩니다. 즉, 진입점을 포함하지 않습니다. 게시된 파일을 원래 파일과 동기화해야 하는 경우 `pub/static` 디렉터리를 제거해야 합니다. 그 결과, 파일은 다음 요청과 함께 자동으로 다시 게시됩니다.

### 미디어 리소스 진입점

[Magento\MediaStorage\App\Media][media] 데이터베이스에서 미디어 리소스(즉, 미디어 저장소에 업로드된 모든 파일)를 검색합니다. 데이터베이스가 미디어 저장소로 구성될 때마다 사용됩니다.

`\Magento\Core\App\Media` 구성된 데이터베이스 저장소에서 미디어 파일을 찾아서 `pub/static` 디렉토리 안에 있는 다음 해당 컨텐츠를 반환합니다. 오류가 발생하면 헤더에서 내용이 없는 HTTP 404(찾을 수 없음) 상태 코드를 반환합니다.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
