---
title: 'Postupy: Převedení smyčky OpenMP využívající zpracování výjimek na využití modulu Concurrency Runtime'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: 118cf3e485fa78ae3eaa5efe34708924b89d6588
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285149"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>Postupy: Převedení smyčky OpenMP využívající zpracování výjimek na využití modulu Concurrency Runtime

Tento příklad ukazuje, jak převést OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pro](../../parallel/openmp/reference/for-openmp.md) smyčku, která provádí zpracování výjimek použít mechanismus zpracování výjimek Concurrency Runtime.

V OpenMP musí být výjimku, která je vyvolána v paralelní oblasti odchycena a zpracována stejným vlákna ve stejné oblasti. Obslužná rutina neošetřené výjimky, která ukončí proces ve výchozím nastavení je zachytil výjimku, aby řídící paralelní oblasti.

V modulu Runtime souběžnosti, při vyvolání výjimky v těle funkce práce, která předáte do skupiny úloh, jako například [concurrency::task_group](reference/task-group-class.md) nebo [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objektu, nebo paralelního algoritmu, jako [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), modul runtime ukládá tuto výjimku a zařadí do kontextu, který se čeká na skupinu úloh nebo algoritmus, který se dokončit. Pro skupiny úloh, je kontext čekání kontext, který volá [Concurrency::task_group:: wait](reference/task-group-class.md#wait), [Concurrency::structured_task_group:: wait](reference/structured-task-group-class.md#wait), [concurrency::task_group::run_and _wait](reference/task-group-class.md#run_and_wait), nebo [Concurrency::structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait). Pro paralelní algoritmus je čekání kontextu kontextu, který volá tento algoritmus. Modul runtime také zastaví všechny aktivní úkoly, které jsou ve skupině úloh, včetně těch v podřízených skupinách úloh, a zahodí všechny úkoly, které ještě nebyly spuštěny.

## <a name="example"></a>Příklad

Tento příklad ukazuje způsob zpracování výjimek v OpenMP `parallel` oblasti a při volání k `parallel_for`. `do_work` Funkce provádí požadavek na přidělení paměti, který selže a proto vyvolá výjimku typu [std::bad_alloc](../../standard-library/bad-alloc-class.md). Ve verzi, která používá OpenMP vlákna, které vyvolá výjimku musí také zachytit. Jednotlivých iteracích paralelní smyčky OpenMP – jinými slovy, musí umět zpracovat výjimku. Hlavní vlákno ve verzi, která používá modulu Runtime souběžnosti, zachytí výjimku, která je vyvolána jiným vláknem.

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

Ve verzi tohoto příkladu, který používá OpenMP výjimky probíhá a je zpracována každé iteraci smyčky. Ve verzi, která používá modulu Runtime souběžnosti, modul runtime ukládá výjimku, ukončí všechny aktivní úkoly, zahodí všechny úkoly, které dosud nebyly spuštěna a zařadí výjimka, která má kontext, který volá `parallel_for`.

Pokud požadujete, verzi, která používá OpenMP ukončí, když dojde k výjimce, můžete použít příznak logické hodnoty na signál pro dalších iterací smyčky, že došlo k chybě. Stejně jako v příkladu v tomto tématu [jak: Převedení smyčky OpenMP této používá zrušení na využití modulu Concurrency Runtime](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md), následné průchod cyklem by neprovedení, pokud je nastavený příznak. Naopak pokud požadujete, smyčky, která používá modul Concurrency Runtime bude pokračovat po vyvolá výjimku, zpracujte výjimku v těle paralelní smyčky, samotného.

Další součásti modulu Runtime souběžnosti, jako je například asynchronních agentů a jednoduché úlohy, není přenášet výjimky. Místo toho neošetřené výjimky jsou zachyceny obslužnou rutinu neošetřených výjimek, které ukončí proces ve výchozím nastavení. Další informace o zpracování výjimek naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Další informace o `parallel_for` a jiné paralelní algoritmy, naleznete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `concrt-omp-exceptions.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /EHsc /openmp concrt-omp-exceptions.cpp**

## <a name="see-also"></a>Viz také:

[Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)
