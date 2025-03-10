---
lab:
  title: 연습 2 - 내부 위험 관리 구성
  module: Module 5 - Manage insider and privacy risk in Microsoft 365
---

# 연습 5 - 내부 위험 관리 구성

사용자는 Contoso Ltd.의 준수 관리자인 Joni Sherman입니다. 사용자의 역할에는 규정 준수를 보장하고 조직 내 중요한 정보를 보호하는 것이 포함됩니다. 최근 Contoso Ltd.에서는 잠재적으로 회사의 평판에 해를 끼치거나 데이터 보안을 손상시키거나 법적 문제로 이어질 수 있는 내부 위험을 적극적으로 해결해야 할 필요성을 인식했습니다.

내부 위험을 효과적으로 관리하려면 잠재적인 내부자 위협을 식별, 분석 및 대응하도록 설계된 포괄적인 솔루션인 Microsoft Purview 내부 위험 관리를 구현합니다.

## 작업 1: 내부 위험 관리 역할 할당

이 연습에서는 Joni에게 내부 위험 관리 역할을 할당하여 Microsoft Purview 포털에서 내부 위험 작업을 수행할 수 있는 액세스 권한을 부여합니다.

1. 클라이언트 1 VM(LON-CL1) **lon-cl1\admin** 계정에 계속 로그인되어 있어야 합니다.

1. Microsoft Edge에서 Microsoft Purview 규정 준수 포털 **https://compliance.microsoft.com**으로 이동하여 **MOD 관리자** admin@WWLxZZZZZZ.onmicrosoft.com(으)로 로그인합니다. 관리자의 암호는 랩 호스팅 공급자가 제공합니다.

1. **역할 및 범위**로 이동한 다음 드롭다운에서 **권한**을 선택합니다.

1. **권한** 페이지의 **Microsoft Purview 솔루션**에서 **역할**을 선택합니다.

1. **Microsoft Purview 솔루션 역할 그룹** 페이지에서 **내부 위험 관리**를 선택합니다.

1. 오른쪽의 **내부 위험 관리** 플라이아웃 페이지에서 **편집**을 선택합니다.

1. **역할 그룹의 멤버 편집** 페이지에서 **+ 사용자 선택**을 선택합니다.

1. **사용자 선택** 페이지에서 Joni Sherman 옆의 확인란을 선택한 다음 **선택** 단추를 선택합니다.

1. **역할 그룹 멤버 편집** 페이지에서 **다음**을 선택합니다.

1. **역할 그룹 검토 및 완료** 페이지에서 **저장**을 선택합니다.

1. **역할 그룹이 업데이트됨** 페이지에서 **완료**를 선택합니다.

1. **MOD 관리자** 계정에서 로그아웃하고 모든 브라우저 창을 닫습니다.

Joni Sherman에게 내부 위험 관리 역할을 성공적으로 할당하여 Microsoft Purview 포털에서 내부 위험 작업을 수행할 수 있는 액세스 권한을 부여했습니다.

## 작업 2: 내부 위험 설정 구성

이 작업에서는 Microsoft Purview 포털에서 내부 위험 관리 설정을 사용자 지정합니다. 이를 통해 Joni Sherman은 조직 내에서 잠재적인 내부 위험을 효과적으로 관리하고 중요한 정보의 보안을 보장할 수 있습니다.

1. **Microsoft Edge**에서 Microsoft Purview 규정 준수 포털인 **https://compliance.microsoft.com**으로 이동하여 JoniS@WWLxZZZZZZ.onmicrosoft.com(으)로 로그인합니다. Joni의 암호는 랩 호스팅 공급자가 제공합니다.

1. 왼쪽 탐색 모음에서 **내부 위험 관리**를 선택합니다.

1. **설정** 오른쪽 상단에 있는 기어 아이콘을 선택합니다. ![기어 아이콘](../Media/gearicon.png)
1. 설정을 살펴봅니다.

    - **개인 정보**: 경고 및 사례에 사용자 이름 또는 익명화된 버전 표시를 선택할 수 있습니다.
    - **정책 표시기**: 특정 위험 표시기를 사용하여 정책 템플릿을 구성하는 작업이 포함됩니다.
    - **검색 그룹(미리 보기)**: 조직의 특정 사용자 집합에 대한 위험 표시기 사용자 지정
    - **정책 적용 기간**: 이벤트 및 작업을 기반으로 정책 일치로 트리거되는 검토 기간을 정의합니다.
    - **지능형 검색**: 경고 볼륨을 제어하고, 위험 점수에서 특정 엔터티를 제외하고, Microsoft Defender 경고 필터링을 허용합니다.
    - **경고 내보내기**: Office 365 관리 작업 API를 사용하여 위험 경고 정보를 SIEM 및 SOAR 솔루션으로 내보냅니다.
    - **우선 순위 사용자 그룹**: 면밀한 검사와 더 중요한 위험 점수를 매기기 위해 고위험 사용자를 결정합니다.
    - **우선 순위 물리적 자산(미리 보기)**: 작업과 사용자 이벤트를 연관시키는 우선 순위 물리적 자산에 대한 액세스를 식별하고 모니터링합니다.
    - **Power Automate 흐름(미리 보기)**: Microsoft Power Automate 흐름을 사용하여 내부 위험 관리 작업을 자동화합니다.
    - **Microsoft Teams(미리 보기)**: 내부 위험 관리 사례에 대한 협업을 위해 Microsoft Teams를 사용하도록 설정합니다.
    - **분석**: 정책 만들기를 안내하는 정책을 구성하지 않고 잠재적인 내부 위험을 평가합니다.
    - **관리자 알림**: 내부 위험 관리 역할 그룹에 이메일 알림을 자동으로 보냅니다.
    - **인라인 경고 사용자 지정**: 경고 대시보드에서 직접 정책 튜닝 및 임계값을 조정할 수 있습니다.

1. **일반** 아래의 내부 위험 관리 설정 표시줄에서 **개인 정보**를 선택합니다.

1. **익명화된 사용자 이름 표시 안 함**을 선택합니다.

1. 이 설정을 저장하려면 **저장**을 선택합니다.

1. **일반** 아래의 내부 위험 관리 설정 표시줄에서 **정책 표시기**를 선택합니다.

1. **정책 표시기** 설정 창의 **Office 표시기**에서 **모두 선택** 확인란을 선택합니다.

1. 아래로 스크롤하여 **저장**을 선택합니다.

1. **일반** 아래의 내부 위험 관리 설정 표시줄에서 **우선 순위 사용자 그룹**을 선택합니다.

1. **+ 우선 순위 사용자 그룹 만들기**를 선택하여 **새 우선 사용자 그룹 마법사**를 엽니다.

1. **우선 순위 사용자 그룹 이름 및 설명** 페이지에서 다음을 입력합니다.

    - **이름**: 재무 팀
    - **설명**: 재무 운영, 예산 책정, 보고를 관리하는 팀 멤버

1. **다음**을 선택합니다.

1. **멤버 선택** 페이지에서 **+ 멤버 선택**을 선택합니다.

1. **멤버 선택** 창에서 **Lynne Robbins**, **Debra Berger** 및 **Megan Bowen** 옆의 확인란을 선택한 다음 **추가**를 선택하여 3명의 멤버를 추가합니다.

1. **멤버 선택** 페이지에서 **다음**을 선택합니다.

1. **이 우선 순위 그룹의 사용자와 관련된 데이터를 볼 수 있는 사용자 선택**에서 **+ 사용자 및 역할 그룹 선택**을 선택합니다.

1. **사용자 및 역할 그룹 선택** 페이지에서 **내부 위험 관리** 옆의 확인란을 선택하여 Microsoft Purview에서 내부 위험 관리 역할을 맡은 모든 멤버를 추가하고 **추가**를 선택합니다.

1. **이 우선 순위 그룹의 사용자와 관련된 데이터를 볼 수 있는 사용자 선택**에서 **다음**을 선택합니다.

1. **검토** 페이지에서 **제출**을 선택합니다.

1. **우선 순위 사용자 그룹 만들기** 페이지에서 **완료**를 선택합니다. 그러면 내부 위험 관리 설정 페이지로 돌아갑니다.

1. **내부 위험 관리**를 선택하여 기본 내부 위험 관리 페이지로 돌아갑니다.

내부 위험 관리 설정을 성공적으로 사용자 지정했습니다. 이제 Joni Sherman은 내부 위험을 적극적으로 식별하고 완화하여 Microsoft Purview 포털에서 귀중한 데이터를 보호하는 데 필요한 도구와 기능을 갖추고 있습니다.

## 작업 3: 내부 위험 정책 만들기

이 작업에서는 조직 내의 중요한 재무 데이터 액세스를 모니터링하고 보호하기 위해 Microsoft Purview에서 '재무 데이터 보호'라는 정책을 구성합니다.

1. Microsoft Purview에서는 여전히 Joni로 로그인되어 있어야 합니다.

1. 왼쪽 탐색 모음에서 **내부 위험 관리**를 선택합니다.

1. 상단 탐색 모음에서 **정책** 탭을 선택한 다음 **+ 정책 만들기**를 선택합니다.

1. **정책 템플릿 선택** 페이지에서 **데이터 유출**을 선택한 후 **다음**을 선택합니다.

1. **정책 이름 지정 페이지**에서 다음을 입력합니다.

    - **이름**: 재무 데이터 보호
    - **설명**: 중요한 재무 데이터 액세스 모니터링

1. **다음**을 선택합니다.

1. **사용자 및 그룹 선택** 페이지에서 **모든 사용자 및 그룹 포함**을 선택된 상태로 두고 **다음**을 선택합니다.

1. **콘텐츠 페이지의 우선 순위 결정**에서 **중요한 정보 유형**만 선택한 상태로 두고 **다음**을 선택합니다.

1. **우선 순위를 지정할 중요한 정보 유형** 페이지에서 **+ 중요한 정보 유형 추가 또는 편집**을 선택합니다.

1. **중요한 정보 유형 추가 또는 편집** 창에서 _은행_을 검색하고 **미국 옆의 확인란을 선택합니다. 은행 계좌 번호** 및 **IBAN(국가별 은행 계좌 번호)** 옆의 확인란을 선택합니다. 그런 다음 _크레딧_을 검색하고 **신용 카드 번호** 옆의 확인란을 선택한 다음 **추가**를 선택하여 3가지 중요한 정보 유형을 추가합니다.

1. **우선 순위를 지정할 중요한 정보 유형**으로 돌아가서 **다음**을 선택합니다.

1. **우선 순위 콘텐츠가 있는 작업만 점수 매길지 여부 결정** 페이지에서 **모든 작업에 대한 경고 가져오기**를 선택한 후 **다음**을 선택합니다.

1. **이 정책의 트리거** 페이지에서 **사용자가 반출 작업을 수행함**을 선택합니다.

1. **이 정책을 트리거할 작업 선택**에서 다음을 선택합니다.

   - **SharePoint에서 콘텐츠 다운로드**
   - **조직 외부의 수신자에게 첨부 파일이 포함된 이메일 보내기**
   - **조직 외부의 사람들과 SharePoint 파일 공유**
   - **Microsoft 365 위치에서 반출 다운로드**

    >[!note] **참고**: 정책 트리거를 선택할 수 없는 경우 표시기 켜기에 대한 팁이 있을 수 있습니다. 이 옵션을 사용할 수 있는 경우 **표시기 켜기**를 선택합니다. **표시기를 선택하여 켜기** 팝업에서 **Office 표시기**에 대해 **모두 선택** 옆의 확인란을 클릭한 다음 **저장**을 선택합니다.

1. **다음**을 선택합니다.

1. **이 정책에 대한 트리거 임계값** 페이지에서 **기본 임계값 사용(권장)** 을 선택한 후 **다음**을 선택합니다.

1. **표시기** 페이지에서 **실제 액세스 표시기** 드롭다운을 선택하고 **중요한 자산에 대한 액세스 종료 또는 실패한 액세스 후 실제 액세스**를 선택 취소한 후 **다음**을 선택합니다.

1. **검색 옵션** 페이지의 **시퀀스 검색**, **누적 반출 검색** 및 **위험 점수 부스터** 섹션에서 **모두 선택**을 선택한 후 **다음**을 선택합니다.

1. **기본 또는 사용자 지정 표시기 임계값을 사용할지 여부 결정** 페이지에서 **기본 임계값**을 선택한 후 **다음**을 선택합니다.

1. **설정 검토 및 완료** 페이지에서 **제출**을 선택합니다.

1. **정책이 만들어짐** 페이지에서 **완료**를 선택합니다.

    >[!note] **참고:** 이 페이지에 설명된 대로 정책 일치 항목이 경고 탭에 표시되기 시작하는 데 최대 24시간이 걸릴 수 있습니다.

중요한 재무 정보에 대한 무단 액세스를 검색하고 보호하는 데 도움이 되는 '재무 데이터 보호' 정책을 성공적으로 만들었습니다. 정책 일치 항목이 경고 탭에 표시되는 데 최대 24시간이 걸릴 수 있습니다.

## 작업 4: 알림 템플릿 만들기

이 작업에서는 Microsoft Purview의 내부 위험 관리에서 미리 알림 템플릿을 만듭니다. 이를 통해 위험 작업에 대한 사례가 만들어질 때 미리 알림 역할을 하거나 규정 준수 학습을 위한 정보를 제공할 때 자동으로 사용자에게 이메일 메시지를 보낼 수 있습니다.

1. 내부 위험 관리의 Microsoft Purview에는 계속 Joni로 로그인되어 있어야 합니다.

1. 상단 탐색 탭에서 **알림 템플릿**을 선택한 다음 **+ 알림 템플릿 만들기**를 선택합니다.

1. 오른쪽에 있는 **새 알림 템플릿 만들기** 플라이아웃 페이지에서 필요한 정보를 작성합니다.

    - **템플릿 이름**: 데이터 유출 정책 경고
    - **보낸 사람**: Joni Sherman
    - **제목**: 잠재적인 데이터 유출이 검색됨
    - **메시지 본문**:

        ````html
        <!DOCTYPE html>
        <html>
        <body>
        <h2>Alert: Potential Data Leak Detected</h2>
        <p>We detected a potential data leak associated with your account. As part of our Insider Risk Management policy, we are required to investigate any suspicious activity related to data breaches.</p>
        <p>Please review your recent actions, report any unusual behavior, and refer to the Contoso User Code of Conduct training at <a href='https://contoso.com'>https://contoso.com</a> for more information.</p>
        <p>Thank you for your cooperation,</p>
        <p><em>Human Resources</em></p>
        </body>
        </html>
        ````

1. **만들기**를 실행합니다.

잠재적인 데이터 유출이 검색되면 자동 경고가 사용자에게 전송되도록 설정하고 보안 조치를 강화하며 Contoso 사용자 사용 규정 준수를 촉진하는 **데이터 유출 정책 경고** 알림 템플릿을 성공적으로 만들었습니다.

## 작업 5: 적응형 보호 살펴보기

이 작업에서는 Microsoft Purview 내부 위험 관리의 적응형 보호를 살펴보겠습니다. 빠른 및 사용자 지정 설정 옵션, 사용자 지정 가능한 위험 수준, 과거 작업 검색 설정 및 위험 수준 시간 프레임을 살펴보겠습니다. 또한 사용자별 위험 수준과 DLP 정책을 표시하는 탭을 검토하고 포털에서 적응형 보호 기능을 사용하거나 사용하지 않도록 설정할 수 있는 위치를 알아봅니다.

1. 내부 위험 관리의 Microsoft Purview에는 계속 Joni로 로그인되어 있어야 합니다.

1. 상단의 탐색 탭에서 **적응형 보호(미리 보기)** 를 선택합니다.

1. 내부 위험 관리에서 처음으로 **적응형 보호(미리 보기)** 단추를 선택하면 적응형 보호를 설정할 수 있는 두 가지 옵션이 표시됩니다.

    ![적응형 보호를 시작을 위한 옵션의 스크린샷.](../Media/turn-on-adaptive-protection.png)

1. 시작하는 데는 두 가지 옵션이 있습니다. **빠른 설정** 또는 **사용자 지정**. 빠른 설정은 가장 빠르게 시작할 수 있는 방법입니다. 시작하는 데 기존 DLP 또는 내부 위험 관리 정책이 필요하지 않습니다. 사용자 지정 설정을 사용하면 정책을 더 효과적으로 제어할 수 있으며 기존 DLP 및 내부 위험 관리 정책이 있는 경우 권장됩니다. 빠른 설정을 시작하는 데는 약 72시간이 소요되고, 사용자 지정 설정은 약 36시간이 소요됩니다.

1. **적응형 보호(미리 보기)** 창의 왼쪽 탐색 창에서 **적응형 보호 위험 수준**을 선택합니다.

    ![적응형 보호에서 선택한 적응형 보호의 위험 수준 스크린샷.](../Media/adaptive-protection-navigation-risk-level.png)

1. 적응형 보호에서 사용자 지정 가능한 위험 수준을 살펴봅니다.

    - **높은 위험 수준**: 심각도가 높은 경고 또는 여러 가지 고위험 작업으로 사용자에게 플래그를 지정합니다.
    - **중간 위험 수준**: 심각도가 중간 수준인 경고 또는 고위험 데이터 반출이 2회 이상 발생한 사용자에게 집중합니다.
    - **낮은 위험 수준**: 심각도가 낮은 경고 또는 단일 고위험 데이터 반출이 있는 사용자의 문제를 해결합니다.

1. 각 위험 수준 옆에 있는 **편집** 단추를 선택하여 액세스할 수 있는 사용자 지정 옵션이 있습니다.

    ![적응형 보호의 위험 수준에 대한 조건 정의 스크린샷](../Media/adaptive-protection-navigation-risk-level-edit.png)

1. **과거 작업 검색** 및 **위험 수준 시간 프레임**에 대한 옵션을 살펴봅니다.

    - **과거 작업 검색**: 사용자의 일별 작업이 위험 수준 조건을 충족하는지 평가하기 위해 5~30일 사이의 되돌아보기 기간을 지정합니다.
    - **위험 수준 시간 프레임**: 자동 초기화 전에 위험 수준이 사용자에게 할당된 상태로 유지되는 기간(5~30일)을 결정합니다.

1. **적응형 보호 위험 수준** 탭의 옵션 검토를 마친 후 왼쪽 탐색 창에서 **사용자가 할당한 위험 수준** 탭을 선택합니다.

    ![적응형 보호에서 선택된 사용자 할당 위험 수준의 스크린샷.](../Media/users-assigned-adaptive-protection.png)

1. 활성화되면 **사용자가 할당한 위험 수준** 탭에 각 사용자의 이름 또는 익명화된 버전, 현재 위험 수준, 할당 이후 경과된 시간, 자동 초기화까지 남은 기간(일)이 표시됩니다. 기존 경고나 사례를 제거하지 않고 위험 수준을 수동으로 만료할 수 있습니다. 탭에는 각 사용자에 대한 현재 경고 및 확인된 사례 수도 표시됩니다.

1. **사용자가 할당한 위험 수준** 탭 탐색을 마친 후 왼쪽 탐색 창에서 **DLP 정책** 탭을 선택합니다.

    ![적응형 보호에서 선택한 DLP 정책의 스크린샷.](../Media/dlp-policies-adaptive-protection.png)

1. **DLP 정책** 페이지에는 각 정책의 이름, 현재 상태, 위치, 포함된 위험 수준, 상태, 만든 날짜 및 마지막 수정 날짜가 표시됩니다.

1. **DLP 정책** 탭 탐색을 마쳤으면 왼쪽 탐색 창에서 **적응형 보호 설정** 탭을 선택합니다.

    ![적응형 보호에서 선택된 적응형 보호 설정의 스크린샷.](../Media/adaptive-protection-settings-selected.png)

1. **적응형 보호 설정** 탭에서 기능을 켜거나 끌 수 있습니다. 이 기능을 끄면 위험 수준 할당이 중지되고 기존 위험 수준이 다시 설정되며, 완전히 비활성화하는 데 최대 6시간이 소요됩니다. 정책은 자동으로 삭제되지 않습니다.

내부 위험 관리에서 적응형 보호를 성공적으로 살펴보았습니다.
