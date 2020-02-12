---
title: 'Postupy: Použití objektu combinable ke slučování množin'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
ms.openlocfilehash: 7ccbb3e8bad5c4d3b6f4177afbfdba3e200681a5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142118"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>Postupy: Použití objektu combinable ke slučování množin

V tomto tématu se dozvíte, jak použít třídu [Concurrency::](../../parallel/concrt/reference/combinable-class.md) kombinovat k výpočtu sady číselných čísel.

## <a name="example"></a>Příklad

Následující příklad vypočítá sadu primárních čísel dvakrát. Každý výpočet ukládá výsledek do objektu [std:: bitset](../../standard-library/bitset-class.md) . V příkladu je nejprve vypočítána množina sériově a pak je tato sada souběžně vypočítána. Tento příklad také vytiskne do konzoly čas potřebný k provedení výpočtů.

Tento příklad používá algoritmus [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) a objekt `combinable` pro generování místních sad vláken. Potom používá metodu [Concurrency:: kombinovatelné:: combine_each](reference/combinable-class.md#combine_each) ke kombinování sad místních vláken do konečné sady.

[!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]

Následující vzorový výstup je určen pro počítač se čtyřmi procesory.

```Output
serial time: 312 ms

parallel time: 78 ms
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `parallel-combine-primes.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Parallel-Combine-PRIMES. cpp**

## <a name="see-also"></a>Viz také

[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable – třída](../../parallel/concrt/reference/combinable-class.md)<br/>
[kombinace:: combine_each – metoda](reference/combinable-class.md#combine_each)
