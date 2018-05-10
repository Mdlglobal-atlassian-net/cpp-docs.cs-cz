---
title: 'Postupy: paralelní smyčky pomocí zrušení přerušení | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1b5153c225c3bb3a67be4265cf8303da2121c2b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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
