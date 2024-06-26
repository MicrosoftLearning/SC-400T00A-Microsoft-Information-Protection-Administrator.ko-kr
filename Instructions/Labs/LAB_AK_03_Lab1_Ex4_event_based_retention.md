---
lab:
  title: 연습 4 - 이벤트 기반 보존 구성
  module: Module 3 - Implement Data Lifecycle and Records Management
---

# 랩 3 - 연습 4 - 이벤트 기반 보존 구성

이 연습에서는 Contoso Ltd.의 준수 관리자인 Joni Sherman으로 작업을 수행하게 됩니다. 조직은 텍사스에 있으며 특정 프로젝트에 속한 콘텐츠를 종료 후 5년 동안 보존하는 보존 정책을 구현하려고 합니다.

## 작업 1 - 이벤트 기반 보존 레이블 및 이벤트 유형 만들기

이 단계에서는 보존 레이블 및 이벤트 유형을 만듭니다. 이벤트 유형은 보존 기간을 트리거합니다. 특정 이벤트 유형에 대해 보존 레이블이 적용된 모든 콘텐츠에는 레이블의 보존 작업이 적용됩니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**(JoniS@WWLxZZZZZZ.onmicrosoft.com)으로 로그인되어 있는 상태여야 합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  Joni의 암호는 랩 호스팅 공급자가 제공합니다.

1. **Microsoft Edge**에서 **`https://compliance.microsoft.com`** 으로 이동하고 Microsoft Purview 포털에 **Joni Sherman**으로 로그인합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **데이터 수명 주기 관리**를 확장한 다음 **Microsoft 365**를 선택합니다.

1. **데이터 수명 주기 관리** 페이지에서 **레이블** 탭을 선택한 다음 **+ 레이블 만들기** 단추를 선택합니다.

1. **보존 레이블 이름 지정**에서 다음 정보를 입력합니다.

    - **이름**: Project Asset
    - **사용자를 위한 설명**: 이 레이블을 프로젝트 문서에 할당하여 5년 동안 보관되도록 합니다.
    - **관리자를 위한 설명**: 이벤트 기반 보존을 위한 Project Asset입니다.

1. **다음** 버튼을 선택합니다.

1. **레이블 설정 정의** 페이지에서 **영구 또는 특정 기간 동안 항목 보관** 설정을 사용하도록 설정한 후 **다음**을 선택합니다.

1. **보존 기간 정의** 페이지에서 **항목 보존 기간** _5년_을 선택합니다.

1. **보존 기간 시작 기준** 드롭다운에서 **+ 새 이벤트 유형 만들기**를 선택합니다. 그러면 이벤트 기반 레이블 마법사가 시작됩니다.

1. 오른쪽의 **이벤트 유형 이름 지정** 플라이아웃에서 다음을 입력합니다.

    - **이름**: Project Closure
    - **설명**: 프로젝트가 닫히면 이 이벤트가 트리거됩니다.

1. **다음**을 선택합니다.

1. **요약** 페이지를 검토한 다음 **제출**을 선택합니다.

1. **이벤트 유형이 만들어짐**에서 **완료**를 선택합니다.

1. **보존 기간 정의**로 돌아와 **보존 기간 시작 기준** 아래에서 새로 만들어진 **제품 마감** 이벤트 유형을 선택한 후 **다음**을 선택합니다.

1. **보존 기간 이후 수행되는 작업 선택** 페이지에서 **자동으로 항목 삭제**를 선택한 다음, **다음**을 선택합니다.

1. **검토 및 완료** 페이지에서 **레이블 만들기**를 선택합니다.  

1. **보존 레이블이 만들어짐** 페이지에서 **아무 작업도 하지 않음**을 선택하고 **완료**를 선택합니다.

레이블을 성공적으로 만들었으며 레이블을 게시해야 합니다.

## 작업 2 - 이벤트 기반 보존 레이블 게시

이전 작업에 이어 이제 Project Asset 보존 레이블을 게시하여 게시된 레이블을 사용자가 SharePoint 문서의 문서에 적용할 수 있도록 합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge**에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **`https://compliance.microsoft.com`** 으로 이동합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **데이터 수명 주기 관리**를 확장한 다음 **Microsoft 365**를 선택합니다.

1. **데이터 수명 주기 관리** 페이지에서 **레이블** 탭을 선택합니다.

1. **프로젝트 자산** 레이블을 선택한 다음 **레이블 게시** 단추를 선택합니다.

1. **게시할 레이블 선택** 페이지에서 **다음**을 선택합니다.

1. **정책 범위** 페이지에서 **다음**을 선택합니다.

1. **만들 보존 정책 유형 선택** 페이지에서 **정적**을 선택한 후 **다음**을 선택합니다.

1. **레이블을 게시할 위치 선택** 페이지에서 **특정 위치를 선택하겠습니다.** 를 선택하여 위치 옵션을 표시합니다.

1. 다음 위치만 **켜기**로 토글되었는지 확인합니다.

    - **SharePoint 클래식 및 커뮤니케이션 사이트**
    - **OneDrive 계정**

    **Exchange 사서함** 및 **Microsoft 365 그룹 사서함 및 사이트**는 **끄기**로 토글되어야 합니다.

1. **다음** 버튼을 선택합니다.

1. **정책 이름 지정**에서 다음 정보를 입력합니다.

    - **이름**: Project Asset 보존 레이블
    - **설명**: Project Assets 보존 레이블, 보존 기간 5년, SharePoint 사이트 위치.

1. **다음** 버튼을 선택합니다.

1. **완료** 페이지를 검토한 다음 **제출**을 선택합니다.

1. **보존 레이블이 게시됨** 페이지에서 **완료**를 선택합니다.

Project Assets의 보존 레이블을 사용자에게 성공적으로 게시했습니다.

## 작업 3 - 레이블 적용 및 자산 ID 추가

레이블이 게시되면 사용자는 레이블을 적용하고 프로젝트의 올바른 Asset ID를 레이블을 지정할 문서에 할당해야 합니다. 이 작업에서는 이 기능을 테스트합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge**에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **`https://compliance.microsoft.com`** 으로 이동합니다.

1. 왼쪽 위 모서리에서 9개의 점을 선택하고 **앱** 아래에서 **SharePoint**를 선택합니다.

1. 위쪽의 검색 창에서 _브랜드_를 검색한 다음 검색 결과에서 **브랜드** SharePoint 페이지를 선택합니다.

1. 왼쪽 탐색 창에서 **문서**를 선택합니다.

1. **문서** 페이지에서 왼쪽의 확인란을 선택하여 **Customer Product Survey.xlsx**를 선택합니다. 가로 줄임표(**...**) 단추, **세부 정보**를 차례로 선택합니다.

1. 오른쪽 메뉴의 **속성**에서 **레이블 적용**을 선택한 다음, **Project Asset** 레이블을 선택합니다.

    >**참고**: 보존 레이블을 게시하는 데 시간이 걸릴 수 있으므로 즉시 사용 가능한 옵션이 없을 수 있습니다.

1. 새로 나타난 **자산 ID**에서 **NewProductLaunch**를 입력하고 오른쪽 위 모서리에서 **X**를 선택하여 오른쪽 메뉴를 닫습니다.

문서에 레이블 및 자산 ID를 할당했습니다. 자산 ID NewProductLaunch에 대한 Project Closure 이벤트가 트리거되면 5년의 보존 기간이 활성화됩니다.

## 작업 4 - 특정 이벤트 만들기

이벤트가 발생하면 레이블이 지정된 콘텐츠가 필수 보존 기간을 시작하도록 트리거해야 합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**(JoniS@WWLxZZZZZZ.onmicrosoft.com)으로 로그인되어 있는 상태여야 합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  Joni의 암호는 랩 호스팅 공급자가 제공합니다.

1. **Microsoft Edge**에서 **`https://compliance.microsoft.com`** 으로 이동하고 Microsoft Purview 포털에 **Joni Sherman**으로 로그인합니다.

1. **Microsoft Purview** 포털의 왼쪽 탐색 창에서 **레코드 관리**를 선택한 다음 **이벤트** 탭을 선택합니다.

1. **+ 만들기**를 선택합니다.

1. **이벤트 이름 지정** 페이지에서 다음 정보를 설정합니다.

    - **이름**: 신제품 출시 마감
    - **설명**: Project Asset 레이블과 AssetID NewProductLaunch가 있는 자산은 보존 기간을 입력합니다.

1. **다음**을 선택합니다.

1. **이벤트 설정** 페이지에서 **이벤트 유형 사용**을 선택한 다음, **이벤트 유형 선택**을 선택합니다.

1. **이벤트 유형 선택** 페이지에서 **Project Closure**를 선택한 다음, **추가**를 선택합니다.

1. **다음**을 선택합니다.

1. **이벤트 설정** 페이지에서 **SharePoint 및 OneDrive의 항목에 대한 자산 ID**를 **NewProductLaunch**로 설정합니다.

1. **이 이벤트는 언제 발생했나요?** 에 대해 오늘 날짜를 선택한 후 **다음**을 선택합니다.

1. **완료** 페이지를 검토한 다음 **제출**을 선택합니다.

1. **이벤트가 만들어짐** 페이지에서 **완료**를 선택합니다.

이벤트를 성공적으로 트리거하고 Project Asset 레이블 및 NewProductLaunch의 자산 ID를 사용하여 모든 문서에 대한 보존 기간을 시작했습니다.

## 작업 5 - 이벤트 트리거의 결과 관찰

지정한 보존 기간이 시작되었는지 확인하려면 파일을 삭제해야 합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 **Joni Sherman**으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge**에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 해당 탭이 열려 있으면 탭을 선택하고 다음 단계를 진행합니다. 닫았다면 새 탭에서 **`https://compliance.microsoft.com`** 으로 이동합니다.

1. 왼쪽 위 모서리에서 9개의 점을 선택하고 **앱** 아래에서 **SharePoint**를 선택합니다.

1. 위쪽의 검색 창에서 _브랜드_를 검색한 다음 검색 결과에서 **브랜드** SharePoint 페이지를 선택합니다.

1. 왼쪽 탐색 창에서 **문서**를 선택합니다.

1. **문서** 페이지에서 왼쪽의 확인란을 선택하여 **Customer Product Survey.xlsx**를 선택합니다. 가로 줄임표(**...**)를 선택합니다.

1. 바로 가기 메뉴에서 **삭제**를 선택하고 결과를 확인합니다.

문서의 보존 기간이 시작되었음을 확인했습니다. 문서를 여전히 삭제할 수 있는 경우 이벤트의 동기화 기간이 완료되지 않았으며 보존 정책 트리거는 아직 진행 중입니다. 다른 보존 레이블과 마찬가지로 이 프로세스를 완료하는 데 최대 7일이 걸릴 수 있습니다.
