---
title: 인증 키 가져오기
description: 다음 단계에 따라 repo.magento.com에서 Adobe Commerce 및 Magento Open Source 작성기 패키지에 액세스할 수 있는 자격 증명을 검색합니다.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# 인증 키 가져오기

다음 `repo.magento.com` 저장소는 Adobe Commerce 및 Magento Open Source 및 타사 작성기 패키지가 저장되며 인증이 필요합니다. Commerce Marketplace 계정을 사용하여 32자로 된 쌍을 생성합니다 *인증 키* 저장소에 액세스하려면

>[!NOTE]
>
>Adobe Commerce 및 Magento Open Source 패키지에 대한 액세스 권한을 부여하려면 해당 패키지에 대한 액세스 권한이 부여된 MAGEID와 연결된 키를 사용해야 합니다. MAGEID는 일반적으로 **청구 담당자** Adobe Commerce 계정에서 항상 **프로젝트 소유자** Adobe Commerce on cloud infrastructure project의 지침에 따라 콘솔에서 스테이징을 로컬로 활성화하십시오. 만약 [오류](https://support.magento.com/hc/en-us/articles/360040296392)를 입력하면 패키지에 액세스할 수 있는 권한이 없거나 계정의 미결 송장으로 인해 액세스 권한이 만료되었을 수 있습니다. 연락처 [Adobe Commerce 지원](https://support.magento.com/hc/en-us) MAGEID에 대한 지원을 요청합니다.

인증 키를 만들려면:

1. 에 로그인합니다. [Commerce Marketplace](https://marketplace.magento.com). 계정이 없는 경우 **등록**.
1. 페이지 오른쪽 상단에 있는 계정 이름을 클릭하고 을 선택합니다 **내 프로필**.

1. 클릭 **액세스 키** ( 마켓플레이스 탭)을 참조하십시오.

   ![Commerce Marketplace에서 보안 액세스 키 가져오기](../../assets/installation/cloud_access-key.png)

1. 클릭 **새 액세스 키 만들기**. 키의 특정 이름(예: 키를 받는 개발자의 이름)을 입력하고 를 클릭합니다 **확인**.

1. 이제 복사하기 위해 클릭할 수 있는 새 공개 및 개인 키가 계정과 연결됩니다. 이 정보를 저장하거나 프로젝트 작업 시 페이지를 열어 두십시오. 를 사용하십시오 **공개 키** 사용자 이름과 **개인 키** 을 암호로 사용할 수 있습니다.

## 인증 키 관리

인증 키를 비활성화하거나 삭제할 수도 있습니다. 예를 들어 다른 사람이 조직을 떠난 후 보안상의 이유로 키를 비활성화하거나 삭제할 수 있습니다.

* 키를 비활성화하려면 다음을 수행하십시오. 클릭 **비활성화**. 키 사용을 일시 중단하려는 경우 이 작업을 수행할 수 있습니다.
* 이전에 비활성화된 키를 활성화하려면 클릭 **활성화**.
* 키를 삭제하려면 다음을 수행하십시오. 클릭 **삭제**.

### SSH 액세스 토큰 관리

SSH를 사용하여 Adobe Commerce 릴리스를 다운로드하려면 다운로드 액세스 토큰을 생성해야 합니다. 토큰을 생성하려면:

1. 에 로그인합니다. [magento.com 계정](https://account.magento.com/customer/account/login).
1. 클릭 **내 계정** 를 클릭합니다.
1. 클릭 **계정 설정** > **액세스 토큰 다운로드**.

   ![키 액세스](../../assets/installation/connect_keys1.png)

1. 클릭 **새 토큰 생성** 기존 토큰을 바꾸거나 비활성화합니다.

릴리스를 다운로드하려면 MAGEID와 토큰을 함께 사용해야 합니다. 계정 페이지의 왼쪽 상단에 MAGID가 표시됩니다.

For example:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

인증 키를 사용하여 다음을 수행할 수 있습니다.

* [메타패키지(통합자, 포장자)](../composer.md)
* [GitHub 리포지토리 복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (기여 개발자만)
* [모듈 업그레이드 및 관리](../../upgrade/modules/upgrade.md)
