---
lab:
  title: 연습 3 - 학습 가능한 분류자 관리
  module: Module 1 - Implement Information Protection
---

# 랩 1 - 연습 3 - 학습 가능한 분류자 관리

Contoso Ltd.는 고급 드론 기술에 중점을 둔 Mark8 프로젝트의 연구 개발(R&D)에 참여하고 있습니다. 회사는 이 프로젝트와 관련된 민감한 정보를 적절히 분류하여 무단 액세스 또는 공유로부터 보호해야 합니다. 이 랩에서는 Mark8 프로젝트와 연결된 문서를 식별하고 레이블을 지정하도록 설계된 학습 가능한 분류자를 만듭니다. 현재 데이터 세트의 제한 사항으로 인해 Contoso는 분류자를 완전히 학습시킬 수 있는 관련 문서의 예제가 충분하지 않을 수 있습니다. 이 연습에서는 분류자 정확도를 개선하기 위해 다양하고 포괄적인 데이터 샘플을 갖는 것의 중요성을 강조합니다.

>[!알림] 이 학습 테넌트에서 사용할 수 있는 제한된 데이터로 인해 이 랩의 학습 가능한 분류자 생성 프로세스는 성공적인 분류 결과를 얻지 못합니다. 이 연습은 학습 가능한 분류자를 구성하는 상호 작용 환경을 제공하여 설정 및 검토 프로세스를 탐색할 수 있도록 설계되었습니다. 분류자는 예상대로 데이터를 완전히 학습시키고 분류하지는 않지만, 연습에서는 워크플로에 대한 인사이트와 효과적인 분류자 학습에 필요한 고려 사항을 제공합니다. 

## 작업 1 – 학습 가능한 분류자 만들기

이 작업에서는 Contoso Ltd. 내에서 Mark8 프로젝트와 관련된 중요한 문서를 식별하고 보호하도록 학습 가능한 분류자를 설정합니다.

1. 클라이언트 1 VM(LON-CL1)에는 여전히 **LON-CL1\admin** 계정으로 로그인해야 하며, Microsoft 365에는 **Joni Sherman**으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge**에서 **`https://compliance.microsoft.com`** 으로 이동합니다.

1. 왼쪽 탐색 창에서 **데이터 분류**를 확장한 다음 **분류자**를 선택합니다.

1. **분류자** 페이지에서 **학습 가능한 분류자** 탭이 이미 선택되어 있어야 합니다.

2. **+ 학습 가능한 분류자 만들기**를 선택하여 새 분류자를 만듭니다.

1. **학습 가능한 분류자 이름 지정 및 설명** 페이지에서 다음 정보를 입력합니다.

    - **이름**: `Mark8 Project Documents`
    - **설명**: `Classifier for identifying sensitive documents related to the Mark8 drone project's research and development efforts.`

1. **다음**을 선택합니다.

1. **긍정적인 샘플 콘텐츠 출처**에서 **+ 사이트 선택**을 선택합니다.

1. 오른쪽에 있는 **SharePoint 사이트 추가** 플라이아웃 페이지에서 다음 SharePoint 사이트를 선택합니다.

    - Mark8ProjectTeam

1. 플라이아웃 페이지의 아래쪽에서 **추가**를 선택합니다.

1. **긍정적인 샘플 콘텐츠 출처** 페이지로 돌아와서 **다음**을 선택합니다.

1. **부정적인 샘플 콘텐츠 출처** 페이지에서 다음 SharePoint 사이트를 선택합니다.

    - HR

1. 플라이아웃 페이지의 아래쪽에서 **추가**를 선택합니다.

1. **부정적인 샘플 콘텐츠 출처** 페이지로 돌아와서 **다음**을 선택합니다.

1. **샘플 콘텐츠 처리를 위해 분류자 검토 및 생성**에서 **학습 가능한 분류자 생성**을 선택합니다.

1. **학습 중인 분류자** 페이지에서 **완료**를 선택합니다.

선택한 SharePoint 사이트의 문서와 파일 분석이 진행됩니다. 이 분석에는 최대 48시간이 걸릴 수 있습니다.

## 작업 2 - 분류자 결과 검토

Joni는 학습 가능한 분류자를 구성했음에도 불구하고 예상했던 결과가 나오지 않는다는 을 발견했습니다. 이 작업에서는 학습 가능한 분류자의 결과를 검토하여 의도한 콘텐츠를 성공적으로 분류하지 못한 이유를 파악하고 부족하거나 잘못 정렬된 학습 샘플과 같은 잠재적인 문제에 집중합니다.

1. 포털의 **분류자** 페이지에서 계속 Microsoft Purview에 로그인되어 있어야 합니다. Microsoft 365에 **Joni Sherman**으로 로그인해야 합니다.

1. **게시됨** 옆의 아래쪽 화살표를 선택하면 게시된 학습 가능한 분류자를 축소하여 학습 중인 분류자를 더 쉽게 식별할 수 있습니다.

1. **Mark8 프로젝트 문서**에는 교육이 완료될 때까지 **진행 중**이라는 상태가 표시됩니다.

1. 학습이 완료되면 분류자가 **학습 실패**로 업데이트됩니다.

1. 이 분류자가 실패한 이유를 확인하려면 **새 창에서 열기** 화살표가 있는 창 아이콘을 선택하세요.

1. **Mark8 프로젝트 문서** 분류자 창에서 **개요** 및 **테스트 결과 검토** 탭을 검토하여 이 분류자가 실패한 이유를 이해합니다.

1. 테스트 결과를 검토한 결과, 샘플 데이터에 **가양성**과 **가음성**이 다수 존재하는 것으로 나타났습니다.

1. 이 분류자를 제거하려면 **Mark8 프로젝트 문서** 페이지의 오른쪽 상단에 있는 **삭제** 버튼을 선택하세요.

이제 학습 가능한 분류자 결과의 검토를 완료했습니다. 이 프로세스에서는 성공적인 분류를 달성하기 위해 충분하고 올바르게 정렬된 학습 샘플의 중요성을 강조했습니다. 분류자의 실패 원인을 이해하면 향후 구성을 더 잘 준비하여 보다 정확하고 신뢰할 수 있는 데이터 분류를 보장할 수 있습니다.
