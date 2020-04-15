---
title: Seznamy vlastností a stránky vlastností v prostředí MFC
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
ms.openlocfilehash: 10fb34c79745e672d30dd2d3c3b97d457583f795
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371175"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Seznamy vlastností a stránky vlastností v prostředí MFC

Seznam vlastností, označovaný také jako dialogové okno karty, je dialogové okno, které obsahuje stránky vlastností. Každá stránka vlastností je založena na prostředku šablony dialogu a obsahuje ovládací prvky. Je uzavřen na stránce s kartou nahoře. Karta pojmenuje stránku a označuje její účel. Uživatelé klepnutím na kartu v seznamu vlastností vyberte sadu ovládacích prvků.

Pomocí stránek seskupte ovládací prvky v seznamu vlastností do smysluplných sad. Obsažený seznam vlastností má obvykle několik vlastních ovládacích prvků. Ty platí pro všechny stránky.

Seznamy vlastností jsou založeny na třídě [CPropertySheet](../mfc/reference/cpropertysheet-class.md). Stránky vlastností jsou založeny na třídě [CPropertyPage](../mfc/reference/cpropertypage-class.md).

Seznam vlastností je zvláštní druh dialogového okna, které se obecně používá k úpravě atributů některého externího objektu, například aktuálního výběru v zobrazení. Seznam vlastností má tři hlavní části: dialogové okno obsahující, jednu nebo více stránek vlastností zobrazenou po jednom a kartu v horní části každé stránky, na kterou uživatel klepne, a vybere tuto stránku. Seznamy vlastností jsou užitečné v situacích, kdy máte několik podobných skupin nastavení nebo možností, které chcete změnit. Seznam vlastností seskupuje informace snadno srozumitelným způsobem.

> [!NOTE]
> Při pokusu o zobrazení seznamu `CPropertySheet::DoModal`vlastností pomocí aplikace může systém vygenerovat výjimku první šance. K této výjimce dochází, protože systém se pokouší změnit [styly oken](../mfc/reference/styles-used-by-mfc.md#window-styles) objektu před vytvořením objektu. Další informace o této výjimce a také jak se jí vyhnout nebo zpracovat, naleznete v [tématu CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal).

## <a name="see-also"></a>Viz také

[Seznamy vlastností](../mfc/property-sheets-mfc.md)
