---
title: Vytvoření vlastní třídy dialogového okna
ms.date: 09/06/2019
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: 424d18196063456245e2a4841b42e6e447bded17
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907330"
---
# <a name="creating-your-dialog-class"></a>Vytvoření vlastní třídy dialogového okna

Pro každé dialogové okno v programu vytvořte novou třídu dialogového okna pro práci s prostředkem dialogu.

[Přidání třídy](../ide/adding-a-class-visual-cpp.md) vysvětluje, jak vytvořit novou třídu dialogového okna. Při vytváření třídy dialogového okna pomocí [Průvodce třídou](reference/mfc-class-wizard.md)zapisuje následující položky do souborů. h a. cpp, které zadáte:

V souboru. h:

- Deklarace třídy pro třídu dialogového okna. Třída je odvozena z typu [CDialog](../mfc/reference/cdialog-class.md).

V souboru. cpp:

- Mapa zprávy pro třídu.

- Standardní konstruktor pro dialogové okno.

- Přepsání členské funkce [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) Upravit tuto funkci Používá se pro výměnu dat dialogových oken a možnosti ověřování, jak je popsáno dále v tématu [Výměna a ověřování dat dialogových oken](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Viz také:

[Vytvoření třídy dialogového okna s použitím průvodců kódem](../mfc/creating-a-dialog-class-with-code-wizards.md)<br/>
[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)
