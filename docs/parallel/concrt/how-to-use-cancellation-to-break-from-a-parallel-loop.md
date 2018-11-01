---
title: 'Postupy: Přerušení paralelní smyčky pomocí zrušení'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 2a19c2874ce331be2d4f5840f61cabf7bca9abf6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612742"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Postupy: Přerušení paralelní smyčky pomocí zrušení

Tento příklad ukazuje způsob použití zrušení k implementaci základní paralelního vyhledávacího algoritmu.

## <a name="example"></a>Příklad

Následující příklad používá zrušení vyhledat prvek v poli. `parallel_find_any` Funkce používá [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus a [concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) funkce pro hledání pozice, který obsahuje zadanou hodnotu. Paralelní smyčka najde hodnotu, volá [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metoda zrušit budoucí práci.

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

[Concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus funguje souběžně. Proto se neprovádí operace v předem určeném pořadí. Pokud pole obsahuje více instancí hodnotu, výsledek může být jedna z jeho pozice.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `parallel-array-search.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc paralelní pole search.cpp**

## <a name="see-also"></a>Viz také

[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for – funkce](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source – třída](../../parallel/concrt/reference/cancellation-token-source-class.md)
