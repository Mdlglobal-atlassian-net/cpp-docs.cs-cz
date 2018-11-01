---
title: OnCmdMsg – obslužná rutina
ms.date: 11/04/2016
f1_keywords:
- OnCmdMsg
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
ms.openlocfilehash: 37b3d5ffa3e6492c8c00b8b22eba58d09fad51f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643167"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg – obslužná rutina

K provedení směrování příkazů, každý cíl příkazu volá `OnCmdMsg` členská funkce další příkaz cíle v sekvenci. Příkaz, zaměřuje použití `OnCmdMsg` a určit, jestli se dokáže zpracovat příkaz směrovat na jiný cíl příkazu, pokud se ji nejde zpracovat.

Každý cíl příkazu třída může přepsat `OnCmdMsg` členskou funkci. Přepsání nechte každé třídy směrování příkazů konkrétní cílový Další. Okno rámce, například vždy směrovat příkazy na její aktuální podřízené okno nebo zobrazení, jak je znázorněno v tabulce [trasy standardní příkaz](../mfc/command-routing.md).

Výchozí hodnota `CCmdTarget` provádění `OnCmdMsg` mapu zpráv příkaz cílové třídy používá k hledání pro obslužnou rutinu pro každý příkaz přijímá – stejným způsobem, že budou vyhledány standardní zprávy. Pokud se najde shodu, zavolá obslužnou rutinu. Vyhledávání map zpráv je podrobně [jak rámci vyhledávání mapy zpráv](../mfc/how-the-framework-searches-message-maps.md).

## <a name="see-also"></a>Viz také

[Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

