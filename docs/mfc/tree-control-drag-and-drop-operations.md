---
title: Operace přetažení u ovládacího prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: 5d2c5aa511844a3d7cbe64d9a15f8ffb46046b29
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510903"
---
# <a name="tree-control-drag-and-drop-operations"></a>Operace přetažení u ovládacího prvku strom

Ovládací prvek stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odesílá oznámení, když uživatel začne přetahovat položku. Ovládací prvek pošle zprávu s oznámením [TVN_BEGINDRAG](/windows/win32/Controls/tvn-begindrag) , když uživatel začne přetahovat položku levým tlačítkem myši a zprávou [TVN_BEGINRDRAG](/windows/win32/Controls/tvn-beginrdrag) oznámení, když uživatel začne přetahovat pomocí pravého tlačítka. Ovládacímu prvku stromu můžete zabránit v odesílání těchto oznámení tím, že ovládacímu prvku stromu umožníte TVS_DISABLEDRAGDROP styl.

Získáte obrázek, který se zobrazí během operace přetažení voláním členské funkce [CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) . Stromová struktura vytvoří přetahování rastrového obrázku na základě popisku položky, která je přetažena. Stromová struktura potom vytvoří seznam obrázků, přidá k němu rastrový obrázek a vrátí ukazatel na objekt [atributu CImageList](../mfc/reference/cimagelist-class.md) .

Je nutné zadat kód, který položku skutečně přetáhne. To obvykle zahrnuje použití možností přetahování funkcí seznamu obrázků a zpracování zpráv [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) a [WM_LBUTTONUP](/windows/win32/inputdev/wm-lbuttonup) (nebo [WM_RBUTTONUP](/windows/win32/inputdev/wm-rbuttonup)) odesílaných po zahájení operace přetažení. Další informace o funkcích seznamu obrázků naleznete v tématu [atributu CImageList](../mfc/reference/cimagelist-class.md) in *MFC Reference* and [image](/windows/win32/controls/image-lists) lists in the Windows SDK. Další informace o přetažení položky ovládacího prvku stromu naleznete v tématu [přetahování položky stromového zobrazení](/windows/win32/Controls/tree-view-controls), a také v Windows SDK.

Pokud jsou položky ve stromovém řízení cílem operace přetažení, musíte znát, kdy se ukazatel myši nachází na cílové položce. Můžete zjistit voláním členské funkce [HitTest](../mfc/reference/ctreectrl-class.md#hittest) . Zadejte buď bod a celé číslo, nebo adresu struktury [TVHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tvhittestinfo) , která obsahuje aktuální souřadnice kurzoru myši. Vrátí-li funkce hodnotu, celé číslo nebo struktura obsahuje příznak označující umístění ukazatele myši vzhledem k ovládacímu prvku stromu. Pokud se ukazatel myši nachází na položce v ovládacím prvku strom, struktura obsahuje také popisovač položky.

Můžete určit, že položka je cílem operace přetažení, voláním členské funkce [SetItem](../mfc/reference/ctreectrl-class.md#setitem) pro nastavení stavu na `TVIS_DROPHILITED` hodnotu. Položka, která má tento stav, je vykreslena ve stylu používaném k označení cíle přetažení myší.

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
