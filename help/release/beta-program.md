---
title: 베타 프로그램
description: Adobe Commerce 베타 프로그램 및 참여 방법에 대해 알아봅니다.
source-git-commit: b92053ae4b5454a686d314bdbbad97a212082046
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---


# Adobe Commerce 베타 프로그램

Adobe Commerce 베타 프로그램에 오신 것을 환영합니다. 참여에 관심을 가져 주셔서 감사합니다.

이 프로그램은 모든 Adobe Commerce 파트너 및 고객이 사용할 수 있습니다. 베타 프로그램에 등록하려면 아래 설명된 단계를 읽고 따릅니다.

>[!IMPORTANT]
>
>Adobe Commerce 2.4.6은 이 프로그램이 지원하는 마지막 릴리스입니다. 2023년 6월부터 향후 Adobe은 Adobe Commerce 및 Magento Open Source의 공개 베타 버전을 릴리스할 예정입니다. 자세한 내용은 [릴리스 일정](schedule.md) 공개 베타 릴리스 날짜 목록.

## 참여 이유

1. Adobe가 개발 중인 코드를 일찍 확인하면 향후 업그레이드를 위한 기술 및 상인을 더 빨리 준비할 수 있습니다.

   예, 상황이 변경될 수 있지만, 코드베이스의 변경 사항이 발생하는 위치를 이해하고 GA 릴리스 날짜보다 빨리 준비를 시작할 수 있습니다.

1. 만약 [솔루션 파트너](https://developer.adobe.com/commerce/contributor/community/contribution-programs/) 또는 Technology Partner with Adobe을 통해 Adobe 개발자에게 중요한 피드백을 제공하고 문제를 더 빨리 찾고 수정할 수 있습니다.

참여할 준비가 되었습니까? 아래 절차를 따르십시오.

## 베타 프로그램 계약에 서명

먼저, 우리 회사에 서명해야 합니다 [베타 프로그램 계약](https://experiencecloudpanel.adobe.com/c/a/6hxAOc9DD1vCx2tg1jBKGB).

서명의 신뢰성을 검증하기 위해 Adobe 관계 소유자(일반적으로 해당 소유자)가 _기본_ 회사와 연결된 MageID에서 위에 링크된 문서를 읽고 서명합니다. &#x200B;
양식을 작성하는 동안 추가 지침:

- 기본 MageID와 연결된 이메일을 사용해야 합니다.
- 대상 _Adobe 담당자 이메일_, 사용 `commercebeta@adobe.com` - _이 이메일을 사용하지 않으면 요청을 받지 못할 수 있습니다._.

## GitHub에 대한 개발자 액세스

둘째, 파트너가 피드백을 제공하고 베타에 대한 중요한 업데이트를 받으려면 사용자에게 개인 GitHub 리포지토리에 대한 액세스 권한을 부여해야 합니다.

이미 Adobe 파트너 프로그램에 참여 중인 경우, 베타 프로그램 계약이 체결된 후에 GitHub 사용자에게 개인 리포지토리에 대한 액세스 권한을 제공할 것입니다. 더 이상 할 필요가 없습니다.

Adobe 파트너 프로그램에 아직 속해 있지 않은 경우 다음을 수행해야 합니다.

1. 모든 기여자에게 2단계 인증이 활성화된 활성 GitHub 계정이 있는지 확인합니다.
1. 유지 관리자 GitHub 사용자 이름을 제공합니다. Adobe는 사용자에게 베타 프로그램 계약(`github.com/accountname`).
1. 연락처 <commercebeta@adobe.com> 유지 관리자와 함께 공식 파트너의 회사 이메일에서 합격 요청을 합니다.

파트너가 아닌 경우 2.4.4 베타에 대한 피드백을 제공할 수 없습니다. Adobe는 다음 베타 릴리스에 대해 이 설정을 변경하기 위해 노력하고 있습니다.

## 코드 가져오기

셋째, 사전 프로덕션 코드는 를 작성기 메타패키지로 발표합니다 `https://repo.magento.com`.

다음 문서를 참조하십시오 [릴리스 일정](schedule.md) 베타 릴리스에 대한 최신 정보를 확인하십시오.

### 베타 코드를 성공적으로 다운로드하는 지침

- Adobe Commerce 라이선스 또는 파트너 라이선스와 연결된 MageID(베타 프로그램 계약에 서명하는 데 사용되는 것과 동일한 MageID)를 사용합니다.
Composer를 사용하여 설치하는 방법에 대한 자세한 내용은 [빠른 설치 시작](../installation/composer.md).
베타 코드에 대한 액세스 문제 해결을 보려면 [최신 베타 버전에 액세스할 수 없음](https://support.magento.com/hc/en-us/articles/360048169471).
- 마지막으로, 코드를 설치하고 사용한 후에 비공개 Beta GitHub 리포지토리를 통해 피드백 및 주석을 제공할 것을 파트너에게 요청합니다.

이 프로그램에 대한 자세한 내용은 [FAQ](https://fieldreadiness-adobe.highspot.com/items/5e5e6b8fc714332f32a7cd96?lfrm=rhp.0). 추가 질문 사항은 <commercebeta@adobe.com>.
