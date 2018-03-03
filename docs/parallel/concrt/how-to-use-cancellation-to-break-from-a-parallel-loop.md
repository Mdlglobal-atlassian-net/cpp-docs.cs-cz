---
title: "Postupy: paralelní smyčky pomocí zrušení přerušení | Microsoft Docs"
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
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27c6b4a216609c788978e4b857b5996587f899f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Postupy: Přerušení paralelní smyčky pomocí zrušení
Tento příklad ukazuje způsob použití zrušení k implementaci základní paralelního vyhledávacího algoritmu.  
  
## <a name="example"></a>Příklad  

 Následující příklad používá pro vyhledávání pro nějaký element v pole zrušení. `parallel_find_any` Využívá [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus a [concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) funkce pro vyhledávání pozice, který obsahuje zadanou hodnotu. Paralelní smyčky vyhledá hodnotu, zavolá [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metoda zrušit budoucí práce.  


  
 [!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]  
  

 [Concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus funguje souběžně. Proto neprovede operace v předem určené pořadí. Pokud pole obsahuje více instancí hodnoty, výsledkem mohou být některého z jeho umístění.  

  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `parallel-array-search.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc paralelní pole search.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)   
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for – funkce](reference/concurrency-namespace-functions.md#parallel_for)   
 [cancellation_token_source – třída](../../parallel/concrt/reference/cancellation-token-source-class.md)
