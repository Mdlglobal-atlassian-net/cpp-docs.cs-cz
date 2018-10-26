---
title: Použití seznamů obrázků s ovládacími prvky záhlaví | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b12f3ff78f88029067d3b77296979a173dad494d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079646"
---
# <a name="using-image-lists-with-header-controls"></a>Použití seznamů obrázků s ovládacími prvky záhlaví

Položky hlavičky se budou moct zobrazit obrázek položky záhlaví. Tuto bitovou kopii, uložené v seznamu přidružených obrázků, je 16 × 16 pixelů a má stejné vlastnosti jako obrázky ikon používaných pro ovládací prvek zobrazení seznamu. Aby bylo možné úspěšně implementovat toto chování, musíte nejprve vytvořit a inicializovat seznam obrázků, přidružení seznamu pomocí ovládacího prvku záhlaví a změňte atributy, které se zobrazí obrázek položky záhlaví.

Následující postup ukazuje podrobnosti, pomocí ukazatele na ovládacím prvku hlavička (`m_pHdrCtrl`) a ukazatel na seznamu obrázků (`m_pHdrImages`).

### <a name="to-display-an-image-in-a-header-item"></a>Pro zobrazení obrázku položky záhlaví

1. Vytvoření nového seznamu obrázků (nebo použijte existující objekt seznam obrázků) pomocí [atributu CImageList](../mfc/reference/cimagelist-class.md) konstruktor ukládání výsledný ukazatel.

1. Inicializovat nový objekt seznamu obrázků voláním [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Následující kód je jedním z příkladů tohoto volání.

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. Přidání obrázků pro jednotlivé položky záhlaví. Následující kód přidá dvě předdefinované bitové kopie.

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. Přidružení seznamu obrázků s ovládacím prvkem záhlaví voláním [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).

1. Upravte položky záhlaví pro zobrazení obrázku ze seznamu přidružené image. Následující příklad přiřadí první image z `m_phdrImages`, na první položku záhlaví `m_pHdrCtrl`.

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

Podrobné informace o používá hodnoty parametrů naleznete v příslušné [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md).

> [!NOTE]
>  Je možné mít více ovládacích prvků pomocí stejného seznamu obrázků. Například v ovládacím prvku seznamu standardní zobrazení, může dojít obrázek seznamu (16 × 16 pixelů imagí) používaných zobrazení malou ikonu ovládacího prvku zobrazení seznamu a položky záhlaví ovládacího prvku zobrazení seznamu.

## <a name="see-also"></a>Viz také

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)

