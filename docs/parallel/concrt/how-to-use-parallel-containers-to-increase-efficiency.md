---
title: 'Postupy: použití paralelních kontejnerů ke zvýšení efektivity | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0e0d79693bef358a582e878ec2d6d138387752c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>Postupy: Použití paralelních kontejnerů ke zvýšení účinnosti
Toto téma ukazuje způsob použití paralelních kontejnerů ke efektivně ukládat a přistupovat k datům paralelně.  
  
 Příklad kódu vypočítá sadu prime a čísla Carmichael paralelně. Potom pro každou číslo Carmichael kód vypočítá prvotní faktory toto číslo.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `is_prime` funkce, která určuje, zda je vstupní hodnotu prime číslo, a `is_carmichael` funkci, která určuje, zda je vstupní hodnoty Carmichael číslo.  
  
 [!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `is_prime` a `is_carmichael` funkce pro výpočet sady prime a Carmichael čísla. V příkladu se používá [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) a [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmy s cílem každou výpočetní nastavit paralelně. Další informace o paralelní algoritmy najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
 Tento příklad používá [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) objekt pro uložení sadu Carmichael čísla, protože tento objekt se bude používat později jako fronty pracovních položek. Použije [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) objekt pro uložení sadu prvočísel, protože se později iteraci přes tento nastavit najít prvotní faktorů.  
  
 [!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `prime_factors_of` funkci, která používá zkušební dělení najít všechny prvotní faktory předané hodnoty.  
  
 Tato funkce používá [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus pro iteraci prostřednictvím kolekce prvočísel. `concurrent_vector` Objektu umožňuje paralelní smyčky současně přidat prvotní faktory na výsledek.  
  
 [!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]  
  
## <a name="example"></a>Příklad  
 Tento příklad zpracovává každý prvek ve frontě Carmichael čísel voláním `prime_factors_of` funkce pro výpočet jeho prvotní faktorů. Používá skupinu úloh pro práci paralelně. Další informace o skupinách úloh najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Tento příklad zobrazí prvotní faktory pro každé Carmichael číslo, pokud toto číslo má více než čtyři hlavní faktory.  
  
 [!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje kompletní příklad, který používá k výpočtu prvotní faktory čísel Carmichael paralelních kontejnerů.  
  
 [!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]  
  
 Tento příklad vytvoří následující ukázkový výstup.  
  
```Output  
Prime factors of 9890881 are: 7 11 13 41 241.  
Prime factors of 825265 are: 5 7 17 19 73.  
Prime factors of 1050985 are: 5 13 19 23 37.  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `carmichael-primes.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc carmichael-primes.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)   
 [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [concurrent_vector – třída](../../parallel/concrt/reference/concurrent-vector-class.md)   
 [concurrent_queue – třída](../../parallel/concrt/reference/concurrent-queue-class.md)   
 [parallel_invoke – funkce](reference/concurrency-namespace-functions.md#parallel_invoke)   
 [parallel_for – funkce](reference/concurrency-namespace-functions.md#parallel_for)   
 [task_group – třída](reference/task-group-class.md)
