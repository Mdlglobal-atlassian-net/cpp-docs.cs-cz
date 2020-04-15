---
title: Volby při návrhu aplikací
ms.date: 09/12/2019
helpviewer_keywords:
- design
- application design [MFC], design goals
- application design [MFC], Internet applications
- Internet applications [MFC], designing applications
- Internet [MFC], vs. intranets
- applications [MFC], Internet
- server applications [MFC], vs. client applications on Internet
- client applications [MFC], vs. server applications on Internet
ms.assetid: 9b96172c-b4d4-4c69-bfb2-226ce0de6d08
ms.openlocfilehash: 89f3e5c108de1cf7b3b73a33a08e2c50b1333c92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374633"
---
# <a name="application-design-choices"></a>Volby při návrhu aplikací

Tento článek popisuje některé problémy návrhu, které je třeba zvážit při programování pro Internet.

Témata uvedená v tomto článku zahrnují:

- [Intranet Versus Internet](#_core_intranet_versus_internet)

- [Klientská nebo serverová aplikace](#_core_client_or_server_application)

- [Webová stránka](#_core_the_web_page)

- [Prohlížeč nebo samostatná aplikace](#_core_browser_or_standalone)

- [COM na internetu](#_core_com_on_the_internet)

- [Služby stahování klientských dat](#_core_client_data_download_services)

Pokud jste připraveni začít psát program nyní, naleznete [v tématu zápis aplikací knihovny MFC](../mfc/writing-mfc-applications.md).

## <a name="intranet-versus-internet"></a><a name="_core_intranet_versus_internet"></a>Intranet Versus Internet

Mnoho aplikací běží na Internetu a jsou přístupné každému, kdo má prohlížeč a přístup k Internetu. Firmy také implementují intranety, což jsou celopodnikové sítě používající protokoly TCP/IP a webové prohlížeče. Intranety nabízejí snadno rozšiřitelný centrální zdroj informací pro celou společnost. Mohou být použity pro upgrade softwaru, pro poskytování a vytváření tabulating průzkumy, pro zákaznickou podporu, a pro poskytování informací. Následující tabulka porovnává funkce Internetu a intranetů.

|Internet|Intranet|
|--------------|--------------|
|Nízká šířka pásma|Vysoká šířka pásma|
|Snížená bezpečnost dat a systémů|Kontrolovaný přístup k datům a systémům|
|Minimální kontrola obsahu|Vysoká kontrola obsahu|

## <a name="client-or-server-application"></a><a name="_core_client_or_server_application"></a>Klientská nebo serverová aplikace

Aplikace může být spuštěna v klientském počítači nebo v počítači serveru. Aplikace může být také uložena na serveru a poté stažena přes Internet a spuštěna v klientském počítači. Třídy WinInet knihovny MFC se používají pro klientské aplikace ke stahování souborů. Knihovny MFC a asynchronní zástupné třídy se používají ke stažení souborů a vlastností ovládacího prvku. Třídy pro ovládací prvky ActiveX a aktivní dokumenty se používají pro klientské aplikace a pro aplikace, které jsou staženy ze serveru ke spuštění na klienta.

## <a name="the-web-page-html-active-documents-activex-controls"></a><a name="_core_the_web_page"></a>Webová stránka: HTML, aktivní dokumenty, ovládací prvky ActiveX

Společnost Microsoft nabízí několik způsobů poskytování obsahu na webové stránce. Webové stránky mohou používat standardní rozšíření HTML nebo HTML, například značku objektu, k poskytování dynamického obsahu, například ovládacích prvků ActiveX.

Webové prohlížeče obvykle zobrazují stránky HTML. Aktivní dokumenty mohou také zobrazit data aplikace v jednoduchém rozhraní point-and-click prohlížeče s podporou com. Server Active Document může zobrazit dokument, celý rámec v celé klientské oblasti, s vlastními nabídkami a panely nástrojů.

Ovládací prvky ActiveX, které píšete, lze asynchronně stáhnout ze serveru a zobrazit na webové stránce. Skriptovací jazyk, například VBScript, můžete před odesláním informací na server použít skriptovací jazyk, například VBScript.

## <a name="browser-or-stand-alone-application"></a><a name="_core_browser_or_standalone"></a>Prohlížeč nebo samostatná aplikace

Můžete psát ovládací prvky ActiveX, které jsou vloženy na stránce HTML a aktivní servery dokumentů, které jsou zobrazeny v prohlížeči. Můžete napsat stránky HTML, které obsahují tlačítko pro odeslání požadavku na spuštění aplikace ISAPI na webovém serveru. Můžete napsat samostatnou aplikaci, která používá internetové protokoly ke stahování souborů a zobrazení informací uživateli, aniž byste museli používat aplikaci prohlížeče.

## <a name="com-on-the-internet"></a><a name="_core_com_on_the_internet"></a>COM na internetu

Ovládací prvky ActiveX, aktivní dokumenty a asynchronní zástupné názvy používají technologie COM (Component Object Model).

Ovládací prvky ActiveX poskytují dynamický obsah dokumentům a stránkám na internetových serverech. Pomocí modelu COM můžete vytvářet ovládací prvky ActiveX a dokumenty s plným rámcem pomocí aktivních dokumentů.

Asynchronní zástupné názvy poskytují funkce umožňující ovládacímu prvku dobře fungovat v prostředí Internetu, včetně přírůstkových nebo progresivních prostředků pro stahování dat. Ovládací prvky musí také dobře pracovat s jinými ovládacími prvky, které mohou být také načítání jejich dat asynchronně současně.

## <a name="client-data-download-services"></a><a name="_core_client_data_download_services"></a>Služby stahování klientských dat

Dvě sady rozhraní API, které vám pomohou přenášet data do klienta jsou WinInet a asynchronní zástupné názvy. Pokud máte velké soubory GIF a AVI a ovládací prvky ActiveX na stránce HTML, můžete zvýšit odezvu na uživatele stažením asynchronně, buď pomocí asynchronních zástupných názvů nebo pomocí WinInet asynchronně.

Běžnou úlohou na Internetu je přenos dat. Pokud již používáte technologii Active (například pokud máte ovládací prvek ActiveX), můžete pomocí asynchronních zástupných názvů postupně vykreslovat data při stahování. WinInet můžete použít k přenosu dat pomocí běžných internetových protokolů, jako je HTTP, FTP a gopher. Obě metody poskytují nezávislost protokolu a poskytují abstraktní vrstvu pro použití winsock a tcp/ip. Stále můžete používat [WinSock](../mfc/windows-sockets-in-mfc.md) přímo.

Následující tabulka shrnuje několik způsobů, jak pomocí knihovny MFC k přenosu dat přes Internet.

|Použít tento protokol|Za těchto podmínek|Použití těchto tříd|
|-----------------------|----------------------------|-------------------------|
|[Stahování z Internetu pomocí asynchronních názvů](../mfc/asynchronous-monikers-on-the-internet.md)|Pro asynchronní přenos pomocí com, Ovládací prvky ActiveX a libovolný internetový protokol.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Pro internetové protokoly pro protokoly HTTP, FTP a gopher. Data mohou být přenášena synchronně nebo asynchronně a jsou uložena v mezipaměti celého systému.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)a mnoho dalších.|
|[Winsock](../mfc/windows-sockets-in-mfc.md)|Pro maximální efektivitu a kontrolu. Vyžaduje pochopení soketů a protokolů TCP/IP.|[Csocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Viz také

[Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Asynchronní monikery na Internetu](../mfc/asynchronous-monikers-on-the-internet.md)
