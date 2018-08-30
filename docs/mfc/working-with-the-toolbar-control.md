---
title: Práce s ovládacím prvkem panel nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e488d4b475cbc73f57bb90ccd081b6d490221d58
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202257"
---
# <a name="working-with-the-toolbar-control"></a>Práce s ovládacím prvkem panel nástrojů
Tento článek vysvětluje, jak můžete přistupovat [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) základní objekt [ctoolbar –](../mfc/reference/ctoolbar-class.md) mít větší kontrolu nad panely nástrojů. Toto je rozšířená.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Pro přístup k běžný ovládací prvek panelu nástrojů základní ctoolbar – objekt  
  
1.  Volání [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).  
  
 `GetToolBarCtrl` Vrátí odkaz na [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objektu. Můžete použít odkaz volat členské funkce třídy ovládacího prvku panel nástrojů.  
  
> [!CAUTION]
>  Při volání `CToolBarCtrl` **získat** funkce budou v bezpečí, buďte opatrní při volání **nastavit** funkce. Toto je rozšířená. Obvykle neměli byste potřebovat přístup k podkladové ovládací prvek panelu nástrojů.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací  
  
-   [Ovládací prvky (běžné ovládací prvky Windows)](../mfc/controls-mfc.md)  
  
-   [Principy panelů nástrojů](../mfc/toolbar-fundamentals.md)  
  
-   [Ukotvitelné a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)  
  
-   [Dynamicky změnu velikosti panelu nástrojů](../mfc/docking-and-floating-toolbars.md)  
  
-   [Popisy tlačítek na panelu nástrojů](../mfc/toolbar-tool-tips.md)  
  
-   [Aktualizace stavového řádku](../mfc/toolbar-tool-tips.md)  
  
-   [Zpracování oznámení popisů tlačítek](../mfc/handling-tool-tip-notifications.md)  
  
-   [Ctoolbar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) třídy  
  
-   [Zpracování oznámení o přizpůsobení](../mfc/handling-customization-notifications.md)  
  
-   [Více panelů nástrojů](../mfc/toolbar-fundamentals.md)  
  
-   [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)  
  
-   [Ovládací pruhy](../mfc/control-bars.md)  
  
 Obecné informace o použití běžných ovládacích prvků Windows najdete v tématu [běžné ovládací prvky](/windows/desktop/Controls/common-controls-intro).  
  
## <a name="see-also"></a>Viz také  
 [Implementace panelu nástrojů v prostředí MFC](../mfc/mfc-toolbar-implementation.md)

