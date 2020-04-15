---
title: Používání atributu CSpinButtonCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: 6f72601d3813f36e4a99b9ab04f2e9383c58df94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366487"
---
# <a name="using-cspinbuttonctrl"></a>Používání atributu CSpinButtonCtrl

Ovládací prvek *číselníku* (označovaný také jako ovládací prvek *nahoru dolů)* poskytuje dvojici šipek, na které může uživatel klepnout a upravit hodnotu. Tato hodnota se označuje jako *aktuální pozice*. Poloha zůstává v dosahu číselníku. Když uživatel klepne na šipku nahoru, pozice se přesune směrem k maximu; a když uživatel klepne na šipku dolů, pozice se posune směrem k minimu.

Ovládací prvek číselníku je v knihovně MFC reprezentován třídou [CSpinButtonCtrl.](../mfc/reference/cspinbuttonctrl-class.md)

> [!NOTE]
> Ve výchozím nastavení má rozsah číselníku maximální hodnotu nastavenou na nulu (0) a minimální hodnotu 100. Protože maximální hodnota je menší než minimální hodnota, klepnutím na šipku nahoru se pozice sníží a klepnutím na šipku dolů ji zvýšíte. Pomocí [cspinbuttonctrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) upravte tyto hodnoty.

Obvykle aktuální pozice se zobrazí v doprovodné ovládací prvek. Doprovodný ovládací prvek se označuje jako *okno kamaráda*. Obrázek ovládacího prvku číselníku naleznete v tématu [O ovládacích prvcích nahoru dolů](/windows/win32/Controls/up-down-controls) v sadě Windows SDK.

Chcete-li vytvořit ovládací prvek pro číselník a okno kamaráda ovládacího prvku pro úpravy, přetáhněte v sadě Visual Studio nejprve ovládací prvek pro úpravy do dialogového okna nebo okna a potom přetáhněte ovládací prvek pro číselník. Vyberte ovládací prvek odstřeďování a nastavte jeho vlastnosti **Auto Buddy** a **Set Buddy Integer** na **True**. Nastavte také **vlastnost Alignment;** **Zarovnat doprava** je nejtypičtější. S těmito nastaveními je ovládací prvek pro úpravy nastaven jako okno kamaráda, protože přímo předchází ovládacímu prvku úprav v pořadí polí. Ovládací prvek pro úpravy zobrazí celá čísla a ovládací prvek odstřeďování je vložen na pravé straně ovládacího prvku pro úpravy. Volitelně můžete nastavit platný rozsah ovládacího prvku odstřeďování pomocí metody [CSpinButtonCtrl::SetRange.](../mfc/reference/cspinbuttonctrl-class.md#setrange) Žádné obslužné rutiny událostí jsou nutné ke komunikaci mezi spin control a buddy okno, protože si vyměňují data přímo. Pokud používáte spin ovládací prvek pro jiný účel, například stránku přes posloupnost oken nebo dialogových oken, přidejte obslužnou rutinu pro UDN_DELTAPOS zprávy a proveďte vlastní akci tam.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Styly číselníků](../mfc/spin-button-styles.md)

- [Členské funkce číselníku](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Viz také

[Ovládací prvky](../mfc/controls-mfc.md)
