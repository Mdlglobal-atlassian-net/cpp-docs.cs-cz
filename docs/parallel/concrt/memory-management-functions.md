---
title: Funkce správy paměti
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: 9a7810267c3eaa11ad7592774440365620e7e8f4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276933"
---
# <a name="memory-management-functions"></a>Funkce správy paměti

Tento dokument popisuje funkce správy paměti, které poskytuje modulu Runtime souběžnosti můžete přidělují a uvolňují paměť souběžných způsobem.

> [!TIP]
>  Poskytuje výchozí plánovač Concurrency Runtime, a proto není nutné vytvořit ve vaší aplikaci. Vzhledem k tomu, že Plánovač úloh umožňuje optimalizovat výkon vašich aplikací, doporučujeme začít s [knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) máte nového modulu runtime souběžnosti.

Modul Concurrency Runtime poskytuje dvě funkce správy paměti, které jsou optimalizovány pro přidělení a uvolnění bloky paměti souběžných způsobem. [Concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) funkce přidělí blok paměti s použitím zadané velikosti. [Concurrency::Free](reference/concurrency-namespace-functions.md#free) uvolnění paměti, která byla přidělena pomocí funkce `Alloc`.

> [!NOTE]
>  `Alloc` a `Free` funkce závisí na sebe navzájem. Použití `Free` funkce pouze k uvolnění paměti, kterou přidělíte pomocí `Alloc` funkce. Navíc při použití `Alloc` funkce přidělení paměti, použijte pouze `Free` funkce, tato paměť uvolnit.

Použití `Alloc` a `Free` funkce při přidělují a uvolňují pevná sada přidělení velikosti z různých vláken nebo úloh. Modul Concurrency Runtime přiděluje z modulu C Runtime haldy paměti ukládá do mezipaměti. Modul Concurrency Runtime obsahuje samostatný mezipaměti pro každé vlákno spuštěné; Proto se modul runtime spravuje paměť bez použití zámků nebo překážky paměti. Aplikace výhody naplno `Alloc` a `Free` funkce při mezipaměti se využívají častěji. Například vlákna, která často volá obě `Alloc` a `Free` výhod více než vlákno, které se primárně volá `Alloc` nebo `Free`.

> [!NOTE]
>  Pokud používáte tyto funkce správy paměti, a vaše aplikace používá velké množství paměti, aplikace může zadat podmínku nedostatku paměti dříve, než na kolik máte očekávat. Protože paměťových bloků, které jsou uložené v mezipaměti jedním vláknem nejsou k dispozici pro ostatní vlákna, pokud jedno vlákno obsahuje velké množství paměti, že paměť není k dispozici.

## <a name="example"></a>Příklad

Příklad, který se používá `Alloc` a `Free` funkce ke zlepšení výkonu paměti naleznete v tématu [jak: Použití funkcí Alloc a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

## <a name="see-also"></a>Viz také:

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Postupy: Použití funkcí Alloc a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)
