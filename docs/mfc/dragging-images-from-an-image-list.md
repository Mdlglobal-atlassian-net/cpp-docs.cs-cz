---
title: Přetahování obrázků ze seznamu obrázků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb872cba298d6d18ab5287a285b22d2f568fa04b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382372"
---
# <a name="dragging-images-from-an-image-list"></a>Přetahování obrázků ze seznamu obrázků

[Cimagelist –](../mfc/reference/cimagelist-class.md) obsahuje funkce pro přetažení myší bitovou kopii na obrazovce. Přetahování funkce přesunout bitovou kopii plynule, barva a bez jakékoli blikající kurzor. Maskované a odmaskovaná imagí můžete přetáhnout.

[Přetahovacích](../mfc/reference/cimagelist-class.md#begindrag) členskou funkci začne operace přetažení. Parametry zahrnují index bitové kopie přetáhněte a umístění aktivního bodu v obrázku. Aktivní bod je jeden pixel, který přetahování funkce rozpoznat jako přesné obrazovky umístění bitové kopie. Aplikace obvykle nastaví aktivního bodu tak, aby se shodovala s aktivního bodu kurzoru myši. [Metodu DragMove](../mfc/reference/cimagelist-class.md#dragmove) členská funkce do nového umístění přesune na obrázku.

[DragEnter](../mfc/reference/cimagelist-class.md#dragenter) členská funkce nastaví počáteční umístění přetáhnout obrázek v rámci časového období a nakreslí obrázek na pozici. Parametry zahrnují ukazatel na okna, ve kterém chcete-li nakreslit obrázek a bodem, který určuje souřadnice počáteční pozici v rámci okna. Souřadnice jsou relativní vzhledem k výšce levý horní roh není klientské oblasti. Totéž platí pro všechny sady funkcí přetahování bitové kopie, které přijímají souřadnice jako parametry. To znamená, že se že musí vyrovnat pro šířku okna prvky, jako je například ohraničení, záhlaví a řádek nabídek, při určování souřadnice. Pokud zadáte **NULL** popisovač okna při volání metody `DragEnter`přetahování funkce vykreslení obrázku v kontextu zařízení spojená s oknem klasické pracovní plochy a souřadnice jsou relativní vzhledem k levého horního rohu obrazovky.

`DragEnter` všechny aktualizace v daném okně uzamkne během operace přetažení. Pokud je třeba provést jakékoli kreslení během operace přetažení, jako je například zvýraznění cíl operace přetažení myší, můžete dočasně skrýt Přetahované image pomocí [DragLeave](../mfc/reference/cimagelist-class.md#dragleave) členskou funkci. Můžete také použít [DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock) členskou funkci.

Volání [EndDrag](../mfc/reference/cimagelist-class.md#enddrag) až budete mít přetáhnete na obrázku.

[SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage) členská funkce vytvoří novou image přetáhněte kombinací danou image (obvykle bitové kopie kurzoru myši) aktuální přetáhnout obrázek. Vzhledem k tomu, aby nový image používala přetahování funkce během operace přetažení, byste měli použít Windows [ShowCursor](/windows/desktop/api/winuser/nf-winuser-showcursor) skrýt skutečné myší po volání funkce `SetDragCursorImage`. V opačném případě systém pravděpodobně mají dva ukazatele myši po dobu trvání operace přetažení.

Pokud aplikace zavolá `BeginDrag`, systém vytvoří dočasné, interní obrázek seznamu a zkopíruje zadaný přetáhněte image do seznamu interní. Ukazatel na seznam obrázků dočasné přetáhněte můžete načíst pomocí [GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage) členskou funkci. Funkce také načte aktuální pozici přetažení a posun přetáhnout obrázek umístění přetažení.

## <a name="see-also"></a>Viz také

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

