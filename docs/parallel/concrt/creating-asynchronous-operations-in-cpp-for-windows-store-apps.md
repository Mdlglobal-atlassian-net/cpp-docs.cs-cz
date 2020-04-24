---
title: Vytváření asynchronních operací v jazyce C++ pro aplikace UPW
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: 635a8c95a3801c6e88feff1cefa3ed27727a8f88
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032184"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>Vytváření asynchronních operací v jazyce C++ pro aplikace UPW

Tento dokument popisuje některé klíčové body, které je třeba mít na paměti při použití třídy úloh k vytvoření asynchronních operací založených na systému Windows ThreadPool v aplikaci Universal Windows Runtime (UPW).

Použití asynchronního programování je klíčovou součástí modelu aplikace Prostředí Windows Runtime, protože umožňuje aplikacím zůstat responzivní na vstup uživatele. Můžete spustit dlouhotrvající úlohu bez blokování vlákna uživatelského rozhraní a výsledky úlohy můžete získat později. Můžete také zrušit úkoly a přijímat oznámení o průběhu, když jsou úlohy spuštěny na pozadí. Asynchronní programování dokumentu [v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) poskytuje přehled asynchronního vzoru, který je k dispozici ve Visual C++ pro vytváření aplikací UPW. Tento dokument učí, jak využívat a vytvářet řetězce asynchronních operací prostředí Windows Runtime. Tato část popisuje, jak používat typy v ppltasks.h k výrobě asynchronních operací, které mohou být spotřebovány jinou komponentou prostředí Windows Runtime a jak řídit, jak se provádí asynchronní práce. Zvažte také čtení [asynchronní programovací vzory a tipy v Hilo (Windows Store aplikace pomocí C++ a XAML)](/previous-versions/windows/apps/jj160321(v=win.10)) se dozvíte, jak jsme použili třídu úloh k implementaci asynchronních operací v Hilo, Windows Runtime aplikace pomocí C ++ a XAML.

> [!NOTE]
> Knihovnu [paralelních vzorů](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) a [knihovnu asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) můžete použít v aplikaci UPW. Nelze však použít Plánovač úloh nebo Správce prostředků. Tento dokument popisuje další funkce, které poskytuje PPL, které jsou k dispozici pouze pro aplikaci UPW a ne pro desktopovou aplikaci.

## <a name="key-points"></a>Klíčové body

- [Souběžnost::create_async](reference/concurrency-namespace-functions.md#create_async) slouží k vytvoření asynchronních operací, které mohou být použity jinými součástmi (které mohou být napsány v jiných jazycích než C++).

- Použití [souběžnosti::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) hlásit oznámení o průběhu součástem, které volají vaše asynchronní operace.

- Pomocí tokenů zrušení povolte zrušení interních asynchronních operací.

- Chování `create_async` funkce závisí na návratový typ pracovní funkce, která je předána do něj. Pracovní funkce, která vrací `task<T>` úlohu (buď nebo `task<void>`) spustí `create_async`synchronně v kontextu, který volal . Pracovní funkce, `T` která `void` vrací nebo běží v libovolném kontextu.

- [Souběžnost::task::then](reference/task-class.md#then) metodu můžete použít k vytvoření řetězce úloh, které běží jeden po druhém. V aplikaci UPW výchozí kontext pro pokračování úkolu závisí na tom, jak byl tento úkol vytvořen. Pokud byla úloha vytvořena předáním asynchronní akce konstruktoru úkolu nebo předáním výrazu lambda, který vrací asynchronní akci, pak je výchozím kontextem pro všechna pokračování tohoto úkolu aktuální kontext. Pokud úloha není vytvořena z asynchronní akce, pak libovolný kontext se používá ve výchozím nastavení pro pokračování úlohy. Výchozí kontext můžete přepsat třídou [souběžnosti::task_continuation_context.](../../parallel/concrt/reference/task-continuation-context-class.md)

## <a name="in-this-document"></a>V tomto dokumentu

- [Vytváření asynchronních operací](#create-async)

- [Příklad: Vytvoření součásti prostředí Windows Runtime pro systém C++](#example-component)

- [Řízení podprocesu spuštění](#exethread)

- [Příklad: Řízení provádění v aplikaci prostředí Windows Runtime s C++ a XAML](#example-app)

## <a name="creating-asynchronous-operations"></a><a name="create-async"></a>Vytváření asynchronních operací

Model úloh a pokračování v knihovně paralelních vzorů (PPL) můžete použít k definování úloh na pozadí a dalších úloh, které se spustí po dokončení předchozí úlohy. Tato funkce je poskytována [třídou souběžnosti::task.](../../parallel/concrt/reference/task-class.md) Další informace o tomto `task` modelu a třídě naleznete v tématu [Paralelismus úlohy](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Prostředí Windows Runtime je programovací rozhraní, které můžete použít k vytvoření aplikací UPW, které běží pouze ve speciálním prostředí operačního systému. Tyto aplikace používají autorizované funkce, datové typy a zařízení a jsou distribuovány z obchodu Microsoft Store. Prostředí Windows Runtime je reprezentováno *binárním rozhraním aplikace* (ABI). ABI je základní binární kontrakt, který zpřístupňuje rozhraní API prostředí Windows Runtime pro programovací jazyky, jako je visual c++.

Pomocí prostředí Windows Runtime můžete použít nejlepší funkce různých programovacích jazyků a zkombinovat je do jedné aplikace. Můžete například vytvořit uI v Jazyce JavaScript a provést logiku aplikace náročné na výpočty v komponentě Jazyka C++. Schopnost provádět tyto výpočtově náročné operace na pozadí je klíčovým faktorem pro udržení odezvy uživatelského rozhraní. Vzhledem `task` k tomu, že třída je specifická pro C++, musíte použít rozhraní prostředí Windows Runtime ke komunikaci asynchronních operací s jinými součástmi (které mohou být napsány v jiných jazycích než C++). Prostředí Windows Runtime poskytuje čtyři rozhraní, která lze použít k reprezentaci asynchronních operací:

[Windows::Foundation::IAsyncAction](/uwp/api/windows.foundation.iasyncaction)<br/>
Představuje asynchronní akci.

[Windows::Foundation::IAsyncActionWithProgress\<TProgress>](/uwp/api/windows.foundation.iasyncactionwithprogress-1)<br/>
Představuje asynchronní akci, která hlásí průběh.

[Windows::Foundation::IAsyncOperation\<TResult>](/uwp/api/windows.foundation.iasyncoperation-1)<br/>
Představuje asynchronní operaci, která vrací výsledek.

[Windows::Foundation::IAsyncOperationWithProgress\<TResult, TProgress>](/uwp/api/windows.foundation.iasyncoperationwithprogress-2)<br/>
Představuje asynchronní operaci, která vrací výsledek a hlásí průběh.

Pojem *akce* znamená, že asynchronní úloha nevytváří hodnotu (představte si funkci, která vrátí). `void` Pojem *operace* znamená, že asynchronní úloha vytváří hodnotu. Pojem *průběhu* znamená, že úkol může hlásit zprávy o průběhu volajícímu. JavaScript, rozhraní .NET Framework a Visual C++ poskytují svůj vlastní způsob vytváření instancí těchto rozhraní pro použití přes hranice ABI. Pro Visual C++ ppl poskytuje [funkci souběžnosti::create_async.](reference/concurrency-namespace-functions.md#create_async) Tato funkce vytvoří asynchronní akci nebo operaci prostředí Windows Runtime, která představuje dokončení úlohy. Funkce `create_async` přebírá pracovní funkci (obvykle výraz lambda), interně vytvoří `task` objekt a zabalí tuto úlohu do jednoho ze čtyř asynchronních rozhraní prostředí Windows Runtime.

> [!NOTE]
> Používejte `create_async` pouze v případě, že máte k vytvoření funkce, která je přístupná z jiného jazyka nebo jiné součásti prostředí Windows Runtime. Třídu `task` použijte přímo, pokud víte, že operace je vyráběna a spotřebována kódem jazyka C++ ve stejné součásti.

Návratový `create_async` typ je určen typem jeho argumentů. Pokud například pracovní funkce nevrací hodnotu a nehlásí `create_async` průběh, vrátí . `IAsyncAction` Pokud vaše pracovní funkce nevrátí hodnotu a `create_async` také `IAsyncActionWithProgress`hlásí průběh, vrátí . Chcete-li ohlásit průběh, zadejte [objekt concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) jako parametr pracovní funkce. Možnost hlásit průběh umožňuje hlásit, jaké množství práce bylo provedeno a jaká částka stále zůstává (například v procentech). Umožňuje také vykazovat výsledky, jakmile budou k dispozici.

Rozhraní `IAsyncAction` `IAsyncActionWithProgress<TProgress>`, `IAsyncOperation<TResult>`a `IAsyncActionOperationWithProgress<TProgress, TProgress>` rozhraní poskytují `Cancel` metodu, která umožňuje zrušit asynchronní operaci. Třída `task` pracuje s tokeny zrušení. Při použití tokenzrušení zrušit práci, runtime nespustí novou práci, která se přihlásí k odběru tohoto tokenu. Práce, která je již aktivní můžete sledovat jeho zrušení token a zastavit, když je to možné. Tento mechanismus je podrobněji popsán v dokumentu [Zrušení v PPL](cancellation-in-the-ppl.md). Zrušení úlohy můžete propojit s`Cancel` metodami prostředí Windows Runtime dvěma způsoby. Nejprve můžete definovat pracovní funkci, `create_async` kterou předáte, aby se [souběžnost::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) objekt. Při `Cancel` volání metody je tento token zrušení zrušen a normální pravidla `task` zrušení platí `create_async` pro základní objekt, který podporuje volání. Pokud nezadáte `cancellation_token` objekt, základní `task` objekt definuje jeden implicitně. Definujte `cancellation_token` objekt, když potřebujete kooperativně reagovat na zrušení ve vaší pracovní funkci. [Příklad: Řízení provádění v aplikaci prostředí Windows Runtime s C++ a XAML](#example-app) ukazuje příklad, jak provést zrušení v aplikaci univerzální platformy Windows (UPW) s C# a XAML, který používá vlastní komponentu Windows Runtime C++.

> [!WARNING]
> V řetězci pokračování úkolu vždy vyčistěte stav a potom volejte [souběžnost::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) při zrušení tokenu zrušení. Pokud vrátíte brzy `cancel_current_task`namísto volání , operace přechody do stavu dokončení namísto zrušeného stavu.

Následující tabulka shrnuje kombinace, které můžete použít k definování asynchronních operací ve vaší aplikaci.

|Vytvoření tohoto rozhraní prostředí Windows Runtime|Vrátit tento typ z`create_async`|Předejte tyto typy parametrů pracovní funkci, abyste použili implicitní token zrušení.|Předejte tyto typy parametrů své pracovní funkci a použijte explicitní token zrušení.|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|`void` nebo `task<void>`|(žádná)|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|`void` nebo `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` nebo `task<T>`|(žádná)|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` nebo `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

Můžete vrátit hodnotu `task` nebo objekt z pracovní funkce, `create_async` kterou předáte funkci. Tyto varianty vytvářejí různé chování. Když vrátíte hodnotu, pracovní funkce je `task` zabalena v tak, aby ji lze spustit na podprocesu na pozadí. Kromě toho podkladové `task` používá implicitní token zrušení. Naopak pokud vrátíte `task` objekt, pracovní funkce spustí synchronně. Proto pokud vrátíte `task` objekt, ujistěte se, že všechny zdlouhavé operace ve vaší pracovní funkci také spustit jako úkoly, aby vaše aplikace zůstat responzivní. Kromě toho podkladové `task` nepoužívá implicitní token zrušení. Proto je třeba definovat pracovní funkce, `cancellation_token` aby objekt, pokud požadujete `task` podporu `create_async`pro zrušení při vrácení objektu z .

Následující příklad ukazuje různé způsoby `IAsyncAction` vytvoření objektu, který může být spotřebován jinou komponentou prostředí Windows Runtime.

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

## <a name="example-creating-a-c-windows-runtime-component-and-consuming-it-from-c"></a><a name="example-component"></a>Příklad: Vytvoření součásti prostředí Windows Runtime pro systém C++ a její spotřeba z jazyka C\#

Zvažte aplikaci, která používá XAML a C# k definování uživatelského prostředí a komponenty Prostředí Windows Runtime pro prostředí C++ windows runtime k provádění operací náročných na výpočetní výkon. V tomto příkladu komponenta C++ vypočítá, která čísla v daném rozsahu jsou prvočísla. Chcete-li ilustrovat rozdíly mezi čtyřmi asynchronními rozhraními modulu Windows Runtime, spusťte `Primes`v sadě Visual Studio vytvořením **prázdného řešení** a jeho pojmenováním . Potom přidejte do řešení projekt **součásti prostředí Windows Runtime a** pojmenujte jej `PrimesLibrary`. Přidejte následující kód do generovaného souboru hlaviček jazyka C++ (tento příklad přejmenuje Class1.h na Primes.h). Každá `public` metoda definuje jedno ze čtyř asynchronních rozhraní. Metody, které vracejí hodnotu, vrátí objekt [Windows::Foundation::Collections::IVector\<int>](/uwp/api/windows.foundation.collections.ivector-1) objekt. Metody, které hlásí `double` průběh, vytvářejí hodnoty, které definují procento celkové dokončené práce.

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
> Podle konvence asynchronní metody názvy v prostředí Windows Runtime obvykle končí "Async".

Přidejte následující kód do generovaného zdrojového souboru C++ (tento příklad přejmenuje Class1.cpp na Primes.cpp). Funkce `is_prime` určuje, zda je jeho vstup prvočíslo. Zbývající metody implementovat `Primes` třídu. Každé volání `create_async` používá podpis, který je kompatibilní s metodou, ze které je volána. Například protože `Primes::ComputePrimesAsync` `IAsyncAction`vrátí , pracovní funkce, která `create_async` je k dispozici nevrátí hodnotu `progress_reporter` a nebere objekt jako jeho parametr.

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

Každá metoda nejprve provede ověření, aby bylo zajištěno, že vstupní parametry jsou nezáporné. Pokud je vstupní hodnota záporná, metoda vyvolá [Platform::InvalidArgumentException](../../cppcx/platform-invalidargumentexception-class.md). Zpracování chyb je vysvětleno dále v této části.

Chcete-li tyto metody využívat z aplikace UPW, přidejte do řešení Sady Visual Studio druhou aplikaci Visual C# **Blank App (XAML).** Tento příklad pojmenuje projekt `Primes`. Potom z `Primes` projektu přidejte odkaz `PrimesLibrary` na projekt.

Přidejte následující kód do souboru MainPage.xaml. Tento kód definuje ui, takže můžete volat komponentu C++ a zobrazit výsledky.

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

Přidejte následující kód `MainPage` do třídy v souboru MainPage.xaml. Tento kód definuje `Primes` objekt a obslužné rutiny události tlačítka.

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

Tyto metody `async` používají `await` klíčová slova a aktualizovat uI po dokončení asynchronních operací. Informace o asynchronním kódování v aplikacích UPW naleznete v [tématu Threading and async programming](/windows/uwp/threading-async).

Metody `getPrimesCancellation` `cancelGetPrimes` a spolupracují, aby uživatel mohl operaci zrušit. Když uživatel zvolí tlačítko **Storno,** `cancelGetPrimes` metoda volá [IAsyncOperationWithProgress\<TResult, TProgress>:Cancel](/uwp/api/windows.foundation.iasyncinfo.cancel) zrušit operaci. Modul Souběžnost Runtime, který spravuje základní asynchronní operace, vyvolá typ vnitřní výjimky, který je zachycen prostředím Windows Runtime sdělit, že zrušení bylo dokončeno. Další informace o modelu zrušení naleznete v tématu [Zrušení](../../parallel/concrt/cancellation-in-the-ppl.md).

> [!IMPORTANT]
> Chcete-li povolit PPL správně hlásit prostředí Windows Runtime, že zrušil operaci, nezachyťte tento typ vnitřní výjimky. To znamená, že byste také neměli zachytit všechny výjimky (`catch (...)`). Pokud je nutné zachytit všechny výjimky, znovu vyvolat výjimku zajistit, že prostředí Windows Runtime můžete dokončit operaci zrušení.

Následující obrázek `Primes` znázorňuje aplikaci po výběru každé možnosti.

![Aplikace Windows Runtime Primes](../../parallel/concrt/media/concrt_windows_primes.png "Aplikace Windows Runtime Primes")

Příklady, které `create_async` se používají k vytvoření asynchronních úloh, které mohou být spotřebovány jinými jazyky, naleznete [v tématu Použití jazyka C++ v ukázce Optimalizace cesty map Bing](/previous-versions/windows/apps/hh699891(v=vs.140)) a [asynchronní operace systému Windows 8 v jazyce C++ s ppl](https://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d).

## <a name="controlling-the-execution-thread"></a><a name="exethread"></a>Řízení podprocesu spuštění

Prostředí Windows Runtime používá model zřetězení modelu MODELU COM. V tomto modelu jsou objekty hostovány v různých bytech, v závislosti na tom, jak zpracují jejich synchronizace. Objekty bezpečné pro přístup z více vláken jsou hostovány v apartment s více vlákny (MTA). Objekty, které musí být přístupné jedním vláknem jsou hostovány v apartment s jedním podprocesem (STA).

V aplikaci, která má uživatelské rozhraní, podproces ASTA (aplikace STA) je zodpovědný za čerpání zpráv okna a je jediným podprocesem v procesu, který můžete aktualizovat ovládací prvky uživatelského rozhraní hostované STA. To má dva důsledky. Za prvé, aby aplikace zůstala responzivní, všechny operace náročné na procesor a vstupně-va by neměly být spuštěny ve vlákně ASTA. Za druhé, výsledky, které pocházejí z podprocesů na pozadí musí být zařazeny zpět do ASTA aktualizovat uživatelské rozhraní. V aplikaci C++ `MainPage` Upw a další stránky XAML jsou spuštěny na ATSA. Proto pokračování úlohy, které jsou deklarovány na ASTA jsou spuštěny ve výchozím nastavení, takže můžete aktualizovat ovládací prvky přímo v těle pokračování. Pokud však vložíte úlohu do jiné úlohy, všechna pokračování v této vnořené úloze budou spuštěna v mta. Proto je třeba zvážit, zda explicitně určit, v jakém kontextu tato pokračování spustit.

Úloha vytvořená z asynchronní operace, například `IAsyncOperation<TResult>`, používá speciální sémantiku, která vám pomůže ignorovat podrobnosti podprocesu. Přestože operace může běžet na vlákno na pozadí (nebo nemusí být zálohována podprocesem vůbec), jeho pokračování jsou ve výchozím nastavení zaručeno `task::then`spuštění v apartment, který spustil operace pokračování (jinými slovy, z apartment, který volal ). Můžete použít [souběžnost::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) třídy k řízení kontextu provádění pokračování. Pomocí těchto statických pomocné metody k vytvoření `task_continuation_context` objektů:

- Pomocí [souběžnosti::task_continuation_context::use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) určete, že pokračování běží ve vlákně na pozadí.

- Pomocí [souběžnosti::task_continuation_context::use_current](reference/task-continuation-context-class.md#use_current) určete, že pokračování běží `task::then`na vlákno, které volalo .

Můžete předat `task_continuation_context` objekt [task::then](reference/task-class.md#then) metoda explicitně řídit kontext provádění pokračování nebo můžete předat úkol do `task::then` jiného bytu a potom volat metodu implicitně řídit kontext spuštění.

> [!IMPORTANT]
> Vzhledem k tomu, že hlavní vlákno uživatelského rozhraní aplikací UPW spustit pod STA, pokračování, které vytvoříte na tomto STA ve výchozím nastavení spustit na STA. V souladu s tím pokračování, které vytvoříte na MTA spustit na MTA.

V následující části je zobrazena aplikace, která čte soubor z disku, vyhledá nejběžnější slova v tomto souboru a pak zobrazí výsledky v ui. Konečná operace, aktualizace uživatelského rozhraní, dochází ve vlákně uživatelského rozhraní.

> [!IMPORTANT]
> Toto chování je specifické pro aplikace UPW. U aplikací klasické pracovní plochy neřídíte, kde se budou pokračovat. Místo toho plánovač zvolí pracovní podproces, na kterém chcete spustit každé pokračování.

> [!IMPORTANT]
> Nevolat [souběžnost::task::wait](reference/task-class.md#wait) v těle pokračování, které běží na STA. V opačném případě runtime vyvolá [souběžnost::invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) protože tato metoda blokuje aktuální vlákno a může způsobit, že aplikace přestane odpovídat. Můžete však volat [souběžnost::task::get](reference/task-class.md#get) metoda pro příjem výsledku předchozí úlohy v pokračování založeném na úkolu.

## <a name="example-controlling-execution-in-a-windows-runtime-app-with-c-and-xaml"></a><a name="example-app"></a>Příklad: Řízení provádění v aplikaci prostředí Windows Runtime s C++ a XAML

Zvažte aplikaci C++ XAML, která čte soubor z disku, vyhledá nejběžnější slova v tomto souboru a pak zobrazí výsledky v uživatelském jazyce. Chcete-li vytvořit tuto aplikaci, začněte v sadě Visual Studio vytvořením projektu **Blank App (Universal Windows)** a jeho pojmenováním `CommonWords`. V manifestu aplikace zadejte možnost **Knihovna dokumentů,** která aplikaci umožní přístup ke složce Dokumenty. Také přidejte typ souboru Text (.txt) do části deklarace manifestu aplikace. Další informace o možnostech a deklaracích aplikací najdete [v tématu Balení, nasazení a dotaz aplikací pro Windows](/windows/win32/appxpkg/appx-portal).

Aktualizujte `Grid` prvek v souboru MainPage.xaml tak, aby obsahoval `ProgressRing` prvek a `TextBlock` prvek. Označuje, `ProgressRing` že operace probíhá `TextBlock` a zobrazí výsledky výpočtu.

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

Do `#include` *pch.h*přidejte následující příkazy .

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

Do `MainPage` třídy přidejte následující deklarace metody (MainPage.h).

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

Přidejte `using` následující příkazy do souboru MainPage.cpp.

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

V souboru MainPage.cpp implementujte metodu `MainPage::MakeWordList`, `MainPage::FindCommonWords`a `MainPage::ShowResults` metody. A `MainPage::MakeWordList` `MainPage::FindCommonWords` provádět výpočtově náročné operace. Metoda `MainPage::ShowResults` zobrazí výsledek výpočtu v ui.

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

Upravte `MainPage` konstruktor a vytvořte řetězec úloh pokračování, který v uzdvi v ui běžná slova v knize *Iliad* od Homer. První dva úkoly pokračování, které rozdělují text na jednotlivá slova a nacházejí běžná slova, mohou být časově náročné a jsou proto explicitně nastaveny tak, aby se spouštěli na pozadí. Konečný úkol pokračování, který aktualizuje uživatelské rozhraní, určuje žádný kontext pokračování a proto se řídí pravidly apartment threading.

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
> Tento příklad ukazuje, jak určit kontexty spuštění a jak vytvořit řetězec pokračování. Připomeňme si, že ve výchozím nastavení úloha, která je vytvořena `task::then`z asynchronní operace spustí jeho pokračování v apartment, který volal . Proto tento příklad `task_continuation_context::use_arbitrary` používá k určení, že operace, které nezahrnují uživatelské rozhraní být provedeny na podprocesu na pozadí.

Na následujícím obrázku jsou `CommonWords` zobrazeny výsledky aplikace.

![Aplikace Windows Runtime CommonWords](../../parallel/concrt/media/concrt_windows_common_words.png "Aplikace Windows Runtime CommonWords")

V tomto příkladu je možné podporovat `task` zrušení, `create_async` protože objekty, které podporují použití implicitní zrušení tokenu. Definujte pracovní funkci `cancellation_token` tak, aby objekt, pokud vaše úkoly musí reagovat na zrušení v kooperativním způsobem. Další informace o zrušení v PPL najdete [v tématu Zrušení v ppl](cancellation-in-the-ppl.md)

## <a name="see-also"></a>Viz také

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)
