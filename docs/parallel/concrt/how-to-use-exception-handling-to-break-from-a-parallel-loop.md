---
title: 'Postupy: Přerušení paralelní smyčky pomocí zpracování výjimek'
ms.date: 11/04/2016
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
ms.openlocfilehash: a5576e8f2416804cac89f5ec34005f4e08b99c47
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142117"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>Postupy: Přerušení paralelní smyčky pomocí zpracování výjimek

Toto téma ukazuje, jak napsat algoritmus vyhledávání pro základní stromovou strukturu.

[Zrušení](cancellation-in-the-ppl.md) tématu vysvětluje roli zrušení v knihovně paralelních vzorů. Použití zpracování výjimek je méně efektivní způsob, jak zrušit paralelní práci, než použití metod [Concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) a [concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) . V jednom scénáři, kde je použití zpracování výjimek pro zrušení práce, je však vhodné použít při volání knihovny třetí strany, která používá úkoly nebo paralelní algoritmy, ale neposkytuje `task_group` nebo `structured_task_group` objekt pro zrušení.

## <a name="example"></a>Příklad

Následující příklad ukazuje základní typ `tree`, který obsahuje datový prvek a seznam podřízených uzlů. Následující část ukazuje tělo metody `for_all`, která rekurzivně provádí pracovní funkci na každém podřízeném uzlu.

[!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje kód metody `for_all`. Používá algoritmus [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) k provedení pracovní funkce na každém uzlu stromu paralelně.

[!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje funkci `search_for_value`, která vyhledá hodnotu v zadaném objektu `tree`. Tato funkce předává do metody `for_all` pracovní funkci, která je vyvolána, když najde uzel stromu, který obsahuje poskytnutou hodnotu.

Předpokládejme, že je třída `tree` poskytovaná knihovnou třetí strany a že ji nemůžete upravovat. V tomto případě je použití zpracování výjimek vhodné, protože metoda `for_all` neposkytuje volajícímu objekt `task_group` nebo `structured_task_group`. Funkce Work proto nemůže přímo zrušit nadřazenou skupinu úloh.

Když pracovní funkce, kterou zadáte do skupiny úloh, vyvolá výjimku, modul runtime zastaví všechny úlohy ve skupině úloh (včetně všech podřízených skupin úloh) a zahodí všechny úlohy, které ještě nebyly spuštěny. Funkce `search_for_value` používá blok `catch` `try`-k zachycení výjimky a k vytištění výsledku do konzoly.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]

## <a name="example"></a>Příklad

Následující příklad vytvoří objekt `tree` a vyhledá v něm více hodnot paralelně. Funkce `build_tree` je uvedena dále v tomto tématu.

[!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]

V tomto příkladu se používá algoritmus [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) k hledání hodnot paralelně. Další informace o tomto algoritmu najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

## <a name="example"></a>Příklad

Následující kompletní příklad používá zpracování výjimek pro vyhledávání hodnot v základní stromové struktuře.

[!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]

Tento příklad vytvoří následující vzorový výstup.

```Output
Found a node with value 32614.
Found a node with value 86131.
Did not find node with value 17522.
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `task-tree-search.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Task-Tree-Search. cpp**

## <a name="see-also"></a>Viz také

[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[task_group – třída](reference/task-group-class.md)<br/>
[structured_task_group – třída](../../parallel/concrt/reference/structured-task-group-class.md)<br/>
[parallel_for_each funkce](reference/concurrency-namespace-functions.md#parallel_for_each)
