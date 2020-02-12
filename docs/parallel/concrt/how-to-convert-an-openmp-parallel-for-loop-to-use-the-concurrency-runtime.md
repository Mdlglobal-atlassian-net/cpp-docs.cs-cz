---
title: 'Postupy: Převedení paralelní smyčky for v OpenMP na využití modulu Concurrency Runtime'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: 2d96ba23582368fe72e61003823826a6f3ab807a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141754"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>Postupy: Převedení paralelní smyčky for v OpenMP na využití modulu Concurrency Runtime

Tento příklad ukazuje, jak převést základní smyčku, která používá direktivy OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) a [for pro](../../parallel/openmp/reference/for-openmp.md) použití Concurrency Runtime algoritmus [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) .

## <a name="example---prime-count"></a>Příklad – počet apostrofů

V tomto příkladu se používá direktiva OpenMP i Concurrency Runtime k výpočtu počtu primárních čísel v poli náhodných hodnot.

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

`parallel_for` algoritmus a OpenMP 3,0 umožňují, aby typ indexu byl celočíselný typ se znaménkem nebo celočíselný typ bez znaménka. Algoritmus `parallel_for` také zajišťuje, aby zadaný rozsah nepřetekl na podepsaný typ. OpenMP verze 2,0 a 2,5 umožňují pouze podepsané typy integrálních indexů. OpenMP také neověřuje rozsah indexu.

Verze tohoto příkladu, který používá Concurrency Runtime, používá také objekt [Concurrency::](../../parallel/concrt/reference/combinable-class.md) kombinovatelné namísto [atomické](../../parallel/openmp/reference/atomic.md) direktivy k zvýšení hodnoty čítače bez nutnosti synchronizace.

Další informace o `parallel_for` a dalších paralelních algoritmech naleznete v tématu [Parallel](../../parallel/concrt/parallel-algorithms.md)Algorithms. Další informace o třídě `combinable` naleznete v tématu [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="example---use-stdarray"></a>Příklad – použijte std:: Array.

Tento příklad upraví předchozí, aby fungoval na objektu [std:: Array](../../standard-library/array-class-stl.md) namísto v nativním poli. Vzhledem k tomu, že verze OpenMP 2,0 a 2,5 povoluje pouze podepsané typy integrálních indexů ve `parallel_for` konstrukce, nelze použít iterátory pro přístup k C++ prvkům kontejneru standardní knihovny paralelně. Knihovna PPL (Parallel Patterns Library) poskytuje algoritmus [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) , který provádí paralelní úlohy na iterativním kontejneru, jako jsou ty, které jsou poskytovány C++ standardní knihovnou. Používá stejnou logiku dělení, kterou používá algoritmus `parallel_for`. Algoritmus `parallel_for_each` se podobá C++ standardní knihovně [std:: for_each](../../standard-library/algorithm-functions.md#for_each) , s tím rozdílem, že `parallel_for_each` algoritmus spouští úlohy souběžně.

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `concrt-omp-count-primes.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc/OpenMP ConcRT-OMP-Count-PRIMES. cpp**

## <a name="see-also"></a>Viz také

[Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)
