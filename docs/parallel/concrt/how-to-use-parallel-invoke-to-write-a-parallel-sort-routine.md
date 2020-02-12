---
title: 'Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění'
ms.date: 11/04/2016
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
ms.openlocfilehash: 6acac3f6bc82db6e6981f83715c7ee88cfd06fbd
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141935"
---
# <a name="how-to-use-parallel_invoke-to-write-a-parallel-sort-routine"></a>Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění

Tento dokument popisuje, jak použít algoritmus [parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke) ke zlepšení výkonu bitonického algoritmu řazení. Algoritmus řazení bitonického rekurzivně rozdělí vstupní sekvenci na menší seřazené oddíly. Algoritmus řazení bitonického lze spustit paralelně, protože každá operace oddílu je nezávislá na všech ostatních operacích.

I když je řazení bitonického příkladem *sítě řazení* , která seřadí všechny kombinace vstupních sekvencí, tento příklad seřadí sekvence, jejichž délka je mocninou dvou.

> [!NOTE]
> V tomto příkladu se používá rutina paralelního řazení pro ilustraci. Můžete také použít vestavěné algoritmy řazení, které poskytuje PPL: [Concurrency::p arallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::p arallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)a [Concurrency::p arallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Další informace najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

## <a name="top"></a>Řezů

Tento dokument popisuje následující úlohy:

- [Provádění bitonického řazení sériově](#serial)

- [Použití parallel_invoke k paralelnímu řazení bitonického](#parallel)

## <a name="serial"></a>Provádění bitonického řazení sériově

Následující příklad ukazuje sériovou verzi algoritmu řazení bitonického. Funkce `bitonic_sort` rozdělí sekvenci na dva oddíly, seřadí tyto oddíly v opačném směru a potom sloučí výsledky. Tato funkce volá dvakrát sebe samé pro řazení jednotlivých oddílů.

[!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]

[[Nahoře](#top)]

## <a name="parallel"></a>Použití parallel_invoke k paralelnímu řazení bitonického

Tato část popisuje, jak použít algoritmus `parallel_invoke` k paralelnímu provedení bitonického algoritmu řazení.

### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>Paralelní provádění algoritmu bitonického řazení

1. Přidejte direktivu `#include` pro hlavičkový soubor PPL. h.

[!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]

1. Přidejte direktivu `using` pro obor názvů `concurrency`.

[!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]

1. Vytvořte novou funkci nazvanou `parallel_bitonic_mege`, která používá algoritmus `parallel_invoke` ke sloučení sekvencí paralelně, pokud existuje dostatečná množství práce. V opačném případě zavolejte `bitonic_merge` ke sloučení sekvencí sériově.

[!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]

1. Proveďte proces, který se podobá v předchozím kroku, ale pro funkci `bitonic_sort`.

[!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]

1. Vytvořte přetíženou verzi funkce `parallel_bitonic_sort`, která seřadí pole ve vzestupném pořadí.

[!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]

Algoritmus `parallel_invoke` snižuje režijní náklady tím, že provádí poslední posloupnost úloh v volajícím kontextu. Například ve funkci `parallel_bitonic_sort` se první úloha spouští v samostatném kontextu a druhá úloha je spuštěna v kontextu volání.

[!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]

Následující kompletní příklad provádí sériové i paralelní verze algoritmu řazení bitonického. Tento příklad také vytiskne do konzoly čas potřebný k provedení jednotlivých výpočtů.

[!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]

Následující vzorový výstup je určen pro počítač se čtyřmi procesory.

```Output
serial time: 4353
parallel time: 1248
```

[[Nahoře](#top)]

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li zkompilovat kód, zkopírujte jej a vložte jej do projektu aplikace Visual Studio nebo jej vložte do souboru s názvem `parallel-bitonic-sort.cpp` a poté spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Parallel-bitonic-Sort. cpp**

## <a name="robust-programming"></a>Robustní programování

Tento příklad používá `parallel_invoke` algoritmus namísto třídy [Concurrency:: task_group](reference/task-group-class.md) , protože životnost každé skupiny úloh nepřekračuje funkci. Doporučujeme použít `parallel_invoke`, pokud je to možné, protože má méně režie na provedení než objekty `task group`, a proto umožňuje psát kód, který je lepší provádět.

Paralelní verze některých algoritmů fungují lépe pouze v případě, že je k dispozici dostatečná práce. Například funkce `parallel_bitonic_merge` volá sériové verze `bitonic_merge`, pokud je v sekvenci 500 nebo méně prvků. Můžete také naplánovat celkovou strategii řazení na základě množství práce. Může být například efektivnější používat sériové verze algoritmu rychlého řazení, pokud pole obsahuje méně než 500 položek, jak je znázorněno v následujícím příkladu:

[!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]

Stejně jako u jakéhokoli paralelního algoritmu doporučujeme profil a ladění kódu podle potřeby.

## <a name="see-also"></a>Viz také

[Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[parallel_invoke funkce](reference/concurrency-namespace-functions.md#parallel_invoke)
