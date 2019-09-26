---
title: Cloudové a webové programování v jazyku Visual C++
ms.date: 05/14/2019
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.topic: overview
ms.openlocfilehash: 4e50557733d474d68b8e503d00b28b2ae8cb7f09
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274647"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Cloudové a webové programování v jazyku Visual C++

V C++nástroji máte několik možností, jak se připojit k webu a ke cloudu.

## <a name="microsoft-azure-sdks-and-rest-services"></a>Microsoft Azure sady SDK a služby REST

- [Klientská knihovna Microsoft Azure Storage proC++](https://azure.github.io/azure-storage-cpp/)

  Klientská knihovna Azure Storage pro C++ poskytuje komplexní rozhraní API pro práci s úložištěm Azure, včetně neomezeného na tyto možnosti:

  - Vytváření, čtení, odstraňování a výpis kontejnerů objektů blob, tabulek a front.
  - Vytváření, čtení, odstraňování, výpisů a kopírování objektů BLOB plus rozsahy objektů BLOB pro čtení a zápis.
  - Vložení, odstranění, nahrazení, sloučení a dotazování entit v tabulce Azure.
  - Zařazování zpráv do fronty a jejich vyřazení z fronty Azure.
  - Laxně vytvářená seznam kontejnerů, objektů blob, tabulek a front a entit dotazů laxně vytvářená

- Sady SDK C99 pro [Azure IoT Hub](/azure/iot-hub/iot-hub-devguide-sdks) pro Internet věcí umožňují aplikacím IoT běžet na zařízení nebo na back-endu.

- [OneDrive a SharePoint v Microsoft Graph](https://dev.onedrive.com/README.htm)

  Rozhraní API OneDrivu poskytuje sadu služeb HTTP pro připojení aplikace k souborům a složkám v Office 365 a SharePoint serveru 2016.

## <a name="windows-and-cross-platform-networking-apis"></a>Síťová rozhraní API pro Windows a více platforem

- [C++REST SDK (název kódu "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  Poskytuje moderní rozhraní API pro více platforem pro interakci se službami REST.

  - Provádění volání REST proti jakémukoli HTTP serveru s integrovanou podporou pro analýzu a serializaci dokumentů JSON
  - Podporuje OAuth 1 a 2, včetně místního naslouchacího procesu přesměrování.
  - Vytváření připojení pomocí protokolu WebSocket ke vzdáleným službám
  - Plně asynchronní rozhraní API pro úlohy založené na PPL, včetně integrovaného fondu vláken

  Podporuje Desktop Windows (7 +), Windows Server (2012 +), Univerzální platforma Windows, Linux, OSX, Android a iOS.

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Prostředí Windows Runtime Třída klienta HTTP modelovaná na .NET Framework třídy se stejným názvem v oboru názvů System. Web. `HttpClient`plně podporuje asynchronní nahrávání a stahování přes protokol HTTP a filtry kanálu, které umožňují vkládání vlastních obslužných rutin HTTP do kanálu. Windows SDK obsahuje vzorové filtry pro účtované sítě, ověřování OAuth a další. Pro aplikace, které cílí jenom na Univerzální platforma Windows, doporučujeme použít `Windows::Web:HttpClient` třídu.

- [Rozhraní IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Poskytuje nativní rozhraní modelu COM, které můžete použít v aplikacích prostředí Windows Runtime aplikace nebo Windows Desktop pro připojení k internetu přes HTTP a vydávání příkazů GET, PUT a dalších HTTP. Další informace najdete v tématu [Návod: Připojení pomocí úloh a požadavků](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)XML http.

- [Windows Internet (WinInet)](/windows/win32/WinInet/portal)

  Rozhraní Windows API, které můžete použít v aplikacích klasické pracovní plochy pro připojení k Internetu.

## <a name="see-also"></a>Viz také:

[C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md) <br/>
[Microsoft Azure C a C++ Developer Center](https://azure.microsoft.com/develop/cpp/) <br/>
[Sítě a webové služby (UWP)](/windows/uwp/networking/)
