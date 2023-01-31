---
title: 클라우드 기반의 상거래를 위한 원격 스토리지
description: 클라우드 인프라에서 Adobe Commerce을 위한 원격 스토리지를 설정하는 방법에 대한 지침을 참조하십시오.
source-git-commit: 4c89ef65ffb559ad4ad3f3fc45bd73079fbacd1b
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# Commerce on Cloud 인프라를 위한 원격 스토리지 구성

시작 `ece-tools` 패키지 2002.1.5에서는 환경 변수를 사용하여 원격 저장소 모듈을 활성화할 수 있습니다. 그러나 원격 스토리지 모듈은 _제한적_ 클라우드 인프라에서 Adobe Commerce 지원. Adobe이 타사 스토리지 어댑터 서비스 문제를 완전히 해결할 수 없습니다.

## 환경 변수

다음 `REMOTE_STORAGE` 변수는 [단계 배포](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) 클라우드 인프라 프로젝트

### `REMOTE_STORAGE`

- **기본값**—_설정되지 않음_
- **버전**—Commerce 2.4.2 이상

구성 _저장소 어댑터_ AWS S3와 같은 저장소 서비스를 사용하여 영구적인 원격 저장소 컨테이너에 미디어 파일을 저장하려면 원격 스토리지 모듈을 사용하면 리소스를 공유해야 하는 복잡한 다중 서버 구성을 통해 클라우드 프로젝트의 성능을 향상시킬 수 있습니다. 다음은 `.magento.env.yaml` 파일:

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

### Cloud CLI로 변수 설정

설정 `REMOTE_STORAGE` 변수로서 [환경 수준 변수](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) 따라서 파일이 프로덕션, 스테이징 및 통합 환경 간에 공유되지 않습니다. 환경 수준에서 변수를 설정하면 원격 스토리지의 통합 환경을 사용하지 않는 등 일부 환경에서 원격 저장소만 유연하게 사용할 수 있습니다.

**Cloud CLI를 사용하여 원격 스토리지 변수를 추가하려면**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

이렇게 하면 `REMOTE_STORAGE` 지정된 JSON 구성을 사용하는 변수를 채우는 방법을 설명합니다. 다음 `REMOTE_STORAGE` 변수는 JSON 문자열을 사용하여 원격 저장소를 구성합니다. 다음은 JSON 구성 예입니다.

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

구성을 만들고 배포한 후 배포 로그에 원격 저장소 구성에 대한 정보(예: `INFO: Remote storage driver set to: "aws-s3"`

### Project Web Interface를 사용하여 변수 설정

또는 Project Web Interface를 사용하여 변수를 적절한 환경에 추가할 수 있습니다.

**Project Web Interface를 사용하여 원격 저장소 변수를 추가하려면**:

1. 에서 _Project Web Interface_&#x200B;를 누르고 왼쪽에서 환경을 선택합니다.

1. 을(를) 클릭합니다. **환경 구성** 아이콘.

1. 에서 _환경 구성_ 보기를 클릭하고 **변수** 탭.

1. 클릭 **변수 추가**.

1. 에서 _이름_ 필드, 입력 `REMOTE_STORAGE`

1. 에서 _값_ 필드에서 JSON 구성을 추가합니다.

1. 선택 **JSON 값** 및 **중요**; 선택 취소 **하위 환경에서 상속 가능**.

1. 클릭 **변수 추가**.

### 선택적 인증 사용

다음 `key` 및 `secret` 은 선택 사항입니다. 변수를 만들 때 `key` 및 `secret` 다음을 선택하여 `sensitive` 선택 사항입니다. 이 설정을 사용하면 웹 인터페이스에 값이 표시되지 않습니다. 자세한 내용은 [변수 가시성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) 에서 _Commerce on Cloud Infrastructure 안내서_.

다른 인증 방법을 사용하려면 `key` 및 `secret` JSON 구성에서 을 참조하십시오. 대체 인증 방법을 구성하고 서버가 S3 버킷에 대해 인증되었는지 확인합니다.

### 원격 스토리지 동기화

원격 저장소 모듈을 활성화한 후 현재 미디어 파일을 원격 저장소 위치에 동기화합니다.

**동기화를 시작하려면**:

1. 원격 저장소가 구성된 원격 환경에 로그인하려면 SSH를 사용합니다.

1. 동기화를 시작합니다.

```bash
bin/magento remote-storage:sync 
```

## 기본 구성

클라우드 인프라 프로젝트에서 Adobe Commerce과 함께 원격 스토리지 솔루션을 사용하도록 선택하는 경우 [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) 의 지침 _명백히_ AWS S3에서 실제 이미지 최적화가 작동하는지 확인하는 설명서입니다.

다음 사항에 대비하십시오. [강력한 자격 증명](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Pro 프로젝트에서 SSH를 사용하여 서버에 연결하고 `/mnt/shared/fastly_tokens.txt` 파일. 스테이징 및 프로덕션 환경에는 고유한 자격 증명이 있습니다. 각 환경에 대한 자격 증명을 받아야 합니다.

다음 작업으로 클라우드 프로젝트에 대한 원격 저장소를 계속 설정합니다.

1. 구성 [강력한 백엔드 통합](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. 에 대한 VCL 논리 만들기 [AWS S3 인증](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. 에 대한 VCL 논리 만들기 [AWS S3 버킷에 대한 백엔드 요청](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
