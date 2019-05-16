---
title: Cloudové a webové programování v jazyku Visual C++
ms.date: 05/14/2019
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 677e9da18e8d171f523994d21bfbd0411270e3c8
ms.sourcegitcommit: bc1b14f29a02685f97c7ef5c098d16db6eaf369f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2019
ms.locfileid: "65790363"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Cloudové a webové programování v jazyku Visual C++

V jazyce C++ máte několik možností pro připojení k webu a cloudu.

## <a name="microsoft-azure-sdks-and-rest-services"></a>Služby Microsoft Azure SDK a REST

- [Klientská knihovna pro úložiště Microsoft Azure pro jazyk C++](https://azure.github.io/azure-storage-cpp/)

  Klientská knihovna pro úložiště Azure pro jazyk C++ poskytuje komplexní rozhraní API pro práci s Azure storage, včetně mimo jiné následující možnosti:

  - Vytvářet, číst, odstranění a vypsat kontejnery objektů blob, tabulky a fronty.
  - Vytvoření, čtení, odstranění, seznamu a kopírování objektů BLOB a číst a zapisovat rozsahy objektu blob.
  - Vložit, odstranit, nahradit, sloučení a dotazu entity v tabulce Azure.
  - Zařazení do fronty a odstranění z fronty zpráv ve frontě služby Azure.
  - Laxně seznamu kontejnerů, objektů BLOB, tabulky a fronty a laxně dotazování entit

- ANSI C99 [sady SDK služby Azure IoT Hub](/azure/iot-hub/iot-hub-devguide-sdks) Internet of Things povolit IoT aplikace, které poběží v zařízení nebo na back-endu.

- [OneDrive a SharePoint v Microsoft Graphu](https://dev.onedrive.com/README.htm)

  Rozhraní API OneDrive poskytuje sada služeb HTTP pro připojení aplikace k souborům a složkám v Office 365 a SharePoint serveru 2016.

## <a name="windows-and-cross-platform-networking-apis"></a>Windows a sítě multiplatformní rozhraní API

- [C++REST SDK (kódový název "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  Poskytuje moderní, napříč platformami, asynchronní rozhraní API pro komunikaci s služeb REST.

  - Provádění volání REST pro všechny HTTP server s integrovanou podporou pro parsování dokumentu JSON a serializace
  - Podporuje OAuth 1 a 2, včetně místních přesměrování naslouchací proces
  - Protokoly Websocket připojení pro vzdálené služby
  - Plně asynchronní úloha rozhraní API založených na PPL, včetně integrovaných vlákna fondu

  Podporuje Windows Desktop (7 +), Windows Server (2012 +), univerzální platforma Windows, Linux, OSX, Android a iOS.

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Třída klienta Windows Runtime HTTP modelována ve třídě rozhraní .NET Framework se stejným názvem v oboru názvů System.Web. `HttpClient` plně podporuje asynchronní nahrávání a stahování prostřednictvím protokolu HTTP a kanály filtrů, které umožňují vkládání vlastní obslužné rutiny HTTP do kanálu. Sada Windows SDK obsahuje ukázku filtrů pro měřené sítě, ověřování OAuth a další. Pro aplikace, které se zaměřují jenom na univerzální platformu Windows, doporučujeme použít `Windows::Web:HttpClient` třídy.

- [Rozhraní IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Poskytuje nativní rozhraní modelu COM, můžete použít v aplikacích pro Windows Runtime nebo aplikace klasické pracovní plochy Windows k připojení k Internetu přes protokol HTTP a vydávání příkazů GET, PUT a jiných příkazů protokolu HTTP. Další informace najdete v tématu [názorný postup: Připojení pomocí úloh a žádostí XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](/windows/desktop/WinInet/portal)

  Rozhraní Windows API, které můžete použít v aplikacích klasické pracovní plochy Windows k připojení k Internetu.

## <a name="see-also"></a>Viz také:

[C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md) <br/>
[Středisko pro vývojáře v C++ a C Microsoft Azure](https://azure.microsoft.com/develop/cpp/) <br/>
[Sítím a webovým službám (UPW)](/windows/uwp/networking/)
