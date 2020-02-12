---
title: Funkce správy paměti
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: aa1951211283ddf7e4823a920d5cdf19bd6d977d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141842"
---
# <a name="memory-management-functions"></a>Funkce správy paměti

Tento dokument popisuje funkce správy paměti, které poskytuje Concurrency Runtime k tomu, aby vám pomohla přidělit a uvolnit paměť souběžným způsobem.

> [!TIP]
> Concurrency Runtime poskytuje výchozí Plánovač, a proto není nutné ho v aplikaci vytvořit. Vzhledem k tomu, že Plánovač úloh pomáhá doladit výkon aplikací, doporučujeme začít s knihovnou [paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo s [knihovnou asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) , pokud s Concurrency Runtime začínáte.

Concurrency Runtime poskytuje dvě funkce správy paměti, které jsou optimalizované pro přidělování a uvolňování bloků paměti souběžným způsobem. Funkce [Concurrency:: alokace](reference/concurrency-namespace-functions.md#alloc) přiděluje blok paměti pomocí zadané velikosti. Funkce [Concurrency:: Free](reference/concurrency-namespace-functions.md#free) uvolní paměť, která byla přidělena `Alloc`.

> [!NOTE]
> Funkce `Alloc` a `Free` spoléhají na sebe navzájem. Použijte funkci `Free` jenom k uvolnění paměti, kterou přidělíte pomocí funkce `Alloc`. Kromě toho, když použijete funkci `Alloc` k přidělení paměti, použijte k uvolnění této paměti pouze funkci `Free`.

Použijte funkce `Alloc` a `Free`, když přidělíte a uvolníte pevnou sadu velikostí alokace z různých vláken nebo úloh. Concurrency Runtime ukládá do mezipaměti paměť, kterou přiděluje z haldy modulu runtime jazyka C. Concurrency Runtime obsahuje samostatnou paměťovou mezipaměť pro každé běžící vlákno; modul runtime proto spravuje paměť bez použití zámků nebo bariéry paměti. Pokud je mezipaměť paměti k dispozici častěji, aplikace využívá `Alloc` a `Free` funkce. Například vlákno, které často volá jak `Alloc`, tak `Free` výhody více než vlákno, které primárně volá `Alloc` nebo `Free`.

> [!NOTE]
> Když použijete tyto funkce správy paměti a vaše aplikace využívá spoustu paměti, může aplikace zadat stav s nízkou pamětí dřív, než očekáváte. Vzhledem k tomu, že bloky paměti, které jsou uloženy v mezipaměti v jednom vlákně, nejsou k dispozici pro žádné jiné vlákno, pokud jedno vlákno uchovává hodně paměti, není tato paměť k dispozici.

## <a name="example"></a>Příklad

Příklad, který používá funkce `Alloc` a `Free` ke zlepšení výkonu paměti, naleznete v tématu [How to: Use a Free pro zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

## <a name="see-also"></a>Viz také

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Postupy: Použití funkcí Alloc a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)
