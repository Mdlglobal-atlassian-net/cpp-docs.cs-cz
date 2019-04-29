---
title: Zásady plánovače
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: e2acfc199e7ad9edf3965dc8ccb4103eb615a66b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408001"
---
# <a name="scheduler-policies"></a>Zásady plánovače

Tento dokument popisuje roli zásady plánovače v modulu Runtime souběžnosti. A *zásadu plánovače* řídí strategie, Plánovač používá při správě úloh. Představte si třeba aplikaci, která vyžaduje některé úlohy provádět na `THREAD_PRIORITY_NORMAL` a dalších úkolů ke zpracování na `THREAD_PRIORITY_HIGHEST`.  Můžete vytvořit dvě instance plánovače: ten, který určuje `ContextPriority` zásad `THREAD_PRIORITY_NORMAL` a další vlastnost, která určuje stejné zásady bude `THREAD_PRIORITY_HIGHEST`.

Pomocí zásady plánovače, můžete rozdělit prostředky procesoru a přiřadit pevná sada prostředků pro každý plánovač. Představte si třeba paralelního algoritmu, který není škálovat na více než čtyři procesory. Můžete vytvořit zásadu plánovače, která omezuje svých úkolů současně používat více než čtyři procesory.

> [!TIP]
>  Modul Concurrency Runtime poskytuje výchozí plánovače. Proto není nutné vytvořit ve vaší aplikaci. Vzhledem k tomu, že Plánovač úloh umožňuje optimalizovat výkon vašich aplikací, doporučujeme začít s [knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) máte nového modulu runtime souběžnosti.

Při použití [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create), [concurrency::Scheduler::Create](reference/scheduler-class.md#create), nebo [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) metodu pro vytvoření instance plánovače, zadáte [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) objekt, který obsahuje kolekci párů klíč hodnota, které určují chování plánovače. `SchedulerPolicy` Konstruktor přebírá proměnný počet argumentů. První argument je počet elementů zásad, které se chystáte zadat. Zbývající argumenty jsou páry klíč hodnota pro každý prvek zásad. Následující příklad vytvoří `SchedulerPolicy` objekt, který určuje tři prvky zásad. Modul runtime používá výchozí hodnoty pro klíče zásad, které nejsou zadané.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

[Concurrency::PolicyElementKey](reference/concurrency-namespace-enums.md#policyelementkey) výčet definuje klíče zásad, které jsou spojeny pomocí plánovače úloh. Následující tabulka popisuje klíče zásad a výchozí hodnotu, která používá modul runtime pro každý z nich.

|Klíč zásad|Popis|Výchozí hodnota|
|----------------|-----------------|-------------------|
|`SchedulerKind`|A [concurrency::SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) hodnotu, která určuje typ vlákna používat k plánování úloh.|`ThreadScheduler` (použijte normální vláken). Toto je jediná platná hodnota pro tento klíč.|
|`MaxConcurrency`|`unsigned int` Hodnota, která určuje maximální počet prostředků souběžnosti Plánovač používá.|[concurrency::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|
|`MinConcurrency`|`unsigned int` Hodnotu, která určuje minimální počet souběžnosti prostředky, které používá plánovače.|`1`|
|`TargetOversubscriptionFactor`|`unsigned int` Hodnota, která určuje, kolik vlákna přidělit do jednotlivých prostředků zpracování.|`1`|
|`LocalContextCacheSize`|`unsigned int` Hodnotu, která určuje maximální počet kontextů, které lze uložit do mezipaměti v místní fronty každý virtuální procesor.|`8`|
|`ContextStackSize`|`unsigned int` Hodnota, která určuje velikost zásobníku, v kilobajtech, můžete vyhradit pro každý kontext.|`0` (použít výchozí velikost zásobníku)|
|`ContextPriority`|`int` Hodnota, která určuje priorita vlákna každý kontext. Může to být libovolná hodnota, kterou můžete předat [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) nebo `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|

|`SchedulingProtocol`| A [concurrency::SchedulingProtocolType](reference/concurrency-namespace-enums.md#schedulingprotocoltype) hodnotu, která určuje plánování použití algoritmu. | `EnhanceScheduleGroupLocality`| | `DynamicProgressFeedback`| A [concurrency::DynamicProgressFeedbackType](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) hodnota, která určuje, jestli se má obnovit rovnováhu prostředků podle informací o průběhu na základě statistiky.<br /><br /> **Poznámka:** nenastavujte tuto zásadu na `ProgressFeedbackDisabled` vzhledem k tomu, že je vyhrazený pro použití modulem runtime. |`ProgressFeedbackEnabled`|

Každý Plánovač používá své vlastní zásady při plánování úloh. Zásady, které jsou spojeny s jeden Plánovač nemají vliv na chování jiné plánovače. Kromě toho nelze změnit zásadu plánovače, po vytvoření `Scheduler` objektu.

> [!IMPORTANT]
>  Používejte pouze zásady plánovače pro řízení atributů pro vlákna, která modul runtime vytvoří. Neměňte spřažení vláken nebo priorita vlákna, které jsou vytvořeny pomocí modulu runtime, protože to může způsobit nedefinované chování.

Modul runtime vytvoří výchozí plánovače za vás, pokud nevytvoříte explicitně jeden. Pokud chcete ve své aplikaci používají výchozí plánovač, ale chcete zadat zásady pro tento plánovač, aby používat, zavolejte [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) metoda před plánování paralelní práce. Pokud není volána `Scheduler::SetDefaultSchedulerPolicy` metody, modul runtime používá výchozí zásady hodnoty z tabulky.

Použití [concurrency::CurrentScheduler::GetPolicy](reference/currentscheduler-class.md#getpolicy) a [concurrency::Scheduler::GetPolicy](reference/scheduler-class.md#getpolicy) metody k načtení kopie zásadu plánovače. Zásada má tyto hodnoty, které jste dostali z těchto metod se může lišit od hodnoty zásad, které zadávají při vytváření plánovače.

## <a name="example"></a>Příklad

Prozkoumat příklady, které používají specifických zásad plánovače pro řízení chování plánovače, naleznete v tématu [jak: Určení specifických zásad plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) a [jak: Vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="see-also"></a>Viz také:

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Postupy: Určení specifických zásad plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[Postupy: Vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
