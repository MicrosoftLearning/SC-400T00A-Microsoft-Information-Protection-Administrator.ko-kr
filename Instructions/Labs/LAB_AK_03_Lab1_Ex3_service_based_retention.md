---
lab:
  title: 연습 3 - 서비스 기반 보존 구성
  module: Module 3 - Implement Data Lifecycle and Records Management
ms.openlocfilehash: b531417b4335973f9c1e3ac0950f000fa1719eab
ms.sourcegitcommit: 53488624251b6cf8f79f2d1ff561e3f334764821
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/26/2022
ms.locfileid: "147694944"
---
# <a name="lab-3---exercise-3---configure-service-based-retention"></a>랩 3 - 연습 3 - 서비스 기반 보존 구성

Joni Sherman의 역할이 Contoso Ltd.의 규정 준수 관리자라고 가정합니다. 법무팀을 지원하여 회사에 불만을 품은 직원이 회사 데이터를 삭제하는 행위를 차단해야 합니다.

### <a name="task-1--configure-mailbox-holds"></a>작업 1 - 사서함 보존 구성

이 작업에서는 직원 사서함의 콘텐츠를 삭제할 수 없도록 사서함 보존을 활성화합니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 가상 머신(LON-CL1)에 로그인합니다.

1. **Microsoft Edge** 에서 **https://outlook.office.com/ecp** 로 이동한 다음 Exchange 관리 센터에 **Joni Sherman** 으로 로그인합니다. JoniS@WWLxZZZZZZ.onmicrosoft.com으로 로그인합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID입니다).  Joni의 암호는 랩 호스팅 공급자가 제공합니다.

1. **로그인 상태를 유지하시겠습니까?** 대화 상자에서 **이 메시지를 다시 표시 안 함** 체크박스를 선택하고 **아니요** 를 선택합니다.

1. 시작 화면이 표시되면 닫습니다.

1. **Exchange 관리 센터** 의 왼쪽 탐색 창에서 **받는 사람** 을 선택하고 **사서함** 을 선택합니다.

1. **Alex Wilber** 의 사서함을 선택하고 사서함을 편집할 수 있는 연필 아이콘을 선택합니다.

1. **사용자 사서함 편집** 창에서 **사서함 기능** 을 선택합니다.

1. **소송 보존: 사용 안 함** 까지 아래로 스크롤하고 **사용** 을 선택합니다.

1. **소송 보존** 페이지에서 다음 정보를 입력합니다.

    - **소송 보존 기간(일)** : 90
    - **참고**: 사서함이 앞으로 90일 동안 보존되도록 설정되었습니다. 이제 이 사서함의 메시지는 삭제할 수 없습니다.

1. **저장** 을 두 번 선택합니다. **참고:** **보존 설정이 적용되는 데 최대 240분이 걸릴 수 있습니다.** 라는 경고 메시지가 표시되면 메시지에서 **확인** 을 클릭합니다.

환경의 사서함에서 사서함 보존을 정상적으로 활성화했으며, 액세스 권한이 있는 모든 사용자가 사서함의 콘텐츠를 영구적으로 삭제하지 못하도록 설정했습니다. 보존이 적용될 때까지는 최대 4시간이 걸릴 수 있습니다.  다음 단계로 즉시 진행할 수 있습니다.

### <a name="task-2--recover-sharepoint-documents"></a>작업 2 - SharePoint 문서 복구

이 작업에서는 문서를 삭제한 후 삭제된 문서를 복원하여 직원이 자신의 사서함에 적용된 소송 보존 관련 정보를 파악한 후 삭제할 수도 있는 문서를 복원할 수 있는지를 확인합니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 VM(LON-CL1)에 로그인합니다.

1. **Microsoft Edge** 에서 **https://www.office.com** 으로 이동한 다음, Microsoft 365에 **Joni Sherman** 으로 로그인합니다.

1. 시작 화면이 표시되면 닫습니다. Office 365 앱 알림이 표시되면 해당 알림도 닫습니다.

1. Microsoft Office 365 방문 페이지에서 왼쪽 위 모서리의 앱 시작 관리자 아이콘(점 9개로 표시된 아이콘)을 선택하고 하위 메뉴에서 **SharePoint** 를 선택합니다.

1. **SharePoint 시작 페이지** 가 나타나면 닫습니다.

1. SharePoint 방문 페이지에서 **Contoso의 복리 후생** SharePoint 사이트를 선택합니다.

1. 왼쪽 탐색 창에서 **문서** 를 선택합니다.

1. **Vacation Policies.pptx** 앞의 체크박스를 선택하여 해당 문서를 강조 표시합니다.

1. 작업 모음에서 **삭제** 를 선택합니다.

1. **삭제할까요?** 대화 상자에서 **삭제** 를 선택합니다.

1. 왼쪽 탐색 창에서 **휴지통** 을 선택한 다음 **Vacation Policies.pptx** 앞의 체크박스를 선택하여 해당 문서를 강조 표시합니다.

1. 위쪽 작업 모음에서 **복원** 을 선택합니다.

1. 왼쪽 탐색 창에서 **문서** 를 선택하고 파일이 복원되었는지 검토합니다.

SharePoint 사이트에서 삭제된 문서를 정상적으로 복구했습니다.

# <a name="proceed-to-lab-3---exercise-4"></a>랩 3 - 연습 4로 진행
