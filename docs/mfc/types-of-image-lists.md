---
title: Typy seznamů obrázků | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8988dc55bbbaa1d446ee14bf78a0cd799b422834
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="types-of-image-lists"></a>Typy seznamů obrázků
Existují dva typy seznamů obrázků ([CImageList](../mfc/reference/cimagelist-class.md)): nonmasked a maskované. "Nonmasked image seznam" se skládá z barva rastrového obrázku, který obsahuje jeden nebo více bitových kopií. "Maskované image seznam" se skládá ze dvou bitmap rovna velikosti. První je barva rastrového obrázku, který obsahuje Image a druhá černobílý rastrový obrázek, který obsahuje řadu masek – jeden pro každé bitové kopie v první rastrového obrázku.  
  
 Jeden z přetížení **vytvořit** – členská funkce trvá příznak označující, zda je maskovat seznamu obrázků. (Další přetížení vytvořit seznamy maskované obrázků.)  
  
 Pokud se nevykreslí nonmasked bitové kopie, je jednoduše zkopírují do kontextu cílové zařízení; To znamená se vykresluje přes existující barvu pozadí kontextu zařízení. Při sestavování maskované bitové kopie, služba bits bitové kopie spolu se bity maska, kde je zobrazeno barvu pozadí cílový kontext zařízení obvykle generovala průhledné oblasti v souboru bitové mapy. Při kreslení maskované bitové kopie můžete zadat několik kreslení stylů. Například můžete zadat, že se k označení vybraný objekt tónovaná bitovou kopii.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CImageList](../mfc/using-cimagelist.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

