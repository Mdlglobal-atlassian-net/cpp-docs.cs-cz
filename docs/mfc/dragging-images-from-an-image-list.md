---
title: Přetahování obrázků ze seznamu obrázků | Microsoft Docs
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
ms.openlocfilehash: d54984cdc1dc7897fb4f5d1d9680c6a2b95a787d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347162"
---
# <a name="dragging-images-from-an-image-list"></a>Přetahování obrázků ze seznamu obrázků
[CImageList](../mfc/reference/cimagelist-class.md) obsahuje funkce pro přetažení myší bitovou kopii na obrazovce. Přetahování funkce, bitovou kopii plynule, přesuňte barevně a bez jakékoli blikající kurzor. Můžete přetáhnout maskované a nemaskované bitové kopie.  
  
 [Přetahovacích](../mfc/reference/cimagelist-class.md#begindrag) – členská funkce zahájí operaci přetažení. Parametry zahrnují index bitové kopie přetáhněte a umístění aktivního bodu v rámci bitovou kopii. Aktivní bod je jeden pixel, který přetahování funkce rozpoznat jako přesné obrazovky umístění bitové kopie. Obvykle se aplikace nastaví aktivního bodu tak, aby ho se shoduje s aktivního bodu kurzoru myši. [DragMove](../mfc/reference/cimagelist-class.md#dragmove) – členská funkce přesune bitovou kopii do nového umístění.  
  
 [DragEnter](../mfc/reference/cimagelist-class.md#dragenter) – členská funkce nastaví počáteční umístění obrázku přetáhněte v rámci časového období a nakreslí obrázek na pozici. Parametry zahrnují ukazatel na okna, ve kterém k vykreslení bitové kopie a bod, který určuje souřadnice počáteční pozici v rámci okna. Souřadnice jsou relativní vzhledem k levého horního rohu okna, není klientské oblasti. Totéž platí pro všechny funkcí přetahování bitové kopie, které přijímají souřadnice jako parametry. To znamená, že šířek okno prvky, jako jsou například ohraničení, záhlaví a řádku nabídek musí kompenzovat při zadávání souřadnice. Pokud zadáte **NULL** popisovač okna při volání metody `DragEnter`přetahování funkce kreslení obrázku v kontextu zařízení, které jsou přidružené k okně plochy a souřadnice jsou relativní vzhledem k levého horního rohu obrazovky.  
  
 `DragEnter` Zamkne všechny další aktualizace do daného okna během operace přetažení. Pokud je potřeba udělat všechny kreslení během operace přetažení, jako je například zvýraznění cíl operace přetahování myší, dočasně můžete skrýt taženou bitové kopie, pomocí [DragLeave](../mfc/reference/cimagelist-class.md#dragleave) – členská funkce. Můžete také [DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock) – členská funkce.  
  
 Volání [EndDrag](../mfc/reference/cimagelist-class.md#enddrag) po dokončení přetahování bitovou kopii.  
  
 [SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage) – členská funkce vytvoří novou bitovou kopii přetáhněte kombinací bitovou kopii daného (obvykle bitové kopie kurzor myši) s aktuální image přetažení. Protože přetahování funkce nový image používala během operace přetažení, měli byste používat Windows [ShowCursor](http://msdn.microsoft.com/library/windows/desktop/ms648396) funkce skrytí skutečné myší po volání `SetDragCursorImage`. Jinak systému může pravděpodobně dva ukazatele myši po dobu trvání operace přetažení.  
  
 Pokud aplikace zavolá `BeginDrag`, systém vytvoří seznam dočasné, interní bitové kopie a kopie zadaný přetáhněte bitové kopie do seznamu interní. Ukazatel na seznamu obrázků dočasné přetažení můžete načíst pomocí [GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage) – členská funkce. Funkce také načte aktuální pozici přetažení a posun bitovou kopii přetáhněte vzhledem ke přetáhněte pozici.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CImageList](../mfc/using-cimagelist.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

