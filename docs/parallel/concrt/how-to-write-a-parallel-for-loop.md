---
title: 'Postupy: Programování smyčky parallel_for'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: 5903114a12de46dc06929c83e9995b39d0136810
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141864"
---
# <a name="how-to-write-a-parallel_for-loop"></a>Postupy: Programování smyčky parallel_for

Tento příklad ukazuje, jak použít [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) k výpočtu součinu dvou matic.

## <a name="example"></a>Příklad

Následující příklad ukazuje funkci `matrix_multiply`, která vypočítá součin dvou čtvercových matic.

[!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje funkci `parallel_matrix_multiply`, která používá algoritmus `parallel_for` k paralelnímu provedení vnější smyčky.

[!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]

V tomto příkladu se parallelizes vnější smyčka pouze proto, že provádí dostatečnou práci, aby mohla těžit z režie pro paralelní zpracování. Pokud paralelizovat vnitřní smyčku, nebudete dostávat žádné zvýšení výkonu, protože malé množství práce, které vnitřní smyčka provede, neprovádí překonání režie na paralelní zpracování. Proto virtuálního pouze vnější smyčka je nejlepším způsobem, jak maximalizovat výhody souběžnosti ve většině systémů.

## <a name="example"></a>Příklad

Následující příklad kompletní porovnává výkon funkce `matrix_multiply` oproti funkci `parallel_matrix_multiply`.

[!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]

Následující vzorový výstup je určen pro počítač se čtyřmi procesory.

```Output
serial: 3853
parallel: 1311
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li zkompilovat kód, zkopírujte jej a vložte jej do projektu aplikace Visual Studio nebo jej vložte do souboru s názvem `parallel-matrix-multiply.cpp` a poté spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Parallel-Matrix-Multiply. cpp**

## <a name="see-also"></a>Viz také

[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for funkce](reference/concurrency-namespace-functions.md#parallel_for)
