---
title: Informace o položkách ovládacího prvku strom | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 724e9d7c4e0ee7db80f024c30e363612cb40fed1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385362"
---
# <a name="tree-control-item-information"></a>Informace o položkách ovládacího prvku strom
Ovládací prvky stromové struktury ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) s počtem členské funkce, které načtení informací o položky v ovládacím prvku. [GetItem](../mfc/reference/ctreectrl-class.md#getitem) – členská funkce načte některá nebo všechna data související s položku. Tato data můžou zahrnovat text položky, stavu, Image, počet podřízených položek a hodnotu 32-bit dat definované aplikací. K dispozici je také [SetItem](../mfc/reference/ctreectrl-class.md#setitem) funkce, která můžete nastavit některá nebo všechna data související s položku.  
  
 [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate), [getitemtext –](../mfc/reference/ctreectrl-class.md#getitemtext), [getitemdata –](../mfc/reference/ctreectrl-class.md#getitemdata), a [GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage) členské funkce načíst jednotlivé atributy položka. Každá z těchto funkcí má odpovídající funkce sady pro nastavení atributů položky.  
  
 [GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem) – členská funkce načte položku ovládacího prvku strom nenese Zadaný vztah s aktuální položkou. Tato funkce může načíst nadřazené položky, položky zobrazené další nebo předchozí, první podřízenou položku a tak dále. Existují také členské funkce procházení stromu: [načtení kořenové položky](../mfc/reference/ctreectrl-class.md#getrootitem), [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem), [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem), [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem), [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem), [GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem), [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem), [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem), [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem), a [GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem).  
  
 [GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect) – členská funkce načte ohraničující obdélník pro položku ovládacího prvku strom. [GetCount](../mfc/reference/ctreectrl-class.md#getcount) a [GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount) členské funkce načíst počet položek v ovládacím prvku stromu a počet položek, které jsou aktuálně viditelné v ovládacím prvku stromu okno, v uvedeném pořadí. Můžete zajistit, že určité položky viditelné voláním [EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

