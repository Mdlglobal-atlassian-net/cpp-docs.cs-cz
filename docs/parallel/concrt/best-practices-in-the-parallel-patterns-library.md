---
title: Osvědčené postupy v knihovně Ppl | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Parallel Patterns Library, practices to avoid
- practices to avoid, Parallel Patterns Library
- best practices, Parallel Patterns Library
- Parallel Patterns Library, best practices
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28bedc703a8fa965b5380cb8c7eba840d07f7772
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396932"
---
# <a name="best-practices-in-the-parallel-patterns-library"></a>Osvědčené postupy v knihovně PPL (Parallel Patterns Library)

Tento dokument popisuje, jak nejlépe provést efektivní použití paralelních vzorů knihovny (PPL). PPL poskytuje pro obecné účely kontejnerů, objektů a algoritmy pro provádění dosáhnout jemně odstupňovaného paralelismu.

Další informace o knihovně PPL naleznete v tématu [knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

##  <a name="top"></a> Oddíly

Tento dokument obsahuje následující části:

- [Nepoužívejte paralelní provádění pro smyčky s krátkým tělem](#small-loops)

- [Vyjádřete paralelismus na nejvyšší možné úrovni](#highest)

- [Použití algoritmu parallel_invoke k řešení problémů Rozděl a Panuj](#divide-and-conquer)

- [Pomocí zrušení nebo zpracování výjimek pro přerušení paralelní smyčky](#breaking-loops)

- [Pochopení vlivu zrušení a zpracování výjimek na odstraňování objektů](#object-destruction)

- [Nepoužívejte opakovaně blokování v paralelních smyčkách](#repeated-blocking)

- [Neprovádějte blokující operace, když rušíte paralelně prováděné](#blocking)

- [Nezapisujte do sdílených dat v paralelních smyčkách](#shared-writes)

- [Pokud je to možné, vyhněte falešnému sdílení](#false-sharing)

- [Ujistěte se, že proměnné jsou platné po celou dobu trvání úlohy](#lifetime)

##  <a name="small-loops"></a> Nepoužívejte paralelní provádění pro smyčky s krátkým tělem

Paralelizace relativně malých smyček může způsobit přidružené režie plánování pro převážit nad výhodami paralelní zpracování. Zvažte následující příklad, který přidá každý pár prvky ve dvou polích.

[!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_1.cpp)]

Úlohu pro každou iteraci paralelní smyčky je příliš malá, abyste využili výhod režie pro paralelní zpracování. Můžete zvýšit výkon této smyčky, provede další práci v těle smyčky nebo sériově provádění smyčky.

[[Horní](#top)]

##  <a name="highest"></a> Vyjádřete paralelismus na nejvyšší možné úrovni

Pokud jste paralelní zpracování kódu pouze na nízké úrovni, můžete zavést forku spojení konstrukce, která nejsou adekvátní jako počtem procesorů. A *forku spojení* konstruktor je konstrukce, kde jeden úkol rozdělí svou práci na menší paralelní dílčí úkoly a čeká na dokončení těchto úkolů. Každému Dílčímu úkolu můžete rekurzivně dělení sama na dalších dílčí úkoly.

Ačkoli forku spojení modelu může být užitečné pro vyřešení různých problémů, existují situace, kde může režie synchronizace zkrátit škálovatelnost. Zvažte například následující kód sériového portu, který zpracovává data bitové kopie.

[!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_2.cpp)]

Protože každé iteraci smyčky je nezávislé, můžete velkou část práce, paralelizovat, jak je znázorněno v následujícím příkladu. V tomto příkladu [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus paralelizovat vnější smyčky.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_3.cpp)]

Následující příklad ukazuje konstrukci forku spojení voláním `ProcessImage` funkce ve smyčce. Každé volání `ProcessImage` nevrací až do dokončení každému Dílčímu úkolu.

[!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_4.cpp)]

Pokud jednotlivých iteracích paralelní smyčky buď provádí téměř žádnou práci nebo práce, kterou provádí paralelní smyčky imbalanced, to znamená, některých iterací smyčky trvat déle než jiné, plánování režie, která je potřeba často rozvětvení a spojení práce můžete převažují nad výhoda pro paralelní zpracování. Tato dodatečná režie se zvyšuje s rostoucím počtem procesorů.

Ke snížení množství plánování režijní náklady v tomto příkladu můžete paralelizovat vnější smyčky před paralelizovat vnitřní smyčky nebo použijte jiné paralelní konstrukce, jako je například zřetězení příkazů. Následující příklad upravuje `ProcessImages` funkce použité [: concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus paralelizovat vnější smyčky.

[!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_5.cpp)]

Podobný příklad, který používá kanál pro paralelní provádění pro zpracování obrázků, naleznete v tématu [návod: vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Horní](#top)]

##  <a name="divide-and-conquer"></a> Použití algoritmu parallel_invoke k řešení problémů Rozděl a Panuj

A *Rozděl a panuj* problém je forma forku spojení konstrukci, která používá rekurzi přerušení úkol na dílčí úkoly. Kromě [concurrency::task_group](reference/task-group-class.md) a [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) třídy, můžete použít také [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus řešení problémů Rozděl a panuj. `parallel_invoke` Algoritmus má stručnější syntaxi než objekty skupiny úloh a je užitečné, když máte pevný počet paralelních úloh.

Následující příklad ukazuje použití `parallel_invoke` algoritmus k provádění bitonického algoritmu řazení.

[!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_6.cpp)]

Aby se snížila režie, `parallel_invoke` algoritmus provádí poslední řadu úloh na kontext volání.

Kompletní verze tohoto příkladu naleznete v tématu [postupy: použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md). Další informace o `parallel_invoke` algoritmus, najdete v článku [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

[[Horní](#top)]

##  <a name="breaking-loops"></a> Pomocí zrušení nebo zpracování výjimek pro přerušení paralelní smyčky

PPL nabízí dva způsoby zrušení paralelně prováděných, kterou provádí paralelní algoritmus nebo skupina úloh. Jedním ze způsobů, je použití mechanismu zrušení, který je poskytován [concurrency::task_group](reference/task-group-class.md) a [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) třídy. Druhý způsob je vyvolání výjimky v těle funkce pracovních úkolů. Mechanismu zrušení je efektivnější než ve stromové struktuře paralelní práce zrušení zpracování výjimek. A *paralelně prováděných úloh stromu* je skupina úlohy související s skupin, ve kterých některé skupiny úloh obsahovat jiné skupiny úloh. Mechanismu zrušení zruší skupinu úloh a její podřízené skupiny úkolů v podobě shora dolů. Naopak zpracování výjimek funguje způsobem zdola nahoru a musíte zrušit každou podřízenou skupinu úloh nezávisle na sobě jako výjimka šíří, směrem nahoru.

Při práci přímo s objektem skupiny úloh, použijte [concurrency::task_group::cancel](reference/task-group-class.md#cancel) nebo [Concurrency::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) metody zrušit práce, která patří do této skupiny úloh . Zrušení paralelních algoritmů, například `parallel_for`, vytvořte skupinu nadřazeného úkolu a zrušení této skupině úloh. Představte si třeba následující funkci `parallel_find_any`, který vyhledá hodnotu v poli paralelně.

[!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_7.cpp)]

Protože paralelní algoritmy použijte skupiny úloh, pokud jeden z paralelní iterace zruší skupinu nadřazeného úkolu, celkový úloha se zruší. Kompletní verze tohoto příkladu naleznete v tématu [postupy: použití zrušení přerušení paralelní smyčky](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md).

I když je méně efektivní způsob, jak zrušení paralelně prováděných úloh než zrušení mechanismus zpracování výjimek, existují případech, kdy je vhodné zpracování výjimek. Například následující metodu, `for_all`, rekurzivně provádí pracovní funkce na každý uzel `tree` struktury. V tomto příkladu `_children` datový člen je [std::list](../../standard-library/list-class.md) obsahující `tree` objekty.

[!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_8.cpp)]

Volající `tree::for_all` metoda může vyvolat výjimku, pokud to nevyžaduje pracovní funkce k volání na každý prvek stromu. Následující příklad ukazuje `search_for_value` funkce, která hledá hodnotu v poskytnutých `tree` objektu. `search_for_value` Funkce používá funkci práce, která vyvolá výjimku, pokud zadaná hodnota odpovídá aktuální prvek stromu. `search_for_value` Funkce používá `try-catch` bloku zachytit výjimku a vytiskne výsledek do konzoly.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_9.cpp)]

Kompletní verze tohoto příkladu naleznete v tématu [postupy: používání zpracování výjimek, přerušení paralelní smyčky](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

Další obecné informace o zrušení a mechanismus zpracování výjimek, které jsou k dispozici v knihovně PPL naleznete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md) a [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

[[Horní](#top)]

##  <a name="object-destruction"></a> Pochopení vlivu zrušení a zpracování výjimek na odstraňování objektů

Ve stromové struktuře paralelní práce úkol, který je zrušen zabraňuje spuštění podřízených úloh. To může způsobit potíže, pokud jeden z podřízených úloh provádí operaci, která je důležitá pro vaši aplikaci, jako je například uvolnění prostředku. Zrušení úlohy navíc může způsobit výjimku šířila destruktorem objektu a způsobila nedefinované chování ve vaší aplikaci.

V následujícím příkladu `Resource` třída popisuje zdroj a `Container` třída popisuje kontejner, který obsahuje prostředky. Ve svém destruktoru `Container` třídy volání `cleanup` metodu na dvě z jeho `Resource` členy v paralelní a pak zavolá `cleanup` metodu na jeho třetí `Resource` člena.

[!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_10.h)]

I když tento model nemá žádné problémy sama o sobě, vezměte v úvahu následující kód, který spustí dvě úlohy paralelně. První úloha vytvoří `Container` objekt a druhá úloha zruší jedné úlohy. Pro ilustraci, v příkladu používá dvě [concurrency::event](../../parallel/concrt/reference/event-class.md) objekty, abyste měli jistotu, že dojde k zrušení po `Container` je vytvořen objekt a že `Container` objekt je zničen po zrušení operace probíhá.

[!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_11.cpp)]

Tento příklad vytvoří následující výstup:

```Output
Container 1: Freeing resources...Exiting program...
```

Tento příklad kódu obsahuje následující problémy, které mohou způsobit, aby chovat odlišně, než očekáváte, že:

- Zrušení nadřazeného úkolu způsobí, že podřízená úloha volání [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke), také budou zrušeny. Proto nejsou tyto dva prostředky uvolněna.

- Zrušení nadřazeného úkolu způsobí, že podřízená úloha vyvolá vnitřní výjimku. Vzhledem k tomu, `Container` destruktor nezpracovává tuto výjimku, výjimka se šíří směrem nahoru a třetí prostředek není uvolněn.

- Výjimka, která je vyvolána podřízenou úlohou šíří prostřednictvím `Container` destruktor. Vyvolání z destruktoru umístí nedefinované stavu aplikace.

Doporučujeme neprovádět důležité operace, jako je například uvolnění prostředků v úlohách, pokud může zaručit, že tyto úlohy nebudou zrušeny. Doporučujeme také, že je velmi riskantní používat funkcionalita modulu runtime, který může vyvolat v destruktoru objektu typů.

[[Horní](#top)]

##  <a name="repeated-blocking"></a> Nepoužívejte opakovaně blokování v paralelních smyčkách

Paralelní smyčka například [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) nebo [: concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) , který je ovládáno blokování operace může způsobit, že modul runtime k vytvoření několika vlákny za krátkou dobu.

Concurrency Runtime provede další práce, když se úloha dokončí nebo kooperativně blokuje nebo provede. Když jedna paralelní smyčka iterace bloky, modul runtime můžou začít vyskytovat, jiné iterace. Pokud neexistují žádné dostupné nečinných vláken, modul runtime vytvoří nové vlákno.

Pokud tělo paralelní smyčky příležitostně bloky, tento mechanismus pomáhá maximalizovat celkovou propustnost úloh. Ale při více iterací blokovat, modul runtime může vytvořit mnoho vláken pro spuštění další práce. To může vést k nedostatku paměti nebo špatné využití hardwarových prostředků.

Zvažte následující příklad, který volá [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce v každé iteraci `parallel_for` smyčky. Protože `send` kooperativně, blokuje modul runtime vytvoří nové vlákno spustit další práce pokaždé, když `send` je volána.

[!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_12.cpp)]

Doporučujeme vám, že refaktorování kódu, aby tento model. V tomto příkladu, můžete se vyhnout vytvořením další vlákna volání `send` v serial `for` smyčky.

[[Horní](#top)]

##  <a name="blocking"></a> Neprovádějte blokující operace, když rušíte paralelně prováděné

Pokud je to možné, neprovádějte blokující operace před voláním [concurrency::task_group::cancel](reference/task-group-class.md#cancel) nebo [Concurrency::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) metodu zrušení paralelně prováděných úloh.

Když úloha provede kooperativní blokující operace, modul runtime můžete provádět jinou práci, zatímco první úloha čeká na data. Modul runtime přeplánuje úkol čekání, když se odblokuje. Modul runtime obvykle přeplánuje úkoly, které byly nedávno odblokované před přeplánuje úlohy, které byly menší odblokované. Modul runtime může proto plánování zbytečné práce během blokující operace, což vede k poklesu výkonu. Když provádíte operaci blokování před zrušení paralelně prováděných úloh, proto můžete blokující operace zpoždění volání `cancel`. To způsobí, že jiné úlohy, které zbytečné práce.

Podívejte se na následující příklad, který definuje `parallel_find_answer` funkce, která vyhledá prvek zadaného pole, která splňuje zadaný predikát funkce. Při vrácení funkce predikátu `true`, vytvoří funkci paralelní práce `Answer` objektu a zruší jedné úlohy.

[!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_13.cpp)]

`new` Operátor provádí přidělení haldy, která může blokovat. Modul runtime provede další práci pouze v případě, že úloha provede spolupráce blokování volání, například volání [concurrency::critical_section::lock](reference/critical-section-class.md#lock).

Následující příklad ukazuje, jak zabránit zbytečným práce a tím zlepšit výkon. V tomto příkladu zruší skupiny úloh před přiděluje úložiště pro `Answer` objektu.

[!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_14.cpp)]

[[Horní](#top)]

##  <a name="shared-writes"></a> Nezapisujte do sdílených dat v paralelních smyčkách

Modul Concurrency Runtime obsahuje několik datových struktur, například [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), které se synchronizují souběžný přístup ke sdíleným datům. Tyto datové struktury jsou užitečné v mnoha případech, například pokud několik úloh jen zřídka vyžadují sdílený přístup k prostředku.

Podívejte se na následující příklad, který používá [: concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus a `critical_section` objektu má vypočítat počet prvočísel v [std::array](../../standard-library/array-class-stl.md) objektu. V tomto příkladu škálování, protože každý podproces musíte počkat na přístup ke sdílené proměnné `prime_sum`.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_15.cpp)]

V tomto příkladu může také vést k nižšímu výkonu, protože časté operace uzamčení efektivně serializuje smyčky. Kromě toho pokud objekt Concurrency Runtime provádí blokující operace, Plánovač může vytvořit další vlákno umožní provádět jinou práci, zatímco první vlákno čeká na data. Pokud modul runtime vytvoří několika vlákny, protože mnoho úloh, které čekají sdílených dat, můžete aplikaci nízký výkon nebo zadat stav nedostatku prostředků.

Definuje PPL [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídu, která pomáhá eliminovat tím, že poskytuje přístup ke sdíleným prostředkům v podobě bez zámku sdíleného stavu. `combinable` Třída poskytuje místní úložiště vláken, která umožňuje provádět podrobné výpočtů a pak těchto výpočtů sloučit do konečný výsledek. Můžete si představit `combinable` objektu jako redukční proměnná.

Následující příklad upravuje předchozí pomocí `combinable` místo objektu `critical_section` objekt pro výpočet součtu. V tomto příkladu se škáluje, protože každé vlákno obsahuje vlastní místní kopii součet. V tomto příkladu [concurrency::combinable::combine](reference/combinable-class.md#combine) metoda místní výpočtů sloučit konečný výsledek.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_16.cpp)]

Kompletní verze tohoto příkladu naleznete v tématu [postupy: použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md). Další informace o `combinable` najdete v tématu [paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md).

[[Horní](#top)]

##  <a name="false-sharing"></a> Pokud je to možné, vyhněte falešnému sdílení

*Falešnému sdílení* nastane, pokud více souběžných úloh, na kterých běží na procesorech samostatné zapisovat do proměnné, které jsou umístěny na stejném řádku mezipaměti. Když jeden úkol zapíše do jedné proměnné, řádek mezipaměti pro obě proměnné je neplatná. Každý procesor musí znovu načíst řádek mezipaměti pokaždé, když platnost řádek mezipaměti. Proto falešnému sdílení může způsobit snížení výkonu v aplikaci.

Následující základní příklad ukazuje dva souběžné úkoly, že každý přírůstek proměnné sdílené čítače.

[!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_17.cpp)]

Chcete-li odstranit, sdílení dat mezi dvěma úlohami, můžete upravit příkladu pro použití dvou proměnných čítače. Tento příklad zjistí hodnotu konečné čítače po dokončení úlohy. Však tento příklad ukazuje falešnému sdílení, protože proměnné `count1` a `count2` jsou pravděpodobně umístěný na stejném řádku mezipaměti.

[!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_18.cpp)]

Jedním ze způsobů, chcete-li odstranit falešnému sdílení je ověřit, že proměnné čítače jsou v mezipaměti samostatné řádky. Následující příklad zarovná proměnné `count1` a `count2` na hranice 64 bajtů.

[!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_19.cpp)]

Tento příklad předpokládá, že velikost mezipaměti je 64 nebo méně bajtů.

Doporučujeme použít [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídy při musí sdílet data mezi úkoly. `combinable` Třídy tak, že falešnému sdílení je méně pravděpodobné, že vytvoří místní proměnné vlákna. Další informace o `combinable` najdete v tématu [paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md).

[[Horní](#top)]

##  <a name="lifetime"></a> Ujistěte se, že proměnné jsou platné po celou dobu trvání úlohy

Když zadáte výraz lambda pro skupinu úloh nebo paralelního algoritmu, klauzule zachycení Určuje, zda hlavní část výrazu lambda přistupuje k proměnným v nadřazeném oboru podle hodnoty nebo odkazu. Při předání proměnných do výrazu lambda pomocí odkazu musíte zaručit, že životnost proměnné potrvá, dokud neskončí úloha.

Podívejte se na následující příklad, který definuje `object` třídy a `perform_action` funkce. `perform_action` Funkce vytvoří `object` proměnné a provede určitou akci proměnné asynchronně. Protože úloha není zaručeno, že dokončení `perform_action` funkce vrátí, program bude k chybě nebo vykazovat neurčené chování, pokud `object` proměnná je zničen při spuštění úlohy.

[!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_20.cpp)]

V závislosti na požadavcích vaší aplikace můžete použít jednu z následujících postupů k zajištění, že proměnné zůstat platný po celou dobu životnosti každé úlohy.

Následující příklad předává `object` proměnné podle hodnoty do úlohy. Proto úloha pracuje vlastní kopii proměnné.

[!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_21.cpp)]

Vzhledem k tomu, `object` proměnná je předán podle hodnoty, změny stavu, ke kterým dochází k této proměnné se nezobrazí v původní kopii.

V následujícím příkladu [Concurrency::task_group:: wait](reference/task-group-class.md#wait) metodu, abyste měli jistotu, že se úlohy dokončí před `perform_action` vrací funkce.

[!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_22.cpp)]

Protože teď neskončí úloha předtím, než funkce vrátí hodnotu, `perform_action` funkce už se chová asynchronně.

Následující příklad upravuje `perform_action` funkce využít odkaz `object` proměnné. Volající musí zaručit, že životnost `object` proměnná je platná, dokud neskončí úloha.

[!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_23.cpp)]

Ukazatel můžete také řídit dobu života objektu, který můžete předat skupina úloh nebo paralelního algoritmu.

Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](../../cpp/lambda-expressions-in-cpp.md).

[[Horní](#top)]

## <a name="see-also"></a>Viz také

[Osvědčené postupy v Concurrency Runtime](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br/>
[Postupy: Přerušení paralelní smyčky pomocí zrušení](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br/>
[Postupy: Použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
[Osvědčené postupy v knihovně asynchronních agentů](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br/>
[Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)

