---
title: Informace o položkách ovládacího prvku strom | Dokumentace Microsoftu
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
ms.openlocfilehash: a61d6dbf2084288d6015e8fc2c08bfc2283d4ba4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391017"
---
# <a name="tree-control-item-information"></a>Informace o položkách ovládacího prvku strom

Strom ovládacích prvků ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) mají počet členských funkcí, které načítají informace o položkách ovládacího prvku. [GetItem](../mfc/reference/ctreectrl-class.md#getitem) členskou funkci načte některá nebo všechna data přidružená k položce. Tato data můžou obsahovat text položky, stavu, obrázky, počet podřízených položek a hodnotu 32-bit dat definované aplikací. K dispozici je také [SetItem](../mfc/reference/ctreectrl-class.md#setitem) funkce, která můžete nastavit některá nebo všechna data přidružená k položce.

[GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate), [getitemtext –](../mfc/reference/ctreectrl-class.md#getitemtext), [getitemdata –](../mfc/reference/ctreectrl-class.md#getitemdata), a [GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage) členské funkce načíst jednotlivé atributy položka. Každá z těchto funkcí má odpovídající funkci Set pro nastavení atributů položky.

[GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem) členskou funkci načte položku ovládacího prvku stromu, který nese Zadaný vztah s aktuální položkou. Tato funkce může načíst nadřazené položky, další nebo předchozí viditelné položky, první podřízené položky a tak dále. Existují také členské funkce pro procházení stromu: [načtení kořenové položky](../mfc/reference/ctreectrl-class.md#getrootitem), [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem), [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem), [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem), [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem), [GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem), [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem), [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem), [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem), a [GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem).

[GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect) načte členské funkce ohraničující rámeček pro položku ovládacího prvku stromu. [GetCount](../mfc/reference/ctreectrl-class.md#getcount) a [GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount) členské funkce načíst počet položek v ovládacím prvku strom a počet položek, které jsou nyní zobrazeny v okně Ovládací prvek stromu, v uvedeném pořadí. Můžete zajistit, že určité položky viditelné voláním [EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible) členskou funkci.

## <a name="see-also"></a>Viz také

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

