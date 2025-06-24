---
title: 원격 스토리지용 AWS S3 버킷 구성
description: 원격 스토리지용 AWS S3 스토리지 서비스를 사용하도록 Commerce 프로젝트를 구성합니다.
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: 3f45b61a2f4fd6db161c66182212f3aff5900e26
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# 원격 스토리지용 AWS S3 버킷 구성

[Amazon 단순 저장소 서비스(Amazon S3)][AWS S3]는 업계 최고의 확장성, 데이터 가용성, 보안 및 성능을 제공하는 개체 저장소 서비스입니다. AWS S3 서비스는 데이터 저장을 위해 버킷 또는 컨테이너를 사용합니다. 이 구성을 사용하려면 _private_ 버킷을 만들어야 합니다. 클라우드 인프라의 Adobe Commerce에 대해서는 [클라우드 인프라의 Commerce에 대한 원격 저장소 구성](cloud-support.md)을 참조하십시오.

>[!WARNING]
>
>Adobe은 심각한 보안 위험을 초래하므로 공개 버킷 사용을 매우 자제합니다.

**AWS S3 어댑터로 원격 저장소를 사용하려면**:

1. Amazon S3 대시보드에 로그인하고 _private_ 버킷을 만듭니다.

1. [AWS IAM] 역할을 설정합니다. 또는 액세스 및 비밀 키를 생성합니다.

1. 기본 데이터베이스 저장소를 비활성화합니다.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. 개인 버킷을 사용하도록 Commerce을 구성합니다. 매개 변수의 전체 목록은 [원격 저장소 옵션](remote-storage.md#remote-storage-options)을 참조하십시오.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. 미디어 파일을 원격 스토리지와 동기화합니다.

   ```bash
   bin/magento remote-storage:sync
   ```

## Nginx 구성

>[!NOTE]
>
>이 접근 방식은 클라우드 인프라 프로젝트의 Adobe Commerce에는 적용되지 않습니다. 클라우드 인프라의 Adobe Commerce에서 Nginx를 구성할 수 없습니다. 자세한 내용은 [클라우드별 설명서](cloud-support.md)를 참조하세요.

Nginx에서 `proxy_pass` 지시문을 사용하여 인증을 수행하려면 추가 구성이 필요합니다. `nginx.conf` 파일에 다음 프록시 정보를 추가하십시오.

>nginx.conf

```conf
location ~* \.(ico|jpg|jpeg|png|gif|svg|js|css|swf|eot|ttf|otf|woff|woff2)$ {
    # Proxying to AWS S3 storage.
    resolver 8.8.8.8;
    set $bucket "<s3-bucket-name>";
    proxy_pass https://s3.amazonaws.com/$bucket$uri;
    proxy_pass_request_body off;
    proxy_pass_request_headers off;
    proxy_intercept_errors on;
    proxy_hide_header "x-amz-id-2";
    proxy_hide_header "x-amz-request-id";
    proxy_hide_header "x-amz-storage-class";
    proxy_hide_header "Set-Cookie";
    proxy_ignore_headers "Set-Cookie";
}
```

### 인증

[AWS IAM] 역할 대신 액세스 및 비밀 키를 사용하는 경우 [`ngx_aws_auth` Nginx 모듈][ngx repo]을(를) 포함해야 합니다.

### 권한

S3 통합은 로컬 파일 시스템에서 캐시된 이미지를 생성하고 저장하는 기능을 사용합니다. 따라서 `pub/media` 및 유사한 디렉터리에 대한 폴더 권한은 로컬 저장소를 사용할 때와 S3에 대해 동일합니다.

### 파일 작업

파일 저장소 유형에 관계없이 코딩 또는 확장 개발에서 [!DNL Commerce] 파일 어댑터 메서드를 사용하는 것이 좋습니다. S3 파일이 파일 시스템 내에 없으므로 스토리지용 S3 사용 시 기본 PHP 파일 I/O 작업(예: `copy`, `rename` 또는 `file_put_contents`)을 사용하지 마십시오. 코드 예제는 [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18)을 참조하십시오.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
