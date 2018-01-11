---
title: "Použití seznamu obrázků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4321649bf4e8fe0e34fef8fe37b8c96598bef2c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-image-list"></a>Použití seznamu obrázků
Typické použití seznamu obrázků se následující níže:  
  
-   Vytvořit [CImageList](../mfc/reference/cimagelist-class.md) objektu a volání jednoho z přetížení jeho [vytvořit](../mfc/reference/cimagelist-class.md#create) funkce vytvoření seznamu obrázků a připojte ji k `CImageList` objektu.  
  
-   Pokud jste při vytvoření seznamu obrázků nepřidali bitové kopie, přidání bitové kopie do seznamu obrázků voláním [přidat](../mfc/reference/cimagelist-class.md#add) nebo [čtení](../mfc/reference/cimagelist-class.md#read) – členská funkce.  
  
-   Přidružení seznamu obrázků s ovládacím prvkem voláním funkce příslušného člena tohoto ovládacího prvku a vykreslení obrázků ze seznamu obrázků sami pomocí seznamu obrázků [kreslení](../mfc/reference/cimagelist-class.md#draw) – členská funkce.  
  
-   Případně povolte uživatelům přetáhněte bitovou kopii, použití seznamu obrázků integrovanou podporu pro přetažení myší.  
  
> [!NOTE]
>  Pokud byl vytvořen seznamu obrázků s **nové** operátor, musíte zničit `CImageList` objektu až skončíte s ním.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CImageList](../mfc/using-cimagelist.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

