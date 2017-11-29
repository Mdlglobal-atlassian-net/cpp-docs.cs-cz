---
title: Concurrency Runtime | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
caps.latest.revision: "40"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 87521d761a0355903408debe3ff27d26a006368b
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="concurrency-runtime"></a>Concurrency Runtime
Concurrency Runtime jazyka C++ vám pomůže zápisu robustní, škálovatelnou a reaguje paralelní aplikace. Vyvolá úrovni abstrakce tak, že nemáte ke správě infrastruktury podrobnosti, které se vztahují k souběžnosti. Můžete ji použít i k určení plánování zásady, které splňují kvality služby požadavky aplikací. Pomocí těchto prostředků usnadňují začátek práce s komponentou Concurrency Runtime.  
  
 Referenční dokumentaci najdete v tématu [odkaz](../../parallel/concrt/reference/reference-concurrency-runtime.md).  
  
> [!TIP]
>  Concurrency Runtime založena na C ++ 11 funkce a přijímá více moderní styl C++. Další informace, přečtěte si [Vítá zpět do C++](../../cpp/welcome-back-to-cpp-modern-cpp.md).  
  
## <a name="choosing-concurrency-runtime-features"></a>Výběr funkcí rozhraní Concurrency Runtime  
  
|||  
|-|-|  
|[Přehled](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|Učí, proč je důležité Concurrency Runtime a popisuje hlavní funkce.|  
|[Porovnání s jinými modely souběžného zpracování](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Ukazuje, jak se porovnává Concurrency Runtime s jinými modely souběžného zpracování, jako je Windows vláken fondu a OpenMP, tak, aby můžete souběžnosti model, který nejlépe vyhovuje požadavkům vaší aplikace.|  
|[Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|Porovná OpenMP do Concurrency Runtime a obsahuje příklady o tom, jak migrovat existující kód OpenMP na využití modulu Concurrency Runtime.|  
|[Knihovna Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Vás seznámí s PPL, která poskytuje paralelní smyčky, úlohy a paralelní kontejnery.|  
|[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)|Ukazuje, jak používat asynchronních agentů a usnadnění snadno začlenit toku dat a paralelní zpracování úloh ve svých aplikacích.|  
|[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|Vás seznámí s Plánovač úloh, které umožňuje optimalizovat výkon desktopových aplikací, který používá Concurrency Runtime.|  
  
## <a name="task-parallelism-in-the-ppl"></a>Paralelismus úloh v knihovně PPL  
  
|||  
|-|-|  
|[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [Postupy: použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [Postupy: použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [Postupy: vytvoření úlohy, která je dokončena po prodlevě](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Popisuje úlohy a úkolů skupin, které mohou pomoci při psaní kódu asynchronní a rozložit paralelní práce na menší části.|  
|[Návod: Implementace tříd Future](../../parallel/concrt/walkthrough-implementing-futures.md)|Ukazuje, jak kombinovat Concurrency Runtime funkce více něco udělat.|  
|[Návod: Odstranění práce z vlákna uživatelského rozhraní](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|Ukazuje, jak přesunout pracovní, které se provádí pomocí vlákna uživatelského rozhraní v aplikaci MFC na pracovní vlákno.|  
|[Osvědčené postupy v Parallel Patterns Library](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Poskytuje tipy a osvědčené postupy pro práci s knihovně PPL.|  
  
## <a name="data-parallelism-in-the-ppl"></a>Datový paralelismus v knihovně PPL  
  
|||  
|-|-|  
|[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [Postupy: smyčky Parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [Postupy: smyčky Parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [Postup: provedení mapy a snížit operace paralelně](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Popisuje `parallel_for`, `parallel_for_each`, `parallel_invoke`a jiné paralelní algoritmy. Paralelní algoritmy použijte k řešení *data paralelní* problémy, které zahrnují kolekce dat.|  
|[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [Postupy: použití paralelních kontejnerů ke zvýšení efektivity](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [Postupy: použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [Postupy: použití objektu combinable ke slučování množin](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|Popisuje `combinable` třída, a také `concurrent_vector`, `concurrent_queue`, `concurrent_unordered_map`a další paralelních kontejnerů. Pokud požadujete kontejnery, které poskytují přístup z více vláken bezpečný přístup k jejich elementů pomocí paralelní kontejnery a objekty.|  
|[Osvědčené postupy v Parallel Patterns Library](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Poskytuje tipy a osvědčené postupy pro práci s knihovně PPL.|  
  
## <a name="canceling-tasks-and-parallel-algorithms"></a>Zrušení úloh a paralelních algoritmů  
  
|||  
|-|-|  
|[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)|Popisuje roli zrušení v knihovně PPL, včetně toho, jak k zahájení a reagovat na požadavky zrušení.|  
|[Postupy: použití zrušení přerušení paralelní smyčky](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [Postupy: použití výjimek zpracování přerušení paralelní smyčky](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Ukazuje dva způsoby, jak zrušit data paralelní práce.|  
  
## <a name="windows-store-apps"></a>Aplikace pro Windows Store  
  
|||  
|-|-|  
|[Vytváření asynchronních operací v jazyce C++ pro aplikace Windows Store](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|Popisuje některé z klíčových bodů mít na paměti, když použijete k vytvoření asynchronních operací v Concurrency Runtime [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace.|  
|[Návod: Připojení pomocí úloh a žádostí XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|Ukazuje, jak kombinovat PPL úlohy s `IXMLHTTPRequest2` a `IXMLHTTPRequest2Callback` rozhraní k odesílání požadavků HTTP GET a POST na webovou službu v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace.|  
|[Ukázky aplikace Windows Store](http://code.msdn.microsoft.com/windowsapps)|Obsahuje ukázky kódu ke stažení a ukázkové aplikace pro [!INCLUDE[win8](../../build/reference/includes/win8_md.md)]. Ukázky C++ pomocí Concurrency Runtime funkce jako je například PPL úloh zpracování dat na pozadí udržovat uživatelského reaguje.|  
  
## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>Programování toku dat v knihovně asynchronních agentů  
  
|||  
|-|-|  
|[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [Funkce usnadnění](../../parallel/concrt/message-passing-functions.md)<br /><br /> [Postupy: implementace různých vzorů typu výrobce spotřebitel](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [Postupy: poskytování pracovních funkcí třídám call a transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [Postupy: použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [Postupy: výběr z dokončených úloh](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [Postupy: odesílání zpráv v pravidelných intervalech](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [Postupy: použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)|Popisuje asynchronních agentů, bloky zpráv a funkce předávání zpráv, které představují stavební kameny pro provádění operací toku dat v Concurrency Runtime.|  
|[Návod: Vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [Návod: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|Ukazuje, jak vytvořit základní aplikace pro agenta.|  
|[Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|Ukazuje, jak vytvořit síť asynchronní bloky zpráv provádějící zpracování obrázků.|  
|[Návod: Použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|Používá nabízet filosofů problém pro ilustraci použití Concurrency Runtime k zabránění vzájemnému zablokování v aplikaci.|  
|[Návod: Vytvoření vlastního bloku zpráv](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|Ukazuje, jak vytvořit vlastní zprávu typ bloku, jemuž příchozí zprávy pořadí podle priority.|  
|[Osvědčené postupy v knihovně asynchronních agentů](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Obsahuje tipy a osvědčené postupy pro práci s agenty.|  
  
## <a name="exception-handling-and-debugging"></a>Zpracování výjimek a ladění  
  
|||  
|-|-|  
|[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Popisuje, jak pracovat s výjimek v Concurrency Runtime.|  
|[Paralelní diagnostické nástroje](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Se naučíte, jak optimalizovat aplikace a ujistěte se, co nejúčinnější použití Concurrency Runtime.|  
  
## <a name="tuning-performance"></a>Optimalizace výkonu  
  
|||  
|-|-|  
|[Paralelní diagnostické nástroje](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Se naučíte, jak optimalizovat aplikace a ujistěte se, co nejúčinnější použití Concurrency Runtime.|  
|[Instance plánovače](../../parallel/concrt/scheduler-instances.md)<br /><br /> [Postupy: Správa Instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [Zásady plánovače](../../parallel/concrt/scheduler-policies.md)<br /><br /> [Postupy: určení specifických zásad plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [Postupy: vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|Ukazuje, jak pracovat s Správa instance plánovače a zásady plánovače. Zásady plánovače aplikací klasické pracovní plochy, umožní přidružit konkrétní pravidla pro konkrétní typy úloh. Můžete například vytvořit jednu instanci plánovače spouštět některé úlohy prioritou zvýšenými vláken a používat výchozí plánovač při spouštění dalších úloh na normální vlákno prioritu.|  
|[Skupiny plánů](../../parallel/concrt/schedule-groups.md)<br /><br /> [Postupy: použití skupin plánů k ovlivnění pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|Demonstruje způsob použití skupin plánů k spřažení nebo seskupit, související úlohy. Pokud tyto úlohy těžit z provádění na stejném procesoru uzlu, například může vyžadovat vysoký stupeň polohu mezi související úlohy.|  
|[Prosté úlohy](../../parallel/concrt/lightweight-tasks.md)|Vysvětluje, jak prosté úlohy jsou užitečné pro vytváření pracovních, který nevyžaduje Vyrovnávání zatížení nebo zrušení a jak jsou užitečné také pro přizpůsobení stávajícího kódu pro použití s komponentou Concurrency Runtime.|  
|[Kontexty](../../parallel/concrt/contexts.md)<br /><br /> [Postupy: použití třídy kontextu pro implementaci semaforu pro spolupráci](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [Postupy: kompenzace latence vytvořením nadbytečného](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|Popisuje, jak můžete řídit chování vláken, které jsou spravovány nástrojem Concurrency Runtime.|  
|[Funkce správy paměti](../../parallel/concrt/memory-management-functions.md)<br /><br /> [Postupy: použití funkcí Alloc a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|Popisuje funkce správy paměti, které poskytuje Concurrency Runtime můžete přidělit a volné paměti souběžných způsobem.|  
  
## <a name="additional-resources"></a>Další prostředky  
  
|||  
|-|-|  
|[Asynchronní programování vzory a tipy v Hilo (aplikace pro Windows Store pomocí C++ a XAML)](http://msdn.microsoft.com/library/windows/apps/jj160321.aspx)|Zjistěte, jak jsme použili Concurrency Runtime k implementaci asynchronních operací v Hilo, [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikaci pomocí C++ a XAML.|  
|[Ukázky kódu pro Concurrency Runtime a Parallel Library vzor v sadě Visual Studio 2010](http://go.microsoft.com/fwlink/linkid=183875)|Poskytuje ukázkové aplikace a nástroje, které ukazují Concurrency Runtime.|  
|[Paralelní programování v blogu nativního kódu](http://go.microsoft.com/fwlink/linkid=183873)|Poskytuje podrobný blog další články o paralelní programování v Concurrency Runtime.|  
|[Paralelní výpočetní ve fóru C++ a nativní kód](http://go.microsoft.com/fwlink/linkid=183874)|Umožňuje komunity diskuze o Concurrency Runtime.|  
|[Paralelní programování](/dotnet/standard/parallel-programming/index)|Se dozvíte, jaké paralelní programovací model, který je k dispozici v [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)].|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace](../../parallel/concrt/reference/reference-concurrency-runtime.md)

