---
title: Plánovač úloh (Concurrency Runtime)
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription [Concurrency Runtime]
- task scheduler [Concurrency Runtime], oversubscription
- schedule groups [Concurrency Runtime]
- task scheduler [Concurrency Runtime], lightweight tasks
- task scheduler [Concurrency Runtime]
- lightweight tasks [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler policies
- task scheduler [Concurrency Runtime], schedule groups
- wait function [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler instances
- scheduler instances [Concurrency Runtime]
- scheduler policies [Concurrency Runtime]
- task scheduler [Concurrency Runtime], wait function
ms.assetid: 9aba278c-e0c9-4ede-b7c6-fedf7a365d90
ms.openlocfilehash: 91ef4ed14fa1ddc25ff494f6666a50f5b39b8a54
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676704"
---
# <a name="task-scheduler-concurrency-runtime"></a>Plánovač úloh (Concurrency Runtime)

Témata v této části dokumentace popisují důležité funkce plánovače úloh modulu Runtime souběžnosti. Plánovač úloh je užitečné, pokud chcete optimalizovat výkon váš stávající kód, který používá modulu Runtime souběžnosti.

> [!IMPORTANT]
>  Plánovač úloh není k dispozici z aplikace pro univerzální platformu Windows (UPW). Další informace najdete v tématu [vytváření asynchronních operací v jazyce C++ pro aplikace pro UPW](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).
>
>  V sadě Visual Studio 2015 a novější [concurrency::task](../../parallel/concrt/reference/task-class.md) třídy a souvisejících typů v ppltasks.h používat Windows fondu vláken jako jejich plánovače. Toto téma se týká už na typy, které jsou definovány v ppltasks.h. Paralelní algoritmy, jako je například parallel_for dál používat jako výchozí plánovač Concurrency Runtime.

> [!TIP]
>  Poskytuje výchozí plánovač Concurrency Runtime, a proto není nutné vytvořit ve vaší aplikaci. Vzhledem k tomu, že Plánovač úloh umožňuje optimalizovat výkon vašich aplikací, doporučujeme začít s [knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) máte nového modulu runtime souběžnosti.

Plánovač úloh plánuje a koordinuje úkoly v době běhu. A *úloh* je jednotka práce, která provádí určitou úlohu. Úlohy lze zpravidla běží paralelně s jinými úkoly. Práce, která se provádí tak, že úkol skupiny položek, paralelní algoritmy a asynchronních agentů jsou všechny příklady úloh.

Plánovač úloh spravuje podrobnosti, které se vztahují k efektivnímu plánování úkolů na počítače, které mají víc výpočetních prostředků. Plánovač úloh také využívá nejnovější funkce základního operačního systému. Proto aplikace, které automaticky používají modulu Runtime souběžnosti škálování a zlepšit hardware, který se má rozšířit možnosti.

[Porovnání s další modely souběžného zpracování](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md) popisuje rozdíly mezi plánování mechanismy preemptive a spolupráci. Plánovač úloh používá k dosažení maximální využití prostředků zpracování plánování spolupráce a algoritmus přebírající práci spolu s plánovači preemptive operačního systému.

Concurrency Runtime poskytuje výchozí plánovače, takže není nutné spravovat infrastrukturu podrobnosti. Proto je obvykle velmi riskantní používat Plánovač úloh přímo. Podle potřeb kvality vaší aplikace, ale můžete použít Plánovač úloh poskytnout vlastní plánování zásad nebo přidružení plánovači s konkrétními úlohami. Předpokládejme například, že máte paralelní řazení rutinu, která není škálovat na více než čtyři procesory. Můžete použít *zásady plánovače* k vytvoření plánovače, která generuje více než čtyři souběžné úkoly. Spuštění rutiny řazení na tento plánovač umožňuje další aktivní plánovači používat všechny zbývající prostředky na zpracování.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Instance plánovače](../../parallel/concrt/scheduler-instances.md)|Popisuje instance plánovače a jak používat `concurrency::Scheduler` a `concurrency::CurrentScheduler` třídy k jejich správě. Instance plánovače použijte, pokud chcete přidružit explicitní zásady plánování určité druhy úloh.|
|[Zásady plánovače](../../parallel/concrt/scheduler-policies.md)|Popisuje roli zásady plánovače. Použijte zásady plánovače, pokud chcete řídit strategie, Plánovač používá při správě úloh.|
|[Skupiny plánů](../../parallel/concrt/schedule-groups.md)|Popisuje roli skupiny plánu. Použití skupin plánů Pokud vyžadujete vysoký stupeň lokality mezi úkoly, třeba když skupinu úkoly související s výhodou spuštěna ve stejném uzlu procesoru.|
|[Prosté úlohy](../../parallel/concrt/lightweight-tasks.md)|Popisuje využití jednoduché úlohy. Prosté úlohy jsou užitečné při přizpůsobení stávajícího kódu pro použití funkce plánování modulu Runtime souběžnosti.|
|[Kontexty](../../parallel/concrt/contexts.md)|Popisuje roli kontextů, `concurrency::wait` funkce a `concurrency::Context` třídy. Tuto funkci používejte, když potřebují mít kontrolu nad při kontexty blokovat, odblokovat a pozastavit nebo pokud chcete povolit překročení stanovených ve vaší aplikaci.|
|[Funkce správy paměti](../../parallel/concrt/memory-management-functions.md)|Popisuje `concurrency::Alloc` a `concurrency::Free` funkce. Tyto funkce lze vylepšit výkon paměti přidělování a uvolňování paměti souběžných způsobem.|
|[Porovnání s jinými modely souběžného zpracování](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Popisuje rozdíly mezi plánování mechanismy preemptive a spolupráci.|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Popisuje způsob použití různých paralelních vzorů, třeba paralelní algoritmy, ve svých aplikacích.|
|[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)|Popisuje způsob použití asynchronních agentů ve svých aplikacích.|
|[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)|Popisuje modulu Runtime souběžnosti, který zjednodušuje paralelní programování a obsahuje odkazy na související témata.|

