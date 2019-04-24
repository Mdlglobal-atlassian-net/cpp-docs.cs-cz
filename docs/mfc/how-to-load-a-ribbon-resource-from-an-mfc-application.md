---
title: 'Postupy: Načtení prostředku pásu karet z aplikace knihovny MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: b7691d4168101209b0e2d2500012a2b4a8e47788
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160325"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Postupy: Načtení prostředku pásu karet z aplikace knihovny MFC

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

## <a name="see-also"></a>Viz také:

[Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)
