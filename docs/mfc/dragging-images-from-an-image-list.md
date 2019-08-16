---
title: Přetahování obrázků ze seznamu obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
ms.openlocfilehash: 3035e6f21d38568b364fce02358c3baed4870bc3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508648"
---
# <a name="dragging-images-from-an-image-list"></a>Přetahování obrázků ze seznamu obrázků

[Atributu CImageList](../mfc/reference/cimagelist-class.md) zahrnuje funkce pro přetahování obrázku na obrazovce. Přetahování funkcí přesune obrázek hladce, barevně a bez nutnosti blikajícího kurzoru. Maskované a nemaskované obrázky lze přetáhnout.

Členská funkce [přetahovacích funkcí](../mfc/reference/cimagelist-class.md#begindrag) zahájí operaci přetažení. Parametry zahrnují index obrázku, který má být přetažen, a umístění aktivního bodu v rámci obrázku. Aktivním bodem je jeden pixel, který funkce přetahování rozpoznává jako přesné umístění obrazovky obrázku. Aplikace obvykle nastavuje aktivní bod tak, aby se shodoval s aktivním bodem kurzoru myši. Členská funkce [DragMove](../mfc/reference/cimagelist-class.md#dragmove) přesune obrázek do nového umístění.

Členská funkce [DragEnter](../mfc/reference/cimagelist-class.md#dragenter) nastaví počáteční pozici obrázku přetažení v rámci okna a nakreslí obrázek na pozici. Parametry zahrnují ukazatel na okno, ve kterém se má obrázek nakreslit, a bod, který určuje souřadnice počáteční pozice v rámci okna. Souřadnice jsou relativní vzhledem k levému hornímu rohu okna, nikoli klientské oblasti. Totéž platí pro všechny funkce přetahování obrázků, které přijímají souřadnice jako parametry. To znamená, že při zadávání souřadnic musíte kompenzovat šířku prvků oken, jako je například ohraničení, záhlaví a panel nabídek. Pokud při volání `DragEnter`zadáte popisovač okna s **hodnotou null** , funkce přetahování nakreslí obrázek v kontextu zařízení přidruženého k oknu plocha a souřadnice jsou relativní vzhledem k levému hornímu rohu obrazovky.

`DragEnter`Uzamkne všechny ostatní aktualizace daného okna během operace přetažení. Pokud během operace přetažení potřebujete udělat všechny kresby, jako je například zvýraznění cíle operace přetažení, můžete přetažený obrázek dočasně skrýt pomocí členské funkce [DragLeave](../mfc/reference/cimagelist-class.md#dragleave) . Můžete také použít členskou funkci [DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock) .

Po přetahování obrázku zavolejte [EndDrag](../mfc/reference/cimagelist-class.md#enddrag) .

Členská funkce [SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage) vytvoří nový obrázek přetažením pomocí kombinace daného obrázku (obvykle obrázku kurzoru myši) s aktuálním obrázkem přetažení. Vzhledem k tomu, že funkce přetahování používají nový obrázek během operace přetažení, měli byste pomocí funkce Windows [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) skrýt skutečný ukazatel myši po volání `SetDragCursorImage`. V opačném případě se může zdát, že systém bude mít po dobu trvání operace přetažení dva ukazatele myši.

Při volání `BeginDrag`aplikace systém vytvoří dočasný a interní seznam obrázků a zkopíruje zadaný obrázek přetáhnutí do interního seznamu. Můžete načíst ukazatel na dočasný seznam obrázků přetažením pomocí členské funkce [GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage) . Funkce také načte aktuální polohu přetažení a posun obrázku přetažením vzhledem k poloze přetažení.

## <a name="see-also"></a>Viz také:

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
