---
title: Asynchronní bloky zpráv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b180b1a92defb2c29d0e54b0ecf9700dd299170
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163423"
---
# <a name="asynchronous-message-blocks"></a>Asynchronní bloky zpráv

Knihovna agentů obsahuje několik typů bloku zpráv, které vám umožní rozšířit zpráv mezi součástmi aplikace způsobem bezpečným pro vlákno. Tyto typy bloku zpráv se často používají různé rutiny předávání zpráv, jako například [concurrency::send](reference/concurrency-namespace-functions.md#send), [concurrency::asend](reference/concurrency-namespace-functions.md#asend), [concurrency::receive](reference/concurrency-namespace-functions.md#receive), a [concurrency::try_receive](reference/concurrency-namespace-functions.md#try_receive). Další informace o usnadnění rutin, které jsou definované knihovnou agentů najdete v tématu [funkce předávání zpráv](../../parallel/concrt/message-passing-functions.md).

##  <a name="top"></a> Oddíly

Toto téma obsahuje následující oddíly:

- [Zdroje a cíle](#sources_and_targets)

- [Šíření zpráv](#propagation)

- [Přehled typů bloků zpráv](#overview)

- [Třída unbounded_buffer](#unbounded_buffer)

- [overwrite_buffer – třída](#overwrite_buffer)

- [single_assignment – třída](#single_assignment)

- [call – třída](#call)

- [transformer – třída](#transformer)

- [choice – třída](#choice)

- [Třídy JOIN a multitype_join](#join)

- [timer – třída](#timer)

- [Filtrování zpráv](#filtering)

- [Rezervace zprávy](#reservation)

##  <a name="sources_and_targets"></a> Zdroje a cíle

Zdroje a cíle jsou dva důležité účastníky, kterými předávání zpráv. A *zdroj* odkazuje na koncový bod komunikace, která odesílá zprávy. A *cílové* odkazuje na koncový bod komunikace, která přijímá zprávy. Si můžete představit jako koncový bod, který lze číst ze zdroj a cíl jako koncový bod, který píšete pro. Aplikace připojit zdroje a cíle společně do formuláře *sítí pro zasílání zpráv*.

Knihovna agentů používá abstraktní dvě třídy pro reprezentaci zdroje a cíle: [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) a [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md). Typy bloků zpráv, které se chovají jako zdroje, jsou odvozeny z `ISource`; typy bloků zpráv, které se chovají jako cíle, jsou odvozeny z `ITarget`. Typy bloků zpráv, které se chovají jako zdroje a cíle, jsou odvozeny z obou `ISource` a `ITarget`.

[[Horní](#top)]

##  <a name="propagation"></a> Šíření zpráv

*Šíření zprávy* je proces odeslání zprávy mezi jednotlivými komponentami. Když bloku zprávy se nabízí zprávu, můžete přijmout, zamítnutí nebo odložit této zprávy. Každý typ bloku zprávy ukládá a odesílá zprávy různými způsoby. Například `unbounded_buffer` třída uchovává neomezený počet zpráv, `overwrite_buffer` třídy ukládá do jedné zprávy najednou a Transformer – třída ukládá upravený verzi každou zprávu. Tyto typy bloků zpráv jsou popsány podrobněji dále v tomto dokumentu.

Pokud blok zpráv přijme zprávu, může volitelně provedení práce a, pokud blok zpráv je zdrojem, předat jiným členem sítě výslednou zprávu. Blok zpráv můžete použít funkci filtru tak, aby odmítal zprávy, které nechce dostávat. Filtry jsou popsány podrobněji dále v tomto tématu v části [filtrování zpráv](#filtering). Blok zpráv, který odloží zprávu můžete rezervovat tuto zprávu a používat ji později. Rezervace zprávy je popsána podrobněji dále v tomto tématu v části [rezervace zprávy](#reservation).

Knihovna agentů asynchronně umožňuje blokům zpráv nebo synchronně předávání zpráv. Pokud předáte zprávy bloku zprávy synchronně, například pomocí `send` funkce, modul runtime blokuje aktuální kontext dokud cílový blok přijme nebo odmítne zprávy. Pokud předáte zprávy bloku zprávy asynchronně, například pomocí `asend` funkce, modul runtime nabízí zprávy na cíl, a pokud cíl přijme zprávu, modul runtime naplánuje asynchronní úloha, která se šíří zprávy, příjemci. Modul runtime používá jednoduché úlohy šíření zpráv na způsob spolupráce za. Další informace o jednoduché úlohy, naleznete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Aplikace zdroje a cíle vzájemně propojit a formulář sítí pro zasílání zpráv. Obvykle propojíte sítě a volání `send` nebo `asend` k předávání dat k síti. Chcete-li připojit blok zpráv zdroje na cíl, zavolejte [concurrency::ISource::link_target](reference/isource-class.md#link_target) metody. Chcete-li zdrojový odpojit cíl, zavolejte [concurrency::ISource::unlink_target](reference/isource-class.md#unlink_target) metody. Chcete-li odpojit zdrojový ze všech svých cílů, zavolejte [concurrency::ISource::unlink_targets](reference/isource-class.md#unlink_targets) metody. Pokud jeden z typů bloků předdefinovaných zpráv opustí rozsah nebo je zničen, se automaticky odpojí samotné z všechny cílové bloky. Některé typy bloků zpráv omezit maximální počet cílů, které může zapisovat. Následující část popisuje omezení, které se vztahují na typy bloků předdefinovaných zpráv.

[[Horní](#top)]

##  <a name="overview"></a> Přehled typů bloků zpráv

Následující tabulka stručně popisuje roli typů důležité bloku zpráv.

[unbounded_buffer](#unbounded_buffer)<br/>
Ukládá frontu zpráv.

[overwrite_buffer](#overwrite_buffer)<br/>
Uloží jednu zprávu, která může být zapsána do a čtení z více než jednou.

[single_assignment](#single_assignment)<br/>
Úložiště zpráv, který může zapisovat do jednou a číst z více než jednou.

[Volání](#call)<br/>
Provede práci, když přijme zprávu.

[Transformer](#transformer)<br/>
Provede práci při přijetí dat a odesílá výsledky, které pracují na jiný cílový blok. `transformer` Třídy můžete reagovat na různé vstupní a výstupní typy.

[podle výběru](#choice)<br/>
Vybírá první dostupnou zprávu ze skupiny zdrojů.

[spojení a multitype spojení](#join)<br/>
Počkejte, všechny zprávy přijaté ze skupiny zdrojů a pak sloučí zprávy do jedné zprávy pro jiného bloku zpráv.

[Časovač](#timer)<br/>
Odešle zprávu do cílový blok v pravidelných intervalech.

Tyto typy bloku zpráv mají jiné charakteristiky, které je provést užitečné pro různé situace. Toto jsou některé vlastnosti:

- *Propagace typu*: Určuje, zda blok zpráv funguje jako zdroj dat, příjemce dat nebo obojí.

- *Pořadí zpráv*: Určuje, zda blok zpráv udržuje původní pořadí, ve kterém jsou zprávy odeslat ani přijmout. Každý typ bloku předem definovanou zprávu udržuje původní pořadí, ve kterém odesílá nebo přijímá zprávy.

- *Zdroj počet*: maximální počet zdrojů, které bloku zpráv můžete číst z.

- *Počtu cílových*: maximální počet cílů, jež zapisovat do bloku zpráv.

Následující tabulka ukazuje, jak tyto vlastnosti se vztahují na různé typy bloku zpráv.

|Typ bloku zprávy|Propagace typu (zdroj, cíl nebo obojí)|Zpráva řazení (objednáno nebo Unordered)|Počet zdroje|Cílový počet|
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|
|`unbounded_buffer`|Obojí|Řazení|bez vazby|bez vazby|
|`overwrite_buffer`|Obojí|Řazení|bez vazby|bez vazby|
|`single_assignment`|Obojí|Řazení|bez vazby|bez vazby|
|`call`|Cíl|Řazení|bez vazby|Není k dispozici|
|`transformer`|Obojí|Řazení|bez vazby|1|
|`choice`|Obojí|Řazení|10|1|
|`join`|Obojí|Řazení|bez vazby|1|
|`multitype_join`|Obojí|Řazení|10|1|
|`timer`|Zdroj|Není k dispozici|Není k dispozici|1|

Následující části popisují typy bloku zpráv podrobněji.

[[Horní](#top)]

##  <a name="unbounded_buffer"></a> Třída unbounded_buffer

[Concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) třída reprezentuje strukturu pro obecné účely asynchronní zasílání zpráv. Tato třída uchovává první in-first-out (FIFO) fronty zpráv, které mohou být zapsaného do více zdrojů nebo číst z více cílů. Když cíl obdrží zprávu od `unbounded_buffer` objektu, tato zpráva se odebere z fronty zpráv. Proto i když `unbounded_buffer` objekt může mít více cílů, získá každou zprávu pouze jeden cíl. `unbounded_buffer` Třídy je užitečné, když chcete předat více zpráv na jiné komponenty a komponenty musí přijmout každou zprávu.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní struktura o tom, jak pracovat `unbounded_buffer` třídy. Tento příklad odešle tři hodnoty do `unbounded_buffer` objektu a pak přečte tyto hodnoty zpět ze stejného objektu.

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

Tento příklad vytvoří následující výstup:

```Output
334455
```

Úplný příklad, který ukazuje způsob použití `unbounded_buffer` najdete v tématu [postupy: implementace různých vzorů producent – příjemce](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Horní](#top)]

##  <a name="overwrite_buffer"></a> overwrite_buffer – třída

[Concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) třídy vypadá podobně jako `unbounded_buffer` třídy s výjimkou, že `overwrite_buffer` ukládá jenom jednu zprávu. Kromě toho, když cíl obdrží zprávu od `overwrite_buffer` objektu, tato zpráva se neodebere z vyrovnávací paměti. Proto více cílů obdrží kopii zprávy.

`overwrite_buffer` Třídy je užitečné, když chcete předat více zpráv na jiné součásti, ale, že součást potřebuje pouze nejnovější hodnotu. Tato třída je také užitečné, když chcete vysílání zpráv do více komponent.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní struktura o tom, jak pracovat `overwrite_buffer` třídy. Tento příklad odešle tři hodnoty do `overwrite _buffer` objektu a pak přečte aktuální hodnotu ze stejného objektu třikrát. Tento příklad je podobné jako v příkladu pro `unbounded_buffer` třídy. Ale `overwrite_buffer` třídy ukládá jenom jednu zprávu. Kromě toho modul runtime neodebere zpráv ze `overwrite_buffer` objektu poté, co je pro čtení.

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

Tento příklad vytvoří následující výstup:

```Output
555555
```

Úplný příklad, který ukazuje způsob použití `overwrite_buffer` najdete v tématu [postupy: implementace různých vzorů producent – příjemce](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Horní](#top)]

##  <a name="single_assignment"></a> single_assignment – třída

[Concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) třídy vypadá podobně jako `overwrite_buffer` třídy s výjimkou, že `single_assignment` objekt je možné zapisovat na pouze jednou. Podobně jako `overwrite_buffer` třídy, pokud je cíl přijme zprávu z `single_assignment` objektu, tato zpráva se neodebere z tohoto objektu. Proto více cílů obdrží kopii zprávy. `single_assignment` Třída je užitečná, když chcete vysílání zpráv do více komponent.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní struktura o tom, jak pracovat `single_assignment` třídy. Tento příklad odešle tři hodnoty k `single_assignment` objektu a pak přečte aktuální hodnotu ze stejného objektu třikrát. Tento příklad je podobné jako v příkladu pro `overwrite_buffer` třídy. I když obě `overwrite_buffer` a `single_assignment` třídy ukládat do jedné zprávy `single_assignment` třídy je možné zapisovat na pouze jednou.

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

Tento příklad vytvoří následující výstup:

```Output
333333
```

Úplný příklad, který ukazuje způsob použití `single_assignment` najdete v tématu [návod: implementace tříd Future](../../parallel/concrt/walkthrough-implementing-futures.md).

[[Horní](#top)]

##  <a name="call"></a> Call – třída

[Concurrency::call](../../parallel/concrt/reference/call-class.md) třída slouží jako příjemce zprávy, který provádí pracovní funkce, když přijme data. Tato pracovní funkce může být výraz lambda, objekt funkce nebo ukazatele na funkci. A `call` objekt chová jinak, než je běžné funkce volání, vzhledem k tomu, že funguje souběžně s ostatními součástmi, které odesílání zpráv do něj. Pokud `call` objektu je provádění práce, když obdrží zprávu, přidá zprávy do fronty. Každý `call` procesy objekt zprávy v pořadí, ve kterém jsou přijímány zařazené do fronty.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní struktura o tom, jak pracovat `call` třídy. Tento příklad vytvoří `call` objekt, který vytiskne jednotlivých hodnot, obdrží do konzoly. Příklad poté odešle tři hodnoty `call` objektu. Protože `call` objekt zpracovávat zprávy na samostatném vlákně, v tomto příkladu také používá proměnné čítače a [události](../../parallel/concrt/reference/event-class.md) objekt zajistit, aby `call` objekt zpracovávat všechny zprávy před `wmain` Funkce vrátí.

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

Tento příklad vytvoří následující výstup:

```Output
334455
```

Úplný příklad, který ukazuje způsob použití `call` najdete v tématu [jak: Zadejte pracovních funkcí třídám call a transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md).

[[Horní](#top)]

##  <a name="transformer"></a> Transformer – třída

[Concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) třída slouží jako obě zprávy příjemce a odesílatele zprávy. `transformer` Třídy vypadá podobně jako `call` třídy, protože při přijetí dat hraje pracovní funkce definované uživatelem. Ale `transformer` třída rovněž odesílá výsledek funkce práce na objekty příjemce. Podobně jako `call` objektu, `transformer` objekt funguje souběžně s ostatními součástmi, které odesílání zpráv do ní. Pokud `transformer` objektu je provádění práce, když obdrží zprávu, přidá zprávy do fronty. Každý `transformer` objekt zpracovává jeho zprávy ve frontě v pořadí, ve kterém jsou přijímány.

`transformer` Třídy odešle zprávu s jeho jeden cíl. Pokud nastavíte `_PTarget` parametr v konstruktoru `NULL`, cíl můžete zadat později pomocí volání [concurrency::link_target](reference/source-block-class.md#link_target) metody.

Na rozdíl od všech ostatních typů blok z asynchronních zpráv, poskytovaných knihovnou agentů `transformer` třídy můžete reagovat na různé vstupní a výstupní typy. Tato schopnost transformovat data z jednoho typu na jiný provede `transformer` třídy klíčovou komponentou v mnoha souběžných sítím. Kromě toho můžete přidat více podrobných paralelní funkcí ve funkci práce `transformer` objektu.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní struktura o tom, jak pracovat `transformer` třídy. Tento příklad vytvoří `transformer` objektu, vstupní násobky každý `int` hodnoty 0.33, aby bylo možné vytvořit `double` hodnotu jako výstup. V příkladu pak přijme transformovaný hodnoty ze stejné `transformer` objektu a vypíše do konzoly.

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

Tento příklad vytvoří následující výstup:

```Output
10.8914.5218.15
```

Úplný příklad, který ukazuje způsob použití `transformer` najdete v tématu [postupy: použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

[[Horní](#top)]

##  <a name="choice"></a> choice – třída

[Concurrency::choice](../../parallel/concrt/reference/choice-class.md) třídy vybírá první dostupnou zprávu ze skupiny zdrojů. `choice` Třída představuje mechanismus řízení toku místo mechanismus toku dat (tématu [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) popisuje rozdíly mezi toku dat a toku řízení).

Čtení z výběru objektu vypadá podobně jako volání funkce rozhraní Windows API `WaitForMultipleObjects` když má `bWaitAll` parametr nastaven na `FALSE`. Ale `choice` třídy sváže data s samotné místo události objektu externího synchronizace.

Obvykle se používají `choice` třídy společně s [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkce k řízení toku řízení ve vaší aplikaci. Použití `choice` třídy v případě, že máte na výběr z vyrovnávací paměti zpráv, které mají různé typy. Použití `single_assignment` případě, že máte na výběr z vyrovnávací paměti zpráv, které mají stejný typ třídy.

Pořadí, ve kterém je zdrojů a propojit `choice` objekt je důležitý, protože můžete určit, zpráv, které je vybrána. Například vezměte si situaci, kde propojit více obsahující zprávu do vyrovnávací paměti zpráv `choice` objektu. `choice` Objekt vybere zprávy z prvního zdroje, který je propojen. Po propojení všech zdrojů, `choice` objekt zachovává pořadí, ve kterém každý zdroj přijme zprávu.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní struktura o tom, jak pracovat `choice` třídy. V tomto příkladu [concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice) funkci, která vytvoří `choice` objekt, který vybírá mezi tři blokům zpráv. V příkladu pak vypočítá různých Fibonacciho čísel a uloží každého výsledku v bloku jiná zpráva. Příklad poté tiskne na konzolu zprávu, která je založena na operaci, který byl dokončen jako první.

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

Tento příklad vytvoří následující ukázkový výstup:

```Output
fib35 received its value first. Result = 9227465
```

Protože úloha, která vypočítá 35<sup>th</sup> Fibonacciho číslo není zaručeno, že nejdřív na dokončení, výstup tohoto příkladu se může lišit.

V tomto příkladu [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus pro výpočet čísla Fibonacciho paralelně. Další informace o `parallel_invoke`, naleznete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

Úplný příklad, který ukazuje způsob použití `choice` najdete v tématu [postupy: výběr mezi dokončené úkoly](../../parallel/concrt/how-to-select-among-completed-tasks.md).

[[Horní](#top)]

##  <a name="join"></a> Třídy JOIN a multitype_join

[Concurrency::join](../../parallel/concrt/reference/join-class.md) a [concurrency::multitype_join](../../parallel/concrt/reference/multitype-join-class.md) třídy umožňují čekat pro každého člena sady zdrojů pro příjem zprávy. `join` Třídy funguje na zdrojové objekty, které mají společný typ zprávy. `multitype_join` Třídy funguje na zdrojové objekty, které mohou mít různé typy zpráv.

Čtení ze služby `join` nebo `multitype_join` volání funkce rozhraní Windows API vypadá podobně jako objekt `WaitForMultipleObjects` když má `bWaitAll` parametr nastaven na `TRUE`. Nicméně, stejně jako `choice` objektu, `join` a `multitype_join` objektů použít událost mechanismus, který váže data na samotné místo události objektu externího synchronizace.

Čtení ze služby `join` objekt vytváří std::[vektoru](../../standard-library/vector-class.md) objektu. Čtení ze služby `multitype_join` objekt vytváří std::[řazené kolekce členů](../../standard-library/tuple-class.md) objektu. Prvky se zobrazí tyto objekty ve stejném pořadí jako jejich odpovídající zdrojové vyrovnávací paměti jsou spojeny s `join` nebo `multitype_join` objektu. Protože pořadí, ve které spojí zdrojová vyrovnávací paměti pro `join` nebo `multitype_join` objekt je přidružený pořadí prvků ve výsledné `vector` nebo `tuple` objektu, doporučujeme vám, že není odpojit existující zdrojová vyrovnávací paměť z Připojte se k. To může způsobit neurčené chování.

### <a name="greedy-versus-non-greedy-joins"></a>Porovnání spojení typu Greedy a Non-Greedy

`join` a `multitype_join` třídy podporují koncept greedy a bez metody greedy spojení. A *greedy spojení* přijímá zprávy ze všech zdrojů, jakmile zprávy budou k dispozici, dokud všechny zprávy nejsou k dispozici. A *spojení typu non-greedy* přijímá zprávy ve dvou fázích. Spojení typu non-greedy nejprve počká, až je k dispozici pro zprávy ze všech zdrojů. Za druhé po všech zpráv zdroje jsou k dispozici, spojení typu non-greedy pokusí rezervovat jednotlivé zprávy. Pokud si můžete rezervovat každou zprávu, zpracovává všechny zprávy a rozšíří je na cíli. V opačném případě ji vyjde nová verze, nebo zruší rezervace zprávy a znovu čeká na všechny zdroje při příjmu zprávy.

Greedy spojení poskytují vyšší výkon než spojení typu non-greedy, protože okamžitě přijetí zprávy. Ve výjimečných případech ale greedy spojení může vést k zablokování. Spojení typu non-greedy používejte, pokud máte více spojení, které obsahují jeden nebo více objektů sdílené zdroje.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní struktura o tom, jak pracovat `join` třídy. V tomto příkladu [concurrency::make_join](reference/concurrency-namespace-functions.md#make_join) funkci, která vytvoří `join` objekt, který přijme ze tří `single_assignment` objekty. Tento příklad vypočítá různých Fibonacciho čísel, ukládá každého výsledku v jiné `single_assignment` objekt a potom vypíše do konzoly každý výsledek, který `join` objekt obsahuje. Tento příklad je podobné jako v příkladu pro `choice` třídy s výjimkou, že `join` třídy čeká na všechny zdrojové bloky zpráv při příjmu zprávy.

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

Tento příklad vytvoří následující výstup:

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

V tomto příkladu [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus pro výpočet čísla Fibonacciho paralelně. Další informace o `parallel_invoke`, naleznete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

Kompletní příklady, které ukazují, jak používat `join` najdete v tématu [postupy: výběr mezi dokončené úkoly](../../parallel/concrt/how-to-select-among-completed-tasks.md) a [návod: použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

[[Horní](#top)]

##  <a name="timer"></a> Timer – třída

Souběžnost::[třída timer](../../parallel/concrt/reference/timer-class.md) slouží jako zdroj zprávy. A `timer` objektu po uplynutí určité zadané době odešle zprávu do cíle. `timer` Třídy je užitečné, když musíte zpoždění odesílání zprávy nebo chcete odesílání zpráv v pravidelných intervalech.

`timer` Třídy odešle zprávu s jeho pouze jeden cíl. Pokud nastavíte `_PTarget` parametr v konstruktoru `NULL`, cíl můžete zadat později pomocí volání [concurrency::ISource::link_target](reference/source-block-class.md#link_target) metody.

A `timer` objektu můžete opakující se nebo bez opakování. Chcete-li vytvořit opakující se časovač, předejte **true** pro `_Repeating` parametru při volání konstruktoru. Jinak předejte **false** pro `_Repeating` parametr k vytvoření časovače bez opakování. Pokud se opakuje časovač, pošle stejná zpráva k cíli po každém intervalu.

Knihovna agentů vytvoří `timer` objekty ve stavu-started. Chcete-li spustit objekt časovače, zavolejte [concurrency::timer::start](reference/timer-class.md#start) metody. Zastavit `timer` objektu, zničit objekt nebo volání [concurrency::timer::stop](reference/timer-class.md#stop) metody. Chcete-li pozastavit opakující se časovač, zavolejte [concurrency::timer::pause](reference/timer-class.md#pause) metody.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní struktura o tom, jak pracovat `timer` třídy. V příkladu `timer` a `call` objekty vykazovat průběh déletrvající operace.

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

Tento příklad vytvoří následující ukázkový výstup:

```Output
Computing fib(42)..................................................result is 267914296
```

Úplný příklad, který ukazuje způsob použití `timer` najdete v tématu [postupy: odesílání zpráv v pravidelných intervalech](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md).

[[Horní](#top)]

##  <a name="filtering"></a> Filtrování zpráv

Když vytvoříte objekt blok zpráv, můžete zadat *funkce filtrování* , který určuje, zda blok zpráv přijme nebo odmítne zprávy. Funkce filtru je užitečný způsob, jak zajistit, že blok zpráv přijme jenom konkrétní hodnoty.

Následující příklad ukazuje, jak vytvořit `unbounded_buffer` objekt, který používá funkce filtru tak, aby přijímal pouze sudá čísla. `unbounded_buffer` Objekt odmítne lichých čísel a proto nešíří lichá čísla na jeho cílovým blokům.

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

Tento příklad vytvoří následující výstup:

```Output
0 2 4 6 8
```

Funkce filtru může být funkce lambda, ukazatele na funkci nebo objektu funkce. Každá funkce filtru má jednu z následujících forem.

```Output
bool (T)
bool (T const &)
```

Chcete-li odstranit zbytečnému kopírování dat, používejte druhý formulář, pokud máte agregační typ, který se šíří podle hodnoty.

Podporuje filtrování zpráv *toku dat* programovací model, ve kterém součásti provádí výpočty při jejich přijímat data. Příklady, které používají funkce filtru pro řízení toku dat v síti předávání zpráv, najdete v článku [postupy: použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md), [návod: vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md), a [ Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Horní](#top)]

##  <a name="reservation"></a> Rezervace zprávy

*Rezervace zprávy* umožňuje bloku zprávy vyhradit zprávu pro pozdější použití. Rezervace zprávy se obvykle nepoužívá přímo. Vysvětlení zpráv rezervace vám mohou pomoci při lepší však pochopit chování některé typy bloků předdefinovaných zpráv.

Vezměte v úvahu spojení typu non-greedy a metodou greedy. Obě tyto rezervace zprávy použijte rezervovat zprávy pro pozdější použití. Je popsáno výše, spojení typu non-greedy přijímá zprávy ve dvou fázích. Během první fáze, bez metody greedy `join` každý z jeho zdroje při příjmu zprávy čeká objekt. Spojení typu non-greedy se pak pokusí rezervovat jednotlivé zprávy. Pokud si můžete rezervovat každou zprávu, zpracovává všechny zprávy a rozšíří je na cíli. V opačném případě ji vyjde nová verze, nebo zruší rezervace zprávy a znovu čeká na všechny zdroje při příjmu zprávy.

Číst další zprávy počká na příjem zprávy z každého zdroje pomocí greedy spojení, které také přečte vstupní zprávy z mnoha různých zdrojů, rezervace zprávy. Představte si třeba greedy spojení, která přijímá zprávy z blokům zpráv `A` a `B`. Pokud greedy spojení obdrží dvě zprávy z B, ale nebyl dosud obdržel zprávu od `A`, greedy spojení uloží zpráva jedinečný identifikátor pro druhé zprávy z `B`. Po spojení greedy přijme zprávu z `A` a rozšíří na tyto zprávy používá identifikátor uložené zprávy zobrazíte, pokud druhá zpráva z `B` je stále k dispozici.

Rezervace zprávy můžete použít, Pokud implementujete vlastní typy bloků zpráv vlastní. Příklad, jak vytvořit typ bloku vlastní zprávy, naleznete v tématu [návod: vytvoření vlastního bloku zpráv](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md).

[[Horní](#top)]

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)

