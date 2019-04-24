---
title: Vytvoření vlastní třídy dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: bacedc49fcdabdd5dc7fb0f392a66afd3baadd06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241755"
---
# <a name="creating-your-dialog-class"></a>Vytvoření vlastní třídy dialogového okna

Pro každý dialogové okno ve svém programu vytvořte novou třídu dialogového okna pro práci s prostředku dialogového okna.

[Přidání třídy](../ide/adding-a-class-visual-cpp.md) vysvětluje, jak vytvořit nové třídy dialogového okna. Při vytváření třídy dialogového okna pomocí Průvodce přidáním třídy zapíše následující položky. H a. Souborů CPP, kterou zadáte:

V. H souboru:

- Deklarace třídy pro třídy dialogového okna. Třída je odvozena z [CDialog](../mfc/reference/cdialog-class.md).

V. Soubor CPP:

- Mapy zpráv pro třídu.

- Standardní konstruktor pro dialogové okno.

- Přepsání [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) členskou funkci. Úprava této funkce. Používá se pro dialogové okno Možnosti výměna a ověřování dat jak je popsáno později v [výměna dat dialogových oken a ověření](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Viz také:

[Vytvoření třídy dialogového okna s použitím průvodců kódem](../mfc/creating-a-dialog-class-with-code-wizards.md)<br/>
[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)
