---
title: "Metody vytváření popisů tlačítek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2d38bd76ff5c8d06daf474cf1c1dcc0286183bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="methods-of-creating-tool-tips"></a>Metody vytváření popisů tlačítek
Knihovna MFC poskytuje tři třídy k vytváření a správě nástroj ovládací prvek tlačítka: [CWnd](../mfc/reference/cwnd-class.md), [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md), [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) a [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md). Nástroj tip členské funkce ve tyto třídy zabalit běžné ovládacího prvku Windows rozhraní API. Třída `CToolBarCtrl` a třída `CToolTipCtrl` jsou odvozeny od třídy `CWnd`.  
  
 `CWnd`poskytuje čtyři členské funkce k vytváření a správě popisy: [EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips), [CancelToolTips](../mfc/reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](../mfc/reference/cwnd-class.md#filtertooltipmessage), a [ Ontoolhittest –](../mfc/reference/cwnd-class.md#ontoolhittest). Najdete v těchto jednotlivých členských funkcí pro další informace o způsobu implementace popisy.  
  
 Pokud vytvoříte nástrojů pomocí `CToolBarCtrl`, můžete implementovat popisy pro tohoto panelu nástrojů přímo pomocí následující členské funkce: [GetToolTips](../mfc/reference/ctoolbarctrl-class.md#gettooltips) a [SetToolTips](../mfc/reference/ctoolbarctrl-class.md#settooltips). Jednotlivými členy s těmito funkcemi a [zpracování oznámení popisů Tip](../mfc/handling-tool-tip-notifications.md) Další informace o způsobu implementace popisy.  
  
 `CToolTipCtrl` Třída poskytuje funkce Windows ovládacího prvku běžné tip nástroj. Ovládací prvek popisek jednotný nástroj může poskytovat informace pro více než jeden nástroj. Nástroj je buď v časovém období, jako je například podřízeného okna nebo ovládací prvek nebo definované aplikací obdélníkovou oblast v rámci časového období klientské oblasti. [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md) třída odvozená z `CToolTipCtrl` a poskytuje další vizuální styly a funkce.  
  
## <a name="see-also"></a>Viz také  
 [Použití objektu CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

