---
lab:
  title: 연습 4 - 이벤트 기반 보존 구성
  module: Module 3 - Implement Data Lifecycle and Records Management
ms.openlocfilehash: bc2419ca627eb18ee16fcd6cf2f9ff59a079521e
ms.sourcegitcommit: 53488624251b6cf8f79f2d1ff561e3f334764821
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/26/2022
ms.locfileid: "147694953"
---
# <a name="lab-3---exercise-4---configure-event-based-retention"></a>랩 3 - 연습 4 - 이벤트 기반 보존 구성

이 연습에서는 Contoso Ltd.의 준수 관리자인 Joni Sherman으로 작업을 수행하게 됩니다. 조직은 텍사스에 있으며 특정 프로젝트에 속한 콘텐츠를 종료 후 5년 동안 보존하는 보존 정책을 구현하려고 합니다.

### <a name="task-1---create-event-type"></a>작업 1 - 이벤트 유형 만들기

먼저 특정 조건이 발생할 때 트리거될 수 있는 이벤트 유형을 만들어야 합니다. 이 경우 Project Closure에서 트리거할 수 있는 이벤트 유형을 만듭니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**(JoniS@WWLxZZZZZZ.onmicrosoft.com)으로 로그인되어 있는 상태여야 합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  Joni의 암호는 랩 호스팅 공급자가 제공합니다. 

1. **Microsoft Edge** 에서 **https://compliance.microsoft.com** 으로 이동하고 Microsoft Purview 포털에 **Joni Sherman** 으로 로그인합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **레코드 관리** 를 선택하고 **이벤트** 탭으로 이동합니다.

1. **이벤트 유형 관리** 를 선택하고 **+ 만들기** 를 선택합니다.

1. **이벤트 유형 이름 지정** 대화 상자에서 다음 정보를 설정합니다.
    - **이름**: Project Closure
    - **설명**: 프로젝트가 닫히면 이 이벤트가 트리거됩니다.

1. **요약** 을 검토하고 **제출** 을 선택한 다음, **완료** 를 선택합니다.

새 이벤트 유형을 만들었습니다.

### <a name="task-2--create-event-driven-retention-label"></a>작업 2 – 이벤트 기반 보존 레이블 만들기

이벤트 유형을 만든 후에는 이벤트가 발생할 때 보존 기간을 트리거하는 레이블을 만들어야 합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**(JoniS@WWLxZZZZZZ.onmicrosoft.com)으로 로그인되어 있는 상태여야 합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  Joni의 암호는 랩 호스팅 공급자가 제공합니다. 

1. **Microsoft Edge** 에서 **https://compliance.microsoft.com** 으로 이동하고 Microsoft Purview 포털에 **Joni Sherman** 으로 로그인합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **정책** 을 선택하고 **데이터** 에서 **보존** 을 선택합니다.

1. **데이터 수명 주기 관리** 페이지에서 **레이블** 탭을 선택합니다.

1. **+ 레이블 만들기** 단추를 선택합니다.

1. **보존 레이블의 이름 지정** 페이지의 **이름**, **사용자를 위한 설명** 및 **관리자를 위한 설명** 에 다음 정보를 각각 입력합니다.

    - **이름**: Project Asset
    - **사용자를 위한 설명**: 이 레이블을 프로젝트 문서에 할당하여 5년 동안 보관되도록 합니다.
    - **관리자를 위한 설명**: 이벤트 기반 보존을 위한 Project Asset입니다.

1. **다음** 단추를 선택합니다.

1. **레이블 설정 정의** 페이지에서 **영구 또는 특정 기간 동안 항목 보관** 설정을 사용하도록 설정합니다.

1. **기간 정의** 페이지에서 다음 정보를 설정합니다.
    - **기간은 얼마인가요?** : 5년.
    - **기간은 언제 시작해야 하나요?** : 프로젝트 마감

1. **다음** 단추를 선택합니다.

1. **보존 기간 이후 수행되는 작업 선택** 페이지에서 **자동으로 항목 삭제** 를 선택한 다음, **다음** 을 선택합니다.

1. **검토 후 완료** 페이지에서 **레이블 만들기** 단추를 선택합니다.  보존 레이블 생성됨 페이지에서 아무 작업도 하지 않음을 선택하고 **완료** 를 선택합니다.

레이블을 성공적으로 만들었으며 레이블을 게시해야 합니다.

### <a name="task-3--publish-event-driven-retention-label"></a>작업 3 – 이벤트 기반 보존 레이블 게시

작업 2에 이어 이제 Project Asset 보존 레이블을 게시하여 게시된 레이블을 사용자가 Sharepoint 문서의 문서에 적용할 수 있도록 합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman** 으로 로그인되어 있는 상태여야 합니다. 

1. **Microsoft Edge** 에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **https://compliance.microsoft.com** 으로 이동합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **정책** 을 선택하고 **데이터** 에서 **보존** 을 선택합니다.

1. **데이터 수명 주기 관리** 페이지에서 **레이블** 탭을 선택합니다.

1. 작업 1에서 만든 레이블 **Project Asset** 을 선택합니다.

1. **레이블 게시** 아이콘 단추를 선택합니다.

1. **게시할 레이블 선택** 페이지에서 **다음** 단추를 선택합니다.

1. **만들 보존 정책 유형 선택** 페이지에서 **정적** 항목을 선택합니다.

1. **다음** 단추를 선택합니다.

1. **위치 선택** 페이지에서 **특정 위치를 선택하겠습니다.** 옵션을 사용하도록 설정합니다.

1. 다음 정보를 입력합니다.
    - **Exchange 메일** 위치 - **상태**: 끄기
    - **SharePoint 사이트** 위치 - **상태**: 켜기
    - **OneDrive 계정** 위치 - **상태**: 켜기
    - **Microsoft 365 그룹** 위치 - **상태**: 끄기  

1. **다음** 단추를 선택합니다.

1. **정책 이름 지정** 페이지의 **이름** 및 **설명** 에 다음 정보를 각각 입력합니다.

    - **이름**: Project Asset 보존 레이블
    - **설명**: Project Assets 보존 레이블, 보존 기간 5년, SharePoint 사이트 위치.

1. **다음** 단추를 선택합니다.

1. **마침** 페이지에서 **제출** 단추를 선택합니다.  정책이 만들어지면 **완료** 를 선택합니다.

Project Assets의 보존 레이블을 사용자에게 성공적으로 게시했습니다.

### <a name="task-4--apply-label-and-add-assetid"></a>작업 4 – 레이블 적용 및 AssetID 추가

레이블이 게시되면 사용자는 레이블을 적용하고 프로젝트의 올바른 Asset ID를 레이블을 지정할 문서에 할당해야 합니다. 이 작업에서는 이 기능을 테스트합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman** 으로 로그인되어 있는 상태여야 합니다. 

1. **Microsoft Edge** 에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **https://compliance.microsoft.com** 으로 이동합니다.

1. 왼쪽 위 모서리에서 9개의 점을 선택하고 **앱** 아래에서 **SharePoint** 를 선택합니다.

1. 왼쪽 탐색 창에서 **내 사이트** 를 선택하고 **다음** 에서 **작업** 을 선택합니다.

1. 왼쪽 탐색 창에서 **문서** 를 선택합니다.

1. **문서** 페이지에서 앞에 있는 확인란을 선택하여 **Bug List.xlsx** 를 선택한 다음, 세로 점 3개를 선택합니다.

1. 바로 가기 메뉴에서 **세부 정보** 를 선택합니다.

1. 오른쪽 메뉴의 **속성** 에서 **레이블 적용** 을 선택한 다음, **Project Asset** 레이블을 선택합니다.

    참고: 보존 레이블을 게시하는 데 시간이 걸릴 수 있으므로 즉시 사용 가능한 옵션이 없을 수 있습니다.

1. 새로 나타난 **자산 ID** 필드를 **BostonOfficeLaunch** 로 설정하고 오른쪽 위 모서리에서 **X** 를 선택하여 오른쪽 메뉴를 닫습니다.

문서에 레이블 및 자산 ID를 할당했습니다. 자산 ID BostonOfficeLaunch에 대한 Project Closure 이벤트가 트리거되면 5년의 보존 기간이 활성화됩니다.

### <a name="task-5--create-specific-event"></a>작업 5 – 특정 이벤트 만들기

이벤트가 발생하면 레이블이 지정된 콘텐츠가 필수 보존 기간을 시작하도록 트리거해야 합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**(JoniS@WWLxZZZZZZ.onmicrosoft.com)으로 로그인되어 있는 상태여야 합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  Joni의 암호는 랩 호스팅 공급자가 제공합니다. 

1. **Microsoft Edge** 에서 **https://compliance.microsoft.com** 으로 이동하고 Microsoft Purview 포털에 **Joni Sherman** 으로 로그인합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **레코드 관리** 를 선택하고 **이벤트** 탭으로 이동합니다.

1. **+ 만들기** 를 선택합니다.

1. **이벤트 이름 지정** 페이지에서 다음 정보를 설정합니다.
    - **이름**: Project Boston Office Launch 종료
    - **설명**: Project Asset 레이블과 AssetID BostonOfficeLaunch가 있는 자산은 보존 기간을 입력합니다.

1. **새로 만들기** 를 선택합니다.

1. **이벤트 설정** 페이지에서 **이벤트 유형 사용** 을 선택한 다음, **이벤트 유형을 선택** 합니다.

1. **이벤트 유형 선택** 페이지에서 **Project Closure** 를 선택한 다음, **추가** 를 선택합니다.

1. **새로 만들기** 를 선택합니다.

1. **이벤트 설정** 페이지에서 **SharePoint 및 OneDrive의 항목에 대한 자산 ID** 를 **BostonOfficeLaunch** 로 설정하고 오늘 날짜를 선택합니다.

1. **다음** 을 선택하고 **제출** 을 선택한 다음, **완료** 를 선택합니다.

이벤트를 성공적으로 트리거하고 Project Asset 레이블 및 BostonOfficeLaunch의 자산 ID를 사용하여 모든 문서에 대한 보존 기간을 시작했습니다.

### <a name="task-6--observe-results-of-event-trigger"></a>작업 6 – 이벤트 트리거의 결과 관찰

지정한 보존 기간이 시작되었는지 확인하려면 파일을 삭제해야 합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman** 으로 로그인되어 있는 상태여야 합니다. 

1. **Microsoft Edge** 에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **https://compliance.microsoft.com** 으로 이동합니다.

1. 왼쪽 위 모서리에서 9개의 점을 선택하고 **앱** 아래에서 **SharePoint** 를 선택합니다.

1. 왼쪽 탐색 창에서 **내 사이트** 를 선택하고 **다음** 에서 **작업** 을 선택합니다.

1. 왼쪽 탐색 창에서 **문서** 를 선택합니다.

1. **문서** 페이지에서 앞에 있는 확인란을 선택하여 **Bug List.xlsx** 를 선택한 다음, 세로 점 3개를 선택합니다.

1. 바로 가기 메뉴에서 **삭제** 를 선택하고 결과를 확인합니다.

문서의 보존 기간이 시작되었음을 확인했습니다. 문서를 여전히 삭제할 수 있는 경우 이벤트의 동기화 기간이 완료되지 않았으며 보존 정책 트리거는 아직 진행 중입니다. 다른 보존 레이블과 마찬가지로 이 프로세스를 완료하는 데 최대 7일이 걸릴 수 있습니다.

# <a name="proceed-to-lab-3---exercise-5"></a>랩 3 - 연습 5로 진행
