---
title: 원격 저장소에 대한 AWS S3 버킷 구성
description: 원격 저장소에 AWS S3 저장소 서비스를 사용하도록 상거래 프로젝트를 구성합니다.
source-git-commit: 9a5993c9a65ad210f1a9682734730f235bbc3d44
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# 원격 저장소에 대한 AWS S3 버킷 구성

다음 [Amazon Simple Storage Service (Amazon S3)][AWS S3] 는 업계 최고의 확장성, 데이터 가용성, 보안 및 성능을 제공하는 객체 스토리지 서비스입니다. AWS S3 서비스는 데이터 저장소에 버킷 또는 컨테이너를 사용합니다. 이 구성을 사용하려면 _개인_ 버킷. 클라우드 기반의 Adobe Commerce에 대해서는 다음을 참조하십시오 [Commerce on Cloud 인프라를 위한 원격 스토리지 구성](cloud-support.md).

>[!WARNING]
>
>Adobe은 심각한 보안 위험을 발생하므로 공개 버킷의 사용을 크게 줄입니다.

**AWS S3 어댑터를 사용하여 원격 저장소를 활성화하려면**:

1. Amazon S3 대시보드에 로그인하고 _개인_ 버킷.

1. 설정 [AWS IAM] 역할. 또는 액세스 및 비밀 키를 생성합니다.

1. 기본 데이터베이스 저장소를 비활성화합니다.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. 비공개 버킷을 사용하도록 상거래를 구성합니다. 자세한 내용은 [원격 스토리지 옵션](remote-storage.md#remote-storage-options) 를 참조하십시오.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

## Nginx 구성

Nginx는 `proxy_pass` 지시문 다음 프록시 정보를 `nginx.conf` 파일:

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

대신 액세스 및 암호 키를 사용하는 경우 [AWS IAM] 역할, 다음을 포함해야 합니다 [`ngx_aws_auth` Nginx 모듈][ngx repo].

### 권한

S3 통합은 로컬 파일 시스템에서 캐시된 이미지를 생성하고 저장하는 기능에 의존합니다. 따라서 폴더 사용 권한 `pub/media` 및 유사한 디렉토리는 로컬 저장소를 사용할 때와 동일한 S3에 대해 동일합니다.

### 파일 작업

을 사용하는 것이 좋습니다 [!DNL Commerce] 파일 저장소 유형에 관계없이 코딩 또는 확장 개발 시 파일 어댑터 메서드를 사용합니다. 스토리지에 S3를 사용할 때는 다음과 같은 기본 PHP 파일 I/O 작업을 사용하지 마십시오 `copy`, `rename`, 또는 `file_put_contents`S3 파일이 파일 시스템 내에 없으므로 자세한 내용은 [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) 코드 예제 의 경우.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
