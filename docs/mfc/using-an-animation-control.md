---
title: Použití ovládacího prvku animace
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
ms.openlocfilehash: 10bd8c0c26f92ce5de2261d6aca6fc7cc3a37365
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274632"
---
# <a name="using-an-animation-control"></a>Použití ovládacího prvku animace

Typické použití ovládacího prvku animace má následující formát, níže:

- Ovládací prvek je vytvořen. Pokud ovládací prvek je zadané v šablony dialogového okna, je automatické vytváření, při vytváření dialogových oken. (Byste měli mít [atributu CAnimateCtrl](../mfc/reference/canimatectrl-class.md) člena v vlastní třídy dialogového okna, která odpovídá do ovládacího prvku animace.) Alternativně můžete použít [vytvořit](../mfc/reference/canimatectrl-class.md#create) členská funkce vytvoření ovládacího prvku jako podřízeného okna z jakékoli okno.

- Načtení klip AVI do ovládacího prvku animace voláním [otevřít](../mfc/reference/canimatectrl-class.md#open) členskou funkci. Pokud je váš ovládací prvek animace v dialogovém okně, je vhodné místo k tomu ve třídě dialog [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkce.

- Přehrajte klip voláním [Přehrát](../mfc/reference/canimatectrl-class.md#play) členskou funkci. Pokud je váš ovládací prvek animace v dialogovém okně, je vhodné místo k tomu ve třídě dialog `OnInitDialog` funkce. Volání `Play` není nezbytné, pokud je nastaven styl ACS_AUTOPLAY ovládací prvek animace.

- Pokud chcete zobrazit části klipu nebo přehrát jej jednotlivých snímcích, použijte `Seek` členskou funkci. Chcete-li zastavit klip přehrává, použijte `Stop` členskou funkci.

- Pokud nebudete ke zničení ovládacího prvku hned, odeberte klip z paměti při volání `Close` členskou funkci.

- Pokud je ovládací prvek animace v dialogovém okně ho a `CAnimateCtrl` bude objekt zničen. automaticky. Pokud ne, musíte zajistit, aby oba ovládací prvek a `CAnimateCtrl` objektu jsou správně zničeny. Zničení ovládacího prvku automaticky zavře klip AVI.

## <a name="see-also"></a>Viz také:

[Používání atributu CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
