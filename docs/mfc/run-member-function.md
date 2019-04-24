---
title: Run – členská funkce
ms.date: 11/04/2016
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
ms.openlocfilehash: 8271a10ad7439d2795dcc45d667b23b0932a0486
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308547"
---
# <a name="run-member-function"></a>Run – členská funkce

Rozhraní framework aplikace tráví většinu času v [spustit](../mfc/reference/cwinapp-class.md#run) členské funkce třídy [CWinApp](../mfc/reference/cwinapp-class.md). Po inicializaci `WinMain` volání `Run` ke zpracování smyčky zpráv.

`Run` procházení smyčku zpráv kontroly fronty zpráv pro zprávy k dispozici. Pokud je k dispozici, zprávu `Run` odešle pro akci. Pokud nejsou k dispozici žádné zprávy, což je často hodnotu true, `Run` volání `OnIdle` provedete jakékoli doby nečinnosti zpracování, které vy nebo rozhraní může být nutné provést. Pokud neexistují žádné zprávy a žádné zpracování při nečinnosti, které provedete, aplikace počká, až se něco stane. Při ukončení aplikace `Run` volání `ExitInstance`. Obrázek v [ONIDLE – členská funkce](../mfc/onidle-member-function.md) zobrazuje posloupnost akcí ve smyčce zpráv.

Odesílání zpráv, závisí na druhu zprávy. Další informace najdete v tématu [zprávy a příkazy v rámci](../mfc/messages-and-commands-in-the-framework.md).

## <a name="see-also"></a>Viz také:

[CWinApp Třída aplikace](../mfc/cwinapp-the-application-class.md)
