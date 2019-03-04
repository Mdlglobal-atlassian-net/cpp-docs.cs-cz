---
title: Operace přetažení u ovládacího prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: c7febeec513d8004df2bd1cc42e4e97e027e9f17
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286306"
---
# <a name="tree-control-drag-and-drop-operations"></a>Operace přetažení u ovládacího prvku strom

Ovládací prvek stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odešle oznámení, když uživatel spustí přetáhněte položku. Ovládací prvek odešle [TVN_BEGINDRAG](/windows/desktop/Controls/tvn-begindrag) zprávy oznámení, když uživatel zahájí přetahování položky s levým tlačítkem myši a [TVN_BEGINRDRAG](/windows/desktop/Controls/tvn-beginrdrag) zprávy oznámení, když uživatel zahájí přetahování s pravým tlačítkem. Ovládací prvek stromu můžete zabránit zadáním do ovládacího prvku stromu styl TVS_DISABLEDRAGDROP posílání těchto oznámení.

Získat obrázek, který se zobrazí během operace přetažení voláním [CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) členskou funkci. Do ovládacího prvku stromu vytvoří přetahování rastrového obrázku na základě štítku položky právě přetáhli. Pak do ovládacího prvku stromu vytvoří seznam obrázků, přidá rastrového obrázku nastaven na ni a vrací ukazatel na [atributu CImageList](../mfc/reference/cimagelist-class.md) objektu.

Je nutné zadat kód, který ve skutečnosti přetáhne položku. To obvykle zahrnuje pomocí přetahování možností funkce seznam obrázků a zpracování [wm_mousemove a](/windows/desktop/inputdev/wm-mousemove) a [WM_LBUTTONUP](/windows/desktop/inputdev/wm-lbuttonup) (nebo [WM_RBUTTONUP](/windows/desktop/inputdev/wm-rbuttonup)) zprávy odeslané po zahájení operace přetažení. Další informace o funkcích seznamu image, najdete v části [atributu CImageList](../mfc/reference/cimagelist-class.md) v *odkaz knihovny MFC* a [seznamy obrázků](/windows/desktop/controls/image-lists) v sadě Windows SDK. Další informace o přetahování položky ovládacího prvku stromu, naleznete v tématu [přetažením položka stromového zobrazení](/windows/desktop/Controls/tree-view-controls), také v sadě Windows SDK.

Pokud jsou položky v ovládacím prvku strom cíli operace přetažení myší, musíte vědět, kdy je ukazatel myši na cílovou položku. Můžete zjistit pomocí volání [hitTest –](../mfc/reference/ctreectrl-class.md#hittest) členskou funkci. Zadejte bod a celé číslo nebo adresu [TVHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvhittestinfo) strukturu, která obsahuje aktuální souřadnic ukazatele myši. Po návratu funkce celé číslo nebo struktura obsahuje příznak označující umístění ukazatele myši relativně vzhledem k stromové struktury. Pokud je kurzor na položku v ovládacím prvku stromu, struktura obsahuje popisovač předmětu také.

Můžete určit, že položka je cíl operace přetažení myší pomocí volání [SetItem](../mfc/reference/ctreectrl-class.md#setitem) členskou funkci pro nastavení stavu `TVIS_DROPHILITED` hodnotu. Položka, která má být tento stav je vykreslena ve stylu slouží k určení cíle přetažení myší.

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
