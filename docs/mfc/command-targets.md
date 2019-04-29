---
title: Cíle příkazů
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: ed3d6a68967dc7f4244f887ae34760fdb99fa7f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388511"
---
# <a name="command-targets"></a>Cíle příkazů

Na obrázku [příkazy v rámci](../mfc/user-interface-objects-and-command-ids.md) zobrazuje spojení mezi objekt uživatelského rozhraní, například položky nabídky a obslužné rutiny, která volá framework k provedení příkazu výsledný při kliknutí na objekt.

Windows odešle zprávy, které nejsou příkaz zprávy přímo do okna je pak volá jehož obslužné rutiny pro zprávy. Však rozhraní směrovat příkazy na počet objektů Release candidate – nazývá "cíle příkazů", z nichž jeden obvykle vyvolá obslužnou rutinu pro příkaz. Funkce obslužných rutin fungovat i pro příkazy a standardní zprávy Windows, ale mechanismy, které se nazývají se liší, jak je vysvětleno v [jakým způsobem volá Framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Viz také:

[Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)
