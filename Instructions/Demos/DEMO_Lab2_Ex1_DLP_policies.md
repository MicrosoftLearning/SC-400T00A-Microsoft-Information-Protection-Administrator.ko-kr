---
lab:
  title: 세션 2 - Microsoft Purview의 데이터 손실 방지
  module: Learning Objective - Implement Data Loss Prevention in Microsoft Purview
---
## WWL 테넌트 - 사용 약관

강사 주도 교육 제공의 일부로 테넌트를 제공하는 경우, 강사 주도 교육에서 실습 랩을 지원하기 위해 테넌트를 사용할 수 있습니다.

테넌트를 실습 랩 외부에서 공유하거나 사용해서는 안 됩니다. 이 과정에서 사용되는 테넌트는 평가판 테넌트이며 클래스가 종료된 후 사용하거나 액세스할 수 없으며 확장판에서도 사용할 수 없습니다.

테넌트를 유료 구독으로 변환해서는 안 됩니다. 이 과정의 일부로 얻은 테넌트는 Microsoft Corporation의 재산으로 유지되며 언제든지 액세스 권한을 획득하고 다시 소유할 수 있는 권리를 보유합니다.

# 데모 랩 3 - DLP 정책 관리

여러분은 데이터 손실 방지를 위해 회사의 Microsoft 365 테넌트를 구성하는 임무를 맡은 Contoso Ltd.의 새로 고용된 규정 준수 관리istrator인 Joni Sherman입니다. Contoso Ltd.는 미국 운전 지침을 제공하는 회사이며 중요한 고객 정보가 조직을 떠나지 않도록 해야 합니다.

## 작업 1 – 테스트 모드에서 DLP 정책 만들기

이 연습에서는 Microsoft Purview 포털에서 중요한 데이터를 사용자들이 공유하지 못하도록 하는 데이터 손실 방지 정책을 만듭니다. 사용자가 만든 DLP 정책은 신용 카드 정보가 포함된 콘텐츠를 공유하려는 경우 사용자에게 알리고 이 정보를 전송하기 위한 근거를 제공할 수 있도록 합니다. 차단 동작이 사용자에게 아직 영향을 미치지 않기 때문에 정책이 테스트 모드에서 구현됩니다.

1. 클라이언트 1 VM(LON-CL1)에 lon-cl1\admin** 계정으로 **로그인합니다.

1. Microsoft Edge에서 **MOD 관리** Microsoft Purview 포털로 **이동하여** **https://compliance.microsoft.com로그인합니다. admin@WWLxZZZZZZ.onmicrosoft.com 로그인합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공하는 고유한 테넌트 ID임).** 관리 암호는 랩 호스팅 공급자가 제공해야 합니다.

1. **로그인 상태를 유지하시겠습니까?** 대화 상자가 나타나면 **다시 표시하지 않음** 확인란을 선택한 다음, **아니요**를 선택합니다.

1. Microsoft Purview** 포털의 **왼쪽 탐색 창에서 데이터 손실 방지**를 확장**한 다음 정책을** 선택합니다**.

1. **정책** 페이지에서 +정책** 만들기를 선택하여 **새 데이터 손실 방지 정책을 만들기 위한 마법사를 시작합니다.

1. **템플릿으로 시작 또는 사용자 지정 정책** 만들기 페이지에서 아래로 스크롤하여 **범주**에서 **사용자 지정**을 선택하고 **템플릿**에서 **사용자 지정 정책**을 선택합니다. 기본적으로 두 옵션을 모두 선택해야 합니다. **다음**을 선택합니다.

1. **이름에 DLP 정책** 페이지에서 다음을 입력합니다.

   - **이름**: 신용 카드 DLP 정책
   - **설명**: 크레딧 카드 번호가 공유되지 않도록 보호

1. **다음**을 선택합니다.

1. **관리 단위 할당(미리 보기)** 페이지에서 다음**을 선택합니다**.

1. **정책을 적용할 위치 선택** 페이지에서 **Teams 채팅 및 채널 메시지** 옵션만 사용하도록 설정하고 **다음**을 선택합니다.

1. **정책 설정 정의** 페이지에서 **고급 DLP 규칙 만들기 또는 사용자 지정**을 선택하고 **다음**을 선택합니다.

1. **고급 DLP 규칙 사용자 지정 페이지에서 + 규칙** 만들기**를 선택합니다**.

1. **규칙** 플라이아웃 만들기 페이지의 이름** 필드에 크레딧 카드 정보를_ **입력_합니다.

1. 조건** 아래에서 + 조건** 추가를 선택한 다음 드롭다운 메뉴에서 콘텐츠 포함**을 선택합니다**.****

1. 새 **콘텐츠 포함** 영역에서 **추가**를 선택하고 드롭다운 메뉴에서 **중요한 정보 유형**을 선택합니다.

1. **중요한 정보 유형** 페이지에서 **신용 카드 번호**를 선택하고 **추가**를 선택합니다.

1. **규칙** 만들기 페이지에서 + 조건** 추가를 선택하고 **** 드롭다운 메뉴에서 Microsoft 365**에서 콘텐츠를 공유합니다.

1. Microsoft 365** 섹션에서 공유되는 새 **콘텐츠에서 조직** 내 사용자와만 옵션을 선택합니다**.

1. **규칙** 만들기 페이지에서 + 작업** 추가를 선택합니다**. 조건이 **충족되면 작업을 사용하여 콘텐츠를 보호합니다.** 는 Microsoft 365 위치에서 액세스 제한 또는 콘텐츠 암호화를 확장하고 **모든 사용자** 차단을 선택합니다 **.**

1. **규칙** 만들기 페이지의 **사용자 알림** 섹션에서 켜**기로 전환하여 **사용자 알림을 사용하도록 설정합니다.

1. 검사 상자를 선택하여 정책 팁**으로 Office 365 서비스에서 사용자에게 알릴 수 있습니다**.

1. 사용자 재정의**에서 **M365 서비스에서 재정의를 허용하려면 **검사 상자를 선택합니다. Exchange, SharePoint, OneDrive 및 Teams의 사용자가 정책 제한을 재정의할 수 있습니다.**

1. 재정의할 비즈니스 근거를 요구하려면 **검사 확인란을** 선택합니다.

1. 인**시던트 보고서** 섹션**의 관리자 경고 및 보고서** 드롭다운에서 이 심각도 수준 사용에서 낮음(Low **)을 선택합니다**.

1. 규칙 만들기 페이지에서 저장**을 선택한 **다음을 선택합니다****.** ** 

1. 정책 모드** 페이지에서 먼저** 테스트를 선택하고 **테스트 모드**에서 정책 팁 표시를 선택합니다**.**

1. **정책 검토 및 만들기** 페이지에서 설정을 검토한 다음 제출을 선택합니다 **.**

1. **새 정책 생성** 페이지에서 완료**를 선택합니다**.

이제 Microsoft Teams 채팅 및 채널에서 신용 카드 번호를 검색하고 사용자가 정책을 재정의할 비즈니스 근거를 제공할 수 있도록 하는 DLP 정책을 만들었습니다.

## 작업 2 - DLP 정책 수정

이 작업에서는 이전 단계에서 만든 기존 DLP 정책이 메일에서도 신용 카드 정보를 검사한 다음, 사용자가 해당 콘텐츠를 메일로 공유하려고 하면 알림을 표시하도록 수정합니다.

1. 여전히 클라이언트 1 VM(LON-CL1)에 lon-cl1\admin 계정으로 **로그인해야 하며, MOD 관리** Microsoft 365**에 로그인해야** 합니다.

1. **Microsoft Edge**에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 그렇다면 선택하고 다음 단계로 진행합니다. 닫았다면 새 탭에서 **https://compliance.microsoft.com**으로 이동합니다.

1. Microsoft Purview** 포털의 **왼쪽 탐색 창에서 데이터 손실 방지**를 확장**한 다음 정책을** 선택합니다**.

1. **정책** 페이지에서 최근에 만든 **신용 카드 DLP 정책** 옆에 있는 검사 상자를 선택한 다음 정책 편집(연필 아이콘)을 선택하여 **정책** 마법사를 엽니다.

1. **DLP 정책** 이름 페이지에서 다음**을 선택합니다**.

1. **관리 단위 할당(미리 보기)** 페이지에서 다음**을 선택합니다**.

1. **정책** 페이지를 적용할 위치 선택 페이지에서 Exchange 전자 메일** 옵션을 사용하도록 설정한 **다음 정책 검토에 도달**하고 페이지를 만들** 때까지 다음**을 선택합니다**.

1. 제출**을 선택하여 **정책에 변경한 내용을 적용합니다.

1. 정책이 업데이트되면 완료**를 선택합니다**.

이제 기존 DLP 정책을 수정하고 콘텐츠를 검색하는 위치를 변경했습니다.

## 작업 3 - 테스트 모드에서 정책 활성화

이 작업에서는 테스트 모드에서 만든 신용 카드 정보 DLP 정책을 활성화하여 보호 작업을 적용합니다.

1. 여전히 클라이언트 1 VM(LON-CL1)에 lon-cl1\admin 계정으로 **로그인해야 하며, MOD 관리** Microsoft 365**에 로그인해야** 합니다.

1. **Microsoft Edge**에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 그렇다면 선택하고 다음 단계로 진행합니다. 닫았다면 새 탭에서 **https://compliance.microsoft.com**으로 이동합니다.

1. Microsoft Purview** 포털의 **왼쪽 탐색 창에서 데이터 손실 방지**를 확장**한 다음 정책을** 선택합니다**.

1. **정책** 페이지에서 신용 카드 DLP 정책** 옆에 있는 **검사 상자를 선택하고 정책** 편집(연필)을 선택하여 **정책 마법사를 엽니다.

1. **정책 모드** 페이지에 도달할 때까지 다음**을 **선택하고 바로** 켜기를 선택합니다**.

1. 정책 검토 및 **만들기에서 제출**을 선택합니다****.

1. **정책 업데이트** 페이지에서 완료**를 선택합니다**.

DLP 정책을 성공적으로 활성화했습니다. 정책이 신용 카드 정보를 공유하려는 시도를 감지하면 이제 시도를 차단하고 사용자가 차단 작업을 재정의할 비즈니스 근거를 제공할 수 있습니다.

## 작업 4 - 정책 우선 순위 수정

두 개의 DLP 정책을 만든 후에는 덜 제한적인 정책보다 더 제한적인 정책이 더 높은 우선 순위로 처리되도록 해야 합니다. 이러한 이유로 EmployeeID DLP 정책을 더 높은 우선 순위로 이동하려고 합니다.

1. 여전히 클라이언트 1 VM(LON-CL1)에 lon-cl1\admin 계정으로 **로그인해야 하며, MOD 관리** Microsoft 365**에 로그인해야** 합니다.

1. **Microsoft Edge**에는 Microsoft Purview 포털 탭이 계속 열려 있어야 합니다. 그렇다면 선택하고 다음 단계로 진행합니다. 닫았다면 새 탭에서 **https://compliance.microsoft.com**으로 이동합니다.

1. Microsoft Purview** 포털의 **왼쪽 탐색 창에서 데이터 손실 방지**를 확장**한 다음 정책을** 선택합니다**.

1. 정책에서 **EmployeeID DLP 정책** 옆에 있는 **세 개의 세로 점을 선택하여 작업** 선택을 열고 **맨 위로** 이동을 선택합니다**.**

1. **데이터 손실 방지** 창에서 **새로 고침**을 선택하고 정책 표의 **순서** 열에서 우선 순위를 검토합니다.

DLP 정책의 우선 순위를 수정했습니다. 두 정책이 동일한 콘텐츠와 일치하는 경우 우선 순위가 높은 정책의 작업이 적용됩니다.
