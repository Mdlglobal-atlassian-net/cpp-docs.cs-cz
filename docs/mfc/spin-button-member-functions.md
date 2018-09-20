---
title: Členské funkce číselníku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88f00aedcf269996277c154f9dd051534a9c5e49
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431518"
---
# <a name="spin-button-member-functions"></a>Členské funkce číselníku

Nejsou k dispozici pro ovládací prvek typu číselník několik členské funkce ([atributu CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)). Pomocí těchto funkcí můžete změnit následující atributy číselníku.

- **Akcelerace** můžete nastavit rychlost, jakou změny pozice, pokud uživatel obsahuje tlačítko se šipkou dolů. Chcete-li pracovat s akcelerace, použijte [SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel) a [GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel) členské funkce.

- **Základní** změníte base (10 nebo 16) slouží k zobrazení umístění v titulku asociovaného okna. Chcete-li pracovat s základní třídy, použijte [getbase –](../mfc/reference/cspinbuttonctrl-class.md#getbase) a [SetBase](../mfc/reference/cspinbuttonctrl-class.md#setbase) členské funkce.

- **Kamarád okno** můžete dynamicky nastavovat asociovaného okna. Chcete-li zadat dotaz nebo změnit, který ovládací prvek je asociovaného okna, použijte [GetBuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy) a [SetBuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy) členské funkce.

- **Pozice** můžete zadávat dotazy a změnit umístění. Chcete-li pracovat přímo s umístěním, použijte [GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos) a [SetPos](../mfc/reference/cspinbuttonctrl-class.md#setpos) členské funkce. Protože titulek přidružený ovládací prvek se možná změnily (například v případě, že je buddy ovládacího prvku pro úpravy), `GetPos` načte aktuální titulek a odpovídajícím způsobem upraví pozici.

- **Rozsah** můžete změnit maximální a minimální pozici číselníku. Ve výchozím nastavení maximální délka je nastavena na hodnotu 0 a minimum je nastavena na hodnotu 100. Protože výchozí maximum je menší než výchozí minimální, je counter-intuitive akce tlačítka se šipkami. Obvykle se nastavit rozsah pomocí [SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) členskou funkci. K dotazování použít rozsah [getrange –](../mfc/reference/cspinbuttonctrl-class.md#getrange).

## <a name="see-also"></a>Viz také

[Používání atributu CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

