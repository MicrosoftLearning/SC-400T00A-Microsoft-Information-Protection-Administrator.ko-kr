---
ms.openlocfilehash: 55e33ed310c3e272cfd1f9812b99bb8df2c5d53f
ms.sourcegitcommit: 87981d92cddd039f65cba07c3f57ea6a12dd251a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2022
ms.locfileid: "147155294"
---
# <a name="lab-2---exercise-3---manage-dlp-reports"></a>랩 2 - 연습 3 - DLP 보고서 관리

Contoso Ltd.의 준수 관리자인 Joni Sherman이 회사 Microsoft 365 테넌트에서 데이터 손실 방지 기능을 구성하는 작업을 맡게 되었습니다. Contoso Ltd.는 미국의 운전학원입니다. 학원에 등록하는 중요한 고객 정보가 조직 외부로 유출되지 않도록 해야 합니다. 신임 준수 관리자가 DLP 보고서 검토를 지원할 예정이라고 합니다.

### <a name="task-1---grant-access-to-dlp-reports"></a>작업 1 - DLP 보고서 액세스 허용

이 연습에서는 신임 준수 관리자 Megan Bowen에게 DLP 보고서 액세스 권한을 부여합니다. 이 준수 관리자는 일반 사용자이므로 보고서 내용만 확인하고 DLP 구성을 변경하지는 않을 예정입니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 VM(LON-CL1)에 로그인합니다.

1. **Microsoft Edge** 에서 **https://compliance.microsoft.com** 으로 이동한 다음, Microsoft Purview 포털에 **MOD 관리자** admin@WWLxZZZZZZ.onmicrosoft.com 으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  관리자의 암호는 랩 호스팅 공급자가 제공합니다.

1. 왼쪽 탐색 창에서 **권한** 을 선택한 다음, **Microsoft Purview 솔루션** 에서 **역할** 을 선택합니다.   **보안 읽기 권한자** 역할에 대한 필드를 선택합니다.

1. 보안 읽기 권한자 창의 **구성원** 영역에서 **편집** 을 선택합니다.

1. **구성원 선택** 을 선택하고 **+ 추가** 를 선택합니다.

1. **Megan Bowen** 을 검색하여 이름 앞의 체크박스를 선택한 후 **추가** 를 선택합니다.

1. 구성원 목록의 변경 내용을 검토하고 **완료** 를 선택합니다.

1. **저장** 을 선택합니다. **보안 읽기 권한자** 역할 창을 닫습니다.

Microsoft 365 규정 준수 포털에서 신임 준수 관리자에게 DLP 보고서 액세스 권한을 부여했습니다.

### <a name="task-2---test-access-to-dlp-reports"></a>작업 2 - DLP 보고서 액세스 테스트

이 작업에서는 작업 1에서 부여한 DLP 보고서 액세스 권한이 올바르게 적용되었는지를 테스트합니다.

1. **lon-cl2\admin** 계정으로 클라이언트 2 VM(LON-CL2)에 로그인합니다.

1. **Microsoft Edge** 에서 **https://compliance.microsoft.com** 으로 이동한 다음, Microsoft Purview 포털에 **Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com 으로 로그인합니다(ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임).  Megan의 암호는 랩 호스팅 공급자가 제공합니다.

1. 왼쪽 탐색 창에서 **보고서** 를 선택하고 보고서 대시보드 액세스 권한을 살펴봅니다.

    **경고**: 오류와 함께 메시지가 표시되는 경우 랩의 이후 지점에서 돌아와 보고 섹션을 확인합니다. 평가판 또는 개인 개발자 테넌트에서 이러한 단계를 수행할 수도 있습니다.

    [//]: <> (보고서 섹션에 액세스할 때 랩 테넌트에 오류 메시지가 표시됩니다. 하지만 이 작업은 랩 테넌트에서 작동합니다.)

1. **조직 데이터** 섹션까지 아래로 스크롤하고 **DLP 정책 일치** 를 선택하여 랩 테넌트에서 DLP 정책의 일치 항목을 검토합니다.

1. **보고서** 를 다시 선택하고 **조직 데이터** 섹션으로 스크롤하여 **DLP 인시던트** 및 **DLP 가양성 및 재정의** 를 하나씩 선택하고 보고서 데이터를 검토합니다. 

1. 보고서를 검토한 후 왼쪽 탐색 창에서 **데이터 손실 방지** 를 선택하고 **활동 탐색기** 를 선택합니다.

1. 필터를 사용하여 테넌트에서 DLP 관련 활동을 표시합니다.

1. 이 마지막 연습을 완료하려면 클라이언트를 열어 둡니다.

Purview 포털에서 액세스 권한이 구성되었으며 신임 준수 관리자가 보고서를 볼 수 있음을 확인했습니다.

## <a name="you-have-completed-the-lab-2-proceed-to-lab-3---exercise-1"></a>랩 2를 완료했습니다. 랩 3 - 연습 1으로 진행합니다.
