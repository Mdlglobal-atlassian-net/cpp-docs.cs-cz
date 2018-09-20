---
title: Jak se Nepříkazové zprávy jejich obslužné rutiny | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5c38a1d4294993170cfeff64be6a83700fa7497
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373435"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Jak se nepříkazové zprávy dostanou k svým obslužným rutinám

Na rozdíl od příkazů standardní zprávy Windows získat nebyl směrován přes příkaz of řetězec cíle, ale jsou obvykle zpracovávány v okně Windows odešle zprávu. V okně může být hlavní okno rámce, podřízené okno MDI, standardního ovládacího prvku, dialogové okno, zobrazení nebo jiný typ podřízené okno.

V době běhu, každé okno Windows připojené k objekt window (odvozený přímo nebo nepřímo z `CWnd`), který má svou vlastní mapy a obslužné rutiny funkce přidružené zprávy. Rozhraní používá mapu zpráv, jako u příkazu – k mapování příchozích zpráv pro obslužné rutiny.

## <a name="see-also"></a>Viz také

[Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

