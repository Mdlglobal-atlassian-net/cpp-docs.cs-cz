---
title: Překryvy obrázků v seznamech obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: 8dd0b30ef29a48ebc763564e6fe23632cd300831
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262776"
---
# <a name="image-overlays-in-image-lists"></a>Překryvy obrázků v seznamech obrázků

Každý seznamu obrázků ([atributu CImageList](../mfc/reference/cimagelist-class.md)) obsahuje seznam imagí, které chcete použít jako překrytí masky. "Překrytí maska" je obrázek transparentně zaškrtnutí nakreslit přes jiný obrázek. Žádné image může sloužit jako masku překrytí. Můžete zadat až čtyři masky překrytí na seznamu obrázků.

Index obrázku, který přidáte do seznamu překrytí masky pomocí [SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) členskou funkci, index bitové kopie a index masku překrytí. Všimněte si, že indexy masky překrytí jsou založen na jedničce, spíše než založený na nule.

Nakreslit masku překrytí přes pomocí jednoho volání image `Draw`. Parametry zahrnují index obrázku pro kreslení a index masku překrytí. Je nutné použít [INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) – makro k určení indexu maska překrytí. Můžete také určit bitovou kopii překrytí při volání [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) členskou funkci.

## <a name="see-also"></a>Viz také:

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
