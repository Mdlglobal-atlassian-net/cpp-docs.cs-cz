---
title: Funkce správy paměti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0a298c7fb9e50bb17d37224b69ce342c54115d7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687293"
---
# <a name="memory-management-functions"></a>Funkce správy paměti
Tento dokument popisuje funkce správy paměti, které poskytuje Concurrency Runtime můžete přidělit a volné paměti souběžných způsobem.  
  
> [!TIP]
>  Concurrency Runtime poskytuje výchozí plánovač, a proto není nutné vytvořit ve vaší aplikaci. Protože Plánovač úloh umožňuje optimalizovat výkon aplikací, doporučujeme začínat [paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) Pokud jste nové do Concurrency Runtime.  
  
 Concurrency Runtime poskytuje dvě funkce správy paměti, která jsou optimalizována pro přidělování a uvolnění bloky paměti souběžných způsobem. [Concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) funkce přiděluje blok paměti pomocí zadané velikosti. [Concurrency::Free](reference/concurrency-namespace-functions.md#free) funkce uvolní paměť, která byla přidělena `Alloc`.  
  
> [!NOTE]
>  `Alloc` a `Free` funkce spoléhají na sobě navzájem. Použití `Free` funkce pouze k uvolnění paměti, kterou přidělit pomocí `Alloc` funkce. Také při použití `Alloc` funkce, které chcete přidělit paměť, použijte pouze `Free` funkce k uvolnění tohoto paměti.  
  
 Použití `Alloc` a `Free` funkce při přidělit a volné sadu pevné velikosti přidělení z různých vláknech nebo úlohy. Concurrency Runtime ukládá do mezipaměti paměti, která přiděluje z haldy C Runtime. Concurrency Runtime obsahuje samostatné mezipaměť pro každé spuštěné vlákno; modul runtime tedy spravuje paměti bez použití zámky nebo překážek paměti. Aplikace výhody informace z `Alloc` a `Free` funkce při mezipaměti paměti přistupuje častěji. Například vlákno, které často volá obě `Alloc` a `Free` výhody víc než vlákno, které především volá `Alloc` nebo `Free`.  
  
> [!NOTE]
>  Pokud používáte tyto funkce správy paměti, a může vaše aplikace používá velké množství paměti, aplikace zadejte podmínku nedostatku paměti dřív než můžete očekávat. Protože bloky paměti, které jsou uloženy v mezipaměti jedno vlákno nejsou k dispozici pro jiné vlákno, pokud jedno vlákno obsahuje velké množství paměti, že paměť není k dispozici.  
  
## <a name="example"></a>Příklad  
 Pro příklad, který používá `Alloc` a `Free` najdete v části funkce ke zlepšení výkonu paměti [postupy: použití Alloc a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).  
  
## <a name="see-also"></a>Viz také  
 [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Postupy: Použití funkcí Alloc a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)

