---
title: Concurrency Runtime
ms.date: 07/20/2018
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
ms.openlocfilehash: fa64e2536fd1697e839f1b4921a290e1b7a30a35
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449694"
---
# <a name="concurrency-runtime"></a>Concurrency Runtime

Concurrency Runtime pro jazyk C++ umožňuje zápis robustní, škálovatelné a interaktivní paralelních aplikací. Vyvolá úroveň abstrakce, takže není nutné spravovat infrastrukturu podrobnosti, které se týkají souběžnosti. Také ho můžete použít k určení plánování zásad, které splňují kvalitu služby potřebám vašich aplikací. Pomocí těchto prostředků vám pomohou v začátcích práce s modulem Runtime souběžnost.

Odkaz na dokumentaci najdete v tématu [odkaz](../../parallel/concrt/reference/reference-concurrency-runtime.md).

> [!TIP]
>  Modulu Runtime souběžnosti spoléhá na funkce C ++ 11 a přijímá více moderní styl C++. Další informace najdete v článku [Vítejte zpět do C++](../../cpp/welcome-back-to-cpp-modern-cpp.md).

## <a name="choosing-concurrency-runtime-features"></a>Výběr funkcí rozhraní Concurrency Runtime

|||
|-|-|
|[Přehled](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|Naučíte se, proč je důležité modulu Runtime souběžnosti a popisuje hlavní funkce.|
|[Porovnání s jinými modely souběžného zpracování](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Ukazuje, jak porovná Concurrency Runtime s jinými modely souběžného zpracování, jako Windows vlákna fondu a OpenMP, aby mohli používat model souběžnosti, který nejlépe vyhovuje požadavkům vaší aplikace na.|
|[Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|Porovná OpenMP do Concurrency Runtime a poskytuje příklady o tom, jak migrovat existující kód OpenMP na využití modulu Concurrency Runtime.|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Vás seznámí s PPL, který poskytuje paralelních smyček, úkoly a paralelní kontejnery.|
|[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)|Ukazuje, jak použít asynchronní agenti a usnadnění snadno začlenit toku dat a paralelní zpracování úloh ve svých aplikacích.|
|[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|Vás seznámí s Plánovačem úloh, která umožňuje optimalizovat výkon vaší aplikace klasické pracovní plochy, která používá modulu Runtime souběžnosti.|

## <a name="task-parallelism-in-the-ppl"></a>Paralelismus úloh v knihovně PPL

|||
|-|-|
|[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [Postupy: Vytvoření úlohy, která se dokončí po prodlevě](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Popisuje úkoly a skupiny úloh, které vám mohou pomoci při zápisu asynchronního kódu a rozložit paralelní práci na menší části.|
|[Návod: Implementace tříd future](../../parallel/concrt/walkthrough-implementing-futures.md)|Ukazuje, jak kombinovat funkce modulu Runtime souběžnosti udělat něco víc.|
|[Návod: Odebrání práce z vlákna uživatelského rozhraní](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|Ukazuje, jak přesunout práce, která se provádí pomocí vlákna uživatelského rozhraní v aplikaci knihovny MFC k pracovní podproces.|
|[Osvědčené postupy v knihovně PPL (Parallel Patterns Library)](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Poskytuje tipy a osvědčené postupy pro práci s PPL.|

## <a name="data-parallelism-in-the-ppl"></a>Datový paralelismus v knihovně PPL

|||
|-|-|
|[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [Postupy: Programování smyčky parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [Postupy: Programování smyčky parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [Postupy: Paralelní provádění operací mapování a redukce](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Popisuje `parallel_for`, `parallel_for_each`, `parallel_invoke`a jiné paralelní algoritmy. Použít paralelní algoritmy k řešení *data paralelní* problémy, které zahrnují kolekce dat.|
|[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [Postupy: Použití paralelních kontejnerů ke zvýšení účinnosti](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [Postupy: Použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [Postupy: Použití objektu combinable ke slučování množin](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|Popisuje `combinable` třídy, jakož i `concurrent_vector`, `concurrent_queue`, `concurrent_unordered_map`a jiné paralelní kontejnery. Používejte paralelní kontejnery a objekty, když budete vyžadovat, kontejnery, které poskytují bezpečné pro vlákna přístup k jejich prvky.|
|[Osvědčené postupy v knihovně PPL (Parallel Patterns Library)](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Poskytuje tipy a osvědčené postupy pro práci s PPL.|

## <a name="canceling-tasks-and-parallel-algorithms"></a>Zrušení úloh a paralelních algoritmů

|||
|-|-|
|[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)|Popisuje zrušení v knihovně PPL, včetně postupu zahájení a reagovat na žádosti o zrušení.|
|[Postupy: Přerušení paralelní smyčky pomocí zrušení](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [Postupy: Přerušení paralelní smyčky pomocí zpracování výjimek](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Ukazuje dva způsoby, jak zrušit pracovní paralelizovaného pro data.|

## <a name="universal-windows-platform-apps"></a>Universal Windows Platform apps

|||
|-|-|
|[Vytváření asynchronních operací v jazyce C++ pro aplikace pro UPW](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|Popisuje některé z klíčových bodů do vzít v úvahu při vytváření asynchronních operací v aplikaci pro UPW pomocí modulu Runtime souběžnosti.|
|[Návod: Připojení pomocí úloh a žádostí XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|Ukazuje, jak kombinovat úlohy PPL s `IXMLHTTPRequest2` a `IXMLHTTPRequest2Callback` rozhraní k odesílání požadavků HTTP GET a POST na webovou službu v aplikaci UWP.|
|[Ukázky aplikací pro Windows Runtime](https://code.msdn.microsoft.com/windowsapps)|Obsahuje ukázky ke stažení kódu a ukázkové aplikace pro Windows 8.x. Ukázky v C++ pomocí funkce modulu Runtime souběžnosti, jako je úlohy PPL pro zpracování dat na pozadí zajistit uživatelského rozhraní reagovat.|

## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>Programování toku dat v knihovně asynchronních agentů

|||
|-|-|
|[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br /><br /> [Postupy: Implementace různých vzorů producent–příjemce](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [Postupy: Poskytování pracovních funkcí třídám call a transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [Postupy: Použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [Postupy: Výběr z dokončených úloh](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [Postupy: Odesílání zpráv v pravidelných intervalech](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [Postupy: Použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)|Popisuje funkce předávání zpráv, které jsou stavební bloky pro provádění operací toku dat v modulu Runtime souběžnosti, asynchronních agentů a bloky zpráv.|
|[Návod: Vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [Návod: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|Ukazuje, jak vytvořit základní aplikace založené na agentovi.|
|[Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|Ukazuje, jak vytvořit síť asynchronní bloky zpráv, které provádějí zpracování obrázků.|
|[Návod: Použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|Problém obědvajících filozofů využívá pro ilustraci použití Concurrency Runtime zabránit zablokování ve vaší aplikaci.|
|[Návod: Vytvoření vlastního bloku zpráv](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|Ukazuje, jak vytvořit typ bloku vlastní zprávy, který řadí příchozích zprávy podle priority.|
|[Osvědčené postupy v knihovně asynchronních agentů](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Poskytuje tipy a osvědčené postupy pro práci s agenty.|

## <a name="exception-handling-and-debugging"></a>Zpracování výjimek a ladění

|||
|-|-|
|[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Popisuje, jak pracovat s výjimek v Concurrency Runtime.|
|[Paralelní diagnostické nástroje](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Vás naučí, jak optimalizovat vaše aplikace a ujistěte se, co nejefektivněji využít modul Concurrency Runtime.|

## <a name="tuning-performance"></a>Optimalizace výkonu

|||
|-|-|
|[Paralelní diagnostické nástroje](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Vás naučí, jak optimalizovat vaše aplikace a ujistěte se, co nejefektivněji využít modul Concurrency Runtime.|
|[Instance plánovače](../../parallel/concrt/scheduler-instances.md)<br /><br /> [Postupy: Správa instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [Zásady plánovače](../../parallel/concrt/scheduler-policies.md)<br /><br /> [Postupy: Určení specifických zásad plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [Postupy: Vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|Ukazuje, jak pracovat s Správa instance plánovače a zásady plánovače. Zásady plánovače pro aplikace klasické pracovní plochy, umožní spojit konkrétní pravidla s konkrétními typy úloh. Můžete například vytvořit jednu instanci plánovač spustit některé úlohy důležitostí vlákna se zvýšenými oprávněními a používají výchozí plánovač spustit další úkoly vláknu s normální prioritou.|
|[Skupiny plánů](../../parallel/concrt/schedule-groups.md)<br /><br /> [Postupy: Použití skupin plánů k ovlivnění pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|Popisuje způsob použití skupin plánů k spřažení nebo seskupit, související úlohy. Například může vyžadovat vysoký stupeň lokality mezi související úlohy při těchto úloh využívat spuštěna ve stejném uzlu procesoru.|
|[Prosté úlohy](../../parallel/concrt/lightweight-tasks.md)|Vysvětluje, jak jednoduché úlohy jsou užitečné při vytváření práce, které se nevyžaduje Vyrovnávání zatížení nebo zrušení a jak jsou také užitečné pro přizpůsobení stávajícího kódu pro použití s komponentou Concurrency Runtime.|
|[Kontexty](../../parallel/concrt/contexts.md)<br /><br /> [Postupy: Použití třídy kontextu pro implementaci semaforu pro spolupráci](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [Postupy: Kompenzace latence vytvořením nadbytečného počtu vláken](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|Popisuje, jak řídit chování, které spravuje nástroj modulu Runtime souběžnosti vláken.|
|[Funkce správy paměti](../../parallel/concrt/memory-management-functions.md)<br /><br /> [Postupy: Použití funkcí Alloc a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|Popisuje funkce správy paměti, které poskytuje modulu Runtime souběžnosti můžete přidělují a uvolňují paměť souběžných způsobem.|

## <a name="additional-resources"></a>Další prostředky

|||
|-|-|
|[Vzory asynchronního programování a v Hilo (aplikace Windows Store pomocí jazyka C++ a XAML)](https://msdn.microsoft.com/library/windows/apps/jj160321.aspx)|Zjistěte, jak můžete využít modul Concurrency Runtime pro implementaci asynchronních operací v Hilo, aplikace v jazyce prostředí Windows Runtime pomocí jazyka C++ a XAML.|
|[Paralelní programování v blogu nativního kódu](https://go.microsoft.com/fwlink/p/?linkid=183873)|Poskytuje podrobný blogový další články o paralelním programování v modulu Runtime souběžnosti.|
|[V C++ a nativním kódu fórum pro paralelní výpočty](https://go.microsoft.com/fwlink/p/?linkid=183874)|Umožňuje účast v komunitě diskuse o modulu Runtime souběžnosti.|
|[Paralelní programování](/dotnet/standard/parallel-programming/index)|Naučíte se o paralelní programovací model, který je k dispozici v rozhraní .NET Framework.|

## <a name="see-also"></a>Viz také:

[Referenční informace](../../parallel/concrt/reference/reference-concurrency-runtime.md)
