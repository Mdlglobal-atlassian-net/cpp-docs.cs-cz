---
title: 'Postupy: Odesílání zpráv v pravidelných intervalech'
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: c51a5cab6fcae5eb45b9d9b54c0dad8e8ec393b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142466"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Postupy: Odesílání zpráv v pravidelných intervalech

Tento příklad ukazuje, jak použít třídu concurrency::[Timer](../../parallel/concrt/reference/timer-class.md) k odeslání zprávy v pravidelných intervalech.

## <a name="example"></a>Příklad

Následující příklad používá objekt `timer` k hlášení průběhu během operace s zdlouhavou operací. Tento příklad propojuje objekt `timer` s objektem [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) . Objekt `call` v pravidelných intervalech tiskne indikátor průběhu. Metoda [Concurrency:: Timer:: Start](reference/timer-class.md#start) spustí časovač samostatného kontextu. Funkce `perform_lengthy_operation` volá funkci [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) v hlavním kontextu pro simulaci časově náročné operace.

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

Tento příklad vytvoří následující vzorový výstup:

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `report-progress.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Report-Progress. cpp**

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)
