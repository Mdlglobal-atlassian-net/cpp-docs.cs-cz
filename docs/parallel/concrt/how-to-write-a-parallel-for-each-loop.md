---
title: 'Postupy: smyčky Parallel_for_each | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68ba40b7d9ea93e73d9d18d3548b0c0f34c6411f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-write-a-parallelforeach-loop"></a>Postupy: Programování smyčky parallel_for_each
Tento příklad ukazuje způsob použití [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus vypočítat počet prvočísel v [std::array](../../standard-library/array-class-stl.md) objekt paralelně.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá počet prvočísel v matici dvakrát. V příkladu se nejdřív pomocí [std::for_each](../../standard-library/algorithm-functions.md#for_each) algoritmus vypočítat počet sériově. V příkladu se pak použije `parallel_for_each` algoritmus provést stejný úkol paralelně. V příkladu také vytiskne konzole čas, který je nutné provést i výpočty.  
  
 [!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]  
  
 Následující ukázkový výstup je pro počítač, který se čtyřmi procesory.  
  
```Output  
serial version:  
found 17984 prime numbers  
took 6115 ms  
 
parallel version:  
found 17984 prime numbers  
took 1653 ms  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, zkopírujte jej a vložte ji do projektu sady Visual Studio nebo ho vložte do souboru, který je pojmenován `parallel-count-primes.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc paralelní počet primes.cpp**  
  
## <a name="robust-programming"></a>Robustní programování  
 Výraz lambda, který předává v příkladu `parallel_for_each` algoritmus používá `InterlockedIncrement` funkce Povolit paralelní iterace smyčky se zvýší čítače současně. Pokud například používáte funkce `InterlockedIncrement` Pokud chcete synchronizovat přístup ke sdíleným prostředkům, může představovat kritické body v kódu. Mechanismus bez zámek synchronizace můžete použít například, [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třída eliminovat současný přístup ke sdíleným prostředkům. Pro příklad, který používá `combinable` třída tímto způsobem, najdete v části [postupy: použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md).  
  
## <a name="see-also"></a>Viz také  
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for_each Function](reference/concurrency-namespace-functions.md#parallel_for_each)


