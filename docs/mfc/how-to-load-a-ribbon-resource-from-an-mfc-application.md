---
title: 'Postupy: Načtení prostředku pásu karet z aplikace MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: 14ba37952d6f8849c51b36901a6bc17404f938e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515151"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Postupy: Načtení prostředku pásu karet z aplikace MFC

Chcete-li použít prostředky pásu karet v aplikaci, přizpůsobit aplikaci pro načtení prostředku pásu karet.

### <a name="to-load-a-ribbon-resource"></a>K načtení prostředku pásu karet

1. Deklarovat `Ribbon Control` objekt `CMainFrame` třídy.

```
    CMFCRibbonBar m_wndRibbonBar;
```

1. V `CMainFrame::OnCreate`, vytvořit a inicializovat ovládací prvek pásu karet.

```
    if (!m_wndRibbonBar.Create (this))
{
    return -1;
}

    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))
{
    return -1;
}
```

## <a name="see-also"></a>Viz také

[Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)

