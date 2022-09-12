---
title: 파일 소유권 및 권한
description: Adobe Commerce 및 Magento Open Source의 온-프레미스 설치를 사용할 때 파일 시스템 권한의 중요도에 대해 알아봅니다.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# 파일 소유권 및 권한

개발 환경에서 Adobe Commerce 또는 Magento Open Source 설치를 안전하게 하여 허가되지 않은 사용자나 프로세스와 관련된 문제를 예방하고 시스템에 액세스하거나 영향을 줄 수 있습니다. 설치를 보호하려면 다음 파일 시스템 소유권 및 권한 지침을 사용하십시오.

## 파일 시스템 소유자

파일 시스템 소유자는 파일 시스템의 파일에 대한 쓰기 권한을 소유하고 보유하는 사용자입니다.

파일 시스템 소유자에게는 두 가지 유형이 있습니다.

- **단일 사용자와 공유 호스팅**

   공유 호스팅 공급자를 사용하면 애플리케이션 서버에 한 명의 사용자로 로그인할 수 있습니다. 단일 사용자는 로그인하고 FTP를 사용하여 파일을 전송하고 웹 서버를 실행할 수 있습니다. 옵션을 설정할 수 있습니다 [`umask`](#restrict-access-with-a-umask) 액세스 권한(특히 프로덕션 환경에서)을 추가로 제한합니다.

- **두 명의 사용자가 있는 비공개 호스팅**

   애플리케이션 서버를 관리하는 경우 비공개 호스팅이 유용합니다. 각 사용자는 특정 권한을 갖습니다.

   - 다음 _웹 서버 사용자_ 관리자 및 storfront를 실행합니다.

   - 다음 _명령줄 사용자_ cron 작업 및 명령줄 유틸리티를 실행합니다.
   두 사용자 모두 파일 시스템에 동일한 권한이 필요하므로 [공유 그룹](configure-permissions.md#set-ownership-and-permissions-for-two-users) 그리고 [`umask`](#restrict-access-with-a-umask).

### umask로 액세스 제한

보안을 강화하기 위해 특히 공유 호스팅 시스템의 프로덕션 환경에서 를 사용할 수 있습니다 `umask` 액세스를 제한합니다. A `umask`—이라고도 합니다. _파일 시스템 생성 마스크_—는 새로 만든 파일에 대한 파일 권한 설정 방법을 제어하는 비트 세트입니다.

>[!WARNING]
>
>파일 시스템 보안은 복잡하고 중요합니다. 설정할 사용 권한 수준을 결정하기 전에 숙련된 시스템 관리자 또는 네트워크 관리자에게 문의하는 것이 좋습니다. 사용할 수 있는 메커니즘을 제공하지만 권한 전략을 작성하는 것이 귀하의 책임입니다.

Adobe Commerce 및 Magento Open Source은 3비트 기본 마스크를 사용합니다. `002`. UNIX 기본값인 666과 디렉토리의 경우 777에서 기본 마스크를 빼십시오.

For example:

- **디렉토리 775**- 사용자의 전체 제어, 그룹의 전체 제어, 모든 사용자가 디렉토리를 트래버스할 수 있도록 합니다. 이러한 권한은 일반적으로 공유 호스팅 공급자에 의해 필요합니다.

- **파일용 664**- 사용자가 쓰기 가능하고, 그룹에 의해 쓸 수 있으며, 다른 모든 사용자가 읽기 전용입니다.

만들기 `magento_umask` 파일, [umask 설정](../../next-steps/set-umask.md).

## 권한, 소유권 및 애플리케이션 모드

다양한 Adobe Commerce 및 Magento Open Source 애플리케이션 모드를 사용하는 경우 다양한 권한 및 소유권이 권장됩니다.

- 기본값
- 개발자
- 프로덕션

자세한 내용은 [모드 정보](../../../configuration/bootstrap/application-modes.md) 에서 _구성 안내서_.

사용 권한 권장 사항에 대해 더 자세히 알아보려면 [파일 시스템 액세스 권한](../../../configuration/deployment/file-system-permissions.md) 에서 _구성 안내서_.

>[!TIP]
>
>Adobe Commerce 또는 Magento Open Source을 설치하기 전에 [파일 소유권 및 권한 구성](configure-permissions.md).
