---
title: 온라인 호스팅 지침
permalink: index.html
layout: home
ms.openlocfilehash: ceaf925c641179145a7a485e5474e02747815173
ms.sourcegitcommit: 53488624251b6cf8f79f2d1ff561e3f334764821
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/26/2022
ms.locfileid: "147694929"
---
# <a name="content-directory"></a>콘텐츠 디렉터리

다음은 각 랩 연습 및 데모의 하이퍼링크입니다.

## <a name="labs"></a>랩

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" %}
| 모듈 | 랩 |
| --- | --- | 
{% for activity in labs  %}| {{ activity.lab.module }} | [{{ activity.lab.title }}{% if activity.lab.type %} - {{ activity.lab.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

<!-- riswinto - 8/26/2022 - commenting out Demos. SC-400 does not have demos at the time of this comment

## Demos

{% assign demos = site.pages | where_exp:"page", "page.url contains '/Instructions/Demos'" %}
| Module | Demo |
| --- | --- | 
{% for activity in demos  %}| {{ activity.demo.module }} | [{{ activity.demo.title }}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
-->
