---
title: "Postupy: převedení smyčky OpenMP využívající zpracování výjimek na využití modulu Concurrency Runtime | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d2964c629ce8a3a83799278ac822b589992b4995
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>Postupy: Převedení smyčky OpenMP využívající zpracování výjimek na využití modulu Concurrency Runtime
Tento příklad ukazuje, jak převést OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pro](../../parallel/openmp/reference/for-openmp.md) smyčky, který provádí zpracování výjimek používat zpracování mechanismus výjimek Concurrency Runtime.  
  
 V OpenMP musí být zachycena výjimka, která je vyvolána v paralelní oblasti a zpracovány ve stejné oblasti, ve stejném vlákně, v. Výjimka, která řídicí sekvence paralelní oblast je zachytila obslužná rutina neošetřených výjimek, která ukončí proces ve výchozím nastavení.  
  

 V Concurrency Runtime, když je vyvolána výjimka v těle pracovní funkce, kterou předáte pro skupinu úloh, jako [concurrency::task_group](reference/task-group-class.md) nebo [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objekt, nebo paralelní algoritmus jako [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), modul runtime ukládá této výjimky a zařazuje do kontextu, která čeká na skupinu úloh nebo algoritmus ukončíte. Pro skupiny úloh čekací kontext je kontext, který volá [concurrency::task_group::wait](reference/task-group-class.md#wait), [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait), [concurrency::task_group::run_and _wait](reference/task-group-class.md#run_and_wait), nebo [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait). Čekání na kontext pro paralelní algoritmus, není kontext, který volá tento algoritmus. Modul runtime také zastaví všechny aktivní úlohy, které jsou ve skupině úloh, včetně programů v podřízené skupiny úloh, a zahodí se všechny úlohy, které nebyly ještě nezačala.  


  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak zpracování výjimek v OpenMP `parallel` oblasti a v volání `parallel_for`. `do_work` Funkce provede požadavek na přidělení paměti, neproběhne úspěšně a proto vyvolá výjimku typu [std::bad_alloc](../../standard-library/bad-alloc-class.md). Ve verzi, která používá OpenMP vláken, která vyvolala výjimku musí také catch ho. Jinými slovy musí každé iteraci smyčky parallel OpenMP ošetření výjimky. Ve verzi, která používá Concurrency Runtime hlavní vlákno zachytí výjimku, která je vyvolána jiné vlákno.  
  
 [!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that uses-exception-handling_1.cpp)]  
  
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
  
 Ve verzi tohoto příkladu, který používá OpenMP výjimka v dojde a jsou zpracována každé iteraci smyčky. Ve verzi, která používá Concurrency Runtime, modul runtime ukládá výjimku, zastaví všechny aktivní úlohy, zahodí se všechny úlohy, které dosud nebyly spuštění a zařazuje výjimka, která má kontext, který volá `parallel_for`.  
  
 Pokud budete potřebovat, že verze, která používá OpenMP ukončí po výskytu výjimky, můžete použít logický příznak do další iterace smyčky signál, že došlo k chybě. Jako v příkladu v tomto tématu [postupy: převedení smyčky OpenMP této používá zrušení na využití modulu Concurrency Runtime](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md), následující smyčce opakování se nic nestane. Pokud je nastavený příznak. Naopak pokud požadujete, aby smyčky, který používá Concurrency Runtime pokračuje po výskytu výjimky, ošetření výjimky v těle paralelní smyčky, sám sebe.  
  
 Ostatní součásti Concurrency Runtime, jako je například asynchronních agentů a prosté úlohy, není přenosu výjimky. Místo toho neošetřené výjimky jsou zachyceny pomocí obslužná rutina neošetřených výjimek, která ukončí proces ve výchozím nastavení. Další informace o zpracování výjimek najdete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 Další informace o `parallel_for` a dalších paralelní algoritmy najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `concrt-omp-exceptions.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc/OpenMP concrt-omp – exceptions.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)

