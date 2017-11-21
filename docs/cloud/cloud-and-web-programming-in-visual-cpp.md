---
title: "Cloudové a webové programování v jazyce Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-azure
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
caps.latest.revision: "13"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 4763dd9048f1d43bde1bd9b67126f85533f6f0c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Cloudové a webové programování v jazyku Visual C++
V jazyce C++ máte několik možností pro připojení k webu a cloudem.  
  
 [Windows Azure Mobile Services](http://www.windowsazure.com/develop/mobile/)  
 Poskytuje nativní rozhraní API, které můžete použít v aplikacích pro Windows Store nebo desktopových aplikací systému Windows pro připojení k systému Windows Azure Mobile Services. I když většina příkladů na webu jsou v jazyce C#, můžete taky C++. Další informace najdete v tématu [rychlé spuštění: Přidání mobilní služby pomocí C++](http://msdn.microsoft.com/library/windows/apps/dn263181.aspx).  

 [Klientská knihovna pro úložiště Microsoft Azure pro jazyk C++](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)  
 Klientská knihovna pro úložiště Azure pro jazyk C++ poskytuje komplexní rozhraní API pro práci s Azure storage, včetně mimo jiné následující možnosti:

- Vytváření, čtení, odstranit a seznam kontejnery objektů blob, tabulek a front.
- Vytváření, čtení, odstranit, seznamu a zkopírujte objekty BLOB plus čtení a zápisu objektů blob rozsahy.
- Vložení, odstranění, nahraďte, sloučení a entity dotazu v Azure table.
- Zařazování a vyřazení z fronty zpráv do fronty Azure.
- Líné seznamu kontejnerů, objektů BLOB, tabulek a front a líné dotaz entity

[OneDrive rozhraní API](https://dev.onedrive.com/README.htm)  
 Rozhraní API OneDrive poskytuje sadu služeb HTTP k připojení aplikace k souborům a složkám v Office 365 a SharePoint Server 2016.

[C++ REST SDK (kódové označení "Casablanca")](https://github.com/Microsoft/cpprestsdk)  
Poskytuje rozhraní API moderní, a platformy, asynchronní pro interakci s služby REST.

-   Provádění volání REST pro libovolný server HTTP se s integrovanou podporu pro analýzy dokumentu JSON a serializace
-   Podporuje OAuth 1 a 2, včetně naslouchací proces místní přesměrování
-   Technologie Websockets připojovat proti vzdálené
-   Plně asynchronní úlohu rozhraní API podle PPL, včetně předdefinovaných fondu

Podporuje Windows Desktop (7 +), Windows Server (2012 +), univerzální platformu Windows, Linux, OSX, Android a iOS. 
  
[Windows::web::http::HttpClient](https://msdn.microsoft.com/en-us/library/windows/apps/windows.web.http.httpclient.aspx)  
 Třídy klienta Windows Runtime HTTP modelován v rozhraní .NET Framework – třída v oboru názvů System.Web se stejným názvem. `HttpClient`plně podporuje asynchronní nahrávání a stahování prostřednictvím protokolu HTTP a kanál filtry, které vložení vlastní obslužné rutiny HTTP do kanálu. Sada Windows SDK obsahuje ukázkové filtry pro monitorovaných sítí, ověřování OAuth a další. U aplikací, které se zaměřují jen univerzální platformu Windows, doporučujeme použít `Windows::Web:HttpClient` třídy. 
  
[IXMLHTTPRequest2 rozhraní](http://msdn.microsoft.com/library/windows/apps/hh831151.aspx)  
 Poskytuje nativní rozhraní modelu COM, můžete použít v aplikacích pro Windows Store nebo desktopových aplikací systému Windows pro připojení k Internetu prostřednictvím protokolu HTTP a problém GET, PUT a další příkazy HTTP. Další informace najdete v tématu [návod: připojení pomocí úloh a žádostí XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).  
  
[Windows Internet (WinInet)](http://msdn.microsoft.com/library/windows/desktop/aa385331\(v=vs.85\).aspx)  
 Rozhraní API systému Windows, který můžete použít v aplikacích klasické pracovní plochy Windows pro připojení k Internetu.  
  
## <a name="see-also"></a>Viz také  
 [Visual C++](../visual-cpp-in-visual-studio.md)   
 [Připojení k síti a webové služby (aplikace pro Windows Store pomocí jazyka C# / VB/C++ a XAML)](http://msdn.microsoft.com/library/windows/apps/br229573.aspx)