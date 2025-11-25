---
title: Adobe Commerce 소프트웨어 다운로드
description: Adobe Commerce 소프트웨어를 다운로드하는 방법을 알아봅니다.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Adobe Commerce 소프트웨어 다운로드

전 세계 24만 명의 상인이 당사의 전자 상거래 소프트웨어를 신뢰하고 있습니다. 설치를 시작하는 데 도움이 되는 몇 가지 정보를 수집했습니다.

## 소프트웨어를 가져오는 방법

[제품 가용성 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability)에서 Adobe 작성 확장과 Adobe Commerce 및 Magento Open Source용 Commerce 서비스의 가용성 및 호환성을 확인하십시오.

>[!NOTE]
>
>이제 정책 변경으로 인해 Adobe Commerce 코드베이스가 작성기를 통해서만 배포됩니다. 코드 베이스를 다운로드 섹션에서 더 이상 사용할 수 없으므로 작성기를 사용하여 나열된 Adobe Commerce 버전을 다운로드하십시오.
>
>자세한 내용은 [클라우드 인프라의 Adobe Commerce에서 청구 정책에 액세스하고 코드베이스를 다운로드할 수 없음](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26611)을 참조하세요.

Adobe Commerce 설치를 시작하려면 다음 표를 참조하십시오.

<table>
    <tbody>
        <tr>
            <th>사용자 요구 사항</th>
            <th>설명</th>
            <th>높은 수준의 설치 및 업그레이드 단계</th>
            <th>시작 링크</th>
        </tr>
    <tr>
        <td><p>통합자, 패키지</p></td>
        <td><p>설치된 모든 구성 요소에 대한 전체 제어를 원하며, 고도로 기술적으로 애플리케이션 서버에 액세스할 수 있고, Magento Open Source을 다른 구성 요소와 다시 패키징할 수 있습니다.</p>
        </td>
        <td><ol><li>사용할 구성 요소 목록을 포함하는 작성기 <em>프로젝트</em>을(를) 만듭니다.</li>
            <li>작성기를 사용하여 패키지 종속성을 업데이트하고, <code>composer create-project</code>을(를) 사용하여 작성기 메타패키지를 가져옵니다.</li>
            <li><a href="../advanced.md">명령줄</a>을 사용하여 응용 프로그램을 설치합니다.</li>
        <li><a href="../../upgrade/implementation/perform-upgrade.md">명령줄</a>을 사용하여 응용 프로그램 및 확장을 업그레이드합니다.</li></ol></td>
        <td><p><a href="../composer.md">메타패키지 가져오기</a></p></td>
    </tr>
    <tr>
        <td><p>기여 개발자</p></td>
        <td><p>Magento Open Source 코드 베이스에 기여하고 버그를 파일링하며 애플리케이션을 사용자 정의합니다. 고도로 기술적이고 자체 개발 서버가 있으며 작성기 및 GitHub를 이해합니다.</p>
            <p>프로덕션 환경에서 응용 프로그램을 <em>사용할 수 없습니다</em>.</p>
      <p><a href="../../upgrade/developer/git-installs.md">작성기 및 Git 명령</a>을 사용하여 업그레이드해야 합니다.</p></td>
        <td><ol><li>GitHub 저장소를 복제합니다.</li>
            <li>작성기를 사용하여 패키지 종속성을 업데이트합니다.</li>
            <li><a href="../advanced.md">명령줄</a>을 사용하여 응용 프로그램을 설치합니다.</li>
            <li><a href="../../upgrade/developer/git-installs.md">작성기 및 Git 명령</a>을 사용하여 응용 프로그램을 업그레이드합니다.</li>
            <li><code>app/code</code> 디렉터리에서 코드를 사용자 지정합니다.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository">GitHub 리포지토리 복제</a></p></td>
    </tr>
    </tbody>
</table>

## 유용한 정보

페이지 왼쪽에 있는 링크를 사용하여 설치의 각 부분에서 항목을 탐색합니다.

## 필요한 서버 권한

UNIX 시스템에서는 웹 서버, PHP와 같은 소프트웨어를 설치하고 구성하려면 `root` 권한이 필요합니다. 이 소프트웨어를 설치해야 하는 경우 `root` 액세스 권한이 있는지 확인하십시오.

웹 서버가 해당 파일과 상호 작용할 수 없으므로 *not* 응용 프로그램을 웹 서버 docroot에 `root` 사용자로 설치하지 마십시오.

`root`파일 시스템 소유자[를 만들고 해당 소유자를 웹 서버의 그룹에 추가하려면 ](file-system/overview.md) 권한이 필요합니다. 파일 시스템 소유자를 사용하여 명령줄에서 `bin/magento` 명령을 실행하고 작업을 예약하는 cron 작업을 설정합니다.
