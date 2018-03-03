---
title: "Postupy: smyčky Parallel_for_each | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 179fa4b055b4743303f5d72ebec851a1d10def93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [parallel_for_each – funkce](reference/concurrency-namespace-functions.md#parallel_for_each)


