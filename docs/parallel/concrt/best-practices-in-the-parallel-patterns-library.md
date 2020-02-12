---
title: Osvědčené postupy v knihovně PPL (Parallel Patterns Library)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library, practices to avoid
- practices to avoid, Parallel Patterns Library
- best practices, Parallel Patterns Library
- Parallel Patterns Library, best practices
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
ms.openlocfilehash: 641d85b03fca13a6592610d87563e3e701ad3e3e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142089"
---
# <a name="best-practices-in-the-parallel-patterns-library"></a>Osvědčené postupy v knihovně PPL (Parallel Patterns Library)

Tento dokument popisuje, jak nejlépe využít knihovnu paralelních vzorů (PPL). PPL poskytuje obecné kontejnery, objekty a algoritmy pro provádění jemně odstupňovaného paralelismu.

Další informace o PPL naleznete v tématu [Knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

## <a name="top"></a>Řezů

Tento dokument obsahuje následující části:

- [Paralelizovaty malých smyček](#small-loops)

- [Vyjádřete paralelismus na nejvyšší možné úrovni](#highest)

- [Řešení problémů s dělením a panuj "pomocí parallel_invoke](#divide-and-conquer)

- [Přerušení paralelní smyčky pomocí zrušení nebo zpracování výjimek](#breaking-loops)

- [Vysvětlení vlivu zrušení a zpracování výjimek na zničení objektu](#object-destruction)

- [Neblokovat opakovaně v paralelní smyčce](#repeated-blocking)

- [Neprovádět blokování operací při zrušení paralelní práce](#blocking)

- [Nezapisovat do sdílených dat v paralelní smyčce](#shared-writes)

- [Pokud je to možné, vyhněte se nepravdivému sdílení](#false-sharing)

- [Ujistěte se, že proměnné jsou platné po celou dobu životnosti úlohy.](#lifetime)

## <a name="small-loops"></a>Paralelizovaty malých smyček

Paralelismus poměrně malých smyček může způsobit, že související režie plánování převažuje nad výhodami paralelního zpracování. Vezměte v úvahu následující příklad, který přidá každou dvojici prvků ve dvou polích.

[!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_1.cpp)]

Zatížení pro každou iteraci paralelní smyčky je moc malé, takže se nedá využít režie pro paralelní zpracování. Výkon této smyčky můžete zvýšit provedením více práce v těle smyčky nebo provedením sériového cyklu.

[[Nahoře](#top)]

## <a name="highest"></a>Vyjádřete paralelismus na nejvyšší možné úrovni

Pokud paralelizovat kód pouze na nízké úrovni, můžete zavést konstrukce větvení, která se neškáluje podle počtu procesorů. Konstrukce *větvení spojení* je konstrukce, kde jeden úkol rozděluje svou práci na menší paralelní dílčí úkoly a čeká na dokončení těchto dílčích úkolů. Každý dílčí úkol může rekurzivně rozdělit sebe sama na další dílčí úkoly.

I když model spojení větví může být užitečný pro řešení nejrůznějších problémů, existují situace, kdy režijní náklady na synchronizaci můžou snížit škálovatelnost. Zvažte například následující sériový kód, který zpracovává data obrázků.

[!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_2.cpp)]

Vzhledem k tomu, že je každá iterace smyčky nezávislá, můžete paralelizovat spoustu práce, jak je znázorněno v následujícím příkladu. Tento příklad používá algoritmus [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) k paralelizovat vnější smyčky.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_3.cpp)]

Následující příklad ukazuje konstrukt větvení spojení voláním funkce `ProcessImage` ve smyčce. Každé volání `ProcessImage` nevrátí do dokončení každého dílčího úkolu.

[!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_4.cpp)]

Pokud Každá iterace paralelní smyčky buď neprovede téměř žádnou práci, nebo práce, kterou provádí paralelní smyčka, je nevyvážená, to znamená, že některé iterace smyčky pobírají déle než jiné, režijní náklady na plánování, které je potřeba často rozvětvení a připojení k práci, můžou převážení výhody na paralelní provádění. Tato režie se zvyšuje tak, jak se zvyšuje počet procesorů.

Chcete-li snížit množství režie plánování v tomto příkladu, můžete paralelizovat vnější smyčky před paralelizovat vnitřních smyček nebo použít jinou paralelní konstrukci, jako je například přesměrování. Následující příklad upraví funkci `ProcessImages`, aby používala algoritmus [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) , aby paralelizovat vnější smyčku.

[!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_5.cpp)]

Podobný příklad, který používá kanál k paralelnímu zpracování bitové kopie, naleznete v tématu [Návod: vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Nahoře](#top)]

## <a name="divide-and-conquer"></a>Řešení problémů s dělením a panuj "pomocí parallel_invoke

Problém s *dělením a panuj "* je forma konstrukce větvení, která používá rekurzi k přerušení úkolu na dílčí úkoly. Kromě tříd [Concurrency:: task_group](reference/task-group-class.md) a [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) můžete také použít algoritmus [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) k řešení problémů s dělením a panuj ". `parallel_invoke` algoritmus má stručnější syntaxi než objekty skupiny úloh a je užitečný v případě, že máte pevný počet paralelních úkolů.

Následující příklad ukazuje použití algoritmu `parallel_invoke` k implementaci algoritmu řazení bitonického.

[!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_6.cpp)]

Chcete-li snížit režii, algoritmus `parallel_invoke` provádí poslední posloupnost úloh v volajícím kontextu.

Úplnou verzi tohoto příkladu naleznete v tématu [How to: Use parallel_invoke k zápisu paralelní řadicí rutiny](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md). Další informace o algoritmu `parallel_invoke` najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

[[Nahoře](#top)]

## <a name="breaking-loops"></a>Přerušení paralelní smyčky pomocí zrušení nebo zpracování výjimek

PPL poskytuje dva způsoby, jak zrušit paralelní práci, kterou provádí skupina úloh nebo paralelní algoritmus. Jedním ze způsobů je použít mechanismus zrušení, který je poskytován třídami [Concurrency:: task_group](reference/task-group-class.md) a [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) . Druhým způsobem je vyvolat výjimku v těle pracovní funkce úkolu. Mechanismus zrušení je efektivnější než zpracování výjimek při zrušení stromové struktury paralelní práce. *Paralelní pracovní strom* je skupina souvisejících skupin úloh, ve kterých některé skupiny úloh obsahují další skupiny úloh. Mechanismus zrušení zruší skupinu úloh a jejích podřízených skupin úloh tak, aby byl shora dolů. Zpracování výjimek naopak funguje tak, jak je v dolní části, a musí každou podřízenou skupinu úloh zrušit nezávisle, protože se výjimka rozšíří nahoru.

Při přímé práci s objektem skupiny úloh použijte metody [Concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) nebo [concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) pro zrušení práce, která patří do této skupiny úloh. Chcete-li zrušit paralelní algoritmus, například `parallel_for`, vytvořte nadřazenou skupinu úloh a zrušte tuto skupinu úloh. Zvažte například následující funkci, `parallel_find_any`, která vyhledává hodnotu v poli paralelně.

[!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_7.cpp)]

Vzhledem k tomu, že paralelní algoritmy používají skupiny úloh, když jedna z paralelních iterací zruší nadřazenou skupinu úloh, je celkový úkol zrušen. Úplnou verzi tohoto příkladu naleznete v tématu [How to: use rerušení pro přerušení paralelní smyčky](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md).

Přestože zpracování výjimek je méně efektivní způsob, jak zrušit paralelní práci, než je mechanismus zrušení, existují případy, kdy je zpracování výjimek vhodné. Například následující metoda, `for_all`, rekurzivně provádí pracovní funkci na každém uzlu `tree` struktury. V tomto příkladu je datový člen `_children` [std:: list](../../standard-library/list-class.md) , který obsahuje objekty `tree`.

[!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_8.cpp)]

Volající metody `tree::for_all` může vyvolat výjimku, pokud nepožaduje volání pracovní funkce pro každý prvek stromu. Následující příklad ukazuje funkci `search_for_value`, která vyhledá hodnotu v zadaném objektu `tree`. Funkce `search_for_value` používá pracovní funkci, která vyvolá výjimku, když aktuální prvek stromu odpovídá zadané hodnotě. Funkce `search_for_value` používá blok `try-catch` k zachycení výjimky a k vytištění výsledku do konzoly.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_9.cpp)]

Úplnou verzi tohoto příkladu naleznete v tématu [How to: použití zpracování výjimek k přerušení paralelní smyčky](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

Obecnější informace o mechanismu zrušení a zpracování výjimek, které jsou k dispozici v PPL, naleznete v tématu [zrušení v PPL](cancellation-in-the-ppl.md) a [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

[[Nahoře](#top)]

## <a name="object-destruction"></a>Vysvětlení vlivu zrušení a zpracování výjimek na zničení objektu

Ve stromové struktuře paralelní práce úloha, která je zrušena, brání spuštění podřízených úloh. To může způsobit problémy, pokud jedna z podřízených úloh provádí operaci, která je pro vaši aplikaci důležitá, například uvolnění prostředku. Kromě toho může zrušení úlohy způsobit, že se výjimka rozšíří skrze destruktor objektu a ve vaší aplikaci způsobí nedefinované chování.

V následujícím příkladu třída `Resource` popisuje prostředek a třída `Container` popisuje kontejner, který obsahuje prostředky. Ve svém destruktoru třída `Container` volá metodu `cleanup` na dvou svých `Resource`ch členů paralelně a potom volá metodu `cleanup` na svém třetím `Resource` členu.

[!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_10.h)]

I když tento model nemá vlastní problémy, zvažte následující kód, který spouští dva úkoly paralelně. První úkol vytvoří objekt `Container` a druhý úkol zruší celkový úkol. Pro ilustraci příklad používá dva objekty [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) , aby se zajistilo, že zrušení proběhne po vytvoření objektu `Container` a že objekt `Container` je zničen po výskytu operace zrušení.

[!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_11.cpp)]

Tento příklad vytvoří následující výstup:

```Output
Container 1: Freeing resources...Exiting program...
```

Tento příklad kódu obsahuje následující problémy, které by mohly způsobit, že se chová jinak, než očekáváte:

- Zrušení nadřazeného úkolu způsobí, že se zruší i podřízená úloha, volání [souběžnosti::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke). Proto tyto dva prostředky nejsou uvolněny.

- Zrušení nadřazené úlohy způsobí, že podřízená úloha vyvolá vnitřní výjimku. Vzhledem k tomu, že destruktor `Container` nezpracovává tuto výjimku, je tato výjimka rozšířena směrem nahoru a třetí prostředek není uvolněn.

- Výjimka, která je vyvolána podřízenou úlohou, se šíří pomocí `Container` destruktoru. Vyvolání z destruktoru vloží aplikaci do nedefinovaného stavu.

Doporučujeme, abyste v úlohách neprováděli kritické operace, jako je třeba uvolnění prostředků, pokud nebudete mít jistotu, že tyto úlohy nebudou zrušeny. Doporučujeme také, abyste nepoužívali běhové funkce, které mohou být vyvolány v destruktoru vašich typů.

[[Nahoře](#top)]

## <a name="repeated-blocking"></a>Neblokovat opakovaně v paralelní smyčce

Paralelní smyčka jako [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) nebo [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) , která je ovládána blokujícími operace, může způsobit, že modul runtime v krátké době vytvoří mnoho vláken.

Concurrency Runtime provádí další práci, když úkol dokončí nebo spolupracuje nebo poskytne. Když jeden cyklus iterace paralelní smyčky, modul runtime může zahájit další iteraci. Pokud nejsou k dispozici žádná nečinná vlákna, modul runtime vytvoří nové vlákno.

Když tělo paralelní smyčky občas blokuje, tento mechanismus pomáhá maximalizovat celkovou propustnost úlohy. Pokud však mnoho iterací blok blokuje, modul runtime může vytvořit mnoho vláken, aby bylo možné spustit další práci. To může vést k nedostatku paměti nebo špatnému využití hardwarových prostředků.

Vezměte v úvahu následující příklad, který volá funkci [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) v každé iteraci `parallel_for` smyčky. Vzhledem k tomu, že `send` zablokuje spolupráci, modul runtime vytvoří nové vlákno pro spuštění dalších práce pokaždé, když `send` je volána.

[!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_12.cpp)]

Pro zamezení tohoto vzoru doporučujeme kód Refaktorovat. V tomto příkladu se můžete vyhnout vytváření dalších vláken voláním `send` ve smyčce sériového `for`.

[[Nahoře](#top)]

## <a name="blocking"></a>Neprovádět blokování operací při zrušení paralelní práce

Pokud je to možné, neprovádějte operace blokování před voláním metody [Concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) nebo [concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) pro zrušení paralelní práce.

Když úloha provede operaci blokování spolupráce, modul runtime může provést další práci, zatímco první úkol počká na data. Modul runtime při odblokování znovu naplánuje čekající úlohu. Modul runtime obvykle znovu naplánuje úlohy, které byly nedávno odblokovány předtím, než znovu naplánuje úlohy, které byly v poslední době odblokovány. Proto může modul runtime naplánovat nepotřebnou práci během blokující operace, což vede ke snížení výkonu. Proto když provádíte blokující operaci před zrušením paralelní práce, blokující operace může zpozdit volání `cancel`. To způsobí, že další úlohy budou provádět zbytečné práce.

Vezměte v úvahu následující příklad, který definuje funkci `parallel_find_answer`, která vyhledá prvek poskytnutého pole, který splňuje zadanou funkci predikátu. Pokud funkce predikátu vrátí **hodnotu true**, funkce paralelní práce vytvoří objekt `Answer` a zruší celkový úkol.

[!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_13.cpp)]

Operátor `new` provádí přidělení haldy, což může zablokovat. Modul runtime provádí jinou práci pouze v případě, že úloha provádí volání blokující při spolupráci, jako je například volání [Concurrency:: critical_section:: Lock](reference/critical-section-class.md#lock).

Následující příklad ukazuje, jak zabránit zbytečné práci, a tím zlepšit výkon. Tento příklad zruší skupinu úloh před tím, než přidělí úložiště pro objekt `Answer`.

[!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_14.cpp)]

[[Nahoře](#top)]

## <a name="shared-writes"></a>Nezapisovat do sdílených dat v paralelní smyčce

Concurrency Runtime poskytuje několik datových struktur, například [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md), které synchronizují souběžný přístup ke sdíleným datům. Tyto datové struktury jsou užitečné v mnoha případech, například když více úloh často vyžaduje sdílený přístup k prostředku.

Vezměte v úvahu následující příklad, který používá algoritmus [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) a objekt `critical_section` k výpočtu počtu primárních čísel v objektu [std:: Array](../../standard-library/array-class-stl.md) . Tento příklad není škálovatelný, protože každé vlákno musí čekat na přístup ke sdílené proměnné `prime_sum`.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_15.cpp)]

Tento příklad může také vést k špatnému výkonu, protože častá operace zamykání efektivně serializovat smyčku. Kromě toho, když objekt Concurrency Runtime provádí blokující operaci, může Plánovač vytvořit další vlákno k provedení jiné práce, zatímco první vlákno čeká na data. Pokud modul runtime vytvoří mnoho vláken, protože mnohé úlohy čekají na sdílená data, může aplikace pracovat špatně nebo zadat stav s nízkým zdrojem.

PPL definuje třídu [Concurrency::](../../parallel/concrt/reference/combinable-class.md) kombinovat, která pomáhá eliminovat sdílený stav tím, že poskytuje přístup ke sdíleným prostředkům způsobem bez zámků. Třída `combinable` poskytuje místní úložiště pro vlákna, které umožňuje provádět jemně odstupňované výpočty a pak tyto výpočty sloučit do konečného výsledku. Objekt `combinable` lze představit jako redukční proměnnou.

Následující příklad upravuje předchozí pomocí objektu `combinable` namísto objektu `critical_section` k výpočtu součtu. Tento příklad se škáluje, protože každé vlákno obsahuje svou vlastní místní kopii součtu. Tento příklad používá metodu [Concurrency:: Merged:: kombinovat](reference/combinable-class.md#combine) pro sloučení místních výpočtů do konečného výsledku.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_16.cpp)]

Úplnou verzi tohoto příkladu naleznete v tématu [How to: use kombinovat pro zlepšení výkonu](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md). Další informace o třídě `combinable` naleznete v tématu [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md).

[[Nahoře](#top)]

## <a name="false-sharing"></a>Pokud je to možné, vyhněte se nepravdivému sdílení

K *nepravdivému sdílení* dojde, pokud více souběžných úloh, které jsou spuštěny v samostatných procesorech, zapisuje do proměnných, které jsou umístěny na stejném řádku mezipaměti. Když jeden úkol zapíše do jedné z proměnných, řádek mezipaměti pro obě proměnné se zruší. Každý procesor musí znovu načíst řádek mezipaměti při každém zrušení platnosti řádku mezipaměti. Proto sdílení false může způsobit snížení výkonu aplikace.

Následující základní příklad ukazuje dva souběžné úlohy, které každý zvýší sdílenou proměnnou čítače.

[!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_17.cpp)]

Chcete-li odstranit sdílení dat mezi dvěma úlohami, můžete příklad upravit tak, aby používal dvě proměnné čítače. Tento příklad vypočítá konečnou hodnotu čítače po dokončení úkolů. Tento příklad ukazuje nepravdivé sdílení, protože proměnné `count1` a `count2` jsou pravděpodobně umístěny na stejném řádku mezipaměti.

[!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_18.cpp)]

Jedním ze způsobů, jak eliminovat nepravdivé sdílení, je zajistit, aby proměnné čítače byly na samostatných řádcích mezipaměti. Následující příklad zarovnává proměnné `count1` a `count2` na hranicích 64 bajtů.

[!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_19.cpp)]

V tomto příkladu se předpokládá, že velikost mezipaměti paměti je 64 nebo méně bajtů.

Pokud je nutné sdílet data mezi úkoly, doporučujeme použít třídu [Concurrency::](../../parallel/concrt/reference/combinable-class.md) kombinovat. Třída `combinable` vytváří proměnné lokální pro vlákna, aby bylo sdílení false méně pravděpodobným způsobem. Další informace o třídě `combinable` naleznete v tématu [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md).

[[Nahoře](#top)]

## <a name="lifetime"></a>Ujistěte se, že proměnné jsou platné po celou dobu životnosti úlohy.

Když zadáte výraz lambda do skupiny úloh nebo paralelního algoritmu, klauzule Capture určuje, zda tělo výrazu lambda přistupuje k proměnným v nadřazeném oboru podle hodnoty nebo odkazu. Pokud předáte proměnné na lambda výraz odkazem, je nutné zaručit, že životnost této proměnné přetrvává až do dokončení úkolu.

Vezměte v úvahu následující příklad, který definuje třídu `object` a funkci `perform_action`. Funkce `perform_action` vytvoří proměnnou `object` a provede u této proměnné asynchronní akci. Vzhledem k tomu, že úloha není zaručena, aby se mohla dokončit, než se funkce `perform_action` vrátí, program dojde k chybě nebo se projeví nespecifikované chování, pokud je při spuštění úlohy zničena `object` proměnná.

[!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_20.cpp)]

V závislosti na požadavcích vaší aplikace můžete použít jeden z následujících postupů k zajištění, aby proměnné zůstaly platné po celou dobu životnosti každého úkolu.

Následující příklad předává `object` proměnnou hodnotou do úlohy. Proto úkol funguje na vlastní kopii proměnné.

[!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_21.cpp)]

Vzhledem k tomu, že je proměnná `object` předána hodnotou, všechny změny stavu, ke kterým dojde v této proměnné, se nezobrazují v původní kopii.

Následující příklad používá metodu [Concurrency:: task_group:: wait](reference/task-group-class.md#wait) k ujištění, že je úloha dokončena před tím, než se vrátí funkce `perform_action`.

[!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_22.cpp)]

Vzhledem k tomu, že úkol je nyní dokončen před vrácením funkce, funkce `perform_action` se už asynchronně nechová.

Následující příklad upraví funkci `perform_action`, aby převzala odkaz na `object` proměnnou. Volající musí zaručit, že životnost `object` proměnné je platná, dokud úloha neskončí.

[!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_23.cpp)]

Můžete také použít ukazatel k řízení životnosti objektu, který předáte do skupiny úloh nebo paralelního algoritmu.

Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

[[Nahoře](#top)]

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
