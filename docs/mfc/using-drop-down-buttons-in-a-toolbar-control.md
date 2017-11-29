---
title: "Použití rozevíracích tlačítek v ovládacím prvku panel nástrojů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
dev_langs: C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 273c73ebfcda13217185b0f1f651229d299632c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Použití rozevíracích tlačítek v ovládacím prvku panel nástrojů
Kromě standardní tlačítek panelu nástrojů můžete taky nechat rozevíracích tlačítek. Rozevírací tlačítko je obvykle indikován přítomnosti připojené dolů šipka.  
  
> [!NOTE]
>  Šipku dolů připojené se zobrazí jenom v případě `TBSTYLE_EX_DRAWDDARROWS` rozšířené styl byla nastavena.  
  
 Když uživatel klikne na tuto šipku (nebo na tlačítko samostatně, pokud je k dispozici žádné šipku), `TBN_DROPDOWN` nadřazeného ovládacího prvku panel nástrojů je odeslána zpráva oznámení. Potom můžete zpracovat toto oznámení a zobrazit místní nabídky; Podobně jako u chování aplikace Internet Explorer.  
  
 Následující postup ukazuje, jak implementovat tlačítka panelu nástrojů rozevírací seznam s místní nabídky:  
  
### <a name="to-implement-a-drop-down-button"></a>K implementaci rozevírací tlačítko  
  
1.  Jednou vaše `CToolBarCtrl` objekt byl vytvořen, nastavte `TBSTYLE_EX_DRAWDDARROWS` styl, pomocí následujícího kódu:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]  
  
2.  Nastavte `TBSTYLE_DROPDOWN` styl pro všechny nové ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) nebo [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) nebo existující ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) tlačítka, které se bude rozevíracích tlačítek. Následující příklad ukazuje, úprava existující tlačítka na `CToolBarCtrl` objektu:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]  
  
3.  Přidat `TBN_DROPDOWN` obslužná rutina nadřazené třídy objektu panelu nástrojů.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]  
  
4.  V nové obslužnou rutinu zobrazte příslušné místní nabídky. Následující kód ukazuje jedno z těchto metod:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)
