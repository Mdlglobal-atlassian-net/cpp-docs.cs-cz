---
title: Cloudové a webové programování v jazyku Visual C++
ms.date: 11/04/2016
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 33431a8f8660af683ed2e39e10811c22fe2f4fcc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773083"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Cloudové a webové programování v jazyku Visual C++

V jazyce C++ máte několik možností pro připojení k webu a cloudu.

## <a name="cloud-programming-options"></a>Programovací možnosti cloudu

- [Windows Azure Mobile Services](http://www.windowsazure.com/develop/mobile/)

  Poskytuje nativní rozhraní API, které můžete použít v aplikacích pro univerzální platformu Windows (UPW) nebo aplikací klasické pracovní plochy Windows k připojení k mobilním službám Windows Azure. I když většina příkladů na webu v jazyce C#, můžete použít také C++. Další informace najdete v tématu [rychlý start: Přidání mobilních služeb pomocí jazyka C++](https://msdn.microsoft.com/library/windows/apps/dn263181.aspx).

- [Klientská knihovna pro úložiště Microsoft Azure pro jazyk C++](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)

  Klientská knihovna pro úložiště Azure pro jazyk C++ poskytuje komplexní rozhraní API pro práci s Azure storage, včetně mimo jiné následující možnosti:

  - Vytvářet, číst, odstranění a vypsat kontejnery objektů blob, tabulky a fronty.
  - Vytvoření, čtení, odstranění, seznamu a kopírování objektů BLOB a číst a zapisovat rozsahy objektu blob.
  - Vložit, odstranit, nahradit, sloučení a dotazu entity v tabulce Azure.
  - Zařazení do fronty a odstranění z fronty zpráv ve frontě služby Azure.
  - Laxně seznamu kontejnerů, objektů BLOB, tabulky a fronty a laxně dotazování entit

- [Rozhraní API OneDrive](https://dev.onedrive.com/README.htm)

  Rozhraní API OneDrive poskytuje sada služeb HTTP pro připojení aplikace k souborům a složkám v Office 365 a SharePoint serveru 2016.

- [C++ REST SDK (kódový název "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  Poskytuje moderní, napříč platformami, asynchronní rozhraní API pro komunikaci s služeb REST.

  - Provádění volání REST pro všechny HTTP server s integrovanou podporou pro parsování dokumentu JSON a serializace
  - Podporuje OAuth 1 a 2, včetně místních přesměrování naslouchací proces
  - Protokoly Websocket připojení pro vzdálené služby
  - Plně asynchronní úloha rozhraní API založených na PPL, včetně integrovaných fondu vláken

  Podporuje Windows Desktop (7 +), Windows Server (2012 +), univerzální platforma Windows, Linux, OSX, Android a iOS.

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Třída klienta Windows Runtime HTTP modelována ve třídě rozhraní .NET Framework se stejným názvem v oboru názvů System.Web. `HttpClient` plně podporuje asynchronní nahrávání a stahování prostřednictvím protokolu HTTP a kanály filtrů, které umožňují vkládání vlastní obslužné rutiny HTTP do kanálu. Sada Windows SDK obsahuje ukázku filtrů pro měřené sítě, ověřování OAuth a další. Pro aplikace, které se zaměřují jenom na univerzální platformu Windows, doporučujeme použít `Windows::Web:HttpClient` třídy.

- [Rozhraní IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Poskytuje nativní rozhraní modelu COM, můžete použít v aplikacích pro Windows Runtime nebo aplikace klasické pracovní plochy Windows k připojení k Internetu přes protokol HTTP a vydávání příkazů GET, PUT a jiných příkazů protokolu HTTP. Další informace najdete v tématu [názorný postup: Připojení pomocí úloh a žádostí XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](/windows/desktop/WinInet/portal)

  Rozhraní Windows API, které můžete použít v aplikacích klasické pracovní plochy Windows k připojení k Internetu.

## <a name="see-also"></a>Viz také:

[Visual C++](../overview/visual-cpp-in-visual-studio.md) <br/>
[Sítím a webovým službám](/windows/uwp/networking/)
