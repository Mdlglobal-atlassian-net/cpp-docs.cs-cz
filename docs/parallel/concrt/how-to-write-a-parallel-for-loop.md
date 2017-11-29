---
title: "Postupy: smyčky Parallel_for | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 678f5cef343157378f159157906888af517dc74a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-write-a-parallelfor-loop"></a>Postupy: Programování smyčky parallel_for
Tento příklad ukazuje, jak používat [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) vypočítat součin dvou matice.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `matrix_multiply` funkci, která vypočítá součin dvou hranaté matice.  
  
 [!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `parallel_matrix_multiply` funkci, která používá `parallel_for` algoritmus vnější smyčky paralelně.  
  
 [!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]  
  
 Tento příklad parallelizes vnější smyčky, protože vykonává dostatek práce, abyste mohli využívat výhod režijní náklady pro paralelní zpracování. Pokud jste paralelní vnitřní smyčky, se nezobrazí nárůst výkonu protože malé množství práce, který provádí vnitřní smyčky neodstraní režijní náklady pro paralelní zpracování. Vytváření paralelní smyčky vnější pouze tedy nejlepší způsob, jak zvýšit výhody souběžnosti u většiny systémů.  
  
## <a name="example"></a>Příklad  
 Následující více kompletní příklad porovná výkon `matrix_multiply` funkce `parallel_matrix_multiply` funkce.  
  
 [!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]  
  
 Následující ukázkový výstup je pro počítač, který se čtyřmi procesory.  
  
```Output  
serial: 3853  
parallel: 1311  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, zkopírujte jej a vložte ji do projektu sady Visual Studio nebo ho vložte do souboru, který je pojmenován `parallel-matrix-multiply.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc paralelní matice multiply.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for – funkce](reference/concurrency-namespace-functions.md#parallel_for)

