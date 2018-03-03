---
title: "Postupy: použití objektu combinable ke slučování množin | Microsoft Docs"
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
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8bbd36e9536707bc639e8f80cc019b7fda18f793
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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


