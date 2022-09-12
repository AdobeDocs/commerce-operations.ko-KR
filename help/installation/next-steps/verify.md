---
title: 설치 확인
description: 다음 단계에 따라 온-프레미스 Adobe Commerce 또는 Magento Open Source 설치가 성공했는지 확인합니다.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# 설치 확인

로 이동합니다. [상점](https://glossary.magento.com/storefront) 참조하십시오. 예를 들어, 설치 기반인 경우 [URL](https://glossary.magento.com/url) is `http://www.example.com`을 눌러 브라우저의 주소 또는 위치 표시줄에 입력합니다.

다음 그림은 샘플 저장소 전면 페이지를 보여줍니다. 다음과 같이 표시되는 경우 설치가 성공했습니다!

![Luma 테마가 있는 상점](../../assets/installation/install-success_store-luma.png)

## 저장소 확인(샘플 데이터 없음)

웹 브라우저에 있는 저장소로 이동합니다. 예를 들어 설치 기본 URL이 `http://www.example.com`을 눌러 브라우저의 주소 또는 위치 표시줄에 입력합니다.

다음 그림은 샘플 저장소 전면 페이지를 보여줍니다. 다음과 같이 표시되는 경우 설치가 성공했습니다!

![성공적으로 설치를 확인하는 저장소](../../assets/installation/install-success_store.png)

페이지에 `404 (Not Found)` 오류 또는 스타일을 표시하지 않습니다. [문제 해결](https://support.magento.com/hc/en-us/articles/360032994352).

## 관리자 확인

로 이동합니다. [관리](https://glossary.magento.com/magento-admin) 참조하십시오. 예를 들어 설치 기본 URL이 `http://www.example.com`, 그리고 관리자 URI는 `admin_au1nT`, 입력 `http://www.example.com/admin_au1nT` 를 클릭합니다.

(다음 [관리](https://glossary.magento.com/admin) URI는 `backend-frontname` 설치 매개 변수)

메시지가 표시되면 관리자로 로그인합니다.

다음 그림은 샘플 관리 페이지를 보여줍니다. 다음과 같이 표시되는 경우 설치가 성공했습니다!

![성공적인 설치를 확인하는 관리자](../../assets/installation/install_success_admin.png)

페이지에 스타일이 표시되지 않으면 [문제 해결](https://support.magento.com/hc/en-us/articles/360032994352).

다음과 유사한 404(찾을 수 없음) 오류가 발생하는 경우 다음을 참조하십시오 [브라우저에서 Adobe Commerce에 액세스할 때 PHP 버전 오류 또는 404](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
