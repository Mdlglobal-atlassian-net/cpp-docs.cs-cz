---
title: Použití třídy CStatusBarCtrl k vytvoření objektu CStatusBarCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb378bba1505f8bbc3739c070d52abe9ef4f8afc
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953822"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Použití třídy CStatusBarCtrl k vytvoření objektu CStatusBarCtrl
Tady je příklad typické použití [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):  
  
### <a name="to-use-a-status-bar-control-with-parts"></a>Použití ovládacího prvku panel stav s částmi  
  
1.  Vytvořit `CStatusBarCtrl` objektu.  
  
2.  Volání [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) Pokud chcete nastavit minimální výšku ovládacích prvků panelu Stav pro kreslení oblasti.  
  
3.  Volání [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) nastavit barvu pozadí ovládacího panelu stavu.  
  
4.  Volání [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) nastavit počet částí ve stavovém řádku řízení a souřadnice pravého okraje jednotlivých součástí.  
  
5.  Volání [SetText –](../mfc/reference/cstatusbarctrl-class.md#settext) nastavit text v dané součástí ovládacích prvků panelu stavu. Zpráva by způsobila neplatnost část ovládací prvek, který změnil způsobuje ovládacího prvku vedle obdrží zprávu WM_PAINT zobrazit nového textu.  
  
 V některých případech stavový řádek stačí k zobrazení na řádku textu. V takovém případě se dovolat do [setsimple –](../mfc/reference/cstatusbarctrl-class.md#setsimple). Tento ovládací prvek panelu Stav umístí do "jednoduchý" režimu, který zobrazuje jeden řádek textu.  
  
## <a name="see-also"></a>Viz také  
 [Použití třídy CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

