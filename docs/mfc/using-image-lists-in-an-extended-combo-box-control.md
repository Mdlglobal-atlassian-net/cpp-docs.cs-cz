---
title: Použití seznamů obrázků v ovládacím prvku rozšířené pole se seznamem
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
ms.openlocfilehash: 38f51205eea7220f0efbc2d8821fcb2b423e0add
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504596"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>Použití seznamů obrázků v ovládacím prvku rozšířené pole se seznamem

Hlavní funkce ovládacích prvcích rozšířeného pole se seznamem je možnost k přidružení obrázků ze seznamu obrázků jednotlivých položek v ovládacím prvku pole se seznamem. Každá položka je možné zobrazit tři různé Image: jednu pro vybraný stav, jeden pro jeho nevybrané stavu a třetí pro bitovou kopii překrytí.

Následující postup přidruží seznamu obrázků s ovládacím prvku rozšířené pole se seznamem:

### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>Přidružení seznamu obrázků s ovládacím prvku rozšířené pole se seznamem

1. Vytvoření nového seznamu obrázků (nebo použijte existující objekt seznam obrázků), pomocí [atributu CImageList](../mfc/reference/cimagelist-class.md) konstruktor a ukládání výsledný ukazatel.

1. Inicializovat nový objekt seznamu obrázků voláním [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Následující kód je jedním z příkladů tohoto volání.

   [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]

1. Přidat volitelné bitových kopií pro každý stav možné: vybraný nebo nevybrané a překrytí. Následující kód přidává tři předdefinované Image.

   [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]

1. Přidružení seznamu obrázků s ovládacím prvkem voláním [CComboBoxEx::SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist).

Jakmile seznamu obrázku přidružený k ovládacímu prvku, je jednotlivě zadat Image, kterou každá položka bude používat pro tři možné stavy. Další informace najdete v tématu [nastavení obrázků pro jednotlivé položky](../mfc/setting-the-images-for-an-individual-item.md).

## <a name="see-also"></a>Viz také

[Používání atributu CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

