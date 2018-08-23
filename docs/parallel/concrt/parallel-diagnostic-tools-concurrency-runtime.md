---
title: Paralelní diagnostické nástroje (Concurrency Runtime) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb41f9630e22d9067743b106aed49ea9c51ee4ae
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464816"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>Paralelní diagnostické nástroje (Concurrency Runtime)
Visual Studio poskytuje rozsáhlou podporu pro ladění a profilování vícevláknových aplikacích.  
  
## <a name="debugging"></a>Ladění  
 Zahrnuje ladicího programu sady Visual Studio **paralelní zásobníky** okně **paralelní úlohy** okna, a **paralelního sledování** okno. Další informace najdete v tématu [návod: ladění paralelní aplikace](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) a [postupy: použití okna paralelního sledování](/visualstudio/debugger/how-to-use-the-parallel-watch-window).  
  
## <a name="profiling"></a>Profilace  
 Nástroje pro profilaci poskytují tři zobrazení dat, které zobrazují grafické, tabulky a číselné informace o interakci vícevláknové aplikace se sebou samým a s jinými programy. Zobrazení vám umožní rychle identifikovat oblastí zájmu a přejít z bodů na grafické zobrazení volání zásobníků, volání lokality a zdrojového kódu. Další informace najdete v tématu [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="event-tracing"></a>Trasování událostí  
 Modul Concurrency Runtime používá [události trasování pro Windows](http://msdn.microsoft.com/library/windows/desktop/bb968803) (ETW) upozornění instrumentace nástrojů, jako je profilovací programy, pokud dojde k různým událostem. Tyto události patří když Plánovač se aktivuje nebo deaktivuje, pokud kontext začíná, skončí, blokuje, odblokuje nebo provede, a když paralelního algoritmu začíná nebo končí.  
  
 Nástroje, jako [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer) využívat tuto funkci; proto obvykle nemusíte pracovat přímo s těmito událostmi. Tyto události jsou však užitečné, když vyvíjíte vlastní profileru nebo při použití nástroje Sledování událostí, jako [Xperf](http://go.microsoft.com/fwlink/p/?linkid=160628).  
  
 Modul Concurrency Runtime vyvolává tyto události pouze v případě, že je povoleno trasování. Volání [concurrency::EnableTracing](reference/concurrency-namespace-functions.md#enabletracing) funkci umožňující trasování událostí a [concurrency::DisableTracing](reference/concurrency-namespace-functions.md#disabletracing) funkce pro vypnutí trasování.  
  
 Následující tabulka popisuje události, které modul runtime vyvolá, když je povoleno trasování událostí:  
  
|Událost|Popis|Hodnota|  
|-----------|-----------------|-----------|  

|[Concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)| Identifikátor poskytovatele trasování událostí pro Windows pro Concurrency Runtime. |`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|  
|[Concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)| Označí události, které souvisejí s kontexty. |`5727a00f-50be-4519-8256-f7699871fecb`|  
|[Concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)| Označí vstupu a výstupu na volání [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus. |`31c8da6b-6165-4042-8b92-949e315f4d84`|  
|[Concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)| Označí vstupu a výstupu na volání [: concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus. |`5cb7d785-9d66-465d-bae1-4611061b5434`|  
|[Concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)| Označí vstupu a výstupu na volání [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus. |`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|  
|[Concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)| Označí události, které se vztahují k [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md). |`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|  
|[Concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)| Označí události, které se týkají virtuálních procesorů. |`2f27805f-1676-4ecc-96fa-7eb09d44302f`|  
  
 Definuje modulu Runtime souběžnosti, ale nevyvolá aktuálně, následující události. Modul runtime rezervuje pro budoucí použití těchto událostí:  
  
-   [Concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)  
  
-   [Concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)  
  
-   [Concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)  
  
-   [Concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)  
  
-   [Concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)  
  
 [Concurrency::ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype) určuje výčet možných operacích, které sleduje události. Například na vstupu `parallel_for` algoritmus, modul runtime vyvolá `PPLParallelForEventGuid` událostí a poskytuje `CONCRT_EVENT_START` jako operaci. Před `parallel_for` vrátí algoritmus, modul runtime znovu vyvolá `PPLParallelForEventGuid` událostí a poskytuje `CONCRT_EVENT_END` jako operaci.  
  
 Následující příklad ukazuje, jak povolit trasování pro volání `parallel_for`. Modul runtime netrasuje první volání `parallel_for` protože to není povoleno trasování. Volání `EnableTracing` trasování druhé volání modulu runtime umožňuje `parallel_for`.  
  
 [!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]  
  
 Modul runtime sleduje počet případů, kdy zavoláte `EnableTracing` a `DisableTracing`. Proto pokud zavoláte `EnableTracing` více než jednou, je nutné volat `DisableTracing` stejný počet, kolikrát aby bylo možné zakázat trasování.  
  
## <a name="see-also"></a>Viz také  
 [Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)

