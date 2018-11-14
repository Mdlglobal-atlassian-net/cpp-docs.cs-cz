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
ms.openlocfilehash: c9f18dfd1498538ce3700fd73a27ce6f6088ee42
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331214"
---
# <a name="task-parallelism-concurrency-runtime"></a>Funkční paralelismus (Concurrency Runtime)

V modulu Runtime souběžnosti *úloh* je jednotka práce, která provádí určitou úlohu a obvykle běží souběžně s ostatními úkoly. Úkol lze rozložit na další detailnější úkoly, které jsou uspořádány do *skupiny úloh*.

Úkoly se používají při psaní asynchronního kódu a chcete některé operace nastat po dokončení asynchronní operace. Můžete například použít úkol pro asynchronní čtení ze souboru a potom použít jiný úkol – *úkol pokračování*, což je vysvětleno dále v tomto dokumentu – zpracování dat po jejich zpřístupnění. Naopak můžete použít úkoly skupiny k rozložení paralelní práce na menší části. Předpokládejme například, že máte rekurzivní algoritmus, který rozdělí zbývající práce na dva oddíly. Skupiny úloh můžete použít k souběžnému spouštění těchto oddílů a potom počkejte na dokončení rozdělené práce.

> [!TIP]
> Pokud chcete použít stejnou rutinu pro každý prvek kolekce paralelně, použijte paralelní algoritmus, například [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), místo úkolu nebo skupiny úkolů. Další informace o paralelních algoritmech naleznete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

## <a name="key-points"></a>Klíčové body

- Při předání proměnných do výrazu lambda pomocí odkazu musíte zaručit, že životnost proměnné potrvá, dokud neskončí úloha.

- Použití úloh ( [concurrency::task](../../parallel/concrt/reference/task-class.md) třídy) při psaní asynchronního kódu. Třída úloh používá Windows fondu vláken jako jeho plánovače, ne modulu Runtime souběžnosti.

- Použijte skupiny úloh ( [concurrency::task_group](reference/task-group-class.md) třídy nebo [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus) Pokud chcete rozložit paralelní práci na menší části a potom počkejte těchto menších části a dokončí.

- Použití [Concurrency::Task:: Then](reference/task-class.md#then) metodu pro vytvoření pokračování. A *pokračování* je úkol, na kterém běží asynchronně po dokončení jiného úkolu. Můžete připojit libovolný počet pokračování k vytvoření řetězce asynchronní práce.

- Pokračování podle úloh je naplánováno na vykonání vždy, když je předchůdce dokončen, i když je předchozí úloha zrušen nebo vyvolá výjimku.

- Použití [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) k vytvoření úlohy, která se dokončí po dokončení každého člena sady úloh. Použití [concurrency::when_any](reference/concurrency-namespace-functions.md#when_any) vytvořit úlohu, která se dokončí po dokončení jednoho člena sady úloh.

- Úloh a skupin úloh mohou účastnit mechanismu zrušení knihovny paralelních vzorů (PPL). Další informace najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).

- Další způsob, jakým modul runtime zpracovává výjimky, které jsou vyvolány pomocí úloh a skupin úloh najdete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="in-this-document"></a>V tomto dokumentu

- [Použití výrazů Lambda](#lambdas)

- [Třídy task](#task-class)

- [Pokračování úlohy](#continuations)

- [Základě hodnoty nebo pokračování podle úloh](#value-versus-task)

- [Skládání úloh](#composing-tasks)

    - [When_all – funkce](#when-all)

    - [When_any – funkce](#when-any)

- [Zpožděné provedení úlohy](#delayed-tasks)

- [Skupiny úloh](#task-groups)

- [Porovnání tříd task_group a structured_task_group](#comparing-groups)

- [Příklad](#example)

- [Robustní programování](#robust)

##  <a name="lambdas"></a> Použití výrazů Lambda

Z důvodu jejich stručné syntaxe jsou lambda výrazy běžným způsobem definování práce, kterou je prováděna podle úloh a skupin úloh. Tady jsou některé tipy:

- Vzhledem k tomu, že úkoly obvykle běží na pozadí podprocesů, mějte na paměti životnosti objektu při zachycení proměnné ve výrazech lambda. Při zachycení proměnné podle hodnoty kopii této proměnné je vytvořena v těle výrazu lambda. Při zachycení odkazem není vytvořena kopie. Proto se ujistěte se, že, který životnost libovolné proměnné, můžete zachytit odkazem outlives úloha, která ji používá.

- Při předání lambda výrazu do úkolu nezachycujte proměnné, které jsou přiděleny v zásobníku podle odkazu.

- Buďte konkrétní o proměnných, které zachytíte v lambda výrazech, aby mohli identifikovat, co právě zachycujete podle hodnoty oproti podle odkazu. Z tohoto důvodu doporučujeme je velmi riskantní používat `[=]` nebo `[&]` možnosti pro výrazy lambda.

Běžným vzorem je, když jeden úkol v řetězci pokračování přiřadí proměnné a jiný úkol danou proměnnou přečte. Podle hodnoty nelze zachytit, protože každý úkol pokračování, by uchovával jinou kopii proměnné. Pro přidělení proměnných zásobníku také nelze zachytit odkazem. protože proměnné již nemusí být platný.

Chcete-li tento problém vyřešit, použijte inteligentní ukazatel, [std::shared_ptr](../../standard-library/shared-ptr-class.md)sbalení proměnné a předávat inteligentního ukazatele podle hodnoty. Tímto způsobem základní objekt je možné přiřadit a číst z a bude něj úkoly, které ji používají. Tento postup použijte i v případě, že proměnná je ukazatel nebo referenčně započítaný popisovač (`^`) na objekt prostředí Windows Runtime. Tady je příklad základní:

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](../../cpp/lambda-expressions-in-cpp.md).

##  <a name="task-class"></a> Třídy task

Můžete použít [concurrency::task](../../parallel/concrt/reference/task-class.md) třídy můžete sestavit úlohy do sady závislých operací. Tento model sestavení je podporován pojmem *pokračování*. Při spuštění kódu pokračování umožňuje předchozí, nebo *předchůdce*, dokončení úkolu. Výsledek předchozí úlohy je předán jako vstup pro jeden nebo více dalších úkolů. Po dokončení předchozí úlohy jakékoli pokračující úkoly, které čekají na ní jsou naplánovány k provedení. Každý úkol pokračování obdrží kopii výsledku předchozí úlohy. Tyto úkoly pokračování zase mohou být předchozími úkoly pro další pokračování, čímž se vytváří řetěz úkolů. Pokračování vám pomůže vytvořit libovolné délky řetězů, úlohy, které mají specifické vzájemné závislosti mezi nimi. Kromě toho se může úkol zúčastnit ve zrušení, buď před úkoly spustí nebo na způsob spolupráce za běhu. Další informace o tomto modelu zrušení naleznete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).

`task` je třída šablony. Parametr typu `T` je typ výsledku, který je vytvořil úkol. Tento typ může být `void` Pokud úloha nevrací hodnotu. `T` nelze použít `const` modifikátor.

Při vytváření úkolu zadáte *pracovní funkce* , která provede tělo úkolu. Tato pracovní funkce dodávána ve formě funkce lambda, ukazatele na funkci nebo objektu funkce. Chcete-li čekání na úlohu dokončit bez získání výsledku, volejte [Concurrency::Task:: wait](reference/task-class.md#wait) metody. `task::wait` Metoda vrátí hodnotu [concurrency::task_status](reference/concurrency-namespace-enums.md#task_group_status) hodnotu, která popisuje, zda byla úloha dokončena nebo zrušena. Chcete-li získat výsledek úkolu, zavolejte [Concurrency::Task:: Get](reference/task-class.md#get) metody. Tato metoda volá `task::wait` čekat výsledek je k dispozici pro úkol k dokončení a blokuje tak provedení aktuálního vlákna.

Následující příklad ukazuje, jak vytvořit úkol, čekat jeho výsledek a zobrazit jeho hodnotu. Příklady v této dokumentaci využívají lambda funkce protože poskytují stručnější syntaxi. Ale můžete taky pomocí ukazatele na funkce a objekty funkcí při použití úkolů.

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

Při použití [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) funkce, můžete použít `auto` – klíčové slovo místo deklarování typu. Zvažte například tento kód, který vytvoří a vytiskne jednotkovou matici:

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

Můžete použít `create_task` funkce lze vytvořit ekvivalentní operaci.

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

Pokud během provádění úkolu je vyvolána výjimka, modul runtime zařazuje tuto výjimku při následném volání `task::get` nebo `task::wait`, nebo na pokračování podle úloh. Další informace o mechanizmu zpracování výjimky úkolu naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Příklad, který používá `task`, [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), zrušení, naleznete v tématu [návod: připojení pomocí úloh a žádostí XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). ( `task_completion_event` Třídy je popsána dále v tomto dokumentu.)

> [!TIP]
>  Další podrobnosti, které jsou specifické pro úlohy v aplikacích pro UPW, najdete v článku [asynchronní programování v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) a [vytváření asynchronních operací v jazyce C++ pro aplikace pro UPW](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

##  <a name="continuations"></a> Pokračování úlohy

V asynchronním programování je velmi běžné, že jedna asynchronní operace při dokončení vyvolá druhou operaci a předá jí data. Tradičně to je prováděno pomocí metod zpětného volání. V modulu Runtime souběžnosti, je stejná funkčnost zajištěna pomocí *pokračujících úloh*. Pokračující úloha (nazývaná také pouze pokračování) je asynchronní úloha, která je vyvolána jinou úlohou, která se nazývá *předchůdce*, jakmile je předchůdce dokončen. Pomocí pokračování můžete:

- Předejte data z předchůdce do pokračování.

- Určete přesné podmínky, za kterých pokračování je či není vyvolána.

- Zrušte pokračování před spuštěním nebo kooperativně během jejího běhu.

- Poskytnout nápovědu, jak by měl být pokračování naplánováno. (To se týká jenom aplikace univerzální platformy Windows (UPW). Další informace najdete v tématu [vytváření asynchronních operací v jazyce C++ pro aplikace pro UPW](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).)

- Vyvolejte ze stejného předchůdce více pokračování.

- Vyvolejte jedno pokračování, až všichni nebo jen někteří z více předchůdců.

- Zřetězit pokračování jedno po druhém do jakékoli libovolné délky.

- Použijte pokračování pro zpracování výjimek vyvolaných předchůdcem.

Tyto funkce umožňují provést jednu nebo více úloh po dokončení první úlohy. Můžete například vytvořit pokračování, které komprimuje soubor po jeho prvním načtení ho z disku.

Následující příklad upravuje předchozí použití [Concurrency::Task:: Then](reference/task-class.md#then) metodu pro plánování pokračování, které vytiskne hodnotu předchozí úlohy, až bude k dispozici.

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

Můžete zřetězit a vnořit úkoly na libovolnou délku. Úkol může mít také více pokračování. Následující příklad ukazuje základní řetěz pokračování, který zvýší hodnotu předchozího úkolu třikrát.

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

Pokračování může také vrátit jiný úkol. Pokud neexistuje žádné zrušení, je tento úkol proveden před dalším pokračováním. Tato technika se nazývá *asynchronní rozvinutí*. Asynchronní rozbalení je užitečné, pokud chcete provést další práce na pozadí, ale nechcete, aby aktuální úkol blokoval aktuální vlákno. (To je běžné v aplikacích pro UPW, kde lze spustit pokračování ve vlákně uživatelského rozhraní). Následující příklad ukazuje tři úkoly. První úkol vrátí jiný úkol, která se spouští před pokračujícím úkolem.

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
>  Když pokračování úlohy vrátí vnořenou úlohu typu `N`, výsledný úkol má typ `N`, nikoli `task<N>`a skončí po dokončení vnořené úlohy. Jinými slovy pokračování provádí rozbalení vnořené úlohy.

##  <a name="value-versus-task"></a> Základě hodnoty nebo pokračování podle úloh

Zadaný `task` objekt, jehož návratový typ je `T`, můžete zadat hodnotu typu `T` nebo `task<T>` k jeho pokračujícím úlohám. Pokračování, které převezme typ `T` se označuje jako *pokračování založené na hodnotách*. Pokračování založené na hodnotách je naplánováno na vykonání, když je předchozí úloha dokončena bez chyb a není zrušena. Pokračování, které převezme typ `task<T>` jako svůj parametr se nazývá *pokračování podle úloh*. Pokračování podle úloh je naplánováno na vykonání vždy, když je předchůdce dokončen, i když je předchozí úloha zrušen nebo vyvolá výjimku. Potom můžete zavolat `task::get` k získání výsledku předchozí úlohy. Pokud předchozí úloha byla zrušena, `task::get` vyvolá [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). Pokud předchozí úloha vyvolala výjimku, `task::get` znovu vyvolá tuto výjimku. Pokračování podle úloh není označeno jako zrušené, když je zrušena jeho předchozí úloha.

##  <a name="composing-tasks"></a> Skládání úloh

Tato část popisuje [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) a [concurrency::when_any](reference/concurrency-namespace-functions.md#when_all) funkce, které vám pomohou vytvořit více úkolů k implementaci běžných vzorů.

###  <a name="when-all"></a> When_all – funkce

`when_all` Funkce vytvoří úlohu, která skončí po dokončení sady úloh. Tato funkce vrací std::[vektoru](../../standard-library/vector-class.md) objekt, který obsahuje výsledek každého úkolu v sadě. V následujícím základním příkladu používá `when_all` k vytvoření úkolu, který představuje dokončení tři dalších úkolů.

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
>  Úlohy, které můžete předat `when_all` musí být jednotné. Jinými slovy musí všichni vrátit stejný typ.

Můžete také použít `&&` syntaxe pro vytvoření úlohy, která se dokončí po dokončení sady úloh, jak je znázorněno v následujícím příkladu.

`auto t = t1 && t2; // same as when_all`

Je běžné používat pokračování společně s `when_all` provádět akce po dokončení sady úloh. Následující příklad upravuje předchozí Tisk součtu tři úkolů, že každý vytváří `int` výsledek.

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

V tomto příkladu můžete také určit `task<vector<int>>` k výrobě pokračování podle úloh.

Pokud libovolný úkol v sadě úloh je zrušen nebo vyvolá výjimku, `when_all` ihned dokončí a nečeká na dokončení zbývajících úkolů. Pokud je vyvolána výjimka, modul runtime znovu vyvolá výjimku při volání `task::get` nebo `task::wait` na objektu úkolu, který `when_all` vrátí. Pokud vyvolá více než jeden úkol, modul runtime vybere jeden z nich. Proto zajistěte sledování všech výjimek po dokončení všech úloh; Nezpracovaná výjimka úlohy způsobí ukončení aplikace.

Zde je nástroj pro funkci, můžete použít k ověření, že váš program dodržuje všechny výjimky. Pro každý úkol v zadané oblasti `observe_all_exceptions` aktivuje jakoukoliv výjimku, která znovu vyvolala a poté pohltila danou výjimku.

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

Vezměte v úvahu aplikace pro UPW, která používá C++ a XAML a zapíše sadu souborů na disk. Následující příklad ukazuje, jak používat `when_all` a `observe_all_exceptions` zajistit, že program dodržuje všechny výjimky.

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>Chcete-li spustit tento příklad

1. Do MainPage.xaml přidejte `Button` ovládacího prvku.

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. V MainPage.xaml.h přidejte tyto deklarace dopředu, do `private` část `MainPage` deklarace třídy.

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. Ve MainPage.xaml.cpp implementujte `Button_Click` obslužné rutiny události.

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. Ve MainPage.xaml.cpp implementujte `WriteFilesAsync` jak je znázorněno v příkladu.

> [!TIP]
> `when_all` je neblokující funkce, která vytváří `task` jako svůj výsledek. Na rozdíl od [task::wait](reference/task-class.md#wait), je bezpečné volat tuto funkci v aplikaci UWP ve vlákně ASTA (Application STA).

###  <a name="when-any"></a> When_any – funkce

`when_any` Funkce vytvoří úlohu, která skončí po dokončení první úlohy v sadě úloh. Tato funkce vrací [std::pair](../../standard-library/pair-structure.md) objekt, který obsahuje výsledek dokončené úlohy a index této úlohy v sadě.

`when_any` Funkce je užitečná v následujících scénářích:

- Nadbytečné operace. Zvažte algoritmus nebo operaci, které lze provést mnoha způsoby. Můžete použít `when_any` funkce pro výběr operace, která skončí jako první a pak zrušení zbývajících operací.

- Prokládané operace. Můžete spustit více operací, že všechny musí dokončit a použít `when_any` funkci ke zpracování výsledků při dokončení každé operace. Po dokončení jedné operace můžete spustit jednu nebo více dalších úloh.

- Omezené operace. Můžete použít `when_any` funkce k rozšíření předchozího scénáře tím, že omezíte počet souběžných operací.

- Operace, jejichž platnost vypršela. Můžete použít `when_any` funkce a vyberte jednu nebo více úloh a úlohy, která skončí po určité době.

Stejně jako u `when_all`, je běžné použití pokračování, které má `when_any` k provedení akce při dokončení první sady úkolů. V následujícím základním příkladu používá `when_any` vytvořit úlohu, která skončí po dokončení první tři dalších úkolů.

[!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]

V tomto příkladu můžete také určit `task<pair<int, size_t>>` k výrobě pokračování podle úloh.

> [!NOTE]
> Stejně jako u `when_all`, úlohy, které můžete předat `when_any` musí všichni vrátit stejný typ.

Můžete také použít `||` syntaxe pro vytvoření úlohy, která skončí po dokončení první úlohy v sadě úloh, jak je znázorněno v následujícím příkladu.

`auto t = t1 || t2; // same as when_any`

> [!TIP]
> Stejně jako u `when_all`, `when_any` je neblokující a je bezpečné volat v aplikaci UWP ve vlákně ASTA.

##  <a name="delayed-tasks"></a> Zpožděné provedení úlohy

Někdy je nutné zpoždění spuštění úlohy, dokud není splněna podmínka, nebo spuštění úlohy jako odpověď na vnější události. V asynchronním programování, například může mít na spuštění úlohy v reakci na událost dokončení vstupně-výstupních operací.

Dva způsoby, jak to provést je použití pokračování nebo spuštění úlohy a čekání na událost uvnitř pracovní funkce této úlohy. Existují však případy, kdy není možné použít některý z následujících postupů. Například chcete-li vytvořit pokračování, musíte mít předchozí úlohu. Ale pokud nemáte předchozí úlohu, můžete vytvořit *událost dokončení úkolu* a později tuto událost dokončení předchozí úlohy, až bude k dispozici. Navíc vzhledem k tomu, že úkol čekání také blokuje vlákno, můžete použít události dokončení k provedení práce po dokončení asynchronní operace a tím uvolnit vlákno.

[Concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) třídy pomáhá zjednodušit složení těchto úkolů. Podobně jako `task` třídy, parametr typu `T` je typ výsledku, který je vytvořil úkol. Tento typ může být `void` Pokud úloha nevrací hodnotu. `T` nelze použít `const` modifikátor. Obvykle `task_completion_event` zadaný objekt do vlákna nebo úlohy, které mu dají signál, jakmile je hodnota pro ni k dispozici. Ve stejnou dobu jeden nebo více úkolů nastavené jako posluchači pro tuto událost. Při nastavení události úkoly modulu listener a jejich pokračování je naplánováno ke spuštění.

Příklad, který používá `task_completion_event` k implementaci úkolu, který se dokončí po prodlevě, naleznete v tématu [postupy: vytvoření úlohy takové se dokončí po zpoždění](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md).

##  <a name="task-groups"></a> Skupiny úloh

A *skupiny úloh* uspořádá kolekci úkolů. Skupiny úloh odešlou úlohy do fronty přebírající práci. Plánovač odstraní úkoly z této fronty a provede je v dostupných výpočetních prostředcích. Jakmile přidáte úlohy do skupiny úloh, můžete počkat na dokončení nebo zrušení úlohy, které ještě nebyly spuštěny všech úloh.

PPL používá [concurrency::task_group](reference/task-group-class.md) a [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) třídy pro reprezentaci skupin úkolů a [concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md) třídy pro reprezentaci úlohy spuštěné v těchto skupinách. `task_handle` Třída zapouzdří kód, který provádí práci. Podobně jako `task` třídy, pracovní funkce dodávána ve formě funkce lambda, ukazatele na funkci nebo objektu funkce. Obvykle není potřeba pracovat `task_handle` objekty přímo. Místo toho předáte pracovní funkce pro skupinu úloh, a skupina úloh vytváří a spravuje `task_handle` objekty.

PPL dělí skupiny úkolů na těchto dvou kategorií: *nestrukturované skupiny úkolů* a *strukturované skupiny úkolů*. PPL používá `task_group` pro reprezentaci nestrukturované skupiny úkolů a `structured_task_group` pro reprezentaci strukturované skupiny úkolů.

> [!IMPORTANT]
> PPL také definuje [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus, který používá `structured_task_group` třídu pro spuštění sady úkolů současně. Vzhledem k tomu, `parallel_invoke` algoritmus využívající dlaždice má stručnější syntaxi, doporučujeme použít místo něj `structured_task_group` třídy, pokud je to možné. Téma [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md) popisuje `parallel_invoke` podrobněji.

Použití `parallel_invoke` Pokud máte několik nezávislých úloh, které chcete provést současně, a je nutné počkat na dokončení, než budete pokračovat všech úloh. Tato technika je často označuje jako *rozvětvení a spojení* paralelismu. Použití `task_group` Pokud máte několik nezávislých úloh, které chcete provést současně, ale chcete počkat na dokončení později. Například můžete přidat úkoly `task_group` objektu a počkejte na dokončení v jiné funkci nebo z jiného vlákna úloh.

Skupiny úloh podporují koncept zrušení. Zrušení umožňuje signalizovat všem aktivním úkolům, že chcete zrušit celkovou operaci. Zrušení zabrání také úlohy, které ještě nebyly spuštěny spuštění. Další informace o zrušení naleznete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).

Modul runtime poskytuje také model zpracování výjimek, pomocí kterých můžete vyvolat výjimku z úkolu a zpracovat tuto výjimku při čekání přidružené skupiny úkolů na dokončení. Další informace o tomto modelu zpracování výjimek naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

##  <a name="comparing-groups"></a> Porovnání tříd task_group a structured_task_group

Přestože doporučujeme používat `task_group` nebo `parallel_invoke` místo `structured_task_group` třídy, existují případy, ve které chcete použít `structured_task_group`, například při psaní paralelního algoritmu, který provádí proměnný počet úkolů nebo vyžaduje Podpora pro zrušení. Tato část vysvětluje rozdíly mezi `task_group` a `structured_task_group` třídy.

`task_group` Třída je bezpečná pro vlákno. Proto můžete přidávat úkoly k `task_group` objektu z více vláken a počkat nebo zrušit `task_group` objektu z více vláken. Výstavba a likvidace objektu `structured_task_group` musí proběhnout ve stejném lexikálním oboru. Kromě toho všechny operace na `structured_task_group` musí proběhnout ve stejném vlákně. Výjimkou z tohoto pravidla je [Concurrency::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) a [Concurrency::structured_task_group:: is_canceling](reference/structured-task-group-class.md#is_canceling) metody. Podřízená úloha může tyto metody volat a zrušit skupinu nadřazeného úkolu nebo zrušení kdykoli zkontrolovat.

Spustit další úkoly při `task_group` objektu po volání [Concurrency::task_group:: wait](reference/task-group-class.md#wait) nebo [Concurrency::task_group:: run_and_wait](reference/task-group-class.md#run_and_wait) metody. Naopak pokud spustíte další úkoly pro `structured_task_group` objektu po volání [Concurrency::structured_task_group:: wait](reference/structured-task-group-class.md#wait) nebo [Concurrency::structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait) metody , pak chování není definováno.

Vzhledem k tomu, `structured_task_group` třída není synchronizována přes více vláken, má nižší nároky na spuštění než `task_group` třídy. Proto pokud váš problém nevyžaduje plánování práce z více vláken a nelze použít `parallel_invoke` algoritmu `structured_task_group` třída může pomoci psát lépe uskutečnitelný kód.

Používáte-li `structured_task_group` objektu uvnitř jiného `structured_task_group` objektu, vnitřní objekt musí být dokončen a zničen, před dokončením vnějšího objektu. `task_group` Třída nevyžaduje pro skupiny vnořené úlohy dokončení před dokončením vnější skupiny.

Nestrukturované skupiny úkolů a strukturované skupiny úloh pracují s popisovači úloh různými způsoby. Pracovní funkce můžete předat přímo na `task_group` objektu; `task_group` objekt bude vytvářet a spravovat popisovač úkolu za vás. `structured_task_group` Třídy vyžaduje, abyste ke správě `task_handle` objekt pro každý úkol. Každý `task_handle` musí zůstat platný po celou dobu trvání jeho přidruženého objektu `structured_task_group` objektu. Použití [concurrency::make_task](reference/concurrency-namespace-functions.md#make_task) funkci, která vytvoří `task_handle` objektu, jak je znázorněno v následujícím základním příkladu:

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

Chcete-li spravovat rutiny úloh pro případy, které mají variabilní počet úloh, použijte rutinu přidělení zásobníku [_malloca](../../c-runtime-library/reference/malloca.md) nebo třída kontejneru, jako je například std::[vektoru](../../standard-library/vector-class.md).

Obě `task_group` a `structured_task_group` podporují zrušení. Další informace o zrušení naleznete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).

##  <a name="example"></a> Příklad

V následujícím základním příkladu ukazuje, jak pracovat se skupinami úloh. V tomto příkladu `parallel_invoke` algoritmus k provedení dvou úloh současně. Každý úkol přidá dílčí úkoly `task_group` objektu. Všimněte si, `task_group` třída umožňuje více úkolům současně přidat úkoly do něj.

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

Tady je ukázkový výstup v tomto příkladu:

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

Vzhledem k tomu, `parallel_invoke` algoritmus spustí úlohy současně, může měnit pořadí výstupu zpráv.

Kompletní příklady, které ukazují, jak používat `parallel_invoke` algoritmus, najdete v článku [postupy: použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) a [postupy: použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Úplný příklad používající `task_group` třídu pro implementaci asynchronních funkcí naleznete v tématu [návod: implementace tříd Future](../../parallel/concrt/walkthrough-implementing-futures.md).

##  <a name="robust"></a> Robustní programování

Ujistěte se, že chápete role zrušení a zpracování výjimek při použití úloh, úkolů skupiny a paralelních algoritmů. Například ve stromové struktuře paralelní práce, úkol, který je zrušen zabraňuje podřízené úlohy spuštění. To může způsobit potíže, pokud jeden z podřízených úloh provádí operaci, která je důležitá pro vaši aplikaci, jako je například uvolnění prostředku. Navíc pokud podřízená úloha vyvolá výjimku, tato výjimka může šířila destruktorem objektu a způsobila nedefinované chování ve vaší aplikaci. Příklad, který znázorňuje tyto body, najdete v článku [porozumění jak zrušení a výjimky zpracování odstraňování objektů ovlivnit](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) kapitoly osvědčené postupy v paralelních vzorcích knihovny dokumentů. Další informace o zrušení a modelech zpracování výjimek v PPL naleznete v tématu [zrušení](../../parallel/concrt/cancellation-in-the-ppl.md) a [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Ukazuje způsob použití `parallel_invoke` algoritmus pro zlepšení výkonu bitonického algoritmu řazení.|
|[Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Ukazuje způsob použití `parallel_invoke` algoritmus pro zlepšení výkonu programu, který provádí více operací na sdílený zdroj dat.|
|[Postupy: Vytvoření úlohy, která se dokončí po prodlevě](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Ukazuje způsob použití `task`, `cancellation_token_source`, `cancellation_token`, a `task_completion_event` třídy k vytvoření úlohy, která se dokončí po prodlevě.|
|[Návod: Implementace tříd future](../../parallel/concrt/walkthrough-implementing-futures.md)|Ukazuje, jak sloučit existující funkce v modulu Runtime souběžnosti do něco jiného s více.|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Popisuje PPL, který poskytuje imperativní programovací model pro vývoj souběžných aplikací.|

## <a name="reference"></a>Odkaz

[task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)

[task_completion_event – třída](../../parallel/concrt/reference/task-completion-event-class.md)

[when_all – funkce](reference/concurrency-namespace-functions.md#when_all)

[when_any – funkce](reference/concurrency-namespace-functions.md#when_any)

[task_group – třída](reference/task-group-class.md)

[parallel_invoke – funkce](reference/concurrency-namespace-functions.md#parallel_invoke)

[structured_task_group – třída](../../parallel/concrt/reference/structured-task-group-class.md)
