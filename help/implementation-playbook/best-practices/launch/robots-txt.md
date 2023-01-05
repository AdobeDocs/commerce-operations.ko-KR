---
title: '''robots.txt'' 및 ''sitemap.xml'' 파일 구성 우수 사례'
description: 웹 크롤러에 Adobe Commerce 사이트에 대한 지침을 전달하는 방법을 알아봅니다.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# 구성 우수 사례 `robots.txt` 및 `sitemap.xml` 파일

이 문서에서는 사용에 대한 모범 사례를 제공합니다 `robots.txt` 및 `sitemap.xml` 구성 및 보안을 포함한 Adobe Commerce 파일. 이러한 파일은 웹 로봇(일반적으로 검색 엔진 로봇)이 웹 사이트에서 페이지를 크롤링하는 방법을 지시합니다. 이러한 파일을 구성하면 사이트 성능과 검색 엔진 최적화를 향상시킬 수 있습니다.

>[!NOTE]
>
>이러한 우수 사례는 기본 Adobe Commerce 스토어를 사용하는 프로젝트에만 적용됩니다. 다른 상점 솔루션(예: Adobe Experience Manager, 헤드리스)을 사용하는 Adobe Commerce 프로젝트에는 적용되지 않습니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## Adobe Commerce on cloud 인프라

기본 Adobe Commerce 프로젝트에는 단일 웹 사이트, 스토어 및 저장소 보기를 포함하는 계층 구조가 포함되어 있습니다. 보다 복잡한 구현을 위해 추가 웹 사이트를 만들고, 웹 사이트에 대한 보기를 저장하고, _다중 사이트_ 상점.

### 단일 사이트 저장소

을 구성할 때 다음 모범 사례를 따르십시오 `robots.txt` 및 `sitemap.xml` 단일 사이트 저장소 파일:

- 프로젝트가 [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) 버전 2002.0.12 이상.
- Admin 애플리케이션을 사용하여 컨텐츠를 `robots.txt` 파일.

   >[!TIP]
   >
   >자동 생성 보기 `robots.txt` 저장할 파일 `<domain.your.project>/robots.txt`.

- 관리 애플리케이션을 사용하여 `sitemap.xml` 파일.

   >[!IMPORTANT]
   >
   >클라우드 인프라 프로젝트에서 Adobe Commerce의 읽기 전용 파일 시스템으로 인해 `pub/media` 파일을 생성하기 전에 경로를 지정합니다.

- 사용자 지정 실제 VCL 코드 조각을 사용하여 사이트의 루트에서 로 리디렉션합니다. `pub/media/` 두 파일의 위치:

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
   }
   ```

- 웹 브라우저에서 파일을 보고 리디렉션을 테스트합니다. 예, `<domain.your.project>/robots.txt` 및 `<domain.your.project>/sitemap.xml`. 다른 경로가 아니라 리디렉션을 구성한 루트 경로를 사용하고 있는지 확인하십시오.

>[!INFO]
>
>자세한 내용은 [사이트 맵 및 검색 엔진 로봇 추가](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) 자세한 지침


### 다중 사이트 상점

클라우드 인프라에서 Adobe Commerce을 단일 구현으로 사용하여 여러 스토어를 설정하고 실행할 수 있습니다. 자세한 내용은 [여러 웹 사이트 또는 저장소 설정](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

구성을 위한 동일한 모범 사례입니다 `robots.txt` 및 `sitemap.xml` 파일 [단일 사이트 저장소](#single-site-storefronts) 에서는 두 가지 중요한 차이점이 있는 다중 사이트 스토어프런트에 적용됩니다.

- 다음을 확인합니다. `robots.txt` 및 `sitemap.xml` 파일 이름에는 해당 사이트의 이름이 포함됩니다. For example:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- 약간 수정된 사용자 정의 실제 VCL 코드 조각을 사용하여 사이트의 루트에서 로 리디렉션합니다. `pub/media` 사이트에서 두 파일에 대한 위치:

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

관리 애플리케이션을 사용하여 `robots.txt` 및 `sitemap.xml` 봇이 불필요한 컨텐츠를 스캔 및 인덱싱하지 못하도록 하는 파일(참조) [검색 엔진 로봇](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>온-프레미스 배포의 경우, 파일을 쓰는 위치는 Adobe Commerce을 설치하는 방법에 따라 다릅니다. 파일에 쓰기 `/path/to/commerce/pub/media/` 또는 `/path/to/commerce/media`, 어느 것이 설치에 적합한지 확인하십시오.

## 보안

관리 경로를 `robots.txt` 파일. 관리자 경로가 노출되면 사이트 해킹 및 데이터 손실의 위험이 있습니다. 에서 관리 경로 제거 `robots.txt` 파일.

를 편집하는 단계는 `robots.txt` 파일 및 관리 경로의 모든 항목 제거 [마케팅 사용 안내서 > SEO 및 검색 > 검색 엔진 로봇](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>도움이 필요하면, [Adobe Commerce 지원 티켓 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 추가 정보

- [웹 사이트, 저장소 및 저장소 보기 이해](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [웹 사이트 추가](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Adobe Commerce 사이트에 대한 악성 트래픽을 차단하려면 페이스트를 사용합니다](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt가 클라우드 인프라 2.3.x의 Adobe Commerce에서 404 오류를 발생합니다](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
