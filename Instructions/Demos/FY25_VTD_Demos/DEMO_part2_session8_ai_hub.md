---
lab:
  title: 세션 8 - AI 허브 인사이트 및 관리
  module: Learning Objective - Manage AI Hub policies in Microsoft Purview
---

# 2부 - 데모 랩 8 - AI 허브에서 정책 활성화

> 참고: 이 데모에서는 AI 허브에서 정책을 사용하도록 설정하는 것 외에는 할 일이 많지 않습니다. 이 데모에서는 AI 허브에 대해 Microsoft Purview 포털에 표시되는 내용 중 일부 요소를 설명하고 정책을 사용하도록 설정합니다.

## 작업 1 - AI 허브에서 정책 활성화

이 작업에서는 Microsoft Purview 내부 위험 관리의 적응형 보호를 살펴보겠습니다. 빠른 및 사용자 지정 설정 옵션, 사용자 지정 가능한 위험 수준, 과거 작업 검색 설정 및 위험 수준 시간 프레임을 살펴보겠습니다. 또한 사용자별 위험 수준과 DLP 정책을 표시하는 탭을 검토하고 포털에서 적응형 보호 기능을 사용하거나 사용하지 않도록 설정할 수 있는 위치를 알아봅니다.

1. **Microsoft Edge**에서 **`https://purview.microsoft.com`** 으로 이동한 다음, Microsoft Purview 포털에 `admin@WWLxZZZZZZ.onmicrosoft.com`으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).

1. 왼쪽 사이드바에서 **솔루션**을 선택한 다음 **AI 허브(미리 보기)** 를 선택합니다.

1. 포털에서 **시작** 필수 구성 요소를 검토합니다.

1. 왼쪽 사이드바에서 **정책**을 선택합니다.

1. **정책** 페이지의 **추천**에서 **AI 데이터 보안 강화** 및 **AI 내 비윤리적 동작 제어** 카드를 검토합니다.

1. **AI 데이터 보안 강화** 카드에서 **시작**을 선택합니다.

1. 오른쪽의 **AI 데이터 보안** 플라이아웃 패널을 검토합니다. 이 패널에서는 이 AI 허브 권장 사항에 대한 정책을 만들면 어떤 일이 생기는지 설명합니다.

   **시작**을 선택하면 적응형 보호 및 민감도 레이블 정책 설정에 대해 간략하게 설명하는 패널이 표시됩니다. 이 설정은 타사 AI 애플리케이션에 중요한 데이터를 붙여넣거나 업로드하려는 사용자를 차단하거나 경고하는 적응형 보호 정책을 만들고, 민감도 레이블을 적용하여 Outlook 및 Word와 같은 앱의 콘텐츠를 보호합니다. 또한 기존 정책은 변경되지 않고 DLP 규칙 일치는 활동 탐색기에 표시된다는 점도 설명합니다.

1. 이 패널을 검토한 후 **정책 만들기**를 선택합니다.

1. 정책이 만들어지면 **정책을 만들었습니다**라는 메시지와 만든 정책에 대한 설명이 표시됩니다.

1. 오른쪽 위에 있는 **X**를 선택하여 오른쪽 플라이아웃 패널을 닫습니다.

1. 정책 페이지로 돌아가서 **AI 내 비윤리적 동작 제어** 카드에서 **시작**을 선택합니다. 

1. 오른쪽의 **AI 내 비윤리적 동작 제어** 플라이아웃 패널을 검토합니다. 이 패널에서는 이 AI 허브 권장 사항에 대한 정책을 만들면 어떤 일이 생기는지 설명합니다.

   이 패널에서는 Microsoft 365 Copilot 상호 작용에서 잠재적으로 비윤리적인 동작을 감지하는 정책을 설정하는 방법에 대한 세부 정보를 제공합니다. 정책은 중요한 정보에 대한 프롬프트 및 응답을 모니터링하여 커뮤니케이션 규정 준수에서 검토를 위한 경고를 생성하되, 최종 사용자에게 영향을 주지 않습니다. 사용자는 감지된 상호 작용의 검토자로 할당됩니다.

1. 이 패널을 검토한 후 **정책 만들기**를 선택합니다.

1. 정책이 만들어지면 **정책을 만들었습니다**라는 메시지와 만든 정책에 대한 설명이 표시됩니다.

1. 패널 아래쪽의 **닫기**를 선택하여 **정책** 화면으로 돌아갑니다.