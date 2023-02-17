---
title: Security.txt
description: 보안 연구원이 취약점을 보고하는 데 도움이 되는 정보를 제공하는 방법을 알아봅니다.
badge: label="Contributed by Kalpesh meta from Corra" type="Consolident" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Meta"
source-git-commit: bcb995ea417423b0cbc59c035ba5fdedbce3310e
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# 보안 TXT 파일

연구원들이 보안상 취약점을 발견했을 때, 적절한 보고 채널이 부족한 경우가 많습니다. 따라서, 일부 취약점이 보고되지 않습니다. 의 목적 `security.txt` [파일 형식](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) 이 파일은 보안 연구원에게 이 결과를 보고하는 데 사용할 수 있는 정보를 제공하는 것입니다.

상인들은 다음 정보를 입력할 수 있습니다 [보안 문제 보고](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) 상거래 _관리_. 개발자의 경우 `Magento_Securitytxt` 이 모듈은 다음 기능을 제공합니다.

- 보안 구성을 _관리_.
- 요청에 대한 응용 프로그램 작업 클래스와 일치하는 라우터를 포함합니다. `.well-known/security.txt` 및 `.well-known/security.txt.sig` 파일.
- 의 컨텐츠를 제공합니다. `.well-known/security.txt` 및 `.well-known/security.txt.sig` 파일.

유효한 `security.txt` 파일은 다음과 같을 수 있습니다.

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

을(를) 만들려면 `security.txt` 서명 (`security.txt.sig`) 파일:

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

서명을 확인하려면:

```bash
gpg --verify security.txt.sig security.txt
```
