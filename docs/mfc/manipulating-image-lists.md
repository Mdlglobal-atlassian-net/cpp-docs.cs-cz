---
title: Manipulace se seznamy obrázků | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1eeccfa5245c6395e530859eb91c7f9a5c01335e
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930368"
---
# <a name="manipulating-image-lists"></a>Manipulace se seznamy obrázků
[Nahradit](../mfc/reference/cimagelist-class.md#replace) – členská funkce nahrazuje obrázek v seznamu obrázků ([CImageList](../mfc/reference/cimagelist-class.md)) s novou bitovou kopii. Tato funkce je také užitečné, pokud je potřeba dynamicky zvýšit počet bitových kopií v objektu seznamu bitové kopie. [SetImageCount](../mfc/reference/cimagelist-class.md#setimagecount) funkce dynamicky změní počet bitových kopií, které jsou uložené v seznamu obrázků. Pokud zvýšíte velikosti seznamu obrázků, zavolejte `Replace` Přidání bitové kopie do nové sloty bitové kopie. Pokud snížit velikost seznamu obrázků jsou uvolněny nad rámec novou velikost bitové kopie.  
  
 [Odebrat](../mfc/reference/cimagelist-class.md#remove) – členská funkce odebere bitovou kopii ze seznamu obrázků. [Kopie](../mfc/reference/cimagelist-class.md#copy) – členská funkce můžete zkopírovat nebo odkládacího souboru bitové kopie v rámci seznamu obrázků. Tato funkce umožňuje určit, zda zdrojová bitová kopie by se měl zkopírovat na cílový index nebo si místo zdrojové a cílové bitové kopie.  
  
 K vytvoření nového seznamu obrázků sloučením dva seznamy obrázků použijte předáte příslušnému přetížení [vytvořit](../mfc/reference/cimagelist-class.md#create) – členská funkce. Toto přetížení `Create` sloučení uvádí první obrázek existující bitová kopie, ukládání výsledné bitové kopie v nový objekt seznamu bitové kopie. Kreslení druhý obrázek transparentně přes první vytvoří novou bitovou kopii. Maska pro novou bitovou kopii je výsledek provedení operace logické nebo na bity masky pro dvě existující bitové kopie.  
  
 To se opakuje, dokud se všechny Image sloučit a přidají se jako nový objekt seznamu bitové kopie.  
  
 Informace o obrázku může zapsat do archivu voláním [zápisu](../mfc/reference/cimagelist-class.md#write) – členská funkce a čtení zpátky voláním [čtení](../mfc/reference/cimagelist-class.md#read) – členská funkce.  
  
 [GetSafeHandle](../mfc/reference/cimagelist-class.md#getsafehandle), [Attach](../mfc/reference/cimagelist-class.md#attach), a [odpojení](../mfc/reference/cimagelist-class.md#detach) členské funkce umožňují pracovat s popisovač seznamu obrázků, který je připojen k `CImageList` objekt, při [DeleteImageList](../mfc/reference/cimagelist-class.md#deleteimagelist) – členská funkce odstraní seznamu obrázků bez zničení `CImageList` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CImageList](../mfc/using-cimagelist.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

