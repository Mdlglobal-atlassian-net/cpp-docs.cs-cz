---
title: Používání atributu CSpinButtonCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: 775668426cd11e20a4c863f07a964935d0d5420f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447187"
---
# <a name="using-cspinbuttonctrl"></a>Používání atributu CSpinButtonCtrl

Ovládací prvek *číselníku* (označuje se také jako ovládací prvek rozevíracího *seznamu* ) poskytuje dvojici šipek, na které může uživatel kliknout pro úpravu hodnoty. Tato hodnota se označuje jako *aktuální pozice*. Pozice zůstane v rozsahu tlačítka číselníku. Když uživatel klikne na šipku nahoru, poloha se přesune k maximálnímu počtu; a když uživatel klikne na šipku dolů, poloha se přesune k minimálnímu.

Ovládací prvek číselník je reprezentován v knihovně MFC třídou [atributu CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) .

> [!NOTE]
>  Ve výchozím nastavení má rozsah číselníku hodnotu Maximum nastavenou na nulu (0) a minimální hodnotu nastavenou na 100. Vzhledem k tomu, že maximální hodnota je menší než minimální hodnota, kliknutím na šipku nahoru zmenšete polohu a kliknutím na šipku dolů ji zvýšíte. Tyto hodnoty upravíte pomocí [atributu CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) .

Obvykle se aktuální pozice zobrazuje v doprovodném ovládacím prvku. Doprovodný ovládací prvek je známý jako *okno kamarád*. Ilustraci ovládacího prvku číselníku naleznete v tématu [informace o ovládacích prvcích](/windows/win32/Controls/up-down-controls) v Windows SDK.

Chcete-li vytvořit číselník a okno pro úpravu ovládacího prvku pro úpravy, v aplikaci Visual Studio nejprve přetáhněte ovládací prvek pro úpravy do dialogového okna nebo okna a poté přetáhněte ovládací prvek číselník. Vyberte číselník a nastavte jeho **Automatický kamarád** a nastavte vlastnosti **kamarádho celého čísla** na **hodnotu true**. Také nastavte vlastnost **Zarovnání** ; **Zarovnání doprava** je nejtypickou. Pomocí těchto nastavení je ovládací prvek pro úpravy nastaven jako okno kamarád, protože přímo předchází ovládacímu prvku pro úpravy v pořadí prvků. Ovládací prvek pro úpravy zobrazuje celá čísla a číselník je vložen do pravé strany ovládacího prvku pro úpravy. Volitelně můžete nastavit platný rozsah číselníku pomocí metody [atributu CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) . Pro komunikaci mezi číselníkem a přítelem okna nejsou vyžadovány žádné obslužné rutiny událostí, protože data přímo vyměňují. Pokud používáte číselník pro nějaký jiný účel, například pro stránku pomocí sekvence oken nebo dialogových oken, přidejte obslužnou rutinu pro UDN_DELTAPOSovou zprávu a proveďte vlastní akci tam.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Styly číselníků](../mfc/spin-button-styles.md)

- [Členské funkce číselníku](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Viz také

[Ovládací prvky](../mfc/controls-mfc.md)
