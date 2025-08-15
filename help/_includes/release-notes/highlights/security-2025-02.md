---
source-git-commit: 6ca34e8713f4f138961786de206cd360f0bc1be7
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---
# 2025년 2월 보안 패치 하이라이트

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

* **암호화 키 관리 및 데이터 다시 암호화**—암호화 키 관리를 새롭게 디자인하여 유용성을 높이고 이전 제한 사항과 버그를 제거합니다.<!-- AC-12679 -->

  이제 [변경](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key) 키와 [다시 암호화](https://developer.adobe.com/commerce/php/development/security/data-encryption/) 특정 시스템 구성, 결제 및 사용자 지정 필드 데이터에 새 CLI 명령을 사용할 수 있습니다. 이 릴리스에서는 관리 UI의 키 변경이 더 이상 지원되지 않습니다. CLI 명령을 사용해야 합니다.

* **[CVE-2025-24434](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)**&#x200B;에 대한 수정 사항 - 인증 취약점을 해결합니다.

  이 수정 사항은 격리된 패치로도 사용할 수 있습니다. 자세한 내용은 [기술 자료 문서](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08)를 참조하세요.<!-- AC-12755 -->

* **TinyMCE 버전 다운그레이드** - 라이선스 호환성 문제를 해결하기 위해 TinyMCE 종속성이 버전 7에서 6.8.5로 다운그레이드되었습니다.

  이 변경 사항은 Adobe이 대체 오픈 소스 WYSIWYG 편집기를 평가하는 동안 지속적인 규정 준수를 보장합니다.
