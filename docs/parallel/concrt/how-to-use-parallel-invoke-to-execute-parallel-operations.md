---
title: 'Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
ms.openlocfilehash: d618b5f202c6aaf454a60f4f37211d9000600562
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345653"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací

Tento příklad ukazuje způsob použití [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus pro zlepšení výkonu programu, který provádí více operací na sdílený zdroj dat. Vzhledem k tomu, že žádné operace upravit zdroj, mohou být provedeny souběžně v přímočarým způsobem.

## <a name="example"></a>Příklad

Zvažte následující příklad kódu, která vytvoří proměnnou typu `MyDataType`, volá funkci pro inicializaci proměnné a pak provádí více operací zdlouhavé na těchto datech.

[!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]

Pokud `lengthy_operation1`, `lengthy_operation2`, a `lengthy_operation3` functions Neupravovat `MyDataType` proměnné, tyto funkce mohou být provedeny souběžně bez dalších úprav.

## <a name="example"></a>Příklad

Následující příklad upravuje předchozí příklad při paralelním spuštění. `parallel_invoke` Algoritmus každý úkol spustí paralelně a vrátí po dokončení všech úloh.

[!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]

## <a name="example"></a>Příklad

Následující příklad stáhne *The Iliad* podle Homer z gutenberg.org a provádí více operací u tohoto souboru. V příkladu nejdřív sériově provádí tyto operace a pak provede stejné operace paralelně.

[!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]

Tento příklad vytvoří následující ukázkový výstup.

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

V tomto příkladu `parallel_invoke` algoritmus pro volání více funkcí na stejný zdroj dat, které se chovají. Můžete použít `parallel_invoke` algoritmus volat všechny sady funkcí paralelně, nejen ty, které fungují na stejných datech.

Vzhledem k tomu, `parallel_invoke` algoritmus volá funkci každou pracovní paralelně, jeho výkon je ohraničen funkci, která trvá nejdéle (to znamená, pokud modul runtime zpracovává každá funkce v samostatných procesoru). Pokud v tomto příkladu provádí více úloh paralelně než počet dostupných procesorů, můžete spustit více úkolů na každý procesor. V takovém případě výkonu ohraničené skupina úloh, který zabere nejvíce času na dokončení.

Protože v tomto příkladu provede tři úkoly paralelně, by neměli očekávat výkon a škálování na počítačích, které mají více než tři procesory. Ke zlepšení výkonu další, můžete rozdělit na menší úlohy nejdelší spuštěné úlohy a tyto úlohy běží paralelně.

Můžete použít `parallel_invoke` algoritmus místo [concurrency::task_group](reference/task-group-class.md) a [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) třídy Pokud nepožadujete podporu pro zrušení. Příklad, který porovnává využití `parallel_invoke` algoritmus a skupiny úloh, naleznete v tématu [jak: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md).

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li kód zkompilovat, ho zkopírujte a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `parallel-word-mining.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /EHsc /MD /DUNICODE /D_AFXDLL parallel-word-mining.cpp**

## <a name="see-also"></a>Viz také:

[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_invoke – funkce](reference/concurrency-namespace-functions.md#parallel_invoke)
