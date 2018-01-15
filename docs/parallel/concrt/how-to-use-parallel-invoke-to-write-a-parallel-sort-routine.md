---
title: "Postupy: použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff14294236efc26b83d31ad185dc1cfd6329dbe9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-parallelinvoke-to-write-a-parallel-sort-routine"></a>Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění
Tento dokument popisuje postup použití [parallel_invoke –](../../parallel/concrt/parallel-algorithms.md#parallel_invoke) algoritmus ke zlepšení výkonu algoritmus řazení bitonic. Rekurzivní algoritmus řazení bitonic rozdělí vstupní pořadí na menší oddíly seřazená. Algoritmus řazení bitonic můžete paralelně spustit, protože každý oddíl operace je nezávislé na dalších operací.  
  
 I když je příkladem bitonic řazení *řazení sítě* , seřadí všechny kombinace vstupní pořadí, v tomto příkladu seřadí pořadí, jejichž délky jsou power dva.  
  
> [!NOTE]
>  Tento příklad používá paralelní řazení rutiny pro obrázek. Můžete také použít integrované řazení algoritmy, které poskytuje knihovně PPL: [concurrency::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort), a [concurrency::parallel_ radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Další informace najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="top"></a>Oddíly  
 Tento dokument popisuje následující úlohy:  
  
- [Provádění Bitonic řazení sériově](#serial)  
  
- [Použití algoritmu parallel_invoke k provedení řazení Bitonic paralelně](#parallel)  
  
##  <a name="serial"></a>Provádění Bitonic řazení sériově  
 Následující příklad ukazuje sériové verzi algoritmus bitonic řazení. `bitonic_sort` Funkce rozdělí sekvenci na dva oddíly, tyto oddíly ve směru seřadí a pak sloučí výsledky. Tato funkce volá dvakrát rekurzivně sama k seřazení každý oddíl.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]  
  
 [[Horní](#top)]  
  
##  <a name="parallel"></a>Použití algoritmu parallel_invoke k provedení řazení Bitonic paralelně  
 Tato část popisuje postup použití `parallel_invoke` algoritmus algoritmus řazení bitonic paralelně.  
  
### <a name="procedures"></a>Procedury  
  
##### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>Paralelní provádění algoritmu bitonického řazení  
  
1.  Přidat `#include` direktivy pro ppl.h soubor hlavičky.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]  
  
2.  Přidat `using` direktivy pro `concurrency` oboru názvů.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]  
  
3.  Vytvořte novou funkci, nazývá `parallel_bitonic_mege`, které používá `parallel_invoke` algoritmus sloučit pořadí paralelně, pokud je dostatečné množství práce uděláte. Jinak volání `bitonic_merge` sloučit daná pořadí sériově.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]  
  
4.  Provést proces, který se podobá v předchozím kroku, ale pro `bitonic_sort` funkce.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]  
  
5.  Vytvořit přetížené verzi `parallel_bitonic_sort` funkce, která seřadí pole ve vzestupném pořadí.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]  
  
 `parallel_invoke` Algoritmus snižuje režii provedením poslední řadu úloh na kontext volání. Například v `parallel_bitonic_sort` funkce, první úloha se spustí v samostatných kontextu a druhý úloha se spustí v kontext volání.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]  
  
 Následující kompletní příklad provádí sériové a paralelní verze algoritmus bitonic řazení. V příkladu také vytiskne konzole doba potřebná k provedení jednotlivých výpočtu.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]  
  
 Následující ukázkový výstup je pro počítač, který se čtyřmi procesory.  
  
```Output  
serial time: 4353  
parallel time: 1248  
```  
  
 [[Horní](#top)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, zkopírujte jej a vložte ji do projektu sady Visual Studio nebo ho vložte do souboru, který je pojmenován `parallel-bitonic-sort.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc paralelní bitonic-sort.cpp**  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento příklad používá `parallel_invoke` algoritmus místo [concurrency::task_group](reference/task-group-class.md) třídy, protože doba platnosti každé skupiny úloh nepřesahuje funkci. Doporučujeme vám, že používáte `parallel_invoke` při můžete, protože obsahuje menší provádění režii než `task group` objektů a proto umožňuje zapisovat lépe provádění kódu.  
  
 Paralelní verze některé algoritmy provést lépe, jenom v případě, že není dostatečná práce uděláte. Například `parallel_bitonic_merge` funkce volá sériové verze `bitonic_merge`, pokud jsou v pořadí elementů 500 nebo méně. Můžete taky naplánovat strategie celkové řazení podle množství práce. Například může být efektivnější použití sériového portu verze algoritmus rychlého řazení, pokud pole obsahuje méně než 500 položek, jak je znázorněno v následujícím příkladu:  
  
 [!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]  
  
 Stejně jako u jakékoli paralelní algoritmus, doporučujeme, abyste profilu a optimalizovat kód podle potřeby.  
  
## <a name="see-also"></a>Viz také  
 [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [parallel_invoke – funkce](reference/concurrency-namespace-functions.md#parallel_invoke)

