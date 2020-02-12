---
title: 'Postupy: Přerušení paralelní smyčky pomocí zrušení'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 21907de6c5625f7774ae788cef0449ac49107e40
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142137"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Postupy: Přerušení paralelní smyčky pomocí zrušení

Tento příklad ukazuje, jak použít zrušení k implementaci základního paralelního vyhledávacího algoritmu.

## <a name="example"></a>Příklad

Následující příklad používá zrušení pro hledání prvku v poli. Funkce `parallel_find_any` používá algoritmus [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) a funkce [concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) k vyhledání pozice, která obsahuje danou hodnotu. Když paralelní smyčka najde hodnotu, zavolá metodu [Concurrency:: cancellation_token_source:: Cancel](reference/cancellation-token-source-class.md#cancel) pro zrušení budoucí práce.

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

Algoritmus [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) funguje současně. Proto neprovádí operace v předem určeném pořadí. Pokud pole obsahuje více instancí hodnoty, může být výsledkem kterákoli z jeho pozic.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `parallel-array-search.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Parallel-Array-Search. cpp**

## <a name="see-also"></a>Viz také

[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for funkce](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source – třída](../../parallel/concrt/reference/cancellation-token-source-class.md)
