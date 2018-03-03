---
title: "Zásady plánovače | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c2e669a429bebbfde19f54200610819d0849d8f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="scheduler-policies"></a>Zásady plánovače
Tento dokument popisuje roli zásady plánovače v Concurrency Runtime. A *zásad plánovače* prvky strategie používající Plánovač při správě úloh. Představte si třeba aplikaci, která vyžaduje některé úlohy provést v `THREAD_PRIORITY_NORMAL` a další úlohy provést v `THREAD_PRIORITY_HIGHEST`.  Můžete vytvořit dvě instance plánovače: ten, který určuje `ContextPriority` k zásad `THREAD_PRIORITY_NORMAL` a druhý, který určuje stejné zásady jako `THREAD_PRIORITY_HIGHEST`.  
  
 Pomocí zásady plánovače může rozdělení prostředky procesoru a přiřadit každý scheduler pevnou sadu prostředků. Představte si třeba paralelní algoritmus, který není škálování nad rámec čtyřmi procesory. Můžete vytvořit scheduler zásadu, která omezuje její úkoly souběžně používat více než čtyři procesory.  
  
> [!TIP]
>  Concurrency Runtime poskytuje výchozí plánovače. Proto není nutné vytvořit ve vaší aplikaci. Protože Plánovač úloh umožňuje optimalizovat výkon aplikací, doporučujeme začínat [paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) Pokud jste nové do Concurrency Runtime.  
  
 Při použití [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create), [concurrency::Scheduler::Create](reference/scheduler-class.md#create), nebo [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) metodu pro vytvoření instance plánovače, zadáte [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) objekt, který obsahuje kolekci páry klíč hodnota, která určují chování plánovače. `SchedulerPolicy` Konstruktor přijímá proměnný počet argumentů. První argument je počet elementů zásad, které se chystáte zadat. Zbývající argumenty jsou páry klíč hodnota pro každý prvek zásad. Následující příklad vytvoří `SchedulerPolicy` objekt, který určuje tři elementů zásad. Modul runtime používá výchozí hodnoty pro klíče zásady, které nejsou zadány.  

  
 [!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]  
  

 [Concurrency::PolicyElementKey](reference/concurrency-namespace-enums.md#policyelementkey) výčet definuje zásady klíčů, které jsou spojeny pomocí plánovače úloh. Následující tabulka popisuje zásady klíče a výchozí hodnotu, která používá modul runtime pro každý z nich.  
  
|Klíč zásad|Popis|Výchozí hodnota|  
|----------------|-----------------|-------------------|  
|`SchedulerKind`|A [concurrency::SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) hodnotu, která určuje typ vláken používaných při plánování úloh.|`ThreadScheduler`(pomocí normální vláken). Toto je jediná platná hodnota pro tento klíč.|  
|`MaxConcurrency`|`unsigned int` Hodnotu, která určuje maximální počet souběžnosti prostředky, které používá plánovače.|[Concurrency::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|  
|`MinConcurrency`|`unsigned int` Hodnotu, která určuje minimální počet souběžnosti prostředky, které používá plánovače.|`1`|  
|`TargetOversubscriptionFactor`|`unsigned int` Hodnotu, která určuje, kolik vláken přidělit všem prostředkům zpracování.|`1`|  
|`LocalContextCacheSize`|`unsigned int` Hodnotu, která určuje maximální počet kontextů, které mohou být uloženy v mezipaměti v místní frontu každý virtuální procesor.|`8`|  
|`ContextStackSize`|`unsigned int` Hodnotu, která určuje velikost zásobníku, v kilobajtech, můžete vyhradit pro každý kontext.|`0`(použít výchozí velikost zásobníku)|  
|`ContextPriority`|`int` Hodnotu, která určuje prioritu vlákno každý kontext. To může být libovolná hodnota, která můžete předat do [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) nebo `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|  

|`SchedulingProtocol`| A [concurrency::SchedulingProtocolType](reference/concurrency-namespace-enums.md#schedulingprotocoltype) hodnotu, která určuje plánování algoritmus použitý. |`EnhanceScheduleGroupLocality`|  
|`DynamicProgressFeedback`| A [concurrency::DynamicProgressFeedbackType](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) hodnotu, která určuje, zda chcete znovu vyvážit prostředky podle informace o průběhu na základě statistik.<br /><br /> **Poznámka:** nenastavujte tuto zásadu na `ProgressFeedbackDisabled` vzhledem k tomu, že je vyhrazený pro použití modulem runtime. |`ProgressFeedbackEnabled`|  

  
 Každý Plánovač používá své vlastní zásady při naplánuje úkoly. Zásady, které jsou spojeny s plánovačem jeden nemají vliv na chování jiné plánovače. Kromě toho nelze změnit zásady plánovače po vytvoření `Scheduler` objektu.  
  
> [!IMPORTANT]
>  K řízení atributy vláken, která vytvoří modulu runtime použijte pouze zásady plánovače. Neměňte spřažení podprocesu nebo prioritě vláken, které jsou vytvořené pomocí modulu runtime, vzhledem k tomu, které může způsobit nedefinované chování.  
  
 Modul runtime vytvoří výchozí plánovače za vás, pokud nevytvoříte explicitně jeden. Pokud chcete použít výchozí plánovače v aplikaci, ale chcete zadat zásady pro tento plánovač chcete použít, volání [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) metoda před naplánování paralelní práce. Pokud není volána `Scheduler::SetDefaultSchedulerPolicy` metoda, používá modul runtime výchozí zásady hodnoty z tabulky.  
  
 Použití [concurrency::CurrentScheduler::GetPolicy](reference/currentscheduler-class.md#getpolicy) a [concurrency::Scheduler::GetPolicy](reference/scheduler-class.md#getpolicy) metody k načtení kopie zásad plánovače. Hodnoty zásad, které jste dostali z těchto metod se může lišit od hodnoty zásad, které určíte při vytvoření plánovače.  
  
## <a name="example"></a>Příklad  
 Zkontrolujte příklady, která k ovládání chování Plánovač používá specifické zásady plánovače, najdete v tématu [postup: Zadejte specifické zásady plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) a [postupy: vytváření agentů této použít specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).  
  
## <a name="see-also"></a>Viz také  
 [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Postupy: určení specifických zásad plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)   
 [Postupy: Vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

