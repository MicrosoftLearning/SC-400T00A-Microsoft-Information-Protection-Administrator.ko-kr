---
lab:
  title: 연습 1 - 보존 정책 구성
  module: Module 3 - Implement Data Lifecycle and Records Management
---

## WWL 테넌트 - 사용 약관

강사 진행 교육 제공의 일부로 테넌트를 제공하는 경우, 강사 진행 교육에서 실습 랩을 지원하기 위해 테넌트를 사용할 수 있습니다.

테넌트를 실습 랩 외부에서 공유하거나 사용해서는 안 됩니다. 이 과정에서 사용되는 테넌트는 평가판 테넌트이며 클래스가 종료된 후 사용하거나 액세스할 수 없으며 확장판에서도 사용할 수 없습니다.

테넌트를 유료 구독으로 변환해서는 안 됩니다. 이 과정의 일부로 얻은 테넌트는 Microsoft Corporation의 재산으로 유지되며 언제든지 액세스 권한을 획득하고 다시 소유할 수 있는 권리를 보유합니다.

# 랩 3 - 연습 1 - 보존 정책 구성

이 랩에서는 텍사스주 Contoso Ltd.의 준수 관리자인 Joni Sherman입니다. 작업은 3년 후에 레코드를 삭제할 수 있도록 주 규정을 준수하도록 보존 정책을 구현하는 것입니다. 이러한 법적 요구 사항에 따라 데이터를 관리하고 보존하도록 조직 전체에서 다양한 보존 정책을 구성합니다.

**작업**:

1. 회사 전체 보존 정책 만들기
1. 특정 사용자 선택을 사용하여 Teams 보존 정책 만들기
1. PowerShell을 통해 보존 정책 만들기
1. 법률 및 소매 문서에 대한 적응형 보존 정책 만들기
1. 적응형 범위 정책 테스트

## 작업 1 - 회사 전체 보존 정책 만들기

이 작업에서는 주요 Microsoft 365 위치를 포괄하는 회사 전체 보존 정책을 설정하여 모든 항목이 주법에 따라 3년 동안 보존되도록 합니다.

1. 클라이언트 1 VM(SC-400-CL1)에 **SC-400-cl1\admin** 계정으로 로그인합니다.

1. **Microsoft Edge**에서 **`https://purview.microsoft.com`** 으로 이동한 다음, Microsoft Purview 포털에 **Joni Sherman** `JoniS@WWLxZZZZZZ.onmicrosoft.com`으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임). Joni의 암호는 이전 연습에서 설정되었습니다.

1. **솔루션**을 선택한 다음, **데이터 수명 주기 관리**를 선택합니다.

1. **데이터 수명 주기 관리** 페이지의 왼쪽 사이드바에서 **정책**을 확장한 다음 **보존 정책**을 선택합니다.

1. **보존 정책** 페이지에서 **+ 새 보존 정책**을 선택합니다.

1. **보존 정책 이름 지정** 페이지에서 다음을 입력합니다.

    - **이름**: `Company wide`
    - **설명**: `All locations except for teams`

1. **다음** 버튼을 선택합니다.  

1. **정책 범위** 페이지에서 **다음**을 선택합니다.

1. **만들 보존 정책 유형 선택** 페이지에서 **정적**을 선택한 후 **다음**을 선택합니다.

1. **이 정책을 적용할 위치 선택**에서 다음 위치를 선택합니다.

   - Exchange 사서함
   - SharePoint 클래식 및 커뮤니케이션 사이트
   - OneDrive 계정
   - Microsoft 365 그룹 사서함 및 사이트

1. **다음**을 선택합니다.

1. **콘텐츠를 보존할지, 삭제할지 또는 둘 다 수행할지 여부 결정** 페이지에서 보존 구성에 대해 이러한 값이 설정되었는지 확인합니다.

   - **특정 기간 동안 항목 보존**을 선택합니다.
   - **특정 기간 동안 항목 보존**의 드롭다운 목록에서 **사용자 지정**을 선택합니다.
   - 연도 필드를 **3**으로 변경합니다.
   - **보존 기간 시작 기준**: 마지막으로 항목을 수정한 시기
   - **보존 기간이 끝날 때**: 자동으로 항목 삭제

1. **다음**을 선택합니다.

1. **검토 후 완료** 페이지에서 **제출**을 선택합니다.

1. 정책이 생성되면 **보존 정책을 성공적으로 만들었습니다** 페이지에서 **완료**를 선택합니다.

마지막으로 수정한 날짜로부터 3년 동안 주요 Microsoft 365 위치에 항목을 보존하는 보존 정책을 만들었습니다. 테넌트에 이 정책을 적용하기까지 최대 24시간이 걸릴 수 있으므로 다음 단계로 진행해도 됩니다.

## 작업 2 – 특정 사용자 선택을 사용하여 Teams 보존 정책 만들기

다음으로, Microsoft Teams에 대한 보존 정책을 만들고 채널 메시지에 적용하고 사용자 채팅을 선택하여 다른 데이터와 별도로 보존을 관리합니다. 조직에서는 제한된 수의 사용자가 Teams 채팅에서 보존 기간을 설정해야 하도록 요청하기로 결정했습니다.

1. 여전히 클라이언트 1 VM(SC-LON-CL1)에는 **SC-400-cl1\admin** 계정으로, Microsoft Purview에는 **Joni Sherman**으로 로그인되어 있는 상태여야 합니다.

1. Microsoft Edge에서는 여전히 Microsoft Purview 포털의 **보존 정책** 페이지에 있어야 합니다. 그렇지 않은 경우 **`https://purview.microsoft.com`**(으)로 이동한 다음, **솔루션**을 선택하고 **데이터 수명 주기 관리**를 선택합니다. 왼쪽 사이드바에서 **정책** > **보존 정책**을 선택합니다.

1. **보존 정책** 페이지에서 **+ 새 보존 정책**을 선택합니다.

1. **보존 정책 이름 지정** 페이지에서 다음을 입력합니다.

   - **이름**: `Teams Retention`
   - **설명**: `Retention for Teams locations`

1. **다음**을 선택합니다.

1. **정책 범위** 페이지에서 **다음**을 선택합니다.

1. **만들 보존 정책 유형 선택** 페이지에서 **정적**을 선택한 후 **다음**을 선택합니다.

1. **정책을 적용할 위치 선택** 페이지에서 다음을 사용하도록 설정합니다.

   - Teams 채널 메시지
   - Teams 채팅 및 Copilot 상호 작용
   - 다른 모든 위치를 사용하지 않도록 설정합니다.

1. **Teams 채팅 및 Copilot 상호 작용** 위치에 대해 **모든 사용자** 아래에 있는 **편집** 텍스트 링크를 선택합니다.

1. **Teams 채팅 및 Copilot 상호 작용** 플라이아웃 패널에서 사용자를 추가합니다.

    - Adele Vance
    - Pradeep Gupta

    >**참고**: 해당 두 사용자를 추가하면 **Teams 채팅**에 **포함된** 설정이 *모든 팀*에서 *사용자 2명*으로 변경됩니다.

1. 플라이아웃 패널 하단에서 **완료**를 선택합니다.

1. **이 정책 적용 위치 선택** 페이지로 돌아가서 **다음**을 선택합니다.

1. **콘텐츠를 보존할지, 삭제할지 또는 둘 다 수행할지 여부 결정** 페이지에서 보존 구성에 대해 이러한 값이 설정되었는지 확인합니다.

   - **특정 기간 동안 항목 보존**을 선택합니다.
   - **특정 기간 동안 항목 보존**의 드롭다운 목록에서 **사용자 지정**을 선택합니다.
   - 연도 필드를 **3**으로 변경합니다.
   - **보존 기간 시작 기준**: 마지막으로 항목을 수정한 시기
   - **보존 기간이 끝날 때**: 자동으로 항목 삭제

1. **다음**을 선택합니다.

1. **검토 후 완료** 페이지에서 **제출**을 선택합니다.

1. 정책이 생성되면 **보존 정책을 성공적으로 만들었습니다** 페이지에서 **완료**를 선택합니다.

1. 브라우저 창을 닫습니다.

채널 메시지 및 특정 사용자 채팅이 3년 동안 보존되도록 Microsoft Teams에 대한 보존 정책을 성공적으로 구성했습니다.

## 작업 3 - PowerShell을 통해 보존 정책 만들기

이 작업에서는 PowerShell을 사용하여 동일한 보존 정책을 만들고 정책 설정 프로세스를 자동화하는 방법을 보여 줍니다.

1. 클라이언트 1 VM(SC-400-CL1)에 **SC-400-cl1\admin** 계정으로 로그인합니다.

1. 작업 표시줄에서 Windows 단추를 마우스 오른쪽 단추로 클릭하여 관리자 권한 PowerShell 창을 연 다음 **터미널(관리자)** 을 선택합니다. **사용자 계정 컨트롤** 대화 상자가 나타나면 **예**를 선택합니다.

1. 테넌트의 보안 및 규정 준수 센터에 연결하려면 **Connect-IPPSSession** cmdlet을 실행합니다.

    ```powershell
    Connect-IPPSSession
    ```

1. 로그인 대화 상자가 표시되면 **MOD 관리자**`admin@WWLxZZZZZZ.onmicrosoft.com`로 로그인합니다(여기서 ZZZZZZ는 랩 호스팅 제공업체에서 제공한 고유 테넌트 ID임). 관리자의 암호는 랩 호스팅 공급자가 제공합니다.

1. 팀을 제외한 모든 위치에 대해 첫 번째 보존 정책을 만들려면 **New-RetentionCompliancePolicy** cmdlet을 실행합니다.

    ```powershell
    New-RetentionCompliancePolicy -Name "Company Wide PS" -ExchangeLocation All -ModernGroupLocation All -SharePointLocation All -OneDriveLocation All
    ```

1. **New-RetentionComplianceRule** cmdlet을 실행하여 수정한 날짜를 기준으로 일 수를 단위로 하여 보존 기간을 3년으로 설정합니다.

    ```powershell
    New-RetentionComplianceRule -Name "Company Wide PS Rule" -Policy "Company Wide PS" -RetentionDuration 1095 -ExpirationDateOption ModificationAgeInDays -RetentionComplianceAction Keep
    ```

1. **New-RetentionCompliancePolicy** cmdlet을 실행하여 Teams 위치에 대한 두 번째 보존 정책을 만듭니다.

    ```powershell
    New-RetentionCompliancePolicy -Name "Teams Retention PS" -TeamsChannelLocation All -TeamsChatLocation "Adele Vance", "Pradeep Gupta"
    ```

1. **New-RetentionComplianceRule** cmdlet을 실행하여 일 수를 단위로 하여 보존 기간을 3년으로 설정합니다.

    ```powershell
    New-RetentionComplianceRule -Name "Teams Retention PS Rule" -Policy "Teams Retention PS" -RetentionDuration 1095 -RetentionComplianceAction Keep
    ```

1. 터미널 창을 닫습니다.

PowerShell을 사용하여 보존 정책을 성공적으로 만들어 Microsoft Purview 포털을 통해 설정된 정책을 미러링하였습니다.

<!------ Commenting out until tenant bug issues are resolved
## Task 4 – Create an adaptive retention policy for legal and retail documents

Now, you'll create an adaptive retention policy for the finance and legal departments, ensuring that all legal-related documents are retained for five years.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. Open Microsoft Edge and navigate to **`https://purview.microsoft.com`**. Verify you're still logged in with Joni's account, then select **Settings** from the left sidebar.

1. On the **Settings** page, expand **Roles and scopes** from the left sidebar, then select **Adaptive scopes**.

1. On the **Adaptive scopes** page select **+ Create scope**.

1. On the **Name your adaptive policy scope** page enter:

    - **Name**: `Legal Documents Retention`
    - **Description**: `Retention for legal related documents`

1. Select **Next**.

1. On the **Assign admin unit** page select **Next**.

1. On the **What type of scope do you want to create?** page select **Users** then select **Next**.

1. On the **Create the query to define users** page, in the **User attributes** section, ensure these values are selected for the user attribute configuration:

   - Select the **Attribute** dropdown then select **Department**
   - Leave the default **is equal to** value in the next field
   - Enter `Legal` as the **Value**

1. Add a second attribute by selecting **+ Add attribute** on the **Create the query to define users** page. In the new field under the one we just configured, configure these values:

   - Select the dropdown for the query operator and update it from And to **Or**
   - Select the **Attribute** dropdown then select **Department**
   - Leave the default **is equal to** value in the next field
   - Enter `Retail` as the **Value**

1. Select **Next**.

1. On the **Review and finish** page select **Submit**.

1. Once your adaptive scope is created select **Done** on the **Your scope was created** page.

1. Back on the **Adaptive scopes** page, select **Solutions** from the bottom of the left sidebar.

1. Select the tab for **Data Governance** from the top filter buttons.

1. Select the **Data Lifecycle Management** card.

1. On the **Data Lifecycle Management** page, expand **Policies** then select **Retention policies**.

1. On the **Retention policies** page, select **+ New retention policy**.

1. On the **Name your retention policy** page enter:

    - **Name**: `Legal Data Retention`
    - **Description**: `Retention of all documents within the legal and retail departments.`

1. Select **Next**.

1. On the **Policy Scope** page select **Next**.

1. On the **Choose the type of retention policy to create** page select **Adaptive** then select **Next**.

1. On the **Choose adaptive policy scopes and locations** page select **+ Add scopes**.

1. On the **Choose adaptive policy scopes** flyout panel select the checkbox for **Legal Documents Retention** then select **Add** at the bottom of the panel.

1. Back on the **Choose locations to apply the policy** enable:

    - Exchange mailboxes
    - OneDrive accounts
    - Leave all other locations disabled.

1. Select **Next**.

1. On the **Decide if you want to retain content, delete it, or both** page, ensure these values are set for the retention configuration:

   - Select **Retain items for a specific period**.
   - Under **Retain items for a specific period**, select **5 years** from the dropdown list
   - **Start the retention period based on**: When items were last modified
   - **At the end of the retention period**: Do nothing

1. Select **Next**.

1. On the **Review and finish** page select **Submit**.

1. Once your policy is created, select the **Done** button.

1. Once your policy is created select **Done** on the **You successfully created a retention policy** page.

You have successfully applied an adaptive scope to a retention policy, covering legal and retail department documents for five years.

## Task 5 – Test the adaptive scope policy

In this final task, you'll verify the users affected by the adaptive scope and test the new retention policy to ensure it is functioning as expected.

>**Note**: When you create and submit a retention policy, it can take up to seven days for the retention policy to be applied.

1. Open an elevated PowerShell window by right clicking the Windows button in the task bar, then select **Terminal (Admin)**. Select **Yes** if the **User Account Control** dialogue pops up.

1. Run the **Connect-IPPSSession** cmdlet to the Security & Compliance Center in your tenant:

    ```powershell
    Connect-IPPSSession
    ```

1. When prompted with a sign in dialog box, sign in with Joni Sherman's account, `JoniS@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's account was set in a previous exercise.

1. Run the **Get-RetentionCompliancePolicy** cmdlet to view all details of the adaptive scope policy:

    ```powershell
    Get-RetentionCompliancePolicy -Identity "Legal Data Retention" -DistributionDetail | Format-List
    ```

1. Review the results and search for these details:

    - **Enabled**: True
    - **Mode**: Enforce
    - **DistributionStatus**: Success

    ![Screenshot of the results of the Get-RetentionCompliancePolicy cmdlet.](../Media/results-getretentioncompliancepolicy.png)

You have verified the successful implementation of the adaptive scope retention policy, confirming that it is correctly applied and operational.
--->
