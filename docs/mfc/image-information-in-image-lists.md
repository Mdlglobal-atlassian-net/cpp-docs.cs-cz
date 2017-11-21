---
title: "Obrázek informace v seznamech obrázků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 80e897ec79314abb2e77864e53d470e72f275a94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="image-information-in-image-lists"></a>Informace o obrázku v seznamu obrázků
[CImageList](../mfc/reference/cimagelist-class.md) zahrnuje několik funkcí, které načtení informací ze seznamu obrázků. [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo) – členská funkce doplní `IMAGEINFO` struktura s informacemi o jednu bitovou kopii, včetně popisovače bitmap bitové kopie a maska, počet barevných rovin a bitů na pixel a ohraničující obdélník bitové kopie v rámci rastrový obrázek bitové kopie. Tyto informace můžete použít k manipulaci se přímo bitmap pro bitovou kopii.  
  
 [Getimagecount –](../mfc/reference/cimagelist-class.md#getimagecount) – členská funkce načte množství obrázků v seznamu obrázků.  
  
 Můžete vytvořit ikonu založené na bitové kopie a maska v seznamu obrázků s použitím [ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon) – členská funkce. Vrátí popisovač na ikonu nový.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CImageList](../mfc/using-cimagelist.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

