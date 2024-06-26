---
lab:
  title: 연습 2 - 보존 레이블 구현
  module: Module 3 - Implement Data Lifecycle and Records Management
---

# 랩 3 - 연습 2 - 보존 레이블 구현

이 연습에서는 Contoso Ltd.의 시스템 관리자인 Joni Sherman으로 작업을 수행하게 됩니다. 영국 서드베리 소재의 조직에는 금융 문서를 보존할 법적 의무가 있습니다.

이 의무를 준수하기 위해 경리부에서 VAT(부가가치세) 환급용 문서와 지원 문서 및 신용 카드 영수증에 보존 레이블을 설정하는 보존 계획을 작성했습니다.

## 작업 1 - 보존 레이블 만들기

이 작업에서는 VAT 환급 정보가 포함된 문서와 이메일에 할당할 수 있는 보존 레이블과 신용 카드 영수증에 적용할 수 있는 보존 레이블을 만듭니다.

1. 클라이언트 1 VM(LON-CL1)에 **lon-cl1\admin** 계정으로 로그인합니다.

1. **Microsoft Edge**에서 **`https://compliance.microsoft.com`** 으로 이동하고 Microsoft Purview 포털에 **Joni Sherman**으로 로그인합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **데이터 수명 주기 관리**를 확장한 다음 **Microsoft 365**를 선택합니다.

1. **데이터 수명 주기 관리** 페이지에서 **레이블** 탭을 선택한 다음 **+ 레이블 만들기**를 선택합니다.

1. **보존 레이블 이름 지정** 페이지에서 다음을 입력합니다.

    - **이름**: VAT 환급 및 지원 문서
    - **사용자를 위한 설명**: 법률에 따라 7년 동안 보존할 수 있도록 VAT 문서에 이 레이블을 할당하세요.
    - **관리자를 위한 설명**: 7년 동안 보존해야 하는 VAT 환급 정보입니다.

1. **다음**을 선택합니다.

1. **레이블 설정 정의** 페이지에서 **영구 또는 특정 기간 동안 항목 보관**을 선택한 후 **다음**을 선택합니다.

1. **기간 정의**에서 다음을 입력합니다.

    - **기간은 얼마인가요?**: 7년
    - **기간은 언제 시작해야 하나요?**: 항목이 생성된 시점

1. **다음**을 선택합니다.

1. **보존 기간 이후에 수행되는 작업 선택** 페이지에서 **보존 설정 비활성화**를 선택한 후 **다음**을 선택합니다.

1. **검토 및 완료** 페이지에서 **레이블 만들기**를 선택합니다.

1. **보존 레이블이 만들어짐** 페이지에서 **아무 작업도 하지 않음** 옵션을 선택한 다음, **완료**를 선택합니다. 레이블은 연습의 뒷부분에 게시됩니다.

1. **데이터 수명 주기 관리** 페이지에서 **+ 레이블 만들기**를 선택합니다.

1. **보존 레이블 이름 지정**에서 다음을 입력합니다.

    - **이름**: 신용 카드 영수증
    - **사용자를 위한 설명**: 3년 동안 보존할 수 있도록 신용 카드 영수증에 자동 적용되는 레이블입니다.
    - **관리자를 위한 설명**: 3년 동안 보존해야 하는 신용 카드 영수증용 자동 적용 보존 레이블입니다.

1. **다음**을 선택합니다.

1. **레이블 설정 정의** 페이지에서 **영구 또는 특정 기간 동안 항목 보관**을 선택한 후 **다음**을 선택합니다.

1. **기간 정의** 페이지에서 다음을 입력합니다.

    - **항목 보존 기간**: 드롭다운 목록을 선택하고 **사용자 지정 **을 선택합니다. 연도에 3을 입력합니다.
    - **보존 기간 시작 기준**: 항목이 만들어졌을 때

1. **다음**을 선택합니다.

1. **보존 기간 이후에 수행되는 작업 선택** 페이지에서 **보존 설정 비활성화**를 선택한 후 **다음**을 선택합니다.

1. **검토 및 완료** 페이지에서 **레이블 만들기**를 선택합니다.

1. **보존 레이블이 만들어짐** 페이지에서 **아무 작업도 하지 않음**을 선택하고 **완료**를 선택합니다.

보존 기간이 7년인 VAT 환급 문서용 보존 레이블과 보존 기간이 3년인 신용 카드 영수증용 보존 레이블을 만들었습니다.

## 작업 2 - 보존 레이블 게시

이 작업에서는 작업 1에서 만든 VAT 환급 문서 보존 레이블을 게시합니다. 그러면 경리부 사용자들이 Exchange 이메일에 있는 문서 및 SharePoint 문서에 게시된 레이블을 적용할 수 있습니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge**에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **`https://compliance.microsoft.com`** 으로 이동합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **데이터 수명 주기 관리**를 확장한 다음 **Microsoft 365**를 선택합니다.

1. **데이터 수명 주기 관리** 페이지에서 **레이블** 탭을 선택합니다.

1. 작업 1에서 만든 **VAT 환급 및 지원 문서** 레이블을 선택합니다.

1. **레이블 게시** 아이콘 단추(연필 옆)를 선택합니다.

1. **게시할 레이블 선택** 페이지에서 **다음**을 선택합니다.

1. **정책 범위** 페이지에서 **다음**을 선택합니다.

1. **만들 보존 정책 유형 선택** 페이지에서 **정적**을 선택한 후 **다음**을 선택합니다.

1. **레이블을 게시할 위치 선택** 페이지에서 **특정 위치를 선택하겠습니다.** 를 선택하고 다음을 사용하도록 설정합니다.

    - **Exchange 사서함**
    - **SharePoint 클래식 및 커뮤니케이션 사이트**
    - **OneDrive 계정**
    - **Microsoft 365 그룹 사서함 및 사이트** 사용 안 함

1. **다음**을 선택합니다.

1. **정책 이름 지정**에서 다음을 입력합니다.

    - **이름**: VAT 환급 및 지원 문서 보존 레이블
    - **설명**: VAT 환급 및 지원 문서 보존 레이블입니다. 보존 기간은 3년이며 적용 대상은 Exchange 이메일 및 SharePoint 사이트 위치입니다.

1. **다음**을 선택합니다.

1. **완료** 페이지에서 **제출**을 선택합니다.  

1. **보존 레이블이 게시됨** 페이지에서 **완료**를 선택합니다.

VAT 환급 및 지원 문서용 보존 레이블을 게시했습니다.

## 작업 3 - 자동 적용 보존 레이블 게시

이 작업에서도 작업 1에 이어 정보가 보존되도록 신용 카드 영수증 보존 레이블을 자동 적용합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge**에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **`https://compliance.microsoft.com`** 으로 이동합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **정책**을 선택하고 **데이터**에서 **보존**을 선택합니다.

1. **데이터 수명 주기 관리** 페이지에서 **레이블** 탭을 선택합니다.

1. 작업 1에서 만든 **신용 카드 영수증** 레이블을 선택합니다.

1. **레이블 자동 적용** 아이콘 단추(번개 + 톱니바퀴)를 선택합니다.

1. **시작** 페이지에서 **이름** 및 **설명**에 다음 정보를 입력합니다.

    - **이름**: 신용 카드 영수증 자동 적용
    - **설명**: 신용 카드 영수증 자동 적용 보존 레이블입니다. 모든 위치에서 보존 기간은 3년입니다.

1. **다음** 버튼을 선택합니다.

1. **이 레이블을 적용할 콘텐츠 유형 선택** 페이지에서 **중요한 정보가 포함된 콘텐츠에 레이블 적용**을 선택한 후 **다음**을 선택합니다.

1. **중요한 정보가 포함된 콘텐츠** 페이지에서 **금융** 범주를 선택합니다.

1. 그러면 금융 템플릿이 템플릿 아래에 표시됩니다. 아래로 스크롤하여 **영국 금융 데이터** 템플릿을 선택한 후 **다음**을 선택합니다.

1. **중요한 정보가 포함된 콘텐츠 정의** 페이지에서 **다음**을 선택합니다.

1. **정책 범위** 페이지에서 **다음**을 선택합니다.

1. **만들 보존 정책 유형 선택** 페이지에서 **정적** 항목을 선택한 후 **다음**을 선택합니다.

1. **정책을 적용할 위치 선택** 페이지에서

    - **Exchange 사서함**
    - **SharePoint 클래식 및 커뮤니케이션 사이트**
    - **OneDrive 계정**
    - **Microsoft 365 그룹 사서함 및 사이트**

1. **다음**을 선택합니다.

1. **자동 적용할 레이블 선택** 페이지에서 **다음**을 선택합니다.

1. **정책을 테스트할지 또는 실행할지 결정**에서 **정책 켜기**를 선택한 후 **다음**을 선택합니다.

1. **검토 후 완료** 페이지에서 **제출**을 선택합니다.  정책이 만들어지면 **완료**를 선택합니다.

1. 오른쪽 위 모서리에서 Joni의 이미지를 선택하고 **로그아웃**을 선택하여 그녀의 계정에서 로그아웃합니다.

자동 적용할 보존 레이블을 게시했습니다. 앞으로 7일 동안 신용 카드 정보가 포함된 모든 문서에 방금 게시한 신용 카드 영수증 레이블이 자동 적용됩니다. 이러한 항목에는 보존 기간 3년이 적용됩니다.

## 작업 4 - Outlook 이메일에서 보존 레이블 사용

이 작업에서는 Outlook 전자 메일에 보존 레이블을 할당합니다.

1. 클라이언트 1 VM(LON-CL1)에 **lon-cl1\admin** 계정으로 로그인합니다.

1. **Microsoft Edge**에서 **`https://outlook.office.com/`** 으로 이동하고 **Megan Bowen**의 계정으로 로그인합니다.

1. Megan의 받은 편지함에서 마우스 오른쪽 단추로는 첫 번째 이메일을 선택한 다음, **고급 작업 > 정책 할당 > VAT 환급 및 지원 문서**를 선택합니다. 새로 만든 레이블을 사용할 수 없는 경우 이 연습을 위해 **1개월 삭제**를 선택합니다.

    >**참고**: 게시된 보존 레이블이 Exchange Online에 표시되려면 7일이 걸릴 수 있습니다. 사서함에는 데이터 10MB가 포함되어 있어야 합니다.

1. **Outlook** 창을 열어 둔 상태로 유지합니다.

Outlook 전자 메일에 보존 레이블을 적용했습니다.

## 작업 5 - Outlook 폴더용 보존 레이블 사용

이 작업에서는 Outlook 폴더에 보존 레이블을 할당합니다.

1. 클라이언트 1 VM(LON-CL1)에 **lon-cl1\admin** 계정으로 로그인되어 있는 상태여야 합니다. **Outlook**이 실행되고 있는 Microsoft Edge 브라우저 창은 계속 열려 있어야 하며 여전히 **Megan Bowen**로 로그인되어 있어야 합니다.

1. 왼쪽 창에서 **받은 편지함**을 선택하고 마우스 오른쪽 단추를 클릭합니다.

1. **새 하위 폴더 만들기**를 선택합니다.

1. 빈 필드가 있는 커서가 새 파일 이름으로 끝나는 것처럼 표시되어야 합니다. 이 필드에 _VAT 환급_을 입력한 다음 **저장**을 선택합니다.

1. 왼쪽 패널에서 새로 만든 **VAT 환급** 폴더를 마우스 오른쪽 단추로 클릭하고 **정책 할당 > VAT 환급 및 지원 문서**를 선택합니다. 새로 만든 레이블을 사용할 수 없는 경우 이 연습을 위해 **5년 삭제**를 선택합니다.

    >참고: 게시된 보존 레이블이 Exchange Online에 표시되려면 7일이 걸릴 수 있습니다. 사서함에는 데이터 10MB가 포함되어 있어야 합니다.

1. 오른쪽 위에서 Megan의 사진 선택하고 **로그아웃**을 선택하여 그녀의 계정에서 로그아웃합니다.

Outlook 폴더에 보존 레이블을 적용했습니다. 이 하위 작업에서 선택한 설정에 따라 이 폴더 내의 모든 전자 메일에 기본 보존 레이블이 할당됩니다.

Outlook 폴더에 보존 레이블을 적용했습니다.

## 작업 6 - SharePoint에서 보존 레이블 사용

이 작업에서는 SharePoint 문서 라이브러리의 문서에 보존 레이블을 적용합니다.

1. 클라이언트 1 VM(LON-CL1)에 **lon-cl1\admin** 계정으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge**에서 **`https://www.office.com`** 으로 이동한 다음 Microsoft 365에 **Joni Sherman**으로 로그인합니다.

1. Microsoft O365 방문 페이지에서 왼쪽 위 모서리의 앱 시작 관리자 아이콘(점 9개로 표시된 아이콘)을 선택하고 하위 메뉴에서 **SharePoint**를 선택합니다.
1. 메시지가 표시되면 **SharePoint 시작 페이지** 창을 닫습니다.

1. SharePoint 방문 페이지에서 _커뮤니케이션 사이트_를 검색한 다음, 검색 결과에서 **커뮤니케이션 사이트**를 선택합니다.

1. 위쪽 탐색 모음에서 **문서** 탭을 선택합니다.

1. **CAS** 폴더를 선택합니다.

1. CAS 폴더 내에서 **Blog Post preview.docx** 문서를 강조 표시합니다(선택은 하지 않음).

1. 강조 표시된 문서의 경우 가로 줄임표(**...**) 단추, **기타 > 규정 준수 세부 정보**를 차례로 선택합니다.

1. 문서에 대한 **규정 준수 세부 정보**가 표시된 새 창이 열립니다. **레이블 상태**의 경우 **없음**을 선택하여 **레이블 적용** 창을 엽니다.

1. 옵션을 사용할 수 있는 경우 **레이블 적용**을 **VAT 환급 및 증빙 문서(7년 동안 보관)** 로 설정한 다음 **저장**을 선택합니다. 보존 레이블이 게시되려면 시간이 다소 걸릴 수도 있으므로 이 옵션을 즉시 사용하지는 못할 수도 있습니다. 이 옵션을 사용할 수 없어도 다음 작업을 계속 진행하세요. 나중에 언제든 이 작업으로 돌아와서 다시 시도해 보세요.

SharePoint의 문서에 보존 레이블을 적용했습니다.

## 작업 7 - OneDrive에서 보존 레이블 사용

이 작업에서는 OneDrive의 문서에 보존 레이블을 적용합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge**에서 **`https://www.office.com`** 으로 이동한 다음 Microsoft 365에 **Joni Sherman**으로 로그인합니다.

1. Microsoft 365 방문 페이지에서 왼쪽 위 모서리의 앱 시작 관리자 아이콘(점 9개로 표시된 아이콘)을 선택하고 하위 메뉴에서 **OneDrive**를 선택합니다.

1. 왼쪽 탐색 창에서 **내 파일**을 선택한 다음 **Contractor Legal Info.docx** 왼쪽에 있는 확인란을 선택합니다.

1. 강조 표시된 문서의 경우 가로 줄임표(**...**) 단추, **세부 정보**를 차례로 선택합니다.

1. 오른쪽 플라이아웃 페이지의 **속성** 아래에 **레이블 적용** 옵션이 표시됩니다. **레이블 선택**을 선택하여 드롭다운을 확장한 다음, 사용 가능한 경우 **VAT 환급 및 지원 문서**를 선택합니다.

    >**참고**: 보존 레이블이 게시되려면 시간이 다소 걸릴 수도 있으므로 이 옵션을 즉시 사용하지는 못할 수도 있습니다. 이 옵션을 사용할 수 없어도 다음 작업을 계속 진행하세요. 나중에 언제든 이 작업으로 돌아와서 다시 시도해 보세요.

OneDrive의 문서에 보존 레이블을 적용했습니다.
