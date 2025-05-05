---
title: 클라우드 인프라의 Commerce을 위한 원격 스토리지
description: 클라우드 인프라에서 Adobe Commerce용 원격 스토리지를 설정하는 방법에 대한 지침을 참조하십시오.
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# 클라우드 인프라에서 Commerce에 대한 원격 스토리지 구성

`ece-tools` 패키지 2002.1.5부터 환경 변수를 사용하여 원격 저장소 모듈을 사용할 수 있지만, 원격 저장소 모듈은 클라우드 인프라의 Adobe Commerce에서 _제한적_ 지원을 받습니다. Adobe이 타사 스토리지 어댑터 서비스의 문제를 완전히 해결할 수 없습니다.

## 환경 변수

`REMOTE_STORAGE` 변수는 클라우드 인프라 프로젝트의 [배포 단계](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=ko) 중에 사용됩니다.

### `REMOTE_STORAGE`

- **기본값**—_설정되지 않음_
- **버전**—Commerce 2.4.2 이상

AWS S3과 같은 저장소 서비스를 사용하여 영구적인 원격 저장소 컨테이너에 미디어 파일을 저장하도록 _저장소 어댑터_&#x200B;를 구성하십시오. 원격 스토리지 모듈을 사용하면 리소스를 공유해야 하는 복잡한 다중 서버 구성을 통해 클라우드 프로젝트의 성능을 향상시킬 수 있습니다. 다음은 `.magento.env.yaml` 파일을 사용하는 원격 저장소 구성의 예입니다.

```yaml
stage:
  deploy:
    REMOTE_STORAGE:
      driver: aws-s3 # Required
      prefix: cloud # Optional
      config:
        bucket: my-bucket # Required
        region: my-region # Required
        key: my-key # Optional
        secret: my-secret-key # Optional
```

### Cloud CLI를 사용하여 변수 설정

프로덕션, 스테이징 및 통합 환경 간에 파일을 공유하지 않도록 `REMOTE_STORAGE` 변수를 [환경 수준 변수](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=ko)(으)로 설정하십시오. 환경 수준에서 변수를 설정하면 원격 스토리지의 통합 환경 사용을 제외하는 것과 같이 일부 환경에서만 원격 스토리지를 유연하게 사용할 수 있습니다.

**Cloud CLI를 사용하여 원격 저장소 변수를 추가하려면**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

지정된 JSON 구성으로 `REMOTE_STORAGE` 변수가 만들어집니다. `REMOTE_STORAGE` 변수는 JSON 문자열을 사용하여 원격 저장소를 구성합니다. 다음은 JSON 구성의 예입니다.

```json
{
  "driver": "aws-s3",
  "prefix": "uat",
  "config": {
    "bucket": "aws-bucket-id",
    "region": "aws-region-id",
    "key": "optional-key",
    "secret": "optional-secret"
  }
}
```

구성을 만들고 배포한 후 배포 로그에 원격 저장소 구성에 대한 정보가 포함되어야 합니다(예: `INFO: Remote storage driver set to: "aws-s3"`).

### Project Web Interface로 변수 설정

또는 Project Web Interface를 사용하여 변수를 적절한 환경에 추가할 수 있습니다.

**Project Web Interface를 사용하여 원격 저장소 변수를 추가하려면**:

1. _Project Web Interface_&#x200B;에서 왼쪽에서 환경을 선택합니다.

1. **환경 구성** 아이콘을 클릭합니다.

1. _환경 구성_ 보기에서 **변수** 탭을 클릭합니다.

1. **변수 추가**&#x200B;를 클릭합니다.

1. _이름_ 필드에 `REMOTE_STORAGE`을(를) 입력하십시오.

1. _값_ 필드에서 JSON 구성을 추가합니다.

1. **JSON 값** 및 **중요**&#x200B;을(를) 선택하십시오. **하위 환경에서 상속 가능**&#x200B;을 선택 취소하십시오.

1. **변수 추가**&#x200B;를 클릭합니다.

### 선택적 인증 사용

`key` 및 `secret`은(는) 선택 사항입니다. 변수를 만들 때 `sensitive` 옵션을 선택하여 `key` 및 `secret`을(를) 숨길 수 있습니다. 이 설정을 사용하면 값이 웹 인터페이스에 표시되지 않습니다. _Cloud Infrastructure의 Commerce_&#x200B;에서 [변수 가시성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=ko#visibility)을 참조하십시오.

다른 인증 방법을 사용하려면 JSON 구성에서 `key` 및 `secret`을(를) 생략합니다. 대체 인증 방법을 구성하고 서버가 S3 버킷에 대해 인증되었는지 확인합니다.

### 원격 저장소 동기화

원격 스토리지 모듈을 활성화한 후 현재 미디어 파일을 원격 저장소 위치에 동기화합니다.

**동기화를 시작하려면**:

1. SSH를 사용하여 원격 저장소가 구성된 원격 환경에 로그인합니다.

1. 동기화를 시작합니다.

```bash
bin/magento remote-storage:sync 
```

## Fastly 구성

클라우드 인프라 프로젝트에서 Adobe Commerce과 함께 원격 스토리지 솔루션을 사용하도록 선택하는 경우 _Fastly_ 설명서의 [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) 지침을 사용하여 Fastly 이미지 최적화가 AWS S3에서 작동하는지 확인하십시오.

[Fastly 자격 증명](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=ko#get-fastly-credentials)을 준비하세요. Pro 프로젝트에서 SSH를 사용하여 서버에 연결하고 `/mnt/shared/fastly_tokens.txt` 파일에서 Fastly 자격 증명을 가져옵니다. 스테이징 및 프로덕션 환경에는 고유한 자격 증명이 있습니다. 각 환경에 대한 자격 증명을 가져와야 합니다.

다음 작업을 사용하여 클라우드 프로젝트에 대한 원격 저장소 설정을 계속합니다.

1. [가장 빠른 백엔드 통합을 구성](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. [AWS S3 인증](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket)에 대한 VCL 논리를 만듭니다.

1. AWS S3 버킷에 대한 [백엔드 요청](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/)에 대한 VCL 논리를 만듭니다.
