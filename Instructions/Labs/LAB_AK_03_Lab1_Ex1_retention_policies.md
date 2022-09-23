---
lab:
  title: 연습 1 - 보존 정책 구성
  module: Module 3 - Implement Data Lifecycle and Records Management
ms.openlocfilehash: dc8282f424065a6c21ceac476f79a15dbf5ed149
ms.sourcegitcommit: 53488624251b6cf8f79f2d1ff561e3f334764821
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/26/2022
ms.locfileid: "147694935"
---
# <a name="lab-3---exercise-1---configure-retention-policies"></a>랩 3 - 연습 1 - 보존 정책 구성

이 연습에서는 Contoso Ltd.의 시스템 관리자인 Joni Sherman으로 작업을 수행하게 됩니다. 미국 텍사스 주 소재의 이 기업에서는 3년이 지나면 법에 저촉되는 사항 없이 레코드를 삭제할 수 있음이 명시된 주법 준수를 위해 보존 정책을 구현하려고 합니다. 

이 법률 준수를 위해 조직에서는 조직의 모든 항목을 3년 동안 보존하는 보존 계획을 작성했습니다.


### <a name="task-1--create-company-wide-retention-policy"></a>작업 1 - 회사 전체 보존 정책 만들기

이 연습에서는 회사 전체 보존 정책을 만들고 보존 기간을 적용한 다음 정책을 적용할 위치를 설정합니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 VM(LON-CL1)에 로그인합니다.

1. **Microsoft Edge** 에서 **https://compliance.microsoft.com** 으로 이동한 다음, Microsoft Purview 포털에 **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com 으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  Joni의 암호는 랩 호스팅 공급자가 제공합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **정책** 을 선택하고 **데이터** 에서 **보존** 을 선택합니다.

1. **데이터 수명 주기 관리** 페이지의 **보존 정책** 탭에서 **+ 새 보존 정책** 을 선택합니다.

1. **보존 정책 이름 지정** 페이지의 **이름** 및 **설명** 에 다음 정보를 각각 입력합니다.

    - 이름: 회사 전체
    - 설명: Teams를 제외한 모든 위치

1. **다음** 단추를 선택합니다.  

1. **생성할 보존 정책 유형 선택** 영역에서 **정적** 을 선택하고 **다음** 을 선택합니다.

1. **정책을 적용할 위치 선택** 영역에서 Exchange 전자 메일, SharePoint 사이트, OneDrive 계정 및 Microsoft 365 그룹이 선택되어 있는지 확인하고 **다음** 을 선택합니다.

1. **콘텐츠를 보존할지, 삭제할지, 아니면 둘 다 수행할지 여부를 결정** 페이지의 **특정 기간 동안 항목 보존** 섹션에서 다음 정보를 입력합니다.

    - **특정 기간 동안 항목 보존**: 드롭다운 목록에서 **사용자 지정** 선택
    - 연도 필드를 **3** 으로 변경합니다.
    - **보존 기간 시작 기준**: 마지막으로 항목을 수정한 시기
    - **보존 기간이 끝날 때**: 자동으로 항목 삭제

1. **다음** 단추를 선택합니다.

1. **검토 후 완료** 페이지에서 **제출** 단추를 선택합니다.

1. 정책이 만들어지면 **완료** 단추를 선택합니다.

Exchange 이메일, Microsoft 365 그룹, OneDrive 및 SharePoint 사이트용 보존 정책을 만들었습니다. 이 보존 정책은 항목을 마지막으로 수정한 날짜로부터 3년 동안 해당 위치에서 항목을 보존합니다. 테넌트에 이 정책을 적용하기까지 최대 24시간이 걸릴 수 있으므로 다음 단계로 진행해도 됩니다.

### <a name="task-2--create-location-based-retention-policies-with-filter"></a>작업 2 - 필터를 사용하여 위치 기반 보존 정책 만들기

이번에는 Teams 위치용 보존 정책을 만듭니다. Teams 채널에는 문서가 포함되어 있을 수 있으므로 모든 채널을 보존해야 합니다. 조직에서는 제한된 수의 사용자가 Teams 채팅에서 보존 기간을 설정해야 하도록 요청하기로 결정했습니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman** 으로 로그인되어 있는 상태여야 합니다. 

1. **Microsoft Edge** 에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **https://compliance.microsoft.com** 으로 이동합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **정책** 을 선택하고 **데이터** 에서 **보존** 을 선택합니다.

1. **데이터 수명 주기 관리** 페이지의 **보존 정책** 탭에서 **+ 새 보존 정책** 을 선택합니다.

1. **보존 정책 이름 지정** 페이지의 **이름** 및 **설명** 에 다음 정보를 각각 입력합니다.

    - **이름**: Teams 보존
    - **설명**: Teams 위치용 보존

1. **다음** 단추를 선택합니다.

1. **생성할 보존 정책 유형 선택** 영역에서 **정적** 을 선택하고 **다음** 을 선택합니다.

1. **정책을 적용할 위치 선택** 페이지에서 다음 설정을 입력합니다.

    - **Teams 채널 메시지** 위치 - **상태**: 켜기 
    - **Teams 채팅** 위치 - **상태**: 켜기
    - 다른 모든 위치는 자동으로 **해제** 되어야 합니다.
    

1. **Teams 채팅** 위치에 대해 **모든 사용자** 아래에 있는 **편집** 텍스트 링크를 선택합니다.

1. **Teams 채팅** 패널에서 다음 사용자를 추가합니다. 
    - Adele Vance
    - Pradeep Gupta

    참고: 해당 두 사용자를 추가하면 Teams 채팅에 포함된 설정이 "모든 팀"에서 추가한 두 사용자만으로 변경됩니다.

1. **완료** 를 선택한 후 **다음** 을 선택합니다.

1. **콘텐츠를 보존할지, 삭제할지, 아니면 둘 다 수행할지 여부를 결정** 페이지의 **특정 기간 동안 항목 보존** 섹션에서 다음 정보를 입력합니다.

    - **특정 기간 동안 항목 보존**: 드롭다운 목록에서 **사용자 지정** 선택
    - 연도 필드를 **3** 으로 변경합니다.
    - **보존 기간 시작 기준**: 마지막으로 항목을 수정한 시기
    - **보존 기간이 끝날 때**: 자동으로 항목 삭제


1. **다음** 단추를 선택합니다.

1. **검토 후 완료** 페이지에서 **제출** 단추를 선택합니다.

1. 정책이 만들어지면 **완료** 를 선택합니다.

Teams 위치용 보존 정책을 만들었습니다. 그리고 모든 Teams 채널 위치에 대해 보존 기간을 3년으로 설정했습니다. 또한 특정 사용자에게만 적용할 Teams 채팅 위치용 필터를 설정했습니다.

### <a name="task-3--create-retention-policy-via-powershell"></a>작업 3 - PowerShell을 통해 보존 정책 만들기

이번에는 PowerShell을 사용하여 동일한 보존 정책을 만듭니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 VM(LON-CL1)에 로그인합니다.

1. 관리자 권한 PowerShell 창을 엽니다. 이렇게 하려면 마우스 오른쪽 단추로 Windows 단추를 선택한 다음 **Windows PowerShell(관리자)** 을 선택하고 사용자 계정 컨트롤 창이 표시되면 **예** 를 선택합니다.

1. 다음 cmdlet을 사용하여 테넌트에서 보안 및 준수 센터에 연결합니다.

    ```powershell
    Connect-IPPSSession
    ```

1. 로그인 대화 상자가 표시되면 **MOD 관리자** 로 로그인합니다. 로그인 ID로는 admin@WWLxZZZZZZ.onmicrosoft.com을 사용합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  관리자의 암호는 랩 호스팅 공급자가 제공합니다.

1. 다음 cmdlet을 실행하여 Teams를 제외한 모든 위치용으로 첫 번째 보존 정책을 만듭니다.

    ```powershell
    New-RetentionCompliancePolicy -Name "Company Wide PS" -ExchangeLocation All -ModernGroupLocation All -PublicFolderLocation All -SharePointLocation All -OneDriveLocation All
    ```

1. 다음 cmdlet을 실행하여 보존 기간을 설정합니다. 단위로는 수정한 날짜 기준 기간(일)을 사용합니다.
    
    ```powershell
    New-RetentionComplianceRule -Name "Company Wide PS Rule" -Policy "Company Wide PS" -RetentionDuration 1095 -ExpirationDateOption ModificationAgeInDays -RetentionComplianceAction Keep
    ```

1. 다음 cmdlet을 실행하여 Teams 위치용으로 두 번째 보존 정책을 만듭니다.

    ```powershell
    New-RetentionCompliancePolicy -Name "Teams Retention PS" -TeamsChannelLocation All -TeamsChatLocation "Adele Vance", "Pradeep Gupta"
    ```

1. 다음 cmdlet을 실행하여 보존 기간을 설정합니다. 단위로는 기간(일)을 사용합니다.

    ```powershell
    New-RetentionComplianceRule -Name "Teams Retention PS Rule" -Policy "Teams Retention PS" -RetentionDuration 1095 -RetentionComplianceAction Keep
    ```

PowerShell을 통해 보존 기간이 3년인 보존 정책을 만들었습니다.

### <a name="task-4--create-retention-policy-with-adaptive-scope"></a>작업 4 – 적응형 범위를 사용하여 보존 정책 만들기

이 연습에서는 재무 및 법률 부서에 대한 보존 정책을 만듭니다. 이 정책의 목적은 법률을 준수하여 5년 동안 모든 법적 관련 문서를 보존하는 것입니다. 먼저 법률 및 소매 부서를 포함한 적응형 범위를 만든 다음, 이 범위를 사용하여 보존 정책을 만듭니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman** 으로 로그인되어 있는 상태여야 합니다. 

1. **Microsoft Edge** 에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **https://compliance.microsoft.com** 으로 이동합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **데이터 수명 주기 관리** 를 선택합니다.
1. **데이터 수명 주기 관리** 의 **적응 범위** 탭에서 **+ 범위 만들기** 를 선택합니다.
1. **적응형 정책 범위 이름 지정** 페이지에서 **이름** 및 **설명** 에 다음 정보를 입력합니다.

    - **이름**: 법적 문서 보존
    - **설명**: 법적 관련 문서에 대한 보존

1. **다음** 단추를 선택합니다.
1. **만들려는 범위 유형** 페이지에서 **사용자** 를 선택합니다.
1. **다음** 단추를 선택합니다.
1. **사용자 정의 쿼리 만들기** 페이지의 **사용자 특성** 아래에서 특성에 대한 드롭다운 메뉴를 열고 **부서** 를 선택합니다.
1. 특성 필드 바로 옆에서 연산자로 **다음과 같음** 을 선택합니다.
1. 값으로 **법적** 입력
1. 두 번째 특성을 추가하려면 **사용자 정의 쿼리 만들기** 페이지에서 **+ 특성 추가** 를 선택합니다.
1. **쿼리 연산자**, **특성**, **연산자**, **값** 에 다음 정보를 입력합니다.
    - **쿼리 연산자**: Or
    - **특성**: 부서
    - **연산자**: 다음과 같음
    - **값**: 소매

1. **다음** 단추를 선택합니다.
1. **검토 후 완료** 페이지에서 **제출** 단추를 선택합니다.
1. 제출에 성공하면 **완료** 단추를 클릭하여 페이지를 닫습니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **정책** 을 선택하고 **데이터** 에서 **보존** 을 선택합니다.

1. **데이터 수명 주기 관리** 페이지의 **보존 정책** 탭에서 **+ 새 보존 정책** 을 선택합니다.

1. **보존 정책 이름 지정** 페이지의 **이름** 및 **설명** 에 다음 정보를 각각 입력합니다.

    - **이름**: 법적 데이터 보존
    - **설명**: 법률 및 소매 부서 내의 모든 문서를 보존합니다.

1. **다음** 단추를 선택합니다.

1. **생성할 보존 정책 유형 선택** 영역에서 **적응형** 을 선택하고 **다음** 을 선택합니다.

1. **적응형 정책 범위 및 위치 선택** 페이지에서 **+ 범위 추가** 를 선택합니다.
2. 새 **적응형 정책 범위 선택** 페이지에서 **법적 문서 보존** 을 선택한 다음, **추가** 단추를 선택합니다.

1. **정책을 적용할 위치 선택** 에서 다음 정보를 입력합니다.

    - **Exchange 메일** - **상태**: 켜짐
    - **OneDrive** - **상태**: 켜짐
    - 다른 모든 위치는 자동으로 **해제** 되어야 합니다.
    
1. **다음** 단추를 선택합니다.
1. **콘텐츠를 보존할지, 삭제할지, 아니면 둘 다 수행할지 여부를 결정** 페이지의 **특정 기간 동안 항목 보존** 섹션에서 다음 정보를 입력합니다.

    - **특정 기간 동안 항목 보존**: 5년
    - **보존 기간 시작 기준**: 항목 작성 시
    - **보존 기간 종료 시**: 아무 작업도 하지 않음

1. **다음** 단추를 선택합니다.

1. **검토 후 완료** 페이지에서 **제출** 단추를 선택합니다.

1. 정책이 만들어지면 **완료** 단추를 선택합니다.
### <a name="task-5--test-adaptive-scope-policy"></a>작업 5 – 적응형 범위 정책 테스트

이 연습에서는 적응형 범위의 영향을 받는 사용자를 확인하고 새 적응형 보존 정책을 테스트합니다.

참고: 보존 정책을 만들고 제출할 때 보존 정책을 적용하는 데 최대 7일이 걸릴 수 있습니다.

 1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman** 으로 로그인되어 있는 상태여야 합니다. 

1. **Microsoft Edge** 에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **https://compliance.microsoft.com** 으로 이동합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **정책** 을 선택하고 **데이터** 에서 **보존** 을 선택합니다.

1. **데이터 수명 주기 관리** 페이지의 **적응형 범위** 탭에서 **법적 문서 보존** 을 선택합니다.

1. 새 **법적 문서 보존** 페이지에서 **범위 세부 정보** 를 선택합니다.
1. **법적 문서 보존** 페이지에서 범위의 영향을 받는 모든 위치를 볼 수 있어야 합니다.

[//]: <> (랩 테넌트 오류: 데이터를 로드하지 못했습니다. 다시 시도하세요.)

1. 적응형 범위 보존 정책의 세부 정보를 검토하려면 마우스 오른쪽 단추로 Windows 단추를 선택하여 PowerShell 창을 연 다음, Windows PowerShell을 선택합니다.

1. 다음 cmdlet을 사용하여 테넌트에서 보안 및 준수 센터에 연결합니다.

    ```powershell
    Connect-IPPSSession
    ```
1. 로그인 대화 상자가 표시되면 MOD 관리자로 로그인합니다. 로그인 ID로는 admin@WWLxZZZZZZ.onmicrosoft.com을 사용합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임). 관리자의 암호는 랩 호스팅 공급자가 제공합니다.
1. 적응형 범위 정책의 모든 세부 정보를 보려면 다음 cmdlet을 실행합니다.
    ```powershell
    Get-RetentionCompliancePolicy -Identity "Legal Data Retention" -DistributionDetail | Format-List
    ```
1. 세부 정보를 검토합니다. 특정 매개 변수에는 다음과 같은 상태가 있어야 합니다.

    - **Enabled**: True
    - **Mode**: 적용
    - **DistributionStatus**: 성공
# <a name="proceed-to-lab-3---exercise-2"></a>랩 3 - 연습 2로 진행

