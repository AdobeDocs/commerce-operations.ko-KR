---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---
# 보안 웹 서버 통신

이 항목에서는 TLS(Transport Layer Security) 암호화와 함께 웹 서버와 검색 엔진(Elasticsearch 또는 OpenSearch) 간의 통신을 보호하는 예를 설명합니다 [HTTP 기본 인증](https://datatracker.ietf.org/doc/html/rfc2617). 다른 유형의 인증도 선택적으로 구성할 수 있습니다. 우리는 그 정보에 대한 참조를 제공한다.

(이전 용어인 SSL(Secure Sockets Layer)은 TLS와 교환적으로 자주 사용됩니다. 이 주제에서는 *TLS*)

>[!WARNING]
>
>별도로 언급되지 않는 한 이 항목의 모든 명령을 `root` 권한.

## Recommendations

다음 사항을 권장합니다.

* 웹 서버에서 TLS를 사용합니다.

   TLS는 이 항목의 범위를 벗어납니다. 그러나 자체 서명된 인증서가 아닌 프로덕션 환경에서 실제 인증서를 사용하는 것이 좋습니다.

* 검색 엔진은 웹 서버와 동일한 호스트에서 실행됩니다. 다른 호스트에서 검색 엔진 및 웹 서버를 실행하는 것은 이 항목의 범위를 벗어납니다.

   검색 엔진과 웹 서버를 동일한 호스트에 배치하는 이점은 암호화된 통신을 가로채는 것을 불가능하게 한다는 것입니다. 검색 엔진 웹 서버는 Adobe Commerce 또는 Magento Open Source 웹 서버와 동일하지 않아도 됩니다. 예를 들어 Adobe Commerce은 Apache를 실행할 수 있으며 Elasticsearch/OpenSearch는 nginx를 실행할 수 있습니다.

   검색 엔진이 공개 웹에 노출된 경우 인증을 구성해야 합니다. 검색 엔진 인스턴스가 네트워크 내에서 보호되는 경우 필요하지 않을 수 있습니다. 호스팅 공급자와 협력하여 인스턴스를 보호하기 위해 구현해야 하는 보안 조치를 결정합니다.

## TLS에 대한 추가 정보

다음 리소스 중 하나를 참조하십시오.

* Apache

   * [Apache 2.4 강력한 암호화 방법](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Ubuntu 14.04용 Apache에서 SSL 인증서를 만드는 방법(Digitalocean 자습서)](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [CentOS(CentOS Wiki)를 사용하여 SSL 보안 웹 서버 설정](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Nginx SSL 종료](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Ubuntu 14.04용 Nginx에서 SSL 인증서를 만드는 방법(Digitalocean 튜토리얼)](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Nginx SSL 인증서 설치(digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
