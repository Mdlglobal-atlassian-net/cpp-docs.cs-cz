---
title: 'Postupy: převedení smyčky OpenMP využívající redukční proměnnou na využití modulu Concurrency Runtime | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0191f88eea47d21c730172ddb3594db7655006ca
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692766"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>Postupy: Převedení smyčky OpenMP využívající redukční proměnnou na využití modulu Concurrency Runtime
Tento příklad ukazuje, jak převést OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pro](../../parallel/openmp/reference/for-openmp.md) smyčky, který používá [snížení](../../parallel/openmp/reference/reduction.md) klauzule na využití modulu Concurrency Runtime.  
  
 OpenMP `reduction` klauzule můžete určit jeden nebo více vlákno soukromé proměnné, které se vztahují na operaci snížení na konci paralelní oblast. OpenMP predefines sadu operátory snížení. Každý redukční proměnnou, musí být skalární hodnota (například `int`, `long`, a `float`). OpenMP také definuje několik omezení při použití redukční proměnné v paralelní oblasti.  
  
 Paralelní vzory knihovny (PPL) poskytuje [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídy, která poskytuje opakovaně použitelný, místní úložiště, které vám umožní provádět podrobné výpočty a pak sloučit těchto výpočtů do konečné výsledek. `combinable` Třída je šablonu, která funguje na skalární a komplexní typy. Použít `combinable` třídy, provedou dílčí výpočtů v těle paralelní konstrukce a pak zavolají [concurrency::combinable::combine](reference/combinable-class.md#combine) nebo [concurrency::combinable::combine_each](reference/combinable-class.md#combine_each) Metoda pro vytvoření konečný výsledek. `combine` a `combine_each` trvat každá z metod *kombinovat funkce* který určuje, jak kombinovat každý pár elementů. Proto `combinable` třída není omezen na pevnou sadu operátory snížení.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá k výpočtu součet čísel nejprve 35 Fibonacciho OpenMP i Concurrency Runtime.  
  
 [!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
Using OpenMP...  
The sum of the first 35 Fibonacci numbers is 14930351.  
Using the Concurrency Runtime...  
The sum of the first 35 Fibonacci numbers is 14930351.  
```  
  
 Další informace o `combinable` třídy najdete v tématu [paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `concrt-omp-fibonacci-reduction.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **concrt modulu cl.exe /EHsc/OpenMP – omp – Fibonacciho reduction.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)

