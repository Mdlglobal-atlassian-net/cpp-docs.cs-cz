---
title: Použití ovládacích prvků posuvník | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0496a15b289ec055fd2706975603f25cef13938
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388833"
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

