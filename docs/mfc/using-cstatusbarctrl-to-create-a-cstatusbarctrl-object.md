---
title: "Použití třídy CStatusBarCtrl k vytvoření objektu CStatusBarCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CStatusBarCtrl
dev_langs: C++
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cf62df91b2952240e460c722c46c0221fb491227
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Použití třídy CStatusBarCtrl k vytvoření objektu CStatusBarCtrl
Tady je příklad typické použití [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):  
  
### <a name="to-use-a-status-bar-control-with-parts"></a>Použití ovládacího prvku panel stav s částmi  
  
1.  Vytvořit `CStatusBarCtrl` objektu.  
  
2.  Volání [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) Pokud chcete nastavit minimální výšku ovládacích prvků panelu Stav pro kreslení oblasti.  
  
3.  Volání [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) nastavit barvu pozadí ovládacího panelu stavu.  
  
4.  Volání [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) nastavit počet částí ve stavovém řádku řízení a souřadnice pravého okraje jednotlivých součástí.  
  
5.  Volání [SetText –](../mfc/reference/cstatusbarctrl-class.md#settext) nastavit text v dané součástí ovládacích prvků panelu stavu. Zpráva by způsobila neplatnost část ovládací prvek, který změnil způsobuje zobrazit nového textu přijetí ovládacího prvku další `WM_PAINT` zprávy.  
  
 V některých případech stavový řádek stačí k zobrazení na řádku textu. V takovém případě se dovolat do [setsimple –](../mfc/reference/cstatusbarctrl-class.md#setsimple). Tento ovládací prvek panelu Stav umístí do "jednoduchý" režimu, který zobrazuje jeden řádek textu.  
  
## <a name="see-also"></a>Viz také  
 [Použití třídy CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)
