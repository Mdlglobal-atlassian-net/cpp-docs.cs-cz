---
title: Použití seznamu obrázků s ovládacím prvkem matrice
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
ms.openlocfilehash: 3cf359a5d06396f9c2c31cbec511c04784053e53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641431"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>Použití seznamu obrázků s ovládacím prvkem matrice

Každé vzdálené matrice může obsahovat mimo jiné bitové kopie ze seznamu obrázků přidružené. Následující postup podrobně popisuje nezbytné kroky pro zobrazení obrázku ve svazku matrice.

### <a name="to-display-images-in-a-rebar-band"></a>K zobrazení obrázků v pruhy matrice

1. Připojení seznamu obrázků na váš objekt ovládacího prvku matrice tím, že zavoláte na [SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist), předání ukazatele na existující seznam obrázků.

1. Upravit **REBARBANDINFO** struktura přiřadit pruhy matrice image:

   - Nastavte *fMask* člen `RBBIM_IMAGE`, zahrňte další příznaky podle potřeby pomocí bitového operátoru OR.

   - Nastavte *iImage* člena do seznamu index bitové kopie bitové kopie má být zobrazen.

1. Inicializuje všechny zbývající datové členy, jako je například velikost, text a popisovač omezením podřízené okno, potřebné informace.

1. Vložit nový mimo pásmo (s obrázkem) pomocí volání [CReBarCtrl::InsertBand](../mfc/reference/crebarctrl-class.md#insertband), předejte **REBARBANDINFO** struktury.

V následujícím příkladu se předpokládá, že existující objekt seznamu obrázků s dvě bitové kopie byl připojen k objektu ovládacího prvku matrice (`m_wndReBar`). Nové vzdálené matrice (definované `rbi`), který obsahuje první image, je přidán voláním `InsertBand`:

[!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]

## <a name="see-also"></a>Viz také

[Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

