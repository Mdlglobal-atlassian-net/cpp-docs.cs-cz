---
title: Nadřízené a podřízené položky ovládacího prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
ms.openlocfilehash: 5a02194ccef8eca81971bb4e8ae24d859e578bcc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513970"
---
# <a name="tree-control-parent-and-child-items"></a>Nadřízené a podřízené položky ovládacího prvku strom

Každá položka v ovládacím prvku stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) může mít seznam podpoložek, které se nazývají podřízené položky, které jsou k ní přidruženy. Položka, která má jednu nebo více podřízených položek, se nazývá nadřazená položka. Podřízená položka je zobrazena pod svou nadřazenou položkou a je odsazena tak, aby označovala podřízenou položku nadřazené. Položka, která nemá nadřazenou položku, je na vrcholu hierarchie a nazývá se kořenová položka.

V jednom okamžiku může být stav seznamu podřízených položek nadřazeného objektu rozbalen nebo sbalen. Když je stav rozbalený, podřízené položky se zobrazí pod nadřazenou položkou. Když je sbalený, podřízené položky nejsou zobrazeny. Seznam se automaticky přepíná mezi rozbaleným a sbaleným stavem, když uživatel dvakrát klikne na nadřazenou položku, nebo pokud má nadřazený styl **TVS_HASBUTTONS** , když uživatel klikne na tlačítko přidružené k nadřazené položce. Aplikace může rozbalit nebo sbalit podřízené položky pomocí funkce [Rozbalit](../mfc/reference/ctreectrl-class.md#expand) členskou funkci.

Přidáte položku do ovládacího prvku strom voláním členské funkce [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) . Tato funkce vrací popisovač typu **hTreeItem** , který jednoznačně identifikuje položku. Při přidávání položky je nutné zadat popisovač nadřazené položky nové položky. Pokud zadáte hodnotu **null** nebo hodnotu **TVI_ROOT** namísto popisovače nadřazené položky ve struktuře [TVINSERTSTRUCT](/windows/win32/api/commctrl/ns-commctrl-tvinsertstructw) nebo parametru *hParent* , položka se přidá jako kořenová položka.

Ovládací prvek stromu pošle zprávu oznámení [TVN_ITEMEXPANDING](/windows/win32/Controls/tvn-itemexpanding) , když se chystá rozšíření nebo sbalení seznamu podřízených položek nadřazené položky. Oznámení vám poskytne možnost zabránit změně nebo nastavení atributů nadřazené položky, která závisí na stavu seznamu podřízených položek. Po změně stavu seznamu pošle ovládací prvek strom zprávu s oznámením [TVN_ITEMEXPANDED](/windows/win32/Controls/tvn-itemexpanded) .

Když se rozbalí seznam podřízených položek, odsadí se vzhledem k nadřazené položce. Můžete nastavit velikost odsazení pomocí členské funkce [SetIndent](../mfc/reference/ctreectrl-class.md#setindent) nebo načíst aktuální množství pomocí členské funkce getodsazení. [](../mfc/reference/ctreectrl-class.md#getindent)

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
