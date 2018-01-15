---
title: "Použití popisů tlačítek v objektu CStatusBarCtrl | Microsoft Docs"
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
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf522d17d8abfc4b8dbf53baa24255ab23cfa621
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Použití popisů tlačítek v objektu CStatusBarCtrl
Chcete-li povolit popisy pro ovládací prvek panelu Stav, vytvořte `CStatusBarCtrl` objektu s **SBT_TOOLTIPS** styl.  
  
> [!NOTE]
>  Pokud používáte `CStatusBar` objekt, který chcete implementovat stavového řádku, použijte `CStatusBar::CreateEx` funkce. Umožňuje vám určit další styly pro vložený **CStatusBarCtrl** objektu.  
  
 Jednou `CStatusBarCtrl` objektu byla úspěšně vytvořena, použijte [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) a [CStatusBarCtrl::GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) nastavit a načíst text tip pro konkrétní podokně.  
  
 Jakmile je nastavená popis tlačítka, se zobrazí jenom v případě, že část obsahuje ikonu a žádný text, nebo pokud veškerý text nelze zobrazit v této části. Typy nástrojů nejsou v jednoduchém režimu podporovány.  
  
## <a name="see-also"></a>Viz také  
 [Použití třídy CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

