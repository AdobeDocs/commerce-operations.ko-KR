---
title: 애플리케이션 모드
description: Commerce 애플리케이션은 필요에 따라 다른 모드로 작동할 수 있습니다. 사용 가능한 애플리케이션 모드의 세부 목록을 봅니다.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: c415c3427f513255b9d4ebe1d24ba4024df21928
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# 애플리케이션 모드

다음 _모드_ 중 하나로 Commerce 응용 프로그램을 실행할 수 있습니다.

| 모드 이름 | 설명 | 클라우드 지원 |
| ------------------------ | ------------------- | ------------- |
| [기본값](#default-mode) | 설정을 변경하지 않고 단일 서버에서 Commerce 애플리케이션을 배포하고 실행합니다. _프로덕션에 최적화되지 않음_. | 아니요 |
| [개발자](#developer-mode) | Commerce 애플리케이션을 확장하거나 사용자 지정할 때 개발에 이상적입니다. | 아니요 |
| [프로덕션](#production-mode) | Commerce 애플리케이션을 프로덕션 시스템에 배포하고 실행합니다. | 예 |
| [유지 관리](#maintenance-mode) | 업데이트 및 구성을 수행하는 동안 사이트에 대한 액세스를 차단합니다. | 예 |

Adobe Commerce 작업 모드를 수동으로 변경하는 방법에 대해 알아보려면 [작업 모드 설정](../cli/set-mode.md)을 참조하십시오.

## 클라우드 지원

읽기 전용 파일 시스템으로 인해 원격 클라우드 환경의 모드 변경에 대한 엄격한 제한이 있으며 Adobe Commerce 지원으로 재정의할 수 없습니다. `app/etc/env.php` 패키지가 여러 구성 소스를 기반으로 파일을 덮어쓰므로 `ece-tools` 파일을 수정하여 모드를 변경하지 마십시오.

클라우드 인프라의 Adobe Commerce은 배포 중에 _유지 관리_ 모드로 응용 프로그램을 자동으로 실행하며, 배포가 완료될 때까지 사이트를 오프라인으로 전환합니다. 그렇지 않으면 응용 프로그램이 _프로덕션_ 모드로 유지됩니다. [Commerce on Cloud Infrastructure 안내서](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase)의 _배포 프로세스_&#x200B;를 참조하십시오.

Commerce용 Cloud Docker를 개발 도구로 사용하는 경우 _개발자_ 모드의 Docker 환경에서 클라우드 인프라 프로젝트를 배포할 수 있지만 추가 파일 동기화 작업으로 인해 성능이 느려집니다. [Commerce용 Cloud Docker 안내서](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode)에서 _Docker 환경 배포_&#x200B;를 참조하십시오.


## 기본 모드

_기본_ 모드를 사용하면 설정을 변경하지 않고 단일 서버에 Commerce 응용 프로그램을 배포할 수 있습니다. 그러나 정적 파일의 성능에 부정적인 영향을 주기 때문에 기본 모드는 프로덕션에 최적화되지 않습니다. 정적 파일을 만들고 캐시하는 것은 정적 파일 만들기 도구를 사용하여 만드는 것보다 성능에 더 큰 영향을 줍니다.

기본 모드에서:

- 표시 대신 로그 파일에 예외가 기록됩니다.
- 정적 보기 파일이 캐시됨
- 사용자 지정 `X-Magento-*` HTTP 요청 및 응답 헤더를 숨깁니다

다른 모드가 지정되지 않은 경우 Commerce은 기본 모드로 작동합니다.

## 개발자 모드

Commerce 응용 프로그램을 확장하고 맞춤화하려면 _developer_ 모드를 사용하는 것이 좋습니다. 정적 보기 파일은 캐시되지 않지만 필요할 때 `pub/static` 디렉터리에 기록됩니다.

개발자 모드에서:

- [자동 코드 컴파일](../cli/code-compiler.md) 및 향상된 디버깅 사용
- 발견되지 않은 예외가 브라우저에 표시됨
- `var/report`의 시스템 로깅이 세부 정보입니다
- 기록되지 않고 오류 처리기에서 예외가 발생합니다
- 이벤트 구독자를 호출할 수 없는 경우 예외가 발생합니다
- 사용자 지정 `X-Magento-*` HTTP 요청 및 응답 헤더를 표시합니다.

>[!NOTE]
>
>이 모드는 Adobe Commerce 클라우드 환경에서 지원되지 않으며 Adobe Commerce 지원에서 애플리케이션 모드를 쉽게 변경할 수 없습니다.

## 프로덕션 모드

_프로덕션_ 모드는 프로덕션 시스템에 Commerce 응용 프로그램을 배포하는 데 가장 적합합니다. 데이터베이스 및 웹 서버와 같은 서버 환경을 최적화한 후에는 [정적 보기 파일 배포 도구](../cli/static-view-file-deployment.md)를 실행하여 `pub/static` 디렉터리에 정적 보기 파일을 써야 합니다. 이렇게 하면 Commerce 애플리케이션이 런타임 중에 필요할 때 정적 파일을 동적으로 찾아서 복사(구체화)하는 대신 배포 시 필요한 모든 정적 파일을 제공하여 성능을 향상시킬 수 있습니다.

일부 필드(예: 관리자의 고급 및 개발자 시스템 구성 섹션)는 프로덕션 모드에서 사용할 수 없습니다. 예를 들어, _관리자를 사용하여 캐시 유형을 활성화 또는 비활성화할 수 없습니다_. _명령줄_&#x200B;을 사용하여 캐시 유형 [only](../cli/manage-cache.md#config-cli-subcommands-cache-en)을(를) 활성화하거나 비활성화할 수 있습니다.

프로덕션 모드에서:

- 정적 보기 파일은 캐시에서만 제공됩니다.
- 오류 및 예외는 파일 시스템에 기록되며 사용자에게 표시되지 않습니다
- 관리자의 일부 구성 필드를 사용할 수 없습니다.

## 유지 관리 모드

_유지 관리_ 모드에서는 개선, 업데이트 및 구성 작업 중에 사이트 액세스를 제한하거나 금지합니다. 기본적으로 사이트는 방문자를 기본 `Service Temporarily Unavailable` 페이지로 리디렉션합니다.

[사용자 지정 유지 관리 페이지](../../upgrade/troubleshooting/maintenance-mode-options.md)를 만들고, 유지 관리 모드를 수동으로 활성화 및 비활성화하고, 인증된 IP 주소의 방문자가 저장소를 정상적으로 볼 수 있도록 유지 관리 모드를 구성할 수 있습니다. [설치 가이드](../../installation/tutorials/maintenance-mode.md)에서 _유지 관리 모드 사용 및 사용 안 함_&#x200B;을 참조하세요.

클라우드 인프라에서 Commerce을 사용하는 경우 Commerce 애플리케이션은 배포 단계 동안 유지 관리 모드에서 실행됩니다. 배포가 정상적으로 완료되면 Commerce 애플리케이션은 프로덕션 모드로 다시 실행됩니다. [Cloud Infrastructure의 Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks)에서 _배포 후크_&#x200B;을(를) 참조하십시오.

유지 관리 모드에서:

- 사이트 방문자가 기본 `Service Temporarily Unavailable` 페이지로 리디렉션됩니다.
- `var/` 디렉터리에 `.maintenance.flag` 파일이 있습니다.
- IP 주소를 기반으로 방문자 액세스를 제한할 수 있습니다
