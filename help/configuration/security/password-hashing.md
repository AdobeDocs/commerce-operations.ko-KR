---
title: 암호 해싱
description: 암호 해시 전략 및 구현에 대해 읽어보십시오.
feature: Configuration, Security
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# 암호 해싱

현재 Commerce은 다른 기본 PHP 해시 알고리즘을 기반으로 하여 암호 해시에 자체 전략을 사용합니다. 상거래는 여러 알고리즘(예: 좋아요 `MD5`, `SHA256`, 또는 `Argon 2ID13`)을 지원합니다. Sodium 확장이 설치된 경우 (PHP 7.3에 기본적으로 설치됨) `Argon 2ID13` 기본 해싱 알고리즘으로 선택됩니다. `SHA256` 그렇지 않으면 기본값입니다. 상거래는 Argon 2i 알고리즘 지원과 함께 기본 PHP `password_hash` 함수를 사용할 수 있습니다.

좋아요 와 같은 `MD5`오래된 알고리즘으로 해시된 이전 암호가 손상되는 것을 방지하기 위해 현재 구현은 원래 암호를 변경하지 않고 해시를 업그레이드하는 방법을 제공합니다. 일반적으로 암호 해시의 포맷 형식은 다음과 같습니다.

```text
password_hash:salt:version<n>:version<n>
```

여기서 `version<n>`...`version<n>` 는 암호에서 사용되는 모든 해시 알고리즘 버전을 나타냅니다. 또한 솔트는 항상 암호 해시 해시와 함께 저장되므로 전체 알고리즘 체인을 복원 할 수 있습니다. 예를 들면 다음과 같습니다좋아요

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

첫 번째 부분은 암호 해시 해시를 나타냅니다. 두 번째는 `8qnyO4H1OYIfGCUb` 소금입니다. 마지막 두 개는 서로 다른 해시 알고리즘입니다 : 1은 이고 `SHA256` 2는 `Argon 2ID13`. 즉, 고객의 암호가 원래 해시 `SHA256` 된 후 알고리즘이 업데이트 `Argon 2ID13` 되고 해시가 Argon으로 다시 해시되었습니다.

## 해시 전략 업그레이드

해시 업그레이드 메커니즘의 모양을 고려합니다. 원래 암호가 `MD5`(으)로 해시된 다음 Argon 2ID13으로 알고리즘이 여러 번 업데이트되었다고 가정해 봅시다. 다음 다이어그램은 해시 업그레이드 플로우를 보여 줍니다.

![해시 업그레이드 작업 과정](../../assets/configuration/hash-upgrade-algorithm.png)

각 해시 알고리즘은 이전 암호 해시를 사용하여 새 해시를 생성합니다. 상거래는 원시의 암호 스토어하지 않습니다.

![해시 업그레이드 전략](../../assets/configuration/hash-upgrade-strategy.png)

위에서 설명한 것처럼 암호 해시에는 원래 암호에 적용된 여러 해시 버전이 있을 수 있습니다.
다음은 고객 인증 중에 암호 확인 메커니즘이 작동하는 방식입니다.

```php
def verify(password, hash):
    restored = password

    hash_map = extract(hash)
    # iterate through all versions specified in the received hash [md5, sha256, argon2id13]
    for version in hash_map.get_versions():
        # generate new hash based on password/previous hash, salt and version
        restored = hash_func(salt . restored, version)

    # extract only password hash from the hash:salt:version chain
    hash = hash_map.get_hash()

    return compare(restored, hash)
```

Commerce는 사용된 모든 암호 해시 버전을 암호 해시와 함께 저장하므로 암호 확인 중에 전체 해시 체인을 복원할 수 있습니다. 해시 확인 메커니즘은 해시 업그레이드 전략과 유사합니다: 암호 해시와 함께 저장된 버전을 기반으로 알고리즘은 제공된 암호에서 해시를 생성하고 해시된 암호와 데이터베이스에 저장된 해시 간의 비교 결과를 반환합니다.

## 이행

클래스는 `\Magento\Framework\Encryption\Encryptor` 암호 해시 생성 및 확인을 담당합니다. [`bin/magento customer:hash:upgrade`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#customerhashupgrade) 명령은 고객 암호 해시를 최신 해시 알고리즘으로 업그레이드합니다.
