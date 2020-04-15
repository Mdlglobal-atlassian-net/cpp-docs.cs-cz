---
title: Použití seznamů obrázků s ovládacími prvky záhlaví
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 8002c16d1cdf5e0683b642001409b6da9c260660
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366462"
---
# <a name="using-image-lists-with-header-controls"></a>Použití seznamů obrázků s ovládacími prvky záhlaví

Položky záhlaví mají možnost zobrazit obrázek v položce záhlaví. Tento obrázek, uložený v přidruženém seznamu obrázků, je 16 x 16 pixelů a má stejné vlastnosti jako obrázky ikon použité v ovládacím prvku zobrazení seznamu. Chcete-li toto chování úspěšně implementovat, musíte nejprve vytvořit a inicializovat seznam obrázků, přidružit seznam k ovládacímu prvku záhlaví a potom upravit atributy položky záhlaví, která zobrazí obrázek.

Následující postup znázorňuje podrobnosti pomocí ukazatele na`m_pHdrCtrl`ovládací prvek záhlaví (`m_pHdrImages`) a ukazatele na seznam obrázků ( ).

### <a name="to-display-an-image-in-a-header-item"></a>Zobrazení obrázku v položce záhlaví

1. Vytvořte nový seznam obrázků (nebo použijte existující objekt seznamu obrázků) pomocí konstruktoru [CImageList](../mfc/reference/cimagelist-class.md) a uveďte výsledný ukazatel.

1. Inicializovat nový objekt seznamu obrázků voláním [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Následující kód je jedním z příkladů tohoto volání.

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. Přidejte obrázky pro každou položku záhlaví. Následující kód přidá dva předdefinované obrázky.

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. Přidružte seznam obrázků k ovládacímu prvku záhlaví ke volání [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).

1. Upravte položku záhlaví tak, aby se zobrazil obrázek z přidruženého seznamu obrázků. Následující příklad přiřadí první obrázek , od `m_phdrImages`, `m_pHdrCtrl`k první položce záhlaví , .

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

Podrobné informace o použitých hodnotách parametrů naleznete v souvisejícím [souboru CHeaderCtrl](../mfc/reference/cheaderctrl-class.md).

> [!NOTE]
> Je možné mít více ovládacích prvků pomocí stejného seznamu obrázků. Například v ovládacím prvku zobrazení standardního seznamu může být seznam obrázků (obrázků o rozměrech 16 x 16 pixelů) používaný jak malým zobrazením ikon ovládacího prvku zobrazení seznamu, tak položkami záhlaví ovládacího prvku zobrazení seznamu.

## <a name="see-also"></a>Viz také

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)
