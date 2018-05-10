---
title: 'Postupy: použití zpracování přerušení paralelní smyčky výjimek | Microsoft Docs'
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
ms.openlocfilehash: 6bacb9ea6a451026f7a515878cb649090ed9cbf4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>Postupy: Přerušení paralelní smyčky pomocí zpracování výjimek
Toto téma ukazuje, jak zápis vyhledávacího algoritmu pro základní stromové struktury.  
  
 Téma [zrušení](cancellation-in-the-ppl.md) vysvětluje roli zrušení v knihovně paralelní vzory. Použití výjimek je méně efektivní způsob, jak zrušit paralelní práce než použití [concurrency::task_group::cancel](reference/task-group-class.md#cancel) a [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) metody. Však jeden scénář, kde je vhodné použití výjimek zrušit pracovní se při volání do knihovny třetí strany, který používá úlohy nebo paralelní algoritmy, ale neposkytuje `task_group` nebo `structured_task_group` objekt, který chcete zrušit.  

  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje základní `tree` typ, který obsahuje datový prvek a seznam podřízené uzly. V následující části se zobrazí text `for_all` metoda, která opakovaně provede pracovní funkce na všech uzlech podřízené.  
  
 [!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `for_all` metoda. Použije [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus, který se provádí pracovní funkci v každém uzlu stromu paralelně.  
  
 [!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `search_for_value` funkci, která hledá hodnotu v zadaných `tree` objektu. Tato funkce předává `for_all` metoda a pracovní funkce, která způsobí výjimku, pokud najde uzel stromu, který obsahuje zadanou hodnotu.  
  
 Předpokládáme, že `tree` třída poskytuje knihovnu třetí strany, a nelze jej upravovat. V takovém případě použití výjimek je vhodné protože `for_all` metoda neposkytuje `task_group` nebo `structured_task_group` objekt volajícímu. Pracovní funkce je proto nelze přímo zrušit své nadřazené skupiny úloh.  
  
 Pokud pracovní funkce, které zadáte pro skupinu úloh vyvolá výjimku, modul runtime zastaví všechny úlohy, které jsou ve skupině úloh (včetně všech podřízených skupin úloh) a zahodí se všechny úlohy, které nebyly ještě nezačala. `search_for_value` Využívá `try` - `catch` blok k Tisk do konzoly a zachycení výjimky.  
  
 [!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří `tree` objektu a hledá několik hodnot paralelně. `build_tree` Funkce se zobrazí později v tomto tématu.  
  
 [!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]  
  
 Tento příklad používá [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus pro vyhledávání hodnoty paralelně. Další informace o tento algoritmus najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="example"></a>Příklad  
 Následující kompletní příklad používá výjimek pro vyhledávání hodnoty v základní stromové struktury.  
  
 [!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]  
  
 Tento příklad vytvoří následující ukázkový výstup.  
  
```Output  
Found a node with value 32614.  
Found a node with value 86131.  
Did not find node with value 17522.  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `task-tree-search.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc úloh strom search.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)   
 [Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)   
 [task_group – třída](reference/task-group-class.md)   
 [structured_task_group – třída](../../parallel/concrt/reference/structured-task-group-class.md)   
 [parallel_for_each Function](reference/concurrency-namespace-functions.md#parallel_for_each)


