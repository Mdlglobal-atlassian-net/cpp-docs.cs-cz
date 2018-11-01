---
title: Použití ovládacích prvků posuvník
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
ms.openlocfilehash: 7bb5bda4a7b85ea8bb852649b20f10f0c4693188
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533559"
---
# <a name="using-slider-controls"></a>Použití ovládacích prvků posuvník

Typické použití ovládacího prvku jezdec má následující formát, níže:

- Ovládací prvek je vytvořen. Pokud ovládací prvek je zadané v šablony dialogového okna, je automatické vytváření, při vytváření dialogových oken. (Byste měli mít [atributu CSliderCtrl](../mfc/reference/csliderctrl-class.md) člena v vlastní třídy dialogového okna, která odpovídá v ovládacím prvku posuvník.) Alternativně můžete použít [vytvořit](../mfc/reference/csliderctrl-class.md#create) členská funkce vytvoření ovládacího prvku jako podřízeného okna z jakékoli okno.

- Volejte různé členské funkce Set k nastavení hodnot pro ovládací prvek. Změny, které můžete provést zahrnují nastavení minimální a maximální pozice pro posuvník, značky kreslení, nastavení oblast výběru a změnou pozice posuvníku. Pro ovládací prvky v dialogovém okně je vhodná doba k tomu v dialogovém okně [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkce.

- Během interakce uživatele s ovládacím prvkem, odešle různé zprávy s oznámením. Hodnota posuvníku se dají extrahovat z ovládacího prvku pomocí volání [GetPos](../mfc/reference/csliderctrl-class.md#getpos) členskou funkci.

- Jakmile budete hotovi s ovládacím prvkem, budete muset Ujistěte se, že je správně zničeny. Pokud je ovládací prvek posuvník v dialogovém okně ho a `CSliderCtrl` bude objekt zničen. automaticky. Pokud ne, musíte zajistit, aby oba ovládací prvek a `CSliderCtrl` objektu jsou správně zničeny.

## <a name="see-also"></a>Viz také

[Používání atributu CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

