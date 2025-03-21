---
lab:
  title: '랩 설정: 관리를 위한 환경 준비'
  module: Module 0 - Lab Setup
---

## WWL 테넌트 - 사용 약관

강사 진행 교육 제공의 일부로 테넌트를 제공하는 경우, 강사 진행 교육에서 실습 랩을 지원하기 위해 테넌트를 사용할 수 있습니다.

테넌트를 실습 랩 외부에서 공유하거나 사용해서는 안 됩니다. 이 과정에서 사용되는 테넌트는 평가판 테넌트이며 클래스가 종료된 후 사용하거나 액세스할 수 없으며 확장판에서도 사용할 수 없습니다.

테넌트를 유료 구독으로 변환해서는 안 됩니다. 이 과정의 일부로 얻은 테넌트는 Microsoft Corporation의 재산으로 유지되며 언제든지 액세스 권한을 획득하고 다시 소유할 수 있는 권리를 보유합니다.

# 랩 설정: 관리를 위한 환경 준비

이 랩에서는 관리 작업을 위한 환경을 구성하고 준비합니다. 필요한 기능을 활성화하고, 관리 권한을 설정하고, 주요 요소를 적절하게 구성할 수 있습니다.

**작업**:

- 랩 연습을 위한 사용자 암호 설정
- Microsoft Purview 포털에서 감사 사용
- Microsoft Teams에서 이름으로 검색 사용
- SharePoint Online 및 OneDrive에서 정보 장벽 사용

## 작업 - 랩을 위한 사용자 암호 설정

이 작업에서는 랩에 필요한 사용자 계정의 암호를 설정합니다.

1. 클라이언트 1 VM(SC-400-CL1)에 **SC-400-CL1\admin** 계정으로 로그인합니다. 암호는 랩 호스팅 공급자가 제공합니다.

1. **Microsoft Edge**를 열고 **`https://admin.microsoft.com`** 로 이동하여 Microsoft 365 관리 센터에 MOD 관리자(`admin@WWLxZZZZZZ.onmicrosoft.com`)로 로그인합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID).

1. 왼쪽 탐색 창에서 **사용자**를 확장한 다음 **활성 사용자**를 선택합니다.

1. **Joni Sherman**, **Lynne Robbins**, **Megan Bowen**의 왼쪽에 있는 확인란을 선택합니다.

   이러한 계정은 랩 연습을 통해 사용됩니다.

   ![재설정해야 하는 사용자 계정을 보여 주는 스크린샷.](../Media/user-accounts.png)

1. 상단 탐색 리본에서 **암호 재설정** 단추를 선택하여 세 개의 암호를 모두 재설정합니다.

   ![Microsoft 365 관리 센터에서 암호 재설정 단추를 보여 주는 스크린샷](../Media/reset-password-button.png)

1. 오른쪽의 **암호 재설정** 플라이아웃 페이지에서 모든 옵션이 선택 취소되었는지 확인합니다.

   이렇게 하면 연습에 사용되는 세 명의 사용자에 대한 암호를 선택할 수 있으며, 처음 로그인할 때 이러한 암호를 재설정할 필요가 없습니다.

1. **암호** 필드에 향후 연습에 사용할 사용자 암호를 재설정하기 위해 기억할 수 있는 암호를 입력합니다.

1. **암호 재설정** 플라이아웃 페이지 하단에서 **암호 재설정** 단추를 선택합니다.

1. **암호가 다시 설정됨** 페이지에서 다시 설정된 세 개의 사용자 계정을 확인할 수 있습니다. 플라이아웃 페이지 하단에서 **저장**을 선택합니다.

랩 연습의 암호를 성공적으로 다시 설정했습니다.

## 작업 - Microsoft Purview 포털에서 감사 사용

이 작업에서는 Microsoft Purview 포털에서 감사를 사용하도록 설정하여 포털 활동을 모니터링합니다.

1. 계속 클라이언트 1 VM(SC-400-CL1)에 **SC-400-CL1\admin** 계정으로 로그인하고 MOD 관리자 계정으로 Microsoft 365에 로그인해야 합니다.

1. Microsoft Edge에서 Microsoft Purview 포털(`https://purview.microsoft.com`)로 이동하여 로그인합니다.

1. 새 Microsoft Purview 포털에 대한 메시지가 화면에 표시됩니다. 데이터 흐름 공개 약관 및 개인정보처리방침에 동의하는 옵션을 선택한 다음 **지금 사용**을 선택합니다.

    ![새 Microsoft Purview 포털의 시작 화면을 보여주는 스크린샷.](../Media/welcome-purview-portal.png)

1. 왼쪽 사이드바에서 **솔루션**을 선택한 다음 **감사**을 선택합니다.

1. **검색** 페이지에서 **사용자 및 관리자 활동 기록 시작** 표시줄을 선택하여 감사 로깅을 활성화합니다.

    ![사용자 및 관리자 활동 기록 시작 단추를 보여 주는 스크린샷.](../Media/enable-audit-button.png)

1. 이 옵션을 선택하면 이 페이지에서 파란색 표시줄이 사라집니다.

>[!경고] 이 연습에서 감사를 사용하도록 설정하는 동안 오류가 발생하는 경우 다음 단계를 해결 방법으로 사용합니다.
>1. 마우스 오른쪽 단추를 누르고 Windows 단추를 선택하여 권한이 있는 터미널 창을 열고, 터미널(관리자)을 선택합니다.
>1. 실행하여 ExchangeOnlineManagement 모듈 설치 `Install-Module -Name ExchangeOnlineManagement`
>1. 실행하여 ExchangeOnlineManagement에 연결 `Connect-ExchangeOnline`
>1. 메시지가 표시되면 랩 호스팅 공급자에서 관리자 사용자 이름 및 암호를 입력하여 로그인합니다.
>1. 감사를 사용할 수 있는지 확인하려면 다음을 실행합니다. `Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled` 
>1. false이면 감사 로그가 꺼집니다.
>1. 감사를 사용하도록 설정하려면 다음을 실행합니다.`Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true`
>   1. 조직에서 스크립트를 실행할 수 없다는 오류가 표시되면 다음을 실행합니다. `Enable-OrganizationCustomization` 
>   1. 다시 시도하여 다음을 실행합니다. `Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true` 
>1. 감사가 사용하도록 설정되어 있는지 확인하려면 다음을 실행합니다. `Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled` 
>1. 완료되면 세션을 종료하기 위해 다음을 실행합니다. `Disconnect-ExchangeOnline` 

Microsoft 365에서 감사를 사용하도록 성공적으로 설정했습니다.

## 작업 - Microsoft Teams에서 이름으로 검색 사용

이 작업에서는 Microsoft Teams에서 **이름으로 검색** 기능을 활성화하여 사용자 위치를 쉽게 찾을 수 있도록 합니다. 이는 이후 연습에서 정보 장벽을 구성하는 데 필요합니다.

1. 계속 클라이언트 1 VM(SC-400-CL1)에 **SC-400-CL1\admin** 계정으로 로그인하고 MOD 관리자 계정으로 Microsoft 365에 로그인해야 합니다.

1. **Microsoft Edge**에서 **`https://admin.teams.microsoft.com`** 으로 이동합니다.

1. 왼쪽 탐색 창의 **Teams** 드롭다운에서 **Teams 설정**을 선택합니다.

    ![Teams 관리 포털의 Teams 설정 단추를 보여 주는 스크린샷.](../Media/teams-settings.png)

1. **이름으로 검색** 섹션까지 아래로 스크롤하고 **Exchange 주소록 정책을 사용하여 범위 디렉터리 검색**을**켜기**로 전환합니다

1. 페이지 맨 아래에서 **저장**을 선택합니다.

1. **변경 사항이 적용되는 데 시간이 걸립니다** 대화상자에서 **확인**을 선택합니다.

Microsoft Teams에서 정보 장벽에 대한 이름별 검색 기능을 사용하도록 설정했습니다.

## 작업 - SharePoint Online 및 OneDrive에서 정보 장벽 사용

이 작업에서는 안전한 협업을 위해 SharePoint Online 및 OneDrive에서 정보 장벽을 사용하도록 설정합니다.

1. 여전히 클라이언트 1 VM(SC-400-CL1)에 **SC-400-CL1\admin** 계정으로 로그인되어 있는 상태여야 합니다.

1. 관리자 권한 PowerShell 창을 엽니다. 이렇게 하려면 마우스 오른쪽 단추로 Windows 단추를 선택한 다음, **Windows PowerShell(관리자)** 을 선택합니다.

1. **사용자 계정 컨트롤** 창에서 **예**를 선택하여 실행을 확인합니다.

1. 다음 cmdlet을 실행하여 최신 버전의 SharePoint Online PowerShell 모듈을 설치합니다.

    ```powershell
    Install-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

1. PowerShell NuGet 공급자를 설치하라는 메시지가 표시되면 **Y**를 입력하여 공급자를 설치합니다.

1. 신뢰할 수 없는 리포지토리에서 설치하라는 메시지가 표시되면 **Y**를 입력하여 PSGallery에서 모듈을 설치합니다.

1. 다음 cmdlet을 실행하여 SharePoint Online 관리 센터에 연결합니다.

    ```powershell
     Connect-SPOService -Url https://WWLxZZZZZZ-admin.sharepoint.com
    ```

    >**참고:** ZZZZZZ를 반드시 업데이트합니다. ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID입니다.

1. 랩 호스팅 공급자에서 제공한 MOD 관리자 암호로 로그인합니다.

1. 다음 명령을 실행하여 SharePoint 및 OneDrive에서 정보 장벽을 사용하도록 설정합니다.

    ```powershell
    Set-SPOTenant -InformationBarriersSuspension $false
    ```

1. 이 작업이 완료되면 PowerShell 창을 닫습니다.

SharePoint Online 및 OneDrive에서 정보 장벽을 사용하도록 설정했습니다.
