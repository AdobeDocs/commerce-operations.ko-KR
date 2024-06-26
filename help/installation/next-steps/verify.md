---
title: 설치 확인
description: 다음 단계에 따라 온-프레미스 Adobe Commerce 설치가 성공했는지 확인합니다.
exl-id: 0bd7ec01-c616-4384-ae26-db2ce3668caf
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# 설치 확인

웹 브라우저의 상점으로 이동합니다. 예를 들어 설치 기본 URL이 `http://www.example.com`를 클릭하고 브라우저의 주소 또는 위치 표시줄에 주소를 입력합니다.

다음 그림은 샘플 상점 첫 페이지를 보여줍니다. 다음과 같이 표시된다면 설치가 성공적으로 완료되었습니다.

![Luma 테마를 사용한 상점](../../assets/installation/install-success_store-luma.png)

## 상점 확인(샘플 데이터 없음)

웹 브라우저의 상점으로 이동합니다. 예를 들어 설치 기본 URL이 `http://www.example.com`를 클릭하고 브라우저의 주소 또는 위치 표시줄에 주소를 입력합니다.

다음 그림은 샘플 상점 첫 페이지를 보여줍니다. 다음과 같이 표시된다면 설치가 성공적으로 완료되었습니다.

![성공적인 설치를 확인하는 Storefront](../../assets/installation/install-success_store.png)

페이지에 `404 (Not Found)` 오류 또는 이 스타일을 표시하지 않습니다. 참조: [문제 해결](https://support.magento.com/hc/en-us/articles/360032994352).

## 관리자 확인

웹 브라우저의 관리자로 이동합니다. 예를 들어 설치 기본 URL이 `http://www.example.com`, 그리고 관리자 URI는 `admin_au1nT`, 입력 `http://www.example.com/admin_au1nT` 를 클릭합니다.

(관리자 URI는 의 값으로 지정됩니다.) `backend-frontname` 설치 매개 변수.)

메시지가 표시되면 관리자로 로그인합니다.

다음 그림은 샘플 관리 페이지를 보여 줍니다. 다음과 같이 표시된다면 설치가 성공적으로 완료되었습니다.

![성공적인 설치를 확인하는 관리자](../../assets/installation/install_success_admin.png)

페이지에 스타일이 표시되지 않으면 [문제 해결](https://support.magento.com/hc/en-us/articles/360032994352).

다음과 유사한 404(찾을 수 없음) 오류가 발생하는 경우 을 참조하십시오. [브라우저에서 Adobe Commerce에 액세스할 때 PHP 버전 오류 또는 404](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
