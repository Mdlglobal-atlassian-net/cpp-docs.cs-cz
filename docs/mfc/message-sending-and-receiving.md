---
title: Odesílání a příjem zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
ms.openlocfilehash: 95a54f3a518be19c7ae6f001e3096b825e64c0c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447395"
---
# <a name="message-sending-and-receiving"></a>Odesílání a příjem zpráv

Vezměte v úvahu odesílání součástí procesu a jak rozhraní reagovat.

Většina výsledek zprávy z interakce uživatele s programem. Příkazy jsou generovány pomocí kliknutí myší položky nabídky nebo tlačítka na panelu nástrojů nebo stisknutí kláves akcelerátoru. Uživatel také například generování zpráv Windows, přesunutí nebo změně velikosti okna. Další zprávy Windows jsou odesílány při výskytu události, například spuštění programu nebo ukončení windows získat nebo ztratí fokus a tak dále. Zprávy s oznámením ovládacího prvku jsou generovány kliknutí myší nebo další interakce uživatele s ovládacím prvkem, jako je například ovládací prvek tlačítko nebo pole se seznamem v dialogovém okně.

`Run` Členské funkce třídy `CWinApp` načítá zprávy a odešle je do příslušné okno. Většina příkazů zpráv se odesílají do okna hlavního rámce aplikace. `WindowProc` Předdefinovaná v nástroji získá knihovny tříd zpráv a směruje je jinak v závislosti na kategorii byla přijata zpráva.

Teď se podíváme přijímající součástí procesu.

Počáteční příjemce zprávy musí být objekt okna. Zprávy Windows jsou obvykle zpracovávány přímo tento objekt okna. Příkaz zpráv, obvykle pocházejí z okna hlavního rámce aplikace směrované do řetězce cíl příkazu je popsáno v [směrování příkazů](../mfc/command-routing.md).

Každý objekt schopná přijmout zprávy nebo příkazů má svůj vlastní zprávu mapování této páry zprávu nebo příkaz s názvem její obslužná rutina.

Pokud cíl příkazu objekt obdrží zprávu nebo příkaz, hledá jeho mapy zpráv pro shody. Pokud najde obslužné rutiny pro zprávy, volá obslužná rutina. Další informace o tom, jak jsou prohledávány mapy zpráv, najdete v části [jak rámci vyhledávání mapy zpráv](../mfc/how-the-framework-searches-message-maps.md). Znovu najdete na obrázku [příkazy v rámci](../mfc/user-interface-objects-and-command-ids.md).

## <a name="see-also"></a>Viz také

[Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

