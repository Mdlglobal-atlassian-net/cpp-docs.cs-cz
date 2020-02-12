---
title: 'Postupy: Programování smyčky parallel_for_each'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
ms.openlocfilehash: 10c281b7db92e2706b20a1c7377fcdb9d924152d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141878"
---
# <a name="how-to-write-a-parallel_for_each-loop"></a>Postupy: Programování smyčky parallel_for_each

Tento příklad ukazuje, jak použít algoritmus [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) k výpočtu počtu primárních čísel v objektu [std:: Array](../../standard-library/array-class-stl.md) paralelně.

## <a name="example"></a>Příklad

Následující příklad vypočítá počet primárních čísel v poli dvakrát. První příklad používá algoritmus [std:: for_each](../../standard-library/algorithm-functions.md#for_each) pro výpočet sériového počtu. Příklad poté používá algoritmus `parallel_for_each` k provedení stejné úlohy paralelně. Tento příklad také vytiskne do konzoly čas potřebný k provedení výpočtů.

[!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]

Následující vzorový výstup je určen pro počítač se čtyřmi procesory.

```Output
serial version:
found 17984 prime numbers
took 6115 ms

parallel version:
found 17984 prime numbers
took 1653 ms
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li zkompilovat kód, zkopírujte jej a vložte jej do projektu aplikace Visual Studio nebo jej vložte do souboru s názvem `parallel-count-primes.cpp` a poté spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Parallel-Count-PRIMES. cpp**

## <a name="robust-programming"></a>Robustní programování

Výraz lambda, který tento příklad projde k algoritmu `parallel_for_each`, používá funkci `InterlockedIncrement` k umožnění paralelních iterací smyčky pro zvýšení čítače současně. Pokud používáte funkce, jako je `InterlockedIncrement` k synchronizaci přístupu ke sdíleným prostředkům, můžete ve svém kódu prezentovat kritická místa výkonu. K vyloučení současného přístupu ke sdíleným prostředkům můžete použít synchronizační mechanismus bez zámků, například třídu [Concurrency::](../../parallel/concrt/reference/combinable-class.md) kombinovat. Příklad, který používá třídu `combinable` tímto způsobem, naleznete v tématu [How to: use kombinovat pro zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md).

## <a name="see-also"></a>Viz také

[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for_each funkce](reference/concurrency-namespace-functions.md#parallel_for_each)
