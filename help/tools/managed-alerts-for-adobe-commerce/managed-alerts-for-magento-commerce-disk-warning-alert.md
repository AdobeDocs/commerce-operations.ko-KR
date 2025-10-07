---
title: 'Adobe Commerce에 대한 관리 경고: 디스크 경고 경고'
description: 이 문서에서는  [!DNL New Relic]에서 Adobe Commerce에 대한 경고 디스크 경고를 받았을 때의 문제 해결 단계를 제공합니다. 문제를 해결하기 위해 즉각적인 조치가 필요합니다.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 90ea4384-97aa-499d-93c1-b40c3a4eed42
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Adobe Commerce에 대한 관리 경고: 디스크 경고 경고

이 문서에서는 [!DNL New Relic]에서 Adobe Commerce에 대한 경고 디스크 경고를 받았을 때의 문제 해결 단계를 제공합니다. 문제를 해결하기 위해 즉각적인 조치가 필요합니다. 선택한 경고 알림 채널에 따라 경고는 다음과 같이 표시됩니다.

![저장소 사용 임계값을 초과하는 디스크 공간 경고 알림](../../assets/managed-alerts/disk-warning-magento-managed.png){width="500"}

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, Pro 플랜 아키텍처.

## 문제

[!DNL New Relic]Adobe Commerce에 대한 관리 경고[에 등록했으며 경고 임계값 중 하나 이상을 초과한 경우 &#x200B;](managed-alerts-for-magento-commerce.md)에서 경고를 받게 됩니다. 이러한 경고는 지원 및 엔지니어링의 인사이트를 사용하여 고객에게 표준 세트를 제공하기 위해 Adobe에서 개발했습니다.

<u> **실행!** </u>

* 이 경고가 지워질 때까지 예약된 배포를 중단합니다.
* 사이트가 응답하지 않거나 완전히 응답하지 않는 경우 즉시 사이트를 유지 관리 모드로 전환합니다. 단계는 Commerce 설치 가이드의 [유지 관리 모드 활성화 또는 비활성화](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)를 참조하십시오. 문제 해결을 위해 사이트에 계속 액세스할 수 있도록 제외 IP 주소 목록에 IP를 추가해야 합니다. 단계는 Commerce 설치 가이드의 [제외 IP 주소 목록 유지](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)를 참조하십시오.

<u> **안 함!** </u>

* 사이트에 추가 페이지 보기를 가져올 수 있는 추가 마케팅 캠페인을 시작합니다.
* 인덱서 또는 추가 크론을 실행하여 CPU 또는 디스크에 추가 스트레스를 발생시킬 수 있습니다.
* 주요 관리 작업(예: Commerce 관리, 데이터 가져오기/내보내기)을 수행합니다.
* 캐시를 지웁니다. 경고 원인을 조사하고 해결하기 전에 &quot;안 함&quot; 작업을 수행하면 사이트가 응답하지 않을 수 있습니다(아직 사이트 중단이 발생하지 않은 경우).

## 솔루션

다음 단계에 따라 원인을 식별하고 해결하십시오.

1. [!DNL New Relic]에서 사용 빈도가 가장 높은 디스크를 검토하십시오. 단계는 **[!UICONTROL Storage]**&#x200B;인프라 모니터링 호스트 페이지 [[!DNL New Relic]  탭[!UICONTROL Storage]의 &#x200B;](https://docs.newrelic.com/docs/infrastructure/infrastructure-data/infrastructure-ui-pages/infra-hosts-ui-page/#storage) 탭을 참조하십시오.
   * [!DNL New Relic]에서 디스크 사용량이 느리게 증가하는 경우 다음 옵션을 시도해 보십시오.
      * 공간 할당을 조정하여 디스크 공간을 최적화합니다. 단계는 Commerce on Cloud Guide의 [디스크 공간 관리](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space)를 참조하십시오. 추가 디스크 공간을 요청해야 할 수도 있습니다(Adobe 계정 팀에 문의).
      * MySQL의 디스크 공간을 정리합니다. 단계는 [MySQL 디스크 공간이 부족함](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud)을 참조하세요.
      * [!DNL New Relic]에 디스크 사용량이 급격히 증가하는 경우 디렉터리에서 파일이 매우 빠르게 증가하는 문제가 있음을 나타낼 수 있습니다. 다음 사항을 확인하십시오.
         1. CLI/터미널에서 다음 명령을 실행하여 문제를 확인하려면 전체 디스크 공간을 확인하십시오. `df -h`
         1. 예기치 않게 용량이 크고 디스크 사용량이 증가하는 디렉토리를 식별한 후 영향을 받는 파일 시스템을 확인해야 합니다. 다음 예제에서는 파일 디렉터리 `pub/media/`을(를) 확인하는 방법을 보여 줍니다. Adobe Commerce이 로그 및 대용량 미디어 파일을 저장하는 데 사용하는 디렉터리입니다. 그러나 예기치 않은 디스크 사용량을 표시하는 모든 디렉터리에 대해 이 명령을 실행해야 합니다. `du -sch ~/pub/media/*`.

터미널의 출력에서 디스크 사용량이 급격히 증가하는 이러한 디렉토리 중 하나에 있는 파일을 표시하는 경우 파일의 콘텐츠가 필요하지 않은 것을 알고 있다면 파일을 제거하는 것이 좋습니다. 이 작업을 수행하는 데 익숙하지 않은 경우 [Adobe Commerce 지원 티켓을 제출](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case)하십시오.
