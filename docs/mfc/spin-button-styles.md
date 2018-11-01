---
title: Styly číselníků
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: 73042dbbdc28819ecc736c282599189ee074ce77
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457106"
---
# <a name="spin-button-styles"></a>Styly číselníků

Mnoho nastavení typu číselník ([atributu CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) se řídí styly. Můžete nastavit následující styly pomocí **vlastnosti** okna v editoru dialogového okna.

- **Orientace** svislý nebo vodorovný. Určuje orientaci ovládacího prvku tlačítka se šipkami. Související se stylem UDS_HORZ.

- **Zarovnání** nepřipojené, vlevo nebo vpravo. Určuje umístění číselníku. Levá a pravá umístit vedle asociované okno číselníku. Šířka asociovaného okna se sníží tak, aby vyhovovaly číselníku. Styly UDS_ALIGNLEFT a UDS_ALIGNRIGHT přidružený.

- **Auto Buddy** automaticky vybere předchozí okno v pořadí vykreslování jako asociované okno na číselníku. V šabloně dialogu Toto je ovládací prvek, který předchází číselníku v pořadí. Související se stylem UDS_AUTOBUDDY.

- **Nastavte Buddy Integer** způsobí, že ovládací prvek typu číselník zvýší a sníží titulek asociovaného okna jako aktuální pozici změny. Související se stylem UDS_SETBUDDYINT.

- **No Thousands** nevkládá tisíců oddělovač v hodnotě v popiscích asociovaného okna. Související se stylem UDS_NOTHOUSANDS.

    > [!NOTE]
    >  Tento styl nastavte, pokud chcete používat výměna dat dialogových oken (DDX) k získání celočíselnou hodnotu z přidružený ovládací prvek. `DDX_Text` nepřijímá vložený oddělovače tisíců.

- **Zabalení** způsobí, že pozice "zabalení", protože hodnota je zvýšena nebo snížena nad rámec přesahují rozsah ovládacího prvku. Související se stylem UDS_WRAP.

- **Klávesy se šipkami** způsobí, že typu číselník tlačítko přičtena nebo odečtena pozice při stisknutí kláves Šipka nahoru a Šipka dolů. Související se stylem UDS_ARROWKEYS.

## <a name="see-also"></a>Viz také

[Používání atributu CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

