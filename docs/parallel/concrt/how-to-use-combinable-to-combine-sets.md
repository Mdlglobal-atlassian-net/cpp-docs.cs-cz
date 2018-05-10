---
title: 'Postupy: použití objektu combinable ke slučování množin | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 689dacb98bc9f8053686a02414151b4982edca67
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-combinable-to-combine-sets"></a>Postupy: Použití objektu combinable ke slučování množin
Toto téma ukazuje, jak používat [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídy výpočetní sadu prvočísel.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá sadu prvočísel dvakrát. Každý výpočetní ukládá výsledek v [std::bitset](../../standard-library/bitset-class.md) objektu. V příkladu nejprve sériově vypočítá sada a pak vypočítá sadu paralelně. V příkladu také vytiskne konzole čas, který je nutné provést i výpočty.  
  
 Tento příklad používá [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus a `combinable` objektu k vygenerování sady specifická pro přístup z více vláken. Poté použije [concurrency::combinable::combine_each](reference/combinable-class.md#combine_each) metoda kombinovat místní sady do závěrečné sady.  

  
 [!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]  
  
 Následující ukázkový výstup je pro počítač, který se čtyřmi procesory.  
  
```Output  
serial time: 312 ms  
 
parallel time: 78 ms  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `parallel-combine-primes.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc paralelní zkombinujte primes.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable – třída](../../parallel/concrt/reference/combinable-class.md)   
 [combinable::combine_each – metoda](reference/combinable-class.md#combine_each)


