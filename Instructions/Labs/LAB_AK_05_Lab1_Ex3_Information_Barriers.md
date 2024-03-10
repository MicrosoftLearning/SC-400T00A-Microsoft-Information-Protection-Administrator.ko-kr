---
lab:
  title: 연습 3 - 정보 장벽 구성
  module: Module 5 - Manage insider and privacy risk in Microsoft 365
---

# 랩 5 - 연습 3 - 정보 장벽 구성

Contoso Ltd.의 규정 준수 관리 주체인 Joni는 Microsoft 365에서 Information Barriers를 구성하고 관리해야 합니다. 정보 장벽은 명확한 경계를 기본 조직 내의 특정 그룹 또는 개인 간의 무단 통신을 방지하는 데 중요한 역할을 합니다. 정보 장벽을 구현하여 규정 준수를 보장하고 중요한 정보를 보호하며 이해 충돌을 최소화합니다. 이 설정은 데이터 기밀성을 보호하고 Contoso Ltd.의 규정 준수 약속을 지원하는 안전한 작업 환경을 만듭니다.

## 작업 1: Microsoft Teams에서 이름으로 검색이 사용하도록 설정되어 있는지 확인

이 작업에서는 Microsoft Teams에서 **이름** 별 검색 기능이 사용하도록 설정되어 있는지 확인합니다. 이 기능을 사용하면 사용자가 조직 내에서 특정 개인을 쉽게 검색하고 찾을 수 있습니다. 제공된 단계에 따라 이 기능을 구성하고 활성화하여 공동 작업을 개선하고 조직의 Microsoft Teams 환경 내에서 통신을 간소화합니다.

1. 클라이언트 1 VM(LON-CL1)에 lon-cl1\admin** 계정으로 **로그인합니다.

1. Joni의 계정으로 로그인한 경우 이 계정에서 로그아웃하고 모든 브라우저 창을 닫습니다.

1. Microsoft Edge에서 **MOD 관리istrator admin@WWLxZZZZZZ.onmicrosoft.com 로 Microsoft Purview 포털로 이동하여 **`https://admin.teams.microsoft.com`** 로그인합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공하는 고유한 테넌트 ID임).**

1. 왼쪽 탐색 창의 Teams 드롭다운 아래에서 **Teams** 설정을 선택합니다 **.**

1. 이름으로** 검색까지 **아래로 스크롤합니다. 이 기능을 끄기로 설정한 경우 이 기능을 **켜**고 저장**을 선택하여 **이 설정을 저장합니다.

1. **변경 내용을 적용**하는 데 시간이 걸리면 팝업에서 확인을 선택합니다 **.**

    >**참고:** 이 변경 내용이 적용되려면 몇 시간이 걸릴 수 있습니다.

## 작업 2: Microsoft Teams에서 정보 장벽에 대한 관리 동의 사용

이 작업에서는 Microsoft Teams에서 관리 IB(정보 장벽)에 대한 동의를 사용하도록 설정합니다. 이 구성은 Teams 채널과 같은 그룹에서 비IB 규격 사용자를 제거할 수 있도록 하여 규정 준수를 보장합니다.

1. 관리자 권한 PowerShell 창을 엽니다. 이렇게 하려면 마우스 오른쪽 단추로 Windows 단추를 선택한 다음, **Windows PowerShell(관리자)** 을 선택합니다.

1. 예로 **사용자 계정 컨트롤** 창을 **확인합니다**.

1. 다음 cmdlet을 입력하여 최신 버전의 Azure AD 모듈을 설치합니다.

    ```powershell
    Install-Module AzureAD
    ```

1. Y** for Yes를 **사용하여 NuGet 공급자 보안 대화 상자를 확인하고 Enter 키를 누릅니**다**. 이 프로세스를 완료하는 데 몇 초 정도 걸릴 수 있습니다.

1. Y** for Yes를 **사용하여 신뢰할 수 없는 리포지토리 보안 대화 상자를 확인하고 Enter 키를 누릅니**다**.  이 프로세스를 완료하는 데 몇 초 정도 걸릴 수 있습니다.

1. 다음 PowerShell cmdlet을 실행합니다.

    ````powershell
    Connect-AzureAD -Tenant "WWLxZZZZZZ.onmicrosoft.com"
    $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
    $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
    if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
    Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
    ````

    >**참고:** ZZZZZZ를 ZZZZZZ.onmicrosoft.com 업데이트해야 합니다. ZZZZZZ는 랩 호스팅 공급자가 제공하는 고유한 테넌트 ID입니다. 테넌트 ID에는 정규화된 do기본 이름이 필요합니다.

1. 메시지가 표시되면 MOD 관리istrator 계정으로 로그인합니다.

1. 요청된 **사용 권한 대화 상자에서 정보를 검토한 다음 수락**을 선택합니다**.**

Azure AD 모듈을 성공적으로 설치하고, 필요한 권한을 부여하고, 요청된 권한을 수락했으므로 PowerShell을 사용하여 구성을 진행할 수 있습니다.

## 작업 3: 조직의 사용자 분할

이 작업에서는 PowerShell을 사용하여 보안 및 규정 준수 모듈에 연결하고 법률** 및 **마케팅** 부서에 대한 조직 세그먼트를 **만듭니다.

1. 관리자 권한 PowerShell 창은 계속 열려 있어야 합니다.

1. **PowerShell** 창에서 보안 및 규정 준수 PowerShell에 연결할 cmdlet을 입력합니다.

    ````powershell
    Connect-IPPSSession
    ````

    및 Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com 으로 **로그인합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공하는 고유한 테넌트 ID임).  Joni의 암호는 랩 호스팅 공급자가 제공해야 합니다.

1. **UserGroupFilter** 매개 변수를 사용하여 **New-OrganizationSegment** cmdlet을 실행하여 법적** 세그먼트를 **만듭니다.

    ````powershell
    New-OrganizationSegment -Name "Legal" -UserGroupFilter "Department -eq 'Legal'"
    ````

1. **New-OrganizationSegment** cmdlet을 다시 실행하여 마케팅** 세그먼트를 **만듭니다.

    ````powershell
    New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"
    ````

1. **Get-OrganizationSegment** cmdlet을 실행하여 생성된 세그먼트를 봅니다.

    ````powershell
    Get-OrganizationSegment
    ````

보안 및 규정 준수 PowerShell에 성공적으로 연결하고, 법률 및 마케팅 부서에 대한 조직 세그먼트를 만들고, Get-OrganizationSegment cmdlet을 사용하여 세그먼트를 확인했습니다.

## 작업 4: 정보 장벽 정책 만들기

이 작업에서는 PowerShell을 사용하여 법률 및 마케팅 부서 간의 통신을 차단하는 정보 장벽 정책을 만듭니다.

1. 관리자 권한 PowerShell 창은 계속 열려 있어야 합니다.

1. **SegmentsBlocked** 매개 변수를 사용하여 **New-InformationBarrierPolicy** cmdlet을 실행하여 새 **법률 마케팅** 정책을 만듭니다.

    ````powershell
    New-InformationBarrierPolicy -Name "Legal-Marketing" -AssignedSegment "Legal" -SegmentsBlocked "Marketing" -State Active
    ````

1. 정보 장벽 정책 경고에 대한 알림이 PowerShell 유형 **Y**에 표시되면 Enter** 키를 눌러 **정책 만들기를 계속합니다.

1. 이제 반대 방향으로 차단하도록 정보 장벽 정책을 만들어야 합니다. **SegmentsBlocked** 매개 변수를 사용하여 **New-InformationBarrierPolicy** cmdlet을 실행하여 새 **Marketing-Legal** 정책을 만듭니다.

    ````powershell
    New-InformationBarrierPolicy -Name "Marketing-Legal" -AssignedSegment "Marketing" -SegmentsBlocked "Legal" -State Active
    ````

1. **Get-InformationBarrierPolicy** cmdlet을 실행하여 만들어진 정책을 봅니다.

    ````powershell
    Get-InformationBarrierPolicy
    ````

    >**참고:** 만들어진 정책을 검토할 때 정책이 활성**으로 **표시되는지 확인합니다. 정보 장벽 정책이 적용되기 전에 활성화되어야 합니다.

PowerShell을 사용하여 법률 마케팅 및 마케팅-법률 정보 장벽 정책을 성공적으로 만들고 Get-InformationBarrierPolicy cmdlet을 실행하여 해당 상태 활성으로 확인했습니다.

## 작업 5: 정보 장벽 정책 적용

이 작업에서는 PowerShell을 사용하여 활성 정보 장벽 정책을 적용하고 애플리케이션 상태 검사.

1. 관리자 권한 PowerShell 창은 계속 열려 있어야 합니다.

1. **Start-InformationBarrierPoliciesApplication** cmdlet을 실행하여 활성 정보 장벽 정책을 적용합니다.

    ````powershell
    Start-InformationBarrierPoliciesApplication
    ````

1. **Get-InformationBarrierPoliciesApplicationStatus** cmdlet을 실행하여 적용된 정책을 봅니다.

    ````powershell
    Get-InformationBarrierPoliciesApplicationStatus
    ````

    >**참고:** 시스템에서 정책 적용을 시작하는 데 30분이 걸립니다.

1. 정책이 적용**되면 상태가** NotStarted**에서 **Completed**로 **업데이트됩니다.

Start-InformationBarrierPoliciesApplication cmdlet을 실행하여 정보 장벽 정책을 성공적으로 적용하고 Get-InformationBarrierPoliciesApplicationStatus cmdlet을 사용하여 애플리케이션 상태 확인했습니다.
