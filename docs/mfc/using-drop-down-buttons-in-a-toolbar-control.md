---
title: Použití rozevíracích tlačítek v ovládacím prvku panel nástrojů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
dev_langs:
- C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e76db0bacd7984c97fd8e2696b3543f6e9bf66b
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953240"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Použití rozevíracích tlačítek v ovládacím prvku panel nástrojů
Kromě standardní tlačítek panelu nástrojů můžete taky nechat rozevíracích tlačítek. Rozevírací tlačítko je obvykle indikován přítomnosti připojené dolů šipka.  
  
> [!NOTE]
>  Šipku dolů připojené se zobrazí jenom v případě, že byla nastavena TBSTYLE_EX_DRAWDDARROWS rozšířený styl.  
  
 Když uživatel klikne na tuto šipku (nebo na tlačítko samostatně, pokud je k dispozici žádné šipku), tbn_dropdown – oznámení posílá nadřazeného ovládacího prvku panel nástrojů. Potom můžete zpracovat toto oznámení a zobrazit místní nabídky; Podobně jako u chování aplikace Internet Explorer.  
  
 Následující postup ukazuje, jak implementovat tlačítka panelu nástrojů rozevírací seznam s místní nabídky:  
  
### <a name="to-implement-a-drop-down-button"></a>K implementaci rozevírací tlačítko  
  
1.  Jednou vaše `CToolBarCtrl` objekt byl vytvořen, nastavte styl TBSTYLE_EX_DRAWDDARROWS, pomocí následujícího kódu:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]  
  
2.  Nastavit styl TBSTYLE_DROPDOWN pro všechny nové ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) nebo [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) nebo existující ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) tlačítka, které se bude rozevíracích tlačítek. Následující příklad ukazuje, úprava existující tlačítka na `CToolBarCtrl` objektu:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]  
  
3.  Obslužná rutina tbn_dropdown – přidejte do nadřazené třídy objektu panelu nástrojů.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]  
  
4.  V nové obslužnou rutinu zobrazte příslušné místní nabídky. Následující kód ukazuje jedno z těchto metod:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

