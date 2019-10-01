---
title: Mapování zpráv systému Windows na třídu
ms.date: 09/06/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
- Class Wizard [MFC]
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 0f1207faca56acd709db86478722eba85eeb284a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685612"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mapování zpráv systému Windows na třídu

Pokud potřebujete, aby vaše dialogové okno zpracovávala zprávy systému Windows, přepište příslušné funkce obslužných rutin. Provedete to tak, že vyberete kartu **zobrazení tříd** v **Průzkumník řešení**, kliknete pravým tlačítkem na třídu, která představuje dialogové okno, a zvolíte možnost [Průvodce třídami](reference/mfc-class-wizard.md). Pomocí průvodce [namapujte zprávy](../mfc/reference/mapping-messages-to-functions.md) na třídu dialogového okna. Tím zapíšete položku mapování zpráv pro každou zprávu a přidáte do třídy členské funkce obslužné rutiny zpráv. Použijte Editor kódu k psaní kódu v obslužných rutinách zpráv.

Můžete také přepsat členské funkce [CDialog](../mfc/reference/cdialog-class.md) a její základní třídy, zejména [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)

- [Běžně přepsané členské funkce](../mfc/commonly-overridden-member-functions.md)

- [Běžně přidávané členské funkce](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>Další informace najdete v tématech

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
