---
title: Použití ovládacích prvků posuvník
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
ms.openlocfilehash: b358b4e92c7d9f214291b047a080f71b48183519
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284135"
---
# <a name="using-slider-controls"></a>Použití ovládacích prvků posuvník

Typické použití ovládacího prvku jezdec má následující formát, níže:

- Ovládací prvek je vytvořen. Pokud ovládací prvek je zadané v šablony dialogového okna, je automatické vytváření, při vytváření dialogových oken. (Byste měli mít [atributu CSliderCtrl](../mfc/reference/csliderctrl-class.md) člena v vlastní třídy dialogového okna, která odpovídá v ovládacím prvku posuvník.) Alternativně můžete použít [vytvořit](../mfc/reference/csliderctrl-class.md#create) členská funkce vytvoření ovládacího prvku jako podřízeného okna z jakékoli okno.

- Volejte různé členské funkce Set k nastavení hodnot pro ovládací prvek. Změny, které můžete provést zahrnují nastavení minimální a maximální pozice pro posuvník, značky kreslení, nastavení oblast výběru a změnou pozice posuvníku. Pro ovládací prvky v dialogovém okně je vhodná doba k tomu v dialogovém okně [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkce.

- Během interakce uživatele s ovládacím prvkem, odešle různé zprávy s oznámením. Hodnota posuvníku se dají extrahovat z ovládacího prvku pomocí volání [GetPos](../mfc/reference/csliderctrl-class.md#getpos) členskou funkci.

- Jakmile budete hotovi s ovládacím prvkem, budete muset Ujistěte se, že je správně zničeny. Pokud je ovládací prvek posuvník v dialogovém okně ho a `CSliderCtrl` bude objekt zničen. automaticky. Pokud ne, musíte zajistit, aby oba ovládací prvek a `CSliderCtrl` objektu jsou správně zničeny.

## <a name="see-also"></a>Viz také:

[Používání atributu CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
