---
title: 'Návod: Připojení pomocí úloh a žádostí XML HTTP | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 411d52201aad69a94267615cd0a2acbe6376f64d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Návod: Připojení pomocí úloh a žádostí XML HTTP
Tento příklad ukazuje způsob použití [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) a [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) rozhraní společně s úkoly na odesílání žádostí HTTP GET a POST na webovou službu v univerzální platformu Windows (UWP ) aplikace. Propojením požadavku `IXMLHTTPRequest2` s úkoly můžete psát kód, který lze kombinovat s ostatními úkoly. Například můžete úlohu stáhnout jako součást řetězce úloh. Úloha stažení také reagovat, když se zruší pracovní.  
  
> [!TIP]
>  C++ REST SDK můžete použít také k provedení požadavky HTTP z pomocí aplikace C++ UWP aplikace nebo z aplikace C++ pro stolní počítače. Další informace najdete v tématu [C++ REST SDK (kódové označení "Casablanca")](https://github.com/Microsoft/cpprestsdk).  
  
 Další informace o úlohách najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Další informace o tom, jak používat úlohy v aplikaci UWP najdete v tématu [asynchronní programování v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) a [vytváření asynchronních operací v jazyce C++ pro aplikace UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).  
  
 Tento dokument nejprve ukazuje, jak vytvořit `HttpRequest` a jeho podpůrné třídy. Potom ukazuje, jak použít tuto třídu z aplikace pro UPW, který používá C++ a XAML.  
  
 Pro více kompletní příklad, který používá `HttpReader` třída popsané v tomto dokumentu najdete v části [vývoj Bing Maps cestě Optimalizátor, aplikace pro Windows Store v JavaScript a C++](http://msdn.microsoft.com/library/974cf025-de1a-4299-b7dd-c6c7bf0e5d30). Další příklad, který používá `IXMLHTTPRequest2` , ale nemá použití úloh najdete v [rychlý start: připojení pomocí XML požadavek HTTP (IXMLHTTPRequest2)](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35).  
  
> [!TIP]
>  `IXMLHTTPRequest2` a `IXMLHTTPRequest2Callback` jsou rozhraní, které doporučujeme pro použití v aplikaci UWP. Můžete také přizpůsobit tento příklad pro použití v aplikace na ploše.  
  
## <a name="prerequisites"></a>Požadavky  
  
## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>Definice tříd HttpRequest, HttpRequestBuffersCallback a HttpRequestStringCallback  
 Při použití `IXMLHTTPRequest2` rozhraní k vytváření žádostí o web prostřednictvím protokolu HTTP, můžete implementovat `IXMLHTTPRequest2Callback` rozhraní, obdrží odpověď serveru a reagovat na další události. Tento příklad definuje `HttpRequest` třídy za účelem vytvoření webových požadavků a `HttpRequestBuffersCallback` a `HttpRequestStringCallback` třídy ke zpracování odpovědi. `HttpRequestBuffersCallback` a `HttpRequestStringCallback` třídy podpory `HttpRequest` třída; fungovat jenom s `HttpRequest` třídy z kódu aplikace.  
  
 `GetAsync`, `PostAsync` Metody `HttpRequest` třída umožňují spouštění operace HTTP GET a POST, v uvedeném pořadí. Tyto metody používat `HttpRequestStringCallback` třídy ke čtení odpovědi serveru jako řetězec. `SendAsync` a `ReadAsync` metody umožňují velké obsah datového proudu bloků. Tyto metody každý vrací [concurrency::task](../../parallel/concrt/reference/task-class.md) představující operaci. `GetAsync` a `PostAsync` metody vracet `task<std::wstring>` hodnotu, kde `wstring` část představuje odpověď serveru. `SendAsync` a `ReadAsync` metody vracet `task<void>` hodnoty; tyto úlohy dokončení po dokončení operace odesílání a pro čtení.  
  
 Protože `IXMLHTTPRequest2` rozhraní fungovat asynchronně, tento příklad používá [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) k vytvoření úlohy, která je dokončena po dokončení zpětné volání objektu nebo stažení operaci zruší. `HttpRequest` Třída vytvoří na základě úkolů pokračování z této úlohy můžete nastavit konečný výsledek. `HttpRequest` Třída používá pokračování založený na úlohách zajistit, že tato pokračování úloha se spustí i v případě, že předchozí úloha vytvoří chybu nebo je zrušena. Další informace o pokračování založený na úlohách najdete v tématu [funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
 Pro podporu zrušení, `HttpRequest`, `HttpRequestBuffersCallback`, a `HttpRequestStringCallback` třídy použijte zrušení tokenů. `HttpRequestBuffersCallback` a `HttpRequestStringCallback` třídy použití [concurrency::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) způsob povolení události dokončení úlohy reagovat na zrušení. Zpětné volání toto zrušení zruší stahování. Další informace o zrušení najdete v tématu [zrušení](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
#### <a name="to-define-the-httprequest-class"></a>Definice třídy HttpRequest  
  
1.  Pomocí Visual C++ **prázdná aplikace (XAML)** šablony k vytvoření prázdného projektu aplikace XAML. Tento příklad názvy projektu `UsingIXMLHTTPRequest2`.  
  
2.  Záhlaví souboru, který je pojmenován HttpRequest.h a zdrojový soubor, který je pojmenován HttpRequest.cpp, přidejte do projektu.  
  
3.  V pch.h přidejte tento kód:  
  
     [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]  
  
4.  V HttpRequest.h přidejte tento kód:  
  
     [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]  
  
5.  V HttpRequest.cpp přidejte tento kód:  
  
     [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]  
  
## <a name="using-the-httprequest-class-in-a-uwp-app"></a>Používání třídy požadavku HTTP v aplikaci UWP  
 V této části ukazuje, jak používat `HttpRequest` třídy v aplikaci UWP. Aplikace obsahuje vstupní pole definující prostředku adresy URL, a tlačítko příkazy, které provádějí operace GET a POST a tlačítko příkaz, který zruší aktuální operace.  
  
#### <a name="to-use-the-httprequest-class"></a>Použití třídy HttpRequest  
  
1.  V MainPage.xaml, zadejte [StackPanel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx) element následujícím způsobem.  
  
     [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]  
  
2.  V MainPage.xaml.h, přidejte tuto `#include` – direktiva:  
  
     [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]  
  
3.  V MainPage.xaml.h, přidejte tyto `private` členské proměnné `MainPage` třídy:  
  
     [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]  
  
4.  V MainPage.xaml.h, deklarovat `private` metoda `ProcessHttpRequest`:  
  
     [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]  
  
5.  V MainPage.xaml.cpp, přidejte tyto `using` příkazy:  
  
     [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]  
  
6.  V MainPage.xaml.cpp, implementovat `GetButton_Click`, `PostButton_Click`, a `CancelButton_Click` metody `MainPage` třídy.  
  
     [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]  
  
    > [!TIP]


    >  Pokud aplikace nevyžaduje podporu pro zrušení, předat [concurrency::cancellation_token:: žádné](reference/cancellation-token-class.md#none) k `HttpRequest::GetAsync` a `HttpRequest::PostAsync` metody.  


  
7.  V MainPage.xaml.cpp, implementovat `MainPage::ProcessHttpRequest` metoda.  
  
     [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]  
  
8.  Ve vlastnostech projektu v části **Linkeru**, **vstup**, zadejte `shcore.lib` a `msxml6.lib`.  
  
 Tady je spuštěné aplikaci:  
  
 ![Spuštěné aplikaci prostředí Windows Runtime](../../parallel/concrt/media/concrt_usingixhr2.png "concrt_usingixhr2")  
  
## <a name="next-steps"></a>Další kroky  
 [Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)  
  
## <a name="see-also"></a>Viz také  
 [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)   
 [Asynchronní programování v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)   
 [Vytváření asynchronních operací v jazyce C++ pro aplikace UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)   
 [Rychlý úvod: Připojení pomocí XML požadavek HTTP (IXMLHTTPRequest2)](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)   
 [Task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)   
 [task_completion_event – třída](../../parallel/concrt/reference/task-completion-event-class.md)
