---
title: 'Postupy: Převedení OpenMP paralelní smyčky na využití modulu Concurrency Runtime'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: bc408465f34f0558e9f426ae35b83d4610898414
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413889"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>Postupy: Převedení OpenMP paralelní smyčky na využití modulu Concurrency Runtime

Tento příklad ukazuje, jak převést základní smyčku, která se používá OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) a [pro](../../parallel/openmp/reference/for-openmp.md) direktivy na využití modulu Concurrency Runtime [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus.

## <a name="example"></a>Příklad

Tento příklad používá OpenMP a modulu Runtime souběžnosti má vypočítat počet prvočísel v poli náhodné hodnoty.

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

`parallel_for` Algoritmus a OpenMP 3.0 povolit pro typ indexu celočíselný typ se znaménkem nebo bez znaménka celočíselného typu. `parallel_for` Algoritmus také zajišťuje, že zadaný rozsah není přetečení typ se znaménkem. OpenMP – verze 2.0 nebo 2.5 povolit podepsané celočíselný index pouze pro typy. OpenMP také neověřuje rozsah indexů.

Verze tohoto příkladu, který používá modulu Runtime souběžnosti, zabírá [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) objektu místo [atomické](../../parallel/openmp/reference/atomic.md) – direktiva se zvýší hodnota čítače bez nutnosti synchronizace.

Další informace o `parallel_for` a jiné paralelní algoritmy, naleznete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md). Další informace o `combinable` najdete v tématu [paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="example"></a>Příklad

Tento příklad upravuje předchozí tak, aby fungoval na [std::array](../../standard-library/array-class-stl.md) místo objektu na nativní pole. Protože verze OpenMP 2.0 nebo 2.5 povolit pro typy celočíselný index pouze v podepsané `parallel_for` konstrukce, iterátory nelze použít pro přístup k prvkům kontejneru standardní knihovny C++ paralelně. Poskytuje knihovna paralelních vzorů (PPL) [: concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus, který paralelně, iterativní kontejneru jako třeba pomocí provádí úkoly, C++ standardní knihovny. Používá stejnou logiku dělení, který `parallel_for` algoritmus používá. `parallel_for_each` Algoritmus vypadá podobně jako C++ standardní knihovny [std::for_each](../../standard-library/algorithm-functions.md#for_each) algoritmus, s výjimkou, že `parallel_for_each` algoritmus spustí úlohy současně.

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `concrt-omp-count-primes.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /EHsc /openmp concrt-omp-count-primes.cpp**

## <a name="see-also"></a>Viz také:

[Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)
