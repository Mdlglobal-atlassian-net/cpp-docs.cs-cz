---
title: "Osvědčené postupy v knihovně Parallel Patterns | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Parallel Patterns Library, practices to avoid
- practices to avoid, Parallel Patterns Library
- best practices, Parallel Patterns Library
- Parallel Patterns Library, best practices
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 40629b25ebcc954ac19389fbc0abb3aef6e9374a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="best-practices-in-the-parallel-patterns-library"></a>Osvědčené postupy v knihovně PPL (Parallel Patterns Library)
Tento dokument popisuje, jak nejlépe efektivní využití paralelní vzory knihovny (PPL). Knihovně PPL poskytuje pro obecné účely kontejnerů, objektů a algoritmy pro provádění podrobného paralelismu.  
  
 Další informace o knihovně PPL najdete v tématu [paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md).  
  
##  <a name="top"></a>Oddíly  
 Tento dokument obsahuje následující části:  
  
- [Není paralelní malých smyček](#small-loops)  
  
- [Express paralelismus na nejvyšší možné úrovni](#highest)  
  
- [Použití algoritmu parallel_invoke k řešení problémů dělení a dobytí](#divide-and-conquer)  
  
- [Použijte zrušení nebo zpracování přerušení paralelní smyčky výjimek](#breaking-loops)  
  
- [Pochopit vliv zrušení a zpracování výjimek na odstranění objektu](#object-destruction)  
  
- [Opakovaně nebrání v paralelní smyčky](#repeated-blocking)  
  
- [Neprovádějte blokování operace při zrušení paralelní práce](#blocking)  
  
- [Nezapisovat sdílených dat v paralelní smyčky](#shared-writes)  
  
- [Pokud je to možné, vyhněte se False sdílení](#false-sharing)  
  
- [Ujistěte se, že jsou platné po celou dobu úlohy](#lifetime)  
  
##  <a name="small-loops"></a>Není paralelní malých smyček  
 Paralelizace relativně malých smyček může způsobit přidružené plánování režie převažují nad přínosy paralelní zpracování. Prohlédněte si následující příklad přidá každý pár elementů v dvěma poli.  
  
 [!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_1.cpp)]  
  
 Úlohy pro každou iteraci paralelní smyčky je příliš malá, abyste mohli využívat výhod režijní náklady pro paralelní zpracování. Provedením další práci do těla smyčky nebo sériově provádění smyčky, můžete zlepšit výkon této smyčky.  
  
 [[Horní](#top)]  
  
##  <a name="highest"></a>Express paralelismus na nejvyšší možné úrovni  
 Pokud jste paralelní kód pouze na nižší úrovni, je připojení k rozvětvení konstruktor, který se nedá použít jako počet procesorů zvyšuje zavést. A *připojení k rozvětvení* konstrukce je konstrukce, kde jeden úkol rozdělí svou práci na menší paralelní dílčí úkoly a čeká na tyto dílčí úkoly k dokončení. Každý dílčí úlohy můžete rekurzivně dělení sám sebe na další dílčí úkoly.  
  
 Přestože se připojení k rozvětvení modelu může být užitečná pro řešení různé problémy, se situací, kdy režii synchronizace může snížit škálovatelnost. Zvažte například následující kód sériového portu, který zpracovává data bitové kopie.  
  
 [!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_2.cpp)]  
  
 Jelikož je každé iteraci smyčky nezávislé, můžete většinu práce, paralelní, jak je znázorněno v následujícím příkladu. Tento příklad používá [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus učinit paralelní vnější smyčky.  

  
 [!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_3.cpp)]  
  
 Následující příklad ilustruje připojení k rozvětvení konstrukce voláním `ProcessImage` funkce ve smyčce. Každé volání `ProcessImage` nevrátí, dokud nebude dokončeno každý dílčí úlohy.  
  
 [!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_4.cpp)]  
  
 Pokud každé iteraci paralelní smyčky buď provede téměř žádné práce nebo práce, které se provádí pomocí paralelní smyčky imbalanced, to znamená, některé iterace smyčky trvat déle než jiné, plánování režie, je potřeba často rozvětvovat a připojení k pracovní můžete náročnější pro paralelní zpracování. Tato dodatečná režie zvyšuje počet procesorů zvyšuje.  
  
 Ke snížení objemu plánování režijní náklady v tomto příkladu, můžete paralelní smyčky vnější před paralelní smyčky vnitřní nebo použijte jiný paralelní konstrukce, jako je například zřetězení příkazů. Následující příklad změní `ProcessImages` funkce použité [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus učinit paralelní vnější smyčky.  

  
 [!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_5.cpp)]  
  
 Podobně jako příklad, který používá kanál provést paralelní zpracování obrázků, najdete v části [návod: vytváření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 [[Horní](#top)]  
  
##  <a name="divide-and-conquer"></a>Použití algoritmu parallel_invoke k řešení problémů dělení a dobytí  

 A *dělení a dobytí* problém je forma konstrukce rozvětvení spojení, která používá rekurze pro přerušení úlohu na dílčí úkoly. Kromě [concurrency::task_group](reference/task-group-class.md) a [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) třídy, můžete použít také [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus řešte problémy dělení a dobytí. `parallel_invoke` Algoritmus má více stručného syntaxi než objekty skupiny úloh a je užitečné, když máte pevný počet paralelních úloh.  
  
 Následující příklad ukazuje použití `parallel_invoke` algoritmus implementovat bitonic řazení algoritmus.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_6.cpp)]  
  
 Ke snížení režie, `parallel_invoke` algoritmus provádí volání kontextu poslední řadu úloh.  
  
 Dokončení verzi v tomto příkladu, naleznete v části [postupy: použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md). Další informace o `parallel_invoke` algoritmus, najdete v části [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
 [[Horní](#top)]  
  
##  <a name="breaking-loops"></a>Použijte zrušení nebo zpracování přerušení paralelní smyčky výjimek  
 Knihovně PPL nabízí dva způsoby, jak zrušit paralelní práce, které se provádí pomocí paralelní algoritmus nebo skupina úloh. Jedním ze způsobů je používat zrušení mechanismy, které poskytuje [concurrency::task_group](reference/task-group-class.md) a [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) třídy. Druhý způsob je vyvolána výjimka v těle funkce pracovních úkolů. Tento mechanismus zrušení je efektivnější než zpracování na zrušení strom paralelní práce výjimek. A *paralelní práce stromu* je skupina úlohy související s skupin, ve kterých některé skupiny úloh obsahovat jiné skupiny úloh. Tento mechanismus zrušení zruší skupinu úloh a její podřízené skupiny úloh způsobem shora dolů. Zpracovávání výjimek v jazyce naopak funguje způsobem zdola nahoru a musí zrušit každou podřízenou skupinu úloh nezávisle jako výjimka šíří směrem nahoru.  
  

 Když začnete pracovat přímo s objektem skupiny úloh, použijte [concurrency::task_group::cancel](reference/task-group-class.md#cancel) nebo [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) metody zrušit práce, která patří do této skupiny úloh . Zrušení paralelních algoritmů, například `parallel_for`, vytvořit nadřazenou skupinu úloh a zrušení této skupiny úloh. Zvažte například následující funkce `parallel_find_any`, která hledá hodnotu do pole paralelně.  


  
 [!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_7.cpp)]  
  
 Protože paralelní algoritmy používat skupiny úloh, pokud jeden z paralelní iterací zruší nadřazenou skupinu úloh, celkový úloha je zrušena. Dokončení verzi v tomto příkladu, naleznete v části [postupy: použití zrušení přerušení paralelní smyčky](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md).  
  
 Přestože výjimek je méně efektivní způsob, jak zrušit paralelní práce než mechanismus zrušení, jsou případech, kdy je vhodné výjimek. Například následující metodu `for_all`, rekurzivně provádí pracovní funkce na každém uzlu `tree` struktury. V tomto příkladu `_children` – datový člen je [std::list](../../standard-library/list-class.md) obsahující `tree` objekty.  
  
 [!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_8.cpp)]  
  
 Volající `tree::for_all` metoda může vyvolat výjimku, pokud není nutné pracovní funkce k volání na každý prvek stromu. Následující příklad ukazuje `search_for_value` funkci, která hledá hodnotu v zadaných `tree` objektu. `search_for_value` Funkce používá pracovní funkci, která vyvolá výjimku, pokud zadaná hodnota odpovídá aktuálního elementu stromu. `search_for_value` Využívá `try-catch` blok k Tisk do konzoly a zachycení výjimky.  
  
 [!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_9.cpp)]  
  
 Dokončení verzi v tomto příkladu, naleznete v části [postupy: použití zpracování výjimek přerušení paralelní smyčky](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).  
  
 Další obecné informace o zrušení a mechanismus zpracování výjimek, které jsou k dispozici v knihovně PPL najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md) a [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 [[Horní](#top)]  
  
##  <a name="object-destruction"></a>Pochopit vliv zrušení a zpracování výjimek na odstranění objektu  
 Ve stromu paralelní pracovní úlohu, která se zruší, zabraňuje spuštění podřízené úlohy. To může způsobit problémy, pokud jeden z podřízené úlohy provádí operaci, která je důležité pro vaši aplikaci, třeba uvolnění prostředku. Zrušení úlohy kromě toho může způsobit výjimku rozšíří v rámci destruktoru objektu a způsobit nedefinované chování vaší aplikace.  
  
 V následujícím příkladu `Resource` třída popisuje prostředek a `Container` třída popisuje kontejner, který obsahuje prostředky. V jeho destruktor `Container` třídy volání `cleanup` metoda dvěma z jeho `Resource` členy v paralelní a poté zavolá `cleanup` metoda na jeho třetí `Resource` člen.  
  
 [!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_10.h)]  
  
 I když tento vzor má sama o sobě žádné problémy, zvažte následující kód, který spouští úlohy dvou paralelně. První úlohou vytvoří `Container` objekt a v druhé úloze zruší celkové úloh. Pro ilustraci v příkladu používá dva [concurrency::event](../../parallel/concrt/reference/event-class.md) objekty, které se ujistěte, že dojde k zrušení po `Container` objekt se vytvoří a že `Container` objekt zničen po zrušení operace probíhá.  
  
 [!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_11.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
Container 1: Freeing resources...Exiting program...  
```  
  
 Tento příklad kódu obsahuje následující problémy, které může způsobit, že se chovat jinak, než bylo očekáváno:  
  
-   Zrušení úlohy nadřazené způsobí, že podřízené úlohy, volání [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke), také být zrušena. Proto nejsou tyto dva prostředky uvolnit.  

  
-   Zrušení úlohy nadřazené způsobí, že podřízené úlohy na vnitřní výjimku. Protože `Container` destruktor nezpracovává výjimku, výjimka je rozšířeny nahoru a třetí prostředku není vydání.  
  
-   Výjimka, která je vyvolána úlohou podřízené šíří prostřednictvím `Container` destruktor. Vyvolání z destruktor vloží nedefinované stavu aplikace.  
  
 Doporučujeme neprovádět kritické operace, jako je například uvolnění prostředků v úlohách, pokud nemůžete zaručit, že tyto úlohy nebudou zrušeny. Doporučujeme taky, nepoužívejte funkcionalita modulu runtime, který lze vyvolat v destruktoru objektu vaší typy.  
  
 [[Horní](#top)]  
  
##  <a name="repeated-blocking"></a>Opakovaně nebrání v paralelní smyčky  

 Paralelní smyčky, jako [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) nebo [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) , je při ovládnutí blokování operace může způsobit, že modul runtime prostřednictvím po krátkou dobu vytvořit mnoho vláken.  

  
 Pokud úloha dokončí, spolupráce při blokování nebo vypočítá, Concurrency Runtime provede další práci. Pokud jeden paralelní smyčka iterace bloky, modul runtime může zahájit další iterace. Pokud nejsou žádné dostupné nečinného vlákna, modul runtime vytvoří nové vlákno.  
  
 Pokud text paralelní smyčka příležitostně bloky, tento mechanismus pomáhá maximalizovat celkovou propustnost úloh. Ale při blokování velký počet iterací, modul runtime může vytvořit mnoho podprocesů pro spuštění další práci. To může vést k nedostatku paměti nebo nízký využití hardwarových prostředků.  
  
 Podívejte se na následující příklad, který volá [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce při každém opakování `parallel_for` smyčky. Protože `send` blokuje spolupráce při, modul runtime vytvoří nové vlákno spouštět další pracovní pokaždé, když `send` je volána.  
  
 [!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_12.cpp)]  
  
 Doporučujeme vám, že zrefaktorujete kódu předejdete tohoto vzoru. V tomto příkladu se můžete vyhnout vytvoření další vlákna voláním `send` v serial `for` smyčky.  
  
 [[Horní](#top)]  
  
##  <a name="blocking"></a>Neprovádějte blokování operace při zrušení paralelní práce  

 Pokud je to možné, neprovádějte blokování operations před voláním [concurrency::task_group::cancel](reference/task-group-class.md#cancel) nebo [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) metoda zrušit paralelní práce.  


  
 Když úloha provede spolupráce, blokování operace, modul runtime provádět jinou práci, zatímco první úloha čeká na data. Modul runtime provádí změny plánu úloh čekací při jeho odblokuje. Modul runtime obvykle provádí změny plánu úlohy, které byly nedávno odblokuje před provádí změny plánu úlohy, které byly méně odblokování. Modul runtime proto může plánování nepotřebné práce při blokování operaci, což vede k poklesu výkonu. Při provádění operace s blokování před zrušením paralelní práce, podle toho, můžete blokování operaci zpoždění volání `cancel`. To způsobí, že další úlohy pro práci zbytečné.  
  
 Podívejte se na následující příklad, který definuje `parallel_find_answer` funkci, která hledá element zadaného pole, která splňuje zadané funkce predikátu. Když funkce predikátu vrátí `true`, vytvoří paralelní pracovní funkce `Answer` objektu a zruší úlohu celkové.  
  
 [!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_13.cpp)]  
  


 `new` Operátor provádí přidělení haldy, které by mohly blokovat. Modul runtime provede další práci jenom v případě, že úloha provede spolupráce, blokování volání, jako je například volání [concurrency::critical_section::lock](reference/critical-section-class.md#lock).  


  
 Následující příklad ukazuje, jak zabránit zbytečných práci, a tak zlepšit výkon. Tento příklad zruší skupiny úloh před přiděluje úložiště pro `Answer` objektu.  
  
 [!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_14.cpp)]  
  
 [[Horní](#top)]  
  
##  <a name="shared-writes"></a>Nezapisovat sdílených dat v paralelní smyčky  
 Concurrency Runtime poskytuje několik datové struktury, například [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), které se synchronizují souběžný přístup ke sdíleným datům. Tyto datové struktury jsou užitečné v mnoha případech, například pokud více úkolů zřídka vyžadují sdílený přístup k prostředku.  
  
 Podívejte se na následující příklad, který používá [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus a `critical_section` objekt, který chcete vypočítat počet prvočísel v [std::array](../../standard-library/array-class-stl.md) objektu. V tomto příkladu se nedá použít, protože každé vlákno musí čekání na přístup k sdílené proměnné `prime_sum`.  

  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_15.cpp)]  
  
 V tomto příkladu může vést k nižšímu výkonu protože časté operace uzamčení efektivně serializuje smyčky. Kromě toho když objekt Concurrency Runtime provede operaci na blokování, plánovače může vytvořit další vlákno umožní provádět jinou práci při první vlákno čeká na data. Pokud modul runtime vytvoří velký počet vláken, protože mnoho úloh, které čekají na sdílených dat, můžete aplikaci nízký výkon nebo zadejte stav nedostatku prostředků.  
  
 Definuje knihovně PPL [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třída, která pomáhá eliminovat sdíleného stavu tím, že poskytuje přístup ke sdíleným prostředkům způsobem uvolnění zámku. `combinable` Třída poskytuje úložiště thread-local, který vám umožní provádět podrobné výpočty a pak sloučit těchto výpočtů do konečný výsledek. Si můžete představit `combinable` objektu jako redukční proměnnou.  
  
 Následující příklad změní předchozímu pomocí `combinable` objektu místo `critical_section` objektu k výpočtu součet. Tento příklad škáluje, protože každé vlákno obsahuje vlastní místní kopii součet. Tento příklad používá [concurrency::combinable::combine](reference/combinable-class.md#combine) metoda sloučit místní výpočtů do konečný výsledek.  

  
 [!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_16.cpp)]  
  
 Dokončení verzi v tomto příkladu, naleznete v části [postupy: použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md). Další informace o `combinable` třídy najdete v tématu [paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md).  
  
 [[Horní](#top)]  
  
##  <a name="false-sharing"></a>Pokud je to možné, vyhněte se False sdílení  
 *False sdílení* nastane, když více souběžných úloh, které jsou spuštěny na samostatné procesory zapisovat do proměnné, které jsou umístěny na stejném řádku mezipaměti. Pokud jeden úkol zapisuje do jedné z proměnných, řádek mezipaměti pro obě proměnné je neplatná. Každý procesor musí znovu načíst řádek mezipaměti pokaždé, když je řádek mezipaměti zrušena. Proto false sdílení může způsobit snížení výkonu ve vaší aplikaci.  
  
 Následující základní příklad ukazuje dva souběžné úlohy, každý zvýší čítače sdílené proměnné.  
  
 [!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_17.cpp)]  
  
 K vyloučení, sdílení dat mezi dvěma úlohami, můžete upravit příklad pro použití dvou proměnných čítače. Tento příklad vypočítá hodnotu konečné čítače po dokončení úlohy. Však tento příklad ukazuje false sdílení, protože proměnné `count1` a `count2` mohou nacházet na stejném řádku mezipaměti.  
  
 [!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_18.cpp)]  
  
 Jedním ze způsobů eliminovat false sdílení je zajistit, že proměnné čítače jsou v mezipaměti samostatné řádky. Následující příklad zarovnává proměnné `count1` a `count2` na hranicích 64 bajtů.  
  
 [!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_19.cpp)]  
  
 Tento příklad předpokládá, že velikost mezipaměti je 64 bajtů.  
  
 Doporučujeme vám, že používáte [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídy při musejí sdílet data mezi úlohy. `combinable` Třída vytvoří tak, že false sdílení je méně pravděpodobné lokální proměnné vláken. Další informace o `combinable` třídy najdete v tématu [paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md).  
  
 [[Horní](#top)]  
  
##  <a name="lifetime"></a>Ujistěte se, že jsou platné po celou dobu úlohy  
 Když zadáte skupinu úloh nebo paralelní algoritmus výrazu lambda, klauzuli zachycení Určuje, zda text výrazu lambda přistupuje k proměnné ve vymezeném oboru hodnotou nebo odkazem. Pokud předáte proměnné výrazu lambda odkazem, musí zaručit, že životnost tuto proměnnou ukládá až do dokončení této úlohy.  
  
 Podívejte se na následující příklad, který definuje `object` třídy a `perform_action` funkce. `perform_action` Funkce vytvoří `object` proměnné a asynchronně provádí některé akce na tuto proměnnou. Protože není zaručeno, že úloha dokončit před `perform_action` funkce vrátí, program bude k chybě nebo vykazovat neurčené chování, pokud `object` proměnná zničen, když je spuštěn úkol.  
  
 [!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_20.cpp)]  
  
 V závislosti na požadavcích vaší aplikace můžete použít jednu z následujících postupů zaručit, že proměnné zůstávají platná po celou dobu každý úkol.  
  
 Následující příklad předá `object` proměnné hodnotou úlohy. Proto úloha funguje na vlastní kopii proměnnou.  
  
 [!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_21.cpp)]  
  
 Protože `object` proměnné je předaná hodnota, změny stavu, ke kterým došlo k této proměnné se nezobrazí v původní kopii.  
  
 Následující příklad používá [concurrency::task_group::wait](reference/task-group-class.md#wait) metoda a ujistěte se, že dokončení této úlohy před `perform_action` funkce vrátí.  


  
 [!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_22.cpp)]  
  
 Protože teď dokončení této úlohy před funkce vrátí hodnotu, `perform_action` funkce už chová asynchronně.  
  
 Následující příklad změní `perform_action` funkce provést odkaz na `object` proměnné. Volající musí zaručit, který platnosti `object` proměnná platí až do dokončení této úlohy.  
  
 [!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_23.cpp)]  
  
 Můžete taky ukazatel k řízení životního cyklu objektu, který můžete předat paralelní algoritmus nebo skupina úloh.  
  
 Další informace o výrazy lambda najdete v tématu [výrazy Lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
 [[Horní](#top)]  
  
## <a name="see-also"></a>Viz také  
 [Osvědčené postupy Concurrency Runtime](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [Knihovna Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md)   
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)   
 [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)   
 [Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [Postupy: použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)   
 [Postupy: použití zrušení přerušení paralelní smyčky](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)   
 [Postupy: použití objektu combinable ke zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)   
 [Osvědčené postupy v knihovně asynchronních agentů](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)   
 [Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)

