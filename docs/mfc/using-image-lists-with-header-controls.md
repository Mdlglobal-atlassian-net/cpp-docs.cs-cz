---
title: "Použití seznamů obrázků s ovládacími prvky záhlaví | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7a51aadc10a7722875597813e24ceb5960ab459
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-image-lists-with-header-controls"></a>Použití seznamů obrázků s ovládacími prvky záhlaví
Položky hlavičky mít možnost zobrazit obrázek v rámci položky záhlaví. Tuto bitovou kopii, uložené v seznamu přidruženou bitovou kopii, je velikosti 16 x 16 pixelů a má stejné vlastnosti jako ikona obrázků použitých v ovládacím prvku zobrazení seznamu. Aby bylo možné úspěšně implementovat toto chování, musíte nejprve vytvořit a Inicializace seznamu obrázků, přidružit seznamu pomocí ovládacího prvku záhlaví a potom upravte atributy položky záhlaví, který se zobrazí bitovou kopii.  
  
 Následující postup ukazuje podrobnosti, pomocí ukazatele do ovládacího prvku záhlaví (`m_pHdrCtrl`) a ukazatel na seznamu obrázků (`m_pHdrImages`).  
  
### <a name="to-display-an-image-in-a-header-item"></a>Chcete zobrazit obrázek v položky záhlaví  
  
1.  Vytvoření nového seznamu obrázků (nebo použijte existující objekt seznamu image) pomocí [CImageList](../mfc/reference/cimagelist-class.md) konstruktoru, ukládání výsledné ukazatele.  
  
2.  Inicializace nového objektu seznamu image voláním [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Následující kód je jedním z příkladů tohoto volání.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]  
  
3.  Přidání bitové kopie pro každou položku záhlaví. Následující kód přidá dvě předdefinované bitové kopie.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]  
  
4.  Přidružení seznamu obrázků s ovládacím prvkem záhlaví s volání [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).  
  
5.  Upravte položky záhlaví zobrazíte bitové kopie ze seznamu přidruženou bitovou kopii. Následující příklad přiřadí první obrázek z `m_phdrImages`, na první položku záhlaví `m_pHdrCtrl`.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]  
  
 Podrobné informace o používá hodnoty parametrů naleznete příslušné [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md).  
  
> [!NOTE]
>  Je možné, že více ovládacích prvků pomocí stejné seznamu obrázků. Například v ovládacím prvku zobrazení seznamu standard, může dojít seznamu obrázků (o velikosti 16 x 16 pixelů Image) používané zobrazení malé ikony ovládacího prvku zobrazení seznamu a položek záhlaví ovládacího prvku zobrazení seznamu.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)

