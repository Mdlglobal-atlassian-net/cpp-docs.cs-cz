---
title: Asynchronní bloky zpráv | Microsoft Docs
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
ms.openlocfilehash: 5de4a9ed20e20c03f44f8b8d421a628f220099f7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="asynchronous-message-blocks"></a>Asynchronní bloky zpráv

Knihovna agentů poskytuje několik typů bloku zpráv, které vám umožní šířit zpráv mezi součástmi aplikace způsobem bezpečné pro přístup z více vláken. Tyto typy bloku zpráv se často používají s různými rutiny předávání zpráv, jako například [concurrency::send](reference/concurrency-namespace-functions.md#send), [concurrency::asend](reference/concurrency-namespace-functions.md#asend), [concurrency::receive](reference/concurrency-namespace-functions.md#receive), a [concurrency::try_receive](reference/concurrency-namespace-functions.md#try_receive). Další informace o usnadnění rutiny, které jsou definovány knihovna agentů najdete v tématu [funkce předávání zpráv](../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="top"></a> Oddíly  
 Toto téma obsahuje následující oddíly:  
  
- [Zdroje a cíle](#sources_and_targets)  
  
- [Šíření zpráv](#propagation)  
  
- [Přehled typů bloku zpráv](#overview)  
  
- [Třída unbounded_buffer](#unbounded_buffer)  
  
- [overwrite_buffer – třída](#overwrite_buffer)  
  
- [single_assignment – třída](#single_assignment)  
  
- [call – třída](#call)  
  
- [transformer – třída](#transformer)  
  
- [choice – třída](#choice)  
  
- [spojování a multitype_join třídy](#join)  
  
- [timer – třída](#timer)  
  
- [Filtrování zpráv](#filtering)  
  
- [Rezervace zpráv](#reservation)  
  
##  <a name="sources_and_targets"></a> Zdroje a cíle  
 Zdroje a cíle jsou dvě důležité účastníky v předávání zpráv. A *zdroj* odkazuje na koncový bod komunikaci, která odesílá zprávy. A *cíl* odkazuje na koncový bod komunikace, která přijímá zprávy. Si můžete představit jako koncový bod, který můžete číst od zdroj a cíl jako koncový bod, který zapsat do. Aplikace připojit zdroje a cíle společně na formulář *zasílání zpráv na úrovni sítě*.  
  
 Knihovna agentů používá dva abstraktní třídy, které představují zdroje a cíle: [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) a [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md). Blok zpráv typy které působí jako zdroje jsou odvozeny od `ISource`; bloku zpráv typy které působí jako cíle odvozena od `ITarget`. Blok zpráv typy které působí jako zdroje a cíle odvozena z obou `ISource` a `ITarget`.  
  
 [[Horní](#top)]  
  
##  <a name="propagation"></a> Šíření zpráv  
 *Zpráva šíření* spočívá v odeslání zprávy z jedné součásti. Když blok zpráv se nabízí zprávu, může přijmout, odmítnout nebo odložit této zprávě. Každý typ bloku zpráv ukládá a odesílá zprávy různými způsoby. Například `unbounded_buffer` třída ukládá neomezený počet zpráv, `overwrite_buffer` třída ukládá do jedné zprávy najednou a třídy transformer ukládá změnit verzi každou zprávu. Tyto typy bloku zpráv jsou podrobněji popsané v dále v tomto dokumentu.  
  
 Pokud zpráva blok přijme zprávu, může volitelně práci a, pokud je zdroj, bloku zpráv předat výsledného na druhý člen sítě. Blok zpráv vám pomůže odmítnout zprávy, které pro příjem nechce funkce filtru. Filtry jsou podrobněji popsané v dále v tomto tématu v části [filtrování zpráv](#filtering). Blok zpráv, který odloží zprávu můžete vyhradit zprávy a později ho využívají. Zpráva rezervace je podrobněji popsané v dále v tomto tématu v části [zpráva rezervace](#reservation).  
  
 Knihovna agentů povolí bloky zpráv pro asynchronní nebo synchronně předávání zpráv. Pokud předáte zprávu pro message block synchronně, například pomocí `send` funkce, modul runtime blokuje aktuální kontext dokud cílový blok přijme nebo odmítne zprávy. Pokud předáte zprávu pro message block asynchronně, například pomocí `asend` funkce, modul runtime nabízí zprávy do cílové a pokud cíl přijímá zprávy, modul runtime plány asynchronní úkol, který rozšíří zprávy k příjemce. Prosté úlohy používá modul runtime potřebný k šíření zprávy spolupráci způsobem. Další informace o prosté úlohy najdete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  

 Aplikace zdroje a cíle vzájemně propojit a formulář zasílání zpráv na úrovni sítě. Obvykle propojení sítí a volání `send` nebo `asend` k předávání dat k síti. Pro připojení blok zpráv zdroje na cíl, volání [concurrency::ISource::link_target](reference/isource-class.md#link_target) metoda. Chcete-li odpojit blok zdroj cíl, volejte [concurrency::ISource::unlink_target](reference/isource-class.md#unlink_target) metoda. Chcete-li odpojit blok zdroje ze všech svých cílů, volejte [concurrency::ISource::unlink_targets](reference/isource-class.md#unlink_targets) metoda. Pokud jeden z typů bloku předdefinované zpráva opustí rozsah nebo zničena, se automaticky odpojí samotné ze všech bloků, cíl. Některé typy bloku zpráv omezit maximální počet cílů, které může zapsat do. Následující část popisuje omezení, které platí pro typ bloku předdefinované zprávy.  
  
 [[Horní](#top)]  
  
##  <a name="overview"></a> Přehled typů bloku zpráv  
 Následující tabulka stručně popisuje roli typů důležité bloku zpráv.  
  
 [unbounded_buffer](#unbounded_buffer)  
 Ukládá fronty zpráv.  
  
 [overwrite_buffer](#overwrite_buffer)  
 Ukládá jednu zprávu, která může zapisovat do a čtení z více než jednou.  
  
 [single_assignment](#single_assignment)  
 Ukládá jednu zprávu, která může zapisovat do jednou a číst z více než jednou.  
  
 [Volání](#call)  
 Provede práci, když obdrží zprávu.  
  
 [Transformer](#transformer)  
 Provede práci při přijetí dat a odešle výsledek svou práci na jiný cílový blok. `transformer` Třída může fungovat na jinou vstupní a výstupní typy.  
  
 [Volba](#choice)  
 Vybere první dostupné zprávu ze sady zdrojů.  
  
 [spojování a multitype spojení](#join)  
 Počkejte, než pro všechny zprávy chcete být přijata ze sady zdroje a pak zprávy do jedné zprávy pro jiného bloku zpráv.  
  
 [Časovač](#timer)  
 Odešle zprávu do cílový blok v pravidelných intervalech.  
  
 Tyto typy bloku zpráv mají různými charakteristikami, díky kterým užitečné pro různé situace. Toto jsou některé z vlastností:  
  
- *Propagace typu*: jestli bloku zpráv slouží jako zdroj dat, příjemce dat nebo oba.  
  
- *Řazení zpráv*: jestli bloku zpráv udržuje původní pořadí, ve kterém jsou zprávy odesílané nebo přijímané. Každý typ bloku předdefinované zprávy udržuje původní pořadí, ve kterém odeslání nebo přijetí zprávy.  
  
- *Zdroj počet*: maximální počet zdrojů, které bloku zpráv může číst z.  
  
- *Cíl počet*: maximální počet cílů, které bloku zpráv může zapsat do.  
  
 Následující tabulka ukazuje, jak tyto vlastnosti se vztahují na různé typy bloku zpráv.  
  
|Typ bloku zpráv|Propagace typu (zdrojový, cílový nebo obojí)|Zpráva řazení (objednáno nebo Unordered)|Počet zdroje|Cílový počet|  
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|  
|`unbounded_buffer`|Obě|řazení|bez vazby|bez vazby|  
|`overwrite_buffer`|Obě|řazení|bez vazby|bez vazby|  
|`single_assignment`|Obě|řazení|bez vazby|bez vazby|  
|`call`|cíl|řazení|bez vazby|Není k dispozici|  
|`transformer`|Obě|řazení|bez vazby|1|  
|`choice`|Obě|řazení|10|1|  
|`join`|Obě|řazení|bez vazby|1|  
|`multitype_join`|Obě|řazení|10|1|  
|`timer`|Zdroj|Není k dispozici|Není k dispozici|1|  
  
 Následující části popisují typy bloku zpráv podrobněji.  
  
 [[Horní](#top)]  
  
##  <a name="unbounded_buffer"></a> Třída unbounded_buffer  
 [Concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) třída reprezentuje strukturou univerzální asynchronní zasílání zpráv. Tato třída ukládá první v první out (FIFO) fronty zpráv, které mohou být zápis více zdrojů nebo číst z více cílů. Když cíl obdrží zprávu od `unbounded_buffer` objektu zpráva, že je odebrána z fronty zpráv. Proto i když `unbounded_buffer` objekt může mít více cílů, pouze jeden cíl obdrží každou zprávu. `unbounded_buffer` Třída je užitečná, když chcete předat více zpráv na jiné komponenty, a tuto součást musí obdržet každou zprávu.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, využít základní strukturu jak pracovat s `unbounded_buffer` třídy. Tento příklad odešle tři hodnoty `unbounded_buffer` objekt a potom načte tyto hodnoty zpátky do stejného objektu.  
  
 [!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
334455  
```  
  
 Úplný příklad, který ukazuje způsob použití `unbounded_buffer` třídy najdete v tématu [postupy: implementace různých vzorů typu výrobce-spotřebitel](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).  
  
 [[Horní](#top)]  
  
##  <a name="overwrite_buffer"></a> Třída overwrite_buffer  
 [Concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) vypadá takto: Třída `unbounded_buffer` třídy, vyjma toho, že `overwrite_buffer` objekt ukládá jenom jednu zprávu. Kromě toho, když cíl obdrží zprávu od `overwrite_buffer` objektu, zprávy se neodebere z vyrovnávací paměti. Proto více cílů obdrží kopii zprávy.  
  
 `overwrite_buffer` Třída je užitečné, když chcete předat více zpráv na jiné komponenty, ale je potřeba tuto součást pouze nejnovější hodnotu. Tato třída je také užitečné, pokud chcete k vysílání zprávy, která se víc součástí.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, využít základní strukturu jak pracovat s `overwrite_buffer` třídy. Tento příklad odešle tři hodnoty `overwrite _buffer` objekt a potom načte aktuální hodnotu ze stejného objektu třikrát. V tomto příkladu je podobná na příklad `unbounded_buffer` třídy. Ale `overwrite_buffer` třída ukládá jenom jednu zprávu. Kromě toho modul runtime neodebere zpráv ze `overwrite_buffer` objektu po je pro čtení.  
  
 [!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
555555  
```  
  
 Úplný příklad, který ukazuje způsob použití `overwrite_buffer` třídy najdete v tématu [postupy: implementace různých vzorů typu výrobce-spotřebitel](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).  
  
 [[Horní](#top)]  
  
##  <a name="single_assignment"></a> Třída single_assignment  
 [Concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) vypadá takto: Třída `overwrite_buffer` třídy, vyjma toho, že `single_assignment` objektu je možné zapsat do pouze jednou. Podobně jako `overwrite_buffer` třída, když cíl obdrží zprávu od `single_assignment` objektu, zprávy se neodebere z tohoto objektu. Proto více cílů obdrží kopii zprávy. `single_assignment` Třída je užitečná, pokud chcete vysílání jednu zprávu více součástí.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, využít základní strukturu jak pracovat s `single_assignment` třídy. Tento příklad odešle tři hodnoty `single_assignment` objekt a potom načte aktuální hodnotu ze stejného objektu třikrát. V tomto příkladu je podobná na příklad `overwrite_buffer` třídy. I když obě `overwrite_buffer` a `single_assignment` třídy ukládat do jedné zprávy `single_assignment` třídy je možné zapsat do pouze jednou.  
  
 [!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
333333  
```  
  
 Úplný příklad, který ukazuje způsob použití `single_assignment` třídy najdete v tématu [návod: implementace tříd Future](../../parallel/concrt/walkthrough-implementing-futures.md).  
  
 [[Horní](#top)]  
  
##  <a name="call"></a> Call – třída  
 [Concurrency::call](../../parallel/concrt/reference/call-class.md) třída slouží jako zprávy příjemce, který provádí funkce pracovní, když obdrží data. Tato funkce pracovní může být výraz lambda, objekt funkce nebo ukazatel na funkci. A `call` objekt chová jinak než volání běžné funkce, protože funguje to paralelně s ostatními součástmi, které odesílat zprávy. Pokud `call` objekt provádí pracovní, když obdrží zprávu, přidá zprávy do fronty. Každý `call` objekt procesy zpráv v pořadí, ve kterém jsou přijaty zařazených do fronty.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, využít základní strukturu jak pracovat s `call` třídy. Tento příklad vytvoří `call` objekt, který vytiskne každou hodnotu, která obdrží ke konzole. Příklad pošle tři hodnoty `call` objektu. Protože `call` objekt zpracovává zprávy v samostatné vlákno, tento příklad také používá proměnnou čítače a [událostí](../../parallel/concrt/reference/event-class.md) objekt, který má zajistit, aby `call` objekt zpracovává všechny zprávy před `wmain` Funkce vrátí.  
  
 [!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
334455  
```  
  
 Úplný příklad, který ukazuje způsob použití `call` třídy najdete v tématu [postupy: poskytování pracovních funkcí třídám call a transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md).  
  
 [[Horní](#top)]  
  
##  <a name="transformer"></a> Třída Transformer  
 [Concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) třída slouží jako obou příjemce zpráv a jako odesílatele zprávy. `transformer` Vypadá takto: Třída `call` třídy, protože provádí uživatelsky definované funkce pracovní, když obdrží data. Ale `transformer` třída rovněž odesílá výsledek pracovní funkce k příjemce objekty. Podobně jako `call` objekt, `transformer` objekt funguje to paralelně s ostatními součástmi, které odesílat zprávy. Pokud `transformer` objekt provádí pracovní, když obdrží zprávu, přidá zprávy do fronty. Každý `transformer` objekt zpracovává jeho zprávy ve frontě v pořadí, ve kterém jsou přijaty.  
  
 `transformer` Třída odešle jeho zprávu jeden cíl. Pokud nastavíte `_PTarget` parametr v konstruktoru `NULL`, můžete později zadat cílový voláním [concurrency::link_target](reference/source-block-class.md#link_target) metoda.  
  
 Na rozdíl od všechny ostatní typy bloku z asynchronní zprávy, které jsou poskytovány knihovna agentů `transformer` třída může fungovat na jinou vstupní a výstupní typy. Tato schopnost transformovat data z jednoho typu na jiný díky `transformer` třídy klíčovou komponentou v mnoha souběžných sítích. Kromě toho můžete přidat další podrobných paralelní funkce v pracovní funkce `transformer` objektu.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, využít základní strukturu jak pracovat s `transformer` třídy. Tento příklad vytvoří `transformer` objektu, že vstup násobky každý `int` hodnoty 0.33, aby bylo možné vytvořit `double` hodnotu jako výstup. V příkladu pak obdrží transformovaných hodnoty ze stejné `transformer` objektu a vypíše je do konzoly.  
  
 [!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
10.8914.5218.15  
```  
  
 Úplný příklad, který ukazuje způsob použití `transformer` třídy najdete v tématu [postupy: použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).  
  
 [[Horní](#top)]  
  
##  <a name="choice"></a> Třída Choice  
 [Concurrency::choice](../../parallel/concrt/reference/choice-class.md) třída vybere první dostupné zprávu ze sady zdrojů. `choice` Třída reprezentuje mechanismus tok řízení místo mechanismus toku dat (tématu [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) popisuje rozdíly mezi toku dat a řízení toku).  
  
 Čtení z výběru objektu se podobá volání funkce rozhraní API systému Windows `WaitForMultipleObjects` Pokud je `bWaitAll` parametr nastaven na `FALSE`. Ale `choice` třída váže dat k samotné místo události do objektu externí synchronizace.  
  

 Obvykle se používá `choice` třídy společně s [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkce k řízení toku řízení ve vaší aplikaci. Použití `choice` třídy při výběru mezi vyrovnávacích pamětí zpráv, které mají různé typy. Použití `single_assignment` při výběru mezi vyrovnávacích pamětí zpráv, které mají stejný typ třídy.  

  
 Pořadí, ve kterém můžete propojit zdrojů `choice` objektu je důležité, protože můžete určit, zpráv, které je vybrána. Představte si třeba tento případ, kdy propojit několik vyrovnávacích pamětí zpráv, obsahující zprávu, která se `choice` objektu. `choice` Objekt vybere zprávy z první zdroj, který bude propojen. Po propojení všech zdrojů, `choice` objekt zachovává pořadí, ve kterém každý zdroj přijme zprávu o.  
  
### <a name="example"></a>Příklad  

 Následující příklad ukazuje, využít základní strukturu jak pracovat s `choice` třídy. Tento příklad používá [concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice) funkce k vytvoření `choice` objekt, který vybere mezi tři bloky zpráv. V příkladu pak vypočítá různé Fibonacciho čísla a ukládá každý výsledek v bloku jiná zpráva. Ke konzole příklad potom zobrazí zprávu, která je založena na operaci, která se nejdřív dokončení.  

  
 [!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
fib35 received its value first. Result = 9227465  
```  
  
 Protože úloha, která vypočítá 35<sup>tý</sup> Fibonacciho číslo není zaručena nejdřív na dokončení, výstup tohoto příkladu se může lišit.  
  

 Tento příklad používá [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus vypočítat čísla Fibonacciho paralelně. Další informace o `parallel_invoke`, najdete v části [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
 Úplný příklad, který ukazuje způsob použití `choice` třídy najdete v tématu [postup: Vyberte mezi dokončení úlohy](../../parallel/concrt/how-to-select-among-completed-tasks.md).  
  
 [[Horní](#top)]  
  
##  <a name="join"></a> spojování a multitype_join třídy  
 [Concurrency::join](../../parallel/concrt/reference/join-class.md) a [concurrency::multitype_join](../../parallel/concrt/reference/multitype-join-class.md) třídy umožňují čekat na každého člena sady zdrojů pro příjem zprávy. `join` Třída slouží na zdrojové objekty, které mají společné typ zprávy. `multitype_join` Třída slouží na objekty zdrojů, které může mít různé typy zpráv.  
  
 Čtení z `join` nebo `multitype_join` objekt vypadá takto: volání funkce rozhraní API systému Windows `WaitForMultipleObjects` Pokud je `bWaitAll` parametr nastaven na `TRUE`. Ale stejně jako `choice` objekt, `join` a `multitype_join` objekty používají mechanismus událostí, který váže dat k samotné místo události do objektu externí synchronizace.  
  
 Čtení z `join` objekt vytváří std::[vektoru](../../standard-library/vector-class.md) objektu. Čtení z `multitype_join` objekt vytváří std::[řazené kolekce členů](../../standard-library/tuple-class.md) objektu. Prvky objeví v tyto objekty ve stejném pořadí jako propojeno s jejich odpovídající zdrojové vyrovnávací paměti `join` nebo `multitype_join` objektu. Protože pořadí, ve kterém můžete propojit zdroje ukládá do vyrovnávací paměti na `join` nebo `multitype_join` objekt je přidružený ke pořadí prvků v výsledná `vector` nebo `tuple` objektu, doporučujeme vám, že není odpojit existující zdrojová vyrovnávací paměť z spojení. Díky tomu může mít za následek neurčené chování.  
  
### <a name="greedy-versus-non-greedy-joins"></a>Porovnání spojení typu Greedy a Non-Greedy  
 `join` a `multitype_join` třídy podporují koncept spojení typu greedy a typu non-greedy. A *spojení typu greedy* přijme zprávu z každé její zdroje, jakmile zprávy k dispozici, dokud všechny zprávy jsou k dispozici. A *spojení typu non-greedy* přijímá zprávy ve dvou fázích. Spojení typu non-greedy nejprve počká, až nabízený zprávu z každé její zdroje. Za druhé po všechny zprávy zdroji jsou k dispozici, spojení typu non-greedy pokusí vyhradit jednotlivé zprávy. Pokud je můžete vyhradit každou zprávu, využívá všechny zprávy a rozšiřuje je na cíli. Jinak hodnota ho uvolní, nebo zruší, rezervace zprávu a opakujte pro každý zdroj pro příjem zprávy počká.  
  
 Spojení typu greedy provést lépe než spojení typu non-greedy, protože zprávy přijímají okamžitě. Ve výjimečných případech, ale spojení typu greedy může vést k zablokování. Spojení typu non-greedy použijte, pokud máte více spojení, které obsahují jeden nebo více objektů sdílené zdroje.  
  
### <a name="example"></a>Příklad  

 Následující příklad ukazuje, využít základní strukturu jak pracovat s `join` třídy. Tento příklad používá [concurrency::make_join](reference/concurrency-namespace-functions.md#make_join) funkce k vytvoření `join` objekt, který přijme ze tří `single_assignment` objekty. Tento příklad vypočítá různé Fibonacciho čísla, ukládá každý výsledek v jiné `single_assignment` objekt a potom výtisků do konzoly každý způsobit `join` objektu blokování. Tato ukázka je podobné jako v příkladu pro `choice` třídy, vyjma toho, že `join` třída čeká na všechny bloky zpráv zdroje pro příjem zprávy.  
  
 [!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008  
```  

 Tento příklad používá [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus vypočítat čísla Fibonacciho paralelně. Další informace o `parallel_invoke`, najdete v části [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
 Pro dokončení příklady, které ukazují, jak používat `join` třídy najdete v tématu [postup: Vyberte mezi dokončit úkoly](../../parallel/concrt/how-to-select-among-completed-tasks.md) a [návod: použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).  
  
 [[Horní](#top)]  
  
##  <a name="timer"></a> Třída Timer  
 Souběžnost::[timer – třída](../../parallel/concrt/reference/timer-class.md) slouží jako zdroj zprávy. A `timer` objekt odešle zprávu do atribut target po uplynutí zadaném časovém období. `timer` Třída je užitečné, když musíte zpoždění odesílání zprávy nebo chcete odeslat zprávu v pravidelných intervalech.  
  

 `timer` Třída odešle jeho zprávu právě jeden cíl. Pokud nastavíte `_PTarget` parametr v konstruktoru `NULL`, můžete později zadat cílový voláním [concurrency::ISource::link_target](reference/source-block-class.md#link_target) metoda.  

  
 A `timer` objekt můžete s opakováním nebo bez opakování. Chcete-li vytvořit opakovaných časovač, předat `true` pro `_Repeating` parametr při volání konstruktoru. Jinak, předá `false` pro `_Repeating` parametr k vytvoření časovač bez opakování. Pokud je s opakováním časovač se odešle po každém intervalu stejná zpráva k cíli.  
  
 Knihovna agentů vytvoří `timer` objekty ve stavu-started. Chcete-li spustit časovač objektu, volejte [concurrency::timer::start](reference/timer-class.md#start) metoda. Zastavení `timer` objektu, destroy objekt nebo volání [concurrency::timer::stop](reference/timer-class.md#stop) metoda. Pozastavit opakovaných časovač, volání [concurrency::timer::pause](reference/timer-class.md#pause) metoda.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, využít základní strukturu jak pracovat s `timer` třídy. Tento příklad používá `timer` a `call` objekty, které chcete hlášení průběhu časově náročná operace.  
  
 [!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
Computing fib(42)..................................................result is 267914296  
```  
  
 Úplný příklad, který ukazuje způsob použití `timer` třídy najdete v tématu [postupy: odesílání zpráv v pravidelných intervalech](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md).  
  
 [[Horní](#top)]  
  
##  <a name="filtering"></a> Filtrování zpráv  
 Když vytvoříte objekt bloku zpráv, můžete zadat *filtrovat funkce* který určuje, zda blok zprávu přijme nebo odmítne zprávy. Funkce filtru je užitečný způsob, jak zajistit, že blok zpráv přijímá jenom určité hodnoty.  
  
 Následující příklad ukazuje, jak vytvořit `unbounded_buffer` objekt, který používá funkce filtru tak, aby přijímal pouze sudá čísla. `unbounded_buffer` Objekt odmítne liché čísla a proto nešířily liché čísla, která se jeho cíl bloky.  
  
 [!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
0 2 4 6 8  
```  
  
 Funkce filtru může být funkce lambda, ukazatel na funkci nebo funkce objektu. Všechny funkce filtru přebírá jednu z následujících podob.  
  
```Output  
bool (T)  
bool (T const &)  
```  
  
 K vyloučení nepotřebných kopírování dat, použijte druhý formulář až budete mít typ agregace, který je rozšířena podle hodnoty.  
  
 Filtrování podporuje zpráv *toku dat* programovací model, ve kterém součásti provádět výpočty při jejich přijímat data. Příklady, které používají funkce filtru k řízení toku dat v síti předávání zpráv najdete v tématu [postupy: použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md), [návod: vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md), a [ Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 [[Horní](#top)]  
  
##  <a name="reservation"></a> Rezervace zpráv  
 *Zpráva rezervace* umožňuje blok zpráv tak, aby vyhradil zprávu pro pozdější použití. Rezervace zpráva se obvykle nepoužívá přímo. Ale Principy zpráva rezervace vám může pomoci lépe pochopit chování některé typy bloku předdefinované zprávy.  
  
 Zvažte spojení typu non-greedy a typu greedy. Obě tyto zprávy rezervace použijte tak, aby vyhradil zprávy pro pozdější použití. Popsané výše, spojení typu non-greedy přijímá zprávy ve dvou fázích. Během první fáze, typu non-greedy `join` objekt čeká na každý z jeho zdrojů pro příjem zprávy. Spojení typu non-greedy pokusí tak, aby vyhradil jednotlivé zprávy. Pokud je můžete vyhradit každou zprávu, využívá všechny zprávy a rozšiřuje je na cíli. Jinak hodnota ho uvolní, nebo zruší, rezervace zprávu a opakujte pro každý zdroj pro příjem zprávy počká.  
  
 Spojení typu greedy, který čte také vstupní zprávy z mnoha různých zdrojů, používá rezervace zprávu přečíst další zprávy během čekání na příjem zprávy z jednotlivých zdrojů. Zvažte například spojení typu greedy, která přijímá zprávy od bloky zpráv `A` a `B`. Pokud spojení typu greedy obdrží dvě zprávy z B, ale ještě neobdržel zprávu od `A`, spojení typu greedy uloží zprávu jedinečný identifikátor pro o druhou zprávu z `B`. Po spojení typu greedy obdrží zprávu od `A` a šíří se tyto zprávy používá identifikátor uložené zprávy pro případ, druhá zpráva od `B` je stále k dispozici.  
  
 Rezervace zprávu můžete použít při implementaci vlastních typů bloku vlastní zprávu. Příklad o tom, jak vytvořit vlastní zprávu typ bloku, naleznete v části [návod: vytvoření vlastního bloku zpráv](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md).  
  
 [[Horní](#top)]  
  
## <a name="see-also"></a>Viz také  
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)

