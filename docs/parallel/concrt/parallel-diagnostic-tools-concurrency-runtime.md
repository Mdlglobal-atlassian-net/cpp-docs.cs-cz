---
title: Paralelní diagnostické nástroje (Concurrency Runtime)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
ms.openlocfilehash: 34b2421dfc53deeb35dcc659a8d555983e583737
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510495"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>Paralelní diagnostické nástroje (Concurrency Runtime)

Visual Studio poskytuje rozsáhlou podporu pro ladění a profilování aplikací s více vlákny.

## <a name="debugging"></a>Ladění

Ladicí program sady Visual Studio obsahuje okno paralelní zásobníky, okno **Paralelní úlohy** a okno **paralelního sledování** . Další informace najdete v tématu [Návod: Ladění paralelní aplikace](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) a [postup: Použijte okno](/visualstudio/debugger/how-to-use-the-parallel-watch-window)paralelní kukátko.

## <a name="profiling"></a>Profilace

Nástroje pro profilaci poskytují tři zobrazení dat, která zobrazují grafické, tabelární a číselné informace o tom, jak vícevláknová aplikace spolupracuje s sebou a s jinými programy. Zobrazení vám umožní rychle identifikovat oblasti, které se týkají, a přejít z bodů v grafickém zobrazení do zásobníků volání, volat weby a zdrojový kód. Další informace najdete v tématu [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).

## <a name="event-tracing"></a>Trasování událostí

Concurrency Runtime používá [trasování událostí pro Windows](/windows/win32/ETW/event-tracing-portal) (ETW) k upozorňování nástrojů instrumentace, jako jsou profilery, když dojde k různým událostem. Tyto události zahrnují při aktivaci nebo deaktivaci plánovače, když kontext začne, končí, blokuje, odblokuje nebo vrátí a když se spustí nebo ukončí paralelní algoritmus.

Tato funkce využívá nástroje jako [Vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer) . Proto není obvykle nutné pracovat s těmito událostmi přímo. Tyto události jsou však užitečné, pokud vyvíjíte vlastní Profiler nebo používáte nástroje pro trasování událostí, jako je [Xperf](https://go.microsoft.com/fwlink/p/?linkid=160628).

Concurrency Runtime tyto události vyvolává pouze v případě, že je povoleno trasování. Voláním funkce [Concurrency:: EnableTracing –](reference/concurrency-namespace-functions.md#enabletracing) Povolte trasování událostí a funkci [Concurrency::D isabletracing](reference/concurrency-namespace-functions.md#disabletracing) pro zakázání trasování.

Následující tabulka popisuje události, které modul runtime vyvolává, když je povoleno trasování událostí:

|Událost|Popis|Value|
|-----------|-----------------|-----------|
|[concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|Identifikátor zprostředkovatele ETW pro Concurrency Runtime.|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|
|[concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)|Označí události, které jsou v souvislosti s kontexty.|`5727a00f-50be-4519-8256-f7699871fecb`|
|[concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|Označí úvodní a výstupní volání do arallel_for algoritmu [Concurrency::p](reference/concurrency-namespace-functions.md#parallel_for) .|`31c8da6b-6165-4042-8b92-949e315f4d84`|
|[concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Označí úvodní a výstupní volání do arallel_for_each algoritmu [Concurrency::p](reference/concurrency-namespace-functions.md#parallel_for_each) .|`5cb7d785-9d66-465d-bae1-4611061b5434`|
|[concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Označí úvodní a výstupní volání do arallel_invoke algoritmu [Concurrency::p](reference/concurrency-namespace-functions.md#parallel_invoke) .|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|
|[concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)|Označí události, které souvisí s [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|
|[concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|Označí události, které souvisí s virtuálními procesory.|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|

Concurrency Runtime definuje, ale v současné době nevyvolává následující události. Modul runtime rezervuje tyto události pro budoucí použití:

- [concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)

- [concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)

- [concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)

- [concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)

- [concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)

Výčet [Concurrency:: ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype) určuje možné operace, které událost sleduje. Například na začátku `parallel_for` algoritmu modul runtime `PPLParallelForEventGuid` vyvolá událost a poskytne `CONCRT_EVENT_START` jako operaci. Předtím, `parallel_for` než se algoritmus vrátí, modul runtime znovu `PPLParallelForEventGuid` vyvolá událost a `CONCRT_EVENT_END` poskytne jako operaci.

Následující příklad ukazuje, jak povolit trasování pro volání `parallel_for`. Modul runtime nesleduje první volání do `parallel_for` , protože trasování není povoleno. Volání, které `EnableTracing` umožňuje modulu runtime sledovat druhé `parallel_for`volání.

[!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]

Modul runtime sleduje počet, kolikrát zavoláte `EnableTracing` a. `DisableTracing` Proto pokud voláte `EnableTracing` víckrát, je nutné volat `DisableTracing` stejný počet, aby bylo trasování zakázáno.

## <a name="see-also"></a>Viz také:

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)
