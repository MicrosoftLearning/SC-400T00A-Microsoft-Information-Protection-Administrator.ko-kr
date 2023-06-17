---
lab:
  title: '랩 설정: 관리를 위한 환경 준비'
  module: Module 0 - Lab Setup
---

## WWL 테넌트 - 사용 약관

강사 주도 교육 제공의 일부로 테넌트를 제공하는 경우, 강사 주도 교육에서 실습 랩을 지원하기 위해 테넌트를 사용할 수 있습니다.

테넌트를 실습 랩 외부에서 공유하거나 사용해서는 안 됩니다. 이 과정에서 사용되는 테넌트는 평가판 테넌트이며 클래스가 종료된 후 사용하거나 액세스할 수 없으며 확장판에서도 사용할 수 없습니다.

테넌트를 유료 구독으로 변환해서는 안 됩니다. 이 과정의 일부로 얻은 테넌트는 Microsoft Corporation의 재산으로 유지되며 언제든지 액세스 권한을 획득하고 다시 소유할 수 있는 권리를 보유합니다.

# 랩 설정: 관리를 위한 환경 준비

이 랩에서는 관리 작업을 위한 환경을 구성하고 준비합니다. 제공된 단계에 따라 필수 기능 및 설정을 미리 사용하도록 설정하여 향후 랩 활동에서 더 쉽게 학습할 수 있도록 합니다. 이 준비에는 필요한 기능 활성화, 관리 권한 설정 및 주요 요소의 적절한 구성 보장이 포함됩니다. 이 랩 설정을 완료하면 나머지 랩 모듈 전체에서 환경을 효과적으로 관리하고 관리할 수 있는 견고한 기반을 제공합니다.

## 작업 - Microsoft Purview 포털에서 감사 사용

작업에서는 Microsoft Purview 규정 준수 포털 감사를 사용하도록 설정하는 데 중점을 줍니다. 감사를 사용하도록 설정하면 포털 내에서 활동을 추적하고 모니터링하여 가시성과 책임을 보장할 수 있습니다. 제공된 단계에 따라 감사 기능을 미리 구성하고 활성화하여 후속 랩 활동에 대한 포괄적인 감사 내역을 제공합니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 VM(LON-CL1)에 로그인합니다. 암호는 랩 호스팅 공급자가 제공합니다.

1. 사용 가능한 모든 Windows 업데이트가 설치되어 있고 클라이언트가 업데이트 설치를 완료하기 위해 다시 시작할 필요가 없는지 확인합니다.

1. **Microsoft Edge**에서 MICROSOFT Purview 포털로 이동하여 **https://compliance.microsoft.com** MOD 관리자 admin@WWLxZZZZZZ.onmicrosoft.com 로 로그인합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공하는 고유한 테넌트 ID임).

1. 왼쪽 탐색 창에서 **감사를** 선택합니다.

1. **감사** 페이지에서. **사용자 및 관리자 활동 기록 시작**을 선택하여 감사 로깅을 활성화합니다.

## 작업 - Microsoft Teams에서 이름으로 검색 사용

이 작업에서는 랩 설정의 일부로 Microsoft Teams에서 **이름으로 검색** 기능을 사용하도록 설정합니다. 이 기능을 사용하면 사용자가 organization 내에서 특정 개인을 쉽게 찾고 연결할 수 있습니다. 제공된 단계에 따라 정보 장벽으로 작업할 때 사용자가 쉽게 사용할 수 있도록 **이름별 검색** 기능을 미리 구성하고 활성화합니다.

1. **Microsoft Edge**에서 MICROSOFT Purview 포털로 이동하여 **https://admin.teams.microsoft.com** MOD 관리자 admin@WWLxZZZZZZ.onmicrosoft.com 로 로그인합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공하는 고유한 테넌트 ID임). 관리자의 암호는 랩 호스팅 공급자가 제공해야 합니다.

1. 왼쪽 탐색 창의 **Teams** 드롭다운 아래에서 **Teams 설정을** 선택합니다.

1. **이름으로 검색**으로 아래로 스크롤하여 **이 기능을 켜**기로 전환하여 이 기능을 사용하도록 설정합니다.

1. **저장**을 선택하여 이 설정을 저장합니다.

## 작업 - SharePoint Online 및 OneDrive에서 정보 장벽 사용

이 작업에서는 SharePoint Online 및 OneDrive의 정보 장벽을 활성화하여 안전한 공동 작업을 촉진하고 무단 통신을 방지합니다. 제공된 단계에 따라 정보 장벽을 미리 구성하고 활성화합니다.

1. 클라이언트 1 VM(LON-CL1)에 **lon-cl1\admin** 계정으로 로그인되어 있는 상태여야 합니다.

1. 관리자 권한 PowerShell 창을 엽니다. 이렇게 하려면 마우스 오른쪽 단추로 Windows 단추를 선택한 다음, **Windows PowerShell(관리자)** 을 선택합니다.

1. **사용자 계정 컨트롤** 창에서 **예**를 선택하여 실행을 확인합니다.

1. 다음 cmdlet을 입력하여 최신 버전의 Sharepoint Online PowerShell 모듈을 설치합니다.

    ```powershell
    Install-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

1. 다음 cmdlet을 입력하여 SharePoint Online **Enter**의 관리 센터에 연결합니다.

    ```powershell
     Connect-SPOService -Url https://<WWLxZZZZZZ>-admin.sharepoint.com -Credential admin@<WWLxZZZZZZ>.onmicrosoft.com
    ```

    >**참고:** ZZZZZZ를 업데이트해야 합니다. ZZZZZZ는 랩 호스팅 공급자가 제공하는 고유한 테넌트 ID입니다.

1. 랩 호스팅 공급자가 제공한 MOD 관리자 암호로 로그인

1. SharePoint 및 OneDrive에서 정보 장벽을 사용하도록 설정하려면 다음 명령을 실행합니다.

    ```powershell
    Set-SPOTenant -InformationBarriersSuspension $false
    ```

1. 이 작업이 완료되면 PowerShell 창을 닫습니다.