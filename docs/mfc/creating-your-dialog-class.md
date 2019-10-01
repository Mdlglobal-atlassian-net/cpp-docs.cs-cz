---
title: Vytvoření třídy dialogového okna
ms.date: 09/06/2019
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: b8275754d46e9d76933624af55335e956736319a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685649"
---
# <a name="creating-your-dialog-class"></a>Vytvoření třídy dialogového okna

Pro každé dialogové okno v programu vytvořte novou třídu dialogového okna pro práci s prostředkem dialogu.

[Přidání třídy](../ide/adding-a-class-visual-cpp.md) vysvětluje, jak vytvořit novou třídu dialogového okna. Při vytváření třídy dialogového okna pomocí [Průvodce třídou](reference/mfc-class-wizard.md)zapisuje následující položky do souborů. h a. cpp, které zadáte:

V souboru. h:

- Deklarace třídy pro třídu dialogového okna. Třída je odvozena z typu [CDialog](../mfc/reference/cdialog-class.md).

V souboru. cpp:

- Mapa zprávy pro třídu.

- Standardní konstruktor pro dialogové okno.

- Přepsání členské funkce [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) Upravit tuto funkci Používá se pro výměnu dat dialogových oken a možnosti ověřování, jak je popsáno dále v tématu [Výměna a ověřování dat dialogových oken](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Další informace najdete v tématech

[Vytvoření třídy dialogového okna pomocí průvodců kódem](../mfc/creating-a-dialog-class-with-code-wizards.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
