---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# 중요 데이터

Adobe Commerce 및 Magento Open Source은 암호화 키를 사용하여 다음을 암호화합니다.

* 신용 카드 정보
* 관리 구성에 지정된 사용자 이름 및 암호(예: 결제 게이트웨이에 로그인)
* 네트워크를 통해 전송된 CAPTCHA 값

Adobe Commerce 및 Magento Open Source 작업 *not* 암호화:

* 관리 및 고객 사용자 이름 및 암호(이 암호는 해시됨)
* 주소
* 전화 번호
* 신용 카드 번호를 제외한 기타 유형의 개인 식별 정보
