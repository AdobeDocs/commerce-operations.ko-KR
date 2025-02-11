---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# 2024년 8월 보안 패치 하이라이트

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

* [!DNL one-time passwords]**에 대한**&#x200B;속도 제한—이제 [!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)] 유효성 검사에서 속도 제한을 사용하도록 설정하는 다음 새 시스템 구성 옵션을 사용할 수 있습니다.

   * [!UICONTROL **2단계 인증에 대한 다시 시도 제한**]
   * [!UICONTROL **2단계 인증 잠금 시간(초)**]

  Adobe은 무차별 대입 공격을 완화하기 위해 재시도 횟수를 제한하려면 2FA OTP 유효성 검사에 대한 임계값을 설정하는 것이 좋습니다. 자세한 내용은 _구성 참조 안내서_&#x200B;의 [보안 > 2FA](https://experienceleague.adobe.com/en/docs/commerce-admin/config/security/2fa)를 참조하십시오. <!-- AC-12095 -->

* **암호화 키 회전**—이제 암호화 키를 변경하는 데 새 CLI 명령을 사용할 수 있습니다. 자세한 내용은 [암호화 키 순환 문제 해결: CVE-2024-34102](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102) 기술 문서를 참조하십시오.

* **[CVE-2020-27511](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)**&#x200B;에 대한 수정 사항 - [!DNL Prototype.js] 보안 취약점을 해결합니다.<!-- AC-11936 -->

* **CVE-2024-39397](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)**&#x200B;에 대한 수정 사항 - 원격 코드 실행 보안 취약점을 해결합니다. [ 이 취약성은 온-프레미스 또는 자체 호스팅 배포용 Apache 웹 서버를 사용하는 가맹점에 영향을 줍니다. 이 수정 사항은 격리된 패치로도 사용할 수 있습니다. 자세한 내용은 [Adobe Commerce에 사용 가능한 보안 업데이트 - APSB24-61](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61) 기술 자료 문서를 참조하십시오.<!-- ACSD-60551 -->
