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
ms.openlocfilehash: 9cce98e4a3b3ffd506607529b9fea6f0c1114cc3
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951263"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Použití popisů tlačítek v objektu CStatusBarCtrl
Chcete-li povolit popisy pro ovládací prvek panelu Stav, vytvořte `CStatusBarCtrl` objekt s SBT_TOOLTIPS styl.  
  
> [!NOTE]
>  Pokud používáte `CStatusBar` objekt, který chcete implementovat stavového řádku, použijte `CStatusBar::CreateEx` funkce. Umožňuje vám určit další styly pro vložený `CStatusBarCtrl` objektu.  
  
 Jednou `CStatusBarCtrl` objektu byla úspěšně vytvořena, použijte [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) a [CStatusBarCtrl::GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) nastavit a načíst text tip pro konkrétní podokně.  
  
 Jakmile je nastavená popis tlačítka, se zobrazí jenom v případě, že část obsahuje ikonu a žádný text, nebo pokud veškerý text nelze zobrazit v této části. Typy nástrojů nejsou v jednoduchém režimu podporovány.  
  
## <a name="see-also"></a>Viz také  
 [Použití třídy CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

