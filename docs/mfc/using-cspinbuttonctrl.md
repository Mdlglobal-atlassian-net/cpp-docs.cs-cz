---
title: Používání atributu CSpinButtonCtrl | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CSpinButtonCtrl
dev_langs:
- C++
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0dfffa5a7ec315c0bc8af93a7cf825c62494bd02
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415392"
---
# <a name="using-cspinbuttonctrl"></a>Používání atributu CSpinButtonCtrl

*Číselníku* ovládacího prvku (označované také jako *nahoru dolů* ovládací prvek) poskytuje dvojice šipek, které může uživatel klepnout na hodnotu upravit. Tato hodnota se označuje jako *aktuální pozici*. Pozice zůstane v rozsahu číselníku. Když uživatel klepne na šipku nahoru, pozice blíží maximální; a když uživatel klepne na šipku dolů, pozice blíží minimální.

Ovládací prvek typu číselník tlačítko je reprezentován v knihovně MFC podle [atributu CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) třídy.

> [!NOTE]
>  Rozsah číselníku má standardně nastavena na hodnotu 100 minimální a maximální doba, nastavit na nulu (0). Vzhledem k tomu, že maximální hodnota je menší než minimální hodnota, kliknutím na šipku nahoru snižuje pozice a kliknutím na šipku dolů zvyšuje. Použití [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) upravit tyto hodnoty.

Obvykle se zobrazí aktuální pozici v ovládacím prvku doprovodná. Ovládací prvek doprovodného se označuje jako *asociované okno*. Pro ilustraci ovládací prvek číselníku, naleznete v tématu [o ovládací prvky typu obousměrný číselník](/windows/desktop/Controls/up-down-controls) v sadě Windows SDK.

Chcete-li vytvořit ovládací prvek typu číselník a upravit ovládací prvek asociované okno, v sadě Visual Studio, nejdřív přetáhněte ovládací prvek úprav nebo dialogovém okně a potom přetáhněte ovládací prvek typu číselník. Vyberte ovládací prvek typu číselník a nastavte jeho **Auto Buddy** a **nastavit Buddy Integer** vlastností **True**. Také nastavit **zarovnání** vlastnosti; **Zarovnat doprava** je obvykle. S těmito nastaveními je ovládací prvek pro úpravy nastavit jako asociované okno, protože přímo předchází ovládací prvek pro úpravy v pořadí. Zobrazí textové pole celých čísel a otočný ovládací prvek se vloží na pravé straně ovládacích prvků pro úpravy. Volitelně můžete nastavit platný rozsah otočný ovládací prvek pomocí [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) metody. Žádné obslužné rutiny událostí jsou nutné pro komunikaci mezi otočný ovládací prvek a asociované okno vzhledem k tomu, že si vyměňují data přímo. Pokud používáte otočný ovládací prvek pro některé jiné účely, třeba stránkovat posloupnost windows nebo dialogových oknech, pak přidejte obslužné rutiny pro zprávy UDN_DELTAPOS a provedení vlastní akce došlo.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Styly číselníků](../mfc/spin-button-styles.md)

- [Členské funkce číselníku](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Viz také

[Ovládací prvky](../mfc/controls-mfc.md)

