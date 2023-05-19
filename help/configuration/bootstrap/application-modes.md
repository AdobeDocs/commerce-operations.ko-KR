---
title: 애플리케이션 모드
description: Commerce 응용 프로그램은 필요에 따라 다른 모드에서 작동 할 수 있습니다. 사용 가능한 애플리케이션 모드의 세부 목록을 봅니다.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---

# 애플리케이션 모드

다음 중 하나에서 Commerce 응용 프로그램을 실행할 수 있습니다 _모드_:

| 모드 이름 | 설명 | 클라우드 지원 |
| ------------------------ | ------------------- | ------------- |
| [기본값](#default-mode) | 설정을 변경하지 않고 단일 서버에서 Commerce 애플리케이션을 배포하고 실행합니다. _아님_ 프로덕션에 최적화되었습니다. | 아니요 |
| [개발자](#developer-mode) | Commerce 응용 프로그램을 확장하거나 사용자 지정할 때 개발에 이상적입니다. | 아니요 |
| [production](#production-mode) | 프로덕션 시스템에 Commerce 응용 프로그램을 배포하고 실행합니다. | 예 |
| [유지 보수](#maintenance-mode) | 업데이트 및 구성을 수행하는 동안 사이트에 대한 액세스를 차단합니다. | 예 |

다음을 참조하십시오 [작업 모드 설정](../cli/set-mode.md) Adobe Commerce 작업 모드를 수동으로 변경하는 방법을 알아봅니다.

## 클라우드 지원

클라우드 인프라 프로젝트에 대한 애플리케이션 모드를 관리할 필요가 없습니다. 읽기 전용 파일 시스템 때문에 원격 클라우드 환경에서는 모드를 변경할 수 없습니다. 클라우드 인프라의 Adobe Commerce은에서 애플리케이션을 자동으로 실행합니다. _유지 보수_ 배포 시 모드: 배포가 완료될 때까지 사이트를 오프라인으로 전환합니다. 그렇지 않으면 응용 프로그램은에 유지됩니다. _production_ 모드. 다음을 참조하십시오 [배포 프로세스](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) 다음에서 _클라우드 인프라의 Commerce 안내서_.

Cloud Docker for Commerce를 개발 도구로 사용하는 경우 의 도커 환경에 클라우드 인프라 프로젝트를 배포할 수 있습니다. _개발자_ 모드이지만 추가 파일 동기화 작업으로 인해 성능이 느려집니다. 다음을 참조하십시오 [Docker 환경 배포](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) 다음에서 _Commerce용 Cloud Docker 안내서_.

## 기본 모드

다음 _기본값_ 모드를 사용하면 설정을 변경하지 않고 단일 서버에 Commerce 애플리케이션을 배포할 수 있습니다. 그러나 정적 파일의 성능에 부정적인 영향을 주기 때문에 기본 모드는 프로덕션에 최적화되지 않습니다. 정적 파일을 만들고 캐시하는 것은 정적 파일 만들기 도구를 사용하여 만드는 것보다 성능에 더 큰 영향을 줍니다.

기본 모드에서:

- 표시 대신 로그 파일에 예외가 기록됩니다.
- 정적 보기 파일이 캐시됨
- 사용자 지정 숨기기 `X-Magento-*` HTTP 요청 및 응답 헤더

다른 모드가 지정되지 않은 경우 Commerce는 기본 모드로 작동합니다.

## 개발자 모드

다음 _개발자_ commerce 응용 프로그램을 확장하고 사용자 지정하는 데 모드가 권장됩니다. 정적 보기 파일은 캐시되지 않지만 `pub/static` 디렉토리 온디맨드.

개발자 모드에서:

- 사용 [자동 코드 컴파일](../cli/code-compiler.md) 및 향상된 디버깅
- 발견되지 않은 예외가 브라우저에 표시됨
- 시스템 로그인 `var/report` 장황함
- 기록되지 않고 오류 처리기에서 예외가 발생합니다
- 이벤트 구독자를 호출할 수 없는 경우 예외가 발생합니다
- 사용자 정의 표시 `X-Magento-*` HTTP 요청 및 응답 헤더

## 프로덕션 모드

다음 _production_ 모드는 프로덕션 시스템에 Commerce 애플리케이션을 배포하는 데 가장 적합합니다. 데이터베이스 및 웹 서버와 같은 서버 환경을 최적화한 후에는 [정적 보기 파일 배포 도구](../cli/static-view-file-deployment.md) 정적 보기 파일을 `pub/static` 디렉토리. 이렇게 하면 Commerce 응용 프로그램이 런타임 중에 정적 파일을 필요에 따라 동적으로 찾고 복사하는 대신 배포 시 필요한 모든 정적 파일을 제공하여 성능을 향상시킬 수 있습니다.

일부 필드(예: 관리자의 고급 및 개발자 시스템 구성 섹션)는 프로덕션 모드에서 사용할 수 없습니다. 예를 들어 _할 수 없음_ 관리자를 사용하여 캐시 유형을 활성화하거나 비활성화합니다. 캐시 유형을 활성화 및 비활성화할 수 있습니다 _전용_ 사용 [명령줄](../cli/manage-cache.md#config-cli-subcommands-cache-en).

프로덕션 모드에서:

- 정적 보기 파일은 캐시에서만 제공됩니다.
- 오류 및 예외는 파일 시스템에 기록되며 사용자에게 표시되지 않습니다
- 관리자의 일부 구성 필드를 사용할 수 없습니다.

## 유지 관리 모드

다음 _유지 보수_ 모드는 개선, 업데이트 및 구성 작업 중 사이트에 대한 액세스를 제한하거나 금지합니다. 기본적으로 사이트는 방문자를 기본값으로 리디렉션합니다 `Service Temporarily Unavailable` 페이지를 가리키도록 업데이트하는 중입니다.

다음을 만들 수 있습니다. [사용자 지정 유지 관리 페이지](../../upgrade/troubleshooting/maintenance-mode-options.md), 수동으로 유지 관리 모드를 활성화 및 비활성화하고, 승인된 IP 주소의 방문자가 저장소를 정상적으로 볼 수 있도록 유지 관리 모드를 구성합니다. 다음을 참조하십시오 [유지 관리 모드 활성화 및 비활성화](../../installation/tutorials/maintenance-mode.md) 다음에서 _설치 안내서_.

클라우드 인프라에서 Commerce를 사용하는 경우 배포 단계 동안 Commerce 애플리케이션이 유지 관리 모드에서 실행됩니다. 배포가 성공적으로 완료되면 Commerce 응용 프로그램은 프로덕션 모드에서 다시 실행됩니다. 다음을 참조하십시오 [배포 후크](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) 다음에서 _클라우드 인프라의 Commerce 안내서_.

유지 관리 모드에서:

- 사이트 방문자는 기본값으로 리디렉션됩니다. `Service Temporarily Unavailable` 페이지
- 다음 `var/` 디렉터리에는 `.maintenance.flag` 파일
- IP 주소를 기반으로 방문자 액세스를 제한할 수 있습니다
