---
title: Použití popisů tlačítek v objektu CStatusBarCtrl | Microsoft Docs
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
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 323f2861da9fcc498e34792c30c763b4dffb2fd1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385960"
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

