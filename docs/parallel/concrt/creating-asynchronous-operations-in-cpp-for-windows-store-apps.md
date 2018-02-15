---
title: "Vytváření asynchronních operací v jazyce C++ pro aplikace UWP | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99251cbf6627d07075dad3d7dfa3fd4d9651fea8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>Vytváření asynchronních operací v jazyce C++ pro aplikace UWP
Tento dokument popisuje některé z klíčových bodů třeba vzít v úvahu při použití třídy úlohy k vytvoření založené na Windows zachovalo asynchronních operací v aplikaci pro univerzální Windows Runtime (UWP).  
  
 Použití asynchronního programování je klíčovou komponentou v prostředí Windows Runtime modelu aplikace, protože umožňuje aplikace zůstala reaguje na vstup uživatele. Dlouhodobou úlohu můžete spustit bez blokování vlákna uživatelského rozhraní a zobrazí výsledky úlohy později. Můžete také zrušení úloh a přijímat oznámení průběhu jako úlohy se spouštějí na pozadí. Dokument [asynchronní programování v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) poskytuje přehled o asynchronní vzor, který je k dispozici v jazyce Visual C++ vytvářet aplikace pro UPW. Tento dokument učí, jak využívat i vytvořit řetězy asynchronních operací v prostředí Windows Runtime. Tato část popisuje, jak použít typy v ppltasks.h k vytváření asynchronních operací, které mohou být spotřebovávána jiné komponenty prostředí Windows Runtime a je proveden řízení jak asynchronní pracovní postupy. Zvažte také čtení [asynchronní programování vzory a tipy v Hilo (aplikace pro Windows Store pomocí C++ a XAML)](http://msdn.microsoft.com/library/windows/apps/jj160321.aspx) se dozvíte, jak jsme použili třída úlohy k implementaci asynchronních operací v Hilo, aplikace prostředí Windows Runtime s použitím C++ a XAML.  
  
> [!NOTE]
>  Můžete použít [Parallel Library vzory](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) a [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) v aplikaci UWP. Nelze však použít Plánovač úloh nebo správce prostředků. Tento dokument popisuje další funkce, které poskytuje knihovně PPL které jsou k dispozici pouze do aplikace pro UPW a ne do aplikace na ploše.  
  
## <a name="key-points"></a>Klíčové body  

-   Použití [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) vytvořit asynchronních operací, které můžete používat ostatní součásti (které může být napsán v jiných jazyků než C++).  

  
-   Použití [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) k odesílání oznámení průběhu sestavy do součásti, které volají asynchronní operace.  
  
-   Zrušení tokenů použijte k povolení interní asynchronní operace zrušení.  
  
-   Chování `create_async` funkce závisí na návratový typ funkce pracovní, který je předán. Pracovní funkci, která vrátí úlohu (buď `task<T>` nebo `task<void>`) synchronně běží v kontextu, který volá `create_async`. Pracovní funkci, která vrátí `T` nebo `void` běží v kontextu libovolného.  
  
-   Můžete použít [concurrency::task::then](reference/task-class.md#then) metodu pro vytvoření řetěz úlohy, které spustí jedna po druhé. V aplikaci pro UPW výchozí kontext pro pokračování úlohy závisí na tom, jak byl zkonstruován tuto úlohu. Pokud úloha byla vytvořena pomocí předání asynchronní akce v konstruktoru úloh nebo pomocí předání výrazu lambda, která vrací asynchronní akce, výchozí kontext pro všechny pokračování této úlohy je aktuálním kontextu. Pokud je úloha není vytvořen z asynchronní akce, poté kontextu libovolný se používá ve výchozím nastavení pro pokračování úkolu. Můžete přepsat výchozí kontext s [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) třídy.  

  
## <a name="in-this-document"></a>V tomto dokumentu  
  
-   [Vytváření asynchronních operací](#create-async)  
  
-   [Příklad: Vytvoření komponenty prostředí Windows Runtime C++](#example-component)  
  
-   [Řízení provádění vlákna](#exethread)  
  
-   [Příklad: Řízení provádění v aplikaci Windows Runtime s C++ a XAML](#example-app)  
  
##  <a name="create-async">Vytváření asynchronních operací</a>  
 Úloha a pokračování modelu můžete použít k definování úlohy na pozadí, jakož i další úkoly, které jsou spuštěny při dokončení předchozí úlohy v paralelní vzory knihovny (PPL). Tato funkce poskytuje [concurrency::task](../../parallel/concrt/reference/task-class.md) třídy. Další informace o tomto modelu a `task` třídy najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Prostředí Windows Runtime je programovací rozhraní, které můžete použít k vytvoření aplikace UPW, které spouští pouze v prostředí speciální operačního systému. Tyto aplikace použít oprávnění funkce, datové typy a zařízení a jsou distribuované z Microsoft Store. Prostředí Windows Runtime je reprezentována *binární rozhraní aplikace* (ABI). ABI je základní binární kontrakt, který zpřístupňuje rozhraní API systému Windows Runtime programovacích jazyků, jako je například Visual C++.  
  
 Pomocí prostředí Windows Runtime, můžete použít nejlepší funkce v různých programovacích jazyků a sloučit je do jedné aplikace. Můžete například vytvořit uživatelské rozhraní v jazyce JavaScript a provádět výpočetně náročných aplikace logiky v komponent C++. Schopnost provádět tyto operace výpočetně náročných na pozadí je klíčovým faktorem při ochraně reagující uživatelské rozhraní. Protože `task` třída je specifická pro jazyk C++, je nutné použít prostředí Windows Runtime rozhraní pro komunikaci asynchronní operace pro jiné komponenty, (které může být napsán v jiných jazyků než C++). Prostředí Windows Runtime obsahuje čtyři rozhraní, které můžete použít k reprezentování asynchronních operací:  
  
 [Windows::Foundation::IAsyncAction](http://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncaction.aspx)  
 Představuje asynchronní akce.  
  
 [Windows::Foundation::IAsyncActionWithProgress\<TProgress>](http://msdn.microsoft.com/library/windows/apps/br206581.aspx)  
 Představuje asynchronní akce, která generuje sestavy průběhu.  
  
 [Windows::Foundation::IAsyncOperation\<TResult>](http://msdn.microsoft.com/library/windows/apps/br206598.aspx)  
 Reprezentuje asynchronní operaci, která vrací výsledek.  
  
 [Windows::Foundation::IAsyncOperationWithProgress\<TResult, TProgress>](http://msdn.microsoft.com/library/windows/apps/br206594.aspx)  
 Reprezentuje asynchronní operaci, která vrací výsledek a sestavy průběhu.  
  
 Znalost problematicky *akce* znamená, že asynchronní úloha neobsahuje hodnotu (Považujte funkci, která vrátí `void`). Znalost problematicky *operace* znamená, že asynchronní úlohu vytvoření hodnoty. Znalost problematicky *průběh* znamená, že úloha může sestavy zprávy o průběhu volajícímu. JavaScript, rozhraní .NET Framework a aplikace Visual C++ poskytuje vlastní způsob, jak vytvořit instance tato rozhraní pro použití v rámci hranic ABI. Pro Visual C++, poskytuje knihovně PPL [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) funkce. Tato funkce vytváří asynchronní akce prostředí Windows Runtime nebo operaci, která představuje dokončení úlohy. `create_async` Funkce trvá pracovní funkci (obvykle výrazu lambda), interně vytvoří `task` objekt a zabalí, které úlohy v jedné z čtyři asynchronní prostředí Windows Runtime rozhraní.  
  
> [!NOTE]
>  Použití `create_async` pouze když je nutné vytvořit funkce, která je přístupná z jiný jazyk nebo jiné komponenty prostředí Windows Runtime. Použití `task` třídy přímo, když víte, že operace je vytvořeného i spotřebovávají kódu C++ v komponentě stejné.  
  
 Návratový typ `create_async` je určen podle typu její argumenty. Pokud vaše pracovní funkce nevrací hodnotu a nemá hlásit průběh, například `create_async` vrátí `IAsyncAction`. Pokud vaše pracovní funkce nevrací hodnotu a také sestavy průběhu `create_async` vrátí `IAsyncActionWithProgress`. Chcete-li hlásit průběh, zadejte [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) objektu jako parametr pro svoji pracovní funkci. Možnost sestavy průběhu umožňuje nahlásit byla provedena jaké množství práce, a jaké množství stále zůstává (například jako procento). Také vám umožní ohlásit výsledky, jakmile budou k dispozici.  
  
 `IAsyncAction`, `IAsyncActionWithProgress<TProgress>`, `IAsyncOperation<TResult>`, A `IAsyncActionOperationWithProgress<TProgress, TProgress>` poskytují rozhraní každé `Cancel` metoda, která umožňuje zrušit asynchronní operaci. `task` Třída pracuje s zrušení tokenů. Použijete-li zrušit pracovní token zrušení, modul runtime nespustí nové práci, která si předplatí tento token. Práce, která je již aktivní můžete sledovat jeho token zrušení a zastavit, když je to možné. Tento mechanismus je větší podrobně popsány v dokumentu [zrušení v knihovně PPL](cancellation-in-the-ppl.md). Zrušení úlohy můžete připojit pomocí prostředí Windows Runtime`Cancel` metody dvěma způsoby. První, můžete definovat pracovní funkce, která je předat do `create_async` provést [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) objektu. Když `Cancel` metoda je volána, tento token zrušení byla zrušena a pravidla normální zrušení platí pro základní `task` objekt, který podporuje `create_async` volání. Pokud nezadáte `cancellation_token` objektu základní `task` objekt definuje jeden implicitně. Definování `cancellation_token` objektu, když potřebujete spolupráce při reagovat na zrušení v svoji pracovní funkci. V části [příklad: řízení provádění v aplikaci Windows Runtime s C++ a XAML](#example-app) ukazuje příklad toho, jak provést zrušení v aplikaci pro univerzální platformu Windows (UWP) s C# a XAML, která používá vlastní C++ Runtime Windows komponenta.  
  
> [!WARNING]
>  V řetězu pokračování úlohy, vždy vyčištění stavu a pak zavolají [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) když byla zrušena token zrušení. Pokud jste již v rané fázi vrátí místo volání `cancel_current_task`, operace přechody do stavu dokončení místo zrušené stavu.  

  
 Následující tabulka shrnuje kombinace, které můžete použít k definování asynchronních operací v aplikaci.  
  
|K vytvoření tohoto prostředí Windows Runtime rozhraní|Vrátí tohoto typu z `create_async`|Tyto typy parametrů předat svoji pracovní funkci použít token implicitní zrušení|Tyto typy parametrů předat svoji pracovní funkci použít token explicitní zrušení|  
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|  
|`IAsyncAction`|`void` Nebo `task<void>`|(žádný)|(`cancellation_token`)|  
|`IAsyncActionWithProgress<TProgress>`|`void` Nebo `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|  
|`IAsyncOperation<TResult>`|`T` Nebo `task<T>`|(žádný)|(`cancellation_token`)|  
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` Nebo `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|  
  
 Můžete vrátit hodnotu nebo `task` z pracovní funkce, která můžete předat objekt `create_async` funkce. Tyto odchylky vytvořit různé chování. Při návratu hodnotu, pracovní funkce je uzavřen do `task` tak, aby mohl být program spuštěn na vlákna na pozadí. Kromě toho základní `task` používá token implicitní zrušení. Naopak pokud se vrátíte `task` objektu, pracovní funkce spouští synchronně. Proto pokud se vrátíte `task` objektu, ujistěte se, že žádné náročná operace v svoji pracovní funkci také spustit jako úlohy, které chcete povolit aplikaci zůstat reaguje. Kromě toho základní `task` nepoužívá token implicitní zrušení. Proto je nutné definovat svoji pracovní funkci provést `cancellation_token` objektu, pokud budete potřebovat podporu pro zrušení při návratu `task` objektu z `create_async`.  
  
 Následující příklad ukazuje různé způsoby vytvoření `IAsyncAction` objektu, která mohou být spotřebovávána jiné komponenty prostředí Windows Runtime.  
  
 [!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]  
  
##  <a name="example-component"></a> Příklad: Vytvoření komponenty prostředí Windows Runtime C++ a použití z jazyka C#  
 Zvažte aplikaci, která používá XAML a C# pro definování uživatelského rozhraní a komponent prostředí C++ Windows Runtime provádět operace náročné na výkon. V tomto příkladu C++ component vypočítá prime jsou které čísla v zadaném rozsahu. Pro ilustraci rozdíly mezi čtyři rozhraní asynchronní úlohu prostředí Windows Runtime, spuštění, v sadě Visual Studio, tak, že vytvoříte **prázdného řešení** a pojmenování ji `Primes`. Pak přidejte do řešení **komponenty prostředí Windows Runtime** projektu a pojmenování ji `PrimesLibrary`. Přidejte následující kód do vygenerovaný soubor hlaviček C++ (Tento příklad přejmenuje Class1.h na Primes.h). Každý `public` metoda definuje jednomu z rozhraní čtyři asynchronní. Vrátí metody, které vrátit hodnotu [Windows::Foundation::Collections::IVector\<int >](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) objektu. Vytvoření metody, které hlásit průběh `double` hodnoty, které definují procentuální hodnotu celkové práce, které bylo dokončeno.  
  
 [!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]  
  
> [!NOTE]
>  Podle konvence asynchronní metody názvy v prostředí Windows Runtime obvykle končit "Asynchronní".  
  
 Přidejte následující kód do vygenerovaný zdrojový soubor C++ (Tento příklad přejmenuje Class1.cpp na Primes.cpp). `is_prime` Funkce určuje, zda je vstupní prime. Ostatní metody implementovat `Primes` třídy. Každé volání `create_async` podpisu, který je kompatibilní s metodou, ze kterého se označuje jako používá. Například protože `Primes::ComputePrimesAsync` vrátí `IAsyncAction`, pracovní funkce, který je zadán pro `create_async` nevrací hodnotu a neberou v `progress_reporter` objektu jako její parametr.  
  
 [!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]  
  
 Každá metoda nejprve provádí ověřování a zajistí, že vstupní parametry jsou nezáporná. Pokud je vstupní hodnota záporná, vyvolá metoda [Platform::InvalidArgumentException](http://msdn.microsoft.com/library/windows/apps/hh755794\(v=vs.110\).aspx). Zpracování chyb je vysvětleno dále v této části.  
  
 Chcete-li používat tyto metody z aplikace pro UPW, použijte Visual C# **prázdná aplikace (XAML)** šablony přidat druhý projekt do řešení sady Visual Studio. Tento příklad názvy projektu `Primes`. Potom z `Primes` projekt, přidejte odkaz na `PrimesLibrary` projektu.  
  
 Přidejte následující kód do MainPage.xaml. Tento kód definuje uživatelské rozhraní, aby mohli volání komponent C++ a zobrazit výsledky.  
  
 [!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]  
  
 Přidejte následující kód, který `MainPage` třídy v MainPage.xaml. Tento kód definuje `Primes` objekt a obslužné rutiny událostí tlačítko.  
  
 [!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]  
  
 Tyto metody používat `async` a `await` klíčová slova aktualizace uživatelského rozhraní, po dokončení asynchronní operace. Informace o asynchronní kódování v aplikacích pro UPW najdete v tématu [zřetězení a asynchronní programování](/windows/uwp/threading-async).  
  
 `getPrimesCancellation` a `cancelGetPrimes` metody vzájemně spolupracují a zajistit, aby uživatel na tlačítko Storno. Když uživatel vybere **zrušit** tlačítko `cancelGetPrimes` volání metod [IAsyncOperationWithProgress\<TResult, TProgress >:: zrušit](http://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncinfo.cancel.aspx) na tlačítko Storno. Concurrency Runtime, která spravuje základní asynchronní operaci, vyvolá zachycené tímto prostředí Windows Runtime pro komunikaci, zda byla dokončena zrušení typem vnitřní výjimky. Další informace o zrušení modelu najdete v tématu [zrušení](../../parallel/concrt/cancellation-in-the-ppl.md).  
  
> [!IMPORTANT]
>  Pokud chcete povolit PPL správně informuje o prostředí Windows Runtime, zrušil operaci, není catch tento typ vnitřní výjimce. To znamená, že jste neměli také zachytit vše výjimky (`catch (...)`). Pokud musí všechny catch výjimky, opětovné výjimka zajistit, že prostředí Windows Runtime můžete dokončit operaci zrušení.  
  
 Následující obrázek ukazuje `Primes` aplikace po jednotlivých možností byla vybrána.  
  
 ![Aplikace Windows Runtime si mosty](../../parallel/concrt/media/concrt_windows_primes.png "concrt_windows_primes")  
  
 Příklady, které používají `create_async` vytvoření asynchronní úlohy, které mohou být spotřebovávána dalších jazyků naleznete v tématu [pomocí C++ v ukázce Bing Maps cestě Optimalizátor](http://msdn.microsoft.com/library/windows/apps/hh699891\(v=vs.110\).aspx) a [Windows 8 asynchronních operací v jazyce C++ s PPL](http://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d).  
  
##  <a name="exethread">Řízení provádění vlákna</a>  
 Prostředí Windows Runtime používá COM model vláken. V tomto modelu jsou objekty hostované v různých apartment, v závislosti na tom, jak budou pracovat s jejich synchronizaci. Objekty vláken jsou hostované v Vícevláknová typu apartment (MTA). Objekty, které musí být přístup jedním vláknem a jsou hostované v single-threaded apartment (STA).  
  
 V aplikaci, která má uživatelské rozhraní vlákno ASTA (aplikace STA) je zodpovědná za čerpání – zprávy okna a je pouze vláken v procesu, který může aktualizovat ovládací prvky hostované STA uživatelského rozhraní. To má dva důsledky. Nejdřív k tomu, aby aplikace zůstaly přizpůsobivý, všechny náročná na prostředky procesoru a vstupně-výstupních operací nesmí spustit na ASTA vlákno. Druhý výsledky, které pocházejí z vlákna na pozadí tvořit zpět na ASTA aktualizace uživatelského rozhraní. V aplikaci C++ UWP `MainPage` a dalších stránek XAML všechny spustili ATSA. Proto pokračování úlohy, které jsou deklarované v ASTA se spouštějí existuje ve výchozím nastavení, můžete aktualizovat ovládací prvky přímo v těle pokračování. Ale pokud je vnořovat úlohu v jiné úloze, všechny pokračování v této vnořené úlohy se spustí v MTA. Proto musíte zvážit, zda chcete explicitně určit, na jaké kontextu tyto pokračování spustit.  
  
 Úloha, která je vytvořená z asynchronní operace, jako například `IAsyncOperation<TResult>`, používá speciální sémantiku, které vám mohou pomoci ignorovat vláken podrobnosti. I když operace může spustit na vlákna na pozadí (nebo ji nemusí být založenou na vlákno vůbec), jeho pokračování jsou ve výchozím nastavení zaručit ke spuštění na typu apartment, který spustil pokračování operace (jinými slovy, z typu apartment, který volá `task::then`). Můžete použít [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) třída k řízení kontext provádění pokračování. Pomocí těchto statické pomocné metody pro vytvoření `task_continuation_context` objekty:  
  
-   Použití [concurrency::task_continuation_context::use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) k určení, že pokračování běžet ve vlákna na pozadí.  
  
-   Použití [concurrency::task_continuation_context::use_current](reference/task-continuation-context-class.md#use_current) k určení, že pokračování běží na vlákno, které volá `task::then`.  

  
 Můžete předat `task_continuation_context` do objektu [Task::Then –](reference/task-class.md#then) metoda explicitně řídit kontext provádění pokračování nebo lze předat jiné apartment úlohy a pak zavolají `task::then` implicitně řídit kontext spuštění.  
  
> [!IMPORTANT]
>  Protože hlavního vlákna uživatelského rozhraní aplikace UWP běh STA, pokračování, které vytvoříte v tomto STA standardně spustili STA Pokračování, které vytvoříte na MTA odpovídajícím způsobem, spusťte na MTA.  
  
 V následující části zobrazuje aplikaci, která načte soubor z disku, vyhledá nejčastější slova v tomto souboru a poté zobrazí výsledky v uživatelském rozhraní. Poslední operace, aktualizace uživatelského rozhraní, proběhne vlákna uživatelského rozhraní.  
  
> [!IMPORTANT]
>  Toto chování je specifické pro aplikace UWP. Aplikací klasické pracovní plochy není řídit, kde je spuštěn pokračování. Místo toho Plánovač zvolí pracovní vlákno, na kterém se má spouštět každý pokračování.  
  
> [!IMPORTANT]

>  Nevolejte [concurrency::task::wait](reference/task-class.md#wait) v těle pokračování, která běží na STA Jinak, modul runtime vyvolá [concurrency::invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) vzhledem k tomu, že tato metoda blokuje aktuální vlákno a může způsobit, že aplikace přestane odpovídat. Můžete však volat [concurrency::task::get](reference/task-class.md#get) metodu výsledek předchozí úlohou v pokračování založený na úlohách.  
  
##  <a name="example-app">Příklad: Řízení provádění v aplikaci Windows Runtime s C++ a XAML</a>  
 Vezměte v úvahu aplikace C++ XAML, který čte soubor z disku, vyhledá nejčastější slova v tomto souboru a poté zobrazí výsledky v uživatelském rozhraní. Chcete-li vytvořit tuto aplikaci, spuštění, v sadě Visual Studio, tak, že vytvoříte **prázdná aplikace (univerzální pro Windows)** projektu a pojmenování ji `CommonWords`. V manifestu aplikace, zadejte **knihovna dokumentů** možnost povolit aplikaci pro přístup do složky Dokumenty. Typ souboru Text (TXT) můžete také přidáte do sekce deklarace manifest aplikace. Další informace o možnosti aplikace a deklarace najdete v tématu [balíčky aplikací a nasazení](http://msdn.microsoft.com/library/windows/apps/hh464929.aspx).  
  
 Aktualizace `Grid` element v MainPage.xaml, zahrnout `ProgressRing` element a `TextBlock` elementu. `ProgressRing` Označuje, že operace je v průběhu a `TextBlock` zobrazuje výsledky výpočet.  
  
 [!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]  
  
 Přidejte následující `#include` příkazy, čímž pch.h.  
  
 [!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]  
  
 Přidejte následující deklarace metoda k `MainPage` – třída (MainPage.h).  
  
 [!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]  
  
 Přidejte následující `using` příkazy, čímž MainPage.cpp.  
  
 [!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]  
  
 V MainPage.cpp, implementovat `MainPage::MakeWordList`, `MainPage::FindCommonWords`, a `MainPage::ShowResults` metody. `MainPage::MakeWordList` a `MainPage::FindCommonWords` provádění výpočetně náročných operací. `MainPage::ShowResults` Metoda zobrazí výsledek výpočet v uživatelském rozhraní.  
  
 [!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]  
  
 Změnit `MainPage` konstruktor vytvořit řetěz pokračování úlohy, které se zobrazí v uživatelském rozhraní běžná slova v knize *Iliad* podle Homer. První dvě pokračování úlohy, která rozdělí text na jednotlivých slov a najít běžná slova, může být časově náročná a jsou proto explicitně nastaven na spouštění v pozadí. Poslední pokračování úkolu, který aktualizuje uživatelské rozhraní, určuje žádný kontext pokračování a tedy dodržuje pravidla vláken typu apartment.  
  
 [!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]  
  
> [!NOTE]
>  Tento příklad ukazuje, jak k určení kontextu provádění a jak tvoří řetěz pokračování. Odvolat, že ve výchozím nastavení úloh, který je vytvořený z asynchronní operace běží jeho pokračování na typu apartment, který volá `task::then`. Proto tento příklad používá `task_continuation_context::use_arbitrary` k určení, že operace, které nezahrnují rozhraní provést v vlákna na pozadí.  
  
 Následující obrázek znázorňuje výsledky `CommonWords` aplikace.  
  
 ![Aplikace Windows Runtime CommonWords](../../parallel/concrt/media/concrt_windows_common_words.png "concrt_windows_common_words")  
  
 V tomto příkladu je možné podporovat zrušení, protože `task` objektů, které podporují `create_async` pomocí tokenu implicitní zrušení. Zadejte svoji pracovní funkci provést `cancellation_token` objektu, pokud vaše úkoly potřeba reagovat na zrušení spolupráci způsobem. Další informace o zrušení v knihovně PPL najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md)  
  
## <a name="see-also"></a>Viz také  
 [Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)
