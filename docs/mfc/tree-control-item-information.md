---
title: "Informace o položkách ovládacího prvku strom | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 16e4a707c4bc1f0fde76ab3a146424d2d34d5ec8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-item-information"></a>Informace o položkách ovládacího prvku strom
Ovládací prvky stromové struktury ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) s počtem členské funkce, které načtení informací o položky v ovládacím prvku. [GetItem](../mfc/reference/ctreectrl-class.md#getitem) – členská funkce načte některá nebo všechna data související s položku. Tato data můžou zahrnovat text položky, stavu, Image, počet podřízených položek a hodnotu 32-bit dat definované aplikací. K dispozici je také [SetItem](../mfc/reference/ctreectrl-class.md#setitem) funkce, která můžete nastavit některá nebo všechna data související s položku.  
  
 [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate), [getitemtext –](../mfc/reference/ctreectrl-class.md#getitemtext), [getitemdata –](../mfc/reference/ctreectrl-class.md#getitemdata), a [GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage) členské funkce načíst jednotlivé atributy položka. Každá z těchto funkcí má odpovídající funkce sady pro nastavení atributů položky.  
  
 [GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem) – členská funkce načte položku ovládacího prvku strom nenese Zadaný vztah s aktuální položkou. Tato funkce může načíst nadřazené položky, položky zobrazené další nebo předchozí, první podřízenou položku a tak dále. Existují také členské funkce procházení stromu: [načtení kořenové položky](../mfc/reference/ctreectrl-class.md#getrootitem), [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem), [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem), [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem), [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem), [GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem), [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem), [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem), [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem), a [GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem).  
  
 [GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect) – členská funkce načte ohraničující obdélník pro položku ovládacího prvku strom. [GetCount](../mfc/reference/ctreectrl-class.md#getcount) a [GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount) členské funkce načíst počet položek v ovládacím prvku stromu a počet položek, které jsou aktuálně viditelné v ovládacím prvku stromu okno, v uvedeném pořadí. Můžete zajistit, že určité položky viditelné voláním [EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

