---
title: Překryvy obrázků v seznamech obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: ec795193a28a68d8aee61e9932481a89c4b3e8e0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508388"
---
# <a name="image-overlays-in-image-lists"></a>Překryvy obrázků v seznamech obrázků

Každý seznam obrázků ([atributu CImageList](../mfc/reference/cimagelist-class.md)) obsahuje seznam obrázků, které se použijí jako překrytí masek. "Překryvná maska" je obrázek vykreslený transparentně přes jiný obrázek. Libovolný obrázek lze použít jako překryvnou masku. Na seznam obrázků můžete zadat až čtyři překryté masky.

Index obrázku můžete přidat do seznamu překrytých masek pomocí členské funkce [SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) , indexu obrázku a indexu překryté masky. Všimněte si, že indexy pro překrytí jsou založeny na jednom, nikoli na základě nuly.

Překreslíte překrytou masku na obrázek pomocí jednoho volání `Draw`. Parametry zahrnují index obrázku, který se má vykreslit, a index překryté masky. Je nutné použít makro [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) k určení indexu překryté masky. Můžete také zadat překrývající obrázek při volání členské funkce [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) .

## <a name="see-also"></a>Viz také:

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
