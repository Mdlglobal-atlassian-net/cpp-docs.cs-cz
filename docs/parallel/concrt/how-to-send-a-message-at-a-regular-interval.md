---
title: 'Postupy: Odesílání zpráv v pravidelných intervalech'
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: 05777b0c00f587f588a50733d5113d9a7362d247
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549614"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Postupy: Odesílání zpráv v pravidelných intervalech

Tento příklad ukazuje způsob použití souběžnost::[timer – třída](../../parallel/concrt/reference/timer-class.md) k odesílání zpráv v pravidelných intervalech.

## <a name="example"></a>Příklad

Následující příklad používá `timer` objekt sestavy pokroku během operace s delším průběhem. Tento příklad obsahuje odkazy `timer` do objektu [concurrency::call](../../parallel/concrt/reference/call-class.md) objektu. `call` Objekt zobrazí indikátor průběhu do konzoly nástroje v pravidelných intervalech. [Concurrency::timer::start](reference/timer-class.md#start) metoda spustí časovač v samostatných kontextu. `perform_lengthy_operation` Volání funkce [concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkce do hlavní kontextu pro simulaci časově náročná operace.

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

Tento příklad vytvoří následující ukázkový výstup:

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `report-progress.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc sestavy progress.cpp**

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)
