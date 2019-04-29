---
title: Knihovna asynchronních agentů
ms.date: 11/19/2018
helpviewer_keywords:
- Agents Library
- Asynchronous Agents Library
ms.assetid: d2a72a31-8ba6-4220-ad7a-e403a6acaa42
ms.openlocfilehash: 39ae785b602b3928f0c32f9fc599527dab5558f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371900"
---
# <a name="asynchronous-agents-library"></a>Knihovna asynchronních agentů

Asynchronní knihovnou agentů (nebo jen *knihovna agentů*) poskytuje programovací model, který umožňuje zvýšit robustnost vývoj aplikace s podporou souběžnosti. Knihovna agentů je knihovna šablon C++, která podporuje model programování podle objektu actor a zprávy v procesu předávání pro hrubých toku dat a paralelní zpracování úloh služby. Knihovna agentů sestavení do plánování a resource management součástí modulu Runtime souběžnosti.

## <a name="programming-model"></a>Programovací model

Knihovna agentů poskytuje alternativy k sdíleného stavu tím, že umožňuje připojit izolovaných součástí prostřednictvím modelu asynchronní komunikaci, která je založená na toku dat namísto tok řízení. *Tok dat* odkazuje programování v modelu, kde výpočty jsou provedeny při všech požadovaných dat je k dispozici. *řízení toku* odkazuje na programovací model, ve kterém výpočty jsou provedeny v předurčeném pořadí.

Programovací model toku dat má vztah k konceptu *předávání zpráv*, kde nezávislé komponenty aplikace komunikovat mezi sebou odesíláním zpráv.

Knihovna agentů se skládá ze tří komponent: *asynchronních agentů*, *asynchronní bloky zpráv*, a *funkce předávání zpráv*. Agenti uchování stavu a použijte bloky zpráv a funkce předávání zpráv ke komunikaci mezi sebou a s externí komponenty. Funkce předávání zpráv umožňují agentům odesílání a příjem zpráv do a z externích součástí. Asynchronní bloky zpráv podržte zprávy a aktivovat agenty ke komunikaci v podobě synchronizované.

Následující obrázek znázorňuje způsob dva agenti blokům zpráv použití a funkce předávání zpráv pro komunikaci. Na tomto obrázku `agent1` odešle zprávu do `agent2` pomocí [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce a [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objektu. `agent2` používá [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkci na čtení zprávy. `agent2` stejnou metodu používá k odesílání zpráv do `agent1`. Přerušované šipky představují tok dat mezi agenty. Solid šipky připojení agentů k blokům zpráv, které zápisu nebo čtení z.

![Součásti knihovna agentů](../../parallel/concrt/media/agent_librarycomp.png "komponenty knihovna agentů")

Příklad kódu, který implementuje tento obrázek je uveden dále v tomto tématu.

Programovací model agenta má několik výhod oproti další souběžnosti a synchronizace mechanismy, například události. Jednou z výhod je, že pomocí předávání zpráv přenést změny stavu mezi objekty, můžete izolovat přístup ke sdíleným prostředkům a tím vylepšit škálovatelnost. Předávání zpráv výhodou je, že spojují synchronizace dat namísto propojí s objektem externí synchronizace. To zjednodušuje přenosu dat mezi součástmi a vyloučit programové chyby ve svých aplikacích.

## <a name="when-to-use-the-agents-library"></a>Když použít knihovnu agentů

Používejte knihovnu agentů v případě, že máte více operací, které musí komunikovat mezi sebou asynchronně. Bloky zpráv a funkce předávání zpráv umožňuje psát paralelní aplikace bez nutnosti synchronizace mechanismy, jako je zámky. Díky tomu se můžete soustředit na logiku aplikace.

Agent programovací model se často používá k vytvoření *datové kanály* nebo *sítě*. Datový kanál je řadu součástí, z nichž každý provádí konkrétní úlohu, která přispívá k větší cíl. Každá komponenta v kanálu toku dat provádí práci, když přijme zprávu z jiné součásti. Výsledek práce je předán do jiné komponenty v kanálu nebo sítě. Komponenty můžou využívat další podrobných souběžnosti funkce z jiných knihovnách, například, [knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

## <a name="example"></a>Příklad

V následujícím příkladu se implementuje na obrázku výše v tomto tématu.

[!code-cpp[concrt-basic-agents#1](../../parallel/concrt/codesnippet/cpp/asynchronous-agents-library_1.cpp)]

Tento příklad vytvoří následující výstup:

```Output
agent1: sending request...
agent2: received 'request'.
agent2: sending response...
agent1: received '42'.
```

Následující témata popisují funkce použité v tomto příkladu.

## <a name="related-topics"></a>Související témata

[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)<br/>
Popisuje roli asynchronních agentů v řešení větší výpočetní úlohy.

[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
Popisuje různé typy bloků zpráv, které jsou k dispozici v knihovně agentů.

[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br/>
Popisuje různé rutin předávání zpráv, které jsou k dispozici v knihovně agentů.

[Postupy: Implementace různých vzorů producent–příjemce](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br/>
Popisuje způsob implementace vzoru producent – příjemce ve vaší aplikaci.

[Postupy: Poskytování pracovních funkcí třídám call a transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br/>
Ukazuje několik způsobů, jak poskytování pracovních funkcí k [concurrency::call](../../parallel/concrt/reference/call-class.md) a [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) třídy.

[Postupy: Použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
Ukazuje způsob použití [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) třídy v datovém kanálu.

[Postupy: Výběr z dokončených úloh](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br/>
Ukazuje způsob použití [concurrency::choice](../../parallel/concrt/reference/choice-class.md) a [concurrency::join](../../parallel/concrt/reference/join-class.md) tříd vyberte první úkol k dokončení vyhledávacího algoritmu.

[Postupy: Odesílání zpráv v pravidelných intervalech](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br/>
Ukazuje způsob použití [concurrency::timer](../../parallel/concrt/reference/timer-class.md) třídu pro odesílání zpráv v pravidelných intervalech.

[Postupy: Použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)<br/>
Ukazuje, jak pomocí filtru můžete povolit blok asynchronních zpráv přijmout nebo odmítnout zprávy.

[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Popisuje způsob použití různých paralelních vzorů, jako je například paralelní algoritmy, ve svých aplikacích.

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
Popisuje modulu Runtime souběžnosti, který zjednodušuje paralelní programování a obsahuje odkazy na související témata.
