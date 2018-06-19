---
title: Obrázek informace v seznamech obrázků | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b45a685a9de44bdc40f83481cb83ef58a5c4234
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343710"
---
# <a name="image-information-in-image-lists"></a>Informace o obrázku v seznamu obrázků
[CImageList](../mfc/reference/cimagelist-class.md) zahrnuje několik funkcí, které načtení informací ze seznamu obrázků. [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo) – členská funkce doplní `IMAGEINFO` struktura s informacemi o jednu bitovou kopii, včetně popisovače bitmap bitové kopie a maska, počet barevných rovin a bitů na pixel a ohraničující obdélník bitové kopie v rámci rastrový obrázek bitové kopie. Tyto informace můžete použít k manipulaci se přímo bitmap pro bitovou kopii.  
  
 [Getimagecount –](../mfc/reference/cimagelist-class.md#getimagecount) – členská funkce načte množství obrázků v seznamu obrázků.  
  
 Můžete vytvořit ikonu založené na bitové kopie a maska v seznamu obrázků s použitím [ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon) – členská funkce. Vrátí popisovač na ikonu nový.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CImageList](../mfc/using-cimagelist.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

