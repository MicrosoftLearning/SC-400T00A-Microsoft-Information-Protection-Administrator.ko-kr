---
lab:
  title: 데모 설정
  module: FY25 VTD Demo - Setup
---

# 데모 랩 0 - VTD 데모 설정

이번 랩에서는 FY25 VTD에 대한 데모 환경을 설정합니다. 해당 랩의 주요 작업은 다음과 같습니다.

- Microsoft Purview에서 내부 위험 관리에 대한 감사 사용
- 디바이스를 엔드포인트 DLP, 내부 위험 관리, 적응형 보호, AI 허브에 온보딩합니다.

환경에서 데모를 실행할 준비를 완료할 수 있도록 VTD 데모를 실행하기 48시간 전에 이 작업을 수행하세요.

랩에 문제가 있는 경우 해결을 위해 제 연락처(richelle.swinton@microsoft.com)로 문의해 주세요.

## Skillable 환경 액세스

1. SC-400 랩 프로필에 액세스합니다([https://gtllabs.learnondemand.net/Lab/68392](https://gtllabs.learnondemand.net/Lab/68392)).

1. 적절한 자격 증명으로 로그인합니다.

1. **시작** 버튼을 선택하여 랩을 시작합니다.

1. 랩 환경을 로드하기 위한 새 창이 열립니다. 랩 프로필이 로드되기를 기다립니다. 이 작업은 몇 분 정도 걸립니다.

1. 데모 실행을 위해 이 랩을 쉽게 표시하려면 **리소스** 탭에서 자격 증명을 사용하고 Microsoft Edge의 시크릿 창에서 랩을 실행하는 방법이 가장 쉬울 수 있습니다.

    ![새 Microsoft Purview 포털의 시작 화면을 보여주는 스크린샷.](/Instructions/Media/skillable-credentials.png)

1. 디바이스를 온보딩하려면 Skillable 랩 VM에서 랩 설정을 실행해야 합니다.

## 작업 1 - 사용자 암호 설정 데모 연습

이 작업에서는 랩에 필요한 사용자 계정의 암호를 설정합니다.

1. 클라이언트 1 VM(SC-400-CL1)에 **SC-400-CL1\admin** 계정으로 로그인합니다. 암호는 랩 호스팅 공급자가 제공합니다.

1. **Microsoft Edge**를 열고 **`https://admin.microsoft.com`** 로 이동하여 MOD 관리자 `admin@WWLxZZZZZZ.onmicrosoft.com`(여기서 ZZZZZZ는 랩 호스팅 제공업체에서 제공한 고유 테넌트 ID)로 Microsoft Purview 포털에 로그인합니다.

1. 왼쪽 탐색 창에서 **사용자**를 확장한 다음 **활성 사용자**를 선택합니다.

1. **Joni Sherman** 왼쪽에 있는 확인란을 선택합니다.

   이 계정이 데모 연습에 사용됩니다.

1. 상단 탐색 리본에서 **암호 재설정** 버튼을 선택하여 Joni의 암호를 재설정합니다.

   ![Microsoft 365 관리 센터에서 암호 재설정 단추를 보여 주는 스크린샷](/Instructions/Media/reset-password-button.png)

1. 오른쪽의 **암호 재설정** 플라이아웃 페이지에서 모든 옵션이 선택 취소되었는지 확인합니다.

   이 방법으로 데모 연습에 사용할 Joni의 암호를 선택할 수 있으며, 처음 로그인할 때 이 암호를 재설정할 필요가 없습니다.

1. **암호** 필드에 향후 연습에 사용할 사용자 암호를 재설정하기 위해 기억할 수 있는 암호를 입력합니다.

1. **암호 재설정** 플라이아웃 페이지 하단에서 **암호 재설정** 단추를 선택합니다.

1. **암호가 다시 설정됨** 페이지에서 다시 설정된 세 개의 사용자 계정을 확인할 수 있습니다. 플라이아웃 페이지 하단에서 **저장**을 선택합니다.

랩 연습의 암호를 성공적으로 다시 설정했습니다.

## 작업 2 - Microsoft Purview에서 감사 사용

1. 클라이언트 1 VM(SC-400-CL1)에 **SC-400-CL1\admin** 계정으로 로그인합니다. 암호는 랩 호스팅 공급자가 제공합니다.

1. **Microsoft Edge**를 열고 **`https://purview.microsoft.com`** 로 이동하여 MOD 관리자 `admin@WWLxZZZZZZ.onmicrosoft.com`(여기서 ZZZZZZ는 랩 호스팅 제공업체에서 제공한 고유 테넌트 ID)로 Microsoft Purview 포털에 로그인합니다.

1. 새 Microsoft Purview 포털에 대한 메시지가 화면에 표시됩니다. 데이터 흐름 공개 약관 및 개인정보처리방침에 동의하는 옵션을 선택한 다음 **지금 사용**을 선택합니다.

    ![새 Microsoft Purview 포털의 시작 화면을 보여주는 스크린샷.](/Instructions/Media/welcome-purview-portal.png)

1. 왼쪽 사이드바에서 **솔루션**을 선택한 다음 **감사**을 선택합니다.

1. **검색** 페이지에서 **사용자 및 관리자 활동 기록 시작** 표시줄을 선택하여 감사 로깅을 활성화합니다.

    ![사용자 및 관리자 활동 기록 시작 단추를 보여 주는 스크린샷.](/Instructions/Media/enable-audit-button.png)

1. 이 옵션을 선택하면 이 페이지에서 파란색 표시줄이 사라집니다.

Microsoft 365에서 감사를 사용하도록 성공적으로 설정했습니다.

## 작업 3 - 엔드포인트 DLP에 디바이스 온보딩

이 작업에서는 조직에서 디바이스 온보딩을 사용하도록 설정합니다.

1. 여전히 클라이언트 1 VM(SC-400-CL1)에 **SC-400-cl1\admin** 계정으로 로그인되어 있는 상태여야 합니다.

    또한 Microsoft Purview에 계속 MOD 관리자로 로그인한 상태여야 합니다.

1. Microsoft Purview 포털의 왼쪽 사이드바에서 **설정**을 선택합니다. **디바이스 온보딩**을 확장한 다음 **디바이스**를 선택합니다.

1. **디바이스** 페이지에서 **디바이스 온보딩 켜기**를 선택하여 테넌트에 대한 솔루션을 사용하도록 설정합니다.

1. **디바이스 온보딩 켜기** 대화 상자에서 **확인**을 선택하여 디바이스 온보딩을 적용합니다.

1. **디바이스 모니터링 켜기** 대화 상자에서 **확인**을 선택하여 디바이스 모니터링을 적용합니다.

이제 디바이스 온보딩이 사용하도록 설정되었으므로 엔드포인트 DLP 정책을 사용하여 보호할 디바이스 온보딩을 시작할 수 있습니다. 기능을 사용하도록 설정하는 프로세스는 최대 30분이 걸릴 수 있습니다.

## 작업 4 - 엔드포인트 DLP에 디바이스 온보딩

이 작업에서는 엔드포인트 DLP 정책을 통해 보호할 수 있도록 로컬 스크립트 옵션을 사용하여 Windows 11 디바이스를 온보딩합니다.

1. 여전히 클라이언트 1 VM(SC-400-CL1)에 **SC-400-CL1\admin** 계정으로 로그인되어 있는 상태여야 합니다.

   또한 Microsoft Purview에 계속 MOD 관리자로 로그인한 상태여야 합니다.

   또한 계속 엔드포인트 DLP의 **디바이스** 페이지에 있어야 합니다.

1. Microsoft Purview 포털의 **디바이스** 페이지에서 **디바이스 온보딩**이 확장되었는지 확인하고 **온보딩**을 선택합니다.

1. **디바이스 온보딩** 페이지의 왼쪽 탐색 창에서 **온보딩**을 선택합니다.

1. **배포 방법** 드롭다운 메뉴에서 **로컬 스크립트(최대 컴퓨터 10대에 사용 가능)** 를 선택하고 **패키지 다운로드**를 선택합니다.

1. **다운로드** 대화 상자에서 다운로드를 마우스로 가리킨 다음 폴더 아이콘을 선택하여 **폴더에 표시**합니다.

1. SC-400-CL1의 **바탕 화면**에 zip 파일의 압축을 풉니다. **DeviceComplianceLocalOnboardingScript.cmd** 스크립트가 표시됩니다.

1. 바탕 화면에서 방금 압축을 푼 **DeviceComplianceLocalOnboardingScript.cmd** 파일을 마우스 오른쪽 버튼으로 클릭하고 **추가 옵션 표시**를 선택한 다음, **속성**을 선택합니다.

1. 속성 창의 **일반** 탭 아래쪽에 있는 **보안** 섹션에서 **차단 해제**를 선택한 다음 **확인**을 선택하여 이 설정을 저장합니다.

1. 바탕 화면으로 돌아가서 **DeviceComplianceLocalOnboardingScript.cmd**를 마우스 오른쪽 버튼으로 클릭하고 **관리자 권한으로 실행**을 선택합니다. **사용자 계정 컨트롤** 대화 상자에서 **예**를 선택합니다.

1. **명령 프롬프트** 화면에서 **Y**를 입력하여 실행을 확인하고 Enter 키를 누릅니다.

1. 스크립트가 완료되면 성공 메시지와 **아무 키나 눌러 계속**하라는 메시지가 표시됩니다. 아무 키나 눌러 명령줄 창을 닫습니다. 온보딩을 완료하려면 1분 정도 걸릴 수 있습니다.

1. 시작 메뉴를 열고 .`Access work or school`를 검색합니다. **가장 일치하는 항목**에서 **회사 또는 학교 액세스**를 선택합니다.

1. **회사 또는 학교 계정 추가**의 **회사 또는 학교 액세스** 창에서 **연결**을 선택합니다.

1. **회사 또는 학교 계정 설정** 대화 상자에서 **이 디바이스를 Microsoft Entra ID에 조인** 링크를 선택하고 **MOD 관리자** `admin@WWLxZZZZZZ.onmicrosoft.com`(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID)으로 로그인합니다.

1. **조직 확인** 대화 상자에서 테넌트 URL을 검토하고 **가입**을 선택합니다.  

1. 디바이스가 연결되면 **모든 설정 완료** 화면에서**완료**를  선택합니다.

1. 클라이언트 1 VM(SC-400-CL1)을 다시 시작합니다.

1. 클라이언트 1 VM을 사용할 수 있게 되면 클라이언트 1 VM(SC-400-CL1)에 다시 로그인합니다.

1. Microsoft Edge를 열고 **`https://purview.microsoft.com`** 으로 다시 이동하여 MOD 관리자 `admin@WWLxZZZZZZ.onmicrosoft.com`(여기서 ZZZZZZ는 랩 호스팅 제공업체에서 제공한 고유 테넌트 ID)로 Microsoft Purview 포털에 로그인합니다.

1. Microsoft Purview 포털에서 **설정** > **디바이스 온보딩** > **디바이스**로 이동하여 디바이스가 성공적으로 온보딩되었는지 확인합니다.

디바이스를 성공적으로 온보딩하고 엔드포인트 DLP 정책의 보호를 받을 수 있도록 Microsoft Entra ID에 가입했습니다.

## 작업 5 - 민감도 레이블을 지원하도록 설정

이 작업에서는 필요한 모듈을 설치하고 테넌트에서 민감도 레이블에 대한 지원을 사용하도록 설정합니다.

1. 여전히 클라이언트 1 VM(SC-400-CL1)에 **SC-400-CL1\admin** 계정으로 로그인되어 있는 상태여야 합니다.

1. 작업 표시줄에서 Windows 단추를 마우스 오른쪽 단추로 클릭하여 관리자 권한 PowerShell 창을 연 다음 **터미널(관리자)** 을 선택합니다.

1. **사용자 계정 컨트롤** 창에서 **예**를 선택하고 Enter 키를 눌러 실행을 확인합니다.

1. **설치-모듈** cmdlet을 실행하여 최신 MS Online PowerShell 모듈 버전을 설치합니다.

    ```powershell
    Install-Module -Name MSOnline
    ```

1. Nuget 보안 대화 상자와 신뢰할 수 없는 리포지토리 보안 대화 상자에서 예를 나타내는 **Y**를 확인하고 Enter 키를 누릅니다. 처리를 완료하는 데 시간이 걸릴 수 있습니다.

1. **설치-모듈** cmdlet을 실행하여 최신 SharePoint Online PowerShell 모듈 버전을 설치합니다.

    ```powershell
    Install-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

1. 신뢰할 수 없는 리포지토리 보안 대화 상자가 표시되면 Yes에 해당하는 **Y** 키를 누르고 Enter 키를 누릅니다.

1. **Connect-MsolService**를 실행하여 MS Online 서비스에 연결합니다.

    ```powershell
    Connect-MsolService
    ```

1. **계정에 로그인** 양식에서 **MOD 관리자**`admin@WWLxZZZZZZ.onmicrosoft.com`(여기서 ZZZZZZ는 랩 호스팅 공급자에서 제공한 고유 테넌트 ID)로 로그인합니다.

1. 로그인한 후 터미널 창으로 다시 이동합니다.

1. **Get-Msoldomain** cmdlet을 실행하고 도메인을 변수로 저장합니다.

    ```powershell
    $domain = get-msoldomain
    ```

1. 이전 단계에서 만든 _$domain_ 변수를 사용하여 _$adminurl_에 대한 새 변수를 만듭니다.

    ```powershell
    $adminurl = "https://" + $domain.Name.split('.')[0] + "-admin.sharepoint.com"
    ```

1. 이전 단계에서 만든 _$adminurl_ 변수를 사용하여 **Connect-SPOService** cmdlet을 실행합니다.

    ```powershell
    Connect-SPOService -url $adminurl
    ```

1. **계정에 로그인** 양식에서 **MOD 관리자**로 로그인합니다. `admin@WWLxZZZZZZ.onmicrosoft.com`(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID입니다). 관리자의 암호는 랩 호스팅 공급자가 제공합니다.

1. 로그인한 후 터미널 창으로 다시 이동합니다.

1. **Set-SPOTenant** cmdlet을 실행하여 민감도 레이블이 지원되도록 설정합니다.

    ```powershell
    Set-SPOTenant -EnableAIPIntegration $true
    ```

1. Yes에 해당하는 **Y** 키를 눌러 변경 내용 적용을 확인하고 Enter 키를 누릅니다.

1. PowerShell 창을 닫습니다.

Teams 및 SharePoint 사이트에 대해 민감도 레이블이 지원되도록 설정했습니다.

## 작업 6 - 암호화된 민감도 레이블이 적용되어 OneDrive 및 SharePoint에 저장된 Office 온라인 파일의 콘텐츠를 처리하는 기능 설정

1. **Microsoft Edge**를 열고 **`https://purview.microsoft.com`** 로 이동하여 MOD 관리자 `admin@WWLxZZZZZZ.onmicrosoft.com`(여기서 ZZZZZZ는 랩 호스팅 제공업체에서 제공한 고유 테넌트 ID)로 Microsoft Purview 포털에 로그인합니다.

1. 왼쪽 사이드바에서 **솔루션**을 선택한 다음, **Information Protection** > **민감도 레이블**을 선택합니다.

1. **조직에서 암호화된 민감도 레이블이 적용되어 OneDrive 및 SharePoint에 저장된 Office 온라인 파일의 콘텐츠를 처리하는 기능을 설정하지 않았습니다. 여기에서 사용하도록 설정할 수 있지만, Multi-Geo 환경에 대한 추가 구성이 필요합니다.** 라는 메시지가 표시된 노란색 대화 상자에서 **지금 사용**을 선택합니다.

1. **이제 Teams, SharePoint 사이트, Microsoft 365 그룹에 대해 개인 정보 및 액세스 제어 설정을 사용하여 민감도 레이블을 만들 수 있습니다.** 라는 메시지가 표시됩니다.
