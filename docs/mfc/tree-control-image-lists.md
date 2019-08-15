---
title: Seznamy obrázků v ovládacím prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: 8f9e323244657ea6a7cc132deab6deedfcd1a167
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513370"
---
# <a name="tree-control-image-lists"></a>Seznamy obrázků v ovládacím prvku strom

K jednotlivým položkám v ovládacím prvku stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) lze přidružit dvojici rastrových obrázků. Obrázky se zobrazí na levé straně popisku položky. Po výběru položky se zobrazí jeden obrázek, který se zobrazí, pokud položka není vybrána. Položka může například zobrazit otevřenou složku, když je vybrána, a zavřenou složku, když není vybrána.

Chcete-li použít obrázky položek, je nutné vytvořit seznam obrázků sestavením objektu [atributu CImageList](../mfc/reference/cimagelist-class.md) a pomocí funkce [atributu CImageList:: Create](../mfc/reference/cimagelist-class.md#create) vytvořit přidružený seznam obrázků. Pak přidejte požadované rastrové obrázky do seznamu a přidružte seznam k ovládacímu prvku stromu pomocí členské funkce [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist) . Ve výchozím nastavení všechny položky zobrazují první obrázek v seznamu obrázků pro vybrané i nevybrané stavy. Můžete změnit výchozí chování pro konkrétní položku zadáním indexů vybraných a nevybraných obrázků při přidávání položky do ovládacího prvku strom pomocí členské funkce [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) . Indexy můžete změnit po přidání položky pomocí členské funkce [SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage) .

Seznamy obrázků v ovládacím prvku strom mohou obsahovat také překryté obrázky, které jsou navrženy tak, aby byly uloženy na obrázcích položek. Nenulová hodnota v bitech 8 až 11 stavu položky ovládacího prvku stromu určuje index překryté Image (0 označuje žádný překryvný obrázek). Vzhledem k tomu, že je použit 4bitový index, musí být překrytí obrázků z prvních 15 obrázků v seznamech obrázků. Další informace o stavech položek ovládacího prvku strom naleznete v tématu [Přehled stavů položek stromu ovládacího prvku stromové struktury](../mfc/tree-control-item-states-overview.md) výše v tomto tématu.

Pokud je zadán seznam obrázků stavů, ovládací prvek stromové struktury vyhrazuje místo vlevo od ikony každé položky pro obrázek stavu. Aplikace může k označení stavů položek definovaných aplikací použít obrázky stavu, například zaškrtnuté a nezaškrtnuté zaškrtávací políčka. Nenulová hodnota v bitech 12 až 15 určuje index obrázku stavu (0 znamená, že obrázek stavu není).

Zadáním hodnoty **I_IMAGECALLBACK** namísto indexu obrázku můžete zpozdit určení vybraného nebo nevybraného obrázku, dokud nebude položka znovu vykreslena. **I_IMAGECALLBACK** přesměruje ovládací prvek stromu na dotaz na aplikaci pro index odesláním zprávy s oznámením [TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo) .

Člen [](../mfc/reference/ctreectrl-class.md#getimagelist) funkce GetImageList načte popisovač seznamu obrázků ovládacího prvku stromu. Tato funkce je užitečná v případě, že do seznamu potřebujete přidat další obrázky. Další informace o seznamech obrázků najdete v tématu [použití atributu CImageList](../mfc/using-cimagelist.md), [atributu CImageList](../mfc/reference/cimagelist-class.md) v *odkazu knihovny MFC*a v [seznamech obrázků](/windows/win32/controls/image-lists) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
