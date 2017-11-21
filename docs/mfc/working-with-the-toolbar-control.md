---
title: "Práce s ovládacím prvkem panel nástrojů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e0d7c3709667b53f03e63463cbfbda997e265c3b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="working-with-the-toolbar-control"></a>Práce s ovládacím prvkem panel nástrojů
Tento článek vysvětluje, jak se dostanete [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) základní objekt [ctoolbar –](../mfc/reference/ctoolbar-class.md) pro větší kontrolu nad panely nástrojů. To je rozšířená.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Pro přístup k běžného ovládacího prvku panel nástrojů základní vaší ctoolbar – objekt  
  
1.  Volání [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).  
  
 `GetToolBarCtrl`Vrátí odkaz na [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objektu. Odkaz na můžete volat funkce člena třídy ovládacího prvku panel nástrojů.  
  
> [!CAUTION]
>  Při volání `CToolBarCtrl` **získat** funkce je bezpečné, buďte opatrní při volání **nastavit** funkce. To je rozšířená. Za normálních okolností by neměl potřebujete přístup k podkladové ovládací prvek panelu nástrojů.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Ovládací prvky (běžné ovládací prvky Windows)](../mfc/controls-mfc.md)  
  
-   [Principy panelů nástrojů](../mfc/toolbar-fundamentals.md)  
  
-   [Ukotvitelné a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)  
  
-   [Dynamicky Změna velikosti panelu nástrojů](../mfc/docking-and-floating-toolbars.md)  
  
-   [Popisy tlačítek panelu nástrojů](../mfc/toolbar-tool-tips.md)  
  
-   [Průběžné aktualizace stavového řádku](../mfc/toolbar-tool-tips.md)  
  
-   [Zpracování oznámení popisů tlačítek](../mfc/handling-tool-tip-notifications.md)  
  
-   [Ctoolbar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) třídy  
  
-   [Zpracování oznámení o přizpůsobení](../mfc/handling-customization-notifications.md)  
  
-   [Více panelů nástrojů](../mfc/toolbar-fundamentals.md)  
  
-   [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)  
  
-   [Ovládací pruhy](../mfc/control-bars.md)  
  
 Obecné informace o použití běžných ovládacích prvků Windows najdete v tématu [běžné ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb775493).  
  
## <a name="see-also"></a>Viz také  
 [Implementace panelu nástrojů v MFC](../mfc/mfc-toolbar-implementation.md)

