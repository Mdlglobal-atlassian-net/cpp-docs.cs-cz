---
title: 'Postupy: Převedení smyčky OpenMP využívající redukční proměnnou na využití modulu Concurrency Runtime'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: d75e115bdb1d13c9e8f45ed67d0f3993eac1b387
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413954"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>Postupy: Převedení smyčky OpenMP využívající redukční proměnnou na využití modulu Concurrency Runtime

Tento příklad ukazuje, jak převést OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pro](../../parallel/openmp/reference/for-openmp.md) smyčku, která se používá [snížení](../../parallel/openmp/reference/reduction.md) klauzule na využití modulu Concurrency Runtime.

OpenMP `reduction` klauzule umožňuje určit jednu nebo více proměnných vlákna privátní, které se vztahují na operaci snížení na konci paralelní oblasti. OpenMP – predefines sadu operátorů snížení. Každý redukční proměnná musí být skalární hodnota (například `int`, `long`, a `float`). OpenMP také definuje několik omezení při použití redukční proměnné v paralelní oblasti.

Poskytuje knihovna paralelních vzorů (PPL) [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídu, která obsahuje opakovaně použitelné, místní úložiště, které umožňuje jemně výpočty a těchto výpočtů sloučit konečné výsledek. `combinable` Třídy je šablona, která funguje na skalární a komplexní typy. Použít `combinable` třídy, provádí dílčí výpočty v těle paralelní konstrukce a poté zavolejte [concurrency::combinable::combine](reference/combinable-class.md#combine) nebo [concurrency::combinable::combine_each](reference/combinable-class.md#combine_each) metodu za účelem vytvoření konečný výsledek. `combine` a `combine_each` trvat každá z metod *kombinovat funkce* , která určuje, jak kombinovat každý pár prvků. Proto `combinable` třídy se neomezuje na pevnou sadu operátorů snížení.

## <a name="example"></a>Příklad

Tento příklad používá pro výpočet součtu nejprve 35 čísla Fibonacciho OpenMP a modulu Runtime souběžnosti.

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

Další informace o `combinable` najdete v tématu [paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `concrt-omp-fibonacci-reduction.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /EHsc /openmp concrt-omp-fibonacci-reduction.cpp**

## <a name="see-also"></a>Viz také:

[Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)
