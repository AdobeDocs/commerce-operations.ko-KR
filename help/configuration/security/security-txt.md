---
title: Security.txt
description: 보안 연구원이 취약점을 보고할 수 있도록 정보를 제공하는 방법에 대해 알아봅니다.
feature: Configuration, Security
badge: label="Contributed by Kalpesh Mehta from Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="칼페시 메타"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: 150
ht-degree: 0%

---

# 보안 TXT 파일

연구자에 의해 보안 취약점이 발견되면 적절한 보고 채널이 부족한 경우가 많다. 그 결과 일부 취약점이 보고되지 않습니다. 의 목적 `security.txt` [파일 형식](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) 파일은 보안 연구원들이 발견한 내용을 보고하는 데 사용할 수 있는 정보를 제공하는 것입니다.

판매자는 다음에 대한 연락처 정보를 입력할 수 있습니다. [보안 문제 보고](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) 상거래 _관리자_. 개발자의 경우 `Magento_Securitytxt` 모듈은 다음 기능을 제공합니다.

- 에서 보안 구성을 저장할 수 있습니다. _관리자_.
- 에 대한 요청에 대해 애플리케이션 작업 클래스를 일치시키는 라우터를 포함합니다. `.well-known/security.txt` 및 `.well-known/security.txt.sig` 파일.
- 의 콘텐츠를 제공합니다. `.well-known/security.txt` 및 `.well-known/security.txt.sig` 파일.

유효 `security.txt` 파일은 다음과 같습니다.

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

다음을 만들려면 `security.txt` 서명(`security.txt.sig`) 파일:

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

서명을 확인하려면:

```bash
gpg --verify security.txt.sig security.txt
```
