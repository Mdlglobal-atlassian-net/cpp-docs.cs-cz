---
title: 'Postupy: načtení prostředku pásu karet z aplikace knihovny MFC | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1643989a96a9003847fb53de624bff12cd51cd88
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434286"
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

