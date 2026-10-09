---
title: Security.txt
description: 보안 연구원이 취약점을 보고할 수 있도록 정보를 제공하는 방법에 대해 알아봅니다.
feature: Configuration, Security
badge: 'label="제공: Kalpesh Mehta from Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="칼페시 메타"'
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%
---
# 보안 TXT 파일

연구자에 의해 보안 취약점이 발견되면 적절한 보고 채널이 부족한 경우가 많다. 그 결과 일부 취약점이 보고되지 않습니다. `security.txt` [파일 형식](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) 파일의 목적은 보안 연구자에게 결과를 보고하는 데 사용할 수 있는 정보를 제공하는 것입니다.

판매자는 Commerce _관리자_&#x200B;에서 [보안 문제 보고](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-issue-reporting)에 대한 연락처 정보를 입력할 수 있습니다. 개발자를 위해 `Magento_Securitytxt` 모듈은 다음 기능을 제공합니다.

- _관리자_&#x200B;에서 보안 구성을 저장할 수 있습니다.
- `.well-known/security.txt` 및 `.well-known/security.txt.sig` 파일에 대한 요청에 대해 응용 프로그램 작업 클래스와 일치하는 라우터를 포함합니다.
- `.well-known/security.txt` 및 `.well-known/security.txt.sig` 파일의 콘텐츠를 제공합니다.

올바른 `security.txt` 파일은 다음과 같습니다.

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

`security.txt` 서명(`security.txt.sig`) 파일을 만들려면:

```shell
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

서명을 확인하려면:

```shell
gpg --verify security.txt.sig security.txt
```
