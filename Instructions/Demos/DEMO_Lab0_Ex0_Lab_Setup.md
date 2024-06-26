---
lab:
  title: '데모 설정: 관리를 위한 환경 준비'
  module: Module 0 - Lab Setup
---

## WWL 테넌트 - 사용 약관

강사 진행 교육 제공의 일부로 테넌트를 제공하는 경우, 강사 진행 교육에서 실습 랩을 지원하기 위해 테넌트를 사용할 수 있습니다.

테넌트를 실습 랩 외부에서 공유하거나 사용해서는 안 됩니다. 이 과정에서 사용되는 테넌트는 평가판 테넌트이며 클래스가 종료된 후 사용하거나 액세스할 수 없으며 확장판에서도 사용할 수 없습니다.

테넌트를 유료 구독으로 변환해서는 안 됩니다. 이 과정의 일부로 얻은 테넌트는 Microsoft Corporation의 재산으로 유지되며 언제든지 액세스 권한을 획득하고 다시 소유할 수 있는 권리를 보유합니다.

# 랩 설정: 관리를 위한 환경 준비

이 랩에서는 관리 작업을 위한 환경을 구성하고 준비합니다. 제공된 단계를 따르면 필수 기능과 설정이 미리 사용하도록 설정되어 예정된 랩 작업에서 더 쉽게 학습할 수 있습니다. 이 준비에는 필요한 기능 활성화, 관리 권한 설정, 핵심 요소의 적절한 구성 확인이 포함됩니다.

## 작업 - Microsoft Purview 포털에서 감사 사용

이 작업에서는 Microsoft Purview 규정 준수 포털에서 감사를 사용하도록 설정합니다. 이 추적 기능을 통해 포털 작업의 표시 여부와 책임성을 모니터링할 수 있습니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 MOD 관리자 계정으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge**에서 **https://compliance.microsoft.com**으로 이동합니다.

1. 왼쪽 탐색 창에서 **감사**를 선택합니다.

1. **감사** 페이지에서. **사용자 및 관리자 활동 기록 시작**을 선택하여 감사 로깅을 활성화합니다.

## 작업 - 민감도 레이블 지원 사용

이 작업에서는 MSOnline 모듈과 SharePoint Online PowerShell 모듈을 설치하고 테넌트에서 민감도 레이블을 지원하도록 설정합니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 VM(LON-CL1)에 로그인합니다.

1. 관리자 권한 PowerShell 창을 엽니다. 이렇게 하려면 마우스 오른쪽 단추로 시작 메뉴를 선택한 다음 **Windows PowerShell**을 선택하여 관리자로 PowerShell을 실행합니다.

1. **사용자 계정 컨트롤** 창에서 **예**를 선택하고 Enter 키를 눌러 실행을 확인합니다.

1. 다음 cmdlet을 입력하여 최신 MS Online PowerShell 모듈 버전을 설치합니다.

   ```powershell
   Install-Module -Name MSOnline
   ```

1. Nuget 보안 대화 상자와 신뢰할 수 없는 리포지토리 보안 대화 상자에서 예를 나타내는 **Y**를 확인하고 Enter 키를 누릅니다.  처리를 완료하는 데 시간이 걸릴 수 있습니다.

1. 다음 cmdlet을 입력하여 최신 SharePoint Online PowerShell 모듈 버전을 설치합니다.

    ```powershell
    Install-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

1. 신뢰할 수 없는 리포지토리 보안 대화 상자가 표시되면 Yes에 해당하는 **Y** 키를 누르고 Enter 키를 누릅니다.

1. 다음 cmdlet을 입력하여 MS Online 서비스에 연결합니다.

    ```powershell
    Connect-MsolService
    ```

1. **계정에 로그인** 양식에서 **MOD 관리자** admin@WWLxZZZZZZ.onmicrosoft.com로 로그인합니다. 여기서 ZZZZZZ는 랩 호스팅 공급자에서 제공한 고유 테넌트 ID입니다.  Joni의 암호는 랩 호스팅 공급자가 제공합니다.

1. 로그인 후 PowerShell 창을 선택합니다.

1. 다음 cmdlet을 입력하여 도메인을 가져옵니다.

    ```powershell
    $domain = get-msoldomain
    ```

1. 다음 cmdlet을 입력하여 SharePoint 관리 URL을 만듭니다.

    ```powershell
    $adminurl = "https://" + $domain.Name.split('.')[0] + "-admin.sharepoint.com"
    ```

1. 다음 cmdlet을 입력하여 SharePoint Online 관리 센터에 로그인합니다.

    ```powershell
    Connect-SPOService -url $adminurl
    ```

1. **계정에 로그인** 양식에서 **MOD 관리자**로 로그인합니다. admin@WWLxZZZZZZ.onmicrosoft.com(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID입니다).  관리자의 암호는 랩 호스팅 공급자가 제공합니다.

1. 로그인 후 PowerShell 창을 선택합니다.

1. 다음 cmdlet을 입력하여 민감도 레이블이 지원되도록 설정합니다.

    ```powershell
    Set-SPOTenant -EnableAIPIntegration $true
    ```

1. Yes에 해당하는 **Y** 키를 눌러 변경 내용 적용을 확인하고 Enter 키를 누릅니다.

1. PowerShell 창을 닫습니다.

Teams 및 SharePoint 사이트에서 민감도 레이블이 지원되도록 설정했습니다.