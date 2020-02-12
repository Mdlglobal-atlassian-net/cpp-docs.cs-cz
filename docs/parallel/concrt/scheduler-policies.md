---
title: Zásady plánovače
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: 0f90b461ecba702501c2f6919572dc828c80907f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142285"
---
# <a name="scheduler-policies"></a>Zásady plánovače

Tento dokument popisuje roli zásad plánovače v Concurrency Runtime. *Zásady plánovače* řídí strategii, kterou Plánovač používá při správě úkolů. Představte si například aplikaci, která vyžaduje, aby některé úlohy běžely na `THREAD_PRIORITY_NORMAL` a další úlohy, které se spustí při `THREAD_PRIORITY_HIGHEST`.  Můžete vytvořit dvě instance Scheduleru: jednu, která určuje `ContextPriority` zásady `THREAD_PRIORITY_NORMAL` a další, které určují stejné zásady, které mají být `THREAD_PRIORITY_HIGHEST`.

Pomocí zásad plánovače můžete rozdělit dostupné prostředky zpracování a přiřadit každému plánovači pevnou sadu prostředků. Představte si například paralelní algoritmus, který není škálování nad čtyřmi procesory. Můžete vytvořit zásadu plánovače, která omezí své úkoly na používání maximálně čtyř procesorů současně.

> [!TIP]
> Concurrency Runtime poskytuje výchozí Plánovač. Proto ho nemusíte vytvářet v aplikaci. Vzhledem k tomu, že Plánovač úloh pomáhá doladit výkon aplikací, doporučujeme začít s knihovnou [paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo s [knihovnou asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) , pokud s Concurrency Runtime začínáte.

Při použití metody [Concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create), [Concurrency:: Scheduler:: Create](reference/scheduler-class.md#create)nebo [Concurrency:: Scheduler:: SetDefaultSchedulerPolicy –](reference/scheduler-class.md#setdefaultschedulerpolicy) pro vytvoření instance Scheduleru, zadáte objekt [Concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) , který obsahuje kolekci párů klíč-hodnota, které určují chování plánovače. Konstruktor `SchedulerPolicy` přebírá proměnný počet argumentů. První argument je počet prvků zásad, které se chystáte zadat. Zbývající argumenty jsou páry klíč-hodnota pro každý prvek zásad. Následující příklad vytvoří objekt `SchedulerPolicy`, který určuje tři prvky zásad. Modul runtime používá pro klíče zásad výchozí hodnoty, které nejsou zadány.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

Výčet [Concurrency::P olicyelementkey](reference/concurrency-namespace-enums.md#policyelementkey) definuje klíče zásad, které jsou přidruženy k Plánovač úloh. Následující tabulka popisuje klíče zásad a výchozí hodnotu, kterou modul runtime používá pro každý z nich.

|Klíč zásad|Popis|Výchozí hodnota|
|----------------|-----------------|-------------------|
|`SchedulerKind`|Hodnota [Concurrency:: SchedulerType –](reference/concurrency-namespace-enums.md#schedulertype) , která určuje typ vláken, která se mají použít pro plánování úloh.|`ThreadScheduler` (použijte normální vlákna). Toto je jediná platná hodnota pro tento klíč.|
|`MaxConcurrency`|Hodnota `unsigned int`, která určuje maximální počet prostředků souběžnosti, které Plánovač používá.|[Concurrency:: MaxExecutionResources –](reference/concurrency-namespace-constants1.md#maxexecutionresources)|
|`MinConcurrency`|Hodnota `unsigned int`, která určuje minimální počet prostředků souběžnosti, které Plánovač používá.|`1`|
|`TargetOversubscriptionFactor`|Hodnota `unsigned int`, která určuje, kolik vláken se má přidělit každému prostředku zpracování.|`1`|
|`LocalContextCacheSize`|Hodnota `unsigned int`, která určuje maximální počet kontextů, které lze uložit do mezipaměti v místní frontě každého virtuálního procesoru.|`8`|
|`ContextStackSize`|Hodnota `unsigned int`, která určuje velikost zásobníku v kilobajtech, která se má vyhradit pro každý kontext.|`0` (použít výchozí velikost zásobníku)|
|`ContextPriority`|Hodnota `int`, která určuje prioritu vlákna každého kontextu. Může to být libovolná hodnota, kterou můžete předat [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) nebo `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|

|`SchedulingProtocol`| Hodnota [Concurrency:: SchedulingProtocolType –](reference/concurrency-namespace-enums.md#schedulingprotocoltype) , která určuje používaný algoritmus plánování. |`EnhanceScheduleGroupLocality`| |`DynamicProgressFeedback`| Hodnota [Concurrency::D ynamicprogressfeedbacktype](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) , která určuje, jestli se mají prostředky v závislosti na informacích o průběhu založené na statistice vyrovnávat.<br /><br /> **Poznámka:** Nenastavte tuto zásadu na `ProgressFeedbackDisabled`, protože je vyhrazena pro použití modulem runtime. |`ProgressFeedbackEnabled`|

Každý Plánovač používá při plánování úloh vlastní zásady. Zásady, které jsou přidruženy k jednomu plánovači, neovlivní chování žádného jiného plánovače. Po vytvoření `Scheduler`ho objektu navíc nemůžete změnit zásady plánovače.

> [!IMPORTANT]
> Pro řízení atributů vláken, která modul runtime vytvoří, použijte pouze zásady Scheduleru. Neměňte spřažení vlákna ani prioritu vláken, která jsou vytvořena modulem runtime, protože to může způsobit nedefinované chování.

Modul runtime vytvoří výchozí Plánovač, pokud jste ho nevytvořili explicitně. Chcete-li použít výchozí Plánovač v aplikaci, ale chcete zadat zásadu, kterou má Plánovač používat, zavolejte metodu [Concurrency:: Scheduler:: SetDefaultSchedulerPolicy –](reference/scheduler-class.md#setdefaultschedulerpolicy) před naplánováním paralelní práce. Pokud nevoláte metodu `Scheduler::SetDefaultSchedulerPolicy`, modul runtime použije výchozí hodnoty zásad z tabulky.

Pomocí metod [Concurrency:: CurrentScheduler:: GetPolicy](reference/currentscheduler-class.md#getpolicy) a [Concurrency:: Scheduler:: GetPolicy](reference/scheduler-class.md#getpolicy) načtěte kopii zásady plánovače. Hodnoty zásad, které z těchto metod obdržíte, se můžou lišit od hodnot zásad, které určíte při vytváření plánovače.

## <a name="example"></a>Příklad

Příklady použití konkrétních zásad plánovače k řízení chování plánovače najdete v tématu [Postupy: určení konkrétních zásad plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) a [Postup: vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="see-also"></a>Viz také

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Postupy: Určení specifických zásad plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[Postupy: Vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
