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
ms.openlocfilehash: e4a2e66afe656f9588ed3040218d1f70b3684190
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143313"
---
# <a name="task-scheduler-concurrency-runtime"></a>Plánovač úloh (Concurrency Runtime)

Témata v této části dokumentace popisují důležité funkce Concurrency Runtime Plánovač úloh. Plánovač úloh je užitečné, pokud chcete vyladit výkon stávajícího kódu, který používá Concurrency Runtime.

> [!IMPORTANT]
> Plánovač úloh není k dispozici z aplikace Univerzální platforma Windows (UWP). Další informace najdete v tématu [Vytváření asynchronních operací C++ v pro aplikace pro UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).
>
> V aplikaci Visual Studio 2015 nebo novější má třída [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) a související typy v ppltasks. h použít jako svůj Plánovač fondu Windows. Toto téma již neplatí pro typy, které jsou definovány v ppltasks. h. Paralelní algoritmy jako parallel_for nadále používají Concurrency Runtime jako výchozí Plánovač.

> [!TIP]
> Concurrency Runtime poskytuje výchozí Plánovač, a proto není nutné ho v aplikaci vytvořit. Vzhledem k tomu, že Plánovač úloh pomáhá doladit výkon aplikací, doporučujeme začít s knihovnou [paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo s [knihovnou asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) , pokud s Concurrency Runtime začínáte.

Plánovač úloh plány a koordinuje úlohy za běhu. *Úkol* je jednotka práce, která provádí určitou úlohu. Úkol obvykle může běžet paralelně s jinými úkoly. Práce, která je prováděna položkami skupiny úloh, paralelní algoritmy a asynchronní agenti, jsou všechny příklady úloh.

Plánovač úloh spravuje podrobnosti, které se týkají efektivního plánování úloh v počítačích, které mají více výpočetních prostředků. Plánovač úloh také využívá nejnovější funkce základního operačního systému. Proto aplikace, které používají Concurrency Runtime automaticky škálují a zlepšují na hardwaru, který má rozšířené možnosti.

[Porovnání s jinými modely souběžnosti](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md) popisuje rozdíly mezi mechanismy pro nečinnost a postupy plánování pro spolupráci. Plánovač úloh využívá plánování spolupráce a algoritmus pro pracovní krádeže spolu s nedostupným plánovačem operačního systému za účelem dosažení maximálního využití prostředků zpracování.

Concurrency Runtime poskytuje výchozí Plánovač, takže nemusíte spravovat podrobnosti o infrastruktuře. Proto obvykle nepoužíváte Plánovač úloh přímo. Pro splnění potřeb kvality aplikace ale můžete použít Plánovač úloh k poskytnutí vlastních zásad plánování nebo k přidružení plánovačů ke konkrétním úlohám. Předpokládejme například, že máte paralelní řadicí rutinu, která neškáluje více než čtyři procesory. Pomocí *zásad Scheduleru* můžete vytvořit Plánovač, který negeneruje víc než čtyři souběžné úlohy. Spuštění řadicí rutiny v tomto plánovači umožňuje jiným aktivním plánovačům používat libovolné zbývající prostředky zpracování.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Instance plánovače](../../parallel/concrt/scheduler-instances.md)|Popisuje instance Scheduleru a způsob použití tříd `concurrency::Scheduler` a `concurrency::CurrentScheduler` ke správě těchto instancí. Instance Scheduleru použijte, když chcete přidružit explicitní zásady plánování ke konkrétním typům úloh.|
|[Zásady plánovače](../../parallel/concrt/scheduler-policies.md)|Popisuje roli zásad plánovače. Zásady plánovače použijte, když chcete řídit strategii, kterou Plánovač používá při správě úkolů.|
|[Skupiny plánů](../../parallel/concrt/schedule-groups.md)|Popisuje roli skupin plánování. Skupiny plánů se používají, když budete potřebovat vysoký stupeň lokálních operací mezi úkoly, například když se skupina souvisejících úloh vykonává ve stejném uzlu procesoru.|
|[Prosté úlohy](../../parallel/concrt/lightweight-tasks.md)|Popisuje roli zjednodušených úloh. Jednoduché úlohy jsou užitečné, když upravujete existující kód pro použití funkce plánování Concurrency Runtime.|
|[Kontexty](../../parallel/concrt/contexts.md)|Popisuje roli kontextů, funkci `concurrency::wait` a třídu `concurrency::Context`. Tuto funkci použijte, pokud potřebujete kontrolu nad tím, kdy kontexty zablokují, odblokuje a vrátí nebo když chcete v aplikaci povolit převzetí služeb při selhání.|
|[Funkce správy paměti](../../parallel/concrt/memory-management-functions.md)|Popisuje funkce `concurrency::Alloc` a `concurrency::Free`. Tyto funkce mohou zlepšit výkon paměti tím, že přidělíte a uvolníte paměť souběžným způsobem.|
|[Porovnání s jinými modely souběžnosti](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Popisuje rozdíly mezi mechanismy pro přerušení a spolupráci.|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Popisuje, jak používat různé paralelní vzory, například paralelní algoritmy, ve vašich aplikacích.|
|[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)|Popisuje způsob použití asynchronních agentů ve vašich aplikacích.|
|[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)|Popisuje Concurrency Runtime, který zjednodušuje paralelní programování a obsahuje odkazy na Příbuzná témata.|
