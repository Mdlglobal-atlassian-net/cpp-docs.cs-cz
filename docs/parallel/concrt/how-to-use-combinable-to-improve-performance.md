---
title: "Postupy: použití objektu combinable ke zlepšení výkonu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7bd035b74988758142fe9d0fedc43946f35c2d58
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-combinable-to-improve-performance"></a>Postupy: Použití objektu combinable ke zlepšení výkonu
Tento příklad ukazuje způsob použití [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třída vypočítat součet čísel v [std::array](../../standard-library/array-class-stl.md) objektu, která jsou prime. `combinable` Třída zlepšuje odstraněním sdílený stav.  
  
> [!TIP]
>  V některých případech paralelní mapování ([concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) a snížení ([souběžnosti:: parallel_reduce –](reference/concurrency-namespace-functions.md#parallel_reduce)) může poskytnout vylepšení výkonu přes `combinable`. Příklad, že používá mapování a snížení operací budou mít stejné výsledky jako v tomto příkladu, naleznete v části [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá [std::accumulate](../../standard-library/numeric-functions.md#accumulate) funkce pro výpočet součet prvků v poli, které jsou prime. V tomto příkladu `a` je `array` objektu a `is_prime` funkce určuje, zda je jeho vstupní hodnoty prime.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]  
  
## <a name="example"></a>Příklad  

 Následující příklad ukazuje způsob naïve učinit paralelní předchozí příklad. Tento příklad používá [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus zpracovat pole paralelně a [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) objekt, který má přístup k synchronizaci `prime_sum` proměnné . V tomto příkladu se nedá použít, protože každé vlákno musí čekat na sdílený prostředek k dispozici.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `combinable` objekt, který chcete-li zlepšit výkon v předchozím příkladu. Tento příklad eliminuje potřebu synchronizačními objekty; se škáluje, protože `combinable` objektu umožňuje každé vlákno k provedení úkolu nezávisle.  
  
 A `combinable` objekt se obvykle používá ve dvou krocích. Nejprve vytvořit řadu podrobných výpočty provedením pracovní paralelně. V dalším kroku kombinovat (nebo snižte) výpočtů do konečný výsledek. Tento příklad používá [concurrency::combinable::local](reference/combinable-class.md#local) metodu za účelem získání odkazu na místní součet. Poté použije [concurrency::combinable::combine](reference/combinable-class.md#combine) metoda a [std::plus](../../standard-library/plus-struct.md) objekt, který chcete kombinovat místní výpočtů do konečný výsledek.  

  
 [!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující kompletní příklad vypočítá součet prime čísel sériově a paralelně. V příkladu se vytiskne ke konzole čas, který je nutné provést i výpočty.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]  
  
 Následující ukázkový výstup je pro počítač, který se čtyřmi procesory.  
  
```Output  
1709600813  
serial time: 6178 ms  
 
1709600813  
parallel time: 1638 ms  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, zkopírujte jej a vložte ji do projektu sady Visual Studio nebo ho vložte do souboru, který je pojmenován `parallel-sum-of-primes.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc paralelní – součet z – primes.cpp**  
  
## <a name="robust-programming"></a>Robustní programování  
 Příklad, že používá mapování a snížit na stejné výsledky operací, naleznete v části [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="see-also"></a>Viz také  
 [Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable – třída](../../parallel/concrt/reference/combinable-class.md)   
 [critical_section – třída](../../parallel/concrt/reference/critical-section-class.md)
