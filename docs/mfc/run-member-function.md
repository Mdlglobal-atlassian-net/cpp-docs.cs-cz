---
title: Run – členská funkce
ms.date: 11/04/2016
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
ms.openlocfilehash: 8e6e74b8f0fd62f96d6d846bbba867f9189550ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666853"
---
# <a name="run-member-function"></a>Run – členská funkce

Rozhraní framework aplikace tráví většinu času v [spustit](../mfc/reference/cwinapp-class.md#run) členské funkce třídy [CWinApp](../mfc/reference/cwinapp-class.md). Po inicializaci `WinMain` volání `Run` ke zpracování smyčky zpráv.

`Run` procházení smyčku zpráv kontroly fronty zpráv pro zprávy k dispozici. Pokud je k dispozici, zprávu `Run` odešle pro akci. Pokud nejsou k dispozici žádné zprávy, což je často hodnotu true, `Run` volání `OnIdle` provedete jakékoli doby nečinnosti zpracování, které vy nebo rozhraní může být nutné provést. Pokud neexistují žádné zprávy a žádné zpracování při nečinnosti, které provedete, aplikace počká, až se něco stane. Při ukončení aplikace `Run` volání `ExitInstance`. Obrázek v [ONIDLE – členská funkce](../mfc/onidle-member-function.md) zobrazuje posloupnost akcí ve smyčce zpráv.

Odesílání zpráv, závisí na druhu zprávy. Další informace najdete v tématu [zprávy a příkazy v rámci](../mfc/messages-and-commands-in-the-framework.md).

## <a name="see-also"></a>Viz také

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
