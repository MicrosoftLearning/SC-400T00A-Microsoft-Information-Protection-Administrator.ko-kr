---
lab:
  title: 연습 3 - 서비스 기반 보존 구성
  module: Module 3 - Implement Data Lifecycle and Records Management
---

# 랩 3 - 연습 3 - 서비스 기반 보존 구성

Contoso Ltd의 규정 준수 관리 Joni Sherman의 역할을 맡게 됩니다. 법률 부서에서는 불만을 품은 직원이 회사 데이터를 삭제하지 못하도록 도와야 합니다.

## 작업 1 – 사서함 보존 구성

이 작업에서는 직원의 사서함에 있는 모든 콘텐츠가 삭제되지 않도록 사서함 보존을 활성화합니다.

1. 클라이언트 1 가상 머신(LON-CL1)에 lon-cl1\admin** 계정으로 **로그인합니다.

1. **Microsoft Edge**에서 **`https://admin.exchange.microsoft.com`** 로 이동한 다음 Exchange 관리 센터에 **Joni Sherman**으로 로그인합니다. JoniS@WWLxZZZZZZ.onmicrosoft.com으로 로그인합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID입니다).

1. 표시되는 경우 모든 팁 창을 닫습니다.

1. Exchange 관리 센터의 왼쪽 탐색 창에서 받는 사람을 확장**한** 다음 사서함을** 선택합니다**.

1. Alex Wilber**의 **사서함을 선택한 다음 연필 아이콘을 선택하여 사서함을 편집합니다.

1. 사서함 목록에서 Alex Wilber**를 선택하면 **오른쪽에 Alex의 사서함 설정이 표시된 플라이아웃 페이지가 표시됩니다.

1. Alex Wilber의 플라이아웃 페이지에서 기타** 탭을 **선택합니다.

1. 소송 보존에서 **소송 보존** 관리를 선택합니다**.**

1. **소송 보존 관리 페이지에서 소송 보존**** 설정을 해제_에서 _켜_기로 _전환**하여 소송 보존 설정을 표시합니다.

1. 다음 보류 설정을 설정합니다.

    - **보존 기간(일).**: 90
    - **참고(사용자에게 표시됨)** : 사서함이 다음 90일 동안 보류되었습니다. 메시지를 삭제할 수 없습니다.

1. 저장을 선택한 **다음 소송 보존이 업데이트**됨을 **표시하는 메시지가** 표시됩니다.

사용자 환경의 사서함에서 사서함 보존을 성공적으로 활성화하고 액세스 권한이 있는 모든 사용자가 사서함의 콘텐츠를 영구적으로 삭제하지 못하도록 중지했습니다. 보류를 적용하는 데 최대 4시간이 걸릴 수 있습니다.  다음 작업을 즉시 진행할 수 있습니다.

## 작업 2 – SharePoint 문서 복구

이 작업에서는 삭제된 문서를 삭제하고 복원하여 사서함에 대한 소송 보존에 대한 정보를 받은 후 직원이 삭제할 수 있는 문서를 복원할 수 있도록 합니다.

1. 클라이언트 1 VM(LON-CL1)에 lon-cl1\admin** 계정으로 **로그인합니다.

1. **Microsoft Edge**에서 **`https://www.office.com`** 으로 이동한 다음, Microsoft 365에 **Joni Sherman**으로 로그인합니다.

1. 시작 화면이 표시되면 닫습니다. Office 365 앱 알림이 표시되면 닫습니다.

1. Microsoft Office 365 방문 페이지의 왼쪽 위 모서리에서 앱 시작 관리자 아이콘(9개의 점이 있는 아이콘)을 선택한 다음 하위 메뉴에서 SharePoint**를 선택합니다**.

1. **SharePoint 시작 페이지**가 나타나면 닫습니다.

1. SharePoint 방문 페이지에서 혜택 @ Contoso** SharePoint 사이트를 선택합니다**.

1. 왼쪽 탐색 창에서 문서를** 선택합니다**.

1. **[문서]** 페이지에서 [휴가 정책 **]의 **왼쪽에 있는 검사 상자를 선택한 다음, 작업 모음에서 삭제**를 선택합니다**.

1. **삭제?** 대화 상자에서 삭제**를 선택합니다**.

1. 왼쪽 탐색 창에서 휴지통을 선택한 **다음 앞에 있는 검사 상자를 선택하여 Vacation Policies.pptx**를 강조 **표시**합니다.

1. 위쪽 작업 모음에서 복원**을 선택합니다**.

1. 왼쪽 탐색 창에서 문서를** 선택하고 **파일이 복원되었는지 검토합니다.

SharePoint 사이트에서 삭제된 문서를 성공적으로 복구했습니다.
