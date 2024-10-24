---
lab:
  title: 연습 2 - Microsoft Purview 메시지 암호화 관리
  module: Module 1 - Implement Information Protection
---

<!--
# Lab 1 - Exercise 2 - Manage Microsoft Purview Message Encryption
-->

# 연습 3 - Microsoft Purview 메시지 암호화 관리

Joni Sherman이 파일럿 팀과 함께 구성하고 테스트해야 하는 첫 번째 설정은 Microsoft Purview 메시지 암호화입니다. 이 작업을 위해 Joni는 기본 템플릿을 수정하여 새 브랜딩 템플릿을 만든 다음 파일럿 사용자 중 한 명에게 할당할 예정입니다. 그런 다음 파일럿 사용자는 자신의 계정으로 메시지 암호화 기능을 테스트합니다.

## 작업 1 - Azure RMS 기능 확인

이 작업에서는 Exchange Online PowerShell 모듈을 설치하고 Joni Sherman의 컨텍스트에서 테넌트의 Azure RMS 기능이 올바르게 작동하는지를 확인합니다. 지난 연습에서 이 작업을 위해 Joni에게 준수 관리자 역할을 할당했습니다.

<!--
1. You should still be signed in to Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. Open an elevated PowerShell window by selecting the Windows button with the right mouse button and then select **Windows PowerShell (Admin)**.

1. Confirm the **User Account Control** window with **Yes**.
-->

1. 작업 표시줄에서 관리자 권한 PowerShell 창을 엽니다.

1. 다음 cmdlet을 입력하여 최신 Exchange Online PowerShell 모듈 버전을 설치합니다.

    ```powershell
    Install-Module ExchangeOnlineManagement
    ```

1. 신뢰할 수 없는 리포지토리 보안 대화 상자가 표시되면 Yes에 해당하는 **Y** 키를 누르고 **Enter** 키를 누릅니다.  이 프로세스를 완료하는 데 약간의 시간이 걸릴 수 있습니다.

1. 다음 cmdlet을 입력하여 실행 정책을 변경하고 **Enter** 키를 누릅니다.

    ```powershell
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
    ```

1. Yes에 해당하는 **Y** 키를 눌러 실행 정책 변경을 확인하고 **Enter** 키를 누릅니다.

<!--
1. Close the PowerShell window.

1. Open a regular PowerShell window, without elevation, by selecting the Windows button with the right mouse button and select **Windows PowerShell**.
-->

1. 다음 cmdlet을 입력하여 Exchange Online PowerShell 모듈을 사용해 테넌트에 연결합니다.

    ```powershell
    Connect-ExchangeOnline
    ```

1. **로그인** 창이 표시되면 JoniS@WWLxZZZZZZ.onmicrosoft.com으로 로그인합니다(여기서 ZZZZZZ는 랩 호스팅 공급자가 제공한 고유 테넌트 ID임). 이전 랩에서 Joni의 암호를 다시 설정한 암호를 사용하게 됩니다.

1. 다음 cmdlet을 사용하여 테넌트에서 Azure RMS 및 IRM이 활성화되어 있는지 확인하고 **Enter** 키를 누릅니다.

    ```powershell
    Get-IRMConfiguration | fl AzureRMSLicensingEnabled
    ```

1. **AzureRMSLicensingEnabled** 결과가 **True**이면 테넌트에 대해 Azure RMS가 활성화됩니다. 다음 단계를 계속합니다. 

1. 다음 cmdlet을 사용하여 다른 파일럿 사용자인 **Megan Bowen**을 대상으로 Office 365 메시지 암호화에 사용되는 Azure RMS 템플릿을 테스트하고 **Enter** 키를 누릅니다.

    ```powershell
    Test-IRMConfiguration -Sender MeganB@contoso.com -Recipient MeganB@contoso.com
    ```

    ![IRM 유효성 검사 스크립트 결과. ](../Media/IRMvalidationl.png)

1. 모든 테스트가 **PASS**로 표시되고 오류가 표시되지 않는지 확인합니다.

1. PowerShell 창은 열어 둡니다.

Exchange Online PowerShell 모듈을 설치하고 테넌트에 연결하여 Azure RMS의 기능이 올바르게 작동하는지를 확인했습니다.

## 작업 2 – 기본 브랜딩 템플릿 수정

조직에서 Google, Facebook 등의 외부 ID 공급자에 대한 신뢰를 제한하려는 경우 이 작업을 수행해야 합니다. 이러한 소셜 ID는 메시지 암호화로 보호되는 메시지에 액세스하기 위해 기본적으로 활성화되므로 조직의 모든 사용자에 대해 소셜 ID 사용을 비활성화해야 합니다.

<!--
1. You should still be signed in to your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account and there should still be an open PowerShell window with Exchange Online connected.
-->

1. 기본 구성을 보려면 다음 cmdlet을 실행합니다.

    ```powershell
    Get-OMEConfiguration -Identity "OME Configuration" | fl
    ```

1. 설정을 검토하고 **SocialIdSignIn** 매개변수가 **True**로 설정되어 있는지 확인합니다.

1. 다음 cmdlet을 실행하여 OME로 보호되는 테넌트에서 메시지 액세스에 소셜 ID 사용을 제한합니다.

    ```powershell
    Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn:$false
    ```

1. 기본 템플릿 사용자 지정 관련 경고 메시지가 표시되면 Yes에 해당하는 **Y** 키를 누르고 **Enter** 키를 누릅니다.

1. 기본 구성을 다시 확인하여 SocialIdSignIn 매개 변수가 이제 False로 설정되어 있는지 유효성을 검사합니다.

    ```powershell
    Get-OMEConfiguration -Identity "OME Configuration" | fl
    ```

1. 결과에 **SocialIDSignIn**이 **False**로 설정되어 있는 것으로 표시되어야 합니다. PowerShell 창과 클라이언트는 열어 둡니다.

Office 365 메시지 암호화에서 Google, Facebook 등의 외부 ID 공급자 사용을 비활성화했습니다.

## 작업 3 – 기본 브랜딩 템플릿 테스트

테넌트 사용자로부터 Office 365 메시지 암호화로 보호되는 메시지를 수신할 때 외부 수신자에 대한 소셜 ID 대화 상자가 표시되지 않는지 확인해야 하며, 암호화된 콘텐츠에 액세스할 때 언제든지 OTP를 사용해야 합니다.

1. 다른 VM인 클라이언트 2 VM(LON-CL2)에 **lon-cl2\admin** 계정으로 로그인합니다.

<!--
1. Make sure all available Windows Updates are installed and the client does not require a restart to finish update installation.

[//]: <> (Installing the latest OS updates will also update the Edge browser to the new chromium version required to do this labs.)

1. Open **Microsoft Edge** from the taskbar and when a **Welcome to Microsoft Edge** windows is displayed, select **Start without your data**, select **Continue without this data** again and select **Confirm and start browsing**.

1. If the welcome message is missing, navigate to https://microsoft.com/edge, select **DOWNLOAD for Windows** and **Windows 10**. Select **Accept and download** and **Run** to install the latest version of the Edge browser. Once this is complete perform the previous step.
-->

1. **Microsoft Edge**를 열고 https://outlook.office.com로 이동합니다.

1. 웹에서 LynneR@WWLxZZZZZZ.onmicrosoft.com(여기서 ZZZZZZ는 랩 호스팅 공급자에서 제공한 고유 테넌트 ID)로 Outlook에 로그인합니다. 

    >코스를 시작할 때 Joni Sherman의 비밀번호와 함께 Lynne의 비밀번호를 다시 설정합니다.

1. **로그인 상태를 유지하시겠습니까?** 대화 상자에서 **이 메시지를 다시 표시 안 함** 체크박스를 선택하고 **아니요**를 선택합니다.

1. **암호 저장** 대화 상자에서 **저장**을 선택하여 파일럿 사용자의 암호를 브라우저에 저장합니다.

1. **페이지 번역...** 창이 표시되면 아래쪽 화살표를 선택하고 **번역하지 않음...** 을 선택합니다.

1. Outlook의 왼쪽 상단 모서리에서 **새 메일**을 선택합니다.

1. **받는 사람** 필드에 테넌트 도메인에 없는 개인 또는 기타 타사 이메일 주소를 입력합니다. 

1. **제목 추가** 필드에 **비밀 메시지**를 입력합니다.

1. 본문에 **나의 극비 메시지**를 입력합니다.

1. 위쪽 막대에서 **옵션** 탭을 선택한 다음 **암호화**(자물쇠 아이콘), 드롭다운 목록에서 **암호화**를 차례로 선택합니다. 

    >**보내기** 위의 메시지 창 상단에 "이 메시지는 암호화되어 있습니다"라는 알림이 표시됩니다. 수신자는 암호화를 제거할 수 없습니다."

    ![Encyption 설정의 스크린샷](../Media/OptionsEncrypt.png)

1. **보내기**를 선택하여 메시지를 보냅니다.

1. 개인 이메일 계정에 로그인하여 Lynne Robbins의 메시지를 엽니다. 

1. 이 이메일을 Microsoft 계정(예: @outlook.com)으로 보낸 경우 암호화가 자동으로 처리되어 추가 단계 없이 메시지가 표시될 수 있습니다.

    >**참고:** **나의 극비 메시지**가 표시되는 경우 이제 이 작업이 완료되었습니다. 그렇지 않으면 다음 단계를 진행하세요.

1. @gmail.com와 같은 다른 이메일 서비스로 이메일을 보낸 경우 암호화를 처리하고 메시지를 읽으려면 다음 단계를 수행해야 할 수 있습니다.

    >**참고:** Lynne Robbins의 메시지가 정크 또는 스팸 폴더에 있는지 확인해야 할 수도 있습니다.

1. **메시지 읽기**를 선택합니다.

1. 소셜 ID가 활성화되어 있지 않으므로 Google 계정을 사용한 인증 단추는 표시되지 않습니다.

1. **일회용 암호로 로그인**을 선택하여 일정 시간 동안만 사용할 수 있는 암호를 받습니다.

1. 개인 이메일 포털로 이동하여 제목이 **메시지를 보기 위한 일회용 암호**인 메시지를 엽니다.

1. 암호를 복사하여 OME 포털에 붙여넣은 후에 **계속**을 선택합니다.

1. 암호화된 메시지를 검토합니다.

<!--
1. Leave Client 1 VM (LON-CL1) open as it is.
-->

비활성화된 소셜 ID를 사용하여 수정된 기본 OME 템플릿을 테스트했습니다.

## 작업 4 - 사용자 지정 브랜딩 템플릿 만들기

조직 경리부에서 보내는 보호된 메시지에는 특수 브랜딩을 사용해야 합니다. 이러한 브랜딩에는 사용자 지정된 소개 및 본문 텍스트, 그리고 바닥글의 고지 사항 링크가 포함됩니다. 또한 경리부에서 보내는 메시지는 7일 후에 만료되어야 합니다. 이 작업에서는 새 사용자 지정 OME 구성, 그리고 경리부에서 보내는 모든 메일에 해당 OME 구성을 적용하는 전송 규칙을 만듭니다.

1. **lon-cl1\admin** 계정으로 클라이언트 1 VM(LON-CL1)에 다시 로그인하면 여전히 Exchange Online이 연결된 상태에서 열려 있는 PowerShell 창이 있어야 합니다.

1. 다음 cmdlet을 실행하여 새 구성을 만듭니다.

    ```powershell
    New-OMEConfiguration -Identity "Finance Department" -ExternalMailExpiryInDays 7
    ```

1. 템플릿 사용자 지정 관련 경고 메시지가 표시되면 Yes에 해당하는 **Y** 키를 누르고 **Enter** 키를 누릅니다. 

1. 다음 cmdlet을 사용하여 소개 텍스트 메시지를 변경합니다.

    ```powershell
    Set-OMEConfiguration -Identity "Finance Department" -IntroductionText " from Contoso Ltd. finance department has sent you a secure message."
    ```

1. 템플릿 사용자 지정 관련 경고 메시지가 표시되면 Yes에 해당하는 **Y** 키를 누르고 **Enter** 키를 누릅니다.

1. 다음 cmdlet을 사용하여 메시지의 본문 전자 메일 텍스트를 변경합니다.

    ```powershell
    Set-OMEConfiguration -Identity "Finance Department" -EmailText "Encrypted message sent from Contoso Ltd. finance department. Handle the content responsibly."
    ```

1. 템플릿 사용자 지정 관련 경고 메시지가 표시되면 Yes에 해당하는 **Y** 키를 누르고 **Enter** 키를 누릅니다.

1. Contoso 개인정보처리방침 사이트를 가리키도록 고지 사항 URL을 변경합니다.

    ```powershell
    Set-OMEConfiguration -Identity "Finance Department" -PrivacyStatementURL "https://contoso.com/privacystatement.html"
    ```

1. 템플릿 사용자 지정 관련 경고 메시지가 표시되면 Yes에 해당하는 **Y** 키를 누르고 **Enter** 키를 누릅니다.

1. 다음 cmdlet을 사용하여 메일 흐름 규칙을 만듭니다. 이 규칙은 경리팀에서 보내는 모든 메시지에 사용자 지정 OME 템플릿을 적용합니다.  이 프로세스가 완료될 때까지 몇 초 정도 걸릴 수 있습니다.

    ```powershell
    New-TransportRule -Name "Encrypt all mails from Finance team" -FromScope InOrganization -FromMemberOf "Finance Team" -ApplyRightsProtectionCustomizationTemplate "Finance Department" -ApplyRightsProtectionTemplate Encrypt
    ```

1. 다음 cmdlet을 입력하여 변경 내용을 확인합니다.

    ```powershell
    Get-OMEConfiguration -Identity "Finance Department" | Format-List
    ```

1. PowerShell 창은 열어 둡니다.

경리부 직원이 외부 받는 사람에게 메시지를 보내면 사용자 지정 브랜딩 템플릿을 자동 적용하는 새 전송 규칙을 만들었습니다.

## 작업 5 - 사용자 지정 브랜딩 템플릿 테스트

새 사용자 지정 구성의 유효성을 검사하기 위해 경리팀 직원인 Lynne Robbins의 계정을 다시 사용해야 합니다.

1. 클라이언트 2 VM(LON-CL2)에 **lon-cl2\admin** 계정으로 다시 로그인합니다.

1. 웹 탭의 Outlook이 여전히 열려 있고 **Lynne Robbins**로 로그인되어 있어야 합니다.

1. Outlook의 왼쪽 상단 모서리에서 **새 메일**을 선택합니다.

1. **받는 사람** 필드에 테넌트 도메인에 없는 개인 또는 기타 타사 이메일 주소를 입력합니다. 

1. **주제 추가** 필드에 **재정 보고서**를 입력합니다.

1. 본문에 **비밀 재무 정보 **를 입력합니다.

1. **보내기**를 선택합니다.

1. 개인 이메일 계정에 로그인하여 **Lynne Robbins**가 보낸 메시지를 엽니다. 아래 이미지와 비슷하게 표시됩니다. **메시지 읽기**를 선택합니다.

    ![Lynne Robbins가 보낸 암호화된 샘플 전자 메일 ](../Media/EncryptedEmail.png)

1. 사용자 지정된 구성에서는 두 옵션을 모두 사용할 수 있으므로 소셜 ID가 활성화됩니다. **일회용 암호로 로그인**을 선택하여 일정 시간 동안만 사용할 수 있는 암호를 받습니다.

1. 개인 이메일로 돌아가서 **메시지를 보기 위한 일회용 암호**라는 제목의 메시지를 엽니다.

1. 암호를 복사하여 포털에 붙여넣고 **계속**을 선택합니다.

1. 사용자 지정 브랜딩이 적용되어 있는 암호화된 메시지를 검토합니다.

새로운 사용자 지정 템플릿을 성공적으로 테스트했습니다.
