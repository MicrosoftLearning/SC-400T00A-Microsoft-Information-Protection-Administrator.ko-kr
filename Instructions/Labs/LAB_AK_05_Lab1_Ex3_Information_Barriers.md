---
lab:
  title: 연습 3 - 정보 장벽 구성
  module: Module 5 - Manage insider and privacy risk in Microsoft 365
---

# 랩 5 - 연습 3 - 정보 장벽 구성

Contoso Ltd.의 규정 준수 관리자인 Joni는 Microsoft 365에서 정보 장벽을 구성하고 관리해야 합니다. 정보 장벽은 명확한 경계를 유지하고 조직 내의 특정 그룹 또는 개인 간의 무단 통신을 방지하는 데 중요한 역할을 합니다. 정보 장벽을 구현하여 규정 준수를 보장하고 중요한 정보를 보호하며 이해 충돌을 최소화합니다. 이 설정은 안전한 작업 환경을 만들어 데이터 기밀성을 보호하고 규정 준수에 대한 Contoso Ltd.의 약속을 지원합니다.

1. Microsoft Teams에서 이름으로 검색이 사용하도록 설정되어 있는지 확인
1. 조직의 사용자 세그먼트 지정
1. 정보 장벽 정책 만들기
1. 정보 장벽 정책 적용

## 작업 1 - Microsoft Teams에서 이름으로 검색이 사용하도록 설정되어 있는지 확인

이 작업에서는 Microsoft Teams에서 **이름으로 검색** 기능이 사용하도록 설정되어 있는지 확인합니다. 이 기능을 사용하면 사용자가 조직 내에서 특정 개인을 쉽게 검색하고 찾을 수 있습니다. 제공된 단계에 따라 이 기능을 구성하고 활성화하여 조직의 Microsoft Teams 환경 내에서 공동 작업을 강화하고 커뮤니케이션을 간소화합니다.

1. **SC-400-cl1\admin** 계정으로 클라이언트 1 VM(SC-400-CL1)에 로그인합니다.

1. Joni의 계정으로 로그인되어 있는 경우 이 계정에서 로그아웃하고 모든 브라우저 창을 닫습니다.

1. **Microsoft Edge**에서 **`https://admin.teams.microsoft.com`** 으로 이동한 다음, Microsoft Purview 포털에 MOD 관리자 `admin@WWLxZZZZZZ.onmicrosoft.com`으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).

1. 왼쪽 탐색 창의 **Teams** 드롭다운에서 **Teams 설정**을 선택합니다.

1. **이름으로 검색**까지 아래로 스크롤합니다. 이 기능을 끄기로 설정한 경우 이 기능을 **켜고** **저장**을 선택하여 이 설정을 저장합니다.

1. **변경 사항이 적용되는 데 시간이 걸립니다** 팝업에서 **확인**을 선택합니다.

    >**참고:** 이 변경 내용이 적용되려면 몇 시간이 걸릴 수 있습니다.

## 작업 2 - 조직의 사용자 세그먼트 지정

이 작업에서는 PowerShell을 사용하여 보안 및 규정 준수 모듈에 연결하고 **법무**팀 및 **마케팅**팀에 대한 조직 세그먼트를 만듭니다.

1. 작업 표시줄에서 Windows 단추를 마우스 오른쪽 단추로 클릭하여 관리자 권한 PowerShell 창을 연 다음 **터미널(관리자)** 을 선택합니다.

1. 터미널 창에서 보안 및 규정 준수 PowerShell에 연결할 cmdlet을 입력합니다.

    ````powershell
    Connect-IPPSSession
    ````

    **Joni Sherman**`JoniS@WWLxZZZZZZ.onmicrosoft.com`으로 로그인합니다. 여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID입니다. Joni의 암호는 이전 연습에서 설정되었습니다.

1. **UserGroupFilter** 매개 변수를 사용하여 **New-OrganizationSegment** cmdlet을 실행하여 **Legal** 세그먼트를 만듭니다.

    ````powershell
    New-OrganizationSegment -Name "Legal" -UserGroupFilter "Department -eq 'Legal'"
    ````

1. **New-OrganizationSegment** cmdlet을 다시 실행하여 **마케팅** 세그먼트를 만듭니다.

    ````powershell
    New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"
    ````

1. **Get-OrganizationSegment** cmdlet을 실행하여 생성된 세그먼트를 봅니다.

    ````powershell
    Get-OrganizationSegment
    ````

보안 & 준수 PowerShell에 성공적으로 연결하고, 법무팀 및 마케팅팀에 대한 조직 세그먼트를 만들고, Get-OrganizationSegment cmdlet을 사용하여 세그먼트를 보았습니다.

## 작업 3 - 정보 장벽 정책 만들기

이 작업에서는 PowerShell을 사용하여 법무팀과 마케팅팀 간의 통신을 차단하는 정보 장벽 정책을 만듭니다.

1. 관리자 권한 PowerShell 창이 계속 열려 있어야 합니다.

1. **SegmentsBlocked** 매개 변수를 사용하여 **New-InformationBarrierPolicy** cmdlet을 실행하여 새 **Legal-Marketing** 정책을 만듭니다.

    ````powershell
    New-InformationBarrierPolicy -Name "Legal-Marketing" -AssignedSegment "Legal" -SegmentsBlocked "Marketing" -State Active
    ````

1. 정보 장벽 정책 경고에 대한 알림이 PowerShell에 표시되면 **Y**를 입력한 다음 **Enter** 키를 눌러 정책 만들기를 진행합니다.

1. 이제 반대 방향으로 차단하도록 정보 장벽 정책을 만들어야 합니다. **SegmentsBlocked** 매개 변수를 사용하여 **New-InformationBarrierPolicy** cmdlet을 실행하여 새 **Marketing-Legal** 정책을 만듭니다.

    ````powershell
    New-InformationBarrierPolicy -Name "Marketing-Legal" -AssignedSegment "Marketing" -SegmentsBlocked "Legal" -State Active
    ````

1. **Get-InformationBarrierPolicy** cmdlet을 실행하여 만들어진 정책을 봅니다.

    ````powershell
    Get-InformationBarrierPolicy
    ````

    >**참고:** 만들어진 정책을 검토할 때 정책이 **활성**으로 표시되는지 확인합니다. 정보 장벽 정책이 적용되기 전에 활성화되어야 합니다.

PowerShell을 사용하여 Legal-Marketing 및 Marketing-Legal 정보 장벽 정책을 성공적으로 만들고 Get-InformationBarrierPolicy cmdlet을 실행하여 해당 상태를 활성으로 확인했습니다.

## 작업 4 - 정보 장벽 정책 적용

이 작업에서는 PowerShell을 사용하여 활성 정보 장벽 정책을 적용하고 해당 애플리케이션 상태를 확인합니다.

1. 관리자 권한 PowerShell 창이 계속 열려 있어야 합니다.

1. **Start-InformationBarrierPoliciesApplication** cmdlet을 실행하여 활성 정보 장벽 정책을 적용합니다.

    ````powershell
    Start-InformationBarrierPoliciesApplication
    ````

1. **Get-InformationBarrierPoliciesApplicationStatus** cmdlet을 실행하여 적용된 정책을 봅니다.

    ````powershell
    Get-InformationBarrierPoliciesApplicationStatus
    ````

    >**참고:** 시스템에서 정책 적용을 시작하는 데 30분이 걸립니다.

1. 정책이 적용되면 **상태**가 **NotStarted**에서 **Completed**로 업데이트됩니다.

Start-InformationBarrierPoliciesApplication cmdlet을 실행하여 정보 장벽 정책을 성공적으로 적용하고 Get-InformationBarrierPoliciesApplicationStatus cmdlet을 사용하여 해당 애플리케이션 상태를 확인했습니다.
