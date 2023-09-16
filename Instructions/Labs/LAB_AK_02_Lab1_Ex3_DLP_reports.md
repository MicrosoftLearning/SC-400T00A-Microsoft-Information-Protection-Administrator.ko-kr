---
lab:
  title: 연습 3 - DLP 보고서 관리
  module: Module 2 - Implement Data Loss Prevention
---

# 랩 2 - 연습 3 - DLP 보고서 관리

Contoso Ltd.의 준수 관리자인 Joni Sherman이 회사 Microsoft 365 테넌트에서 데이터 손실 방지 기능을 구성하는 작업을 맡게 되었습니다. Contoso Ltd.는 미국의 운전학원입니다. 학원에 등록하는 중요한 고객 정보가 조직 외부로 유출되지 않도록 해야 합니다. 신임 준수 관리자가 DLP 보고서 검토를 지원할 예정이라고 합니다.

## 작업 1 - DLP 보고서 액세스 허용

이 연습에서는 신임 준수 관리자 Megan Bowen에게 DLP 보고서 액세스 권한을 부여합니다. 이 준수 관리자는 일반 사용자이므로 보고서 내용만 확인하고 DLP 구성을 변경하지는 않을 예정입니다.

1. 클라이언트 1 VM(LON-CL1) **에 lon-cl1\admin** 계정으로 로그인합니다.

1. **Microsoft Edge**에서 **https://compliance.microsoft.com** 으로 이동한 다음, Microsoft Purview 포털에 **MOD 관리자** admin@WWLxZZZZZZ.onmicrosoft.com 으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임). 관리자의 암호는 랩 호스팅 공급자가 제공합니다.

1. 왼쪽 탐색 창에서 **역할 & 범위를** 확장한 다음 **권한을** 선택합니다.

1. **Microsoft Purview 솔루션** 아래**의 권한** 페이지에서 **역할을** 선택합니다.

1. **Microsoft Purview 솔루션의 역할 그룹** 페이지에서 **Information Protection 분석가**의 필드를 선택합니다.

1. **Information Protection 분석가** 플라이아웃 페이지에서 **편집**을 선택합니다.

1. **역할 그룹의 구성원 편집** 페이지에서 **+ 사용자 선택을 선택합니다**.

1. **사용자 선택**에서 **Megan Bowen**의 계정 옆에 있는 검사 상자를 선택한 다음 **, 선택 단추를 선택합니다**.

1. **역할 그룹의 구성원 편집** 페이지로 돌아가서 Megan의 계정을 추가할지 확인한 다음, **다음**을 선택합니다.

1. **역할 그룹 검토 및 완료에서** **저장을** 선택합니다.

1. **역할 그룹을 업데이트했습니다**. 페이지에서 **완료**를 선택합니다.

Microsoft 365 규정 준수 포털에서 신임 준수 관리자에게 DLP 보고서 액세스 권한을 부여했습니다.

## 작업 2 - 활동 탐색기에서 DLP 데이터 검토

이 작업에서는 작업 1에서 부여한 DLP 보고서 액세스 권한이 올바르게 적용되었는지를 테스트합니다.

1. **lon-cl2\admin** 계정으로 클라이언트 2 VM(LON-CL2)에 로그인합니다.

1. **Microsoft Edge**에서 **https://compliance.microsoft.com** 으로 이동한 다음, Microsoft Purview 포털에 **Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com 으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).

1. 왼쪽 탐색 창에서 **데이터 손실 방지** 드롭다운을 선택한 다음 **, 활동 탐색기를** 선택합니다.

1. **활동 탐색기** 페이지에서 **기본 제공 필터**에 대한 드롭다운을 선택합니다.

1. 활동 필터를 **검색한 DLP 정책 및 활동** 필터를 **검색한 DLP 정책 규칙을** 탐색합니다.

Purview 포털에서 액세스 권한이 구성되었으며 신임 준수 관리자가 보고서를 볼 수 있음을 확인했습니다.

## 작업 3 - PowerShell을 사용하여 DLP 데이터 탐색

이 작업에서는 PowerShell을 통해 DLP 활동을 검토합니다.

1. 여전히 클라이언트 1 VM(LON-CL1)에 **lon-cl1\admin** 계정으로 로그인해야 합니다.

1. 관리자 권한 PowerShell 창을 엽니다. 이렇게 하려면 마우스 오른쪽 단추로 Windows 단추를 선택한 다음, **Windows PowerShell(관리자)** 을 선택합니다.

1. 다음을 입력하여 Information Protection PowerShell 세션에 연결합니다.

   ``` powershell
   Connect-IPPSSession
   ```

1. **+ 다른 계정 사용을** 선택한 다음 **, Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com 계정으로 로그인합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공하는 고유한 테넌트 ID임).

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

새 규정 준수 책임자인 Megan Bowen으로 DLP 활동을 성공적으로 검토했습니다.
