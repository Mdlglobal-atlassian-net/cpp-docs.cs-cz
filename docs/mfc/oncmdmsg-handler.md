---
title: Oncmdmsg – obslužná rutina | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnCmdMsg
dev_langs:
- C++
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6691e4935d46b32bc8f433823888bb7f53a36890
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398830"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg – obslužná rutina

K provedení směrování příkazů, každý cíl příkazu volá `OnCmdMsg` členská funkce další příkaz cíle v sekvenci. Příkaz, zaměřuje použití `OnCmdMsg` a určit, jestli se dokáže zpracovat příkaz směrovat na jiný cíl příkazu, pokud se ji nejde zpracovat.

Každý cíl příkazu třída může přepsat `OnCmdMsg` členskou funkci. Přepsání nechte každé třídy směrování příkazů konkrétní cílový Další. Okno rámce, například vždy směrovat příkazy na její aktuální podřízené okno nebo zobrazení, jak je znázorněno v tabulce [trasy standardní příkaz](../mfc/command-routing.md).

Výchozí hodnota `CCmdTarget` provádění `OnCmdMsg` mapu zpráv příkaz cílové třídy používá k hledání pro obslužnou rutinu pro každý příkaz přijímá – stejným způsobem, že budou vyhledány standardní zprávy. Pokud se najde shodu, zavolá obslužnou rutinu. Vyhledávání map zpráv je podrobně [jak rámci vyhledávání mapy zpráv](../mfc/how-the-framework-searches-message-maps.md).

## <a name="see-also"></a>Viz také

[Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

