---
title: 인증 키 받기
description: repo.magento.com에서 Adobe Commerce Composer 패키지에 액세스하기 위해 자격 증명을 검색하려면 다음 단계를 따르십시오.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: fc63ca58cd2ff7c5ec597751980a39bfbe68aa5f
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# 인증 키 받기

`repo.magento.com` 리포지토리는 Adobe Commerce 및 타사 Composer 패키지가 저장되어 있으며 인증이 필요합니다. 저장소에 액세스할 수 있도록 32자로 된 *인증 키* 쌍을 생성하려면 Commerce Marketplace 계정을 사용하십시오.

Adobe Commerce 패키지에 대한 액세스 권한을 얻으려면 해당 패키지에 대한 액세스 권한이 부여된 MAGEID와 연결된 키를 사용해야 합니다. MAGEID는 일반적으로 Adobe Commerce 계정의 기본 연락처이며 항상 Adobe Commerce on cloud infrastructure 프로젝트의 프로젝트 소유자는 아닐 수 있습니다.

>[!TIP]
>
>[오류](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)가 발생한 경우 패키지에 액세스할 수 있는 권한이 없거나 계정의 미결 송장으로 인해 액세스 권한이 만료되었을 수 있습니다.
>
>* 귀하가 계정에서 기본 담당자 사용자인 경우 계정에 미결 송장이 나열되어 있지 않은지 확인하십시오.
>* 기본 연락처에서 제공한 키가 작동하지 않고 계정에 해결되지 않은 청구서가 없는 경우 기본 연락처는 [Adobe Commerce 지원](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)에 지원을 요청해야 합니다.

인증 키를 만들려면 다음을 수행하십시오.

1. [Commerce Marketplace](https://commercemarketplace.adobe.com/)에 로그인합니다. 계정이 없는 경우 **등록**&#x200B;을 클릭하세요.

1. 페이지 오른쪽 상단에서 계정 이름을 클릭하고 **내 프로필**&#x200B;을 선택합니다.

1. 마켓플레이스 탭에서 **액세스 키**&#x200B;를 클릭합니다.

   ![Commerce Marketplace에서 보안 액세스 키 받기](../../assets/installation/cloud_access-key.png)

1. **새 액세스 키 만들기**&#x200B;를 클릭합니다. 특정 키 이름(예: 키를 받는 개발자의 이름)을 입력하고 **확인**&#x200B;을 클릭합니다.

1. 새 공개 및 비공개 키가 이제 복사하기 위해 클릭할 수 있는 계정과 연결됩니다. 이 정보를 저장하거나 프로젝트 작업 시 페이지를 열어 두십시오. **공개 키**&#x200B;를 사용자 이름으로 사용하고 **개인 키**&#x200B;를 암호로 사용합니다.

## 인증 키 관리

인증 키를 비활성화하거나 삭제할 수도 있습니다. 예를 들어, 누군가 조직을 떠난 후 보안을 위해 키를 비활성화하거나 삭제할 수 있습니다.

* 키를 사용하지 않으려면 **사용 안 함**&#x200B;을 클릭하세요. 키 사용을 일시 중단하려는 경우 이 작업을 수행할 수 있습니다.
* 이전에 비활성화된 키를 활성화하려면 **활성화**&#x200B;를 클릭합니다.
* 키를 삭제하려면 **삭제**&#x200B;를 클릭하세요.

### SSH 액세스 토큰 관리

SSH를 사용하여 Adobe Commerce 릴리스를 다운로드하려면 다운로드 액세스 토큰을 생성해야 합니다. 토큰을 생성하려면:

1. [magento.com 계정](https://account.magento.com/customer/account/login)에 로그인합니다.
1. 페이지 맨 위에서 **내 계정**&#x200B;을 클릭합니다.
1. **계정 설정** > **액세스 토큰 다운로드**&#x200B;를 클릭합니다.

   ![키에 액세스](../../assets/installation/connect_keys1.png)

1. 기존 토큰을 대체하고 비활성화하려면 **새 토큰 생성**&#x200B;을 클릭하십시오.

릴리스를 다운로드하려면 MAGEID와 토큰을 사용해야 합니다. MAGEID는 계정 페이지의 왼쪽 상단에 표시됩니다.

For example:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

인증 키를 사용하여 다음을 수행합니다.

* [메타패키지 가져오기(통합자, 패키지)](../composer.md)
* [GitHub 리포지토리 복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)(기여 개발자만 해당)
* [모듈 업그레이드 및 관리](../../upgrade/modules/upgrade.md)
