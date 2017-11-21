---
title: "Vytváření v měsíci v ovládacím prvku Kalendář | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7ad088f67431af58a81dc06d5b0f3352a844299e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-the-month-calendar-control"></a>Vytvoření ovládacího prvku měsíční kalendář
Vytváření ovládací prvek měsíční kalendář závisí na tom, jestli jsou pomocí ovládacího prvku v dialogovém okně nebo jeho vytváření v okně nondialog.  
  
### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>K použití přímo v dialogovém okně CMonthCalCtrl  
  
1.  V editoru dialogového okna přidáte ovládací prvek měsíční kalendář vaše dialogu šablony prostředků. Zadejte své ID ovládacího prvku.  
  
2.  Zadejte všechny styly potřeby pomocí dialogové okno Vlastnosti ovládací prvek měsíční kalendář.  
  
3.  Použití [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidání členské proměnné typu [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md) s vlastností ovládacího prvku. Tento člen mohou využít k volání `CMonthCalCtrl` členské funkce.  
  
4.  Použijte okno Vlastnosti pro mapování obslužné rutiny funkce ve třídě dialog pro všechna oznámení ovládací prvek měsíční kalendář zpráv, které můžete potřebovat pro zpracování (viz [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md)).  
  
5.  V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), nastavení pro všechny další stylů `CMonthCalCtrl` objektu.  
  
### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>V okně nondialog používat CMonthCalCtrl  
  
1.  Definování ovládacího prvku ve třídě zobrazení nebo okno.  
  
2.  Volání ovládacího prvku [vytvořit](../mfc/reference/cmonthcalctrl-class.md#create) člen funkce, které by mohly mít v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), pravděpodobně časná jako nadřazeného okna [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkce obslužné rutiny (Pokud jste vytvoření podtřídy ovládacího prvku). Nastavení stylů pro ovládací prvek.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

