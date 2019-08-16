---
title: Vytváření asynchronních operací C++ v aplikacích pro UWP
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: d6a36da79f24d98d162c4ffffff17b4471b2b063
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512247"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>Vytváření asynchronních operací C++ v aplikacích pro UWP

Tento dokument popisuje některé z klíčových bodů, které je potřeba vzít v úvahu při vytváření asynchronních operací založených na systému Windows v aplikaci v rámci univerzální prostředí Windows Runtime (UWP) pomocí třídy Task.

Použití asynchronního programování je klíčovou komponentou v modelu prostředí Windows Runtime aplikace, protože umožňuje aplikacím zůstat reagovat na vstup uživatele. Můžete spustit dlouhodobě běžící úlohu bez blokování vlákna uživatelského rozhraní a výsledky úlohy můžete získat později. Můžete také zrušit úlohy a přijímat oznámení o průběhu jako úlohy spouštěné na pozadí. Dokument [asynchronní programování v C++ ](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) nástroji poskytuje přehled asynchronního vzoru, který je k dispozici ve vizuálu C++ k vytváření aplikací UWP. Tento dokument se učí, jak spotřebovávat, tak i vytvořit řetězy asynchronních operací prostředí Windows Runtime. Tato část popisuje, jak použít typy v ppltasks. h k vytvoření asynchronních operací, které mohou být spotřebovány jinou komponentou prostředí Windows Runtime a jak řídit, jak je prováděna asynchronní práce. Zvažte také čtení [asynchronních programovacích vzorů a tipů v Hilo (aplikace C++ pro Windows Store pomocí a XAML)](/previous-versions/windows/apps/jj160321(v=win.10)) , abyste se dozvěděli, jak jsme použili třídu Task k implementaci asynchronních C++ operací v Hilo, prostředí Windows Runtime aplikace pomocí a XAML.

> [!NOTE]
>  V aplikaci UWP můžete použít knihovnu PPL ( [Parallel Patterns Library](../../parallel/concrt/parallel-patterns-library-ppl.md) ) a [knihovny asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) . Nemůžete však použít Plánovač úloh ani Správce prostředků. Tento dokument popisuje další funkce, které poskytuje PPL k dispozici pouze pro aplikaci UWP, a ne pro desktopovou aplikaci.

## <a name="key-points"></a>Klíčové body

- Použijte [Concurrency:: create_async](reference/concurrency-namespace-functions.md#create_async) k vytvoření asynchronních operací, které mohou být použity jinými komponentami (které mohou být napsány v C++jiných jazycích než).

- Použijte [Concurrency::p rogress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) k oznamování průběhu k součástem, které volají vaše asynchronní operace.

- Použijte tokeny zrušení k umožnění zrušení interních asynchronních operací.

- Chování `create_async` funkce závisí na návratový typ pracovní funkce, která je předána. Pracovní funkce, která vrací úlohu (buď `task<T>` nebo `task<void>`), běží synchronně v kontextu, který se nazývá `create_async`. Pracovní funkce, která vrací `T` nebo `void` běží v libovolném kontextu.

- Můžete použít metodu [Concurrency:: task:: then](reference/task-class.md#then) k vytvoření řetězce úloh, které jsou spouštěny jednou po druhém. V aplikaci pro UWP závisí výchozí kontext pro pokračování úlohy na tom, jak byla tato úloha vytvořená. Pokud byla úloha vytvořena předáním asynchronní akce do konstruktoru úlohy nebo předáním výrazu lambda, který vrací asynchronní akci, je výchozím kontextu všech pokračování této úlohy aktuální kontext. Pokud úloha není vytvořena z asynchronní akce, pak je ve výchozím nastavení pro pokračování úlohy použit libovolný kontext. Můžete přepsat výchozí kontext pomocí třídy [Concurrency:: task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) .

## <a name="in-this-document"></a>V tomto dokumentu

- [Vytváření asynchronních operací](#create-async)

- [Příklad: Vytvoření součásti C++ prostředí Windows Runtime](#example-component)

- [Řízení vlákna spuštění](#exethread)

- [Příklad: Řízení spouštění v prostředí Windows Runtime aplikace pomocí C++ a XAML](#example-app)

##  <a name="create-async"></a>Vytváření asynchronních operací

Můžete použít model úlohy a pokračování v knihovně PPL (Parallel Patterns Library) k definování úloh na pozadí a dalších úloh, které se spustí po dokončení předchozí úlohy. Tato funkce je poskytována třídou [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) . Další informace o tomto modelu a `task` třídě naleznete v tématu [Task paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Prostředí Windows Runtime je programovací rozhraní, které můžete použít k vytváření aplikací pro UWP, které běží pouze ve speciálním prostředí operačního systému. Takové aplikace používají autorizované funkce, datové typy a zařízení a jsou distribuované z Microsoft Store. Prostředí Windows Runtime je reprezentované binárním *rozhraním aplikace* (ABI). ABI je základní binární kontrakt, který zpřístupňuje prostředí Windows Runtime rozhraní API pro programovací jazyky, jako je C++vizuál.

Pomocí prostředí Windows Runtime můžete použít nejlepší funkce různých programovacích jazyků a zkombinovat je do jedné aplikace. Můžete například vytvořit uživatelské rozhraní v jazyce JavaScript a provést výpočetně náročné aplikační logiku v C++ komponentě. Možnost provádět tyto výpočetně náročné operace na pozadí je klíčovým faktorem, ve kterém vaše uživatelské rozhraní reaguje. Vzhledem k tomu, že C++ C++ Třídajespecifickápro,jenutnépoužítrozhraníprostředíWindowsRuntimekekomunikaciasynchronníchoperacísostatnímikomponentami(kterémohoubýtnapsányvjinýchjazycíchnež`task` ). Prostředí Windows Runtime poskytuje čtyři rozhraní, která lze použít k reprezentaci asynchronních operací:

[Windows::Foundation::IAsyncAction](/uwp/api/windows.foundation.iasyncaction)<br/>
Představuje asynchronní akci.

[Windows::Foundation::IAsyncActionWithProgress\<TProgress>](/uwp/api/Windows.Foundation.IAsyncActionWithProgress_TProgress_)<br/>
Představuje asynchronní akci, která oznamuje průběh.

[Windows:: Foundation:: IAsyncOperation\<TResult >](/uwp/api/windows.foundation.iasyncoperation_tresult_)<br/>
Představuje asynchronní operaci, která vrací výsledek.

[Windows:: Foundation:: IAsyncOperationWithProgress\<TResult, TProgress >](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)<br/>
Představuje asynchronní operaci, která vrací výsledek a sestavuje průběh.

Pojem *Akce* znamená, že asynchronní úloha nevytvoří hodnotu (může se zdát, že funkce vrací `void`). Pojem *operace* znamená, že asynchronní úloha vytvoří hodnotu. Pojem " *postup* " znamená, že úkol může hlásit průběh zprávy pro volajícího. JavaScript, .NET Framework a vizuál C++ poskytují vlastní způsob, jak vytvořit instance těchto rozhraní pro použití v rámci hranice ABI. Pro vizuál C++PPL poskytuje funkci [Concurrency:: create_async](reference/concurrency-namespace-functions.md#create_async) . Tato funkce vytvoří prostředí Windows Runtime asynchronní akci nebo operaci, která představuje dokončení úkolu. Funkce používá pracovní funkci (obvykle lambda výraz), interně `task` vytvoří objekt a obaluje tento úkol v jednom ze čtyř asynchronních prostředí Windows Runtime rozhraní. `create_async`

> [!NOTE]
>  Tuto `create_async` možnost použijte pouze v případě, že je nutné vytvořit funkce, které jsou k dispozici v jiném jazyce nebo jiné součásti prostředí Windows Runtime. Třídu použijte přímo tehdy, když víte, že operace je vyráběná a spotřebovaná C++ kódem ve stejné komponentě. `task`

Návratový typ `create_async` je určen typem svých argumentů. Například pokud vaše pracovní funkce nevrátí hodnotu a neohlásí průběh, `create_async` vrátí. `IAsyncAction` Pokud vaše pracovní funkce nevrací hodnotu a také zaznamenává průběh, `create_async` vrátí. `IAsyncActionWithProgress` Chcete-li ohlásit průběh, poskytněte objekt [Concurrency::p rogress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) jako parametr vaší pracovní funkce. Možnost nahlásit průběh vám umožní nahlásit, jakou množství práce bylo provedeno a jakou částku stále zbývá (například jako procento). Umožňuje vám také nahlásit výsledky, jakmile budou k dispozici.

Rozhraní `IAsyncAction` ,`IAsyncActionWithProgress<TProgress>`, a`IAsyncActionOperationWithProgress<TProgress, TProgress>` každý z nich poskytují`Cancel` metodu, která umožňuje zrušit asynchronní operaci. `IAsyncOperation<TResult>` `task` Třída funguje s tokeny zrušení. Použijete-li k zrušení práce token zrušení, modul runtime nespustí novou práci, která se přihlásí k odběru tohoto tokenu. Práce, která je již aktivní, může monitorovat svůj token zrušení a zastavit, když ho může. Tento mechanismus je podrobněji popsán v dokumentu [zrušení v PPL](cancellation-in-the-ppl.md). Zrušení úlohy můžete spojit s metodami prostředí Windows Runtime`Cancel` dvěma způsoby. Nejprve můžete definovat pracovní funkci, kterou předáte `create_async` k provedení objektu [Concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) . Při volání `task` `create_async` metody je tento token zrušení zrušen a normální pravidla zrušení platí pro podkladový objekt, který podporuje volání. `Cancel` Pokud neposkytnete `cancellation_token` objekt, podkladové `task` objekty definují implicitně. `cancellation_token` Definujte objekt, když potřebujete spolupracovat na zrušení v pracovní funkci. Příklad oddílu [: Řízení spouštění C++ v aplikaci prostředí Windows Runtime s a XAML](#example-app) ukazuje příklad, jak provést zrušení v aplikaci Univerzální platforma Windows (UWP) pomocí C# a XAML, která používá vlastní prostředí Windows Runtime C++ komponentu.

> [!WARNING]
>  V řetězci pokračování úlohy, vždy vyčistit stav a pak volání metody [Concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) při zrušení tokenu zrušení. Pokud vrátíte úvodní místo volání `cancel_current_task`, operace přejde do stavu dokončeno, nikoli z zrušeného stavu.

Následující tabulka shrnuje kombinace, které můžete použít k definování asynchronních operací ve vaší aplikaci.

|Vytvoření tohoto prostředí Windows Runtime rozhraní|Vrátit tento typ z`create_async`|Předejte tyto typy parametrů do pracovní funkce pro použití implicitního tokenu zrušení.|Předejte tyto typy parametrů do pracovní funkce pro použití explicitního tokenu zrušení.|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|`void` Nebo `task<void>`|nTato|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|`void` Nebo `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` Nebo `task<T>`|nTato|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` Nebo `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

Můžete vrátit hodnotu nebo `task` objekt z pracovní funkce, kterou předáte `create_async` do funkce. Tyto variace vytváří různá chování. Při vrácení hodnoty je pracovní funkce zabalena do `task` , aby ji bylo možné spustit ve vlákně na pozadí. Kromě toho základní `task` používá implicitní token zrušení. Naopak, pokud vrátíte `task` objekt, pracovní funkce se spustí synchronně. Proto pokud vrátíte `task` objekt, zajistěte, aby všechny zdlouhavé operace ve vaší pracovní funkci běžely také jako úlohy, které umožní vaší aplikaci reagovat. Kromě toho základní `task` nepoužívá implicitní token zrušení. Proto je nutné definovat pracovní funkci pro převzetí `cancellation_token` objektu, pokud požadujete podporu pro zrušení při `task` vrácení objektu z `create_async`.

Následující příklad ukazuje různé způsoby vytvoření `IAsyncAction` objektu, které mohou být spotřebovány jinou prostředí Windows Runtime komponentou.

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

##  <a name="example-component"></a>Případě Vytvoření součásti C++ prostředí Windows Runtime a její využíváníC#

Vezměte v úvahu aplikaci, která používá C# XAML a k definování uživatelského rozhraní C++ a prostředí Windows Runtime komponenty pro provádění operací náročných na výpočetní výkon. V tomto příkladu C++ komponenta počítá, která čísla v daném rozsahu jsou typu základna. Pro ilustraci rozdílů mezi čtyřmi prostředí Windows Runtime rozhraní asynchronních úloh, začněte v aplikaci Visual Studio vytvořením **prázdného řešení** a pojmenováním `Primes`. Pak přidejte do řešení prostředí Windows Runtime projekt **komponenty** a pojmenujte ho `PrimesLibrary`. Do vygenerovaného C++ souboru hlaviček přidejte následující kód (Tento příklad přejmenuje Class1. h na základny. h). Každá `public` Metoda definuje jedno ze čtyř asynchronních rozhraní. Metody, které vracejí hodnotu vrací objekt [Windows:: Foundation:: Collections:: IVector\<int >](/uwp/api/Windows.Foundation.Collections.IVector_T_) objekt. Metody, které nastavují `double` průběh, vytváří hodnoty definující procentuální hodnotu celkové práce, která byla dokončena.

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
>  Podle konvence názvy asynchronních metod v prostředí Windows Runtime obvykle končí na "Async".

Do generovaného C++ zdrojového souboru přidejte následující kód (Tento příklad přejmenuje Class1. cpp na základny. cpp). `is_prime` Funkce určuje, zda je její vstup na primární. Zbývající metody implementují `Primes` třídu. Každé volání `create_async` používá podpis, který je kompatibilní s metodou, ze které je volána. Například vzhledem k tomu `Primes::ComputePrimesAsync` , `IAsyncAction`že funkce vrací funkci, která je poskytnuta `create_async` pro, nevrátí hodnotu a nepřijímá `progress_reporter` objekt jako svůj parametr.

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

Každá metoda nejprve provede ověření, aby se zajistilo, že vstupní parametry jsou nezáporné. Pokud je vstupní hodnota záporná, metoda vyvolá [Platform:: InvalidArgumentException](../../cppcx/platform-invalidargumentexception-class.md). Zpracování chyb je vysvětleno dále v této části.

Pro využívání těchto metod z aplikace pro UWP použijte šablonu Visual C# **prázdná aplikace (XAML)** k přidání druhého projektu do řešení sady Visual Studio. Tento příklad pojmenovává projekt `Primes`. Pak z `Primes` projektu přidejte odkaz `PrimesLibrary` na projekt.

Do souboru MainPage. XAML přidejte následující kód. Tento kód definuje uživatelské rozhraní, abyste mohli volat C++ komponentu a výsledky zobrazení.

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

Do `MainPage` třídy v souboru MainPage. XAML přidejte následující kód. Tento kód definuje `Primes` objekt a obslužné rutiny událostí tlačítek.

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

Tyto metody používají `async` klíčová `await` slova a k aktualizaci uživatelského rozhraní po dokončení asynchronních operací. Informace o asynchronním kódování v aplikacích UWP naleznete v tématu [dělení vlákna a asynchronní programování](/windows/uwp/threading-async).

Metody `getPrimesCancellation` a`cancelGetPrimes` pracují společně, aby mohl uživatel operaci zrušit. Když uživatel klikne na tlačítko **Storno** , `cancelGetPrimes` metoda volá [\<IAsyncOperationWithProgress TResult, TProgress >:: Cancel](/uwp/api/windows.foundation.iasyncinfo.cancel) pro zrušení operace. Concurrency Runtime, která spravuje základní asynchronní operaci, vyvolá typ interní výjimky, který je zachycen prostředí Windows Runtime ke sdělení, že zrušení bylo dokončeno. Další informace o modelu zrušení naleznete v tématu [zrušení](../../parallel/concrt/cancellation-in-the-ppl.md).

> [!IMPORTANT]
>  Chcete-li povolit PPL správné hlášení prostředí Windows Runtime, že operace zrušila, Nezachycujte tento typ interní výjimky. To znamená, že byste také neměli zachytit všechny výjimky (`catch (...)`). Pokud je nutné zachytit všechny výjimky, znovu vyvolejte výjimku, aby bylo zajištěno, že prostředí Windows Runtime může dokončit operaci zrušení.

Následující ilustrace znázorňuje `Primes` aplikaci po výběru každé z možností.

![Aplikace prostředí Windows runtimech základny](../../parallel/concrt/media/concrt_windows_primes.png "Aplikace prostředí Windows runtimech základny")

Příklady, které se `create_async` používají k vytvoření asynchronních úloh, které mohou být spotřebovány jinými jazyky, najdete v tématu [použití C++ v ukázce optimalizace cest Bing Maps](/previous-versions/windows/apps/hh699891(v=vs.140)) a [asynchronní operace C++ se systémem Windows 8 v systému PPL](https://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d).

##  <a name="exethread"></a>Řízení vlákna spuštění

Prostředí Windows Runtime používá model vláken modelu COM. V tomto modelu jsou objekty hostovány v různých objektech Apartment v závislosti na tom, jak zpracovávají svou synchronizaci. Objekty bezpečné pro přístup z více vláken jsou hostovány v modelu MTA (multi-threaded Apartment). Objekty, které musí být k dispozici v jednom vlákně, jsou hostovány v prostředí STA (Single-threaded Apartment).

V aplikaci, která má uživatelské rozhraní, je vlákno ASTA (Application STA) zodpovědné za čerpadlo zpráv oken a je jediným vláknem v procesu, které může aktualizovat ovládací prvky uživatelského rozhraní hostované v prostředí STA. To má dvě důsledky. Nejdřív Pokud chcete, aby aplikace zůstala v provozu, neměli byste v ASTA vláknu spouštět všechny vstupně-výstupní operace náročné na procesor a v/v. Za druhé, výsledky, které pocházejí z vláken na pozadí, musí být zařazeny zpátky do ASTA, aby se aktualizovalo uživatelské rozhraní. V aplikaci C++ `MainPage` pro UWP a ostatní stránky XAML jsou všechny spuštěné v ATSA. Proto se ve výchozím nastavení spouštějí pokračování úlohy, která jsou deklarována v ASTA, aby bylo možné aktualizovat ovládací prvky přímo v těle pokračování. Pokud však provedete vnoření úkolu v jiné úloze, všechna pokračování na tomto vnořeném úkolu se spustí v modelu MTA. Proto je nutné vzít v úvahu, jestli chcete explicitně určit, v jakém kontextu se tato pokračování spouštějí.

Úkol, který je vytvořen z asynchronní operace, například `IAsyncOperation<TResult>`, používá speciální sémantiku, která vám může pomáhat ignorovat podrobnosti o vláknech. I když se operace může spustit na vlákně na pozadí (nebo nemusí být zálohována vůbec), jejich pokračování je ve výchozím nastavení zaručeno pro spuštění v typu apartment, který zahájil operace pokračování (jinými slovy, z typu apartment, který se nazývá `task::then`.). Pro řízení kontextu provádění pokračování lze použít třídu [Concurrency:: task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) . Pomocí těchto statických pomocných metod `task_continuation_context` vytvořte objekty:

- Použijte [Concurrency:: task_continuation_context:: use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) k určení, že pokračování běží ve vlákně na pozadí.

- Použijte [Concurrency:: task_continuation_context:: use_current](reference/task-continuation-context-class.md#use_current) , chcete-li určit, že pokračování běží ve vlákně `task::then`, které je voláno.

Můžete předat `task_continuation_context` objekt metodě [Task:: then](reference/task-class.md#then) pro explicitní řízení kontextu provádění pokračování nebo můžete předat úkol do jiného objektu Apartment `task::then` a pak zavolat metodu pro implicitní řízení kontextu spuštění. .

> [!IMPORTANT]
>  Vzhledem k tomu, že hlavní vlákno uživatelského rozhraní aplikací pro UWP běží pod STA, pokračování, která v tomto STA vytvoříte, se spustí v STA. Proto pokračování vytvořená v modulu MTA běží v prostředí MTA.

Následující část ukazuje aplikaci, která čte soubor z disku, najde nejběžnější slova v tomto souboru a potom zobrazí výsledky v uživatelském rozhraní. Poslední operace, která aktualizuje uživatelské rozhraní, dojde ve vlákně uživatelského rozhraní.

> [!IMPORTANT]
> Toto chování je specifické pro aplikace pro UWP. U aplikací klasické pracovní plochy neřídíte, kde se budou spouštět pokračování. Místo toho Plánovač zvolí pracovní vlákno, ve kterém se má spustit každé pokračování.

> [!IMPORTANT]
> Nevolejte metodu [Concurrency:: task:: wait](reference/task-class.md#wait) v těle pokračování, které běží na sta. V opačném případě modul runtime vyvolá [Concurrency:: invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) , protože tato metoda blokuje aktuální vlákno a může způsobit, že aplikace přestane reagovat. Můžete však zavolat metodu [Concurrency:: task:: Get](reference/task-class.md#get) pro přijetí výsledku předchozí úlohy v pokračování založeném na úlohách.

##  <a name="example-app"></a>Případě Řízení spouštění v prostředí Windows Runtime aplikace pomocí C++ a XAML

Vezměte v C++ úvahu aplikaci XAML, která čte soubor z disku, najde nejběžnější slova v tomto souboru a potom zobrazí výsledky v uživatelském rozhraní. Pokud chcete vytvořit tuto aplikaci, začněte v aplikaci Visual Studio vytvořením prázdného projektu **aplikace (univerzální pro Windows)** a pojmenujte ho `CommonWords`. V manifestu aplikace určete schopnost **knihovny dokumenty** , aby aplikace mohla přistupovat ke složce dokumentů. Přidejte také textový soubor (. txt) do části Declarations (deklarace) manifestu aplikace. Další informace o funkcích a deklaracích aplikace naleznete v tématu [balení, nasazení a dotazování aplikací pro Windows](/windows/win32/appxpkg/appx-portal).

Aktualizujte `ProgressRing` `TextBlock` element v souboru MainPage. XAML tak, aby zahrnoval element a element. `Grid` Označuje, že operace probíhá, `TextBlock` a zobrazuje výsledky výpočtu. `ProgressRing`

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

Přidejte následující `#include` příkazy do souboru PCH. h.

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

Přidejte následující deklarace metody do `MainPage` třídy (MainPage. h).

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

Přidejte následující `using` příkazy do MainPage. cpp.

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

V MainPage. cpp implementujte `MainPage::MakeWordList`metody, `MainPage::FindCommonWords`a. `MainPage::ShowResults` A provádí `MainPage::FindCommonWords` výpočetní a náročné operace. `MainPage::MakeWordList` `MainPage::ShowResults` Metoda zobrazí výsledek výpočtu v uživatelském rozhraní.

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

Upravte konstruktor tak, aby vytvořil řetězec pokračujících úloh, které se zobrazí v uživatelském rozhraní, což je společná slova v knize Iliad podle Homer. `MainPage` První dva pokračující úkoly, které rozdělí text na jednotlivá slova a hledají běžná slova, můžou být časově náročné a jsou proto explicitně nastaveny tak, aby běžely na pozadí. Úloha poslední pokračování, která aktualizuje uživatelské rozhraní, neurčuje kontext pokračování, a proto řídí pravidla vláken typu apartment.

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
>  Tento příklad ukazuje, jak určit kontexty provádění a jak vytvořit řetězec pokračování. Ve výchozím nastavení se úloha, která je vytvořena z asynchronní operace, spustí jejich pokračování v izolovaném typu, který `task::then`je volán. Proto tento příklad používá `task_continuation_context::use_arbitrary` k určení, které operace, které nezahrnují uživatelské rozhraní, musí být provedeny ve vlákně na pozadí.

Na následujícím obrázku jsou znázorněny výsledky `CommonWords` aplikace.

![Aplikace prostředí Windows Runtime CommonWords](../../parallel/concrt/media/concrt_windows_common_words.png "Aplikace prostředí Windows Runtime CommonWords")

V tomto příkladu je možné podporovat zrušení, protože `task` objekty, které podporují `create_async` použití implicitního tokenu zrušení. Definujte pracovní funkci pro převzetí `cancellation_token` objektu, pokud vaše úkoly musí reagovat na zrušení v družstvu. Další informace o zrušení v PPL najdete v tématu [zrušení v PPL](cancellation-in-the-ppl.md) .

## <a name="see-also"></a>Viz také:

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)
