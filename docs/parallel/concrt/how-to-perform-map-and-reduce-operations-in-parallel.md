---
title: "Postup: provedení mapy a snížit operace paralelně | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6648933aa972ec1391afe2d9cecd37b15ad53f9c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>Postupy: Paralelní provádění operací mapování a redukce

Tento příklad ukazuje způsob použití [concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) a [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algoritmy a [concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)třídu k určení počtu výskytů slova v souborech.  
  
 A *mapy* operace platí pro každou hodnotu v pořadí funkce. A *snížit* operace kombinuje elementy sekvence do jednu hodnotu. Můžete použít standardní knihovna C++ [std::transform](../../standard-library/algorithm-functions.md#transform) a [std::accumulate](../../standard-library/numeric-functions.md#accumulate) funkce k provedení mapy a snížení operací. Ke zlepšení výkonu mnohé problémy, ale můžete použít `parallel_transform` algoritmus k provedení operace mapy paralelně a `parallel_reduce` algoritmus k provedení operace. Snižte paralelně. V některých případech můžete použít `concurrent_unordered_map` k provádění mapy a snižte v rámci jedné operace.  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí počet výskytů slova v souborech. Používá [std::vector](../../standard-library/vector-class.md) představují obsah dva soubory. Operaci mapy vypočítá výskyty jednotlivých slov v každé vektoru. Snižte operaci shromažďuje počty slov v obou vektory.  
  
 [!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, zkopírujte jej a vložte ji do projektu sady Visual Studio nebo ho vložte do souboru, který je pojmenován `parallel-map-reduce.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc paralelní map – reduce.cpp**  
  
## <a name="robust-programming"></a>Robustní programování  
 V tomto příkladu můžete použít `concurrent_unordered_map` třída, která je definována v concurrent_unordered_map.h—to provést mapy a snížit v rámci jedné operace.  
  
 [!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]  
  
 Obvykle paralelní jenom vnější nebo vnitřní smyčky. Paralelní smyčky vnitřní, pokud máte poměrně málo souborů a každý soubor obsahuje mnoho slova. Paralelní smyčky vnější, pokud máte relativně mnoho souborů a každý soubor obsahuje několik slova.  
  
## <a name="see-also"></a>Viz také  
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_transform – funkce](reference/concurrency-namespace-functions.md#parallel_transform)   
 [parallel_reduce – funkce](reference/concurrency-namespace-functions.md#parallel_reduce)   
 [concurrent_unordered_map – třída](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
