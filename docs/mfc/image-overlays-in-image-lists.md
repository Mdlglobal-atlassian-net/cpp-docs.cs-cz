---
title: Obrázek překryvy v seznamech obrázků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4369fe312669f75eb8217be7a6a09c4287f7cc8b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210710"
---
# <a name="image-overlays-in-image-lists"></a>Překryvy obrázků v seznamech obrázků
Každý seznamu obrázků ([atributu CImageList](../mfc/reference/cimagelist-class.md)) obsahuje seznam imagí, které chcete použít jako překrytí masky. "Překrytí maska" je obrázek transparentně zaškrtnutí nakreslit přes jiný obrázek. Žádné image může sloužit jako masku překrytí. Můžete zadat až čtyři masky překrytí na seznamu obrázků.  
  
 Index obrázku, který přidáte do seznamu překrytí masky pomocí [SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) členskou funkci, index bitové kopie a index masku překrytí. Všimněte si, že indexy masky překrytí jsou založen na jedničce, spíše než založený na nule.  
  
 Nakreslit masku překrytí přes pomocí jednoho volání image `Draw`. Parametry zahrnují index obrázku pro kreslení a index masku překrytí. Je nutné použít [INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) – makro k určení indexu maska překrytí. Můžete také určit bitovou kopii překrytí při volání [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) členskou funkci.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CImageList](../mfc/using-cimagelist.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

