---
title: "Obrázek překryvy v seznamech obrázků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e9c5ff46d20af4b668d705a782e7765a9d49da35
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="image-overlays-in-image-lists"></a>Překryvy obrázků v seznamech obrázků
Každý seznamu obrázků ([CImageList](../mfc/reference/cimagelist-class.md)) obsahuje seznam bitové kopie na použití jako překrytí masky. "Překrytí maska" je obrázek, který vykresluje transparentně přes jiné image. Žádný obrázek slouží jako masku překrytí. Můžete zadat až čtyři masek překrytí na seznamu obrázků.  
  
 Přidejte index bitové kopie do seznamu překrytí masky pomocí [SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) – členská funkce, index bitové kopie a index masku překrytí. Upozorňujeme, že indexy masek překrytí jsou základem jedna místo od nuly.  
  
 Zakreslit masku překrytí nad bitovou kopii pomocí jediné volání **kreslení**. Parametry patří index bitové kopie k vykreslení a index masku překrytí. Je nutné použít [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) makro k určení index maska překrytí. Můžete také určit bitovou kopii překrytí při volání metody [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CImageList](../mfc/using-cimagelist.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

