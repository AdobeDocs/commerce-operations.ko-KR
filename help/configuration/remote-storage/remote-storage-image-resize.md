---
title: 원격 스토리지에 대한 이미지 크기 조정 구성
description: 서버측 이미지 크기 조정을 구성하여 디스크 리소스를 최적화합니다.
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# 원격 스토리지에 대한 이미지 크기 조정 구성

기본적으로 Adobe Commerce은 응용 프로그램 쪽에서 이미지 크기 조정을 지원합니다. 그러나 원격 스토리지 모듈을 활성화하면 Ngix 를 사용하여 이미지 크기 조정을 서버 측으로 오프로드할 수 있으므로 디스크 자원을 절약하고 디스크 사용을 최적화할 수 있습니다.

다음 다이어그램은 Nginx가 캐시에 이미지를 검색, 크기 조정 및 저장하는 방법을 보여 줍니다. 크기 조정은 높이 및 폭과 같이 URL에 포함된 매개 변수에 의해 결정됩니다.

![이미지 크기 조정](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>클라우드 인프라 프로젝트의 Adobe Commerce에 대해서는 [클라우드 인프라의 Commerce에 대한 원격 저장소 구성](cloud-support.md)을 참조하십시오.

## Adobe Commerce에서 URL 형식 구성

서버측에서 이미지 크기를 조정하려면 이미지의 높이, 너비 및 위치(URL)에 대한 인수를 제공하도록 Adobe Commerce을 구성해야 합니다.

**서버측 이미지 크기 조정을 위해 Commerce을 구성하려면**:

1. _관리자_ 패널에서 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**&#x200B;을(를) 클릭합니다.

1. 오른쪽 창에서 **[!UICONTROL Url options]**&#x200B;을(를) 확장합니다.

1. _카탈로그 미디어 URL 형식_ 섹션에서 **[!UICONTROL Use system value]**&#x200B;을(를) 지웁니다.

1. `Image optimization based on query parameters`카탈로그 미디어 URL 형식&#x200B;**_필드에서_** URL을 선택합니다.

1. **[!UICONTROL Save Config]**&#x200B;을(를) 클릭합니다.

1. [Nginx 구성](#configure-nginx)을 계속합니다.

## Nginx 구성

서버측 이미지 크기 조정을 계속 구성하려면 `nginx.conf` 파일을 준비하고 선택한 어댑터에 대해 `proxy_pass` 값을 제공해야 합니다.

**Nginx에서 이미지 크기를 조정하려면**:

1. [Nginx 이미지 필터 모듈][nginx-module]을 설치하십시오.

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. 포함된 템플릿 `nginx.conf` 파일을 기반으로 `nginx.conf.sample` 파일을 만듭니다. For example:

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

1. [_선택 사항_] 특정 어댑터에 대해 `proxy_pass` 값을 구성합니다.

   - [Amazon Simple Storage Service(Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
