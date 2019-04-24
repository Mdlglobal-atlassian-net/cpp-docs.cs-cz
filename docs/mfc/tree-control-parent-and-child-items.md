---
title: Nadřízené a podřízené položky ovládacího prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
ms.openlocfilehash: 2961009e3f1b21c3caacec001c53f5e52740dd67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181666"
---
# <a name="tree-control-parent-and-child-items"></a>Nadřízené a podřízené položky ovládacího prvku strom

Všechny položky v ovládacím prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) může mít seznam podřízených položek, které se volají, podřízené položky, které s ním spojená. Položka, která má jeden nebo více podřízených položek se nazývá nadřazenou položku. Podřízené položky se zobrazí pod její nadřazenou položku a odsazena označující, že je podřízená nadřazené. Položka, která nemá žádný nadřazený objekt je na nejvyšší úrovni hierarchie a je volána kořenovou položku.

V daném okamžiku stavu nadřazená položka seznamu podřízených položek můžete buď rozbalit nebo sbalit. Po rozbalení stav podřízených položek se zobrazí pod nadřazené položky. Když je sbalený, podřízené položky se nezobrazují. V seznamu automaticky přepíná mezi stavy rozšíření a sbalené při poklepání nadřazené položky, nebo pokud má nadřazená **TVS_HASBUTTONS** styl, když uživatel klikne na tlačítko přidružené k nadřazené položky. Můžete rozbalit nebo sbalit podřízených položek pomocí aplikace [Rozbalit](../mfc/reference/ctreectrl-class.md#expand) členskou funkci.

Přidání položky do ovládacího prvku stromu voláním [metody InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) členskou funkci. Tato funkce vrací popisovač **HTREEITEM** typ, který jednoznačně identifikuje položku. Při přidávání položky, je nutné zadat popisovač nová položka nadřazená položka. Pokud zadáte **NULL** nebo **TVI_ROOT** nemusejí popisovač nadřazené položky v [TVINSERTSTRUCT](/windows/desktop/api/commctrl/ns-commctrl-tagtvinsertstructa) struktury nebo *hParent* parametr je položka přidána jako kořenovou položku.

Odesílá se ovládacím prvkem strom [TVN_ITEMEXPANDING](/windows/desktop/Controls/tvn-itemexpanding) zprávy oznámení, když nadřazená položka seznamu podřízených položek se chystá rozbalená nebo sbalená. Oznámení vám dává příležitost, aby se zabránilo změně nebo nastavit atributy nadřazené položky, které závisí na stavu seznamu podřízených položek. Po změně stavu v seznamu, odešle do ovládacího prvku stromu [TVN_ITEMEXPANDED](/windows/desktop/Controls/tvn-itemexpanded) zprávy oznámení.

Po rozbalení seznamu podřízených položek odsadí relativně k nadřazené položky. Můžete nastavit velikost odsazení pomocí [SetIndent](../mfc/reference/ctreectrl-class.md#setindent) členská funkce nebo načíst aktuální velikost pomocí [GetIndent](../mfc/reference/ctreectrl-class.md#getindent) členskou funkci.

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
