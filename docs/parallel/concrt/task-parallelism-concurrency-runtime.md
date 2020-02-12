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
ms.openlocfilehash: 634b4b584e997007a7de72e23c9b16e937a694ae
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143324"
---
# <a name="task-parallelism-concurrency-runtime"></a>Funkční paralelismus (Concurrency Runtime)

V Concurrency Runtime *úkol* je jednotka práce, která provádí určitou úlohu a obvykle běží paralelně s jinými úkoly. Úkol je možné rozložit na další detailní úlohy, které jsou uspořádané do *skupiny úloh*.

Úkoly použijete při psaní asynchronního kódu a chcete, aby k nějaké operaci docházelo po dokončení asynchronní operace. Můžete například použít úlohu pro asynchronní čtení ze souboru a potom použít jiný úkol – *úlohu pokračování*, která je vysvětlena dále v tomto dokumentu – ke zpracování dat po jejich zpřístupnění. Naopak můžete pomocí skupin úloh rozložit paralelní práci na menší části. Předpokládejme například, že máte rekurzivní algoritmus, který rozděluje zbývající práci na dva oddíly. Skupiny úloh můžete použít ke spuštění těchto oddílů souběžně a pak počkat na dokončení rozdělené práce.

> [!TIP]
> Pokud chcete použít stejnou rutinu pro každý prvek v kolekci paralelně, použijte paralelní algoritmus, jako je například [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for), namísto úlohy nebo skupiny úloh. Další informace o paralelních algoritmech najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

## <a name="key-points"></a>Klíčové body

- Pokud předáte proměnné na lambda výraz odkazem, je nutné zaručit, že životnost této proměnné přetrvává až do dokončení úkolu.

- Použijte úlohy (třída [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) ) při psaní asynchronního kódu. Třída Task používá jako Plánovač Windows jako svůj Plánovač, nikoli Concurrency Runtime.

- Použijte skupiny úloh (třída [Concurrency:: task_group](reference/task-group-class.md) nebo algoritmus [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) ), pokud chcete rozložit paralelní práci na menší části a pak počkat na dokončení těchto menších částí.

- K vytvoření pokračování použijte metodu [Concurrency:: task:: then](reference/task-class.md#then) . *Pokračování* je úkol, který se spouští asynchronně po dokončení jiného úkolu. Můžete propojit libovolný počet pokračování a vytvořit tak řetěz asynchronní práce.

- Pokračování na základě úkolů je vždy naplánováno na spuštění po dokončení předchozí úlohy, a to i v případě, že předchozí úloha byla zrušena nebo vyvolá výjimku.

- Použijte [Concurrency:: when_all](reference/concurrency-namespace-functions.md#when_all) k vytvoření úlohy, která se dokončí po dokončení všech členů sady úkolů. Použijte [Concurrency:: when_any](reference/concurrency-namespace-functions.md#when_any) k vytvoření úlohy, která se dokončí po dokončení jednoho člena sady úloh.

- Úlohy a skupiny úloh se můžou účastnit mechanismu pro zrušení knihovny paralelních vzorů (PPL). Další informace najdete v tématu [zrušení v PPL](cancellation-in-the-ppl.md).

- Informace o tom, jak modul runtime zpracovává výjimky, které jsou vyvolány úlohami a skupinami úloh, naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="in-this-document"></a>V tomto dokumentu

- [Použití výrazů lambda](#lambdas)

- [Třída Task](#task-class)

- [Pokračující úkoly](#continuations)

- [Pokračování na základě hodnoty oproti úlohám](#value-versus-task)

- [Vytváření úloh](#composing-tasks)

    - [Funkce when_all](#when-all)

    - [Funkce when_any](#when-any)

- [Zpožděné provedení úlohy](#delayed-tasks)

- [Skupiny úloh](#task-groups)

- [Porovnávání task_group structured_task_group](#comparing-groups)

- [Příklad](#example)

- [Robustní programování](#robust)

## <a name="lambdas"></a>Použití výrazů lambda

Z důvodu jejich stručné syntaxe představují výrazy lambda běžný způsob, jak definovat práci, kterou provádí úkoly a skupiny úloh. Tady je několik tipů k používání:

- Vzhledem k tomu, že úkoly jsou obvykle spouštěny na vláknech na pozadí, pamatujte na životnost objektu při zachycení proměnných ve výrazech lambda. Při zachycení proměnné podle hodnoty je vytvořena kopie této proměnné v těle lambda. Při digitalizaci podle odkazu není vytvořena kopie. Proto zajistěte, aby životnost jakékoli proměnné, kterou zachytíte odkazem, vychází z úlohy, která ji používá.

- Když do úlohy předáte výraz lambda, nezachytí proměnné, které jsou přiděleny v zásobníku odkazem.

- Být explicitní o proměnných, které zachytíte ve výrazech lambda, abyste mohli zjistit, co zachycujete pomocí hodnoty versus odkazem. Z tohoto důvodu doporučujeme, abyste nepoužívali možnosti `[=]` nebo `[&]` pro výrazy lambda.

Běžným vzorem je, že jeden úkol v řetězci pokračování přiřadí proměnné a další úloha tuto proměnnou přečte. Nemůžete zachytit podle hodnoty, protože každá úloha pokračování by obsahovala jinou kopii proměnné. Pro proměnné přidělené zásobníkem nelze také zachytit odkaz podle odkazu, protože proměnná již pravděpodobně není platná.

Chcete-li tento problém vyřešit, použijte inteligentní ukazatel, například [std:: shared_ptr](../../standard-library/shared-ptr-class.md), a zabalte proměnnou a předejte inteligentní ukazatel podle hodnoty. Tímto způsobem lze podkladové objekty přiřadit a číst z a vyplní úlohy, které ji používají. Tuto techniku použijte i v případě, že proměnná je ukazatel nebo popisovač s odkazem (`^`) na objekt prostředí Windows Runtime. Tady je základní příklad:

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

## <a name="task-class"></a>Třída Task

Můžete použít třídu [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) k vytváření úkolů do sady závislých operací. Tento model kompozice je podporován pojmem *pokračování*. Pokračování umožňuje, aby byl kód proveden po dokončení předchozího nebo *předchůdce*úlohy. Výsledek předchozí úlohy je předán jako vstup do jedné nebo více úloh pokračování. Po dokončení předchozí úlohy se naplánuje spuštění všech pokračujících úloh, které na ni čekají. Každý úkol pokračování obdrží kopii výsledku předchozí úlohy. Tyto úlohy pokračování mohou být také předchozími úkoly pro další pokračování, čímž se vytvoří řetězec úkolů. Pokračování vám pomůžou vytvořit libovolné řetězy úloh, které mají mezi nimi konkrétní závislosti. Kromě toho se může úkol účastnit zrušení buď před zahájením úlohy, nebo v průběhu spolupráce, pokud je spuštěný. Další informace o tomto modelu zrušení naleznete v tématu [zrušení v PPL](cancellation-in-the-ppl.md).

`task` je třída šablony. Parametr typu `T` je typ výsledku, který je vytvořen úlohou. Tento typ může být `void`, pokud úloha nevrací hodnotu. `T` nemůže použít modifikátor `const`.

Když vytvoříte úlohu, poskytnete *pracovní funkci* , která provede tělo úkolu. Tato pracovní funkce je dodávána ve formě funkce lambda, ukazatele na funkci nebo objektu funkce. Chcete-li počkat na dokončení úlohy bez získání výsledku, zavolejte metodu [Concurrency:: task:: wait](reference/task-class.md#wait) . Metoda `task::wait` vrací hodnotu [Concurrency:: task_status](reference/concurrency-namespace-enums.md#task_group_status) , která popisuje, zda byl úkol dokončen nebo zrušen. Chcete-li získat výsledek úlohy, zavolejte metodu [Concurrency:: task:: Get](reference/task-class.md#get) . Tato metoda volá `task::wait` pro čekání na dokončení úlohy, a proto zablokuje spuštění aktuálního vlákna, dokud nebude výsledek k dispozici.

Následující příklad ukazuje, jak vytvořit úkol, počkat na jeho výsledek a zobrazit jeho hodnotu. Příklady v této dokumentaci používají lambda funkce, protože poskytují stručnější syntaxi. Můžete však také použít ukazatele na funkce a objekty funkce při použití úkolů.

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

Při použití funkce [Concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) lze místo deklarace typu použít klíčové slovo `auto`. Zvažte například tento kód, který vytvoří a vytiskne matici identity:

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

Pomocí funkce `create_task` můžete vytvořit ekvivalentní operaci.

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

Pokud je vyvolána výjimka během provádění úlohy, modul runtime zazařazuje tuto výjimku do následného volání `task::get` nebo `task::wait`nebo do pokračování založeného na úlohách. Další informace o mechanismu zpracování výjimek úloh naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Příklad, který používá `task`, [Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), zrušení, viz [Návod: připojení pomocí úloh a HTTP požadavky XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). (`task_completion_event` třída je popsána dále v tomto dokumentu.)

> [!TIP]
> Informace, které jsou specifické pro úlohy v aplikacích pro UWP, najdete v tématu [asynchronní C++ programování v](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) a [ C++ vytváření asynchronních operací v aplikacích pro UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

## <a name="continuations"></a>Pokračující úkoly

V asynchronním programování je velmi běžné pro jednu asynchronní operaci po dokončení, k vyvolání druhé operace a předání dat do ní. Tradičně je to prováděno pomocí metod zpětného volání. V Concurrency Runtime jsou stejné funkce k dispozici v *návazných úlohách*. Pokračování úlohy (označované také jako pokračování) je asynchronní úloha, která je vyvolána jinou úlohou, která se označuje jako *předchůdce*po dokončení předchůdce. Pomocí pokračování můžete:

- Předat data z předchůdce do pokračování.

- Určete přesné podmínky, za kterých je pokračování vyvoláno nebo není vyvoláno.

- Zrušit pokračování před spuštěním nebo kospoluprácim, když je spuštěný.

- Poskytněte nápovědu, jak má být pokračování naplánováno. (To platí jenom pro aplikace Univerzální platforma Windows (UWP). Další informace najdete v tématu [Vytváření asynchronních operací C++ v pro aplikace pro UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).)

- Vyvolá několik pokračování ze stejného předchůdce.

- Vyvolat jedno pokračování, až se dokončí vše nebo jakýkoli z více předchůdců.

- Zřetězit pokračování jedno po druhém na libovolnou délku.

- Použijte pokračování pro zpracování výjimek vyvolaných předchůdcem.

Tyto funkce umožňují spustit jednu nebo více úloh po dokončení první úlohy. Můžete například vytvořit pokračování, které komprimuje soubor poté, co první úkol načte z disku.

Následující příklad upravuje předchozí metodu pro použití metody [Concurrency:: task:: then](reference/task-class.md#then) k naplánování pokračování, které vytiskne hodnotu předchozí úlohy, je-li k dispozici.

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

Můžete zřetězit a vnořit úkoly na libovolnou délku. Úkol může mít také více pokračování. Následující příklad znázorňuje základní řetězec pokračování, který zvýší hodnotu předchozí úlohy třikrát.

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

Pokračování může také vrátit jinou úlohu. Pokud nedojde k žádnému zrušení, tato úloha se spustí před dalším pokračováním. Tato technika se označuje jako *asynchronní rozbalení*. Asynchronní rozbalení je užitečné, pokud chcete provést další práci na pozadí, ale nechcete, aby aktuální úloha blokovala aktuální vlákno. (To je běžné v aplikacích pro UWP, kde je možné spustit pokračování ve vlákně uživatelského rozhraní). Následující příklad ukazuje tři úkoly. První úloha vrátí jiný úkol, který se spustí před pokračováním úlohy.

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
> Pokud pokračování úlohy vrátí vnořenou úlohu typu `N`, výsledný úkol má typ `N`, nikoli `task<N>`a dokončen po dokončení vnořené úlohy. Jinými slovy pokračování provádí rozbalení vnořené úlohy.

## <a name="value-versus-task"></a>Pokračování na základě hodnoty oproti úlohám

Vzhledem k objektu `task`, jehož návratový typ je `T`, můžete zadat hodnotu typu `T` nebo `task<T>` do svých pokračujících úloh. Pokračování, které přebírá typ `T`, se označuje jako *pokračování založené na hodnotách*. Pokračování založené na hodnotách je naplánováno na provedení, pokud je předchozí úloha dokončena bez chyby a není zrušena. Pokračování, které přebírá typ `task<T>` jako jeho parametr, se označuje jako *pokračování založené na úlohách*. Pokračování na základě úkolů je vždy naplánováno na spuštění po dokončení předchozí úlohy, a to i v případě, že předchozí úloha byla zrušena nebo vyvolá výjimku. Potom můžete zavolat `task::get` a získat tak výsledek předchozí úlohy. Pokud předchozí úloha byla zrušena, `task::get` vyvolá [Concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md). Pokud předchozí úloha vyvolala výjimku, `task::get` znovu vyvolá tuto výjimku. Pokračování založené na úlohách není označeno jako zrušené, když je zrušená předchozí úloha.

## <a name="composing-tasks"></a>Vytváření úloh

Tato část popisuje funkce [Concurrency:: when_all](reference/concurrency-namespace-functions.md#when_all) a [concurrency:: when_any](reference/concurrency-namespace-functions.md#when_all) , které vám pomohou vytvořit více úkolů pro implementaci běžných vzorů.

### <a name="when-all"></a>Funkce when_all

Funkce `when_all` vytvoří úlohu, která skončí po dokončení sady úloh. Tato funkce vrací objekt std::[Vector](../../standard-library/vector-class.md) , který obsahuje výsledek každého úkolu v sadě. Následující základní příklad používá `when_all` k vytvoření úkolu, který představuje dokončení tří dalších úkolů.

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
> Úkoly, které předáváte `when_all`, musí být jednotné. Jinými slovy, musí všechny vracet stejný typ.

Můžete také použít syntaxi `&&` k vytvoření úlohy, která se dokončí po dokončení sady úloh, jak je znázorněno v následujícím příkladu.

`auto t = t1 && t2; // same as when_all`

Je běžné používat pokračování společně s `when_all` k provedení akce po dokončení sady úkolů. Následující příklad upravuje předchozí a vytiskne součet tří úloh, které každý z nich vytvoří `int` výsledek.

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

V tomto příkladu můžete také zadat `task<vector<int>>` pro vytvoření pokračování založeného na úlohách.

Pokud se nějaká úloha v sadě úkolů zruší nebo vyvolá výjimku, `when_all` se okamžitě dokončí a nečeká na dokončení zbývajících úloh. Pokud je vyvolána výjimka, modul runtime znovu vyvolá výjimku při volání `task::get` nebo `task::wait` objektu Task, který `when_all` vrací. Pokud je vyvolána více než jedna úloha, modul runtime zvolí jednu z nich. Proto se ujistěte, že po dokončení všech úkolů máte pozorovat všechny výjimky; Neošetřená výjimka úlohy způsobí ukončení aplikace.

Zde je funkce nástroje, kterou můžete použít, chcete-li zajistit, že váš program sleduje všechny výjimky. Pro každý úkol v zadaném rozsahu `observe_all_exceptions` aktivuje jakoukoli výjimku, ke které došlo znovu, a pak tuto výjimku požití.

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

Zvažte použití aplikace pro UWP, C++ která používá a XAML a zapisuje sadu souborů na disk. Následující příklad ukazuje, jak použít `when_all` a `observe_all_exceptions`, abyste zajistili, že program sleduje všechny výjimky.

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>Spuštění tohoto příkladu

1. V souboru MainPage. XAML přidejte ovládací prvek `Button`.

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. V souboru MainPage. XAML. h přidejte tyto předávané deklarace do oddílu `private` deklarace `MainPage` třídy.

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. V souboru MainPage. XAML. cpp Implementujte obslužnou rutinu události `Button_Click`.

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. V souboru MainPage. XAML. cpp implementujte `WriteFilesAsync`, jak je znázorněno v příkladu.

> [!TIP]
> `when_all` je neblokovaná funkce, která jako svůj výsledek vytvoří `task`. Na rozdíl od [úlohy:: wait](reference/task-class.md#wait), je bezpečné volat tuto funkci v aplikaci UWP ve vlákně ASTA (Application sta).

### <a name="when-any"></a>Funkce when_any

Funkce `when_any` vytvoří úlohu, která se dokončí po dokončení první úlohy v sadě úloh. Tato funkce vrací objekt [Air std::p](../../standard-library/pair-structure.md) , který obsahuje výsledek dokončené úlohy a index tohoto úkolu v sadě.

Funkce `when_any` je obzvláště užitečná v následujících scénářích:

- Nadbytečné operace. Zvažte algoritmus nebo operaci, které lze provést mnoha způsoby. Můžete použít funkci `when_any` k výběru operace, která skončí jako první, a pak zrušit zbývající operace.

- Prokládané operace. Můžete spustit více operací, které musí dokončit, a použít funkci `when_any` ke zpracování výsledků při dokončení každé operace. Po dokončení jedné operace můžete spustit jednu nebo více dalších úloh.

- Omezené operace. Pomocí funkce `when_any` můžete zvětšit předchozí scénář tak, že omezíte počet souběžných operací.

- Operace, jejichž platnost vypršela. Pomocí funkce `when_any` můžete vybrat jednu nebo více úloh a úlohu, která skončí po určitém čase.

Stejně jako u `when_all`je běžné použití pokračování, které má `when_any` k provedení akce při dokončení první sady úkolů. Následující základní příklad používá `when_any` k vytvoření úlohy, která se dokončí po dokončení prvních tří dalších úloh.

[!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]

V tomto příkladu můžete také zadat `task<pair<int, size_t>>` pro vytvoření pokračování založeného na úlohách.

> [!NOTE]
> Stejně jako u `when_all`musí úlohy, které předáte `when_any`, vracet stejný typ.

K vytvoření úlohy, která se dokončí po prvním úkolu v sadě úloh, můžete použít také syntaxi `||`, jak je znázorněno v následujícím příkladu.

`auto t = t1 || t2; // same as when_any`

> [!TIP]
> Stejně jako u `when_all``when_any` není blokující a je bezpečný pro volání v aplikaci UWP ve vlákně ASTA.

## <a name="delayed-tasks"></a>Zpožděné provedení úlohy

Někdy je nutné zpozdit provádění úlohy, dokud není splněna podmínka, nebo spustit úlohu v reakci na externí událost. Například v asynchronním programování může být nutné spustit úlohu jako odpověď na událost dokončení I/O.

Existují dva způsoby, jak to provést, je použít pokračování nebo spustit úlohu a počkat na událost v pracovní funkci úkolu. Existují však případy, kdy není možné použít jeden z těchto postupů. Chcete-li například vytvořit pokračování, je nutné mít předchozí úlohu. Pokud však předchozí úlohu nemáte, můžete vytvořit *událost dokončení úkolu* a později řetězit událost dokončení pro předchozí úlohu, jakmile bude k dispozici. Kromě toho, vzhledem k tomu, že čekající úloha také blokuje vlákno, můžete použít události dokončení úkolu k provedení práce po dokončení asynchronní operace, a tím uvolnit vlákno.

Třída [Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) pomáhá zjednodušit takové složení úkolů. Podobně jako třída `task`, parametr typu `T` je typ výsledku, který je vytvořen úlohou. Tento typ může být `void`, pokud úloha nevrací hodnotu. `T` nemůže použít modifikátor `const`. Obvykle je objekt `task_completion_event` k dispozici vláknu nebo úloze, který mu signalizuje, když bude hodnota k dispozici. Současně je jeden nebo více úkolů nastaveno jako naslouchací procesy této události. Po nastavení události jsou dokončeny úlohy naslouchacího procesu a jejich pokračování je naplánováno na spuštění.

Příklad, který používá `task_completion_event` k implementaci úlohy, která se dokončí po zpoždění, naleznete v tématu [How to: Create a Task, který se dokončí po zpoždění](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md).

## <a name="task-groups"></a>Skupiny úloh

*Skupina úloh* uspořádá kolekci úkolů. Skupiny úloh přidávají úlohy do fronty pro práci s odcizením. Plánovač odebere úkoly z této fronty a provede je na dostupných výpočetních prostředcích. Po přidání úkolů do skupiny úkolů můžete počkat na dokončení všech úkolů nebo zrušit úlohy, které ještě nebyly spuštěny.

PPL používá třídy [Concurrency:: task_group](reference/task-group-class.md) a [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) pro reprezentaci skupin úloh a třídu [Concurrency:: task_handle](../../parallel/concrt/reference/task-handle-class.md) , která představuje úkoly spouštěné v těchto skupinách. Třída `task_handle` zapouzdřuje kód, který provádí práci. Podobně jako třída `task`, funguje pracovní funkce ve formě funkce lambda, ukazatele na funkci nebo objektu funkce. Obvykle není nutné pracovat s `task_handle` objekty přímo. Místo toho předáte pracovní funkce skupině úkolů a skupina úloh vytvoří a spravuje objekty `task_handle`.

PPL rozdělí skupiny úloh do těchto dvou kategorií: *nestrukturované skupiny úloh* a *strukturované skupiny úloh*. PPL používá třídu `task_group` k reprezentaci nestrukturovaných skupin úloh a `structured_task_group` třídy k reprezentaci strukturovaných skupin úloh.

> [!IMPORTANT]
> PPL také definuje algoritmus [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) , který používá třídu `structured_task_group` k paralelnímu spouštění sady úkolů. Vzhledem k tomu, že algoritmus `parallel_invoke` má stručnější syntaxi, doporučujeme ho použít místo `structured_task_group` třídy, když můžete. Téma [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md) popisuje `parallel_invoke` podrobněji.

Použijte `parallel_invoke`, pokud máte několik nezávislých úloh, které chcete spustit současně, a před pokračováním musíte počkat na dokončení všech úloh. Tato technika je často označována jako *rozvětvení a spojení* paralelismu. Použijte `task_group`, pokud máte několik nezávislých úloh, které chcete spustit současně, ale chcete počkat na dokončení úloh v pozdějším čase. Například můžete přidat úkoly do objektu `task_group` a počkat, až se úlohy dokončí jinou funkcí nebo z jiného vlákna.

Skupiny úloh podporují koncept zrušení. Zrušení umožňuje signalizovat všechny aktivní úlohy, u kterých chcete zrušit celkovou operaci. Zrušení také zabrání úlohám, které ještě nebyly spuštěny od spuštění. Další informace o zrušení naleznete v tématu [zrušení v PPL](cancellation-in-the-ppl.md).

Modul runtime také poskytuje model zpracování výjimek, který umožňuje vyvolat výjimku z úlohy a zpracovat tuto výjimku při čekání na dokončení přidružené skupiny úloh. Další informace o tomto modelu zpracování výjimek naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="comparing-groups"></a>Porovnávání task_group structured_task_group

I když doporučujeme použít `task_group` nebo `parallel_invoke` namísto třídy `structured_task_group`, existují případy, kdy chcete použít `structured_task_group`, například při psaní paralelního algoritmu, který provádí proměnlivý počet úkolů nebo vyžaduje podporu pro zrušení. Tato část vysvětluje rozdíly mezi `task_group` a `structured_task_group` třídy.

Třída `task_group` je bezpečná pro přístup z více vláken. Proto můžete přidat úkoly do objektu `task_group` z více vláken a počkat nebo zrušit objekt `task_group` z více vláken. Konstrukce a zničení objektu `structured_task_group` musí být ve stejném lexikálním oboru. Kromě toho musí být všechny operace na objektu `structured_task_group` provedeny ve stejném vlákně. Výjimkou z tohoto pravidla jsou metody [Concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) a [concurrency:: structured_task_group:: is_canceling](reference/structured-task-group-class.md#is_canceling) . Podřízená úloha může zavolat tyto metody a zrušit tak nadřazenou skupinu úloh nebo zrušit kontrolu zrušení.

Můžete spustit další úkoly pro objekt `task_group` po volání metody [Concurrency:: task_group:: wait](reference/task-group-class.md#wait) nebo [concurrency:: task_group:: run_and_wait](reference/task-group-class.md#run_and_wait) . Naopak, pokud spustíte další úkoly objektu `structured_task_group` po volání metod [Concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait) nebo [concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait) , pak není chování definováno.

Vzhledem k tomu, že se třída `structured_task_group` nesynchronizuje mezi vlákny, má méně režijních nákladů na provedení než třída `task_group`. Proto pokud váš problém nevyžaduje, abyste naplánovali práci z více vláken a nemůžete použít algoritmus `parallel_invoke`, `structured_task_group` Třída vám může usnadnit psaní kódu, který je lepší provádět.

Použijete-li jeden `structured_task_group` objekt uvnitř jiného objektu `structured_task_group`, musí být vnitřní objekt dokončen a zničen před dokončením vnějšího objektu. Třída `task_group` nevyžaduje, aby vnořené skupiny úloh byly dokončeny před dokončením vnější skupiny.

Nestrukturované skupiny úloh a strukturované skupiny úkolů pracují s popisovači úkolů různými způsoby. Pracovní funkce můžete předat přímo objektu `task_group`; objekt `task_group` vytvoří a bude spravovat popisovač úlohy za vás. Třída `structured_task_group` vyžaduje, abyste pro každý úkol spravovali objekt `task_handle`. Každý objekt `task_handle` musí zůstat platný po celou dobu životnosti jeho přidruženého objektu `structured_task_group`. Pomocí funkce [Concurrency:: make_task](reference/concurrency-namespace-functions.md#make_task) vytvořte objekt `task_handle`, jak je znázorněno v následujícím základním příkladu:

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

Pro správu obslužných rutin úloh pro případy, kde máte proměnlivý počet úkolů, použijte rutinu přidělení zásobníku, například [_malloca](../../c-runtime-library/reference/malloca.md) nebo třídu kontejneru, jako je například std::[Vector](../../standard-library/vector-class.md).

`task_group` i `structured_task_group` zrušení podpory. Další informace o zrušení naleznete v tématu [zrušení v PPL](cancellation-in-the-ppl.md).

## <a name="example"></a>Případě

Následující základní příklad ukazuje, jak pracovat se skupinami úloh. V tomto příkladu se používá algoritmus `parallel_invoke` k souběžnému provádění dvou úloh. Každý úkol přidá dílčí úkoly do objektu `task_group`. Všimněte si, že třída `task_group` umožňuje více úlohám současně přidat úlohy.

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

Následuje ukázkový výstup pro tento příklad:

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

Vzhledem k tomu, že algoritmus `parallel_invoke` spouští úlohy souběžně, může se změnit pořadí výstupních zpráv.

Kompletní příklady, které ukazují, jak použít `parallel_invoke` algoritmus, naleznete v tématu [How to: use parallel_invoke to Write The Parallel Sorting](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) a [How to: použijte Parallel_invoke k provedení paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Kompletní příklad, který používá třídu `task_group` pro implementaci asynchronních termínů, naleznete v tématu [Návod: implementace futures](../../parallel/concrt/walkthrough-implementing-futures.md).

## <a name="robust"></a>Robustní programování

Ujistěte se, že rozumíte roli zrušení a zpracování výjimek při použití úloh, skupin úloh a paralelních algoritmů. Například ve stromové struktuře paralelní práce úloha, která je zrušena, brání spuštění podřízených úloh. To může způsobit problémy, pokud jedna z podřízených úloh provádí operaci, která je pro vaši aplikaci důležitá, například uvolnění prostředku. Kromě toho, pokud podřízená úloha vyvolá výjimku, mohla by tato výjimka rozšířit objekt destruktoru objektu a způsobit nedefinované chování vaší aplikace. Příklad, který znázorňuje tyto body, naleznete v tématu [Principy způsobu, jakým zrušení a zpracování výjimek ovlivňují oddíl zničení objektů](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) v tématu osvědčené postupy v dokumentu knihovny paralelních vzorů. Další informace o zrušení a modelech zpracování výjimek v PPL naleznete v tématu [rušení](../../parallel/concrt/cancellation-in-the-ppl.md) a [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Ukazuje, jak použít algoritmus `parallel_invoke` ke zlepšení výkonu bitonického algoritmu řazení.|
|[Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Ukazuje, jak použít algoritmus `parallel_invoke` ke zlepšení výkonu programu, který provádí více operací na sdíleném zdroji dat.|
|[Postupy: Vytvoření úlohy, která se dokončí po prodlevě](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Ukazuje, jak použít třídy `task`, `cancellation_token_source`, `cancellation_token`a `task_completion_event` k vytvoření úlohy, která se dokončí po zpoždění.|
|[Návod: Implementace tříd future](../../parallel/concrt/walkthrough-implementing-futures.md)|Ukazuje, jak kombinovat stávající funkce v Concurrency Runtime do něčeho, co více dělá.|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Popisuje PPL, který poskytuje imperativní programovací model pro vývoj souběžných aplikací.|

## <a name="reference"></a>Referenční informace

[task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)

[task_completion_event – třída](../../parallel/concrt/reference/task-completion-event-class.md)

[when_all funkce](reference/concurrency-namespace-functions.md#when_all)

[when_any funkce](reference/concurrency-namespace-functions.md#when_any)

[task_group – třída](reference/task-group-class.md)

[parallel_invoke funkce](reference/concurrency-namespace-functions.md#parallel_invoke)

[structured_task_group – třída](../../parallel/concrt/reference/structured-task-group-class.md)
