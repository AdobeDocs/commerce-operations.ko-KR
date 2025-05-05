---
title: 웹 크롤러 구성에 대한 우수 사례
description: '''robots.txt'' 및 ''sitemap.xml'' 파일을 사용하여 Adobe Commerce 사이트에 대한 지침을 웹 크롤러에 전달하는 방법을 알아봅니다.'
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# 웹 크롤러 구성에 대한 우수 사례

이 문서에서는 구성 및 보안을 포함하여 Adobe Commerce에서 `robots.txt` 및 `sitemap.xml` 파일을 사용하기 위한 모범 사례를 제공합니다. 이러한 파일은 웹 크롤러(일반적으로 검색 엔진 로봇)에게 웹 사이트의 페이지를 크롤링하는 방법을 지시합니다. 이러한 파일을 구성하면 사이트 성능 및 검색 엔진 최적화를 향상시킬 수 있습니다.

>[!NOTE]
>
>이러한 우수 사례는 기본 Adobe Commerce 상점 사용을 사용하는 프로젝트에만 적용됩니다. 다른 상점 솔루션(예: Adobe Experience Manager, Headless)을 사용하는 Adobe Commerce 프로젝트에는 적용되지 않습니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 클라우드 인프라의 Adobe Commerce

기본 Adobe Commerce 프로젝트에는 단일 웹 사이트, 스토어 및 스토어 보기를 포함하는 계층 구조가 포함되어 있습니다. 보다 복잡한 구현의 경우 _다중 사이트_ 상점 앞에 대한 추가 웹 사이트, 스토어 및 스토어 보기를 만들 수 있습니다.

### 단일 사이트 상점

단일 사이트 상점에 대해 `robots.txt` 및 `sitemap.xml` 파일을 구성할 때 다음 모범 사례를 따르십시오.

- 프로젝트에서 [`ece-tools`](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) 버전 2002.0.12 이상을 사용하고 있는지 확인하십시오.
- 관리 응용 프로그램을 사용하여 `robots.txt` 파일에 콘텐츠를 추가하십시오.

  >[!TIP]
  >
  >`<domain.your.project>/robots.txt`에 스토어에 대해 자동 생성된 `robots.txt` 파일을 봅니다.

- 관리 응용 프로그램을 사용하여 `sitemap.xml` 파일을 생성하십시오.

  >[!IMPORTANT]
  >
  >클라우드 인프라 프로젝트의 Adobe Commerce에서 읽기 전용 파일 시스템으로 인해 파일을 생성하기 전에 `pub/media` 경로를 지정해야 합니다.

- 사용자 지정 Fastly VCL 코드 조각을 사용하여 사이트의 루트에서 두 파일의 `pub/media/` 위치로 리디렉션합니다.

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- 웹 브라우저에서 파일을 보고 리디렉션을 테스트합니다. 예: `<domain.your.project>/robots.txt` 및 `<domain.your.project>/sitemap.xml`. 다른 경로가 아닌 리디렉션을 구성한 루트 경로를 사용하고 있는지 확인하십시오.

>[!INFO]
>
>자세한 지침은 [사이트 맵 및 검색 엔진 로봇 추가](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap)를 참조하십시오.


### 다중 사이트 상점

클라우드 인프라에서 Adobe Commerce의 단일 구현으로 여러 스토어를 설정하고 실행할 수 있습니다. [여러 웹 사이트 또는 스토어 설정](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites)을 참조하십시오.

[단일 사이트 상점](#single-site-storefronts)에 대해 `robots.txt` 및 `sitemap.xml` 파일을 구성하는 것과 동일한 모범 사례가 두 가지 중요한 차이점이 있는 다중 사이트 상점 상점에 적용됩니다.

- `robots.txt` 및 `sitemap.xml` 파일 이름에 해당 사이트의 이름이 포함되어 있는지 확인하십시오. For example:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- 약간 수정된 사용자 지정 Fastly VCL 코드 조각을 사용하여 사이트 루트에서 사이트 간 두 파일의 `pub/media` 위치로 리디렉션합니다.

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Commerce 온-프레미스

봇이 불필요한 콘텐츠를 검색하고 인덱싱하지 않도록 `robots.txt` 및 `sitemap.xml` 파일을 구성하려면 관리 응용 프로그램을 사용하십시오([검색 엔진 로봇](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html?lang=ko#search-engine-robots) 참조).

>[!TIP]
>
>온-프레미스 배포의 경우, 파일을 작성하는 위치는 Adobe Commerce 설치 방법에 따라 다릅니다. 파일을 `/path/to/commerce/pub/media/` 또는 `/path/to/commerce/media`에 작성하십시오. 어느 것이든 설치에 적합합니다.

## 보안

`robots.txt` 파일에 관리자 경로를 표시하지 않습니다. 관리자 경로가 노출된 것은 사이트 해킹과 잠재적인 데이터 손실에 대한 취약성입니다. `robots.txt` 파일에서 관리자 경로를 제거합니다.

`robots.txt` 파일을 편집하고 관리 경로의 모든 항목을 제거하는 단계는 [마케팅 사용 안내서 > SEO 및 검색 > 검색 엔진 로봇](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html?lang=ko#search-engine-robots)을 참조하십시오.

>[!TIP]
>
>도움이 필요하면 [Adobe Commerce 지원 티켓을 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ko#submit-ticket)하십시오.

## 추가 정보

- [웹 사이트, 스토어 및 스토어 조회수 이해](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [웹 사이트 추가](https://experienceleague.adobe.com/ko/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [Fastly를 사용하여 Adobe Commerce 사이트의 악성 트래픽을 차단하세요](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
- [robots.txt 클라우드 인프라 2.3.x에서 Adobe Commerce에 404 오류 발생](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html?lang=ko)
