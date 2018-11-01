---
title: 'Postupy: Programování smyčky parallel_for_each'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
ms.openlocfilehash: e3b19ec180f9f4e75a2f280a0ecd159e5b932565
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610506"
---
# <a name="how-to-write-a-parallelforeach-loop"></a>Postupy: Programování smyčky parallel_for_each

Tento příklad ukazuje způsob použití [: concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus, který se Vypočítat hodnotu count prvočísel v [std::array](../../standard-library/array-class-stl.md) objekt paralelně.

## <a name="example"></a>Příklad

Následující příklad vypočítá počet prvočísel v poli dvakrát. V prvním příkladu [std::for_each](../../standard-library/algorithm-functions.md#for_each) algoritmus má vypočítat počet sériově. Příklad poté použije `parallel_for_each` algoritmus provést stejnou úlohu současně. V příkladu také tiskne na konzolu čas, který je potřeba provést i výpočty.

[!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]

Následující ukázkový výstup je pro počítač, který má čtyři procesory.

```Output
serial version:
found 17984 prime numbers
took 6115 ms

parallel version:
found 17984 prime numbers
took 1653 ms
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li kód zkompilovat, ho zkopírujte a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `parallel-count-primes.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc paralelní počet primes.cpp**

## <a name="robust-programming"></a>Robustní programování

Výraz lambda, který příklad předá `parallel_for_each` algoritmus používá `InterlockedIncrement` funkce Povolit paralelní iterace smyčky se zvýší čítač současně. Pokud například používáte funkce `InterlockedIncrement` k synchronizaci přístupu ke sdíleným prostředkům, můžete představovat problémových míst výkonu ve vašem kódu. Mechanismus uvolnění zámku synchronizace můžete použít například, [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídy, chcete-li odstranit mělo současně přístup ke sdíleným prostředkům. Příklad, který se používá `combinable` tímto způsobem najdete v tématu [postupy: použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md).

## <a name="see-also"></a>Viz také

[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for_each Function](reference/concurrency-namespace-functions.md#parallel_for_each)

