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
ms.openlocfilehash: b205599ed3bf33e84516120b1855482797b86c9b
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924906"
---
# <a name="application-design-choices"></a>Volby při návrhu aplikací

Tento článek popisuje některé problémy s návrhem, které je potřeba vzít v úvahu při programování pro Internet.

Témata, která jsou popsaná v tomto článku, zahrnují:

- [Intranet Versus Internet](#_core_intranet_versus_internet)

- [Klientská nebo serverová aplikace](#_core_client_or_server_application)

- [Webová stránka](#_core_the_web_page)

- [Prohlížeč nebo samostatná aplikace](#_core_browser_or_standalone)

- [COM na internetu](#_core_com_on_the_internet)

- [Služby stahování klientských dat](#_core_client_data_download_services)

Pokud jste připraveni začít psát program nyní, přečtěte si téma [psaní aplikací MFC](../mfc/writing-mfc-applications.md).

##  <a name="_core_intranet_versus_internet"></a>Intranet a Internet

Řada aplikací běží na internetu a je přístupná pro kohokoli s prohlížečem a přístupem k Internetu. Firmy také implementují intranetové sítě, které jsou sítěmi v podnikové síti pomocí protokolů TCP/IP a webových prohlížečů. Intranetové služby nabízejí snadno aktualizovatelný, centrální zdroj pro informace pro celé firmy. Dají se použít k upgradu softwaru, k doručování a tabulating průzkumům, zákaznické podpoře a k doručování informací. Následující tabulka porovnává funkce Internetu a intranetu.

|Internet|Vaší|
|--------------|--------------|
|Nízká šířka pásma|Velká šířka pásma|
|Menší zabezpečení dat a systémů|Řízený přístup k datům a systémům|
|Minimální kontrola obsahu|Vysoká kontrola obsahu|

##  <a name="_core_client_or_server_application"></a>Klientská nebo serverová aplikace

Vaše aplikace se může spouštět na klientském počítači nebo na serveru. Vaše aplikace může být uložená i na serveru a pak se stáhne přes Internet a spustí se na klientském počítači. Třídy WinInet knihovny MFC jsou používány pro klientské aplikace ke stahování souborů. Třídy MFC a asynchronní monikery se používají ke stahování souborů a vlastností ovládacích prvků. Třídy pro ovládací prvky ActiveX a aktivní dokumenty se používají pro klientské aplikace a pro aplikace stažené ze serveru pro spuštění v klientovi.

##  <a name="_core_the_web_page"></a>Webová stránka: HTML, aktivní dokumenty, ovládací prvky ActiveX

Microsoft nabízí několik způsobů poskytování obsahu na webové stránce. Webové stránky mohou používat standardní rozšíření HTML nebo HTML, například značku objektu, k poskytnutí dynamického obsahu, jako jsou například ovládací prvky ActiveX.

Webové prohlížeče obvykle zobrazují stránky HTML. Aktivní dokumenty mohou také zobrazit data vaší aplikace v jednoduchém rozhraní typu Point-to-and-click v prohlížeči s podporou modelu COM. Váš aktivní dokumentový server může zobrazit dokument, celý snímek v celé klientské oblasti s vlastními nabídkami a panely nástrojů.

Ovládací prvky ActiveX, které zapisujete, se dají ze serveru stáhnout asynchronně a zobrazují se na webové stránce. Před odesláním informací na server můžete použít skriptovací jazyk, například VBScript, a provést ověřování na straně klienta.

##  <a name="_core_browser_or_standalone"></a>Prohlížeč nebo samostatná aplikace

Můžete psát ovládací prvky ActiveX, které jsou vloženy na stránce HTML a na serverech aktivních dokumentů, které se zobrazují v prohlížeči. Můžete psát stránky HTML, které obsahují tlačítko pro odeslání žádosti o spuštění aplikace ISAPI na webovém serveru. Můžete napsat samostatnou aplikaci, která pomocí internetových protokolů stahuje soubory a zobrazuje informace pro uživatele, a to bez nutnosti použití aplikace v prohlížeči.

##  <a name="_core_com_on_the_internet"></a>COM na internetu

Ovládací prvky ActiveX, aktivní dokumenty a asynchronní monikery využívají technologii COM (Component Object Model).

Ovládací prvky ActiveX poskytují dynamický obsah pro dokumenty a stránky na internetových serverech. Pomocí modelu COM můžete vytvářet ovládací prvky ActiveX a dokumenty založené na plném snímku pomocí aktivních dokumentů.

Asynchronní monikery poskytují funkce, které umožňují ovládacímu prvku dobře fungovat v internetovém prostředí, včetně přírůstkových nebo progresivních způsobů, jak stahovat data. Ovládací prvky musí také dobře fungovat s dalšími ovládacími prvky, které mohou také asynchronně načíst data ve stejnou dobu.

##  <a name="_core_client_data_download_services"></a>Služby stahování klientských dat

Dvě sady rozhraní API, které vám pomůžou přenést data do vašeho klienta, jsou rozhraní WinInet a asynchronní monikery. Pokud máte velké soubory. gif a. avi a ovládací prvky ActiveX na stránce HTML, můžete zvýšit rychlost odezvy pro uživatele, a to buď pomocí asynchronních monikerů nebo asynchronního použití rozhraní WinInet.

Běžným úkolem na internetu je přenos dat. Pokud již používáte aktivní technologii (například pokud máte ovládací prvek ActiveX), můžete použít asynchronní monikery pro průběžné vykreslování dat při jejich stahování. Pomocí rozhraní WinInet můžete přenášet data pomocí běžných internetových protokolů, jako jsou HTTP, FTP a Gopher. Obě metody poskytují nezávislost protokolu a poskytují abstraktní vrstvu pro použití rozhraní WinSock a protokolu TCP/IP. [Rozhraní Winsock](../mfc/windows-sockets-in-mfc.md) můžete dál používat přímo.

Následující tabulka shrnuje několik způsobů použití knihovny MFC k přenosu dat napříč internetem.

|Použít tento protokol|Za těchto podmínek|Použití těchto tříd|
|-----------------------|----------------------------|-------------------------|
|[Stahování z Internetu pomocí asynchronních monikerů](../mfc/asynchronous-monikers-on-the-internet.md)|Pro asynchronní přenos pomocí modelu COM, ovládacích prvků ActiveX a libovolného protokolu sítě Internet.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Pro internetové protokoly pro HTTP, FTP a Gopher. Data je možné přenést synchronně nebo asynchronně a ukládají se do mezipaměti v rámci systému.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)a spousta dalších.|
|[WinSock](../mfc/windows-sockets-in-mfc.md)|Pro maximální efektivitu a kontrolu. Vyžaduje porozumění soketům a protokolům TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Viz také:

[Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Asynchronní monikery na internetu](../mfc/asynchronous-monikers-on-the-internet.md)
