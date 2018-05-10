---
title: Paralelní vzory knihovna (PPL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Parallel Patterns Library (PPL)
ms.assetid: 40fd86b2-69fa-45e5-93d8-98a75636c242
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7263d764014fa3532c3234bd4c7a0d4f1ff8d3c3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="parallel-patterns-library-ppl"></a>Knihovna PPL (Parallel Patterns Library)
Paralelní vzory knihovny (PPL) poskytuje imperativní programovací model, který zvýší úroveň škálovatelnost a snadné použití pro vývoj souběžných aplikací. Knihovně PPL staví na plánování a prostředků součásti správy Concurrency Runtime. Vyvolá úroveň abstrakce mezi kódu aplikace a podkladový vláken mechanismus tím, že poskytuje obecné, bezpečnost typů algoritmů a kontejnerů, které fungují na data paralelně. Knihovně PPL také umožňuje vyvíjet aplikace, které škálování tím, že poskytuje alternativy do sdíleného stavu.  
  
 Knihovně PPL poskytuje následující funkce:  
  
- *Úloha paralelismus*: mechanismus, který funguje na Windows zachovalo souběžně provést několik pracovních položek (úlohy)  
  
- *Paralelní algoritmy*: Obecné algoritmy, které funguje nad Concurrency Runtime tak, aby fungoval na kolekce dat paralelně  
  
- *Paralelní kontejnery a objekty*: Obecné kontejneru typy, které poskytují bezpečné souběžný přístup k jejich elementů  
  
## <a name="example"></a>Příklad  
 Knihovně PPL poskytuje programovací model, který vypadá takto: standardní knihovna C++. Následující příklad ukazuje mnoho funkcí knihovně PPL. Vypočítá několik Fibonacciho čísla sériově a paralelně. Obě výpočty fungovat na [std::array](../../standard-library/array-class-stl.md) objektu. V příkladu také vytiskne konzole čas, který je nutné provést i výpočty.  
  
 Sériové verze používá standardní knihovna C++ [std::for_each](../../standard-library/algorithm-functions.md#for_each) algoritmus procházení pole a ukládá výsledky do [std::vector](../../standard-library/vector-class.md) objektu. Paralelní verze provádí stejný úkol, ale používá knihovně PPL [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus a ukládá výsledky do [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) objektu. `concurrent_vector` Třída umožňuje každé iteraci smyčky současně přidat elementy bez nutnosti synchronizovat oprávnění k zápisu do kontejneru.  
  
 Protože `parallel_for_each` jednání souběžně, paralelní verze tohoto příkladu nutné seřadit `concurrent_vector` objekt, který chcete vytvořit stejné výsledky jako sériové verze.  
  
 Všimněte si, že příklad používá metodu naïve k výpočtu čísel Fibonacciho; Tato metoda však ukazuje, jak Concurrency Runtime může zlepšit výkon dlouho výpočty.  
  
 [!code-cpp[concrt-parallel-fibonacci#1](../../parallel/concrt/codesnippet/cpp/parallel-patterns-library-ppl_1.cpp)]  
  
 Následující ukázkový výstup je pro počítač, který se čtyřmi procesory.  
  
```Output  
serial time: 9250 ms  
parallel time: 5726 ms  
 
fib(24): 46368  
fib(26): 121393  
fib(41): 165580141  
fib(42): 267914296  
```  
  
 Každé iteraci smyčky vyžaduje jiný množství času na dokončení. Výkon `parallel_for_each` ohraničená operaci, která se dokončí poslední. Proto by nemělo očekávat vylepšení výkonu lineární mezi verzemi sériové a paralelní tohoto příkladu.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Popisuje roli úloh a skupiny úloh v knihovně PPL.|  
|[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)|Popisuje, jak pomocí paralelní algoritmy, jako například `parallel_for` a `parallel_for_each`.|  
|[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)|Popisuje různé paralelní kontejnery a objekty, které jsou poskytovány knihovně PPL.|  
|[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)|Vysvětluje, jak zrušit práci, kterou provádí paralelní algoritmem.|  
|[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)|Popisuje Concurrency Runtime, který zjednodušuje paralelní programování a obsahuje odkazy na související témata.|

