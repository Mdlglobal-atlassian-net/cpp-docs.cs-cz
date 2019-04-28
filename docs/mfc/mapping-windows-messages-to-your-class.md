---
title: Mapování zpráv systému Windows na třídu
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 7e15f52e41d4ac91a839629342258128db86e2d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363840"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mapování zpráv systému Windows na třídu

Pokud potřebujete vašem dialogovém okně pro zpracování zpráv Windows, přepište odpovídající obslužná rutina funkce. Uděláte to tak, použijte okno Vlastnosti k [mapování zpráv](../mfc/reference/mapping-messages-to-functions.md) pro třídu dialog. To zapíše položku mapování zpráv pro každou zprávu a přidá popisovač zprávy členské funkce třídy. Editor zdrojového kódu jazyka Visual C++ můžete psát kód v obslužné rutiny zpráv.

Můžete členské funkce také přepsat [CDialog](../mfc/reference/cdialog-class.md) a její základní třídy, zejména [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)

- [Běžně přepisované členské funkce](../mfc/commonly-overridden-member-functions.md)

- [Běžně přidávané členské funkce](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>Viz také:

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)
