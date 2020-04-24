---
title: 'Návod: Připojení pomocí úloh a žádostí XML HTTP'
ms.date: 04/25/2019
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
ms.openlocfilehash: 2c627a543ec18702bf5358ff0170bec177fd7497
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032262"
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Návod: Připojení pomocí úloh a žádostí XML HTTP

Tento příklad ukazuje, jak používat rozhraní [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) a [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) spolu s úkoly k odeslání požadavků HTTP GET a POST webové službě v aplikaci Univerzální platforma Windows (UPW). Propojením požadavku `IXMLHTTPRequest2` s úkoly můžete psát kód, který lze kombinovat s ostatními úkoly. Úlohu stahování můžete například použít jako součást řetězce úkolů. Úloha stahování může také reagovat při zrušení práce.

> [!TIP]
> Pomocí sady C++ REST SDK můžete také provádět požadavky HTTP z aplikace UPW pomocí aplikace C++ nebo z desktopové aplikace C++. Další informace naleznete v tématu [C++ REST SDK (kódové označení "Casablanca")](https://github.com/Microsoft/cpprestsdk).

Další informace o úkolech naleznete v [tématu Paralelismus úloh](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Další informace o použití úloh v aplikaci UPW naleznete [v tématu Asynchronní programování v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) a [Vytváření asynchronních operací v jazyce C++ pro aplikace UPW](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

Tento dokument nejprve `HttpRequest` ukazuje, jak vytvořit a jeho podpůrné třídy. Potom ukazuje, jak používat tuto třídu z aplikace UPW, která používá C++ a XAML.

Příklad, který `IXMLHTTPRequest2` používá, ale nepoužívá úkoly, najdete [v tématu Úvodní příručka: Připojení pomocí xml http požadavku (IXMLHTTPRequest2).](/previous-versions/windows/apps/hh770550\(v=win.10\))

> [!TIP]
> `IXMLHTTPRequest2`a `IXMLHTTPRequest2Callback` jsou rozhraní, které doporučujeme pro použití v aplikaci UPW. Tento příklad můžete také upravit pro použití v desktopové aplikaci.

## <a name="prerequisites"></a>Požadované součásti

Podpora UPW je volitelná v sadě Visual Studio 2017 a novějších. Chcete-li ji nainstalovat, otevřete instalační službu sady Visual Studio z nabídky Start systému Windows a zvolte verzi sady Visual Studio, kterou používáte. Klepněte na tlačítko **Změnit** a zkontrolujte, zda je zaškrtnutá dlaždice **Vývoj UPW.** V části **Volitelné součásti** zkontrolujte, zda je zaškrtnuto **políčko C++ Nástroje UWP.** Použijte v141 pro Visual Studio 2017 nebo v142 pro Visual Studio 2019.

## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>Definice tříd HttpRequest, HttpRequestBuffersCallback a HttpRequestStringCallback

Při použití `IXMLHTTPRequest2` rozhraní k vytvoření webových požadavků přes `IXMLHTTPRequest2Callback` HTTP, implementovat rozhraní pro příjem odpovědi serveru a reagovat na jiné události. Tento příklad definuje `HttpRequest` třídu pro vytvoření webových požadavků a `HttpRequestBuffersCallback` třídy a `HttpRequestStringCallback` pro zpracování odpovědí. `HttpRequestBuffersCallback` Třídy `HttpRequestStringCallback` a `HttpRequest` podporují třídu; pracujete pouze `HttpRequest` s třídou z kódu aplikace.

Metody `GetAsync` `PostAsync` , `HttpRequest` umožňují spustit operace HTTP GET a POST. Tyto metody `HttpRequestStringCallback` používají třídu ke čtení odpovědi serveru jako řetězec. Metody `SendAsync` `ReadAsync` a umožňují streamovat velký obsah v blocích. Tyto metody každý vrátit [souběžnost::task](../../parallel/concrt/reference/task-class.md) reprezentovat operaci. Metody `GetAsync` `PostAsync` a `task<std::wstring>` vytvářejí hodnotu, kde `wstring` část představuje odpověď serveru. Metody `SendAsync` `ReadAsync` a `task<void>` vytvářejí hodnoty; tyto úkoly se dokončí po dokončení operací odesílání a čtení.

Vzhledem `IXMLHTTPRequest2` k tomu, že rozhraní působí asynchronně, tento příklad používá [souběžnost::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) k vytvoření úlohy, která se dokončí po dokončení objektu zpětného volání nebo zruší operaci stahování. Třída `HttpRequest` vytvoří pokračování na základě úlohy z tohoto úkolu nastavit konečný výsledek. Třída `HttpRequest` používá pokračování založené na úlohách, aby zajistila, že úloha pokračování bude spuštěna i v případě, že předchozí úloha způsobí chybu nebo je zrušena. Další informace o pokračování na základě úloh, naleznete [v tématu Paralelismus úlohy](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

Chcete-li podporovat `HttpRequest` `HttpRequestBuffersCallback`zrušení, `HttpRequestStringCallback` , a třídy použít tokeny zrušení. A `HttpRequestBuffersCallback` `HttpRequestStringCallback` třídy používají [souběžnost::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) metodu, aby událost dokončení úkolu reagovala na zrušení. Toto zpětné volání zrušení přeruší stahování. Další informace o zrušení najdete v tématu [Zrušení](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

### <a name="to-define-the-httprequest-class"></a>Definice třídy HttpRequest

1. V hlavní nabídce zvolte **Soubor** > **nového** > **projektu**.

1. Pomocí šablony prázdné aplikace jazyka C++ **(Universal Windows)** vytvořte prázdný projekt aplikace XAML. Tento příklad pojmenuje projekt `UsingIXMLHTTPRequest2`.

1. Přidejte do projektu soubor záhlaví s názvem HttpRequest.h a zdrojový soubor s názvem HttpRequest.cpp.

1. V pch.h přidejte tento kód:

   [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]

1. V souboru HttpRequest.h přidejte tento kód:

   [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]

1. V souboru HttpRequest.cpp přidejte tento kód:

   [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]

## <a name="using-the-httprequest-class-in-a-uwp-app"></a>Použití třídy HttpRequest v aplikaci UPW

Tato část ukazuje, jak `HttpRequest` používat třídu v aplikaci UPW. Aplikace poskytuje vstupní pole, které definuje prostředek adresy URL a příkazy tlačítek, které provádějí operace GET a POST, a příkaz tlačítka, který zruší aktuální operaci.

### <a name="to-use-the-httprequest-class"></a>Použití třídy HttpRequest

1. V MainPage.xaml definujte element [StackPanel](/uwp/api/windows.ui.xaml.controls.stackpanel) následujícím způsobem.

   [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]

1. V souboru MainPage.xaml.h přidejte tuto `#include` direktivu:

   [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]

1. V souboru MainPage.xaml.h přidejte `MainPage` do třídy tyto `private` členské proměnné:

   [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]

1. V souboru MainPage.xaml.h `ProcessHttpRequest`deklarujte metodu `private` :

   [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]

1. V souboru MainPage.xaml.cpp přidejte tyto `using` příkazy:

   [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]

1. V souboru MainPage.xaml.cpp implementujte `GetButton_Click`metodu , `PostButton_Click`a `CancelButton_Click` metody třídy. `MainPage`

   [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]

   > [!TIP]
   > Pokud vaše aplikace nevyžaduje podporu pro zrušení, předat [souběžnost::cancellation_token:none](reference/cancellation-token-class.md#none) na `HttpRequest::GetAsync` a `HttpRequest::PostAsync` metody.

1. V Souboru MainPage.xaml.cpp implementujte metodu. `MainPage::ProcessHttpRequest`

   [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]

1. Ve vlastnostech projektu v části **Propojovací aplikace**, **Input**zadejte `shcore.lib` a `msxml6.lib`.

Zde je spuštěná aplikace:

![Spuštěná aplikace Windows Runtime](../../parallel/concrt/media/concrt_usingixhr2.png "Spuštěná aplikace Windows Runtime")

## <a name="next-steps"></a>Další kroky

[Návody runtime souběžnosti](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

## <a name="see-also"></a>Viz také

[Paralelismus úkolu](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Asynchronní programování v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)<br/>
[Vytváření asynchronních operací v jazyce C++ pro aplikace UPW](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)<br/>
[Úvodní příručka: Připojení pomocí třídy úlohy požadavku XML HTTP (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\))
[(Runtime souběžnosti)](../../parallel/concrt/reference/task-class.md)<br/>
[task_completion_event – třída](../../parallel/concrt/reference/task-completion-event-class.md)
