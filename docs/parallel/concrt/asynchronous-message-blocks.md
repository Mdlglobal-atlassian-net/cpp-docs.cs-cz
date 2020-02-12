---
title: Asynchronní bloky zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
ms.openlocfilehash: ef6f6f56a82cc76c2c270817ed40d15418960dc1
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141957"
---
# <a name="asynchronous-message-blocks"></a>Asynchronní bloky zpráv

Knihovna agentů poskytuje několik typů bloků zpráv, které umožňují šířit zprávy mezi součástmi aplikace v bezpečném vlákně. Tyto typy bloku zpráv jsou často používány s různými rutinami předávání zpráv, například [Concurrency:: Send](reference/concurrency-namespace-functions.md#send), [Concurrency:: asend](reference/concurrency-namespace-functions.md#asend), [Concurrency:: receive](reference/concurrency-namespace-functions.md#receive)a [Concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive). Další informace o rutinách předávání zpráv, které jsou definovány knihovnou agentů, najdete v tématu [funkce předávání zpráv](../../parallel/concrt/message-passing-functions.md).

## <a name="top"></a>Řezů

Toto téma obsahuje následující oddíly:

- [Zdroje a cíle](#sources_and_targets)

- [Šíření zpráv](#propagation)

- [Přehled typů bloků zpráv](#overview)

- [unbounded_buffer – třída](#unbounded_buffer)

- [overwrite_buffer – třída](#overwrite_buffer)

- [single_assignment – třída](#single_assignment)

- [call – třída](#call)

- [transformer – třída](#transformer)

- [choice – třída](#choice)

- [Třídy JOIN a multitype_join](#join)

- [timer – třída](#timer)

- [Filtrování zpráv](#filtering)

- [Rezervace zprávy](#reservation)

## <a name="sources_and_targets"></a>Zdroje a cíle

Zdroje a cíle jsou dva důležité účastníky předávání zpráv. *Zdroj* odkazuje na koncový bod komunikace, který odesílá zprávy. *Cíl* odkazuje na koncový bod komunikace, který přijímá zprávy. Zdroj můžete představit jako koncový bod, který načtete z a cíl jako koncový bod, do kterého zapisujete. Aplikace spojují zdroje a cíle dohromady a tvoří *sítě pro zasílání zpráv*.

Knihovna agentů používá dvě abstraktní třídy, které reprezentují zdroje a cíle: [Concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) a [Concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md). Typy bloků zpráv, které fungují jako zdroje odvozené od `ISource`; typy bloků zpráv, které fungují jako cíle, jsou odvozeny od `ITarget`. Typy bloků zpráv, které fungují jako zdroje a cíle, jsou odvozeny z `ISource` i `ITarget`.

[[Nahoře](#top)]

## <a name="propagation"></a>Šíření zpráv

*Šíření zpráv* je operace odeslání zprávy z jedné součásti do druhé. Když je v bloku zprávy nabízená zpráva, může tuto zprávu přijmout, odmítnout nebo odložit. Každý typ bloku zprávy ukládá a odesílá zprávy různými způsoby. Například třída `unbounded_buffer` ukládá neomezený počet zpráv, třída `overwrite_buffer` ukládá vždy jednu zprávu a třída Transformer ukládá změněnou verzi každé zprávy. Tyto typy bloků zpráv jsou podrobněji popsány dále v tomto dokumentu.

Když blok zprávy přijme zprávu, může volitelně provést práci, a pokud je blok zprávy zdrojem, předejte výslednou zprávu jinému členovi sítě. Blok zpráv může pomocí funkce filtru odmítat zprávy, které nechce přijímat. Filtry jsou podrobněji popsané dále v tomto tématu v části [filtrování zpráv](#filtering). Blok zpráv, který odloží zprávu, může tuto zprávu vyhradit a později ji spotřebovat. Rezervace zpráv je podrobněji popsána dále v tomto tématu v části [rezervace zpráv](#reservation).

Knihovna agentů umožňuje blokům zpráv asynchronně nebo synchronně předávat zprávy. Pokud předáte zprávu do bloku zprávy synchronně, například pomocí funkce `send`, modul runtime zablokuje aktuální kontext, dokud cílový blok buď nepřijme nebo odmítne zprávu. Při asynchronním předání zprávy do bloku zprávy, například pomocí funkce `asend`, modul runtime nabídne zprávu cíli a pokud cíl zprávu přijme, modul runtime naplánuje asynchronní úlohu, která šíří zprávu do přijímače. Modul runtime používá ke společnému šíření zpráv zjednodušené úlohy. Další informace o odlehčených úlohách najdete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Aplikace spojují zdroje a cíle dohromady a tvoří sítě pro zasílání zpráv. Obvykle propojíte síť a zavoláte `send` nebo `asend` a předáte data do sítě. Chcete-li připojit blok zdrojové zprávy k cíli, zavolejte metodu [Concurrency:: ISource:: link_target](reference/isource-class.md#link_target) . Chcete-li odpojit zdrojový blok od cíle, zavolejte metodu [Concurrency:: ISource:: unlink_target](reference/isource-class.md#unlink_target) . Chcete-li odpojit zdrojový blok od všech svých cílů, zavolejte metodu [Concurrency:: ISource:: unlink_targets](reference/isource-class.md#unlink_targets) . Když některý z předdefinovaných typů bloků zpráv opustí rozsah nebo je zničen, automaticky se odpojí ze všech cílových bloků. Některé typy bloků zpráv omezují maximální počet cílů, do kterých můžou zapisovat. V následující části jsou popsána omezení, která se vztahují na předdefinované typy bloků zpráv.

[[Nahoře](#top)]

## <a name="overview"></a>Přehled typů bloků zpráv

Následující tabulka stručně popisuje roli důležitých typů bloku zpráv.

[unbounded_buffer](#unbounded_buffer)<br/>
Ukládá frontu zpráv.

[overwrite_buffer](#overwrite_buffer)<br/>
Ukládá jednu zprávu, na kterou lze zapisovat a číst z více než jednou.

[single_assignment](#single_assignment)<br/>
Ukládá jednu zprávu, která může být jednou zapsána a čtena několikrát.

[volání](#call)<br/>
Provede práci, když obdrží zprávu.

[Transformer](#transformer)<br/>
Provede práci, když přijme data a pošle výsledek této práce do jiného cílového bloku. Třída `transformer` může pracovat s různými typy vstupu a výstupu.

[libovolném](#choice)<br/>
Vybírá první dostupnou zprávu ze sady zdrojů.

[spojení a spojení s více typy](#join)<br/>
Počkejte, až budou všechny zprávy přijaty ze sady zdrojů, a pak tyto zprávy sloučí do jedné zprávy pro další blok zpráv.

[ukládání](#timer)<br/>
Odešle zprávu do cílového bloku v pravidelných intervalech.

Tyto typy bloku zpráv mají různé charakteristiky, které je vhodným způsobem vydávat v různých situacích. Jedná se o některé vlastnosti:

- *Typ šíření*: Určuje, zda blok zprávy funguje jako zdroj dat, přijímač dat nebo obojí.

- *Řazení zpráv*: Určuje, zda blok zpráv uchovává původní pořadí, ve kterém jsou zprávy odesílány nebo přijímány. Každý předdefinovaný typ bloku zprávy udržuje původní pořadí, ve kterém odesílá nebo přijímá zprávy.

- *Počet zdrojů*: maximální počet zdrojů, ze kterých může blok zpráv číst.

- *Počet*cílů: maximální počet cílů, do kterých může blok zpráv zapisovat.

Následující tabulka ukazuje, jak se tyto charakteristiky vztahují k různým typům bloku zpráv.

|Typ bloku zprávy|Typ šíření (zdroj, cíl nebo obojí)|Řazení zpráv (seřazené nebo neuspořádané)|Počet zdrojů|Počet cílů|
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|
|`unbounded_buffer`|Obojí|Objednáno|Unbounded|Unbounded|
|`overwrite_buffer`|Obojí|Objednáno|Unbounded|Unbounded|
|`single_assignment`|Obojí|Objednáno|Unbounded|Unbounded|
|`call`|Cíl|Objednáno|Unbounded|Nepoužitelné|
|`transformer`|Obojí|Objednáno|Unbounded|1|
|`choice`|Obojí|Objednáno|10|1|
|`join`|Obojí|Objednáno|Unbounded|1|
|`multitype_join`|Obojí|Objednáno|10|1|
|`timer`|Zdroj|Nepoužitelné|Nepoužitelné|1|

V následujících částech jsou popsány typy bloku zpráv podrobněji.

[[Nahoře](#top)]

## <a name="unbounded_buffer"></a>unbounded_buffer – třída

Třída [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) představuje strukturu asynchronního zasílání zpráv pro obecné účely. Tato třída ukládá do fronty první v, první ven (FIFO) zprávy, na které může zapisovat více zdrojů nebo číst z více cílů. Když cíl obdrží zprávu z objektu `unbounded_buffer`, tato zpráva se odebere z fronty zpráv. Proto i když objekt `unbounded_buffer` může mít více cílů, obdrží každou zprávu pouze jeden cíl. Třída `unbounded_buffer` je užitečná v případě, že chcete předat více zpráv jiné komponentě a tato součást musí přijmout každou zprávu.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu, jak pracovat s třídou `unbounded_buffer`. Tento příklad odešle tři hodnoty do objektu `unbounded_buffer` a pak tyto hodnoty přečte ze stejného objektu.

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

Tento příklad vytvoří následující výstup:

```Output
334455
```

Kompletní příklad, který ukazuje, jak použít třídu `unbounded_buffer`, naleznete v tématu [How to: Implementing různých způsobů producent-Consumer](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Nahoře](#top)]

## <a name="overwrite_buffer"></a>overwrite_buffer – třída

Třída [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) se podobá třídě `unbounded_buffer`, s tím rozdílem, že objekt `overwrite_buffer` ukládá pouze jednu zprávu. Kromě toho, když cíl obdrží zprávu z objektu `overwrite_buffer`, tato zpráva není odebrána z vyrovnávací paměti. Proto více cílů obdrží kopii zprávy.

Třída `overwrite_buffer` je užitečná v případě, že chcete předat více zpráv jiné komponentě, ale komponenta potřebuje pouze nejnovější hodnotu. Tato třída je užitečná také v případě, že chcete vysílat zprávu na více součástí.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu, jak pracovat s třídou `overwrite_buffer`. Tento příklad odešle tři hodnoty do objektu `overwrite _buffer` a potom přečte aktuální hodnotu ze stejného objektu třikrát. Tento příklad je podobný příkladu pro třídu `unbounded_buffer`. Nicméně třída `overwrite_buffer` ukládá pouze jednu zprávu. Kromě toho modul runtime neodstraní zprávu z `overwrite_buffer` objektu po jeho čtení.

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

Tento příklad vytvoří následující výstup:

```Output
555555
```

Kompletní příklad, který ukazuje, jak použít třídu `overwrite_buffer`, naleznete v tématu [How to: Implementing různých způsobů producent-Consumer](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Nahoře](#top)]

## <a name="single_assignment"></a>single_assignment – Třída

Třída [Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) se podobá třídě `overwrite_buffer`, s tím rozdílem, že objekt `single_assignment` lze zapsat pouze jednorázově. Podobně jako třída `overwrite_buffer`, když cíl obdrží zprávu z objektu `single_assignment`, tato zpráva není odebrána z tohoto objektu. Proto více cílů obdrží kopii zprávy. Třída `single_assignment` je užitečná v případě, že chcete vysílat jednu zprávu na více součástí.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu, jak pracovat s třídou `single_assignment`. Tento příklad odešle tři hodnoty do objektu `single_assignment` a potom přečte aktuální hodnotu ze stejného objektu třikrát. Tento příklad je podobný příkladu pro třídu `overwrite_buffer`. I když třídy `overwrite_buffer` i `single_assignment` ukládají jednu zprávu, třída `single_assignment` může být zapsána pouze jednorázově.

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

Tento příklad vytvoří následující výstup:

```Output
333333
```

Kompletní příklad, který ukazuje použití třídy `single_assignment`, naleznete v tématu [Návod: implementace futures](../../parallel/concrt/walkthrough-implementing-futures.md).

[[Nahoře](#top)]

## <a name="call"></a>Call – třída

Třída [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) funguje jako přijímač zpráv, který při přijímání dat provádí pracovní funkci. Tato pracovní funkce může být výraz lambda, objekt funkce nebo ukazatel na funkci. Objekt `call` se chová jinak než běžné volání funkce, protože funguje paralelně s jinými součástmi, které do ní odesílají zprávy. Pokud objekt `call` provádí práci, když obdrží zprávu, přidá tuto zprávu do fronty. Každý objekt `call` zpracovává zprávy ve frontě v pořadí, ve kterém byly přijaty.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu, jak pracovat s třídou `call`. Tento příklad vytvoří objekt `call`, který vytiskne všechny hodnoty, které obdrží do konzoly. Příklad následně odešle tři hodnoty do objektu `call`. Vzhledem k tomu, že objekt `call` zpracovává zprávy v samostatném vlákně, tento příklad také používá proměnnou čítače a objekt [události](../../parallel/concrt/reference/event-class.md) , aby bylo zajištěno, že objekt `call` zpracovává všechny zprávy před vrácením funkce `wmain`.

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

Tento příklad vytvoří následující výstup:

```Output
334455
```

Kompletní příklad, který ukazuje, jak použít třídu `call`, naleznete v tématu [How to: Function Working a Transformer Classes](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md).

[[Nahoře](#top)]

## <a name="transformer"></a>Transformer – třída

Třída [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) funguje jako příjemce zprávy i jako odesilatel zprávy. Třída `transformer` se podobá `call` třídy, protože při přijímání dat provádí uživatelsky definovanou pracovní funkci. Nicméně třída `transformer` také odesílá výsledek pracovní funkce do objektů přijímače. Podobně jako objekt `call`, objekt `transformer` pracuje paralelně s jinými komponentami, které jim odesílají zprávy. Pokud objekt `transformer` provádí práci, když obdrží zprávu, přidá tuto zprávu do fronty. Každý objekt `transformer` zpracovává své zprávy ve frontě v pořadí, ve kterém byly přijaty.

Třída `transformer` odesílá zprávu do jednoho cíle. Pokud nastavíte parametr `_PTarget` v konstruktoru tak, aby `NULL`, můžete později zadat cíl voláním metody [Concurrency:: link_target](reference/source-block-class.md#link_target) .

Na rozdíl od všech ostatních typů asynchronních bloků zpráv, které jsou k dispozici v knihovně agenti, třída `transformer` může pracovat s různými typy vstupu a výstupu. Tato schopnost transformovat data z jednoho typu na jiný vytvoří `transformer` třídy klíč a klíčovou komponentou v mnoha současných sítích. Kromě toho můžete přidat další jemně odstupňované paralelní funkce v pracovní funkci objektu `transformer`.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu, jak pracovat s třídou `transformer`. Tento příklad vytvoří objekt `transformer`, který vynásobí každý vstup `int` hodnotou 0,33, aby se vytvořila hodnota `double` jako výstup. Příklad poté obdrží transformované hodnoty ze stejného `transformer` objektu a vytiskne je do konzoly.

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

Tento příklad vytvoří následující výstup:

```Output
10.8914.5218.15
```

Kompletní příklad, který ukazuje, jak použít třídu `transformer`, naleznete v tématu [How to: use in a Transformer in a data Pipeline](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

[[Nahoře](#top)]

## <a name="choice"></a>Choice – třída

Třída [Concurrency:: Choice](../../parallel/concrt/reference/choice-class.md) vybírá první dostupnou zprávu ze sady zdrojů. Třída `choice` představuje mechanismus toku řízení namísto mechanismu toku dat (téma [knihovny asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) popisuje rozdíly mezi tokem dat a tok řízení).

Čtení z objektu Choice se podobá volání funkce rozhraní Windows API `WaitForMultipleObjects`, když má `bWaitAll` parametr nastaven na `FALSE`. Třída `choice` však váže data pouze k události samotné, nikoli k externímu objektu synchronizace.

Obvykle používáte třídu `choice` společně s funkcí [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) k řízení toku řízení v aplikaci. Třídu `choice` použijte v případě, že je nutné vybrat mezi vyrovnávacími pamětmi zpráv, které mají různé typy. Třídu `single_assignment` použijte v případě, že je nutné vybrat mezi vyrovnávacími pamětmi zpráv, které mají stejný typ.

Pořadí, ve kterém propojíte zdroje s objektem `choice`, je důležité, protože může určit, která zpráva je vybrána. Zvažte například případ, kdy propojíte více vyrovnávacích pamětí zpráv, které již obsahují zprávu pro objekt `choice`. Objekt `choice` vybere zprávu z prvního zdroje, ke kterému je propojena. Po propojení všech zdrojů objekt `choice` zachovává pořadí, ve kterém každý zdroj obdrží zprávu.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu, jak pracovat s třídou `choice`. Tento příklad používá funkci [Concurrency:: make_choice](reference/concurrency-namespace-functions.md#make_choice) k vytvoření objektu `choice`, který vybírá ze tří bloků zpráv. Příklad pak vypočítá různá Fibonacci čísla a uloží každý výsledek do jiného bloku zpráv. V příkladu se pak v konzole vytiskne zpráva, která je založená na operaci, která se dokončila jako první.

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

Tento příklad vytvoří následující vzorový výstup:

```Output
fib35 received its value first. Result = 9227465
```

Vzhledem k tomu, že není zaručeno dokončení úlohy, která<sup>vypočítá 35 Fibonacci</sup> číslo, může se výstup tohoto příkladu lišit.

V tomto příkladu se používá algoritmus [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) k výpočtu čísel Fibonacci paralelně. Další informace o `parallel_invoke`najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

Kompletní příklad, který ukazuje, jak použít třídu `choice`, naleznete v tématu [How to: SELECT mezi dokončenými úkoly](../../parallel/concrt/how-to-select-among-completed-tasks.md).

[[Nahoře](#top)]

## <a name="join"></a>Třídy JOIN a multitype_join

Třídy [Concurrency:: JOIN](../../parallel/concrt/reference/join-class.md) a [concurrency:: multitype_join](../../parallel/concrt/reference/multitype-join-class.md) umožňují počkat, až každý člen sady zdrojů získá zprávu. Třída `join` pracuje na zdrojových objektech, které mají společný typ zprávy. Třída `multitype_join` pracuje se zdrojovými objekty, které mohou mít různé typy zpráv.

Čtení z `join` nebo `multitype_join` objektu se podobá volání funkce rozhraní API systému Windows `WaitForMultipleObjects`, pokud má parametr `bWaitAll` nastaven na `TRUE`. Stejně jako objekt `choice`, `join` a `multitype_join` objekty však používají mechanismus události, který váže data pouze k události samotné místo na externí objekt synchronizace.

Čtení z `join` objektu vytvoří objekt std::[Vector](../../standard-library/vector-class.md) . Čtení z `multitype_join` objektu vytvoří objekt std::[Tuple](../../standard-library/tuple-class.md) . Prvky se zobrazí v těchto objektech ve stejném pořadí, ve kterém jsou příslušné zdrojové vyrovnávací paměti propojeny s objektem `join` nebo `multitype_join`. Vzhledem k tomu, že pořadí, ve kterém propojíte zdrojové vyrovnávací paměti s `join` nebo `multitype_join` objekt je přidruženo k pořadí prvků ve výsledném objektu `vector` nebo `tuple`, doporučujeme nezrušit propojení existující zdrojové vyrovnávací paměti od spojení. V důsledku toho může dojít k nespecifikovanému chování.

### <a name="greedy-versus-non-greedy-joins"></a>Porovnání spojení typu Greedy a Non-Greedy

Třídy `join` a `multitype_join` podporují koncept hladového a nehladého spojení. *Připojení hladce* přijme zprávu z každého ze svých zdrojů, protože zprávy budou k dispozici, dokud nebudou k dispozici všechny zprávy. *Připojení bez hladce* přijímá zprávy ve dvou fázích. Nejprve nehladící spojení počká, dokud nebude nabídnuta zpráva z každého ze svých zdrojů. Za druhé, jakmile budou k dispozici všechny zdrojové zprávy, pokusy o nevizuální spojení si vyhradí každou z těchto zpráv. Pokud může každá zpráva vyhradit, spotřebovává všechny zprávy a šíří je do cíle. V opačném případě uvolní nebo zruší rezervace zpráv a znovu počká, až každý zdroj obdrží zprávu.

Hladové spojení provádí lepší spojení než nehladové spojení, protože přijímá zprávy okamžitě. Ve výjimečných případech však hladové spojení může vést k zablokování. Použijte nehladec JOIN, pokud máte více spojení, která obsahují jeden nebo více sdílených zdrojových objektů.

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu, jak pracovat s třídou `join`. V tomto příkladu se používá funkce [Concurrency:: make_join](reference/concurrency-namespace-functions.md#make_join) k vytvoření objektu `join`, který přijímá tři objekty `single_assignment`. V tomto příkladu jsou vypočítána různá Fibonacci čísla, ukládají se každý výsledek do jiného objektu `single_assignment` a potom se vytisknou do konzoly každý výsledek, že objekt `join` obsahuje. Tento příklad je podobný příkladu pro třídu `choice`, s tím rozdílem, že třída `join` počká, až všechny zdrojové bloky zpráv obdrží zprávu.

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

Tento příklad vytvoří následující výstup:

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

V tomto příkladu se používá algoritmus [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) k výpočtu čísel Fibonacci paralelně. Další informace o `parallel_invoke`najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

Kompletní příklady, které ukazují, jak používat třídu `join`, naleznete v tématu [How to: SELECT for dokončených Tasks](../../parallel/concrt/how-to-select-among-completed-tasks.md) and [Názorný postup: použití funkce Join k zabránění zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

[[Nahoře](#top)]

## <a name="timer"></a>Timer – třída

Třída concurrency::[Timer](../../parallel/concrt/reference/timer-class.md) funguje jako zdroj zprávy. Objekt `timer` odešle zprávu cíli po uplynutí zadaného časového období. Třída `timer` je užitečná v případě, že je nutné zpozdit odeslání zprávy nebo chcete poslat zprávu v pravidelných intervalech.

Třída `timer` odesílá zprávu pouze do jednoho cíle. Pokud nastavíte parametr `_PTarget` v konstruktoru tak, aby `NULL`, můžete později zadat cíl voláním metody [Concurrency:: ISource:: link_target](reference/source-block-class.md#link_target) .

Objekt `timer` může být opakující se nebo bez opakování. Chcete-li vytvořit opakovaný časovač, předejte **hodnotu true** pro parametr `_Repeating` při volání konstruktoru. V opačném případě předejte **hodnotu false** pro parametr `_Repeating` pro vytvoření časovače bez opakování. Pokud se časovač opakuje, pošle stejnou zprávu na cíl po každém intervalu.

Knihovna agentů vytvoří objekty `timer` v nespuštěném stavu. Chcete-li spustit objekt časovače, zavolejte metodu [Concurrency:: Timer:: Start](reference/timer-class.md#start) . Chcete-li zastavit objekt `timer`, zničení objektu nebo volání metody [Concurrency:: Timer:: stop](reference/timer-class.md#stop) . Pro pozastavení opakujícího se časovače volejte metodu [Concurrency:: Timer::p Ause](reference/timer-class.md#pause) .

### <a name="example"></a>Příklad

Následující příklad ukazuje základní strukturu, jak pracovat s třídou `timer`. V příkladu se používá `timer` a `call` objektů k hlášení průběhu operace s zdlouhavou operací.

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

Tento příklad vytvoří následující vzorový výstup:

```Output
Computing fib(42)..................................................result is 267914296
```

Kompletní příklad, který ukazuje, jak použít třídu `timer`, naleznete v tématu [How to: Send a Message v pravidelných intervalech](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md).

[[Nahoře](#top)]

## <a name="filtering"></a>Filtrování zpráv

Při vytváření objektu bloku zprávy můžete zadat *funkci filtru* , která určuje, zda blok zpráv přijímá nebo odmítá zprávu. Funkce filtru je užitečný způsob, jak zaručit, že blok zpráv přijímá pouze určité hodnoty.

Následující příklad ukazuje, jak vytvořit objekt `unbounded_buffer`, který používá funkci filtru pro příjem pouze sudých čísel. Objekt `unbounded_buffer` odmítne lichá čísla, a proto nerozšíří lichá čísla do cílových bloků.

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

Tento příklad vytvoří následující výstup:

```Output
0 2 4 6 8
```

Funkce Filter může být funkce lambda, ukazatel na funkci nebo objekt funkce. Každá funkce filtru používá jednu z následujících forem.

```Output
bool (T)
bool (T const &)
```

Chcete-li odstranit zbytečné kopírování dat, použijte druhý formulář, pokud máte agregovaný typ, který je šířen hodnotou.

Filtrování zpráv podporuje model programování *toku* dat, ve kterém komponenty provádějí výpočty při přijímání dat. Příklady použití funkcí filtrování k řízení toku dat v síti s předáváním zpráv naleznete v tématu [How to: Use a Filter Block Message Filter](../../parallel/concrt/how-to-use-a-message-block-filter.md), [Návod: Vytvoření agenta toku](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)dat a [Návod: vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Nahoře](#top)]

## <a name="reservation"></a>Rezervace zprávy

*Rezervace zprávy* umožňuje bloku zpráv rezervovat zprávu pro pozdější použití. Obvykle se rezervace zprávy nepoužívá přímo. Pochopení rezervací zpráv vám ale pomůže lépe porozumět chování některých předdefinovaných typů bloků zpráv.

Zvažte nehladové a hladové spojení. Obě tyto zprávy používají rezervaci pro vyhradení zpráv pro pozdější použití. Výše popsaná zpráva bez hladového připojení přijímá zprávy ve dvou fázích. V první fázi nehladec `join` objekt počká, až každý ze svých zdrojů dostanou zprávu. Nehladé spojení se pak pokusí vyhradit každou z těchto zpráv. Pokud může každá zpráva vyhradit, spotřebovává všechny zprávy a šíří je do cíle. V opačném případě uvolní nebo zruší rezervace zpráv a znovu počká, až každý zdroj obdrží zprávu.

Připojení hladce, které také čte vstupní zprávy z řady zdrojů, používá rezervaci zprávy ke čtení dalších zpráv, když čeká na přijetí zprávy z jednotlivých zdrojů. Představte si třeba připojení hladce, které přijímá zprávy z bloků zpráv `A` a `B`. Pokud připojení hladce obdrží dvě zprávy z B, ale ještě neobdržela zprávu od `A`, hladce JOIN uloží jedinečný identifikátor zprávy pro druhou zprávu z `B`. Po připojení hladce obdrží zprávu od `A` a rozšíří tyto zprávy, pomocí uloženého identifikátoru zprávy zjistíte, jestli je stále dostupná druhá zpráva z `B`.

Můžete použít rezervaci zprávy při implementaci vlastních typů bloků zpráv. Příklad vytvoření vlastního typu bloku zprávy naleznete v tématu [Návod: Vytvoření vlastního bloku zpráv](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md).

[[Nahoře](#top)]

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)
