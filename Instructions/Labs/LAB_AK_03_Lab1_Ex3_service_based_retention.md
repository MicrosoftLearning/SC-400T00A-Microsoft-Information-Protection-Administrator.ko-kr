---
lab:
  title: 연습 3 - 서비스 기반 보존 구성
  module: Module 3 - Implement Data Lifecycle and Records Management
---

# 랩 3 - 연습 3 - 서비스 기반 보존 구성

Joni Sherman의 역할이 Contoso Ltd.의 규정 준수 관리자라고 가정합니다. 법무팀을 지원하여 회사에 불만을 품은 직원이 회사 데이터를 삭제하는 행위를 차단해야 합니다.

## 작업 1 - 사서함 보존 구성

이 작업에서는 직원 사서함의 콘텐츠를 삭제할 수 없도록 사서함 보존을 활성화합니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 가상 머신(LON-CL1)에 로그인합니다.

1. **Microsoft Edge**에서 **`https://admin.exchange.microsoft.com`** 로 이동한 다음 Exchange 관리 센터에 **Joni Sherman**으로 로그인합니다. JoniS@WWLxZZZZZZ.onmicrosoft.com으로 로그인합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID입니다).

1. 표시되는 경우 모든 팁 창을 닫습니다.

1. Exchange 관리 센터의 왼쪽 탐색 창에서 **받는 사람**을 확장한 다음 **사서함**을 선택합니다.

1. **Alex Wilber**의 사서함을 선택하고 사서함을 편집할 수 있는 연필 아이콘을 선택합니다.

1. 사서함 목록에서 **Alex Wilber**를 선택하면 오른쪽에 Alex의 사서함 설정이 표시된 플라이아웃 페이지가 표시됩니다.

1. Alex Wilber의 플라이아웃 페이지에서 **기타** 탭을 선택합니다.

1. **소송 보존**에서 **소송 보존 관리**를 선택합니다.

1. **소송 보존 관리** 페이지에서 **소송 보존** 설정을 _끄기_에서 _켜기_로 전환하여 소송 보존 설정을 표시합니다.

1. 다음 보류 설정을 설정합니다.

    - **보존 기간(일).** 90
    - **참고(사용자가 볼 수 있음)**: 사서함이 앞으로 90일 동안 보존되도록 설정되었습니다. 이제 이 사서함의 메시지는 삭제할 수 없습니다.

1. **저장**을 선택한 다음 **소송 보존이 업데이트됨**을 표시하는 메시지가 표시됩니다.

환경의 사서함에서 사서함 보존을 정상적으로 활성화했으며, 액세스 권한이 있는 모든 사용자가 사서함의 콘텐츠를 영구적으로 삭제하지 못하도록 설정했습니다. 보존이 적용될 때까지는 최대 4시간이 걸릴 수 있습니다.  다음 단계로 즉시 진행할 수 있습니다.

## 작업 2 - SharePoint 문서 복구

이 작업에서는 문서를 삭제한 후 삭제된 문서를 복원하여 직원이 자신의 사서함에 적용된 소송 보존 관련 정보를 파악한 후 삭제할 수도 있는 문서를 복원할 수 있는지를 확인합니다.

1. 클라이언트 1 VM(LON-CL1)에 **lon-cl1\admin** 계정으로 로그인합니다.

1. **Microsoft Edge**에서 **`https://www.office.com`** 으로 이동한 다음, Microsoft 365에 **Joni Sherman**으로 로그인합니다.

1. 시작 화면이 표시되면 닫습니다. Office 365 앱 알림이 표시되면 해당 알림도 닫습니다.

1. Microsoft Office 365 방문 페이지에서 왼쪽 위 모서리의 앱 시작 관리자 아이콘(점 9개로 표시된 아이콘)을 선택하고 하위 메뉴에서 **SharePoint**를 선택합니다.

1. **SharePoint 시작 페이지**가 나타나면 닫습니다.

1. SharePoint 방문 페이지에서 **Contoso의 복리 후생** SharePoint 사이트를 선택합니다.

1. 왼쪽 탐색 창에서 **문서**를 선택합니다.

1. **문서** 페이지에서 **Vacation Policies.pptx** 왼쪽에 있는 확인란을 선택한 다음 작업 표시줄에서 **삭제**를 선택합니다.

1. **삭제할까요?** 대화 상자에서 **삭제**를 선택합니다.

1. 왼쪽 탐색 창에서 **휴지통**을 선택한 다음 **Vacation Policies.pptx** 앞의 체크박스를 선택하여 해당 문서를 강조 표시합니다.

1. 위쪽 작업 모음에서 **복원**을 선택합니다.

1. 왼쪽 탐색 창에서 **문서**를 선택하고 파일이 복원되었는지 검토합니다.

SharePoint 사이트에서 삭제된 문서를 정상적으로 복구했습니다.
