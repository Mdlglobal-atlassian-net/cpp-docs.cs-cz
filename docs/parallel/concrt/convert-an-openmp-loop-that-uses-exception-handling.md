---
title: 'Postupy: Převedení smyčky OpenMP využívající zpracování výjimek na využití modulu Concurrency Runtime'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: 380a96eedb8a70965197c4a5ce0c5199bc268db5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141817"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>Postupy: Převedení smyčky OpenMP využívající zpracování výjimek na využití modulu Concurrency Runtime

Tento příklad ukazuje, jak převést [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)metodu OpenMP[pro](../../parallel/openmp/reference/for-openmp.md) smyčku, která provádí zpracování výjimek pro použití mechanismu Concurrency Runtimeho zpracování výjimek.

V příkazu OpenMP musí být výjimka, která je vyvolána v paralelní oblasti, zachycena a zpracována ve stejné oblasti stejným vláknem. Výjimka, která řídí, že je paralelní oblast zachycena neošetřenou obslužnou rutinou výjimky, která ve výchozím nastavení ukončí proces.

V Concurrency Runtime při vyvolání výjimky v těle pracovní funkce, kterou předáte do skupiny úloh, jako je například [Concurrency:: task_group](reference/task-group-class.md) nebo [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) Object nebo do paralelního algoritmu, jako je [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for), modul runtime ukládá tuto výjimku a zařazuje do kontextu, který čeká na dokončení skupiny úloh nebo algoritmu. Pro skupiny úloh je čekací kontext kontext, který volá [Concurrency:: task_group:: wait](reference/task-group-class.md#wait), [concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait), [Concurrency:: task_group:: run_and_wait](reference/task-group-class.md#run_and_wait)nebo [Concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait). Pro paralelní algoritmus je čekací kontext kontext, který tento algoritmus volal. Modul runtime také zastaví všechny aktivní úlohy, které jsou ve skupině úloh, včetně těch v podřízených skupinách úloh, a zahodí všechny úlohy, které ještě nebyly spuštěny.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak zpracovat výjimky v `parallel` oblasti OpenMP a volání `parallel_for`. Funkce `do_work` provádí požadavek na přidělení paměti, který není úspěšný, a proto vyvolá výjimku typu [std:: bad_alloc](../../standard-library/bad-alloc-class.md). Ve verzi, která používá OpenMP, vlákno, které vyvolá výjimku, musí také zachytit. Jinými slovy, Každá iterace paralelní smyčky OpenMP musí zpracovat výjimku. Ve verzi, která používá Concurrency Runtime, hlavní vlákno zachytí výjimku, která je vyvolána jiným vláknem.

[!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-exception-handling_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Using OpenMP...
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
Using the Concurrency Runtime...
An error of type 'class std::bad_alloc' occurred.
```

Ve verzi tohoto příkladu, který používá OpenMP, dojde k výjimce v a je zpracována každou iterací smyčky. Ve verzi, která používá Concurrency Runtime, modul runtime uloží výjimku, zastaví všechny aktivní úlohy, zahodí všechny úlohy, které ještě nebyly spuštěny, a zazařazuje výjimku do kontextu, který volá `parallel_for`.

Pokud požadujete, aby byla verze, která používá OpenMP, ukončena po výskytu výjimky, můžete použít logický příznak k signalizaci jiným iteracím smyčky, ke kterým došlo k chybě. Jak je uvedeno v příkladu v tématu [Postupy: převod smyčky OpenMP, která používá zrušení pro použití Concurrency Runtime](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md), by následné iterace v případě, že je nastavený příznak, nedělají nic. Naopak, pokud požadujete, aby smyčka, která používá Concurrency Runtime, pokračovala i poté, co dojde k výjimce, zpracujte výjimku v samotném těle paralelní smyčky.

Jiné součásti Concurrency Runtime, například asynchronní agenti a jednoduché úlohy, nepřenosují výjimky. Místo toho jsou neošetřené výjimky zachyceny obslužnou rutinou neošetřené výjimky, která proces ve výchozím nastavení ukončí. Další informace o zpracování výjimek naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Další informace o `parallel_for` a dalších paralelních algoritmech naleznete v tématu [Parallel](../../parallel/concrt/parallel-algorithms.md)Algorithms.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `concrt-omp-exceptions.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc/OpenMP ConcRT-OMP-Exceptions. cpp**

## <a name="see-also"></a>Viz také

[Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)
