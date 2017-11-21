---
title: "Návod: Připojení pomocí úloh a žádostí XML HTTP | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- connecting to web services, Windows Store apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1f309673b5f0362657434bf3160d1062fdefe881
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Návod: Připojení pomocí úloh a žádostí XML HTTP
Tento příklad ukazuje způsob použití [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) a [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) rozhraní společně s úkoly na odesílání žádostí HTTP GET a POST na webovou službu v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Propojením požadavku `IXMLHTTPRequest2` s úkoly můžete psát kód, který lze kombinovat s ostatními úkoly. Například můžete úlohu stáhnout jako součást řetězce úloh. Úloha stažení také reagovat, když se zruší pracovní.  
  
> [!TIP]
>  K provádění požadavků protokolu HTTP z aplikace [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] pomocí aplikace jazyka C++ nebo z aplikace pracovní plochy jazyka C++ lze také použít sadu C++ REST SDK. Další informace najdete v tématu [C++ REST SDK (kódové označení "Casablanca")](https://github.com/Microsoft/cpprestsdk).  
  
 Další informace o úlohách najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Další informace o tom, jak používat úlohy v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace, najdete v části [asynchronní programování v jazyce C++](http://msdn.microsoft.com/en-us/512700b7-7863-44cc-93a2-366938052f31) a [vytváření asynchronních operací v C++ pro aplikace Windows Store](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).  
  
 Tento dokument nejprve ukazuje, jak vytvořit `HttpRequest` a jeho podpůrné třídy. Potom ukazuje, jak použít tuto třídu z [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikaci, která používá C++ a XAML.  
  
 Pro více kompletní příklad, který používá `HttpReader` třída popsané v tomto dokumentu najdete v části [vývoj Bing Maps cestě Optimalizátor, aplikace pro Windows Store v JavaScript a C++](http://msdn.microsoft.com/library/974cf025-de1a-4299-b7dd-c6c7bf0e5d30). Další příklad, který používá `IXMLHTTPRequest2` , ale nemá použití úloh najdete v [rychlý start: připojení pomocí XML požadavek HTTP (IXMLHTTPRequest2)](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35).  
  
> [!TIP]
>  `IXMLHTTPRequest2`a `IXMLHTTPRequest2Callback` jsou rozhraní, které doporučujeme pro použití v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Můžete také přizpůsobit tento příklad pro použití v aplikace na ploše.  
  
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
  
## <a name="using-the-httprequest-class-in-a-includewin8appnamelongbuildincludeswin8appnamelongmdmd-app"></a>Používání třídy požadavku HTTP v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace  
 V této části ukazuje, jak používat `HttpRequest` třídy v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Aplikace obsahuje vstupní pole definující prostředku adresy URL, a tlačítko příkazy, které provádějí operace GET a POST a tlačítko příkaz, který zruší aktuální operace.  
  
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
  
 ![Spuštěné aplikace pro Windows Store](../../parallel/concrt/media/concrt_usingixhr2.png "concrt_usingixhr2")  
  
## <a name="next-steps"></a>Další kroky  
 [Návody k Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)  
  
## <a name="see-also"></a>Viz také  
 [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)   
 [Asynchronní programování v jazyce C++](http://msdn.microsoft.com/en-us/512700b7-7863-44cc-93a2-366938052f31)   
 [Vytváření asynchronních operací v jazyce C++ pro aplikace Windows Store](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)   
 [Rychlý úvod: Připojení pomocí XML požadavek HTTP (IXMLHTTPRequest2)](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)   
 [Task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)   
 [task_completion_event – třída](../../parallel/concrt/reference/task-completion-event-class.md)
