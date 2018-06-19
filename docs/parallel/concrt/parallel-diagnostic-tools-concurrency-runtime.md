---
title: Paralelní diagnostické nástroje (Concurrency Runtime) | Microsoft Docs
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
ms.openlocfilehash: 1cd3ce4c86332719e299c11fee3ffbee8b41c14f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693104"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>Paralelní diagnostické nástroje (Concurrency Runtime)
[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] poskytuje rozsáhlou podporu pro ladění a profilování vícevláknových aplikací.  
  
## <a name="debugging"></a>Ladění  
 Zahrnuje ladicího programu sady Visual Studio **paralelní zásobníky** okně **paralelních úloh** okně a **paralelního sledování** okno. Další informace najdete v tématu [návod: ladění paralelní aplikace](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) a [postupy: použití okna paralelního sledování](/visualstudio/debugger/how-to-use-the-parallel-watch-window).  
  
## <a name="profiling"></a>Profilace  
 Nástroje pro profilaci poskytují tři zobrazení dat, které zobrazují grafické, tabulkový a číselné informace o spolupráci vícevláknové aplikace s sám a další programy. Zobrazení vám umožní rychle identifikovat oblastí zájmu a chcete přejít z bodů na grafické zobrazí volat zásobníky, volejte lokality a zdrojového kódu. Další informace najdete v tématu [vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="event-tracing"></a>Trasování událostí  
 Používá Concurrency Runtime [trasování událostí pro Windows](http://msdn.microsoft.com/library/windows/desktop/bb968803) (ETW) oznámit instrumentace nástroje, jako je například profilery, když dojde k různé události. Tyto události zahrnují při plánovače je aktivace nebo deaktivace, pokud kontext začne, končí, blokuje, odblokuje nebo vypočítá a při paralelní algoritmus začíná nebo končí.  
  
 Nástroje, jako [vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer) tuto funkci využívat; proto obvykle nemusíte tyto události pracovat přímo. Tyto události jsou však užitečné, když vyvíjíte vlastní profileru nebo při použití nástroje trasování událostí, jako [Xperf](http://go.microsoft.com/fwlink/p/?linkid=160628).  
  
 Concurrency Runtime vyvolá tyto události jenom v případě, že je povolené trasování. Volání [concurrency::EnableTracing](reference/concurrency-namespace-functions.md#enabletracing) funkce povolit trasování událostí a [concurrency::DisableTracing](reference/concurrency-namespace-functions.md#disabletracing) funkce pro vypnutí trasování.  
  
 Následující tabulka popisuje události, které modul runtime vyvolá při zapnutém trasování událostí:  
  
|Událost|Popis|Hodnota|  
|-----------|-----------------|-----------|  

|[Concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)| Identifikátor zprostředkovatele trasování událostí pro Windows pro Concurrency Runtime. |`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|  
|[Concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)| Označí události, které souvisí s kontexty. |`5727a00f-50be-4519-8256-f7699871fecb`|  
|[Concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)| Označí vstupu a konec volání [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus. |`31c8da6b-6165-4042-8b92-949e315f4d84`|  
|[Concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)| Označí vstupu a konec volání [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus. |`5cb7d785-9d66-465d-bae1-4611061b5434`|  
|[Concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)| Označí vstupu a konec volání [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus. |`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|  
|[Concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)| Označí události, které se vztahují k [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md). |`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|  
|[Concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)| Označí události, které souvisí s virtuálními procesory. |`2f27805f-1676-4ecc-96fa-7eb09d44302f`|  
  
 Concurrency Runtime definuje, ale nevyvolá aktuálně, následující události. Modul runtime rezerv tyto události pro budoucí použití:  
  
-   [Concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)  
  
-   [Concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)  
  
-   [Concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)  
  
-   [Concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)  
  
-   [Concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)  
  
 [Concurrency::ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype) výčet Určuje možné operace, které sleduje události. Například u vstupu `parallel_for` algoritmus, modul runtime vyvolává `PPLParallelForEventGuid` událostí a poskytuje `CONCRT_EVENT_START` jako operaci. Před `parallel_for` vrátí algoritmus, modul runtime znovu vyvolává `PPLParallelForEventGuid` událostí a poskytuje `CONCRT_EVENT_END` jako operaci.  
  
 Následující příklad ukazuje, jak povolit trasování pro volání `parallel_for`. Modul runtime netrasuje první volání `parallel_for` protože trasování není povolené. Volání `EnableTracing` umožňuje modulu runtime trasování druhé volání `parallel_for`.  
  
 [!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]  
  
 Modul runtime sleduje počet pokusů, které zavoláte `EnableTracing` a `DisableTracing`. Proto když zavoláte `EnableTracing` vícekrát, musí volat `DisableTracing` stejný počet pokusů, aby bylo možné zakázat trasování.  
  
## <a name="see-also"></a>Viz také  
 [Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)

