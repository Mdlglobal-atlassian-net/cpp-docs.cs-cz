---
title: "Přidávání sloupců do ovládacího prvku (zobrazení sestavy) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a4c1676db440b003d0c0914b12b6c5b8ba08986a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="adding-columns-to-the-control-report-view"></a>Přidávání sloupců do ovládacího prvku (zobrazení sestavy)
> [!NOTE]
>  Následující postup platí pro buď [CListView](../mfc/reference/clistview-class.md) nebo [CListCtrl](../mfc/reference/clistctrl-class.md) objektu.  
  
 Když je ovládací prvek seznamu v zobrazení sestavy, jsou zobrazeny sloupce, poskytuje metodu pro uspořádání různých podřízených položek každé položky ovládací prvek seznamu. Tato organizace je implementováno s souvislosti mezi sloupci v ovládacím prvku seznamu a přidružené podpoložek položky ovládací prvek seznamu. Další informace o podřízených položek najdete v tématu [přidávání položek do ovládacího prvku](../mfc/adding-items-to-the-control.md). Zobrazení podrobností v systému Windows 95 a Průzkumníka Windows 98 poskytuje příklad ovládacího prvku seznam v zobrazení sestavy. První sloupec obsahuje složka, soubor ikony a popisky. Ostatních sloupců seznamu velikost souboru, typu souboru, datum poslední změny a tak dále.  
  
 I když sloupce lze přidat do ovládacího prvku seznam kdykoli, sloupce, které jsou viditelné pouze v případě, že má ovládací prvek `LVS_REPORT` bit stylu zapnuté.  
  
 Každý sloupec má položku přidružená záhlaví (najdete v části [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) objekt, který označuje sloupci a umožňuje uživatelům měnit velikost sloupce.  
  
 Pokud vaše ovládací prvek seznamu podporuje zobrazení sestavy, budete muset přidat sloupec pro každý možné podpoložek v položce seznamu ovládacího prvku. Příprava přidat sloupec [LV_COLUMN](http://msdn.microsoft.com/library/windows/desktop/bb774743) struktury a pak provedením volání [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Po přidání nezbytné sloupců (někdy označované jako položky hlavičky), můžete změnit jejich pořadí pomocí členských funkcí a styly patřící do ovládacího prvku záhlaví embedded. Další informace najdete v tématu [pořadí položek v ovládacím prvku záhlaví](../mfc/ordering-items-in-the-header-control.md).  
  
> [!NOTE]
>  Pokud ovládacího prvku seznam je vytvořen s **LVS_NOCOLUMNHEADER** styl, pokusy o sloupce k vložení budou ignorovány.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)
