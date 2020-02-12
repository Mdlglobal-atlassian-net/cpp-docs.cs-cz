---
title: 'Postupy: Převedení smyčky OpenMP využívající redukční proměnnou na využití modulu Concurrency Runtime'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: ee0a600f4234c3ebf4681ad92b5e3623be5665c3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141266"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>Postupy: Převedení smyčky OpenMP využívající redukční proměnnou na využití modulu Concurrency Runtime

Tento příklad ukazuje, jak převést [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)smyčku OpenMP[for](../../parallel/openmp/reference/for-openmp.md) , která používá klauzuli [Reduction](../../parallel/openmp/reference/reduction.md) pro použití Concurrency Runtime.

Klauzule OpenMP `reduction` umožňuje zadat jednu nebo více privátních proměnných vlákna, které podléhají operaci snížení na konci paralelní oblasti. OpenMP předdefinuje sadu operátorů redukce. Každá proměnná omezení musí být skalární (například `int`, `long`a `float`). OpenMP také definuje několik omezení způsobu použití proměnných snížení v paralelní oblasti.

Knihovna PPL (Parallel Patterns Library) poskytuje třídu [Concurrency::](../../parallel/concrt/reference/combinable-class.md) Merged, která poskytuje opětovné použití, místní úložiště vlákna, které umožňuje provádět jemně odstupňované výpočty a pak tyto výpočty sloučit do konečného výsledku. Třída `combinable` je šablona, která funguje na skalárních i složitých typech. Chcete-li použít třídu `combinable`, proveďte dílčí výpočty v těle paralelní konstrukce a pak zavolejte metodu [Concurrency:: kombined:: kombinovat](reference/combinable-class.md#combine) nebo [concurrency:: combine_each](reference/combinable-class.md#combine_each) pro vytvoření konečného výsledku. Metody `combine` a `combine_each` každou z nich přebírají *funkci kombinování* , která určuje, jak kombinovat jednotlivé páry prvků. Proto třída `combinable` není omezena na pevně danou sadu operátorů redukce.

## <a name="example"></a>Příklad

V tomto příkladu se k výpočtu součtu prvních 35 Fibonacci čísel používá direktiva OpenMP i Concurrency Runtime.

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

Další informace o třídě `combinable` naleznete v tématu [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `concrt-omp-fibonacci-reduction.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc/OpenMP ConcRT-OMP-Fibonacci-Reduction. cpp**

## <a name="see-also"></a>Viz také

[Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)
