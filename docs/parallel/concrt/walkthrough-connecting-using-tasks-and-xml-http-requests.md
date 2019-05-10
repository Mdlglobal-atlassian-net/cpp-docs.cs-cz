---
title: 'Návod: Připojení pomocí úloh a žádostí XML HTTP'
ms.date: 04/25/2019
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
ms.openlocfilehash: 449f99f37f0d328b7c874730b814335f8b69e807
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856284"
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Návod: Připojení pomocí úloh a žádostí XML HTTP

Tento příklad ukazuje způsob použití [IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2) a [IXMLHTTPRequest2Callback](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback) spolu s úkoly odesílajícími požadavky HTTP GET a POST na webovou službu v Universal Windows Platform (UPW ) aplikace. Propojením požadavku `IXMLHTTPRequest2` s úkoly můžete psát kód, který lze kombinovat s ostatními úkoly. Například můžete použít úlohu stahování jako součást posloupnosti úkolů. Úloha stažení můžete také odpovídat při práci se zruší.

> [!TIP]
>  C++ REST SDK můžete použít také k provádění požadavků protokolu HTTP z aplikace pro UPW pomocí aplikace jazyka C++ nebo z desktopové aplikace jazyka C++. Další informace najdete v tématu [C++ REST SDK (kódový název "Casablanca")](https://github.com/Microsoft/cpprestsdk).

Další informace o úlohách najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Další informace o tom, jak použít úlohy v aplikaci UWP, naleznete v tématu [asynchronní programování v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) a [vytváření asynchronních operací v jazyce C++ pro aplikace pro UPW](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

Tento dokument nejprve ukazuje, jak vytvořit `HttpRequest` a její podpůrnou třídy. Následně ukazuje, jak použít tuto třídu v rámci aplikace pro UPW, která používá C++ a XAML.

Příklad, který používá `IXMLHTTPRequest2` ale úkoly, naleznete v tématu [rychlý start: Připojení pomocí XML požadavku protokolu HTTP (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\)).

> [!TIP]
>  `IXMLHTTPRequest2` a `IXMLHTTPRequest2Callback` jsou rozhraní, které doporučujeme pro použití v aplikaci UWP. Tento příklad pro použití v desktopové aplikaci můžete také přizpůsobit.

## <a name="prerequisites"></a>Požadavky

Podpora UWP je volitelné v sadě Visual Studio 2017 nebo novější. Ho Pokud chcete nainstalovat, spusťte instalační program sady Visual Studio v nabídce Windows Start a zvolte verzi sady Visual Studio, kterou používáte. Klikněte na tlačítko **změnit** tlačítko a ujistěte se, že **vývoj UWP** je zaškrtnuté políčko vedle sebe. V části **volitelné součásti** Ujistěte se, že  **C++ nástrojů pro UPW** je zaškrtnuté políčko. Použijte v141 pro Visual Studio 2017 nebo v142 pro Visual Studio 2019.

## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>Definice tříd HttpRequest, HttpRequestBuffersCallback a HttpRequestStringCallback

Při použití `IXMLHTTPRequest2` rozhraní pro vytvoření webových požadavků pomocí protokolu HTTP, můžete implementovat `IXMLHTTPRequest2Callback` rozhraní pro příjem odpovědi serveru a reagovat na další události. Tento příklad definuje `HttpRequest` třídy za účelem vytvoření webových požadavků a `HttpRequestBuffersCallback` a `HttpRequestStringCallback` třídy ke zpracování odpovědi. `HttpRequestBuffersCallback` a `HttpRequestStringCallback` třídy podporu `HttpRequest` třídy autority fungovat jenom s `HttpRequest` třídu v kódu aplikace.

`GetAsync`, `PostAsync` Metody `HttpRequest` třídy umožňují spustit operací HTTP GET a POST, v uvedeném pořadí. Tyto metody používají `HttpRequestStringCallback` třídy ke čtení odpovědi serveru jako řetězec. `SendAsync` a `ReadAsync` metody umožňují streamování velkých obsahu v blocích. Tyto metody každý vrací [concurrency::task](../../parallel/concrt/reference/task-class.md) představující operaci. `GetAsync` a `PostAsync` metody vracet `task<std::wstring>` hodnota, kde `wstring` část představuje odpověď serveru. `SendAsync` a `ReadAsync` metody vracet `task<void>` hodnoty; tyto úlohy dokončení po dokončení operací send a pro čtení.

Vzhledem k tomu, `IXMLHTTPRequest2` rozhraní funguje asynchronně, v tomto příkladu [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) k vytvoření úlohy, která se dokončí poté, co objekt zpětného volání dokončí nebo zruší operaci stahování. `HttpRequest` Třídy pokračování podle úloh vytvoří z této úlohy můžete nastavit konečný výsledek. `HttpRequest` Třídy využívají pokračování podle úloh k zajištění toho, že úloha pokračování spustí i v případě předchozího úkolu, dojde k chybě nebo se zruší. Další informace o pokračování založené na úlohách najdete v tématu [funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

Pro podporu zrušení, `HttpRequest`, `HttpRequestBuffersCallback`, a `HttpRequestStringCallback` třídy použití tokenů zrušení. `HttpRequestBuffersCallback` a `HttpRequestStringCallback` třídy použijte [concurrency::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) metoda umožňuje událost dokončení úkolu reagovat na zrušení. Toto zpětné volání zrušení zruší stahování. Další informace o zrušení naleznete v tématu [zrušení](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

#### <a name="to-define-the-httprequest-class"></a>Definice třídy HttpRequest

1. V hlavní nabídce zvolte **souboru** > **nový** > **projektu**. 

1. Použití C++ **prázdná aplikace (Universal Windows)** šablony k vytvoření prázdného projektu aplikace XAML. V tomto příkladu názvy projektu `UsingIXMLHTTPRequest2`.

1. Přidejte do projektu soubor hlaviček, který je pojmenován HttpRequest.h a zdrojový soubor, který je pojmenován HttpRequest.cpp.

1. V soubor pch.h přidejte tento kód:

   [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]

1. V HttpRequest.h přidejte tento kód:

   [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]

1. V HttpRequest.cpp přidejte tento kód:

   [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]

## <a name="using-the-httprequest-class-in-a-uwp-app"></a>Používání třídy HttpRequest v aplikaci UWP

Tato část popisuje způsob použití `HttpRequest` třídy v aplikaci UWP. Aplikace obsahuje vstupní pole, která definuje prostředek URL, a příkazy tlačítek, které provádějí operace GET a POST a tlačítko příkaz, který zruší aktuální operaci.

#### <a name="to-use-the-httprequest-class"></a>Použití třídy HttpRequest

1. V souboru MainPage.xaml definujte [StackPanel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx) element následujícím způsobem.

   [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]

2. V MainPage.xaml.h přidejte tuto `#include` – direktiva:

   [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]

3. V MainPage.xaml.h přidejte tyto `private` členské proměnné `MainPage` třídy:

   [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]

4. V MainPage.xaml.h deklarovat `private` metoda `ProcessHttpRequest`:

   [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]

5. V souboru MainPage.xaml.cpp přidejte tyto `using` příkazy:

   [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]

6. Ve MainPage.xaml.cpp implementujte `GetButton_Click`, `PostButton_Click`, a `CancelButton_Click` metody `MainPage` třídy.

   [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]

   > [!TIP]
   > Pokud vaše aplikace nevyžaduje podporu zrušení, předejte [concurrency::cancellation_token:: žádný](reference/cancellation-token-class.md#none) k `HttpRequest::GetAsync` a `HttpRequest::PostAsync` metody.

1. Ve MainPage.xaml.cpp implementujte `MainPage::ProcessHttpRequest` metody.

   [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]

8. Ve vlastnostech projektu v rámci **Linkeru**, **vstup**, zadejte `shcore.lib` a `msxml6.lib`.

Tady je spuštěné aplikaci:

![Spuštěné aplikaci Windows Runtime](../../parallel/concrt/media/concrt_usingixhr2.png "spuštěné aplikaci Windows Runtime")

## <a name="next-steps"></a>Další kroky

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

## <a name="see-also"></a>Viz také:

[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Asynchronní programování v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)<br/>
[Vytváření asynchronních operací v jazyce C++ pro aplikace pro UPW](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)<br/>
[Rychlý start: Připojení pomocí XML požadavku protokolu HTTP (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\))
[task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)<br/>
[task_completion_event – třída](../../parallel/concrt/reference/task-completion-event-class.md)
