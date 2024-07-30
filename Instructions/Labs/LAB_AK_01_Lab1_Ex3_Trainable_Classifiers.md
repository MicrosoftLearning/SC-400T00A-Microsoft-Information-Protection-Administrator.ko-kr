---
lab:
  title: 연습 3 - 학습 가능한 분류자 관리
  module: Module 1 - Implement Information Protection
---

# 랩 1 - 연습 3 - 학습 가능한 분류자 관리

Contoso Ltd.는 '영업 및 마케팅' SharePoint 사이트에 저장된 재무 문서 및 보고서가 제대로 분류되었는지 확인해야 합니다. 이렇게 하려면 이러한 파일을 인식하고 레이블을 지정하는 학습 가능한 분류자를 만들어야 합니다.

## 작업 1 – 학습 가능한 분류자 만들기

이 작업에서는 테넌트에서 학습 가능한 분류자를 활성화하여 사용자 지정 분류자를 만들 수 있습니다.

1. 클라이언트 1 VM(LON-CL1)에는 여전히 **LON-CL1\admin** 계정으로 그리고 Microsoft 365에는 **Joni Sherman**으로 로그인되어 있는 상태여야 합니다.

1. **Microsoft Edge**에서 **`https://compliance.microsoft.com`** 으로 이동합니다.

1. 왼쪽 탐색 창에서 **데이터 분류**를 확장한 다음 **분류자**를 선택합니다.

1. **분류자** 페이지에서 **학습 가능한 분류자** 탭이 이미 선택되어 있어야 합니다.

2. **+ 학습 가능한 분류자 만들기**를 선택하여 새 분류자를 만듭니다.

1. **학습 가능한 분류자 이름 지정 및 설명** 페이지에서 다음 정보를 입력합니다.

    - **이름**: `Contoso Company Data`
    - **설명**: `Trainable classifier for company data produced and stored by Contoso Ltd.`

1. **다음**을 선택합니다.

1. **긍정적인 샘플 콘텐츠 출처**에서 **+ 사이트 선택**을 선택합니다.

1. 오른쪽에 있는 **SharePoint 사이트 추가** 플라이아웃 페이지에서 다음 SharePoint 사이트를 선택합니다.

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

<!---
## Task 3 – Publish a trainable classifier (optional lab task)

After the new trainable classifier was created and the initial analysis of the documents and files is done, the manual training process needs to be performed. In this task, Joni will start the calibration of the classifier to achieve the required accuracy for publishing.

1. You should still be logged into your Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In your browser window, you are in the Microsoft Purview portal at **Data classification** in the **Trainable classifiers** tab.

1. Select the trainable classifier with the name **Contoso Company Data** of the type **Custom** to open the detailed settings.

1. Review the **Details** tab on the right side, including the source site for the classifier, the number of processed items and the **Status**, which is in **Need test items**.

1. To add items for training the classifier, select **Add items to test** to open the right side selection pane.

1. In the **Choose sites with items to test** pane, select **+ Choose sites**.

1. Select the following SharePoint sites:

    - **Communication site**
    - **News @ Contoso**
    - **Contoso Web 1**
    - **Brand**
    - **Digital Initiative Public Relations**
    - **Work @ Contoso**
    - **Sales and Marketing**
    - **Contoso Landings**
    - **Mark 8 Project Team**
    - **HR**
    - **Operations**
    - **Retail**
    - **PointPublishing Hub Site**
    - **Team Site**
    - **Leadership Team**
    - **Community**
    - **Give @ Contoso**
    - **Benefits @ Contoso**
    - **Learn @ Contoso**
    - **Campaigns - Events**

1. Select **Add**.

1. Wait until the sites are shown in the list and select **Add**.

1. When the **Overview** section is updated, a new tab is shown in the top of the window.

1. Select **Tested items to review** from the top pane.

1. It will take between 15 to 30 minutes until first results are ready for review. Refresh the browser window if no files are shown in the list, until data is available.

1. Select the name of the first file from the list to open the preview window.

1. When the **Prediction** row is equal to **Match**, the file was identified as a match for the classifier. Below the preview window, a message **We predict this item "matched" this classifier.** is shown. Select **Match** to approve the automatic classification.

1. When the **Prediction** row is equal to **Not a match**, the file was identified not as a match for the classifier. Below the preview window, a message **We predict this item "does not match" this classifier.** is shown. Select **Not a match** to approve the automatic classification.

1. Proceed with all items in the list and approve the automatic classification. After all items have been reviewed, select **Overview** from the top pane and **Tested items to review** again, to load the next set of items for review.

1. For each 30 reviewed items an **Auto-retrain performed** window is shown. Select **OK** and proceed with the previous steps, until no items for review are left.

1. After sufficient items are reviewed, the **Publish** button in the upper right gets available. Select it as soon it is available.

1. In the **Publish classifier** window, select **Yes** to publish the classifier.

1. When the right side pane with **Your trainable classifier has been published** is displayed, the trainable classifier was successfully published.

1. Close the right side pane with the **X** in the upper right.

1. Back at the main site, the custom classifier was moved to **Published** and the **Status** has been changed to **Ready to use**.

1. Leave the browser window open.

You have successfully created, trained, and published a custom trainable classifier that matches the files stored on the existing SharePoint sites of Contoso Ltd.
