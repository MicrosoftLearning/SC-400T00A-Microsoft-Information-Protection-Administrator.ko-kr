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

이 연습에서는 Contoso Ltd.의 시스템 관리자인 Joni Sherman으로 작업을 수행하게 됩니다. 미국 텍사스 주 소재의 이 기업에서는 3년이 지나면 법에 저촉되는 사항 없이 레코드를 삭제할 수 있음이 명시된 주법 준수를 위해 보존 정책을 구현하려고 합니다.

이 법률 준수를 위해 조직에서는 조직의 모든 항목을 3년 동안 보존하는 보존 계획을 작성했습니다.

## 작업 1 - 회사 전체 보존 정책 만들기

이 연습에서는 회사 전체 보존 정책을 만들고 보존 기간을 적용한 다음 정책을 적용할 위치를 설정합니다.

1. 클라이언트 1 VM(LON-CL1)에 **lon-cl1\admin** 계정으로 로그인합니다.

1. **Microsoft Edge**에서 **`https://compliance.microsoft.com`** 으로 이동한 다음, Microsoft Purview 포털에 **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  Joni의 암호는 랩 호스팅 공급자가 제공합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **데이터 수명 주기 관리**를 확장한 다음 **Microsoft 365**를 선택합니다.

1. **데이터 수명 주기 관리** 페이지의 **보존 정책** 탭에서 **+ 새 보존 정책**을 선택합니다.

1. **보존 정책 이름 지정** 페이지의 **이름** 및 **설명**에 다음 정보를 각각 입력합니다.

    - **이름**: 회사 전체
    - **설명**: Teams를 제외한 모든 위치

1. **다음** 버튼을 선택합니다.  

1. **정책 범위** 페이지에서 **다음**을 선택합니다.

1. **만들 보존 정책 유형 선택** 영역에서 **정적**을 선택한 후 **다음**을 선택합니다.

1. **이 정책을 적용할 위치 선택**을 활성화합니다.

   - **Exchange 사서함**
   - **SharePoint 클래식 및 커뮤니케이션 사이트**
   - **OneDrive 계정**
   - **Microsoft 365 그룹 사서함 및 사이트**

1. **다음**을 선택합니다.

1. **콘텐츠를 보존할지, 삭제할지, 아니면 둘 다 수행할지 여부를 결정** 페이지의 **특정 기간 동안 항목 보존** 섹션에서 다음 정보를 입력합니다.

   - **특정 기간 동안 항목 보존**: 드롭다운 목록에서 **사용자 지정** 선택
   - 연도 필드를 **3**으로 변경합니다.
   - **보존 기간 시작 기준**: 마지막으로 항목을 수정한 시기
   - **보존 기간이 끝날 때**: 자동으로 항목 삭제

1. **다음**을 선택합니다.

1. **검토 후 완료** 페이지에서 **제출**을 선택합니다.

1. 정책이 만들어지면 **완료**를 선택합니다.

Exchange 이메일, Microsoft 365 그룹, OneDrive 및 SharePoint 사이트용 보존 정책을 만들었습니다. 이 보존 정책은 항목을 마지막으로 수정한 날짜로부터 3년 동안 해당 위치에서 항목을 보존합니다. 테넌트에 이 정책을 적용하기까지 최대 24시간이 걸릴 수 있으므로 다음 단계로 진행해도 됩니다.

## 작업 2 - 필터를 사용하여 위치 기반 보존 정책 만들기

이번에는 Teams 위치용 보존 정책을 만듭니다. Teams 채널에는 문서가 포함되어 있을 수 있으므로 모든 채널을 보존해야 합니다. 조직에서는 제한된 수의 사용자가 Teams 채팅에서 보존 기간을 설정해야 하도록 요청하기로 결정했습니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge**에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **`https://compliance.microsoft.com`** 으로 이동합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **데이터 수명 주기 관리**를 확장한 다음 **Microsoft 365**를 선택합니다.

1. **데이터 수명 주기 관리** 페이지의 **보존 정책** 탭에서 **+ 새 보존 정책**을 선택합니다.

1. **보존 정책 이름 지정** 페이지의 **이름** 및 **설명**에 다음 정보를 각각 입력합니다.

   - **이름**: Teams 보존
   - **설명**: Teams 위치용 보존

1. **다음**을 선택합니다.

1. **정책 범위** 페이지에서 **다음**을 선택합니다.

1. **생성할 보존 정책 유형 선택** 영역에서 **정적**을 선택하고 **다음**을 선택합니다.

1. **정책을 적용할 위치 선택** 페이지에서 다음을 사용하도록 설정합니다.

   - **Teams 채널 메시지**
   - **Teams 채팅**
   - 다른 모든 위치를 사용하지 않도록 설정합니다.

1. **Teams 채팅** 위치에 대해 **모든 사용자** 아래에 있는 **편집** 텍스트 링크를 선택합니다.

1. **Teams 채팅** 플라이아웃 페이지에서 사용자를 추가합니다.

    - Adele Vance
    - Pradeep Gupta

    >**참고**: 해당 두 사용자를 추가하면 **Teams 채팅**에 **포함된** 설정이 *모든 팀*에서 *사용자 2명*으로 변경됩니다.

1. **완료**를 선택한 후 **다음**을 선택합니다.

1. **콘텐츠를 보존할지, 삭제할지, 아니면 둘 다 수행할지 여부를 결정** 페이지의 **특정 기간 동안 항목 보존** 섹션에서 다음 정보를 입력합니다.

   - **특정 기간 동안 항목 보존**: 드롭다운 목록에서 **사용자 지정** 선택
   - 연도 필드를 **3**으로 변경합니다.
   - **보존 기간 시작 기준**: 마지막으로 항목을 수정한 시기
   - **보존 기간이 끝날 때**: 자동으로 항목 삭제

1. **다음**을 선택합니다.

1. **검토 후 완료** 페이지에서 **제출**을 선택합니다.

1. **보존 정책을 성공적으로 만들었습니다** 페이지에서 **완료**를 선택합니다.

Teams 위치용 보존 정책을 만들었습니다. 그리고 모든 Teams 채널 위치에 대해 보존 기간을 3년으로 설정했습니다. 또한 특정 사용자에게만 적용할 Teams 채팅 위치용 필터를 설정했습니다.

## 작업 3 - PowerShell을 통해 보존 정책 만들기

이번에는 PowerShell을 사용하여 동일한 보존 정책을 만듭니다.

1. 클라이언트 1 VM(LON-CL1)에 **lon-cl1\admin** 계정으로 로그인합니다.

1. 관리자 권한 PowerShell 창을 엽니다. 이렇게 하려면 마우스 오른쪽 단추로 Windows 단추를 선택한 다음 **Windows PowerShell(관리자)** 을 선택하고 사용자 계정 컨트롤 창이 표시되면 **예**를 선택합니다.

1. 다음 cmdlet을 사용하여 테넌트에서 보안 및 준수 센터에 연결합니다.

    ```powershell
    Connect-IPPSSession
    ```

1. 로그인 대화 상자가 표시되면 **MOD 관리자**로 로그인합니다. 로그인 ID로는 admin@WWLxZZZZZZ.onmicrosoft.com을 사용합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  관리자의 암호는 랩 호스팅 공급자가 제공합니다.

1. 다음 cmdlet을 실행하여 Teams를 제외한 모든 위치용으로 첫 번째 보존 정책을 만듭니다.

    ```powershell
    New-RetentionCompliancePolicy -Name "Company Wide PS" -ExchangeLocation All -ModernGroupLocation All -SharePointLocation All -OneDriveLocation All
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

<!-- ## Task 4 – Create Retention Policy with adaptive scope

In this exercise you will create a retention policy for the finance and legal department. The purpose of the policy is to comply with the law, retaining all legal related documents for 5 years. First you will create an adaptive scope including the legal and the retail department, then you will create a retention policy using this scope.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **`https://compliance.microsoft.com`**.

1. In the **Microsoft Purview** portal on the left navigation pane expand **Roles & scopes** then select **Adaptive scopes**.

1. On the **Adaptive scopes** page select **+ Create scope**.

1. On the **Name your adaptive policy scope** page input:

    - **Name**: Legal Documents Retention
    - **Description**: Retention for legal related documents

1. Select **Next**.

1. On the **Assign admin unit** page select **Next**.

1. On the **What type of scope do you want to create?** page select **Users** then select **Next**.

1. On the **Create the query to define users** page, under **User attributes** select the drop-down menu for **Attribute** then select **Department**.

1. Directly next to the attribute field select **is equal to** as the operator.

1. Input **Legal** in the **Value** field.

1. To add a second attribute, select **+ Add attribute** on the **Create the query to define users** page.

1. For the **Query operator**, **Attribute**, **Operator**, and **Value** input:

   - **Query operator**: Or
   - **Attribute**: Department
   - **Operator**: is equal to
   - **Value**: Retail

1. Ensure the checkboxes are selected next to each attribute then select **Next**.

1. On the **Review and finish** page select **Submit**.

1. On the **Your scope was created page** select **Done**.

1. In the **Microsoft Purview** portal, in the left navigation pane, expand **Data lifecycle management** then select **Microsoft 365**.

1. On the **Data lifecycle management** page select the **Retention policies** tab then select **+ New retention policy**.

1. On the **Name your retention policy** page input:

    - **Name**: Legal Data Retention
    - **Description**: Retention of all documents within the legal and retail departments.

1. Select **Next**.

1. On the **Policy Scope** page select **Next**.

1. On the **Choose the type of retention policy to create** page select **Adaptive** then select **Next**.

1. On the **Choose adaptive policy scopes and locations** page select **+ Add scopes**.

1. In the right flyout **Choose adaptive policy scopes** page select the checkbox for **Legal Documents Retention** then select the **Add** button.

1. Back on the **Choose locations to apply the policy** enable:

    - **Exchange mailboxes**
    - **OneDrive accounts**
    - Leave all other locations disabled.

1. Select **Next**.

1. On the **Decide if you want to retain content, delete it, or both** page, for the **Retain items for a specific period** section input:

    - **Retain items for a specific period**: 5 years
    - **Start the retention period based on**: When items were created
    - **At the end of the retention period**: Do nothing

1. Select **Next**.

1. On the **Review and finish** page select **Submit**.

1. Once your policy is created, select the **Done** button.

1. On the **You successfully created a retention policy** page select **Done**.

You have successfully applied an adaptive scope to a retention policy.

## Task 5 – Test adaptive scope policy

In this exercise you will verify the users affected by the adaptive scope and test the new adaptive retention policy.

>**Note**: When you create and submit a retention policy, it can take up to seven days for the retention policy to be applied.

1. To review the details of the adaptive scope retention policy, logged into  **lon-cl1\admin**, open a PowerShell window by selecting the Windows button with the right mouse button and then select Windows PowerShell.

1. Connect to the Security & Compliance Center in your tenant with the following cmdlet:

    ```powershell
    Connect-IPPSSession
    ```

1. If prompted with a sign in dialog box, sign in with Joni Sherman's account,  JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.

1. Run the following cmdlet to view all details of the adaptive scope policy:

    ```powershell
    Get-RetentionCompliancePolicy -Identity "Legal Data Retention"     -DistributionDetail | Format-List
    ```

1. Review the details. Certain parameters should have following statuses:

    - **Enabled**: True
    - **Mode**: Enforce
    - **DistributionStatus**: Success

You have verified the success of your adaptive scope.-->
