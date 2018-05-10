---
title: 'Postupy: použití algoritmu parallel_invoke k provádění paralelních operací | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07c7a5248d5a132ae7b0542bfcedddee0c081753
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací
Tento příklad ukazuje způsob použití [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus ke zlepšení výkonu programu, který provádí víc operací na sdílený zdroj dat. Protože žádné operace upravit zdroj, se mohou být provedeny souběžně přehledné způsobem.  

  
## <a name="example"></a>Příklad  
 Vezměte v úvahu následující příklad kódu, který vytváří proměnné typu `MyDataType`, volá funkci k chybě při inicializaci tuto proměnnou a potom provede několik náročná operace s těmito daty.  
  
 [!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]  
  
 Pokud `lengthy_operation1`, `lengthy_operation2`, a `lengthy_operation3` funkce Neupravujte `MyDataType` proměnné, tyto funkce mohou být provedeny souběžně bez dalších úprav.  
  
## <a name="example"></a>Příklad  
 Následující příklad změní předchozí příklad spouštět souběžně. `parallel_invoke` Algoritmus spustí každý úkol paralelně a vrátí po dokončení všech úloh.  
  
 [!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad stáhne *Iliad* podle Homer z gutenberg.org a provádí víc operací na daný soubor. V příkladu nejprve sériově provádí tyto operace a pak provádí stejné operace paralelně.  
  
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
  
 Tento příklad používá `parallel_invoke` algoritmus volání více funkcí které působí na stejném datovém zdroji. Můžete použít `parallel_invoke` algoritmus volat libovolnou sadu funkcí paralelně, ne jenom ty, které fungují v stejná data.  
  
 Protože `parallel_invoke` algoritmus volá funkci každý pracovní paralelně, jeho výkon ohraničená funkce, která přebírá nejdelší doba na dokončení (to znamená, pokud modul runtime zpracovává jednotlivé funkce samostatné procesoru). Pokud v tomto příkladu provede další informace o úlohách paralelně než počet dostupných procesorů, můžete spustit více úloh na každý procesor. V takovém případě výkonu ohraničené skupiny úlohy, která trvá nejdelší dobu dokončit.  
  
 Protože v tomto příkladu provádí tři úlohy paralelně, není pravděpodobné, že výkon a škálování na počítačích, které mají víc než třemi procesory. Ke zlepšení výkonu další, můžete rozdělit na menší úkoly nejdelší běžící úlohy a paralelní spuštění těchto úloh.  
  
 Můžete použít `parallel_invoke` algoritmus místo [concurrency::task_group](reference/task-group-class.md) a [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) třídy Pokud nepožadujete podporu pro zrušení. Pro příklad, který porovnává využití `parallel_invoke` algoritmus versus skupiny úloh najdete v části [postupy: použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, zkopírujte jej a vložte ji do projektu sady Visual Studio nebo ho vložte do souboru, který je pojmenován `parallel-word-mining.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc /MD/DUNICODE /D_AFXDLL paralelní word-mining.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_invoke – funkce](reference/concurrency-namespace-functions.md#parallel_invoke)


