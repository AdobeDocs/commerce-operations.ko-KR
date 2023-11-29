---
title: 원격 스토리지 구성
description: 온-프레미스 Commerce 응용 프로그램에 대한 원격 저장소 모듈을 구성하는 방법에 대해 알아봅니다.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# 원격 스토리지 구성

원격 스토리지 모듈은 미디어 파일을 저장하고 AWS S3와 같은 스토리지 서비스를 사용하여 영구적인 원격 스토리지 컨테이너에 가져오기 및 내보내기를 예약하는 옵션을 제공합니다. 기본적으로 Adobe Commerce 애플리케이션은 애플리케이션이 포함된 동일한 파일 시스템에 미디어 파일을 저장합니다. 이는 복잡한 다중 서버 구성에서 비효율적이며 리소스를 공유할 때 성능이 저하될 수 있습니다. 원격 스토리지 모듈을 사용하여 미디어 파일을 `pub/media` 디렉토리에서 파일 가져오기/내보내기 `var` 서버측 이미지 크기 조정을 활용하는 원격 개체 스토리지의 디렉토리입니다.

>[!INFO]
>
>원격 저장소는 Commerce 버전 2.4.2 이상에서만 사용할 수 있습니다. 다음을 참조하십시오. [2.4.2 릴리스 노트](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>원격 스토리지 모듈에 _제한적_ 클라우드 인프라에서 Adobe Commerce 지원. Adobe이 타사 스토리지 어댑터 서비스의 문제를 완전히 해결할 수 없습니다. 다음을 참조하십시오 [클라우드 인프라에서 Commerce를 위한 원격 스토리지 구성](cloud-support.md) 클라우드 프로젝트용 원격 스토리지를 구현하는 방법에 대한 지침을 제공합니다.

![스키마 이미지](../../assets/configuration/remote-storage-schema.png)

## 원격 스토리지 옵션

다음을 사용하여 원격 저장소를 구성할 수 있습니다. `remote-storage` 옵션이 있는 [`setup` CLI 명령](../../installation/tutorials/deployment.md). 다음 `remote-storage` 옵션은 다음 구문을 사용합니다.

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

다음 `parameter-name` 는 특정 원격 스토리지 매개 변수 이름을 나타냅니다. 다음 표에는 원격 스토리지를 구성하는 데 사용할 수 있는 매개 변수가 나와 있습니다.

| 명령줄 매개 변수 | 매개 변수 이름 | 설명 | 기본값 |
|--- |--- |--- |--- |
| `remote-storage-driver` | 드라이버 | 어댑터 이름<br>가능한 값:<br>**파일**: 원격 스토리지를 비활성화하고 로컬 파일 시스템 사용&#x200B;<br>**aws-s3**: 사용 [Amazon Simple Storage Service(Amazon S3)](remote-storage-aws-s3.md) | 없음 |
| `remote-storage-bucket` | 버킷 | 개체 저장소 또는 컨테이너 이름 | 없음 |
| `remote-storage-prefix` | 접두사 | 선택적 접두사(개체 저장소 내부의 위치) | 비어 있음 |
| `remote-storage-region` | 지역 | 지역 이름 | 없음 |
| `remote-storage-key` | 액세스 키 | 선택적 액세스 키 | 비어 있음 |
| `remote-storage-secret` | 비밀 키 | 선택적 비밀 키 | 비어 있음 |

### 스토리지 어댑터

기본 저장소 위치는 로컬 파일 시스템에 있습니다. A _저장소 어댑터_ 스토리지 서비스에 연결하고 어디에나 파일을 저장할 수 있습니다. [!DNL Commerce] 는 다음 스토리지 서비스 구성을 지원합니다.

- [Amazon Simple Storage Service(Amazon S3)](remote-storage-aws-s3.md)

## 원격 스토리지 사용

Adobe Commerce 설치 중에 원격 저장소를 설치하거나 기존 Commerce 인스턴스에 원격 저장소를 추가할 수 있습니다. 다음 예에서는 일련의 를 사용하는 각 방법을 보여 줍니다. `remote-storage` commerce가 있는 매개 변수 `setup` CLI 명령 최소한으로, 당신은 저장소를 제공해야 합니다 `driver`, `bucket`, 및 `region`.

- 예: 원격 스토리지로 Commerce 설치

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- 예: 기존 Commerce에서 원격 스토리지 활성화

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>클라우드 인프라의 Adobe Commerce에 대해서는 다음을 참조하십시오. [클라우드 인프라에서 Commerce를 위한 원격 스토리지 구성](cloud-support.md).

## 제한 사항

원격 저장소와 데이터베이스 저장소를 동시에 활성화할 수 없습니다. 원격 저장소를 사용하는 경우 데이터베이스 저장소를 비활성화합니다.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

원격 스토리지를 활성화하면 기존 개발 환경에 영향을 줄 수 있습니다. 예를 들어 특정 PHP 파일 함수가 예상대로 작동하지 않을 수 있습니다. 파일 작업에 대해 Commerce Framework를 사용해야 합니다.

금지된 PHP 네이티브 함수 목록은에서 사용할 수 있습니다. [magento-coding-standard 저장소][code-standard].

## 콘텐츠 마이그레이션

특정 어댑터에 대해 원격 스토리지를 활성화한 후 CLI를 사용하여 기존 스토리지를 마이그레이션할 수 있습니다 _미디어_ 파일을 원격 저장소에 저장합니다.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>sync 명령은 `pub/media` 디렉토리, _아님_ 에서 파일 가져오기/내보내기 `var` 디렉토리. 다음을 참조하십시오 [예약된 가져오기/내보내기](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html) 다음에서 _Commerce 2.4 사용 안내서_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[code-standard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
