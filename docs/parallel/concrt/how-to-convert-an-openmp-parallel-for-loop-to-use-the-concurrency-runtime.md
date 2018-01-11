---
title: "Postupy: převedení paralelní smyčky for na využití modulu Concurrency Runtime v OpenMP | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a27e07884b4ada54f694136ea2fbca474c9d214d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>Postupy: Převedení paralelní smyčky for v OpenMP na využití modulu Concurrency Runtime

Tento příklad ukazuje, jak převést základní smyčky, který používá OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) a [pro](../../parallel/openmp/reference/for-openmp.md) direktivy na využití modulu Concurrency Runtime [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá k výpočtu počet prvočísel v matici náhodných hodnot OpenMP a Concurrency Runtime.  
  
 [!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
Using OpenMP...  
found 107254 prime numbers.  
Using the Concurrency Runtime...  
found 107254 prime numbers.  
```  
  
 `parallel_for` Algoritmus a OpenMP 3.0 povolit pro index typ, který má být typ se znaménkem integrální nebo nepodepsaných integrálních typu. `parallel_for` Algoritmus také zajišťuje, že zadaný rozsah není přetečení typ se znaménkem. OpenMP verze 2.0 a 2.5 umožňují jenom pro typy podepsaný celočíselný index. OpenMP také neověřuje rozsahu index.  
  
 Verze tohoto příkladu, který používá Concurrency Runtime také používá [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) objektu místě [atomic](../../parallel/openmp/reference/atomic.md) se zvýší hodnota čítače bez nutnosti – direktiva synchronizace.  
  
 Další informace o `parallel_for` a dalších paralelní algoritmy najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md). Další informace o `combinable` třídy najdete v tématu [paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="example"></a>Příklad  

 Tento příklad upraví tak, aby fungoval na předchozímu [std::array](../../standard-library/array-class-stl.md) objekt místo v nativní pole. Protože verze OpenMP 2.0 a 2.5 povolit pro podepsané pouze v indexu integrální typy `parallel_for` konstrukce, iterátory nelze použít pro přístup k elementy kontejneru standardní knihovna C++ paralelně. Paralelní vzory knihovny (PPL) poskytuje [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus, který provádí úlohy, paralelně na kontejner iterativní jako třeba standardní knihovna C++. Používá stejné logiky, která rozdělení oddílů, `parallel_for` algoritmus používá. `parallel_for_each` Algoritmus vypadá takto: standardní knihovna C++ [std::for_each](../../standard-library/algorithm-functions.md#for_each) algoritmus, vyjma toho, že `parallel_for_each` algoritmus provádí úkoly současně.  
  
 [!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `concrt-omp-count-primes.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **concrt modulu cl.exe /EHsc/OpenMP – omp – počet primes.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)   
 [Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)

