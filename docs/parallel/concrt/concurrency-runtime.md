---
title: Concurrency Runtime
ms.date: 07/20/2018
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
ms.openlocfilehash: a17b4439baaec9caacfeca08983d0255b5a145de
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141622"
---
# <a name="concurrency-runtime"></a>Concurrency Runtime

Concurrency Runtime pro C++ vám pomůže psát robustní, škálovatelné a reagující paralelní aplikace. Vyvolá úroveň abstrakce, takže nemusíte spravovat podrobnosti infrastruktury, které se vztahují k souběžnosti. Můžete ji také použít k určení zásad plánování, které splňují požadavky vašich aplikací na kvalitu služeb. Tyto prostředky vám pomůžou začít pracovat s Concurrency Runtime.

Referenční dokumentaci najdete v tématu [reference](../../parallel/concrt/reference/reference-concurrency-runtime.md).

> [!TIP]
> Concurrency Runtime spoléhá silně na funkce C++ 11 a přijímá moderní C++ styl. Pokud se chcete dozvědět víc, přečtěte si téma [Vítejte zpátky na C++ ](../../cpp/welcome-back-to-cpp-modern-cpp.md).

## <a name="choosing-concurrency-runtime-features"></a>Výběr funkcí rozhraní Concurrency Runtime

|||
|-|-|
|[Přehled](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|Učí, proč je Concurrency Runtime důležité a popisuje její klíčové funkce.|
|[Porovnání s jinými modely souběžnosti](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Ukazuje, jak Concurrency Runtime porovnává s jinými modely souběžnosti, jako je například fond vláken Windows a OpenMP, aby bylo možné použít model souběžnosti, který nejlépe vyhovuje požadavkům vaší aplikace.|
|[Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|Porovnává OpenMP s Concurrency Runtime a obsahuje příklady, jak migrovat existující kód OpenMP pro použití Concurrency Runtime.|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Vás seznámí s PPL, který poskytuje paralelní smyčky, úlohy a paralelní kontejnery.|
|[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)|Zavádí vám, jak pomocí asynchronních agentů a předávání zpráv snadno začlenit úlohy toku dat a kanálů v aplikacích.|
|[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|Vás seznámí s Plánovač úloh, které vám umožní vyladit výkon desktopových aplikací využívajících Concurrency Runtime.|

## <a name="task-parallelism-in-the-ppl"></a>Paralelismus úloh v knihovně PPL

|||
|-|-|
|[Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [Postupy: Vytvoření úlohy, která se dokončí po prodlevě](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Popisuje úlohy a skupiny úloh, které vám můžou pomáhat při psaní asynchronního kódu a rozložit paralelní práci na menší části.|
|[Návod: Implementace tříd future](../../parallel/concrt/walkthrough-implementing-futures.md)|Ukazuje, jak zkombinovat Concurrency Runtime funkce a provést něco dalšího.|
|[Návod: Odebrání práce z vlákna uživatelského rozhraní](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|Ukazuje, jak přesunout práci, která je provedena vláknem uživatelského rozhraní v aplikaci knihovny MFC, do pracovního vlákna.|
|[Osvědčené postupy v knihovně PPL (Parallel Patterns Library)](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Poskytuje tipy a osvědčené postupy pro práci s PPL.|

## <a name="data-parallelism-in-the-ppl"></a>Datový paralelismus v knihovně PPL

|||
|-|-|
|[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [Postupy: Programování smyčky parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [Postupy: Programování smyčky parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [Postupy: Paralelní provádění operací mapování a redukce](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Popisuje `parallel_for`, `parallel_for_each`, `parallel_invoke`a další paralelní algoritmy. Pomocí paralelních algoritmů můžete řešit paralelní problémy s *daty* , které zahrnují kolekce dat.|
|[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [Postupy: Použití paralelních kontejnerů ke zvýšení účinnosti](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [Postupy: Použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [Postupy: Použití objektu combinable ke slučování množin](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|Popisuje třídu `combinable` a také `concurrent_vector`, `concurrent_queue`, `concurrent_unordered_map`a dalších paralelních kontejnerů. Paralelní kontejnery a objekty používejte při vyžadování kontejnerů, které poskytují přístup s bezpečným přístupem ke svým prvkům.|
|[Osvědčené postupy v knihovně PPL (Parallel Patterns Library)](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Poskytuje tipy a osvědčené postupy pro práci s PPL.|

## <a name="canceling-tasks-and-parallel-algorithms"></a>Zrušení úloh a paralelních algoritmů

|||
|-|-|
|[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)|Popisuje roli zrušení v PPL, včetně toho, jak iniciovat žádosti o zrušení a reagovat na ně.|
|[Postupy: Přerušení paralelní smyčky pomocí zrušení](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [Postupy: Přerušení paralelní smyčky pomocí zpracování výjimek](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Ukazuje dva způsoby, jak zrušit paralelní práci s daty.|

## <a name="universal-windows-platform-apps"></a>Universal Windows Platform apps

|||
|-|-|
|[Vytváření asynchronních operací v jazyce C++ pro aplikace pro UPW](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|Popisuje některé klíčové body, které je potřeba vzít v úvahu při použití Concurrency Runtime k vytvoření asynchronních operací v aplikaci pro UWP.|
|[Návod: Připojení pomocí úloh a žádostí XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|Ukazuje, jak kombinovat PPL úkoly s rozhraními `IXMLHTTPRequest2` a `IXMLHTTPRequest2Callback` k odesílání požadavků HTTP GET a POST webové službě v aplikaci UWP.|
|[Ukázky prostředí Windows Runtime aplikací](https://code.msdn.microsoft.com/windowsapps)|Obsahuje ukázky kódu ke stažení a ukázkové aplikace pro systém Windows 8. x. C++ Ukázky používají Concurrency Runtimeé funkce, jako jsou úlohy PPL ke zpracování dat na pozadí, aby se zajistilo, že uživatelské prostředí reaguje.|

## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>Programování toku dat v knihovně asynchronních agentů

|||
|-|-|
|[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br /><br /> [Postupy: Implementace různých vzorů producent–příjemce](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [Postupy: Poskytování pracovních funkcí třídám call a transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [Postupy: Použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [Postupy: Výběr z dokončených úloh](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [Postupy: Odesílání zpráv v pravidelných intervalech](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [Postupy: Použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)|Popisuje asynchronní agenty, bloky zpráv a funkce pro předávání zpráv, které jsou stavebními bloky pro provádění operací toku dat v Concurrency Runtime.|
|[Návod: Vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [Postupy: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|Ukazuje, jak vytvořit základní aplikace založené na agentech.|
|[Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|Ukazuje, jak vytvořit síť asynchronních bloků zpráv, které provádějí zpracování imagí.|
|[Návod: Použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|Pomocí obědvajících problému s stravováním ilustruje, jak používat Concurrency Runtime k tomu, aby se zabránilo zablokování ve vaší aplikaci.|
|[Návod: Vytvoření vlastního bloku zpráv](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|Ukazuje, jak vytvořit vlastní typ bloku zprávy, který vyřadí příchozí zprávy podle priority.|
|[Osvědčené postupy v knihovně asynchronních agentů](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Poskytuje tipy a osvědčené postupy pro práci s agenty.|

## <a name="exception-handling-and-debugging"></a>Zpracování výjimek a ladění

|||
|-|-|
|[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Popisuje, jak pracovat s výjimkami v Concurrency Runtime.|
|[Paralelní diagnostické nástroje](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Naučíte se, jak vyladit aplikace a využívat Concurrency Runtime nejúčinnějším způsobem.|

## <a name="tuning-performance"></a>Optimalizace výkonu

|||
|-|-|
|[Paralelní diagnostické nástroje](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Naučíte se, jak vyladit aplikace a využívat Concurrency Runtime nejúčinnějším způsobem.|
|[Instance plánovače](../../parallel/concrt/scheduler-instances.md)<br /><br /> [Postupy: Správa instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [Zásady plánovače](../../parallel/concrt/scheduler-policies.md)<br /><br /> [Postupy: Určení specifických zásad plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [Postupy: Vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|Ukazuje, jak pracovat s úlohami spravovat instance Scheduleru a Plánovač. U aplikací klasické pracovní plochy vám zásady plánovače umožňují přidružit konkrétní pravidla ke konkrétním typům úloh. Můžete například vytvořit jednu instanci Scheduleru, která bude spouštět některé úlohy se zvýšenou prioritou, a použít výchozí Plánovač pro spouštění dalších úloh s normální prioritou vlákna.|
|[Skupiny plánů](../../parallel/concrt/schedule-groups.md)<br /><br /> [Postupy: Použití skupin plánů k ovlivnění pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|Ukazuje, jak používat skupiny Schedule k spřaženíí nebo seskupení souvisejících úkolů dohromady. Můžete například vyžadovat vysokou úroveň mezi souvisejícími úlohami, pokud tyto úlohy mají na stejném uzlu procesoru užitek.|
|[Prosté úlohy](../../parallel/concrt/lightweight-tasks.md)|Vysvětluje, jak se nenáročné úlohy hodí pro vytváření práce, která nevyžaduje vyrovnávání zatížení nebo zrušení, a jak jsou také užitečné pro přizpůsobení stávajícího kódu pro použití s Concurrency Runtime.|
|[Kontexty](../../parallel/concrt/contexts.md)<br /><br /> [Postupy: Použití třídy kontextu pro implementaci semaforu pro spolupráci](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [Postupy: Kompenzace latence vytvořením nadbytečného počtu vláken](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|Popisuje, jak řídit chování vláken, která jsou spravována Concurrency Runtime.|
|[Funkce správy paměti](../../parallel/concrt/memory-management-functions.md)<br /><br /> [Postupy: Použití funkcí Alloc a Free ke zlepšení výkonu paměti](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|Popisuje funkce správy paměti, které Concurrency Runtime poskytuje, aby vám pomohla přidělit a uvolnit paměť souběžným způsobem.|

## <a name="additional-resources"></a>Další materiály a zdroje informací

|||
|-|-|
|[Asynchronní programové vzory a tipy v Hilo (aplikace pro Windows Store C++ s využitím a XAML)](/previous-versions/windows/apps/jj160321(v=win.10))|Přečtěte si, jak jsme použili Concurrency Runtime k implementaci asynchronních operací v Hilo, prostředí Windows Runtime C++ aplikace pomocí a XAML.|
|[Paralelní programování v blogu nativního kódu](https://go.microsoft.com/fwlink/p/?linkid=183873)|Poskytuje další podrobné články o blogu o paralelním programování v Concurrency Runtime.|
|[Paralelní výpočetní prostředí C++ a fórum nativního kódu](https://go.microsoft.com/fwlink/p/?linkid=183874)|Umožňuje se zúčastnit diskuzí komunity o Concurrency Runtime.|
|[Paralelní programování](/dotnet/standard/parallel-programming/index)|Učí o paralelním programovacím modelu, který je k dispozici v .NET Framework.|

## <a name="see-also"></a>Viz také

[Referenční informace](../../parallel/concrt/reference/reference-concurrency-runtime.md)
