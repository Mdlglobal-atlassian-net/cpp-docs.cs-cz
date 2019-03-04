---
title: Seznamy obrázků v ovládacím prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: f4dc4f0d7b2cfb78b07b23802054f119da9cbbc3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290674"
---
# <a name="tree-control-image-lists"></a>Seznamy obrázků v ovládacím prvku strom

Každá položka v ovládacím prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) může mít pár rastrovými obrázky, které s ním spojená. Image se zobrazí na levé straně popisku položky. Při výběru položky a druhé se zobrazí, pokud položka není vybrána, zobrazí se jedné image. Například může položku zobrazit, otevřít složku, pokud je vybrána a uzavřené složky pokud není vybrán.

Použití obrázků položek, musíte vytvořit seznam obrázků tak, že vytváří [atributu CImageList](../mfc/reference/cimagelist-class.md) objektů a pomocí [CImageList::Create](../mfc/reference/cimagelist-class.md#create) funkci, která vytvoří seznam přidružené image. Pak přidejte do seznamu požadovanou rastrové obrázky a přidružení seznamu pomocí ovládacího prvku stromu pomocí [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist) členskou funkci. Ve výchozím nastavení všechny položky zobrazit první obrázek v seznamu obrázků pro vybranou a nevybrané stavy. Výchozí chování pro určité položky můžete změnit zadáním indexy imagí vybraných a nevybrané při přidání položky do stromu ovládacího prvku pomocí [metody InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) členskou funkci. Indexy, které můžete změnit po přidání položky pomocí [SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage) členskou funkci.

Ovládací prvek stromu seznamů obrázků může také obsahovat obrázky překrytí, které mají být bude zobrazen na obrázků položek. Určuje založen na jedničce index obrázku, který překrytí nenulovou hodnotu v bitech 8 až 11 stav položky ovládacího prvku strom (0 znamená bez překrytí obrázku). Index 4-bit, založen na jedničce, protože se používají překrytí Image musí být mezi prvních 15 obrázků v seznamech obrázků. Další informace o stavů položek ovládacího prvku stromu, naleznete v tématu [přehled stavů položek ovládacího prvku stromu](../mfc/tree-control-item-states-overview.md) výše v tomto tématu.

Pokud je zadán seznam obrázků stavu, ovládací prvek stromu rezervuje prostor nalevo od každé položky ikonu obrázku stavu. Aplikace může použít Image stavu, jako jsou zaškrtnuto a nezaškrtnuté zaškrtávací políčka označíte stavy položky definované aplikací. Určuje index obrázku stavu založen na jedničce nenulovou hodnotu v bitech 12 až 15 (0 znamená bez obrázku stavu).

Zadáním **I_IMAGECALLBACK** hodnotu místo index image, může pozdržet zadávání vybrané nebo nevybrané image, dokud se má položka přibližně vyžadovaly překreslení. **I_IMAGECALLBACK** přesměruje do ovládacího prvku stromu k dotazování aplikací pro index odesláním [TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo) zprávy oznámení.

[GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist) členskou funkci načte popisovač ovládací prvek stromu seznamu obrázků. Tato funkce je užitečná, pokud je potřeba přidat další Image do seznamu. Další informace o seznamech image, najdete v části [používání atributu CImageList](../mfc/using-cimagelist.md), [atributu CImageList](../mfc/reference/cimagelist-class.md) v *odkaz knihovny MFC*, a [seznamy obrázků](/windows/desktop/controls/image-lists) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
