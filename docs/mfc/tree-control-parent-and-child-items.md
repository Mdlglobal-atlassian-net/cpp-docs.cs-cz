---
title: Ovládací prvek nadřazené a podřízené položky strom | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 260cbf640f6c57e4b145d01e8f883025a4dc6507
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="tree-control-parent-and-child-items"></a>Nadřízené a podřízené položky ovládacího prvku strom
Všechny položky v ovládacím prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) může mít seznam podřízených položek, které se nazývají podřízené položky, které s ním spojená. Položku, která obsahuje jednu nebo více podřízených položek se nazývá nadřazené položky. Podřízené položky se zobrazí pod její nadřazené položky a odsazeno se indikovat, že podřízená nadřazené. Položku, která nemá nadřazený je na nejvyšší úrovni hierarchie a je volána kořenovou položku.  
  
 V každém okamžiku stav nadřazené položky seznamu podřízené položky můžete buď rozbalit nebo sbalit. Pokud je stav rozbalen, podřízené položky se zobrazí pod nadřazené položky. Když sbalena, nejsou zobrazeny podřízené položky. V seznamu automaticky přepíná mezi stavy rozšířené a sbalené při poklepání nadřazené položky nebo, pokud má nadřazený **TVS_HASBUTTONS** styl, když uživatel klikne na tlačítko přidružené k nadřazené položce. Aplikace můžete rozbalit nebo sbalit podřízené položky pomocí [rozbalte](../mfc/reference/ctreectrl-class.md#expand) – členská funkce.  
  
 Přidání položky do ovládacího prvku strom voláním [metody InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) – členská funkce. Funkce vrátí hodnotu popisovače **HTREEITEM** typu, který jednoznačně identifikuje položku. Při přidávání položky, je nutné zadat popisovač novou položku nadřazené položky. Pokud zadáte **NULL** nebo **TVI_ROOT** hodnotu namísto popisovač nadřazené položky v [TVINSERTSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb773452) struktura nebo `hParent` parametr, položka je přidána jako kořenové položka.  
  
 Odešle ovládacím prvkem strom [TVN_ITEMEXPANDING](http://msdn.microsoft.com/library/windows/desktop/bb773537) oznámení po chystáte rozbalit nebo sbalit seznam nadřazené položky podřízené položky. Oznámení vám dává příležitost, aby se změny, nebo nastavit atributy nadřazené položky, které závisí na stavu seznam podřízené položky. Po změně stavu v seznamu, odešle ovládací prvek stromu [TVN_ITEMEXPANDED](http://msdn.microsoft.com/library/windows/desktop/bb773533) oznámení.  
  
 Pokud je seznam podřízené položky rozbalen, je odsazeny relativně k nadřazené položky. Velikost odsazení lze nastavit pomocí [SetIndent](../mfc/reference/ctreectrl-class.md#setindent) – členská funkce nebo načtení aktuální velikost pomocí [GetIndent](../mfc/reference/ctreectrl-class.md#getindent) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

