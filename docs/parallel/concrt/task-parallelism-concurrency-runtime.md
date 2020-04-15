---
title: Funkční paralelismus (Concurrency Runtime)
ms.date: 11/04/2016
helpviewer_keywords:
- structured task groups [Concurrency Runtime]
- structured tasks [Concurrency Runtime]
- task groups [Concurrency Runtime]
- task parallelism
- tasks [Concurrency Runtime]
ms.assetid: 42f05ac3-2098-494a-ba84-737fcdcad077
ms.openlocfilehash: f65521771db3eb0fe19dc863b1b49e9627fc60e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368593"
---
# <a name="task-parallelism-concurrency-runtime"></a>Funkční paralelismus (Concurrency Runtime)

V souběžném běhu je *úloha* jednotkou práce, která provádí určitou úlohu a obvykle běží paralelně s jinými úkoly. Úkol lze rozložit na další, podrobnější úkoly, které jsou uspořádány do *skupiny úkolů*.

Úlohy se používají při psaní asynchronního kódu a chcete, aby po dokončení asynchronní operace došlo k určité operaci. Můžete například použít úlohu k asynchronnímu čtení ze souboru a potom použít jinou úlohu – *úlohu pokračování*, která je vysvětlena dále v tomto dokumentu – ke zpracování dat poté, co budou k dispozici. Naopak můžete pomocí skupin úkolů rozložit paralelní práci na menší části. Předpokládejme například, že máte rekurzivní algoritmus, který rozděluje zbývající práci do dvou oddílů. Skupiny úloh můžete použít ke spuštění těchto oddílů současně a potom počkejte na dokončení rozdělené práce.

> [!TIP]
> Pokud chcete použít stejnou rutinu pro každý prvek kolekce paralelně, použijte paralelní algoritmus, jako je [například souběžnost::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), namísto úkolu nebo skupiny úkolů. Další informace o paralelních algoritmech naleznete [v tématu Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

## <a name="key-points"></a>Klíčové body

- Při předání proměnných výrazu lambda odkazem, musíte zaručit, že životnost této proměnné přetrvává až do dokončení úkolu.

- Při psaní asynchronního kódu použijte úkoly [(souběžnost::třída úloh).](../../parallel/concrt/reference/task-class.md) Třída úlohpoužívá jako plánovač fond Windows ThreadPool, nikoli souběžnost runtime.

- Pomocí skupin úloh [(souběžnost::task_group](reference/task-group-class.md) třídy nebo [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus) pokud chcete rozložit paralelní práci na menší části a pak čekat na dokončení těchto menších kusů.

- Použijte [souběžnost::task::then](reference/task-class.md#then) metodu k vytvoření pokračování. *Pokračování* je úloha, která je spuštěna asynchronně po dokončení jiné úlohy. Můžete připojit libovolný počet pokračování tvořit řetězec asynchronní práce.

- Pokračování založené na úlohách je vždy naplánováno pro spuštění po dokončení předchozí úlohy, i když je předchozí úloha zrušena nebo vyvolá výjimku.

- [Souběžnost::when_all](reference/concurrency-namespace-functions.md#when_all) slouží k vytvoření úkolu, který se dokončí po dokončení každého člena sady úkolů. [Souběžnost::when_any](reference/concurrency-namespace-functions.md#when_any) slouží k vytvoření úkolu, který se dokončí po dokončení jednoho člena sady úkolů.

- Úkoly a skupiny úkolů se mohou účastnit mechanismu zrušení knihovny paralelních vzorů (PPL). Další informace naleznete [v tématu Zrušení v ppl](cancellation-in-the-ppl.md).

- Chcete-li zjistit, jak runtime zpracovává výjimky, které jsou vyvolány úkoly a skupinami úkolů, naleznete v [tématu Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="in-this-document"></a>V tomto dokumentu

- [Používání výrazů lambda](#lambdas)

- [Třída úkolu](#task-class)

- [Úkoly pokračování](#continuations)

- [Pokračování založená na hodnotách versus na základě úloh](#value-versus-task)

- [Skládání úkolů](#composing-tasks)

  - [Funkce when_all](#when-all)

  - [Funkce when_any](#when-any)

- [Zpožděné spuštění úlohy](#delayed-tasks)

- [Skupiny úloh](#task-groups)

- [Porovnání task_group s structured_task_group](#comparing-groups)

- [Příklad](#example)

- [Robustní programování](#robust)

## <a name="using-lambda-expressions"></a><a name="lambdas"></a>Použití výrazů Lambda

Z důvodu jejich stručné syntaxe jsou výrazy lambda běžným způsobem definování práce prováděné úkoly a skupinami úkolů. Zde je několik tipů pro použití:

- Vzhledem k tomu, že úlohy obvykle běží na vláknech na pozadí, uvědomte si životnost objektu při zachycení proměnných ve výrazech lambda. Při zachycení proměnné podle hodnoty je v těle lambda provedena kopie této proměnné. Při zachycení odkazem není provedena kopie. Proto ujistěte se, že životnost libovolné proměnné, kterou zachytíte odkazem outlives úlohy, která ji používá.

- Když předáte výraz lambda úkolu, nezachyťte proměnné, které jsou přiděleny v zásobníku odkazem.

- Buďte explicitní o proměnných, které zachytíte ve výrazech lambda, abyste mohli identifikovat, co zachycujete podle hodnoty, a podle odkazu. Z tohoto důvodu doporučujeme nepoužívat `[=]` `[&]` možnosti nebo pro výrazy lambda.

Běžným vzorem je, když jeden úkol v řetězci pokračování přiřadí proměnné a jiný úkol tuto proměnnou přečte. Nelze zachytit podle hodnoty, protože každá úloha pokračování by obsahovat jinou kopii proměnné. Pro proměnné přidělené zásobníku také nelze zachytit odkazem, protože proměnná již nemusí být platná.

Chcete-li tento problém vyřešit, použijte inteligentní ukazatel, například [std::shared_ptr](../../standard-library/shared-ptr-class.md), zabalit proměnnou a předat inteligentní ukazatel podle hodnoty. Tímto způsobem základní objekt lze přiřadit a číst z a přežije úkoly, které jej používají. Tuto techniku použijte i v případě, že proměnná`^`je ukazatel nebo popisovač s počítanou odkazem ( ) na objekt prostředí Windows Runtime. Tady je základní příklad:

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

Další informace o výrazech lambda naleznete v tématu [Lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

## <a name="the-task-class"></a><a name="task-class"></a>Třída úkolu

Třídu [souběžnosti::task](../../parallel/concrt/reference/task-class.md) můžete použít k vytvoření úkolů do sady závislých operací. Tento model složení je podpořen pojmem *pokračování*. Pokračování umožňuje spuštění kódu po dokončení předchozí nebo *předchozí*úlohy. Výsledek předchozí úlohy je předán jako vstup pro jeden nebo více úkolů pokračování. Po dokončení předchozí úlohy jsou všechny úlohy pokračování, které na ni čekají, naplánovány ke spuštění. Každá úloha pokračování obdrží kopii výsledku předchozí úlohy. Na druhé straně tyto úkoly pokračování může být také předchozí úkoly pro další pokračování, a tím vytvořit řetězec úkolů. Pokračování vám pomohou vytvořit libovolné délky řetězy úkolů, které mají specifické závislosti mezi nimi. Kromě toho se úkol může účastnit zrušení buď před zahájením úlohy, nebo kooperativním způsobem, když je spuštěn. Další informace o tomto modelu zrušení naleznete [v tématu Zrušení v PPL](cancellation-in-the-ppl.md).

`task`je šablona třídy. Parametr `T` type je typ výsledku, který je výsledkem úkolu. Tento typ `void` může být, pokud úkol nevrátí hodnotu. `T`nelze použít `const` modifikátor.

Při vytváření úkolu poskytujete *pracovní funkci,* která provádí tělo úkolu. Tato pracovní funkce je dodávána ve formě funkce lambda, ukazatele funkce nebo objektu funkce. Chcete-li čekat na dokončení úkolu bez získání výsledku, zavolejte metodu [concurrency::task::wait.](reference/task-class.md#wait) Metoda `task::wait` vrátí [souběžnost::task_status](reference/concurrency-namespace-enums.md#task_group_status) hodnotu, která popisuje, zda byl úkol dokončen nebo zrušen. Chcete-li získat výsledek úkolu, zavolejte metodu [concurrency::task:get.](reference/task-class.md#get) Tato metoda `task::wait` volá čekat na dokončení úlohy a proto blokuje provádění aktuálního vlákna, dokud není k dispozici výsledek.

Následující příklad ukazuje, jak vytvořit úkol, čekat na jeho výsledek a zobrazit jeho hodnotu. Příklady v této dokumentaci používají funkce lambda, protože poskytují stručnější syntaxi. Při použití úloh však můžete také použít ukazatele funkce a objekty funkce.

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

Při použití [funkce concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) můžete použít `auto` klíčové slovo namísto deklarování typu. Zvažte například tento kód, který vytvoří a vytiskne matici identity:

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

`create_task` Funkci můžete použít k vytvoření ekvivalentní operace.

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

Pokud je vyvolána výjimka během provádění úlohy, zařazuje `task::get` za `task::wait`běhu tuto výjimku v následném volání nebo nebo pokračování založené na úlohách. Další informace o mechanismu zpracování výjimek úlohy naleznete v [tématu Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Příklad, který `task`používá [, souběžnost::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), zrušení, naleznete [v tématu Návod: Připojení pomocí úloh a xml http požadavků](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). (Třída `task_completion_event` je popsána dále v tomto dokumentu.)

> [!TIP]
> Podrobnosti, které jsou specifické pro úkoly v aplikacích UPW, najdete [v tématu Asynchronní programování v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) a [vytváření asynchronních operací v jazyce C++ pro aplikace UPW](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

## <a name="continuation-tasks"></a><a name="continuations"></a>Úkoly pokračování

V asynchronním programování je velmi běžné, že jedna asynchronní operace po dokončení vyvolá druhou operaci a předá jí data. Tradičně se to provádí pomocí metod zpětného volání. V souběžnosti Runtime stejné funkce je poskytována *pokračování úlohy*. Úloha pokračování (označovaná také jako pokračování) je asynchronní úloha, která je vyvolána jinou úlohou, která se nazývá *předchůdce*, když se předchůdce dokončí. Pomocí pokračování můžete:

- Předá data z předchůdce pokračování.

- Určete přesné podmínky, za kterých je pokračování vyvoláno nebo není vyvoláno.

- Zrušte pokračování před spuštěním nebo kooperativně, když je spuštěn.

- Poskytněte rady o tom, jak by mělo být naplánováno pokračování. (To platí pouze pro aplikace platformy Universal Platform (UPW). Další informace naleznete v [tématu Vytváření asynchronních operací v jazyce C++ pro aplikace UPW](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).)

- Vyvolat více pokračování ze stejného předchůdce.

- Vyvolat jedno pokračování po dokončení všech nebo některý z více předchůdců.

- Řetěz pokračuje jeden po druhém na libovolnou délku.

- Použijte pokračování pro zpracování výjimek, které jsou vyvolány předchůdcem.

Tyto funkce umožňují provést jeden nebo více úkolů po dokončení první úlohy. Můžete například vytvořit pokračování, které komprimuje soubor po první úloze, která jej přečte z disku.

Následující příklad upraví předchozí použít [souběžnost::task::then](reference/task-class.md#then) metoda naplánovat pokračování, které vytiskne hodnotu předchozí úlohy, když je k dispozici.

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

Úkoly můžete zřetězit a vnořit na libovolnou délku. Úloha může mít také více pokračování. Následující příklad ilustruje základní řetězec pokračování, který třikrát zvětší hodnotu předchozího úkolu.

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

Pokračování může také vrátit jiný úkol. Pokud není zrušení, pak tento úkol je proveden před následné pokračování. Tato technika se označuje jako *asynchronní rozbalování*. Asynchronní rozbalení je užitečné, pokud chcete provést další práci na pozadí, ale nechcete, aby aktuální úloha blokovala aktuální vlákno. (To je běžné v aplikacích UPW, kde pokračování lze spustit ve vlákně uživatelského rozhraní). Následující příklad ukazuje tři úkoly. První úloha vrátí jinou úlohu, která je spuštěna před pokračováním úlohy.

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
> Pokud pokračování úkolu vrátí vnořenou `N`úlohu typu , má `N`výsledná úloha typ , nikoli `task<N>`a po dokončení vnořené úlohy se dokončí. Jinými slovy pokračování provádí rozbalování vnořené úlohy.

## <a name="value-based-versus-task-based-continuations"></a><a name="value-versus-task"></a>Pokračování založená na hodnotách versus na základě úloh

Daný `task` objekt, jehož `T`návratový typ je `T` , `task<T>` můžete zadat hodnotu typu nebo jeho pokračování úkoly. Pokračování, které `T` přebírá typ, se označuje jako *pokračování založené na hodnotě*. Pokračování založené na hodnotě je naplánováno pro spuštění, když předchozí úloha dokončí bez chyby a není zrušena. Pokračování, které `task<T>` bere typ jako jeho parametr se označuje jako *pokračování založené na úlohách*. Pokračování založené na úlohách je vždy naplánováno pro spuštění po dokončení předchozí úlohy, i když je předchozí úloha zrušena nebo vyvolá výjimku. Potom můžete `task::get` volat získat výsledek předchozí úlohy. Pokud byla předchozí úloha zrušena, `task::get` vyvolá [souběžnost::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). Pokud předchozí úloha vyvolala `task::get` výjimku, znovu vyvolá tuto výjimku. Pokračování založené na úlohách není označeno jako zrušeno, pokud je jeho předchozí úloha zrušena.

## <a name="composing-tasks"></a><a name="composing-tasks"></a>Skládání úkolů

Tato část popisuje [souběžnost::when_all](reference/concurrency-namespace-functions.md#when_all) a [souběžnost::when_any](reference/concurrency-namespace-functions.md#when_all) funkce, které vám pomohou vytvořit více úkolů k implementaci běžných vzorů.

### <a name="the-when_all-function"></a><a name="when-all"></a>Funkce when_all

Funkce `when_all` vytvoří úkol, který se dokončí po dokončení sady úkolů. Tato funkce vrátí std::[vektorový](../../standard-library/vector-class.md) objekt, který obsahuje výsledek každého úkolu v sadě. Následující základní příklad `when_all` používá k vytvoření úkolu, který představuje dokončení tří dalších úkolů.

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
> Úkoly, které `when_all` předáte, musí být jednotné. Jinými slovy, všechny musí vrátit stejný typ.

`&&` Syntaxi můžete také použít k vytvoření úkolu, který se dokončí po dokončení sady úkolů, jak je znázorněno v následujícím příkladu.

`auto t = t1 && t2; // same as when_all`

Je běžné použít pokračování spolu `when_all` s provést akci po dokončení sady úkolů. Následující příklad upraví předchozí vytisknout součet tří úkolů, které `int` každý výsledek.

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

V tomto příkladu můžete `task<vector<int>>` také určit, chcete-li vytvořit pokračování založené na úlohách.

Pokud je některý úkol v sadě úkolů zrušen nebo `when_all` vyvolá výjimku, okamžitě se dokončí a nečeká na dokončení zbývajících úkolů. Pokud je vyvolána výjimka, runtime znovu vyvolá `task::get` výjimku při volání nebo `task::wait` na objekt úlohy, který `when_all` vrátí. Pokud více než jeden úkol vyvolá, runtime vybere jeden z nich. Proto ujistěte se, že dodržovat všechny výjimky po dokončení všech úkolů; výjimka neošetřené úlohy způsobí ukončení aplikace.

Zde je nástrojová funkce, kterou můžete použít k zajištění toho, aby váš program dodržoval všechny výjimky. Pro každý úkol v zadaný rozsah aktivuje všechny výjimky, `observe_all_exceptions` ke kterým došlo k opětovnému vyvolání a potom pozveden tuto výjimku.

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

Zvažte aplikaci UPW, která používá C++ a XAML a zapíše sadu souborů na disk. Následující příklad ukazuje, `when_all` jak `observe_all_exceptions` používat a zajistit, aby program dodržuje všechny výjimky.

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>Spuštění tohoto příkladu

1. V souboru MainPage.xaml přidejte `Button` ovládací prvek.

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. V MainPage.xaml.h přidejte tyto forward `private` deklarace `MainPage` do části deklarace třídy.

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. V souboru MainPage.xaml.cpp implementujte obslužnou rutinu `Button_Click` události.

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. V MainPage.xaml.cpp `WriteFilesAsync` implementujte, jak je znázorněno v příkladu.

> [!TIP]
> `when_all`je neblokující funkce, která `task` vytváří jako jeho výsledek. Na rozdíl od [task::wait](reference/task-class.md#wait), je bezpečné volat tuto funkci v aplikaci UPW ve vlákně ASTA (Application STA).

### <a name="the-when_any-function"></a><a name="when-any"></a>Funkce when_any

Funkce `when_any` vytvoří úkol, který se dokončí po dokončení prvního úkolu v sadě úkolů. Tato funkce vrátí [std::pair](../../standard-library/pair-structure.md) objekt, který obsahuje výsledek dokončené úlohy a index této úlohy v sadě.

Funkce `when_any` je užitečná zejména v následujících scénářích:

- Nadbytečné operace. Zvažte algoritmus nebo operaci, které lze provést mnoha způsoby. Pomocí `when_any` funkce můžete vybrat operaci, která se dokončí jako první, a potom zrušit zbývající operace.

- Prokládané operace. Můžete spustit více operací, které musí `when_any` všechny dokončit a použít funkci ke zpracování výsledků při dokončení každé operace. Po dokončení jedné operace můžete spustit jednu nebo více dalších úloh.

- Omezené operace. `when_any` Funkci můžete použít k rozšíření předchozího scénáře omezením počtu souběžných operací.

- Operace, jejichž platnost vypršela. `when_any` Pomocí této funkce můžete vybrat mezi jedním nebo více úkoly a úkolem, který bude dokončen po určitém čase.

Stejně `when_all`jako u , je běžné `when_any` použít pokračování, které má provést akci při dokončení první v sadě úkolů. Následující základní příklad `when_any` používá k vytvoření úkolu, který se dokončí po dokončení první ze tří dalších úkolů.

[!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]

V tomto příkladu můžete `task<pair<int, size_t>>` také určit, chcete-li vytvořit pokračování založené na úlohách.

> [!NOTE]
> Stejně `when_all`jako u , `when_any` úkoly, které předáte, musí všechny vrátit stejný typ.

`||` Syntaxi můžete také použít k vytvoření úkolu, který se dokončí po dokončení první úlohy v sadě úkolů, jak je znázorněno v následujícím příkladu.

`auto t = t1 || t2; // same as when_any`

> [!TIP]
> Stejně `when_all` `when_any` jako u , je non-blocking a je bezpečné volat v aplikaci UPW na vlákno ASTA.

## <a name="delayed-task-execution"></a><a name="delayed-tasks"></a>Zpožděné spuštění úlohy

Někdy je nutné odložit provádění úkolu, dokud není splněna podmínka, nebo spustit úkol v reakci na externí událost. Například v asynchronní programování může být možné spustit úlohu v reakci na událost dokončení vstupně-v..

Dva způsoby, jak toho dosáhnout, jsou použití pokračování nebo spuštění úkolu a čekání na událost uvnitř pracovní funkce úkolu. Existují však případy, kdy není možné použít jednu z těchto technik. Chcete-li například vytvořit pokračování, musíte mít předchozí úkol. Pokud však nemáte předchozí úkol, můžete vytvořit *událost dokončení úkolu* a později zřetězit událost dokončení na předchozí úkol, jakmile bude k dispozici. Kromě toho vzhledem k tomu, že čekající úloha také blokuje vlákno, můžete použít události dokončení úlohy k provedení práce po dokončení asynchronní operace a tím uvolnit vlákno.

[Souběžnost::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) třída pomáhá zjednodušit takové složení úkolů. Stejně `task` jako třída, `T` parametr typu je typ výsledku, který je vytvořen úkolem. Tento typ `void` může být, pokud úkol nevrátí hodnotu. `T`nelze použít `const` modifikátor. Objekt je `task_completion_event` obvykle k dispozici podprocesu nebo úkolu, který bude signalizovat, když je k dispozici hodnota pro něj. Současně jsou jako posluchače této události nastaveny jeden nebo více úloh. Když je událost nastavena, úlohy naslouchací proces uděláte a jejich pokračování jsou naplánovány ke spuštění.

Příklad, který `task_completion_event` se používá k implementaci úkolu, který se dokončí po zpoždění, najdete v tématu [Postup: Vytvoření úkolu, který se dokončí po zpoždění](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md).

## <a name="task-groups"></a><a name="task-groups"></a>Skupiny úkolů

*Skupina úkolů* uspořádá kolekci úkolů. Skupiny úkolů vysouvá úkoly do fronty krádeže práce. Plánovač odebere úlohy z této fronty a provede je na dostupných výpočetních prostředcích. Po přidání úkolů do skupiny úkolů můžete počkat na dokončení všech úkolů nebo zrušit úkoly, které ještě nebyly zahájeny.

PPL používá [souběžnost::task_group](reference/task-group-class.md) a [souběžnost::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) třídy představují skupiny úkolů a [třída concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md) představují úkoly, které jsou spuštěny v těchto skupinách. Třída `task_handle` zapouzdřuje kód, který provádí práci. Stejně `task` jako třída, pracovní funkce přichází ve formě funkce lambda, ukazatel funkce nebo objekt funkce. Obvykle není nutné pracovat s `task_handle` objekty přímo. Místo toho předáte pracovní funkce skupině úkolů a skupina úkolů `task_handle` vytvoří a spravuje objekty.

PPL rozděluje skupiny úkolů do těchto dvou kategorií: *nestrukturované skupiny úkolů* a *strukturované skupiny úkolů*. PPL používá `task_group` třídu k reprezentaci nestrukturovaných skupin úkolů a třídy `structured_task_group` k reprezentaci strukturovaných skupin úkolů.

> [!IMPORTANT]
> PPL také definuje [souběžnost::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus, `structured_task_group` který používá třídu k paralelnímu provádění sady úloh. Vzhledem `parallel_invoke` k tomu, že algoritmus má stručnější syntaxi, `structured_task_group` doporučujeme použít místo třídy, když je to možné. Téma [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md) `parallel_invoke` popisuje podrobněji.

Použijte, `parallel_invoke` pokud máte několik nezávislých úkolů, které chcete provést současně, a musíte počkat na dokončení všech úkolů, než budete pokračovat. Tato technika je často označována jako *vidlice a spojit* paralelismus. Použijte, `task_group` pokud máte několik nezávislých úkolů, které chcete provést současně, ale chcete počkat na dokončení úkolů později. Můžete například přidat úkoly `task_group` do objektu a počkat na dokončení úkolů v jiné funkci nebo z jiného vlákna.

Skupiny úloh podporují koncept zrušení. Zrušení umožňuje signalizovat všem aktivním úkolům, které chcete zrušit celkovou operaci. Zrušení také zabraňuje spuštění úloh, které ještě nebyly spuštěny. Další informace o zrušení naleznete [v tématu Zrušení v PPL](cancellation-in-the-ppl.md).

Runtime také poskytuje model zpracování výjimek, který umožňuje vyvolat výjimku z úlohy a zpracovat tuto výjimku při čekání na dokončení přidružené skupiny úloh. Další informace o tomto modelu zpracování výjimek naleznete v [tématu Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="comparing-task_group-to-structured_task_group"></a><a name="comparing-groups"></a>Porovnání task_group s structured_task_group

I když doporučujeme `task_group` `parallel_invoke` použít nebo `structured_task_group` místo třídy, existují případy, kdy chcete použít `structured_task_group`, například při psaní paralelní algoritmus, který provádí proměnný počet úkolů nebo vyžaduje podporu pro zrušení. Tato část vysvětluje rozdíly mezi `task_group` `structured_task_group` a třídy.

Třída `task_group` je bezpečná pro přístup z více vláken. Proto můžete přidat úkoly do objektu `task_group` z více `task_group` vláken a čekat nebo zrušit objekt z více vláken. Konstrukce a zničení `structured_task_group` objektu musí dojít ve stejném lexikálním oboru. Kromě toho musí všechny `structured_task_group` operace na objektu dojít ve stejném vlákně. Výjimkou z tohoto pravidla jsou metody [souběžnosti::structured_task_group:cancel](reference/structured-task-group-class.md#cancel) a [concurrency::structured_task_group::is_canceling.](reference/structured-task-group-class.md#is_canceling) Podřízená úloha může tyto metody volat ke zrušení nadřazené skupiny úkolů nebo ke kontrole zrušení.

Další úlohy objektu `task_group` můžete spustit po volání [metody concurrency::task_group::wait](reference/task-group-class.md#wait) nebo [concurrency::task_group::run_and_wait.](reference/task-group-class.md#run_and_wait) Naopak pokud spustíte další úlohy na `structured_task_group` objekt po volání [souběžnosti::structured_task_group::wait](reference/structured-task-group-class.md#wait) nebo [souběžnosti::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) metody, pak chování není definováno.

Vzhledem `structured_task_group` k tomu, že třída není synchronizována `task_group` mezi vlákny, má menší režii spuštění než třída. Proto pokud váš problém nevyžaduje, že naplánovat práci z více `parallel_invoke` vláken `structured_task_group` a nelze použít algoritmus, třída vám může pomoci napsat lépe fungující kód.

Pokud použijete `structured_task_group` jeden `structured_task_group` objekt uvnitř jiného objektu, musí být vnitřní objekt dokončen a zničen před dokončením vnějšího objektu. Třída `task_group` nevyžaduje, aby vnořené skupiny úkolů bylo dokončeno před dokončením vnější skupiny.

Nestrukturované skupiny úkolů a strukturované skupiny úkolů pracují s úchyty úkolů různými způsoby. Pracovní funkce můžete předat `task_group` přímo objektu; `task_group` objekt vytvoří a bude spravovat popisovač úkolu za vás. Třída `structured_task_group` vyžaduje, abyste `task_handle` pro každý úkol spravovali objekt. Každý `task_handle` objekt musí zůstat platný po `structured_task_group` celou dobu životnosti jeho přidruženého objektu. Pomocí funkce [souběžnosti::make_task](reference/concurrency-namespace-functions.md#make_task) vytvořte `task_handle` objekt, jak je znázorněno v následujícím základním příkladu:

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

Chcete-li spravovat popisovače úkolů pro případy, kdy máte proměnný počet úkolů, použijte rutinu přidělení zásobníku, například [_malloca](../../c-runtime-library/reference/malloca.md) nebo třídu kontejneru, například std::[vector](../../standard-library/vector-class.md).

Jak `task_group` `structured_task_group` a podpora zrušení. Další informace o zrušení naleznete [v tématu Zrušení v PPL](cancellation-in-the-ppl.md).

## <a name="example"></a><a name="example"></a>Příklad

Následující základní příklad ukazuje, jak pracovat se skupinami úkolů. Tento příklad `parallel_invoke` používá algoritmus k provádění dvou úloh současně. Každý úkol přidá k `task_group` objektu dílčí úkoly. Všimněte `task_group` si, že třída umožňuje více úkolů přidat úkoly k němu současně.

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

Následuje ukázkový výstup pro tento příklad:

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

Vzhledem `parallel_invoke` k tomu, že algoritmus spouští úlohy souběžně, pořadí výstupních zpráv se může lišit.

Úplné příklady, které ukazují, `parallel_invoke` jak používat algoritmus, naleznete v [tématu How to: Use parallel_invoke to Write a Parallel Sort Routine](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) and How [to: Use parallel_invoke to Execute Parallel Operations](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Úplný příklad, který `task_group` používá třídu k implementaci asynchronních termínových obchodů, naleznete [v návodu: Implementace futures](../../parallel/concrt/walkthrough-implementing-futures.md).

## <a name="robust-programming"></a><a name="robust"></a>Robustní programování

Ujistěte se, že rozumíte roli zrušení a zpracování výjimek při použití úkolů, skupin úkolů a paralelních algoritmů. Například ve stromu paralelní práce, úloha, která je zrušena zabraňuje spuštění podřízených úloh. To může způsobit problémy, pokud jeden z podřízených úloh provádí operaci, která je důležitá pro vaši aplikaci, jako je například uvolnění prostředku. Kromě toho pokud podřízená úloha vyvolá výjimku, tato výjimka může šířit prostřednictvím destruktoru objektu a způsobit nedefinované chování ve vaší aplikaci. Příklad, který ilustruje tyto body, naleznete [v části Understand How Cancellation and Exception Handling Affect Object Destruction](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) v dokumentu Best Practices in the Parallel Patterns Library . Další informace o zrušení a zpracování výjimek modely v PPL, naleznete v [tématu zrušení](../../parallel/concrt/cancellation-in-the-ppl.md) a [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Ukazuje, jak `parallel_invoke` pomocí algoritmu ke zlepšení výkonu bitonic algoritmu řazení.|
|[Postup: Použití parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Ukazuje, jak `parallel_invoke` pomocí algoritmu zlepšit výkon programu, který provádí více operací na sdíleném zdroji dat.|
|[Postupy: Vytvoření úlohy, která se dokončí po prodlevě](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Ukazuje, jak `task`pomocí `cancellation_token_source` `cancellation_token`, `task_completion_event` , a třídy vytvořit úkol, který dokončí po zpoždění.|
|[Návod: Implementace tříd future](../../parallel/concrt/walkthrough-implementing-futures.md)|Ukazuje, jak kombinovat existující funkce v souběžnosti Runtime do něčeho, co dělá víc.|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Popisuje PPL, který poskytuje imperativní programovací model pro vývoj souběžných aplikací.|

## <a name="reference"></a>Referenční informace

[třída úlohy (souběžné běhové zařízení)](../../parallel/concrt/reference/task-class.md)

[task_completion_event – třída](../../parallel/concrt/reference/task-completion-event-class.md)

[when_all funkce](reference/concurrency-namespace-functions.md#when_all)

[when_any funkce](reference/concurrency-namespace-functions.md#when_any)

[task_group – třída](reference/task-group-class.md)

[parallel_invoke funkce](reference/concurrency-namespace-functions.md#parallel_invoke)

[structured_task_group – třída](../../parallel/concrt/reference/structured-task-group-class.md)
