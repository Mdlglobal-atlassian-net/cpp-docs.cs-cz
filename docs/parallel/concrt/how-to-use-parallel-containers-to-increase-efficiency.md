---
title: 'Postupy: Použití paralelních kontejnerů ke zvýšení účinnosti'
ms.date: 11/04/2016
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
ms.openlocfilehash: 2479915b167ee3dbc2ce43d9c2733efc74818bbe
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300632"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>Postupy: Použití paralelních kontejnerů ke zvýšení účinnosti

Toto téma ukazuje, jak efektivně ukládat a přistupovat k datům v paralelní použití paralelních kontejnerů.

Ukázkový kód vypočítá sadu prime a čísla Carmichael paralelně. Pak pro každé číslo Carmichael kód vypočítá prvotní faktory tohoto čísla.

## <a name="example"></a>Příklad

Následující příklad ukazuje `is_prime` funkce, která určuje, zda je vstupní hodnota Prvočíslo, a `is_carmichael` funkce, která určuje, zda je vstupní hodnota Carmichael číslo.

[!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]

## <a name="example"></a>Příklad

V následujícím příkladu `is_prime` a `is_carmichael` funkcí pro výpočet sady prime a Carmichael čísel. V příkladu se používá [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) a [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmy pro výpočet každé sadě paralelně. Další informace o paralelních algoritmech naleznete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

Tento příklad používá [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) objekt pro uložení sadu Carmichael čísla, protože později použije tento objekt jako fronty pracovních položek. Použije [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) objekt pro uložení sadu prvočísel, protože se později iterovat přes nastavení najít prvotní faktory.

[!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje `prime_factors_of` funkci, která používá zkušební dělení najít všechny hlavní faktory předané hodnoty.

Tato funkce využívá [: concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus pro iteraci prostřednictvím kolekce prvočísel. `concurrent_vector` Objektu umožňuje paralelní smyčky současně přidat hlavní faktory k výsledku.

[!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]

## <a name="example"></a>Příklad

V tomto příkladu zpracovává každý prvek ve frontě Carmichael čísla voláním `prime_factors_of` funkcí pro výpočet jeho hlavní faktory. Skupiny úloh používá k provedení této práci paralelně. Další informace o skupinách úkolů najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Tento příklad vytiskne prvotní faktory pro každé číslo Carmichael, pokud toto číslo má více než čtyři hlavní faktory.

[!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]

## <a name="example"></a>Příklad

Následující kód ukazuje úplný příklad, který používá paralelní kontejnery pro výpočet prvotní faktory Carmichael čísla.

[!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]

Tento příklad vytvoří následující ukázkový výstup.

```Output
Prime factors of 9890881 are: 7 11 13 41 241.
Prime factors of 825265 are: 5 7 17 19 73.
Prime factors of 1050985 are: 5 13 19 23 37.
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `carmichael-primes.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /EHsc carmichael-primes.cpp**

## <a name="see-also"></a>Viz také:

[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[concurrent_vector – třída](../../parallel/concrt/reference/concurrent-vector-class.md)<br/>
[concurrent_queue – třída](../../parallel/concrt/reference/concurrent-queue-class.md)<br/>
[parallel_invoke – funkce](reference/concurrency-namespace-functions.md#parallel_invoke)<br/>
[parallel_for – funkce](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[task_group – třída](reference/task-group-class.md)
