---
title: Knihovna PPL (Parallel Patterns Library)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library (PPL)
ms.assetid: 40fd86b2-69fa-45e5-93d8-98a75636c242
ms.openlocfilehash: 11440d56b9618d4763e1b7e47a21b365bbdc0c15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301848"
---
# <a name="parallel-patterns-library-ppl"></a>Knihovna PPL (Parallel Patterns Library)

Knihovna paralelních vzorů (PPL) poskytuje imperativní programovací model, který podporuje škálovatelnost a snadné použití pro vývoj souběžných aplikací. PPL sestavení do plánování a resource management součástí modulu Runtime souběžnosti. Vyvolá úrovni abstrakce mezi kódu aplikace a základní mechanismus dělení na vlákna tím, že poskytuje typově bezpečný, obecné algoritmy a kontejnerů, které fungují s daty současně. PPL také umožňuje vyvíjet aplikace, které se škálují tím, že poskytuje alternativy k sdílený stav.

PPL poskytuje následující funkce:

- *Paralelismus úloh*: mechanismus, který pracuje nad Windows fondu vláken spustit paralelně několik pracovních položek (úkoly)

- *Paralelní algoritmy*: Obecné algoritmy, které funguje na modulu Runtime souběžnosti, tak, aby fungoval na kolekce dat paralelně

- *Paralelní kontejnery a objekty*: kontejner obecné typy, které poskytují bezpečné souběžný přístup k jejich prvky

## <a name="example"></a>Příklad

PPL poskytuje programovací model, který vypadá podobně jako standardní knihovny C++. Následující příklad ukazuje mnoho funkcí PPL. Několik čísel Fibonacciho vypočítává sériově i paralelně. Zpracovat oba výpočty [std::array](../../standard-library/array-class-stl.md) objektu. V příkladu také tiskne na konzolu čas, který je potřeba provést i výpočty.

Sériové verze používá C++ standardní knihovny [std::for_each](../../standard-library/algorithm-functions.md#for_each) algoritmus k procházení pole a ukládá výsledky [std::vector](../../standard-library/vector-class.md) objektu. Paralelní verze provádí stejné úlohy, ale používá PPL [: concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus a ukládá výsledky [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) objektu. `concurrent_vector` Třída umožňuje každého průchodu cyklem současně přidávat prvky bez nutnosti synchronizovat oprávnění k zápisu do kontejneru.

Protože `parallel_for_each` funguje souběžně, paralelní verze tohoto příkladu musí řazení `concurrent_vector` objekt vytvářejí stejné výsledky jako verze sériového portu.

Všimněte si, že v příkladu používá metodu naivní vypočítat Fibonacciho čísel. Tato metoda však ukazuje, jak modulu Runtime souběžnosti, můžete zvýšit výkon dlouhé výpočtů.

[!code-cpp[concrt-parallel-fibonacci#1](../../parallel/concrt/codesnippet/cpp/parallel-patterns-library-ppl_1.cpp)]

Následující ukázkový výstup je pro počítač, který má čtyři procesory.

```Output
serial time: 9250 ms
parallel time: 5726 ms

fib(24): 46368
fib(26): 121393
fib(41): 165580141
fib(42): 267914296
```

Každá iterace smyčky vyžaduje jinou množství času na dokončení. Výkon `parallel_for_each` ohraničená operaci, která skončí jako poslední. Proto by neměli očekávat lineární rychlejší mezi sériové a paralelní verze tohoto příkladu.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Popisuje využití úloh a skupin úloh v knihovně PPL.|
|[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)|Popisuje, jak použít paralelní algoritmy, jako `parallel_for` a `parallel_for_each`.|
|[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)|Popisuje různé paralelní kontejnery a objekty, které jsou k dispozici v knihovně PPL.|
|[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)|Vysvětluje, jak zrušit práci prováděnou pomocí paralelního algoritmu.|
|[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)|Popisuje modulu Runtime souběžnosti, který zjednodušuje paralelní programování a obsahuje odkazy na související témata.|
