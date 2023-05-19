---
title: 클라우드 인프라의 Commerce를 위한 원격 스토리지
description: 클라우드 인프라에서 Adobe Commerce용 원격 스토리지를 설정하는 방법에 대한 지침을 참조하십시오.
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# 클라우드 인프라에서 Commerce를 위한 원격 스토리지 구성

다음으로 시작 `ece-tools` 패키지 2002.1.5에서는 환경 변수를 사용하여 원격 스토리지 모듈을 활성화할 수 있지만 원격 스토리지 모듈에는 _제한적_ 클라우드 인프라에서 Adobe Commerce 지원. Adobe이 타사 스토리지 어댑터 서비스의 문제를 완전히 해결할 수 없습니다.

## 환경 변수

다음 `REMOTE_STORAGE` 변수는에서 사용됩니다. [배포 단계](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) 클라우드 인프라 프로젝트의

### `REMOTE_STORAGE`

- **기본값**—_설정되지 않음_
- **버전**—Commerce 2.4.2 이상

구성 _저장소 어댑터_ AWS S3와 같은 저장소 서비스를 사용하여 영구적인 원격 저장소 컨테이너에 미디어 파일을 저장합니다. 원격 스토리지 모듈을 사용하면 리소스를 공유해야 하는 복잡한 다중 서버 구성을 통해 클라우드 프로젝트의 성능을 향상시킬 수 있습니다. 다음은 를 사용한 원격 스토리지 구성의 예입니다. `.magento.env.yaml` 파일:

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

설정 `REMOTE_STORAGE` 변수 형식 [환경 수준 변수](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) 프로덕션, 스테이징 및 통합 환경 간에 파일이 공유되지 않도록 합니다. 환경 수준에서 변수를 설정하면 원격 스토리지의 통합 환경 사용을 제외하는 것과 같이 일부 환경에서만 원격 스토리지를 유연하게 사용할 수 있습니다.

**Cloud CLI를 사용하여 원격 스토리지 변수를 추가하려면**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

이렇게 하면 `REMOTE_STORAGE` 지정된 JSON 구성이 있는 변수입니다. 다음 `REMOTE_STORAGE` 변수는 JSON 문자열을 사용하여 원격 저장소를 구성합니다. 다음은 JSON 구성의 예입니다.

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

구성을 만들고 배포한 후 배포 로그에는 다음과 같은 원격 저장소 구성에 대한 정보가 포함되어야 합니다 `INFO: Remote storage driver set to: "aws-s3"`

### Project Web Interface로 변수 설정

또는 Project Web Interface를 사용하여 변수를 적절한 환경에 추가할 수 있습니다.

**Project Web Interface를 사용하여 원격 저장소 변수를 추가하려면**:

1. 다음에서 _프로젝트 웹 인터페이스_&#x200B;를 클릭하고 왼쪽에서 환경을 선택합니다.

1. 다음을 클릭합니다. **환경 구성** 아이콘.

1. 다음에서 _환경 구성_ 보기, 클릭 **변수** 탭.

1. 클릭 **변수 추가**.

1. 다음에서 _이름_ 필드, 입력 `REMOTE_STORAGE`

1. 다음에서 _값_ 필드에서 JSON 구성을 추가합니다.

1. 선택 **JSON 값** 및 **중요**; 선택 해제 **하위 환경에 의해 상속 가능**.

1. 클릭 **변수 추가**.

### 선택적 인증 사용

다음 `key` 및 `secret` 선택 사항입니다. 변수를 만들 때 `key` 및 `secret` 을(를) 선택하여 `sensitive` 옵션을 선택합니다. 이 설정을 사용하면 값이 웹 인터페이스에 표시되지 않습니다. 다음을 참조하십시오 [변수 가시성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) 다음에서 _클라우드 인프라의 Commerce 안내서_.

다른 인증 방법을 사용하려면 다음을 생략합니다 `key` 및 `secret` json 구성에서. 대체 인증 방법을 구성하고 서버가 S3 버킷에 대해 인증되었는지 확인합니다.

### 원격 저장소 동기화

원격 스토리지 모듈을 활성화한 후 현재 미디어 파일을 원격 저장소 위치에 동기화합니다.

**동기화를 시작하려면**:

1. SSH를 사용하여 원격 저장소가 구성된 원격 환경에 로그인합니다.

1. 동기화를 시작합니다.

```bash
bin/magento remote-storage:sync 
```

## Fastly 구성

Adobe Commerce on cloud infrastructure 프로젝트와 함께 원격 스토리지 솔루션을 사용하도록 선택하는 경우 [Amazon](https://docs.fastly.com/en/guides/amazon-s3) 의 지침 _Fastly_ Fastly 이미지 최적화가 AWS S3에서 작동하도록 하는 문서입니다.

다음을 준비하십시오 [Fastly 자격 증명](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Pro 프로젝트에서 SSH를 사용하여 서버에 연결하고 `/mnt/shared/fastly_tokens.txt` 파일. 스테이징 및 프로덕션 환경에는 고유한 자격 증명이 있습니다. 각 환경에 대한 자격 증명을 가져와야 합니다.

다음 작업을 사용하여 클라우드 프로젝트에 대한 원격 저장소 설정을 계속합니다.

1. 구성 [Fastly 백엔드 통합](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. 에 대한 VCL 논리 생성 [AWS S3 인증](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. 에 대한 VCL 논리 생성 [AWS S3 버킷에 대한 백엔드 요청](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
