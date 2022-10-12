---
title: 원격 스토리지에 대한 이미지 크기 조정 구성
description: 서버측 이미지 크기 조정을 구성하여 디스크 리소스를 최적화합니다.
source-git-commit: 7fc5d561baa3c2a4aab160a35a1c8a302a62a3b1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 1%

---

# 원격 스토리지에 대한 이미지 크기 조정 구성

기본적으로 Adobe Commerce은 애플리케이션 측에서 이미지 크기 조정을 지원합니다. 그러나 원격 스토리지 모듈을 사용하면 Nginx를 사용하여 디스크 리소스를 저장하고 디스크 사용을 최적화할 수 있는 서버 측에서 이미지 크기 조정을 오프로드할 수 있습니다.

다음 다이어그램은 Nginx가 캐시에서 이미지를 검색, 크기 조정 및 저장하는 방법을 보여줍니다. 크기 조정은 높이 및 폭과 같이 URL에 포함된 매개 변수에 의해 결정됩니다.

![이미지 크기 조정](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>클라우드 인프라 프로젝트에 대한 Adobe Commerce의 경우 다음을 참조하십시오. [Commerce on Cloud 인프라를 위한 원격 스토리지 구성](cloud-support.md)

## Adobe Commerce에서 URL 형식 구성

서버 측에서 이미지 크기를 조정하려면 이미지의 높이, 너비 및 위치(URL)에 대한 인수를 제공하도록 Adobe Commerce을 구성해야 합니다.

**서버측 이미지 크기 조정을 위해 Commerce를 구성하려면**:

1. 에서 _관리_ 패널, **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. 오른쪽 창에서 **[!UICONTROL Url options]**.

1. 에서 _카탈로그 미디어 URL 형식_ 섹션, 지우기 **[!UICONTROL Use system value]**.

1. 을(를) 선택합니다 `Image optimization based on query parameters` 의 URL **_카탈로그 미디어 URL 형식_** 필드.

1. 클릭 **[!UICONTROL Save Config]**.

1. 계속 [Nginx 구성](#configure-nginx).

## Nginx 구성

서버측 이미지 크기 조정을 계속 구성하려면 다음을 준비해야 합니다 `nginx.conf` 파일 및 `proxy_pass` 선택한 어댑터의 값입니다.

**Nginx에서 이미지 크기를 조정하려면**:

1. 설치 [Nginx 이미지 필터 모듈][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. 만들기 `nginx.conf` 포함된 템플릿을 기반으로 하는 파일 `nginx.conf.sample` 파일. For example:

   ```conf
   location ~* \.(jpg|jpeg|png|gif|webp)$ {
       set $width "-";
       set $height "-";
       if ($arg_width != '') {
           set $width $arg_width;
       }
       if ($arg_height != '') {
           set $height $arg_height;
       }
       image_filter resize $width $height;
       image_filter_jpeg_quality 90;
   }
   ```

1. [_선택 사항입니다_] 구성 `proxy_pass` 특정 어댑터에 대한 값입니다.

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
