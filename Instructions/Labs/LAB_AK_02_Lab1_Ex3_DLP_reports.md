---
lab:
  title: 연습 3 - DLP 보고서 관리
  module: Module 2 - Implement Data Loss Prevention
---

# 랩 2 - 연습 3 - DLP 보고서 관리

여러분은 데이터 손실 방지를 위해 회사의 Microsoft 365 테넌트를 구성하는 임무를 맡은 Contoso Ltd.의 규정 준수 관리 주체인 Joni Sherman입니다. Contoso Ltd.는 미국 운전 지침을 제공하는 회사이며 중요한 고객 정보가 조직을 떠나지 않도록 해야 합니다. 새 규정 준수 담당자가 DLP 보고서를 검토하는 데 도움이 될 것이라는 통보를 받게 됩니다.

## 작업 1 - DLP 보고서에 대한 액세스 권한 부여

이 연습에서는 신임 준수 관리자 Megan Bowen에게 DLP 보고서 액세스 권한을 부여합니다. 비기술 사용자인 이 규정 준수 책임자는 보고서만 읽고 DLP 구성을 변경하지 않습니다.

1. 클라이언트 1 VM(LON-CL1)에 lon-cl1\admin** 계정으로 **로그인합니다.

1. **Microsoft Edge**에서 **https://compliance.microsoft.com**으로 이동한 다음, Microsoft Purview 포털에 **MOD 관리자** admin@WWLxZZZZZZ.onmicrosoft.com으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임). 관리 암호는 랩 호스팅 공급자가 제공해야 합니다.

1. 왼쪽 탐색 창에서 역할 및 범위를 확장**한** 다음 사용 권한을** 선택합니다**.

1. Microsoft Purview 솔루션 아래의 **사용 권한 페이지에서 역할을** 선택합니다**.** **** 

1. **Microsoft Purview 솔루션**에 대한 역할 그룹에서 Information Protection 분석가**의 필드를 **선택합니다.

1. **Information Protection 분석가** 플라이아웃 페이지에서 편집**을 선택합니다**.

1. **역할 그룹** 페이지의 구성원 편집 페이지에서 + 사용자** 선택을 선택합니다**.

1. 사용자 선택에서 **Megan Bowen**의 계정 옆에 있는 **검사 상자를 선택한 다음 선택 단추를 선택합니다****.**

1. **역할 그룹** 페이지의 구성원 편집 페이지로 돌아가서 Megan의 계정을 추가할지 확인한 다음, 다음**을 선택합니다**.

1. **역할 그룹 검토에서 저장**을** 선택합니다**.

1. **성공적으로 업데이트된 역할 그룹** 페이지에서 완료**를 선택합니다**.

Microsoft 365 규정 준수 포털에서 신임 준수 관리자에게 DLP 보고서 액세스 권한을 부여했습니다.

## 작업 2 - 활동 탐색기에서 DLP 데이터 검토

이 작업에서는 작업 1에서 부여한 DLP 보고서에 대한 액세스가 올바르게 적용되었는지 테스트합니다.

1. **lon-cl2\admin** 계정으로 클라이언트 2 VM(LON-CL2)에 로그인합니다.

1. **Microsoft Edge**에서 **https://compliance.microsoft.com**으로 이동한 다음, Microsoft Purview 포털에 **Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).

1. 왼쪽 탐색 창에서 데이터 손실 방지**를 위한 드롭다운을 **선택한 다음, 활동 탐색기를** 선택합니다**.

1. **활동 탐색기** 페이지에서 기본 제공 필터에 대한 **드롭다운을** 선택합니다.

1. 활동 필터를 **검색한 DLP 정책과 활동** 필터를 **검색한** DLP 정책 규칙을 탐색합니다.

Purview 포털에서 액세스 권한이 구성되었으며 신임 준수 관리자가 보고서를 볼 수 있음을 확인했습니다.

## 작업 3 - PowerShell을 사용하여 DLP 데이터 탐색

이 작업에서는 PowerShell을 통해 DLP 활동을 검토합니다.

1. 여전히 클라이언트 1 VM(LON-CL1)에 lon-cl1\admin** 계정으로 **로그인해야 합니다.

1. 관리자 권한 PowerShell 창을 엽니다. 이렇게 하려면 마우스 오른쪽 단추로 Windows 단추를 선택한 다음, **Windows PowerShell(관리자)** 을 선택합니다.

1. Information Protection PowerShell 세션에 연결하려면 다음을 입력합니다.

   ``` powershell
   Connect-IPPSSession
   ```

1. 선택 **+ 다른 계정을** 사용한 다음, Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com 계정**으로 로그인합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공하는 고유한 테넌트 ID임).

1. `Export-ActivityExplorerData` PowerShell cmdlet을 사용하여 PowerShell에서 활동 탐색기를 탐색합니다. 아래 스크립트는 가장 최근 주의 활동에 대한 그리드 보기를 표시하는 예제입니다.

   ``` powershell
   $StartTime = (Get-Date).AddDays(-7)
   $EndTime = (Get-Date).AddDays(1)
   $Results = Export-ActivityExplorerData -StartTime $StartTime -EndTime $EndTime -OutputFormat JSON
   ($Results.ResultData) | ConvertFrom-Json | select -ExpandProperty SyncRoot | ogv
   ```

1. 이전 랩에서 수집된 데이터를 탐색한 다음 그리드 보기 창을 닫습니다.

1. 아래 스크립트는 Filter1 매개 변수를 사용하여 가장 최근 주의 엔드포인트 활동을 표시하는 예제입니다.

   ``` powershell
   $StartTime = (Get-Date).AddDays(-7)
   $EndTime = (Get-Date).AddDays(1)
   $Results = Export-ActivityExplorerData -StartTime $StartTime -EndTime $EndTime -Filter1 @("Workload","Endpoint")-OutputFormat JSON
   ($Results.ResultData) | ConvertFrom-Json | select -ExpandProperty SyncRoot | ogv
   ```

1. 이전 랩에서 수집된 데이터를 탐색한 다음 그리드 보기 창을 닫습니다.

DLP 활동을 새로운 규정 준수 책임자인 Megan Bowen으로 성공적으로 검토했습니다.
