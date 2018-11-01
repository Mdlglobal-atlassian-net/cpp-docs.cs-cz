---
title: Jak se nepříkazové zprávy dostanou k svým obslužným rutinám
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: f64eb97315b41a314c791e1a4c5bc7721b329fca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545454"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Jak se nepříkazové zprávy dostanou k svým obslužným rutinám

Na rozdíl od příkazů standardní zprávy Windows získat nebyl směrován přes příkaz of řetězec cíle, ale jsou obvykle zpracovávány v okně Windows odešle zprávu. V okně může být hlavní okno rámce, podřízené okno MDI, standardního ovládacího prvku, dialogové okno, zobrazení nebo jiný typ podřízené okno.

V době běhu, každé okno Windows připojené k objekt window (odvozený přímo nebo nepřímo z `CWnd`), který má svou vlastní mapy a obslužné rutiny funkce přidružené zprávy. Rozhraní používá mapu zpráv, jako u příkazu – k mapování příchozích zpráv pro obslužné rutiny.

## <a name="see-also"></a>Viz také

[Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

