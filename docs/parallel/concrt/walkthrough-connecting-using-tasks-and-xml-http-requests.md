---
title: 'Návod: Připojení pomocí úloh a požadavků XML HTTP'
ms.date: 04/25/2019
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
ms.openlocfilehash: b11b56578cadc4b3bd037acf84014a718f9fad84
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512135"
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Návod: Připojení pomocí úloh a požadavků XML HTTP

Tento příklad ukazuje, jak používat rozhraní [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) a [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) spolu s úkoly k odesílání požadavků HTTP GET a post webové službě v aplikaci Univerzální platforma Windows (UWP). Propojením požadavku `IXMLHTTPRequest2` s úkoly můžete psát kód, který lze kombinovat s ostatními úkoly. Například můžete použít úlohu stáhnout jako součást řetězce úloh. Úkol stažení může také reagovat na zrušení práce.

> [!TIP]
>  Můžete také použít sadu C++ REST SDK k provádění požadavků HTTP z aplikace UWP pomocí C++ aplikace nebo z desktopové C++ aplikace. Další informace najdete v tématu [ C++ sada REST SDK (kódový název "Casablanca")](https://github.com/Microsoft/cpprestsdk).

Další informace o úlohách najdete v tématu [Task paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Další informace o tom, jak používat úkoly v aplikaci UWP, najdete v tématu [asynchronní programování C++ v](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) a [Vytváření asynchronních C++ operací v aplikacích pro UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

Tento dokument nejprve ukazuje, jak vytvořit `HttpRequest` a jeho podpůrné třídy. Pak ukazuje, jak tuto třídu používat z aplikace pro UWP, která používá C++ a XAML.

Příklad, který používá `IXMLHTTPRequest2` , ale nepoužívá úkoly, najdete v tématu [rychlý Start: Připojení pomocí požadavku HTTP XML (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\)).

> [!TIP]
>  `IXMLHTTPRequest2`a `IXMLHTTPRequest2Callback` jsou rozhraní, která doporučujeme použít v aplikaci pro UWP. Tento příklad můžete také upravit pro použití v desktopové aplikaci.

## <a name="prerequisites"></a>Požadavky

Podpora UWP je volitelná v aplikaci Visual Studio 2017 nebo novější. Chcete-li ji nainstalovat, otevřete Instalační program pro Visual Studio z nabídky Start systému Windows a vyberte verzi sady Visual Studio, kterou používáte. Klikněte na tlačítko **Upravit** a ujistěte se, že je zaškrtnutá dlaždice **vývoj pro UWP** . V části **volitelné součásti** se ujistěte, že **C++** jsou zaškrtnuté nástroje UWP. Použijte v141 pro Visual Studio 2017 nebo V142 pro Visual Studio 2019.

## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>Definice tříd HttpRequest, HttpRequestBuffersCallback a HttpRequestStringCallback

Když použijete `IXMLHTTPRequest2` rozhraní k vytváření webových požadavků přes protokol HTTP, `IXMLHTTPRequest2Callback` implementujete rozhraní pro příjem odpovědi serveru a reakci na další události. Tento příklad definuje `HttpRequest` třídu pro vytváření webových požadavků `HttpRequestBuffersCallback` a třídy a `HttpRequestStringCallback` pro zpracování odpovědí. Třídy `HttpRequestBuffersCallback` `HttpRequest` a `HttpRequestStringCallback` podporují třídu;pracujetepouzestřídouzkóduaplikace.`HttpRequest`

`GetAsync` MetodytřídyumožňujíspustitoperaceHTTPGETapost(`HttpRequest` v uvedeném pořadí). `PostAsync` Tyto metody používají `HttpRequestStringCallback` třídu ke čtení odpovědi serveru jako řetězce. Metody `SendAsync` a`ReadAsync` umožňují streamovat velký obsah v blocích. Tyto metody každý vrací [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) , které reprezentují operaci. Metody `GetAsync` a `PostAsync` tvoří`task<std::wstring>`hodnotu , kde částpředstavujeodpověďserveru.`wstring` Metody `SendAsync` a `ReadAsync` vytváří`task<void>` hodnoty; tyto úlohy jsou dokončeny po dokončení operací odeslání a čtení.

Vzhledem k `IXMLHTTPRequest2` tomu, že rozhraní pracují asynchronně, v tomto příkladu používá [Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) k vytvoření úlohy, která se dokončí po dokončení objektu zpětného volání, nebo zrušení operace stahování. `HttpRequest` Třída vytvoří pokračování na základě úkolů z této úlohy k nastavení konečného výsledku. `HttpRequest` Třída používá pokračování založené na úlohách, aby bylo zajištěno, že úloha pokračování bude spuštěna i v případě, že předchozí úloha vyvolá chybu nebo je zrušena. Další informace o pokračování na základě úkolů najdete v tématu [Task paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md) .

Pro podporu zrušení, `HttpRequest`třídy, `HttpRequestBuffersCallback`a `HttpRequestStringCallback` používají zrušení tokenů. Třídy `HttpRequestBuffersCallback` a`HttpRequestStringCallback` používají metodu [Concurrency:: cancellation_token:: register_callback](reference/cancellation-token-class.md#register_callback) , která umožňuje události dokončení úkolu reagovat na zrušení. Toto zpětné volání zrušení přeruší stahování. Další informace o zrušení naleznete v tématu [zrušení](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

#### <a name="to-define-the-httprequest-class"></a>Definice třídy HttpRequest

1. V hlavní nabídce vyberte **soubor** > **Nový** > **projekt**. 

1. C++ Použijte šablonu **prázdná aplikace (univerzální pro Windows)** k vytvoření prázdného projektu aplikace XAML. Tento příklad pojmenovává projekt `UsingIXMLHTTPRequest2`.

1. Přidejte do projektu hlavičkový soubor s názvem HttpRequest. h a zdrojový soubor s názvem HttpRequest. cpp.

1. V souboru PCH. h přidejte tento kód:

   [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]

1. V HttpRequest. h přidejte tento kód:

   [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]

1. Do HttpRequest. cpp přidejte tento kód:

   [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]

## <a name="using-the-httprequest-class-in-a-uwp-app"></a>Použití třídy HttpRequest v aplikaci UWP

Tato část ukazuje, jak používat `HttpRequest` třídu v aplikaci pro UWP. Aplikace poskytuje vstupní pole, které definuje prostředek adresy URL, a příkazy tlačítek, které provádějí operace GET a POST, a příkaz, který zruší aktuální operaci.

#### <a name="to-use-the-httprequest-class"></a>Použití třídy HttpRequest

1. V souboru MainPage. XAML definujte prvek [StackPanel](/uwp/api/Windows.UI.Xaml.Controls.StackPanel) následujícím způsobem.

   [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]

2. V souboru MainPage. XAML. h přidejte tuto `#include` direktivu:

   [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]

3. V souboru MainPage. XAML. h přidejte tyto `private` členské proměnné `MainPage` do třídy:

   [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]

4. V souboru MainPage. XAML. h deklarujte `private` metodu `ProcessHttpRequest`:

   [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]

5. V souboru MainPage. XAML. cpp přidejte tyto `using` příkazy:

   [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]

6. V souboru MainPage. XAML. cpp implementujte `GetButton_Click`metody `PostButton_Click` `MainPage` , a `CancelButton_Click` třídy.

   [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]

   > [!TIP]
   > Pokud vaše aplikace nevyžaduje podporu pro zrušení, předat [Concurrency:: cancellation_token:: none](reference/cancellation-token-class.md#none) k `HttpRequest::GetAsync` metodám a `HttpRequest::PostAsync` .

1. V souboru MainPage. XAML. cpp implementujte `MainPage::ProcessHttpRequest` metodu.

   [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]

8. Ve vlastnostech projektu v části **linker**, **vstup**zadejte `shcore.lib` , a `msxml6.lib`.

Tady je spuštěná aplikace:

![Běžící aplikace prostředí Windows Runtime](../../parallel/concrt/media/concrt_usingixhr2.png "Běžící aplikace prostředí Windows Runtime")

## <a name="next-steps"></a>Další kroky

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

## <a name="see-also"></a>Viz také:

[Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Asynchronní programování vC++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)<br/>
[Vytváření asynchronních operací v jazyce C++ pro aplikace pro UPW](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)<br/>
[Rychlý start: Připojení pomocí třídy úloh požadavku HTTP XML (](/previous-versions/windows/apps/hh770550\(v=win.10\))IXMLHTTPRequest2)
[(Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)<br/>
[task_completion_event – třída](../../parallel/concrt/reference/task-completion-event-class.md)
