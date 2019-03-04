---
title: 'Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění'
ms.date: 11/04/2016
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
ms.openlocfilehash: 329cf275f283ba7b57276d06e909905c9a900697
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284174"
---
# <a name="how-to-use-parallelinvoke-to-write-a-parallel-sort-routine"></a>Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění

Tento dokument popisuje způsob použití [algoritmu parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke) algoritmus pro zlepšení výkonu bitonického algoritmu řazení. Rekurzivně algoritmu bitonického řazení rozdělí vstupní sekvence do menších oddílů seřazená. Algoritmu bitonického řazení můžou běžet paralelně, protože každý oddíl operace nezávislé na všechny ostatní operace.

I když je příkladem bitonického řazení *řazení sítě* , který seřadí všechny kombinace vstupní pořadí, v tomto příkladu seřadí sekvence, jejichž délky mají hodnotu mocninou čísla 2.

> [!NOTE]
>  Tento příklad používá rutiny paralelního třídění pro ilustraci. Můžete také použít integrované algoritmy řazení poskytuje PPL: [concurrency::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort), a [concurrency::parallel_ radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Další informace najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

##  <a name="top"></a> Oddíly

Tento dokument popisuje následující úkoly:

- [Sériové provádění Bitonického řazení](#serial)

- [Paralelně s použitím algoritmu parallel_invoke k provádění Bitonického řazení](#parallel)

##  <a name="serial"></a> Sériové provádění Bitonického řazení

Následující příklad ukazuje sériového portu verzi bitonického algoritmu řazení. `bitonic_sort` Funkce sekvence rozdělí na dva oddíly, řadí těchto oddílů ve směru a pak sloučí výsledky. Tato funkce zavolá sama sebe dvakrát rekurzivně seřadíte každý oddíl.

[!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]

[[Horní](#top)]

##  <a name="parallel"></a> Paralelně s použitím algoritmu parallel_invoke k provádění Bitonického řazení

Tato část popisuje způsob použití `parallel_invoke` algoritmus paralelní provádění bitonického algoritmu řazení.

### <a name="procedures"></a>Procedury

##### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>Paralelní provádění algoritmu bitonického řazení

1. Přidat `#include` směrnice pro ppl.h souboru záhlaví.

[!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]

1. Přidat `using` směrnice pro `concurrency` oboru názvů.

[!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]

1. Vytvořit novou funkci nazvanou `parallel_bitonic_mege`, který používá `parallel_invoke` algoritmus sloučit pořadí paralelně, pokud je dostatečné množství práce. V opačném případě volat `bitonic_merge` sloučit sekvencí sériově.

[!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]

1. Provádění procesu, který se podobá v předchozím kroku, ale pro `bitonic_sort` funkce.

[!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]

1. Vytvořit přetíženou verzi `parallel_bitonic_sort` funkce, která řadí pole ve vzestupném pořadí.

[!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]

`parallel_invoke` Algoritmus snižuje režii provedením poslední řadu úloh na kontext volání. Například v `parallel_bitonic_sort` spuštění první úlohy v rámci samostatné funkce, a druhý úkol spustí na kontext volání.

[!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]

Následující kompletní příklad provádí sériové číslo a paralelní verze bitonického algoritmu řazení. V příkladu také tiskne na konzolu čas, který je potřeba provést každý výpočet.

[!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]

Následující ukázkový výstup je pro počítač, který má čtyři procesory.

```Output
serial time: 4353
parallel time: 1248
```

[[Horní](#top)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li kód zkompilovat, ho zkopírujte a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `parallel-bitonic-sort.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /EHsc parallel-bitonic-sort.cpp**

## <a name="robust-programming"></a>Robustní programování

V tomto příkladu `parallel_invoke` algoritmus místo [concurrency::task_group](reference/task-group-class.md) třídy, protože životnost každá skupina úloh nepřesahuje funkce. Doporučujeme, abyste použili `parallel_invoke` kde je to možné protože má nižší nároky na spuštění než `task group` objekty a proto vám umožňuje psát lépe uskutečnitelný kód.

Paralelní verze některé algoritmy líp fungovat pouze v případě, že je dostatečná pracovní postup. Například `parallel_bitonic_merge` funkce volá sériového portu verze `bitonic_merge`, pokud existují 500 nebo méně prvky v sekvenci. Můžete taky naplánovat strategie celkové řazení podle množství práce. Například může být efektivnější použití sériového portu verze algoritmus rychlého řazení, pokud pole obsahuje méně než 500 položek, jak je znázorněno v následujícím příkladu:

[!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]

Stejně jako u jakékoli paralelního algoritmu, doporučujeme, abyste profilování a ladění kódu podle potřeby.

## <a name="see-also"></a>Viz také:

[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[parallel_invoke – funkce](reference/concurrency-namespace-functions.md#parallel_invoke)
