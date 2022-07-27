---
ms.openlocfilehash: 7919442bc520d131fa869e44556eff1276b9c880
ms.sourcegitcommit: c78ddb966a982b76e7f46fc17a42847f76d6e1a0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2022
ms.locfileid: "147154880"
---
# <a name="lab-3---exercise-4---use-ediscovery-for-recovery"></a>랩 3 - 연습 4 - 복구에 eDiscovery 사용

이 연습에서는 Contoso Ltd.의 규정 준수 관리자인 Joni Sherman으로 작업을 수행하게 됩니다. 텍사스 소재의 조직에서는 현지 법률을 준수하는 보존 정책을 시행하려고 합니다. Uniform Preservation of Private Business Records Act에 따라 3년이 지나면 법에 저촉되는 사항 없이 레코드를 폐기할 수 있습니다(일부 예외는 있음). 이 법률 준수를 위해 조직에서는 조직의 모든 항목을 3년 동안 보존하는 보존 계획을 작성했습니다.

### <a name="task-1--create-ediscovery-case"></a>작업 1 - eDiscovery 케이스 만들기

이 연습에서는 eDiscovery 케이스를 만들고 Megan Bowen이 보낸 Mark 8 프로젝트 관련 정보가 포함된 메일 검색을 시작합니다. 법무팀에서 규정 준수 검토를 위해 이 정보를 요청했기 때문입니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman** 으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge** 에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **https://compliance.microsoft.com** 으로 이동합니다.

1. 포털의 왼쪽 탐색 창에서 **eDiscovery** 를 확장하고 **표준** 을 선택합니다.

1. **eDiscovery(표준)** 페이지에서 **+ 사례 만들기** 를 선택합니다.

1. **새 사례** 페이지의 **이름** 필드에 Mark 8 Project 사례를 입력하고 **설명** 에 이 사례는 Mark 8 Project에 관한 Megan Bowen의 메일을 평가하는 데 사용됩니다.를 입력한 다음, **저장** 을 선택합니다. 

1. **Core eDiscovery(표준)** 페이지로 돌아가서 **Mark 8 Project 사례** 를 선택하여 사례를 엽니다.

1. 케이스 보기에서 **검색** 탭을 선택합니다.

1. **+ 새 검색** 을 선택하여 새 검색을 시작합니다.

1. **이름 및 설명** 페이지에서 이름으로 *Mark 8 Project* 를 입력하고 **다음** 을 선택합니다.

1. **위치** 페이지에서 **Exchange 사서함** 을 **켜짐** 으로 설정하고 **사용자, 그룹 또는 팀 선택** 을 선택합니다.

1. **Exchange 사서함** 페이지에서 *Megan Bowen* 을 검색하고 Megan의 사서함을 선택합니다.  **완료** 를 선택합니다.

1. **위치** 페이지에서 **온-프레미스 사용자를 위한 앱 콘텐츠 추가** 확인란의 선택을 취소하고 **다음** 을 선택합니다.

1. **키워드** 영역의 **검색 조건 정의** 페이지에서 *Mark 8* 을 입력하고 **다음** 을 선택합니다.

1. **검색 항목을 검토한 후 만들기** 창에서 **제출** 을 선택합니다.

1. 검색이 만들어지면 **완료** 를 선택합니다.

eDiscovery 케이스를 만들었으며, Mark 8 프로젝트에 대한 정보가 들어 있는 Megan Bowen이 보내거나 받은 모든 메일을 검색했습니다.

### <a name="task-2--assign-records-management-and-ediscovery-manager-permissions"></a>작업 2 – 레코드 관리 및 eDiscovery 관리자 권한 할당

이 작업에서는 법무팀에 제공할 수 있는 PST 파일에 작업 1에서 검색한 데이터를 내보낼 수 있도록 준비합니다. 먼저 준수 관리자에게 레코드 관리 역할을 할당해야 합니다. 이 역할을 할당하지 않으면 준수 관리자가 검색 결과를 내보낼 수 없습니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 VM(LON-CL1)에 로그인합니다.

1. **Microsoft Edge** 에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 오른쪽 위 모서리에 있는 **Joni Sherman** 의 **프로필 사진** 을 선택하고 **로그아웃** 을 선택합니다. 그런 다음, 브라우저를 닫습니다.

1. **Microsoft Edge** 에서 **https://compliance.microsoft.com** 으로 이동한 다음, Microsoft Purview 포털에 **MOD 관리자** admin@WWLxZZZZZZ.onmicrosoft.com 으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임). 관리자의 암호는 랩 호스팅 공급자가 제공합니다. 

1. 왼쪽 탐색 창에서 **권한** 을 선택한 다음, **Microsoft Purview 솔루션** 에서 **역할** 을 선택합니다.  **레코드 관리** 역할을 선택합니다.

1. **레코드 관리** 창에서 **구성원** 범주 옆에 있는 **편집** 을 선택합니다.

1. **구성원 선택** 을 선택하고 **+ 추가** 를 선택합니다.
 
1. **Joni Sherman** 을 검색하여 이름 앞의 체크박스를 선택한 후 **추가** 를 선택합니다.

1. 구성원 목록의 변경 내용을 검토하고 **완료** 를 선택합니다.

1. **저장** 및 **닫기** 를 선택합니다.

1. **Microsoft Purview 솔루션의 역할 그룹** 에서 **eDiscovery 관리자** 역할을 선택합니다.

1. **eDiscovery 관리자** 창에서 **eDiscovery 관리자** 범주 옆에 있는 **편집** 을 선택합니다.

1. **eDiscovery 관리자 선택 편집** 창에서 **eDiscovery 관리자 선택** 을 선택합니다.

1. **+ 추가** 를 선택하고 **Joni Sherman** 을 검색하고 이름 앞의 확인란을 선택한 다음, **추가** 를 선택합니다.

1. 구성원 목록의 변경 내용을 검토하고 **완료** 를 선택합니다.

1. **저장** 및 **닫기** 를 선택합니다.

검색 결과 내보내기 권한을 준수 관리자에게 부여하고 레코드 관리 작업을 수행했습니다. 사용 권한이 사용자에게 적용될 때까지 최대 60분이 걸릴 수 있으므로 다음 단계로 진행해도 됩니다.

### <a name="task-3--export-data-from-ediscovery-case"></a>작업 3 - eDiscovery 케이스에서 데이터 내보내기

이 작업에서는 법무팀에 제공할 수 있도록 작업 1에서 검색한 데이터 내보내기를 준비합니다.  테넌트에서 권한을 사용할 수 있을 때까지 60분이 걸릴 수 있습니다.

1. 클라이언트 1 VM(LON-CL1)에 **lon-cl1\admin** 계정으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge** 에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 오른쪽 위 모서리에 있는 **MOD 관리자** 의 **프로필 사진** 을 선택하고 **로그아웃** 을 선택합니다. 그런 다음, 브라우저를 닫습니다.

1. **Microsoft Edge** 를 열고 **https://compliance.microsoft.com** 으로 이동한 다음, Microsoft Purview 포털에 **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com 으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  Joni의 암호는 랩 호스팅 공급자가 제공합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **eDiscovery** 를 확장하고 **표준** 을 선택합니다.

1. **Mark 8 Project 사례** 를 선택하여 사례를 엽니다.

1. **검색** 탭을 선택하고 **Mark 8 Project** 검색을 선택합니다.

    >[!TIP]
    eDiscovery 검색에 데이터가 없다면 검색 매개 변수를 고려해 보세요. Megan의 사서함에는 *Mark 8* 프로젝트에 대한 일부 메시지가 포함되어야 합니다.  보내지 않았다면 Megan의 사서함에 있는 기존 전자 메일에 있는 아무 단어로 검색 키워드를 변경해 보세요.  예를 들어 "planner"라는 용어는 보통 Megan의 기존 전자 메일 중 몇 개에 나타납니다.  내보내기에 처리할 내용이 있으려면 검색할 데이터가 있어야 합니다.

1. **Mark 8 Project** 대화 상자에서 **작업** 버튼 드롭다운을 선택하고 **결과 내보내기** 를 선택합니다.

1. **결과 내보내기** 창의 **출력 옵션** 에서 옵션을 검토합니다.  **내보내기** 단추를 선택합니다.

    [//]: <> (LOD 테넌트에서 상태 코드 500으로 요청이 실패했습니다. M365 개발자 테넌트에서 이전에 작업했습니다.)

1. **규정 준수** 창이 나타나면 **확인** 을 선택합니다.

1. 사례 화면에서 **내보내기** 탭을 선택합니다.  방금 만든 내보내기를 두 번 클릭합니다.

1. 내보내기 창의 **내보내기 키** 아래에서 **클립보드에 복사** 를 선택한 다음 **결과 다운로드** 를 선택합니다.
  
1. 메시지가 표시되면 브라우저에서 **열기** 를 선택하여 eDiscovery 내보내기 도구를 설치한 다음 **설치** 를 선택합니다.

1. 이전에 클립보드에 복사한 키에 붙여넣는 대화 상자가 나타납니다.  파일을 다운로드하는 데 적합한 위치를 선택합니다. **시작** 을 선택합니다. 

검색된 데이터를 내보냈습니다.

### <a name="task-4--perform-search--purge-on-mailboxes"></a>작업 4 - 사서함에서 검색 및 제거 수행

조사 결과 사용자가 피싱 메일 몇 통을 받은 것으로 확인되어 환경 내의 모든 사서함에서 해당 메시지를 삭제해야 합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman** 으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge** 에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **https://compliance.microsoft.com** 으로 이동합니다.

1. Purview 포털의 왼쪽 탐색 창에서 **콘텐츠 검색** 을 선택합니다.

1. **+ 새 검색** 을 선택합니다.

1. **이름 및 설명** 창에서 **이름** 으로 *피싱 메일 제거* 를 입력하고 **다음** 을 선택합니다.

1. **위치** 섹션에서 **Exchange 사서함** 을 선택하고 **다음** 을 선택합니다.

1. **검색 조건 정의** 페이지의 **키워드** 영역에 *From:phishingmail@outlook.com AND subject:"Password changed"* 를 입력하고 **다음** 을 선택합니다.

1. **검색 항목을 검토한 후 만들기** 창에서 **제출** 을 선택합니다. 그런 다음, **완료** 합니다.

1. 검색을 만든 후에는 **Security & Compliance PowerShell** 을 사용하여 제거를 시작해야 합니다. 시작 메뉴에서 **Windows PowerShell** 을 선택하고 관리자 권한을 실행을 선택합니다.

1. **PowerShell** 창에서 다음 cmdlet을 사용하여 **MOD 관리자** 로 로그인합니다.

    ```powershell
    Connect-IPPSSession
    ```

1. **PowerShell** 창에서 다음 명령을 사용합니다.

    ```powershell
    New-ComplianceSearchAction -SearchName "Phishing mail removal" -Purge -PurgeType HardDelete
    ```

1. PowerShell에서 예인 경우 **Y** 를 입력하고 **Enter** 키를 눌러 작업을 확인합니다.

특정 전자 메일을 확인하는 새 콘텐츠 검색을 만들었으며, 제거 작업을 사용하여 사용자 사서함에서 피싱 메일을 삭제했습니다. 조직 관리 역할 구성원만 제거 작업을 실행할 수 있습니다. 준수 관리자는 이 역할의 구성원이 아닙니다.

# <a name="proceed-to-lab-3---exercise-6"></a>랩 3 - 연습 6으로 진행
