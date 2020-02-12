---
title: 'Postupy: Použití paralelních kontejnerů ke zvýšení účinnosti'
ms.date: 11/04/2016
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
ms.openlocfilehash: cd120d1fbe0f73ed0974efda5a1aa643a1afde9d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143013"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>Postupy: Použití paralelních kontejnerů ke zvýšení účinnosti

V tomto tématu se dozvíte, jak pomocí paralelních kontejnerů efektivně ukládat data a přistupovat k nim.

Vzorový kód vypočítá sadu primárních a Carmichael čísel paralelně. Pro každé číslo Carmichael kód vypočítá základní faktory tohoto čísla.

## <a name="example"></a>Příklad

Následující příklad ukazuje funkci `is_prime`, která určuje, zda je vstupní hodnota hlavní číslo a funkce `is_carmichael`, která určuje, zda je vstupní hodnotou Carmichael číslo.

[!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]

## <a name="example"></a>Příklad

V následujícím příkladu jsou použity funkce `is_prime` a `is_carmichael` k výpočtu sady čísel Carmichael a. V příkladu se používá [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) a [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus k výpočtu každé sady paralelně. Další informace o paralelních algoritmech najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

V tomto příkladu se používá objekt [Concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) k uložení sady Carmichael čísel, protože později použije tento objekt jako pracovní frontu. Používá objekt [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) k uložení množiny primárních čísel, protože bude později iterovat pomocí této sady k nalezení primárních faktorů.

[!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje funkci `prime_factors_of`, která používá rozdělení zkušební verze k vyhledání všech primárních faktorů dané hodnoty.

Tato funkce používá algoritmus [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) k iteraci v kolekci apostrofových čísel. Objekt `concurrent_vector` umožňuje paralelní smyčce souběžně přidávat do výsledku základní faktory.

[!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]

## <a name="example"></a>Příklad

Tento příklad zpracovává každý prvek ve frontě čísel Carmichael voláním funkce `prime_factors_of` pro výpočet svých primárních faktorů. K paralelnímu provedení této práce používá skupinu úloh. Další informace o skupinách úloh najdete v tématu [Task paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Tento příklad vytiskne hlavní faktory pro každé číslo Carmichael, pokud má toto číslo více než čtyři základní faktory.

[!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]

## <a name="example"></a>Příklad

Následující kód ukazuje kompletní příklad, který používá paralelní kontejnery k výpočtu primárních faktorů Carmichael čísel.

[!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]

Tento příklad vytvoří následující vzorový výstup.

```Output
Prime factors of 9890881 are: 7 11 13 41 241.
Prime factors of 825265 are: 5 7 17 19 73.
Prime factors of 1050985 are: 5 13 19 23 37.
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `carmichael-primes.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Carmichael-PRIMES. cpp**

## <a name="see-also"></a>Viz také

[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[concurrent_vector – třída](../../parallel/concrt/reference/concurrent-vector-class.md)<br/>
[concurrent_queue – třída](../../parallel/concrt/reference/concurrent-queue-class.md)<br/>
[parallel_invoke funkce](reference/concurrency-namespace-functions.md#parallel_invoke)<br/>
[parallel_for funkce](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[task_group – třída](reference/task-group-class.md)
