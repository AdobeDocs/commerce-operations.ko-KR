---
title: 응용 프로그램 초기화 및 부트스트랩
description: Commerce 애플리케이션의 초기화 및 부트스트랩 논리에 대해 읽어보십시오.
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# 초기화 및 부트스트랩 개요

Commerce 응용 프로그램을 실행하려면 [pub/index.php](https://github.com/magento/magento2/tree/2.4.8/pub/index.php)에서 다음 작업을 구현합니다.

- 환경에 배포된 Commerce 버전용 [app/bootstrap.php](https://github.com/magento/magento2/blob/2.4.8/app/bootstrap.php) 파일을 포함하십시오. 이 파일은 오류 처리, 자동 로더 초기화, 프로파일링 옵션 설정 및 기본 시간대 설정과 같은 필수 초기화 루틴을 수행합니다.
- [\Magento\Framework\App\Bootstrap.php](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/App/Bootstrap.php) <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->의 인스턴스 만들기
- Commerce 응용 프로그램 인스턴스 만들기: [\Magento\Framework\AppInterface](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/AppInterface.php)
- Commerce 실행

## Bootstrap 실행 논리

[부트스트랩 개체](https://github.com/magento/magento2/tree/2.4.8/app/bootstrap.php)는 다음 알고리즘을 사용하여 Commerce 응용 프로그램을 실행합니다.

1. 오류 핸들러를 초기화합니다.
1. 모든 곳에서 사용되고 환경의 영향을 받는 [개체 관리자](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/ObjectManager) 및 기본 공유 서비스를 만듭니다. 환경 매개 변수는 이러한 개체에 올바르게 삽입됩니다.
1. 유지 관리 모드가 _활성화되지 않음_&#x200B;임을 확인하고 그렇지 않으면 종료됩니다.
1. Commerce 애플리케이션이 설치되어 있다고 주장합니다. 그렇지 않으면 가 종료됩니다.
1. Commerce 애플리케이션을 시작합니다.

   응용 프로그램을 시작하는 동안 발견되지 않은 예외는 예외를 처리하는 데 사용할 수 있는 `catchException()` 메서드의 Commerce으로 자동으로 다시 전달됩니다. 후자는 `true` 또는 `false`을(를) 반환해야 합니다.

   - If `true`: Commerce에서 예외를 처리했습니다. 다른 건 할 필요 없어
   - `false`:(또는 다른 빈 결과)인 경우 Commerce에서 예외를 처리하지 않았습니다. 부트스트랩 객체는 기본 예외 처리 서브루틴을 수행합니다.

1. 응용 프로그램 개체에서 제공한 응답을 보냅니다.

   >[!INFO]
   >
   >Commerce 응용 프로그램이 설치되어 있고 유지 관리 모드가 아니라는 주장은 `\Magento\Framework\App\Bootstrap` 클래스의 기본 동작입니다. 부트스트랩 객체를 작성할 때 진입점 스크립트를 사용하여 수정할 수 있습니다.

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

- [개발자 모드](../bootstrap/application-modes.md#developer-mode)에서 예외를 있는 그대로 표시합니다.
- 다른 모든 모드에서 은 예외를 로그하고 일반 오류 메시지를 표시하려고 합니다.
- 오류 코드 `1`(으)로 Commerce 종료

## 진입점 애플리케이션

다음과 같은 진입점 애플리케이션(즉, 웹 서버에서 디렉토리 인덱스로 사용하는 Commerce에서 정의한 애플리케이션)이 있습니다.

### HTTP 진입점

[\Magento\Framework\App\Http](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/App/Http)은(는) 다음과 같이 작동합니다.

1. [응용 프로그램 영역](https://developer.adobe.com/commerce/php/architecture/modules/areas/)을 결정합니다.
1. 컨트롤러 작업을 찾고 실행하기 위해 프런트 컨트롤러 및 라우팅 시스템을 시작합니다.
1. HTTP 응답 개체를 사용하여 컨트롤러 작업에서 얻은 결과를 반환합니다.
1. 오류 처리(다음 우선 순위 순서로):

   1. [개발자 모드](../bootstrap/application-modes.md#developer-mode)를 사용하는 경우:
      - Commerce 응용 프로그램이 설치되지 않은 경우 설치 마법사로 리디렉션합니다.
      - Commerce 애플리케이션이 설치된 경우 오류 및 HTTP 상태 코드 500(내부 서버 오류)을 표시합니다.
   1. Commerce 애플리케이션이 유지 관리 모드인 경우 HTTP 상태 코드 503(서비스 이용 불가)과 함께 사용자에게 친숙한 &quot;서비스 이용 불가&quot; 랜딩 페이지를 표시합니다.
   1. Commerce 응용 프로그램이 _설치되지 않은_&#x200B;경우 설치 마법사로 리디렉션합니다.
   1. 세션이 유효하지 않으면 홈 페이지로 리디렉션합니다.
   1. 다른 응용 프로그램 초기화 오류가 있는 경우 HTTP 상태 코드 404(찾을 수 없음)와 함께 사용자에게 친숙한 &quot;페이지를 찾을 수 없음&quot; 페이지를 표시합니다.
   1. 다른 모든 오류에서 HTTP 응답 503이 있는 사용자에게 친숙한 &quot;서비스 사용할 수 없음&quot; 페이지를 표시하고 오류 보고서를 생성하고 해당 ID를 페이지에 표시합니다.

### 정적 리소스 진입점

[\Magento\Framework\App\StaticResource](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/App/StaticResource.php)은(는) 정적 리소스(예: CSS, JavaScript 및 이미지)를 검색하는 응용 프로그램입니다. 리소스를 요청할 때까지 정적 리소스로 작업을 연기합니다.

>[!INFO]
>
>정적 보기 파일의 진입점은 서버에서 발생할 수 있는 악용을 방지하기 위해 [프로덕션 모드](application-modes.md#production-mode)에서 사용되지 않습니다. 프로덕션 모드에서 Commerce 응용 프로그램에서는 필요한 모든 리소스가 `<your Commerce install dir>/pub/static` 디렉터리에 있을 것으로 예상합니다.

기본 또는 개발자 모드에서 존재하지 않는 정적 리소스에 대한 요청은 해당 `.htaccess`에 의해 지정된 재작성 규칙에 따라 정적 진입점으로 리디렉션됩니다.
요청이 진입점으로 리디렉션되면 Commerce 애플리케이션은 검색된 매개변수를 기반으로 요청된 URL을 구문 분석하고 요청된 리소스를 찾습니다.

- [developer](application-modes.md#developer-mode) 모드에서 리소스의 콘텐츠를 반환하여 리소스를 요청할 때마다 반환된 콘텐츠가 최신 상태가 되도록 합니다.
- [기본](application-modes.md#default-mode) 모드에서 검색된 리소스가 게시되므로 이전에 요청한 URL로 액세스할 수 있습니다.

  정적 리소스에 대한 모든 향후 요청은 서버에서 정적 파일과 동일한 방식으로 처리됩니다. 즉, 진입점을 포함하지 않습니다. 게시된 파일을 원본 파일과 동기화해야 하는 경우 `pub/static` 디렉터리를 제거해야 합니다. 따라서 다음 요청과 함께 파일이 자동으로 다시 게시됩니다.

### 미디어 리소스 진입점

[Magento\MediaStorage\App\Media](https://github.com/magento/magento2/tree/2.4.8/app/code/Magento/MediaStorage/App/Media.php)은(는) 데이터베이스에서 미디어 리소스(즉, 미디어 저장소에 업로드된 모든 파일)를 검색합니다. 데이터베이스가 미디어 스토리지로 구성될 때마다 사용됩니다.

`\Magento\Core\App\Media`이(가) 구성된 데이터베이스 저장소에서 미디어 파일을 찾아 `pub/static` 디렉터리에 쓴 다음 내용을 반환합니다. 오류가 발생하면 콘텐츠가 없는 헤더에서 HTTP 404(찾을 수 없음) 상태 코드를 반환합니다.

