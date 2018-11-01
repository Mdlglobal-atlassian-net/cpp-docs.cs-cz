---
title: 'Postupy: Programování smyčky parallel_for'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: 5caba385304e97bf2e1008a44724c792d56124f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592706"
---
# <a name="how-to-write-a-parallelfor-loop"></a>Postupy: Programování smyčky parallel_for

Tento příklad ukazuje, jak používat [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) vypočítat součin dvou matice.

## <a name="example"></a>Příklad

Následující příklad ukazuje `matrix_multiply` funkce, která vypočítá součin dvou čtvercové matice.

[!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje `parallel_matrix_multiply` funkci, která používá `parallel_for` algoritmus paralelní provádění vnější smyčky.

[!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]

V tomto příkladu parallelizes vnější smyčky pouze, protože provádí dostatek práce, abyste využili výhod režie pro paralelní zpracování. Pokud jste paralelizovat vnitřní smyčky, neobdržíte žádné zvýšení výkonu vzhledem k tomu, že malé množství práce, které provádí vnitřní smyčku neodstraní režie pro paralelní zpracování. Paralelní provádění vnější smyčky pouze tedy nejlepší způsob, jak zvýšit výhody souběžnosti ve většině systémů.

## <a name="example"></a>Příklad

Následující kompletní příklad porovná výkon `matrix_multiply` fungovat oproti `parallel_matrix_multiply` funkce.

[!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]

Následující ukázkový výstup je pro počítač, který má čtyři procesory.

```Output
serial: 3853
parallel: 1311
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li kód zkompilovat, ho zkopírujte a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `parallel-matrix-multiply.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc paralelní matice multiply.cpp**

## <a name="see-also"></a>Viz také

[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for – funkce](reference/concurrency-namespace-functions.md#parallel_for)

