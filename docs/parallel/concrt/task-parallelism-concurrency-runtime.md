---
title: Úloha paralelismus (Concurrency Runtime) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- structured task groups [Concurrency Runtime]
- structured tasks [Concurrency Runtime]
- task groups [Concurrency Runtime]
- task parallelism
- tasks [Concurrency Runtime]
ms.assetid: 42f05ac3-2098-494a-ba84-737fcdcad077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4f2a1f1a5bd0b4a8ca68f3aa47f6890a11efa11
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="task-parallelism-concurrency-runtime"></a>Funkční paralelismus (Concurrency Runtime)
V Concurrency Runtime *úloh* je jednotka práce, která provádí konkrétní úlohu a obvykle běží paralelně s ostatními úkoly. Úlohy lze rozložit na další, podrobnějšího úlohy, které jsou uspořádány do *skupina úkolů*.  
  
 Úlohy se používají, když napíšete asynchronní kódu a mají některé operace se provádějí až po dokončení asynchronní operace. Můžete například použít úlohu asynchronně číst ze souboru a pak použít jiná úloha – *úkolů pokračování*, který se vysvětluje dále v tomto dokumentu – ke zpracování dat, jakmile bude k dispozici. Naopak můžete úlohy skupiny rozložit paralelní práce na menší části. Předpokládejme například, že máte rekurzivní algoritmus, který rozděluje zbývající práce na dva oddíly. Skupiny úloh můžete použít ke spuštění těchto oddílů souběžně a potom počkejte rozdělený pracovní k dokončení.  
  
> [!TIP]

>  Pokud chcete použít stejné rutiny pro každý element kolekci paralelně, používají paralelní algoritmus, jako například [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), místo úlohy nebo skupina úloh. Další informace o paralelní algoritmy najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  

  
## <a name="key-points"></a>Klíčové body  
  
-   Pokud předáte proměnné výrazu lambda odkazem, musí zaručit, že životnost tuto proměnnou ukládá až do dokončení této úlohy.  
  
-   Použití úloh ( [concurrency::task](../../parallel/concrt/reference/task-class.md) třída) při psaní asynchronní kódu. Třída úlohy používá Windows zachovalo jako jeho Plánovač, není Concurrency Runtime.  
  
-   Použijte skupiny úloh ( [concurrency::task_group](reference/task-group-class.md) – třída nebo [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus) Pokud chcete rozložit paralelní práce na menší části a potom počkejte, než pro tyto menší součásti pro dokončení.  
  
-   Použití [concurrency::task::then](reference/task-class.md#then) metodu pro vytvoření pokračování. A *pokračování* je úkol, který asynchronně spustí po dokončení jiné úlohy. Libovolný počet pokračování řetěz asynchronní práce se můžete připojit.  
  
-   Po dokončení předchozí úlohou, i když je zrušená nebo vyvolá výjimku předchozí úloha je vždy pokračování založený na úlohách naplánovat provedení.  
  
-   Použití [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) k vytvoření úlohy, která je dokončena po dokončení všech členů sadu úloh. Použití [concurrency::when_any](reference/concurrency-namespace-functions.md#when_any) k vytvoření úlohy, která je dokončena po dokončení jednoho člena sady úkolů.  

  
-   Úlohy a skupiny úloh účastnit mechanismus zrušení paralelních vzory knihovna PPL (). Další informace najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).  
  
-   Informace o tom, jak modul runtime zpracovává výjimky, které jsou vyvolány úlohy a skupiny úloh, najdete v části [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
## <a name="in-this-document"></a>V tomto dokumentu  
  
- [Použití výrazů Lambda](#lambdas)  
  
- [Úloha – třída](#task-class)  
  
- [Úloh pokračování](#continuations)  
  
- [Na základě hodnoty Versus podle úloh pokračování](#value-versus-task)  
  
- [Skládání úlohy](#composing-tasks)  
  
    - [When_all – funkce](#when-all)  
  
    - [When_any – funkce](#when-any)  
  
- [Provedení zpožděné úlohy](#delayed-tasks)  
  
- [Skupiny úloh](#task-groups)  
  
- [Porovnání task_group k structured_task_group](#comparing-groups)  
  
- [Příklad](#example)  
  
- [Robustní programování](#robust)  
  
##  <a name="lambdas"></a> Použití výrazů Lambda  
 Kvůli jejich stručného syntaxi výrazů lambda je běžný způsob, jak definovat pracovní, které se provádí pomocí úlohy a skupiny úloh. Zde jsou některé tipy využití:  
  
-   Protože úlohy jsou obvykle běží na vlákna na pozadí, pamatujte na doba života objektu, když zaznamenáte proměnné v výrazy lambda. Pokud zaznamenáte hodnotou proměnné, kopie tuto proměnnou se provádí v těle lambda. Pokud zaznamenáte odkazem kopii jiného výrobce. Proto se ujistěte, že který platnosti proměnné, které zaznamenáte odkazem outlives úlohu, která jej používá.  
  
-   Při předání výrazu lambda úlohu, není zachytit proměnné, které jsou přiděleny v zásobníku odkazem.  
  
-   Být explicitní o proměnné, které zaznamenáte v výrazy lambda, aby mohli identifikovat, co jste se zaznamenávání podle hodnoty a podle reference. Z tohoto důvodu doporučujeme, aby nepoužijete `[=]` nebo `[&]` možnosti pro výrazy lambda.  
  
 Běžný vzor je, když jeden úkol v řetězu pokračování přiřadí proměnné a jiná úloha přečte tuto proměnnou. Vzhledem k tomu, že každý úkol pokračování by obsahující kopii jinou proměnnou nelze zachytit podle hodnoty. Zásobník přidělené proměnných také nelze zachytit odkazem vzhledem k tomu, že proměnná již nebude platný.  
  
 Chcete-li tento problém vyřešit, použijte inteligentní ukazatel [std::shared_ptr](../../standard-library/shared-ptr-class.md)zabalení proměnnou a hodnotou předat chytré ukazatele. Tímto způsobem lze přiřadit k základní objekt a číst z a bude outlive úlohy, které ho používají. Tento postup použijte i v případě, že proměnná je ukazatel nebo popisovač počítá odkaz (`^`) k objektu prostředí Windows Runtime. Zde je ukázka základní:  
  
 [!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]  
  
 Další informace o výrazy lambda najdete v tématu [výrazy Lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
##  <a name="task-class"></a> Úloha – třída  
 Můžete použít [concurrency::task](../../parallel/concrt/reference/task-class.md) třídy tvoří úlohy do sady závislých operací. Tento model složení podporuje představu o *pokračování*. Kód umožňuje pokračování při spouštění předchozí, nebo *předchůdce*, dokončení úlohy. Jako vstup do jedné nebo více úloh pokračování je předán výsledek předchozí úlohou. Po dokončení předchozí úlohou všech úkolů pokračování, které čekají na něm je naplánováno spuštění. Každý úkol pokračování obdrží kopii výsledek předchozí úlohou. Tyto úlohy pokračování se pak může být předchozí úlohy pro ostatní pokračování, a vytvoří tak řetěz úlohy. Pokračování vám pomůže vytvořit řetězy libovolný délku úloh, které mají konkrétní závislosti mezi nimi. Kromě toho můžete úlohu zúčastnit, zrušení buď před úlohy spustí nebo spolupráci způsobem je spuštěna. Další informace o tomto modelu zrušení najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).  
  
 `task` je třída šablony. Parametr typu `T` je typ výsledku, která je vytvořena úloha. Tento typ může být `void` Pokud úloha nevrací hodnotu. `T` nelze použít `const` modifikátor.  
  
 Když vytvoříte úlohu, zadejte *pracovní funkce* který provede těla úkolu. Tato funkce pracovní obsahuje ve formě funkce lambda, – ukazatel na funkci nebo funkce objektu. Počkat na dokončení bez získání výsledek úlohy, volání [concurrency::task::wait](reference/task-class.md#wait) metoda. `task::wait` Metoda vrátí [concurrency::task_status](reference/concurrency-namespace-enums.md#task_group_status) hodnotu, která popisuje, zda byl úlohu dokončit nebo zrušit. Chcete-li získat výsledek úlohy, zavolejte [concurrency::task::get](reference/task-class.md#get) metoda. Tato metoda volá `task::wait` počkal výsledek je k dispozici pro úlohu dokončit, a proto bloky provádění aktuální vlákno.  
  
 Následující příklad ukazuje postup vytvoření úlohy, počkejte na její výsledek a zobrazit jeho hodnotu. V příkladech v této dokumentaci pomocí funkcí lambda, protože poskytují více stručného syntaxe. Však také můžete ukazatelů na funkce a objekty funkcí při použití úlohy.  
  
 [!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]  
  

 Při použití [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) funkce, můžete použít `auto` – klíčové slovo místo deklarace typu. Představte si třeba tento kód, který vytvoří a vytiskne matice identity:  

  
 [!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]  
  
 Můžete použít `create_task` funkce vytvořit ekvivalentní operaci.  
  
 [!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]  
  
 Pokud během provádění úlohy je vyvolána výjimka, modul runtime zařazuje této výjimky v následných volání `task::get` nebo `task::wait`, nebo pokračování založený na úlohách. Další informace o mechanismus zpracování výjimek úloh najdete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 Pro příklad, který používá `task`, [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), zrušení, najdete v části [návod: připojení pomocí úloh a žádostí XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). ( `task_completion_event` Třída je popsán dále v tomto dokumentu.)  
  
> [!TIP]
>  Další podrobnosti, které jsou specifické pro úlohy v aplikacích pro UPW najdete v tématu [asynchronní programování v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) a [vytváření asynchronních operací v jazyce C++ pro aplikace UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).  
  
##  <a name="continuations"></a> Úloh pokračování  
 V asynchronní programování, je velmi běžné jeden asynchronní operaci na dokončení pro vyvolání druhá operace a předat data. Tradičně to se provádí pomocí metody zpětného volání. V Concurrency Runtime stejné funkce poskytované *úloh pokračování*. Úloha pokračování (známou taky stejně jako pokračování) je asynchronní úkol, který je vyvolán jiná úloha, která se označuje jako *předchůdce*, jakmile je předchůdce dokončen. Pomocí pokračování můžete:  
  
-   Předejte data z předchůdce pokračování.  
  
-   Zadejte přesné podmínky, za kterých je pokračování vyvolat nebo není vyvolána.  
  
-   Zrušení pokračování buď před spuštěním nebo spolupráce při jejím průběhu.  
  
-   Poskytnout nápovědu, jak má být naplánováno pokračování. (To se týká pouze aplikací univerzální platformu Windows (UWP). Další informace najdete v tématu [vytváření asynchronních operací v jazyce C++ pro aplikace UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).)  
  
-   Vyvolání více pokračování ze stejného předchůdce.  
  
-   Po dokončení všech nebo některých více předchůdců vyvolejte jedno pokračování.  
  
-   Zřetězené pokračování jedna po druhé jakékoli délky.  
  
-   Zpracování výjimek, které jsou vyvolány předchůdce pomocí pokračování.  
  
 Tyto funkce umožňují spuštění jedné nebo více úloh po dokončení prvního úkolu. Můžete například vytvořit pokračování, které se soubor zkomprimuje po první úlohou přečte ji z disku.  
  


 Následující příklad změní předchozímu používat [concurrency::task::then](reference/task-class.md#then) metoda při plánování pokračování, které se vytiskne hodnota předchozí úloha v případě, že je k dispozici.  


  
 [!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]  
  
 Můžete řetězu a vnořit úlohy pro jakékoli délky. Úloha může mít více pokračování. Následující příklad ilustruje řetěz základní pokračování, který zvýší hodnota předchozí úloha třikrát.  
  
 [!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]  
  
 Pokračování můžete se taky vrátit jiná úloha. Pokud není žádná zrušení, tento úkol provést před následné pokračování. Tento postup se označuje jako *asynchronní rozbalování*. Asynchronní rozbalování je užitečné, když chcete provést další práce na pozadí, ale nechcete, aby aktuální úlohy pro blokování aktuální vlákno. (To je běžné v aplikacích pro UPW, kde můžete spustit pokračování ve vlákně UI). Následující příklad ukazuje tři úlohy. První úlohou vrátí jiný úkol, který je spustit před spuštěním úkolů pokračování.  
  
 [!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]  
  
> [!IMPORTANT]
>  Při pokračování úlohy vrátí vnořené úlohy typu `N`, výsledná úloha má typ `N`, nikoli `task<N>`a dokončí při dokončení vnořené úlohy. Jinými slovy pokračování provádí rozbalování vnořené úlohy.  
  
##  <a name="value-versus-task"></a> Na základě hodnoty Versus podle úloh pokračování  
 Zadané `task` objekt, jehož návratový typ `T`, můžete zadat hodnotu typu `T` nebo `task<T>` pro její úkoly pokračování. Pokračování, která přebírá typ `T` se označuje jako *na základě hodnoty pokračování*. Pokračování na základě hodnoty je naplánováno spuštění při předchozí úloha dokončí bez chyby a není zrušena. Pokračování, která přebírá typ `task<T>` jako jeho parametr se nazývá *založený na úlohách pokračování*. Po dokončení předchozí úlohou, i když je zrušená nebo vyvolá výjimku předchozí úloha je vždy pokračování založený na úlohách naplánovat provedení. Potom můžete volat `task::get` získat výsledek předchozí úlohou. Pokud předchozí úloha byla zrušena, `task::get` vyvolá [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). Pokud předchozí úlohou došlo k výjimce `task::get` znovu vyvolá této výjimky. Pokračování založený na úlohách není označena jako zrušit, když je zrušeno jeho předchozí úlohou.  
  
##  <a name="composing-tasks"></a> Skládání úlohy  
 Tato část popisuje [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) a [concurrency::when_any](reference/concurrency-namespace-functions.md#when_all) funkce, které vám můžou pomoct vytvořit více úloh k implementaci běžných vzorů.  

  
###  <a name="when-all"></a> When_all – funkce  
 `when_all` Funkce vytvoří úlohu, která je dokončena po dokončení sadu úloh. Tato funkce vrátí std::[vektoru](../../standard-library/vector-class.md) objekt obsahující výsledek každé úlohy v sadě. Následující příklad základní používá `when_all` k vytvoření úlohy, která představuje dokončení tři další úlohy.  
  
 [!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]  
  
> [!NOTE]
>  Úlohy, které můžete předat `when_all` musí být uniform. Jinými slovy musí všechny vracejí stejného typu.  
  
 Můžete také `&&` syntaxe vytvořit úlohu, která je dokončena po dokončení sadu úloh, jak je znázorněno v následujícím příkladu.  
  
 `auto t = t1 && t2; // same as when_all`  
  
 Je běžné použití pokračování společně s `when_all` k provedení akce po dokončení sadu úloh. Následující příklad změní předchozímu tisknout součet tři úlohy každou vytvořit `int` výsledek.  
  
 [!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]  
  
 V tomto příkladu můžete také zadat `task<vector<int>>` k vytvoření pokračování založený na úlohách.  
  
 Pokud všechny úlohy v sadu úloh, je zrušená nebo vyvolá výjimku, `when_all` okamžitě dokončí a nečeká na dokončení zbývajících úkolů. Pokud je vyvolána výjimka, modul runtime znovu vyvolá výjimku při volání `task::get` nebo `task::wait` v úloze objektu, který `when_all` vrátí. Pokud vyvolá více než jeden úkol, modul runtime zvolí jeden z nich. Proto se ujistěte, že všechny výjimky zjistíte po dokončení všech úloh; výjimky neošetřené úloh způsobí, že aplikaci ukončit.  
  
 Tady je nástroj funkci, která můžete použít k zajištění, že váš program zaznamenává všechny výjimky. Pro každý úkol v zadaný rozsah `observe_all_exceptions` aktivuje žádné výjimka, která do být znovu vyvolány došlo k chybě a pak swallows této výjimky.  
  
 [!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]  
  
 Vezměte v úvahu aplikace pro UPW, která používá C++ a XAML a zapíše sadu souborů na disk. Následující příklad ukazuje, jak používat `when_all` a `observe_all_exceptions` zajistit, že program zaznamenává všechny výjimky.  
  
 [!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]  
  
##### <a name="to-run-this-example"></a>Pro spuštění tohoto příkladu  
  
1.  V MainPage.xaml, přidejte `Button` ovládacího prvku.  
  
 [!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]  
  
2.  V MainPage.xaml.h, přidejte tyto dopředného deklarace, abyste `private` části `MainPage` deklarace třídy.  
  
 [!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]  
  
3.  V MainPage.xaml.cpp, implementovat `Button_Click` obslužné rutiny události.  
  
 [!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]  
  
4.  V MainPage.xaml.cpp, implementovat `WriteFilesAsync` jak je znázorněno v příkladu.  
  
> [!TIP]

> `when_all` je neblokující funkce, která vytváří `task` jako svůj výsledek. Na rozdíl od [Task::wait –](reference/task-class.md#wait), je bezpečné volat tuto funkci v aplikaci UWP ve vlákně ASTA (STA aplikace).  

  
###  <a name="when-any"></a> When_any – funkce  
 `when_any` Funkce vytvoří úlohu, která se dokončí po dokončení první úlohou sadu úloh. Funkce vrátí hodnotu [std::pair](../../standard-library/pair-structure.md) objekt obsahující výsledek dokončené úlohy a index této úlohy v sadě.  
  
 `when_any` Funkce je obzvláště užitečná v následujících scénářích:  
  
-   Nadbytečné operace. Zvažte algoritmus nebo operaci, které lze provést mnoha způsoby. Můžete použít `when_any` funkce vyberte operaci, nejprve dokončí a poté zrušte zbývajících operací.  
  
-   Prokládané operace. Můžete spustit více operací všechny musíte dokončit a použít `when_any` funkce zpracovat výsledky, protože dokončení jednotlivých operací. Po dokončení jedné operace můžete spustit jednu nebo více dalších úloh.  
  
-   Omezené operace. Můžete použít `when_any` funkce rozšířit předchozím scénáři omezením počet souběžných operací.  
  
-   Operace, jejichž platnost vypršela. Můžete použít `when_any` funkce můžete vybrat, jestli jeden nebo více úloh a úlohu, která se dokončí po určité době.  
  
 Stejně jako u `when_all`, je běžné použití pokračování, který má `when_any` k provedení akce při dokončení první sadu úloh. Následující příklad základní používá `when_any` k vytvoření úlohy, která se dokončí po dokončení první tři další úlohy.  
  
 [!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]  
  
 V tomto příkladu můžete také zadat `task<pair<int, size_t>>` k vytvoření pokračování založený na úlohách.  
  
> [!NOTE]
>  Stejně jako u `when_all`, úlohy, které můžete předat `when_any` musí vracet stejného typu.  
  
 Můžete také `||` syntaxe vytvořit úlohu, která je dokončena po dokončení první úlohou sadu úloh, jak je znázorněno v následujícím příkladu.  
  
 `auto t = t1 || t2; // same as when_any`  
  
> [!TIP]
>  Stejně jako u `when_all`, `when_any` neblokující a je bezpečné volat v aplikaci UWP ve vlákně ASTA.  
  
##  <a name="delayed-tasks"></a> Provedení zpožděné úlohy  
 Někdy je nezbytné ke zpoždění spuštění úlohy, dokud je podmínka, nebo úlohu lze spustit v reakci na externí událost. Například v asynchronní programování, můžete chtít spustit úlohu v reakci na událost dokončení vstupně-výstupní operace.  
  
 Použití pokračování nebo ke spuštění úlohy a čekání na událost uvnitř úkolu pracovní funkce jsou dva způsoby, jak dosáhnout. Ale existují případy, kdy není možné použít jednu z těchto postupů. Například pokud chcete vytvořit pokračování, musí mít předchozí úlohou. Ale pokud nemáte předchozí úlohou, můžete vytvořit *událost dokončení úlohy* a později řetězu danou událost dokončení pro předchozí úlohou, až bude k dispozici. Navíc vzhledem k tomu, že úloha čekání blokuje taky vlákno, můžete použít událostí dokončení úlohy pro práci při dokončení asynchronní operace a tím volné vlákno.  
  
 [Concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) třída pomáhá zjednodušit takové složení úlohy. Podobně jako `task` třídy, parametr typu `T` je typ výsledku, která je vytvořena úloha. Tento typ může být `void` Pokud úloha nevrací hodnotu. `T` nelze použít `const` modifikátor. Obvykle `task_completion_event` objekt zajišťuje přístup z více vláken nebo úloha, která bude signalizován jeho hodnota je k dispozici. Ve stejnou dobu jeden nebo více úloh, jsou nastavené jako naslouchací procesy této události. Pokud je nastavená události, dokončete úlohy naslouchací proces a jejich pokračování mají naplánované spuštění.  
  
 Pro příklad, který používá `task_completion_event` implementovat úlohu, která je dokončena po prodlevě, najdete v části [postupy: vytvoření úlohy, že dokončení po zpoždění](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md).  
  
##  <a name="task-groups"></a> Skupiny úloh  
 A *skupina úkolů* organizuje kolekce úloh. Skupiny úloh push úlohy do fronty pracovní krádež. Plánovač úloh odebere z této fronty a je spouštěna v dostupných výpočetních prostředcích. Po přidání úloh pro skupinu úloh, můžete počkat pro všechny úkoly můžete dokončit nebo zrušit úlohy, které ještě nebyly spustili.  
  
 Používá knihovně PPL [concurrency::task_group](reference/task-group-class.md) a [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) třídy představující skupin úloh a [concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md) – třída představují úkoly spuštěné v těchto skupinách. `task_handle` Třída zapouzdří kód, který provede práci. Podobně jako `task` třídy, pracovní funkce obsahuje ve formě funkce lambda, – ukazatel na funkci nebo funkce objektu. Obvykle není nutné pro práci s `task_handle` objekty přímo. Místo toho předat pracovních funkcí pro skupinu úloh, a skupině úloh vytváří a spravuje `task_handle` objekty.  
  
 Knihovně PPL rozděluje skupiny úloh do těchto dvou kategorií: *skupiny nestrukturovaných úloh* a *strukturovaná skupiny úloh*. Používá knihovně PPL `task_group` třída k reprezentování skupiny nestrukturovaných úloh a `structured_task_group` třída k reprezentování skupiny strukturovaných úloh.  
  
> [!IMPORTANT]

>  Knihovně PPL definuje také [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus, který používá `structured_task_group` třída spustí sadu úloh paralelně. Protože `parallel_invoke` algoritmus má více stručného syntaxi, doporučujeme používat ji místo `structured_task_group` třídy, pokud to bude možné. Téma [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md) popisuje `parallel_invoke` podrobněji.  
  
 Použití `parallel_invoke` Pokud máte několik nezávislých úlohy, které chcete provést ve stejnou dobu, a je nutné počkat na dokončeno předtím, než budete pokračovat všech úloh. Tento postup se často označuje jako *větve a připojení k* stupně paralelního zpracování. Použití `task_group` Pokud máte několik nezávislých úkolů, které chcete provést ve stejnou dobu, ale chcete čekat na dokončení později úkolů. Například můžete přidat na úlohy `task_group` objektu a počkejte na dokončení v jiné funkce nebo z jiného vlákna úkolů.  
  
 Skupiny úloh podporují koncept zrušení. Zrušení umožňuje signál všechny aktivní úlohy chcete zrušit celou operaci. Zrušení rovněž zamezí úlohy, které nebyly ještě nezačala spuštění. Další informace o zrušení najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).  
  
 Modul runtime také poskytuje model zpracování výjimek, která umožňuje vyvolat výjimku z úlohy a zpracování této výjimky, je-li čekat na skupině úloh přidružených k dokončení. Další informace o tento model zpracování výjimek najdete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
##  <a name="comparing-groups"></a> Porovnání task_group k structured_task_group  
 I když vám doporučujeme používat `task_group` nebo `parallel_invoke` místo `structured_task_group` třídy, ale existují případy, ve které chcete použít `structured_task_group`, například při psaní paralelní algoritmus, který provádí proměnný počet úloh nebo vyžaduje Podpora pro zrušení. Tato část vysvětluje rozdíly mezi `task_group` a `structured_task_group` třídy.  
  
 `task_group` Třída je bezpečné pro přístup z více vláken. Proto můžete přidat na úlohy `task_group` objektů z více vláken a počkejte nebo zrušit `task_group` objektů z více vláken. Vytváření a zničení `structured_task_group` objekt musí být stejné ve stejném lexikální oboru. Kromě toho, všechny operace v `structured_task_group` objekt musí být stejné ve stejném vlákně. Výjimka, která má toto pravidlo je [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) a [concurrency::structured_task_group::is_canceling](reference/structured-task-group-class.md#is_canceling) metody. Tyto metody a zrušení úloh nadřazené skupiny, nebo zaškrtněte pro zrušení kdykoli můžete volat podřízené úlohy.  
  
 Další úlohy můžete spustit na `task_group` objektu po zavolání metody [concurrency::task_group::wait](reference/task-group-class.md#wait) nebo [concurrency::task_group::run_and_wait](reference/task-group-class.md#run_and_wait) metoda. Naopak pokud spustíte další úkoly `structured_task_group` objektu po zavolání metody [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait) nebo [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) metody , pak toto chování nedefinovaný.  
  
 Protože `structured_task_group` třídu nebude synchronizovat napříč vlákny, má méně provádění režii než `task_group` třídy. Proto pokud váš problém, který nevyžaduje plánování práce z více vláken a nemůžete použít `parallel_invoke` algoritmus, `structured_task_group` třída může pomoci psát lépe provádění kódu.  
  
 Pokud použijete jeden `structured_task_group` objekt uvnitř jiné `structured_task_group` objektu, vnitřní objekt se musí ukončit a být zničený, před dokončením vnější objekt. `task_group` Třída nevyžaduje, aby vnořené úlohy skupiny dokončeno předtím, než se dokončí vnější skupiny.  
  
 Skupiny úloh nestrukturovaných a skupiny strukturovaných úloh pracovat úloh zpracovává různými způsoby. Můžete přímo na předat pracovních funkcí `task_group` objektu; `task_group` objektu bude vytvářet a spravovat úlohy popisovač pro vás. `structured_task_group` Třída vyžaduje, abyste ke správě `task_handle` objekt pro každou úlohu. Každý `task_handle` objekt musí zůstat platné během doby životnosti přidružené `structured_task_group` objektu. Použití [concurrency::make_task](reference/concurrency-namespace-functions.md#make_task) funkce k vytvoření `task_handle` objektu, jak je znázorněno v následujícím příkladu základní:  
  
 [!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]  
  
 Ke správě úloh obslužné rutiny pro případy, kdy máte proměnný počet úloh, použijte rutinu přidělení zásobníku [_malloca –](../../c-runtime-library/reference/malloca.md) nebo třídy kontejneru, například – std::[vektoru](../../standard-library/vector-class.md).  
  
 Obě `task_group` a `structured_task_group` podporují zrušení. Další informace o zrušení najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).  
  
##  <a name="example"></a> Příklad  
 Základní následující příklad ukazuje, jak pracovat s skupiny úloh. Tento příklad používá `parallel_invoke` algoritmus provést dvě úlohy současně. Každý úkol přidá dílčí úkoly k `task_group` objektu. Všimněte si, že `task_group` třída umožňuje více úlohy přidat úkoly k němu současně.  
  
 [!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]  
  
 Následuje příklad výstupu v tomto příkladu:  
  
```Output  
Message from task: Hello  
Message from task: 3.14  
Message from task: 42  
```  
  
 Protože `parallel_invoke` algoritmus spouští úlohy souběžně, pořadí zprávy výstup může lišit.  
  
 Pro dokončení příklady, které ukazují, jak používat `parallel_invoke` algoritmus, najdete v části [postupy: použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) a [postupy: použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Úplný příklad používající `task_group` třída implementace tříd Future asynchronní, najdete v článku [návod: implementace tříd Future](../../parallel/concrt/walkthrough-implementing-futures.md).  
  
##  <a name="robust"></a> Robustní programování  
 Ujistěte se, že rozumíte roli zrušení a zpracování výjimek při použití úlohy, skupin úloh a paralelní algoritmy. Například ve stromu paralelní pracovní úlohu, která se zruší, zabraňuje podřízené úlohy spuštění. To může způsobit problémy, pokud jeden z podřízené úlohy provádí operaci, která je důležité pro vaši aplikaci, třeba uvolnění prostředku. Kromě toho pokud podřízené úlohy vyvolá výjimku, této výjimky může rozšíří v rámci destruktoru objektu a způsobit nedefinované chování vaší aplikace. Příklad, který znázorňuje tyto body, najdete v článku [Rady pro pochopení jak zrušení a výjimky zpracování odstranění objektu ovlivnit](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) část v osvědčené postupy v dokumentu paralelní vzory knihovny. Další informace o zrušení a modely zpracování výjimek v knihovně PPL najdete v tématu [zrušení](../../parallel/concrt/cancellation-in-the-ppl.md) a [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Použití algoritmu parallel_invoke k zápisu rutiny paralelního třídění](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Ukazuje, jak používat `parallel_invoke` algoritmus ke zlepšení výkonu algoritmus bitonic řazení.|  
|[Postupy: Použití algoritmu parallel_invoke k provádění paralelních operací](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Ukazuje, jak používat `parallel_invoke` algoritmus ke zlepšení výkonu programu, který provádí víc operací na sdílený zdroj dat.|  
|[Postupy: Vytvoření úlohy, která se dokončí po prodlevě](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Ukazuje, jak používat `task`, `cancellation_token_source`, `cancellation_token`, a `task_completion_event` třídy k vytvoření úlohy, která je dokončena po prodlevě.|  
|[Návod: Implementace tříd future](../../parallel/concrt/walkthrough-implementing-futures.md)|Ukazuje, jak kombinovat stávajících funkcí v Concurrency Runtime na něco jiného, který nemá informace.|  
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Popisuje PPL, která poskytuje imperativní programovací model pro vývoj souběžných aplikací.|  
  
## <a name="reference"></a>Odkaz  
 [task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)  
  
 [task_completion_event – třída](../../parallel/concrt/reference/task-completion-event-class.md)  

 [when_all – funkce](reference/concurrency-namespace-functions.md#when_all)  
  
 [when_any – funkce](reference/concurrency-namespace-functions.md#when_any)  
  
 [task_group – třída](reference/task-group-class.md)  
  
 [parallel_invoke – funkce](reference/concurrency-namespace-functions.md#parallel_invoke)  
  
 [structured_task_group – třída](../../parallel/concrt/reference/structured-task-group-class.md)
