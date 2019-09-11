---
title: Styly číselníků
ms.date: 09/09/2019
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: 1aae4b7e4c63929ebe03c97d50f05754bc13ec26
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907862"
---
# <a name="spin-button-styles"></a>Styly číselníků

Mnohé z nastavení pro tlačítko číselníku ([atributu CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) jsou ovládány styly. Můžete nastavit následující styly pomocí [Průvodce třídou](reference/mfc-class-wizard.md).

- **Orientace** Buď svislá, nebo vodorovná. Určuje orientaci tlačítek se šipkami. Přidruženo k UDS_HORZ stylu.

- **Zarovnání** Jedna z nepřipojeného, levého nebo pravého. Určuje umístění tlačítka pro otočení. Vlevo a vpravo umístěte tlačítko číselníku vedle okna s kamarádem. Šířka okna kamaráda se zmenší tak, aby se přizpůsobila k tlačítku číselníku. Přidruženo ke stylům UDS_ALIGNLEFT a UDS_ALIGNRIGHT.

- **Automatický kamarád** Automaticky vybere předchozí okno v pořadí vykreslování jako přítel pro tlačítko číselníku. V šabloně dialogového okna se jedná o ovládací prvek, který předchází číselníku v pořadí ovládacích prvků. Přidruženo k UDS_AUTOBUDDY stylu.

- **Nastavit celé číslo kamaráda** Způsobí, že číselník zvýší a sníží titulek okna kamaráda při změně aktuální pozice. Přidruženo k UDS_SETBUDDYINT stylu.

- **Žádné tisíce** Nevloží oddělovač tisíců do hodnoty v popisku okna kamarád. Přidruženo k UDS_NOTHOUSANDS stylu.

    > [!NOTE]
    >  Tento styl nastavte, pokud chcete k získání celočíselné hodnoty z kamarádního ovládacího prvku použít dialogové okno výměny dat (DDX). `DDX_Text`nepřijímá vložené oddělovače tisíců.

- **Zalamovat** Způsobí, že je pozice "Wrap" nastavena jako hodnota zvětšena nebo snížena nad rozsah ovládacího prvku. Přidruženo k UDS_WRAP stylu.

- **Klávesy se šipkami** Způsobí, že číselník zvýší nebo sníží pozici při stisknutí kláves Šipka nahoru a dolů. Přidruženo k UDS_ARROWKEYS stylu.

## <a name="see-also"></a>Viz také:

[Používání atributu CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
