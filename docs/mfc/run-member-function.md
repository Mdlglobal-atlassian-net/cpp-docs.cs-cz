---
title: Run – členská funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 446b1b6fc2a5265e2c4eb8a608ff8b4f0028c57d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408229"
---
# <a name="run-member-function"></a>Run – členská funkce

Rozhraní framework aplikace tráví většinu času v [spustit](../mfc/reference/cwinapp-class.md#run) členské funkce třídy [CWinApp](../mfc/reference/cwinapp-class.md). Po inicializaci `WinMain` volání `Run` ke zpracování smyčky zpráv.

`Run` procházení smyčku zpráv kontroly fronty zpráv pro zprávy k dispozici. Pokud je k dispozici, zprávu `Run` odešle pro akci. Pokud nejsou k dispozici žádné zprávy, což je často hodnotu true, `Run` volání `OnIdle` provedete jakékoli doby nečinnosti zpracování, které vy nebo rozhraní může být nutné provést. Pokud neexistují žádné zprávy a žádné zpracování při nečinnosti, které provedete, aplikace počká, až se něco stane. Při ukončení aplikace `Run` volání `ExitInstance`. Obrázek v [ONIDLE – členská funkce](../mfc/onidle-member-function.md) zobrazuje posloupnost akcí ve smyčce zpráv.

Odesílání zpráv, závisí na druhu zprávy. Další informace najdete v tématu [zprávy a příkazy v rámci](../mfc/messages-and-commands-in-the-framework.md).

## <a name="see-also"></a>Viz také

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
