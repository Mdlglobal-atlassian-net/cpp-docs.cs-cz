---
title: 'Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
ms.openlocfilehash: 199b663331e3322601100206f222e80bbb7c8db0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142268"
---
# <a name="how-to-use-parallel_invoke-to-execute-parallel-operations"></a>Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací

Tento příklad ukazuje, jak použít algoritmus [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) ke zlepšení výkonu programu, který provádí více operací na sdíleném zdroji dat. Vzhledem k tomu, že žádné operace nemění zdroj, dají se provádět paralelně způsobem.

## <a name="example"></a>Příklad

Vezměte v úvahu následující příklad kódu, který vytvoří proměnnou typu `MyDataType`, zavolá funkci pro inicializaci této proměnné a poté provede více zdlouhavých operací s těmito daty.

[!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]

Pokud funkce `lengthy_operation1`, `lengthy_operation2`a `lengthy_operation3` nemění `MyDataType` proměnnou, mohou být tyto funkce spouštěny paralelně bez dalších úprav.

## <a name="example"></a>Příklad

Následující příklad upravuje předchozí příklad pro paralelní spuštění. Algoritmus `parallel_invoke` spouští jednotlivé úlohy paralelně a po dokončení všech úkolů vrátí.

[!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]

## <a name="example"></a>Příklad

Následující příklad stáhne *Iliad* podle Homer z Gutenberg.org a provede více operací na tomto souboru. Příklad nejprve provede tyto operace v sériovém tvaru a pak provede stejné operace paralelně.

[!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]

Tento příklad vytvoří následující vzorový výstup.

```Output
Downloading 'The Iliad'...

Running serial version... took 953 ms.
Running parallel version... took 656 ms.

The most common words that have five or more letters are:
    their (953)
    shall (444)
    which (431)
    great (398)
    Hector (349)
    Achilles (309)
    through (301)
    these (268)
    chief (259)
The longest sequence of words that have the same first letter is:
    through the tempest to the tented
The following palindromes appear in the text:
    spots stops
    speed deeps
    keels sleek
```

V tomto příkladu se používá algoritmus `parallel_invoke` pro volání více funkcí, které fungují ve stejném zdroji dat. Algoritmus `parallel_invoke` můžete použít k volání libovolné sady funkcí paralelně, nikoli jenom těch, které fungují se stejnými daty.

Vzhledem k tomu, že algoritmus `parallel_invoke` volá každou pracovní funkci paralelně, její výkon je svázán funkcí, která trvá nejdelší čas dokončení (to znamená, pokud modul runtime zpracuje jednotlivé funkce na samostatném procesoru). Pokud tento příklad provede více úkolů paralelně než počet dostupných procesorů, může na každém procesoru běžet více úloh. V takovém případě je výkon svázán skupinou úloh, které zabírají nejdelší čas na dokončení.

Vzhledem k tomu, že tento příklad provádí tři úkoly paralelně, neměli byste očekávat výkon pro škálování na počítačích, které mají více než tři procesory. Chcete-li zvýšit výkon, můžete narušit nejdelší běžící úlohy na menší úlohy a spouštět tyto úlohy paralelně.

Pokud nepožadujete podporu pro zrušení, můžete použít `parallel_invoke` algoritmus namísto tříd [Concurrency:: task_group](reference/task-group-class.md) a [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) . Příklad, který porovnává použití `parallel_invoke`ho algoritmu oproti skupinám úloh, naleznete v tématu [How to: Use parallel_invoke to Write The Parallel Sort](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md).

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li zkompilovat kód, zkopírujte jej a vložte jej do projektu aplikace Visual Studio nebo jej vložte do souboru s názvem `parallel-word-mining.cpp` a poté spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc/MD/DUNICODE/D_AFXDLL Parallel-Word-mining. cpp**

## <a name="see-also"></a>Viz také

[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_invoke funkce](reference/concurrency-namespace-functions.md#parallel_invoke)
