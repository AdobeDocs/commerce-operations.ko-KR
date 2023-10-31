---
title: 웹 크롤러 구성에 대한 우수 사례
description: '''robots.txt'' 및 ''sitemap.xml'' 파일을 사용하여 Adobe Commerce 사이트에 대한 지침을 웹 크롤러에 전달하는 방법을 알아봅니다.'
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: e1e7ad76b1df8e920ab7f9740fd4be8dc7335954
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---


# 웹 크롤러 구성에 대한 우수 사례

이 문서에서는 사용 모범 사례를 제공합니다. `robots.txt` 및 `sitemap.xml` 구성 및 보안을 포함한 Adobe Commerce의 파일. 이러한 파일은 웹 크롤러(일반적으로 검색 엔진 로봇)에게 웹 사이트의 페이지를 크롤링하는 방법을 지시합니다. 이러한 파일을 구성하면 사이트 성능 및 검색 엔진 최적화를 향상시킬 수 있습니다.

>[!NOTE]
>
>이러한 우수 사례는 기본 Adobe Commerce 상점 사용을 사용하는 프로젝트에만 적용됩니다. 다른 상점 솔루션(예: Adobe Experience Manager, Headless)을 사용하는 Adobe Commerce 프로젝트에는 적용되지 않습니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 클라우드 인프라의 Adobe Commerce

기본 Adobe Commerce 프로젝트에는 단일 웹 사이트, 스토어 및 스토어 보기를 포함하는 계층 구조가 포함되어 있습니다. 보다 복잡한 구현의 경우 다음에 대한 추가 웹 사이트, 스토어 및 스토어 보기를 만들 수 있습니다 _다중 사이트_ 가게 앞이야

### 단일 사이트 상점

를 구성할 때 다음 모범 사례를 따르십시오. `robots.txt` 및 `sitemap.xml` 단일 사이트 상점 파일:

- 프로젝트가 다음을 사용하고 있는지 확인합니다. [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) 버전 2002.0.12 이상
- 관리 애플리케이션을 사용하여에 콘텐츠를 추가합니다. `robots.txt` 파일.

  >[!TIP]
  >
  >자동 생성 보기 `robots.txt` 다음 위치에 저장소용 파일: `<domain.your.project>/robots.txt`.

- 관리 애플리케이션을 사용하여 다음을 생성합니다. `sitemap.xml` 파일.

  >[!IMPORTANT]
  >
  >클라우드 인프라 프로젝트의 Adobe Commerce에서 읽기 전용 파일 시스템으로 인해 `pub/media` 파일을 생성하기 전 경로입니다.

- 사용자 지정 Fastly VCL 코드 조각을 사용하여 사이트 루트에서 `pub/media/` 두 파일의 위치:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- 웹 브라우저에서 파일을 보고 리디렉션을 테스트합니다. 예를 들어, `<domain.your.project>/robots.txt` 및 `<domain.your.project>/sitemap.xml`. 다른 경로가 아닌 리디렉션을 구성한 루트 경로를 사용하고 있는지 확인하십시오.

>[!INFO]
>
>다음을 참조하십시오 [사이트 맵 및 검색 엔진 로봇 추가](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) 자세한 지침은 을 참조하십시오.


### 다중 사이트 상점

클라우드 인프라에서 Adobe Commerce의 단일 구현으로 여러 스토어를 설정하고 실행할 수 있습니다. 다음을 참조하십시오 [여러 웹 사이트 또는 스토어 설정](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

를 구성하는 것과 동일한 모범 사례 `robots.txt` 및 `sitemap.xml` 다음에 대한 파일 [단일 사이트 상점](#single-site-storefronts) 다음 두 가지 중요한 차이점이 있는 다중 사이트 상점에 적용됩니다.

- 다음을 확인하십시오. `robots.txt` 및 `sitemap.xml` 파일 이름에는 해당 사이트의 이름이 들어 있습니다. For example:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- 사이트 루트에서 로 리디렉션하려면 약간 수정된 사용자 지정 Fastly VCL 코드 조각을 사용하십시오. `pub/media` 사이트에서 두 파일의 위치:

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

관리 애플리케이션을 사용하여 다음을 구성하십시오. `robots.txt` 및 `sitemap.xml` 봇이 불필요한 콘텐츠를 검색하고 색인화하지 못하도록 하는 파일(참조) [검색 엔진 로봇](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>온-프레미스 배포의 경우, 파일을 작성하는 위치는 Adobe Commerce 설치 방법에 따라 다릅니다. 파일 쓰기 대상 `/path/to/commerce/pub/media/` 또는 `/path/to/commerce/media`, 어느 것이든 설치에 적합합니다.

## 보안

에 관리자 경로를 표시하지 않음 `robots.txt` 파일. 관리자 경로가 노출된 것은 사이트 해킹과 잠재적인 데이터 손실에 대한 취약성입니다. 에서 관리자 경로 제거 `robots.txt` 파일.

을(를) 편집하는 단계는 `robots.txt` 파일 및 관리 경로의 모든 항목 제거, 다음을 참조하십시오. [마케팅 사용 안내서 > SEO 및 검색 > 검색 엔진 로봇](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>도움이 필요하시면 [Adobe Commerce 지원 티켓 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 추가 정보

- [웹 사이트, 스토어 및 스토어 조회수 이해](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [웹 사이트 추가](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Fastly를 사용하여 Adobe Commerce 사이트에 대한 악의적인 트래픽을 차단하십시오](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt 클라우드 인프라 2.3.x에서 Adobe Commerce에 404 오류 발생](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
