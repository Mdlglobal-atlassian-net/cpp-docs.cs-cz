---
title: 'Postupy: zpracování výjimek pro přerušení paralelní smyčky pomocí | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a15910885b26c8026a6e504ef36d492cf63445e8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379824"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>Postupy: Přerušení paralelní smyčky pomocí zpracování výjimek

Toto téma ukazuje, jak zápis vyhledávacího algoritmu pro základní stromové struktury.

Téma [zrušení](cancellation-in-the-ppl.md) vysvětluje roli zrušení v paralelních vzorcích knihovny. Použijte zpracování výjimek je méně efektivní způsob, jak zrušení paralelně prováděných úloh než použití [concurrency::task_group::cancel](reference/task-group-class.md#cancel) a [Concurrency::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) metody. Jeden scénář, kde je vhodné použít zpracování výjimek zrušení prováděných ale při volání do knihovny třetí strany, který používá úkoly a paralelní algoritmy, ale neposkytuje `task_group` nebo `structured_task_group` objekt pro zrušení.

## <a name="example"></a>Příklad

Následující příklad ukazuje základní `tree` typ, který obsahuje datový prvek a seznam podřízených uzlů. Následující části zobrazuje text `for_all` metoda, která opakovaně provede pracovní funkce na každý podřízený uzel.

[!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje `for_all` metody. Používá [: concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus pracovní funkce na každý uzel stromu paralelně.

[!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]

## <a name="example"></a>Příklad

Následující příklad ukazuje `search_for_value` funkce, která hledá hodnotu v poskytnutých `tree` objektu. Tato funkce se předá `for_all` metoda pracovní funkci, která vyvolá výjimku, pokud se najde uzel stromu, který obsahuje zadanou hodnotou.

Předpokládejme, že `tree` třída poskytuje knihovnu třetí strany, a už ho nelze změnit. V takovém případě je vhodné použít zpracování výjimek vzhledem k tomu `for_all` metoda neposkytuje `task_group` nebo `structured_task_group` objekt volajícímu. Pracovní funkce je proto nelze přímo zrušit své nadřazené skupiny úloh.

Pokud je pracovní funkce, které zadáte skupinu úloh vyvolá výjimku, modul runtime zastaví všechny úlohy, které jsou ve skupině úloh (včetně všech podřízených skupin úloh) a zahodí všechny úkoly, které ještě nebyly spuštěny. `search_for_value` Funkce používá `try` - `catch` bloku zachytit výjimku a vytiskne výsledek do konzoly.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]

## <a name="example"></a>Příklad

Následující příklad vytvoří `tree` objekt a hledá několik hodnot současně. `build_tree` Funkce je uveden dále v tomto tématu.

[!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]

V tomto příkladu [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus pro hledání hodnot současně. Další informace o tento algoritmus, najdete v části [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

## <a name="example"></a>Příklad

Následující kompletní příklad používá pro vyhledávání hodnoty v základní stromovou strukturu zpracování výjimek.

[!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]

Tento příklad vytvoří následující ukázkový výstup.

```Output
Found a node with value 32614.
Found a node with value 86131.
Did not find node with value 17522.
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `task-tree-search.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc úloh strom search.cpp**

## <a name="see-also"></a>Viz také

[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[task_group – třída](reference/task-group-class.md)<br/>
[structured_task_group – třída](../../parallel/concrt/reference/structured-task-group-class.md)<br/>
[parallel_for_each Function](reference/concurrency-namespace-functions.md#parallel_for_each)

