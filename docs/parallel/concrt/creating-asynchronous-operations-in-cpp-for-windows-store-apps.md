---
title: Vytváření asynchronních operací v jazyce C++ pro aplikace pro UPW
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: 59630c7702dffc4b606943e174e44fdba6aecfe8
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176949"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>Vytváření asynchronních operací v jazyce C++ pro aplikace pro UPW

Tento dokument popisuje některé z klíčových bodů do vzít v úvahu při použití třídy úkolu k vytvoření asynchronní operace založené na Windows fondu vláken v aplikaci univerzální modul Runtime Windows (UPW).

Použití asynchronního programování je klíčovou komponentou v aplikaci modelu Windows Runtime, protože umožňuje aplikace nadále reagovat na vstup uživatele. Dlouho probíhající úlohu můžete spustit bez blokování vlákna uživatelského rozhraní, a zobrazí výsledky úloh později. Můžete také zrušit úlohy a jako úkoly, které běží na pozadí, zobrazí se oznámení o průběhu. Dokument [asynchronní programování v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) poskytuje přehled asynchronního vzoru, který je k dispozici v jazyce Visual C++ k vytvoření aplikací pro UWP. Tento dokument se naučíte využívat i vytvoření řetězce asynchronní operací modulu Windows Runtime. Tato část popisuje, jak použít typy v ppltasks.h k vytvoření asynchronní operace, které mohou být spotřebovány jiné součásti prostředí Windows Runtime a tom, jak řídit způsob asynchronní práce provádí. Zkuste si také přečíst [vzory asynchronního programování a v Hilo (aplikace Windows Store pomocí jazyka C++ a XAML)](https://msdn.microsoft.com/library/windows/apps/jj160321.aspx) se dozvíte, jak můžete využít třída úlohy pro implementaci asynchronních operací v Hilo, aplikace v jazyce prostředí Windows Runtime pomocí jazyka C++ a XAML.

> [!NOTE]
>  Můžete použít [knihovny Ppl](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) a [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) v aplikaci UWP. Nelze však použít Plánovač úloh nebo Resource Manageru. Tento dokument popisuje další funkce, které poskytuje PPL, které jsou k dispozici pouze pro aplikace pro UPW a není pro aplikace klasické pracovní plochy.

## <a name="key-points"></a>Klíčové body

- Použití [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) k vytvoření asynchronní operace, které můžete používat další součásti (která může být napsán v jiných jazycích než C++).

- Použití [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) na oznámení o průběhu sestavy pro součásti, které volají asynchronní operace.

- Povolit vnitřní asynchronních operací se zrušit pomocí tokeny zrušení.

- Chování `create_async` funkce závisí na návratový typ pracovní funkce, který je předán. Pracovní funkce, který vrátí úlohu (buď `task<T>` nebo `task<void>`) pracuje synchronně, v kontextu, který se nazývá `create_async`. Pracovní funkce, která vrací `T` nebo `void` spouští v libovolné kontextu.

- Můžete použít [Concurrency::Task:: Then](reference/task-class.md#then) metodu pro vytvoření posloupnosti úkolů, které běží jeden po druhém. Aplikace pro UPW výchozí kontext pokračování úlohy závisí na tom, jak tento úkol byl vytvořen. Pokud byl úkol vytvořen předáním asynchronní akce úlohy konstruktoru, nebo tím, že předáte výraz lambda, která vrací asynchronní akce, výchozí kontext pro všechny pokračování úlohy je aktuální kontext. Pokud úloha není vytvořen z asynchronní akce, pak libovolného kontextu se používá ve výchozím nastavení pro pokračování úkolu. Můžete přepsat výchozí kontext s [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) třídy.

## <a name="in-this-document"></a>V tomto dokumentu

- [Vytváření asynchronních operací](#create-async)

- [Příklad: Vytvoření součásti modulu Runtime Windows C++](#example-component)

- [Řízení prováděcího vlákna](#exethread)

- [Příklad: Řízení provádění v aplikaci Windows Runtime s C++ a XAML](#example-app)

##  <a name="create-async"></a> Vytváření asynchronních operací

Úlohy a pokračování model můžete použít k definování úlohy na pozadí, jakož i další úlohy, které spustí po dokončení předchozího úkolu v paralelních vzorů knihovny (PPL). Tato funkce je poskytována [concurrency::task](../../parallel/concrt/reference/task-class.md) třídy. Další informace o tomto modelu a `task` najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Modul Windows Runtime je programovací rozhraní, můžete použít k vytvoření aplikací pro UPW, na kterých běží jenom v prostředí speciální operačního systému. Tyto aplikace použít oprávnění funkce, typy dat a zařízení a jsou distribuované ze služby Microsoft Store. Modul Windows Runtime je reprezentována *rozhraní binární* (ABI). ABI je základní binárního kontraktu, která zpřístupňuje rozhraní API Windows Runtime programovacích jazyků, jako je například Visual C++.

Pomocí prostředí Windows Runtime můžete využívat nejlepší funkce různých programovacích jazycích a je zkombinovat do jedné aplikace. Můžete například vytvářet uživatelské rozhraní v jazyce JavaScript a provádění výpočetně náročné aplikace logiky v komponentě C++. Možnost provádět tyto výpočetně náročné operace na pozadí je ale klíčovým faktorem ochraně responzivní uživatelské rozhraní. Vzhledem k tomu, `task` třída je specifická pro C++, je nutné použít rozhraní Windows Runtime pro komunikaci asynchronních operací na jiné součásti (která může být napsán v jiných jazycích než C++). Modul Windows Runtime poskytuje čtyři rozhraní, které můžete použít k reprezentaci asynchronních operací:

[Windows::Foundation:: iasyncaction](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncaction.aspx)<br/>
Představuje asynchronní akci.

[Windows::Foundation::IAsyncActionWithProgress\<TProgress>](https://msdn.microsoft.com/library/windows/apps/br206581.aspx)<br/>
Představuje asynchronní akci, která hlásí průběh.

[:: Iasyncoperation\<TResult >](https://msdn.microsoft.com/library/windows/apps/br206598.aspx)<br/>
Představuje asynchronní operaci, která vrací výsledek.

[Windows::Foundation:: iasyncoperationwithprogress\<TResult, TProgress >](https://msdn.microsoft.com/library/windows/apps/br206594.aspx)<br/>
Představuje asynchronní operaci, která vrací výsledek a sestavy pokroku.

Pojem *akce* znamená, že asynchronní úloha nevytvoří hodnotu (Představte si, že funkce, která vrátí `void`). Pojem *operace* znamená, že asynchronní úloha výsledkem hodnota. Pojem *průběh* znamená, že úloha může hlásit zprávy o průběhu volajícímu. JavaScript, rozhraní .NET Framework a jazyka Visual C++ nabízí svou vlastní způsob, jak vytvořit instance pro použití těchto rozhraní hranice ABI. Pro jazyk Visual C++ poskytuje PPL [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) funkce. Tato funkce vytvoří prostředí Windows Runtime asynchronní akce nebo operace, která představuje dokončení úlohy. `create_async` Funkce přebírá pracovní funkci (obvykle výraz lambda), vytvoří interně `task` objektu a zabalí, které úlohy v jednom ze čtyř asynchronní rozhraní Windows Runtime.

> [!NOTE]
>  Použití `create_async` pouze pokud je nutné vytvořit funkci, která je přístupná z jiného jazyka nebo jiné součásti prostředí Windows Runtime. Použití `task` třídy přímo, ve kterých víte, že operaci je vytvořen i zaplněny kódem C++ pod stejnou komponentou.

Návratový typ `create_async` se určuje podle typu argumentů. Pokud vaše pracovní funkce nevrací hodnotu a neoznamuje průběh, například `create_async` vrátí `IAsyncAction`. Pokud vaše pracovní funkce nevrací hodnotu a také zobrazuje průběh, `create_async` vrátí `IAsyncActionWithProgress`. Chcete-li vykazování průběh, zadejte [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) objektu jako parametr na svoji pracovní funkci. Schopnost vykazovat postup umožňuje nahlásit, jaké množství práce byla provedena a jaké množství stále zůstává (například jako procento). Umožňuje také můžete ohlásit výsledky, jakmile budou k dispozici.

`IAsyncAction`, `IAsyncActionWithProgress<TProgress>`, `IAsyncOperation<TResult>`, A `IAsyncActionOperationWithProgress<TProgress, TProgress>` rozhraními každý `Cancel` metodu, která umožňuje zrušit asynchronní operaci. `task` Třída pracuje s tokeny zrušení. Při použití token zrušení pro zrušení pracovní modul runtime nelze spustit novou práci, která si předplatí tento token. Práce, která je již aktivní můžete monitorovat jeho token zrušení a zastaví, jakmile ho může. Tento mechanismus je podrobněji popsána v dokumentu [zrušení v knihovně PPL](cancellation-in-the-ppl.md). Zrušení úlohy můžete připojit s modulem Windows Runtime`Cancel` metody dvěma způsoby. Nejprve můžete definovat pracovní funkce, který předáte `create_async` provést [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) objektu. Když `Cancel` metoda je volána, tento token zrušení se zrušila a normální zrušení pravidla se vztahují na základní `task` objekt, který podporuje `create_async` volání. Pokud nezadáte `cancellation_token` objektu základní `task` objektu definuje jeden implicitně. Definování `cancellation_token` objektu, když budete chtít kooperativně reagovat na zrušení v pracovní funkci. V části [příklad: řízení provádění v aplikaci Windows Runtime s C++ a XAML](#example-app) ukazuje příklad toho, jak provádět zrušení v aplikaci pro univerzální platformu Windows (UPW) pomocí C# a XAML, který používá vlastní modul Runtime C++ Windows komponenta.

> [!WARNING]
>  V řetězci pokračování úlohy, vždy vyčistit stavu a poté zavolejte [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) když je zrušen token zrušení. Pokud jste již v rané fázi vrátíte namísto volání metody `cancel_current_task`, operace přechody do dokončeného stavu místo zrušeném stavu.

Následující tabulka shrnuje kombinace, které můžete použít k definování asynchronních operací ve vaší aplikaci.

|Chcete-li vytvořit toto rozhraní Windows Runtime|Vrátí tento typ z `create_async`|Tyto typy parametrů předat vaše pracovní funkce použít implicitní rušícího tokenu|Tyto typy parametrů předat vaše pracovní funkce použít explicitní rušícího tokenu|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|`void` Nebo `task<void>`|(žádné)|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|`void` Nebo `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` Nebo `task<T>`|(žádné)|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` Nebo `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

Může vrátit hodnotu nebo `task` objekt z pracovní funkce, které můžete předat `create_async` funkce. Tyto odchylky vytvářet různé chování. Po návratu hodnotu pracovní funkce není zabalené ve `task` tak, aby ji lze spustit ve vlákně na pozadí. Kromě toho základní `task` používá token implicitní zrušení. Naopak pokud se vrátíte `task` objektu, pracovní funkce pracuje synchronně. Proto pokud se vrátíte `task` objektu, ujistěte se, že všechny dlouhé operace v pracovní funkce také spustit jako úlohy aplikace nadále reagovat. Kromě toho základní `task` nepoužívá token implicitní zrušení. Proto je třeba definovat vaše pracovní funkce k převzetí `cancellation_token` objektu, pokud budete potřebovat podporu pro zrušení při návratu `task` objektu z `create_async`.

Následující příklad ukazuje různé způsoby, jak vytvořit `IAsyncAction` objekt, který mohou využívat jiné součásti prostředí Windows Runtime.

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

##  <a name="example-component"></a> Příklad: Vytvoření komponenty prostředí Windows Runtime C++ a její použití v jazyce C#

Vezměte v úvahu aplikaci, která se používá k definování uživatelského rozhraní a komponenty modulu Windows Runtime C++ provádět operace náročné na výpočetní prostředky XAML a C#. V tomto příkladu vypočítá komponent C++, která čísla v dané oblasti jsou primární. Pro ilustraci rozdíly mezi čtyři asynchronní úloha rozhraní Windows Runtime, spuštění, v sadě Visual Studio, tak, že vytvoříte **prázdné řešení** a jeho pojmenování `Primes`. Pak přidejte do řešení **součást prostředí Windows Runtime** projektu a jeho pojmenování `PrimesLibrary`. Přidejte následující kód vygenerovaný soubor hlaviček jazyka C++ (Tento příklad přejmenuje Class1.h Primes.h). Každý `public` metoda definuje jednu ze čtyř asynchronní rozhraní. Vrátí metody, které vrací hodnotu [Windows::Foundation::Collections::IVector\<int >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx) objektu. Vytvoření metody, které vykazování průběh `double` hodnoty, které definují procento celkové práce, která byla dokončena.

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
>  Podle úmluvy názvy asynchronních metod v modulu Windows Runtime obvykle končit "Async".

Přidejte následující kód do generovaného zdrojového souboru jazyka C++ (Tento příklad přejmenuje Class1.cpp Primes.cpp). `is_prime` Funkce určuje, zda vstup je primární. Zbývající metody implementovat `Primes` třídy. Každé volání `create_async` používá stejný podpis kompatibilní s metodou, ze kterého je volána. Například protože `Primes::ComputePrimesAsync` vrátí `IAsyncAction`, pracovní funkce, který byl poskytnut `create_async` nevrací hodnotu a nepřijímá `progress_reporter` objektu jako svůj parametr.

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

Každá metoda nejprve provádí ověřování vstupních parametrů musí být nezáporná. Pokud je vstupní hodnota záporná, vyvolá metoda [Platform::InvalidArgumentException](https://msdn.microsoft.com/library/windows/apps/hh755794.aspx). Zpracování chyb je vysvětleno dále v této části.

Chcete-li používat tyto metody z aplikace pro UPW, použijte Visual C# **prázdná aplikace (XAML)** šablony přidáte druhý projekt do řešení sady Visual Studio. V tomto příkladu názvy projektu `Primes`. Pak v `Primes` projektu, přidejte odkaz na `PrimesLibrary` projektu.

Přidejte následující kód do souboru MainPage.xaml. Tento kód definuje uživatelské rozhraní, aby mohl volat komponent C++ a zobrazení výsledků.

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

Přidejte následující kód, který `MainPage` třída v souboru MainPage.xaml. Tento kód definuje `Primes` objektu a obslužné rutiny události tlačítek.

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

Tyto metody používají `async` a `await` klíčových slov pro aktualizaci uživatelského rozhraní, po dokončení asynchronní operace. Informace o asynchronním programování v aplikacích pro UPW, naleznete v tématu [asynchronní programování a zřetězení](/windows/uwp/threading-async).

`getPrimesCancellation` a `cancelGetPrimes` metody spolupracují a umožňují uživateli zrušit operaci. Když uživatel klikne **zrušit** tlačítko, `cancelGetPrimes` volání metody [IAsyncOperationWithProgress\<TResult, TProgress >:: zrušit](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncinfo.cancel.aspx) na zrušení operace. Modulu Runtime souběžnosti, který spravuje podkladová asynchronní operace, vyvolá výjimku, která je zachycena ve Windows Runtime pro komunikaci, že dokončení zrušení typ vnitřní výjimky. Další informace o tomto modelu zrušení naleznete v tématu [zrušení](../../parallel/concrt/cancellation-in-the-ppl.md).

> [!IMPORTANT]
>  Pokud chcete povolit PPL správně hlášení do prostředí Windows Runtime zrušil operaci, nebude zachytávat tento typ vnitřní výjimky. To znamená, že neměli byste také zachytit všechny výjimky (`catch (...)`). Pokud musíte zachytit všechny výjimky, znovu vyvolá výjimku, k zajištění, že prostředí Windows Runtime můžete dokončit operaci zrušení.

Je vidět na následujícím obrázku `Primes` aplikace po jednotlivých možností byla vybrána.

![Prostředí Windows Runtime základen aplikace](../../parallel/concrt/media/concrt_windows_primes.png "základen modulu Windows Runtime aplikace")

Příklady, které používají `create_async` pro vytváření asynchronních úloh určených pro jiné jazyky, naleznete v tématu [pomocí C++ v příklad optimalizace cesty mapy Bing](https://msdn.microsoft.com/library/windows/apps/hh699891.aspx) a [asynchronní operace systému Windows 8 v jazyce C++ pomocí úlohy PPL](http://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d).

##  <a name="exethread"></a> Řízení prováděcího vlákna

Modul Runtime Windows používá COM model vláken. V tomto modelu objekty jsou hostované v jiné objekty apartment, v závislosti na tom, jak se zpracovávají jejich synchronizaci. Bezpečná pro vlákno objekty jsou hostované v vícevláknového objektu apartment (MTA). Objekty, které musí být přistupováno jedním vláknem a jsou hostované v jednovláknový apartment (STA).

V aplikaci, která má uživatelské rozhraní vlákna ASTA (Application STA) zodpovídá za čerpání – zprávy okna a je pouze vlákno v procesu, který může aktualizovat ovládací prvky hostované v STA uživatelského rozhraní. To má dva důsledky. Nejdřív k tomu, aby aplikace nadále reagovat, všechny náročnou na procesor a vstupně-výstupních operací by neměla běžet ve vlákně ASTA. Za druhé výsledky, které pocházejí z vlákna na pozadí musí zařadit zpět na ASTA k aktualizaci uživatelského rozhraní. V aplikaci C++ UWP `MainPage` a všech ostatních XAML spouštět ATSA. Proto pokračování úlohy, které jsou deklarovány na ASTA jsou existuje ve výchozím nastavení spouští mohli aktualizovat ovládací prvky přímo v těle pokračování. Ale pokud byste vnořit úkolu v jiné úlohy, libovolný pokračování pro tento úkol vnořené spusťte v MTA. Proto je potřeba zvážit, jestli se s ohledem na kontext spuštění tyto pokračování.

Úloha, která je vytvořena z asynchronní operace, jako například `IAsyncOperation<TResult>`, používá speciální sémantiku, která vám může pomoct ignorovat vláken podrobnosti. I když operace narazit na vlákně na pozadí (nebo ji nesmí být se opírá o vlákno vůbec), jeho pokračování jsou standardně se zaručeně spustí na objektu apartment, který spustil pokračování operace (jinými slovy, z objektu apartment, který volá `task::then`). Můžete použít [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) třídy k řízení kontextu spuštění pokračování. Použít tyto statické pomocné metody k vytvoření `task_continuation_context` objekty:

- Použití [concurrency::task_continuation_context::use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) k určení, že pokračování běžet ve vlákně na pozadí.

- Použití [concurrency::task_continuation_context::use_current](reference/task-continuation-context-class.md#use_current) k určení, že pokračování běžet ve vlákně, který volal `task::then`.

Můžete předat `task_continuation_context` objektu [Task::Then –](reference/task-class.md#then) můžete předat úlohy do jiného objektu apartment a poté zavolejte metodu chcete explicitně kontrolovat kontextu spuštění pokračování nebo můžete `task::then` implicitně řídit kontext spuštění.

> [!IMPORTANT]
>  Vzhledem k tomu, že hlavní vlákno uživatelského rozhraní v aplikacích pro UWP běžet pod STA, pokračování, které vytvoříte v tomto STA ve výchozím nastavení spustit v STA. Pokračování, které vytvoříte na MTA odpovídajícím způsobem, spusťte na MTA.

Následující části zobrazuje aplikaci, která načte soubor z disku, najde nejčastější slova v tomto souboru a potom zobrazí výsledky v uživatelském rozhraní. Poslední operaci aktualizace uživatelského rozhraní, dochází na vlákně UI.

> [!IMPORTANT]
> Toto chování je specifické pro aplikace UWP. Pro aplikace klasické pracovní plochy ne řídit, ve kterém se spouští pokračování. Místo toho Plánovač zvolí pracovní vlákno, ve kterém se spustí každý pokračování.

> [!IMPORTANT]
> Nevolejte [Concurrency::Task:: wait](reference/task-class.md#wait) v těle pokračování, které běží v STA. V opačném případě modul runtime vyvolá [concurrency::invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) vzhledem k tomu, že tato metoda blokuje aktuální vlákno a může způsobit, že aplikace přestane reagovat. Můžete však volat [Concurrency::Task:: Get](reference/task-class.md#get) metody pro získání výsledku předchozího úkolu v pokračování založeném na úkolech.

##  <a name="example-app"></a> Příklad: Řízení provádění v aplikaci Windows Runtime s C++ a XAML

Vezměte v úvahu aplikace s C++ XAML, která načte soubor z disku, zjistí nejčastější slova v tomto souboru a potom zobrazí výsledky v uživatelském rozhraní. Pokud chcete vytvořit tuto aplikaci, spustit, v sadě Visual Studio, tak, že vytvoříte **prázdná aplikace (Universal Windows)** projektu a jeho pojmenování `CommonWords`. Do manifestu aplikace, zadejte **knihovna dokumentů** možnost k povolení aplikace pro přístup do složky Dokumenty. Typ souboru Text (TXT) můžete také přidáte do části deklarace manifestu aplikace. Další informace o možnostech a deklaracích aplikace naleznete v tématu [balíčky a nasazení aplikací](https://msdn.microsoft.com/library/windows/apps/hh464929.aspx).

Aktualizace `Grid` prvku v souboru MainPage.xaml zahrnout `ProgressRing` elementu a `TextBlock` elementu. `ProgressRing` Označuje, že operace je v průběhu a `TextBlock` zobrazuje výsledky výpočtu.

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

Přidejte následující `#include` příkazy pro soubor pch.h.

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

Přidejte následující deklarace metody k `MainPage` třídy (MainPage.h).

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

Přidejte následující `using` příkazy MainPage.cpp.

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

V MainPage.cpp, implementovat `MainPage::MakeWordList`, `MainPage::FindCommonWords`, a `MainPage::ShowResults` metody. `MainPage::MakeWordList` a `MainPage::FindCommonWords` provádění výpočetně náročných operací. `MainPage::ShowResults` Metoda zobrazí výsledek výpočtu v uživatelském rozhraní.

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

Upravit `MainPage` konstruktor pro vytvoření řetězec pokračujících úloh, která se zobrazí v uživatelském rozhraní běžná slova v knize *The Iliad* podle Homer. První dva pokračujících úloh, která rozdělí text na jednotlivá slova a najít běžná slova, může být časově náročné a jsou proto explicitně nastavená na spuštěný na pozadí. Konečnou pokračující úlohou, která aktualizuje uživatelské rozhraní, určuje žádný kontext pokračování a proto řídí apartment práce s vlákny pravidla.

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
>  Tento příklad ukazuje, jak zadat kontexty provádění a jak sestavit řetěz pokračování. Připomínáme, že ve výchozím nastavení úkolu, který je vytvořen z asynchronní operace spustí jeho pokračování na objektu apartment, který volá `task::then`. Proto se v tomto příkladu `task_continuation_context::use_arbitrary` udává, že operace, které nezahrnují rozhraní provést ve vlákně na pozadí.

Následující obrázek ukazuje výsledky `CommonWords` aplikace.

![Aplikace Windows Runtime CommonWords](../../parallel/concrt/media/concrt_windows_common_words.png "Windows Runtime CommonWords aplikace")

V tomto příkladu je možné pro podporu zrušení, protože `task` objektů, které podporují `create_async` použít token implicitní zrušení. Definujte svoji pracovní funkci provést `cancellation_token` objektu, pokud vaše úkoly potřebují reagovat na způsob spolupráce za zrušení. Další informace o zrušení v knihovně PPL naleznete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md)

## <a name="see-also"></a>Viz také

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)
