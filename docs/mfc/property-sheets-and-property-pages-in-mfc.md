---
title: Seznamy vlastností a stránky vlastností v prostředí MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f35282ce46aff3a3f0fba5fca505653cd892a392
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430034"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Seznamy vlastností a stránky vlastností v prostředí MFC

Seznam vlastností, také známé jako dialogové okno Karta, je dialogové okno, které obsahuje stránky vlastností. Každou stránku vlastností založenou na prostředku šablony dialogového okna a obsahuje ovládací prvky. Na stránce je uzavřen kartě v horní části. Na kartě Název stránky a označuje její účel. Uživatelé kliknou na kartě v seznamu vlastností vyberte sadu ovládacích prvků.

Pomocí stránky smysluplné sady pro seskupení ovládacích prvků v seznamu vlastností. Seznam vlastností obsažených obvykle obsahuje několik ovládacích prvků své vlastní. Platí pro všechny stránky.

Seznamy vlastností jsou založeny na třídě [cpropertysheet –](../mfc/reference/cpropertysheet-class.md). Stránky vlastností, které jsou založeny na třídě [CPropertyPage](../mfc/reference/cpropertypage-class.md).

Seznam vlastností je zvláštní druh dialogové okno, které se obecně používá k úpravě atributy některé externí objekt, jako je například aktuální výběr v zobrazení. Seznam vlastností má tři hlavní části: dialogovém okně obsahující jeden nebo více vlastností stránky je vidět jeden po druhém a na kartě v horní části každé stránky, který uživatel klikne na této stránce vyberte. Seznamy vlastností jsou užitečné v situacích, kdy máte několik podobné skupiny nastavení nebo změnu. Seznam vlastností skupiny informace snadno pochopitelného způsobem.

> [!NOTE]
>  Když se snažíte zobrazit seznam vlastností s použitím `CPropertySheet::DoModal`, systém může vygenerovat první odpovídající výjimce. Touto výjimkou způsobeno systém se pokouší změnit [styly oken](../mfc/reference/styles-used-by-mfc.md#window-styles) objektu předtím, než byl vytvořen objekt. Další informace o této výjimky a také jak jí předcházet, nebo ji zpracovat, naleznete v tématu [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal).

## <a name="see-also"></a>Viz také

[Seznamy vlastností](../mfc/property-sheets-mfc.md)

