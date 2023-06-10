---
lab:
  title: 연습 3 - DLP 보고서 관리
  module: Module 2 - Implement Data Loss Prevention
---

# 랩 2 - 연습 3 - DLP 보고서 관리

Contoso Ltd.의 준수 관리자인 Joni Sherman이 회사 Microsoft 365 테넌트에서 데이터 손실 방지 기능을 구성하는 작업을 맡게 되었습니다. Contoso Ltd.는 미국의 운전학원입니다. 학원에 등록하는 중요한 고객 정보가 조직 외부로 유출되지 않도록 해야 합니다. 신임 준수 관리자가 DLP 보고서 검토를 지원할 예정이라고 합니다.

## 작업 1 - DLP 보고서 액세스 허용

이 연습에서는 신임 준수 관리자 Megan Bowen에게 DLP 보고서 액세스 권한을 부여합니다. 이 준수 관리자는 일반 사용자이므로 보고서 내용만 확인하고 DLP 구성을 변경하지는 않을 예정입니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 VM(LON-CL1)에 로그인합니다.

1. **Microsoft Edge**에서 **https://compliance.microsoft.com** 으로 이동한 다음, Microsoft Purview 포털에 **MOD 관리자** admin@WWLxZZZZZZ.onmicrosoft.com 으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  관리자의 암호는 랩 호스팅 공급자가 제공합니다.

1. 왼쪽 탐색 창에서 **권한**을 선택한 다음, **Microsoft Purview 솔루션**에서 **역할**을 선택합니다.   **Information Protection 분석가** 역할에 대한 필드를 선택합니다.

1. *Information Protection 분석가* 창의 **구성원** 영역에서 **편집**을 선택합니다.

1. **구성원 선택**을 선택하고 **+ 추가**를 선택합니다.

1. **Megan Bowen**을 검색하여 이름 앞의 체크박스를 선택한 후 **추가**를 선택합니다.

1. 구성원 목록의 변경 내용을 검토하고 **완료**를 선택합니다.

1. **저장**을 선택합니다. **Information Protection 분석가** 역할 창을 닫습니다.

Microsoft 365 규정 준수 포털에서 신임 준수 관리자에게 DLP 보고서 액세스 권한을 부여했습니다.

## 작업 2 - DLP 보고서 액세스 테스트

이 작업에서는 작업 1에서 부여한 DLP 보고서 액세스 권한이 올바르게 적용되었는지를 테스트합니다.

1. **lon-cl2\admin** 계정으로 클라이언트 2 VM(LON-CL2)에 로그인합니다.

1. **Microsoft Edge**에서 **https://compliance.microsoft.com** 으로 이동한 다음, Microsoft Purview 포털에 **Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com 으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  Megan의 암호는 랩 호스팅 공급자가 제공합니다.

1. 왼쪽 탐색 창에서 **데이터 손실 방지** 를 위한 드롭다운을 선택한 다음 **, 활동 탐색기를** 선택합니다.

1. **활동 탐색기** 페이지에서 **기본 제공 필터**에 대한 드롭다운을 선택합니다. 

1. 활동 필터 **를 검색한 DLP 정책 및 활동** 필터를 **검색한 DLP 정책 규칙을** 탐색합니다.

1. 이 마지막 연습을 완료하려면 클라이언트를 열어 둡니다.

Purview 포털에서 액세스 권한이 구성되었으며 신임 준수 관리자가 보고서를 볼 수 있음을 확인했습니다.
