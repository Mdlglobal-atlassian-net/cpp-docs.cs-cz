---
title: Použití ovládacího prvku horké | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be0d27016204724672c23f04fdee38f01b69e6a5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372287"
---
# <a name="using-a-hot-key-control"></a>Použití ovládacího prvku klávesová zkratka

Typické použití ovládacího prvku horké má následující formát, níže:

- Ovládací prvek je vytvořen. Pokud ovládací prvek je zadané v šablony dialogového okna, je automatické vytváření, při vytváření dialogových oken. (Byste měli mít [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) člena v vlastní třídy dialogového okna, která odpovídá výměně klíčů ovládacího prvku.) Alternativně můžete použít [vytvořit](../mfc/reference/chotkeyctrl-class.md#create) členská funkce vytvoření ovládacího prvku jako podřízeného okna z jakékoli okno.

- Pokud chcete nastavit výchozí hodnota pro ovládací prvek, zavolejte [SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey) členskou funkci. Pokud chcete zakázat určité stavy posunu, zavolejte [SetRules](../mfc/reference/chotkeyctrl-class.md#setrules). Pro ovládací prvky v dialogovém okně je vhodná doba k tomu v dialogových oken [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkce.

- Uživatel pracuje s ovládacím prvkem stisknutím klávesové kombinace kláves při výměně klíče ovládací prvek má fokus. Uživatel pak nějakým způsobem znamená, že tento úkol je dokončen, případně kliknutím na tlačítko v dialogovém okně.

- Když aplikaci zasláno oznámení, že uživatel vybral klávesové zkratky, měla by používat členskou funkci [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) načíst klíč a shift virtuální hodnoty stavu z ovládacího prvku výměně klíčů.

- Jakmile budete vědět, co uživatel vybral klíče, můžete nastavit klávesovou zkratku pomocí jedné z metod popsaných v [nastavení klávesové zkratky](../mfc/setting-a-hot-key.md).

- Při výměně klíče ovládacího prvku v dialogovém okně ho a `CHotKeyCtrl` bude objekt zničen. automaticky. Pokud ne, musíte zajistit, aby oba ovládací prvek a `CHotKeyCtrl` objektu jsou správně zničeny.

## <a name="see-also"></a>Viz také

[Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

