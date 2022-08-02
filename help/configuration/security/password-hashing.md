---
title: 암호 해싱
description: 암호 해싱 전략 및 구현에 대해 읽어 보십시오.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# 암호 해싱

현재 Commerce에서는 다른 기본 PHP 해싱 알고리즘을 기반으로 암호 해시에 자체 전략을 사용합니다. Commerce에서는 다음과 같은 여러 알고리즘을 지원합니다 `MD5`, `SHA256`, 또는 `Argon 2ID13`. 나트륨 확장이 설치되어 있는 경우(기본적으로 PHP 7.3에 설치) `Argon 2ID13` 기본 해싱 알고리즘으로 선택됩니다. 그렇지 않으면, `SHA256` 는 기본값입니다. Commerce에서는 기본 PHP를 사용할 수 있습니다 `password_hash` Argun 2i 알고리즘 지원을 사용하여 작동합니다.

오래된 알고리즘으로 해시된 이전 암호를 손상시키지 않기 위해 `MD5`현재 구현에서는 원래 암호를 변경하지 않고 해시를 업그레이드하는 방법을 제공합니다. 일반적으로 암호 해시는 다음 형식을 갖습니다.

```text
password_hash:salt:version<n>:version<n>
```

위치 `version<n>`...`version<n>` 암호에 사용되는 모든 해시 알고리즘 버전을 나타냅니다. 또한 소금은 항상 암호 해시와 함께 저장되므로 전체 알고리즘 체인을 복원할 수 있습니다. 예는 다음과 같습니다.

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

첫 번째 부분은 암호 해시를 나타냅니다. 둘째는 `8qnyO4H1OYIfGCUb` 소금은 소금입니다. 마지막 두 가지는 서로 다른 해시 알고리즘입니다. 1: `SHA256` 2가 `Argon 2ID13`. 고객의 암호가 원래 `SHA256` 그 이후에 알고리즘이 `Argon 2ID13` 그리고 해시는 아르곤과 함께 다시 해시되었다.

## 해시 전략 업그레이드

해시 업그레이드 메커니즘의 모습을 생각해 보십시오. 원래 암호가 `MD5` 그런 다음 이 알고리즘은 Argon 2ID13을 사용하여 여러 번 업데이트되었습니다. 다음 다이어그램은 해시 업그레이드 흐름을 보여줍니다.

![해시 업그레이드 워크플로우](../../assets/configuration/hash-upgrade-algorithm.png)

각 해시 알고리즘에서는 이전 암호 해시를 사용하여 새 해시를 생성합니다. 상거래에 원본 원시 암호가 저장되지 않습니다.

![해시 업그레이드 전략](../../assets/configuration/hash-upgrade-strategy.png)

위에서 설명한 것처럼, 암호 해시에는 원래 암호에 적용된 여러 해시 버전이 있을 수 있습니다.
고객 인증 중에 암호 확인 메커니즘이 작동하는 방식은 다음과 같습니다.

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

Commerce는 사용된 모든 암호 해시 버전을 암호 해시와 함께 저장하므로, 암호 확인 중에 전체 해시 체인을 복원할 수 있습니다. 해시 확인 메커니즘은 해시 업그레이드 전략과 유사합니다. 암호 해시와 함께 저장된 버전을 기반으로 알고리즘은 제공된 암호에서 해시를 생성하고 해시된 암호와 데이터베이스 저장 해시 간의 비교 결과를 반환합니다.

## 구현

다음 `\Magento\Framework\Encryption\Encryptor` 클래스는 암호 해시 생성 및 확인을 담당합니다. 다음 [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) 명령은 고객 암호 해시를 최신 해시 알고리즘으로 업그레이드합니다.
