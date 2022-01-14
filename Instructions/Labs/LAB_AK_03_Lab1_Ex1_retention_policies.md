# 랩 3 - 연습 1 - 보존 정책 구성

이 연습에서는 Contoso Ltd.의 시스템 관리자인 Joni Sherman으로 작업을 수행하게 됩니다. Joni가 소속된 미국 텍사스 주 소재의 기업인 Contoso Ltd.에서는 3년이 지나면 법에 저촉되는 사항 없이 레코드를 삭제할 수 있음이 명시된 주법 준수를 위해 보존 정책을 구현하려고 합니다. 

이 법률 준수를 위해 조직에서는 조직의 모든 항목을 3년 동안 보존하는 보존 계획을 작성했습니다.


### 작업 1 - 회사 전체 보존 정책 만들기

이 연습에서는 회사 전체 보존 정책을 만들고 보존 기간을 적용한 다음 정책을 적용할 위치를 설정합니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 VM(LON-CL1)에 로그인합니다.

2. **Microsoft Edge**에서 **https://compliance.microsoft.com** 으로 이동한 다음 **Joni Sherman**으로 Microsoft 365 규정 준수 포털에 로그인합니다. 로그인 ID로는 JoniS@WWLxZZZZZZ.onmicrosoft.com을 사용합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  Joni의 암호는 랩 호스팅 공급자가 제공합니다.

3. **Microsoft 365 규정 준수** 포털의 왼쪽 탐색 창에서 **정책**을 선택하고 **데이터** 아래에서 **보존**을 선택합니다.

4. **정보 거버넌스** 페이지의 **보존** 탭에서 **+ 새 보존 정책**을 선택합니다.

5. **보존 정책 이름 지정** 페이지의 **이름** 및 **설명**에 다음 정보를 각각 입력합니다.

	- 이름: 회사 전체
	- 설명: Teams를 제외한 모든 위치

6. **다음** 단추를 선택합니다.  

7. **만들 보존 정책의 유형 선택** 영역에서 **정적**을 선택하고 **다음**을 선택합니다.

8. **정책을 적용할 위치 선택** 영역에서 Exchange 전자 메일, SharePoint 사이트, OneDrive 계정 및 Microsoft 365 그룹이 선택되어 있는지 확인하고 **다음**을 선택합니다.

9. **콘텐츠를 보존할지, 삭제할지, 아니면 둘 다 수행할지 여부를 결정** 페이지의 **특정 기간 동안 항목 보존** 섹션에서 다음 정보를 입력합니다.

	- 특정 기간 동안 항목 보존: 드롭다운 목록에서 **사용자 지정**을 선택합니다.
	- 연도 필드를 **3**으로 변경
	- **보존 기간 시작 기준**: 마지막으로 항목을 수정한 시기

10. **다음** 단추를 선택합니다.

11. **검토 후 완료** 페이지에서 **제출** 단추를 선택합니다.

12. 정책이 만들어지면 **완료** 단추를 선택합니다.

Exchange 이메일, Microsoft 365 그룹, OneDrive 및 SharePoint 사이트용 보존 정책을 만들었습니다. 이 보존 정책은 항목을 마지막으로 수정한 날짜로부터 3년 동안 해당 위치에서 항목을 보존합니다. 테넌트에 이 정책을 적용하기까지 최대 24시간이 걸릴 수 있으므로 다음 단계로 진행해도 됩니다.

### 작업 2 - 필터를 사용하여 위치 기반 보존 정책 만들기

이번에는 Teams 위치용 보존 정책을 만듭니다. Teams 채널에는 문서가 포함되어 있을 수 있으므로 모든 채널을 보존해야 합니다. 조직에서는 제한된 수의 사용자가 Teams 채팅에서 보존 기간을 설정해야 하도록 요청하기로 결정했습니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**으로 로그인되어 있는 상태여야 합니다. 

2. 그리고 **Microsoft Edge**에는 Microsoft 365 규정 준수 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 해당 탭을 닫았다면 새 탭에서 **https://compliance.microsoft.com** 으로 이동합니다.

3. **Microsoft 365 규정 준수** 포털의 왼쪽 탐색 창에서 **정책**을 선택하고 **데이터** 아래에서 **보존**을 선택합니다.

4. **정보 거버넌스** 페이지의 **보존 정책** 탭에서 **+ 새 보존 정책**을 선택합니다.

5. **보존 정책 이름 지정** 페이지의 **이름** 및 **설명**에 다음 정보를 각각 입력합니다.

	- **이름**: Teams 보존
	- **설명**: Teams 위치용 보존

6. **다음** 단추를 선택합니다.

7. **만들 보존 정책의 유형 선택** 영역에서 **정적**을 선택하고 **다음**을 선택합니다.

8. **정책을 적용할 위치 선택** 페이지에서 다음 설정을 입력합니다.

	- **Teams 채널 메시지** 위치 - **상태**: 켜짐 
	- **Teams 채팅 위치** - **상태**: 켜짐
	- 다른 위치는 모두 **꺼짐**으로 설정합니다.

9. **Teams 채팅** 위치의 경우 **모든 사용자** 아래에서 **편집** 텍스트 링크를 선택합니다.

10. **Teams 채팅** 패널에서 다음 사용자를 추가합니다. 
    - Adele Vance
    - Pradeep Gupta

    참고: 해당 두 사용자를 추가하면 Teams 채팅에 포함된 설정이 "모든 팀"에서 추가한 두 사용자만으로 변경됩니다.

11. **완료** 단추를 선택합니다.

12. 위치 페이지에 다음 알림이 표시됩니다. **2명의 사용자**가 추가되었습니다.

13. **다음** 단추를 선택합니다.

14. **콘텐츠를 보존할지, 삭제할지, 아니면 둘 다 수행할지 여부를 결정** 페이지의 **특정 기간 동안 항목 보존** 섹션에서 다음 정보를 입력합니다.

	- 특정 기간 동안 항목 보존: 드롭다운 목록에서 **사용자 지정**을 선택합니다.
	- 연도 필드를 **3**으로 변경
	- **보존 기간 시작 기준**: 마지막으로 항목을 수정한 시기


15. **다음** 단추를 선택합니다.

16. **검토 후 완료** 페이지에서 **제출** 단추를 선택합니다.

17. 정책이 만들어지면 **완료**를 선택합니다.

Teams 위치용 보존 정책을 만들었습니다. 그리고 모든 Teams 채널 위치에 대해 보존 기간을 3년으로 설정했습니다. 또한 특정 사용자에게만 적용할 Teams 채팅 위치용 필터를 설정했습니다.

### 작업 3 - PowerShell을 통해 보존 정책 만들기

이번에는 PowerShell을 사용하여 동일한 보존 정책을 만듭니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 VM(LON-CL1)에 로그인합니다.

2. 관리자 권한 PowerShell 창을 엽니다. 이렇게 하려면 마우스 오른쪽 단추로 Windows 단추를 선택한 다음 **Windows PowerShell(관리자)** 을 선택하고 사용자 계정 컨트롤 창이 표시되면 **예**를 선택합니다.

3. 다음 cmdlet을 사용하여 테넌트에서 보안 및 준수 센터에 연결합니다.

    `Connect-IPPSSession`

4. 로그인 대화 상자가 표시되면 **MOD 관리자**로 로그인합니다. 로그인 ID로는 admin@WWLxZZZZZZ.onmicrosoft.com을 사용합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  관리자의 암호는 랩 호스팅 공급자가 제공합니다.

5. 다음 cmdlet을 실행하여 Teams를 제외한 모든 위치용으로 첫 번째 보존 정책을 만듭니다.

    `New-RetentionCompliancePolicy -Name "Company Wide PS" -ExchangeLocation All -ModernGroupLocation All -PublicFolderLocation All -SharePointLocation All -OneDriveLocation All`

6. 다음 cmdlet을 실행하여 보존 기간을 설정합니다. 단위로는 수정한 날짜 기준 기간(일)을 사용합니다.
	
    `New-RetentionComplianceRule -Name "Company Wide PS Rule" -Policy "Company Wide PS" -RetentionDuration 1095 -ExpirationDateOption ModificationAgeInDays -RetentionComplianceAction Keep`

7. 다음 cmdlet을 실행하여 Teams 위치용으로 두 번째 보존 정책을 만듭니다.

    `New-RetentionCompliancePolicy -Name "Teams Retention PS" -TeamsChannelLocation All -TeamsChatLocation "Adele Vance", "Pradeep Gupta"`

8. 다음 cmdlet을 실행하여 보존 기간을 설정합니다. 단위로는 기간(일)을 사용합니다.

    `New-RetentionComplianceRule -Name "Teams Retention PS Rule" -Policy "Teams Retention PS" -RetentionDuration 1095 -RetentionComplianceAction Keep`

PowerShell을 통해 보존 기간이 3년인 보존 정책을 만들었습니다.

# 랩 3 - 연습 2로 넘어가세요.
