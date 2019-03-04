---
title: Volby při návrhu aplikací
ms.date: 11/04/2016
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
ms.openlocfilehash: cdb294e4ab808a7e4cbcec457f6e744eff9f12cb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302806"
---
# <a name="application-design-choices"></a>Volby při návrhu aplikací

Tento článek popisuje některé faktory vzít v úvahu při programování pro Internet.

V tomto článku probíraná témata zahrnují:

- [Intranet Versus Internet](#_core_intranet_versus_internet)

- [Klientské nebo serverové aplikace](#_core_client_or_server_application)

- [](#_core_the_web_page)

- [Prohlížeč nebo samostatné aplikace](#_core_browser_or_standalone)

- [COM na Internetu](#_core_com_on_the_internet)

- [Stáhnout Data klientů služby](#_core_client_data_download_services)

Pokud jste připravení začít psát aplikace nyní naleznete v tématu [psaní aplikací MFC](../mfc/writing-mfc-applications.md).

##  <a name="_core_intranet_versus_internet"></a> Intranet Versus Internet

Mnoho aplikací spusťte na Internetu a jsou přístupné všem uživatelům s prohlížeči a přístup k Internetu. Firmám také implementují sítě intranet, které jsou pořádaného microsoftem sítě pomocí protokolů TCP/IP a webové prohlížeče. Intranety nabízejí zdroj je možné snadno upgradovat, centrální informace pořádaného microsoftem. Můžete použít pro upgrade softwaru, týkající se doručování a sestavování tabulek zjišťování, pro zákaznickou podporu a pro doručení informací. Následující tabulka obsahuje porovnání funkcí z Internetu a intranetu.

|Internet|Intranet|
|--------------|--------------|
|S malou šířkou pásma|Velká šířka pásma|
|Snížení zabezpečení dat a systémy|Řízený přístup k datům a systémům|
|Minimální ovládací prvek obsahu|Vysoká ovládacího prvku obsahu|

##  <a name="_core_client_or_server_application"></a> Klientské nebo serverové aplikace

Aplikace může být v klientském počítači nebo na počítači serveru. Vaše aplikace může také uloženy na serveru a potom stažení přes Internet a spuštění v klientském počítači. Tříd WinInet knihovny MFC se používají pro klientské aplikace ke stažení souborů. Asynchronní zástupný název třídy knihovny MFC a slouží k stažení souborů a vlastnosti ovládacího prvku. Třídy pro ovládací prvky ActiveX a aktivních dokumentů se používají pro klientské aplikace a aplikace, které jsou staženy ze serveru pro spuštění v klientském počítači.

##  <a name="_core_the_web_page"></a> Webové stránky: Ovládací prvky ActiveX HTML, aktivní dokumenty

Společnost Microsoft nabízí několik způsobů, jak zajistit obsah na webové stránce. Webové stránky můžete použít standardní HTML nebo HTML rozšíření, jako je například objekt značky poskytují dynamický obsah, jako je například ovládací prvky ActiveX.

Webové prohlížeče obvykle zobrazení stránek HTML. Aktivní dokumenty lze také zobrazit data vaší aplikace v jednoduché rozhraní ukázat a kliknout podporou modelu COM prohlížeče. Váš server aktivní dokument můžete zobrazit dokumentu, úplné rámce v celé oblasti klienta, s vlastní nabídek a panelů nástrojů.

Ovládací prvky ActiveX, který napíšete můžete asynchronně staženy ze serveru a zobrazit na webové stránce. Skriptovací jazyk, jako je například VBScript můžete použít k provedení ověřování na straně klienta před odesláním informací na server.

##  <a name="_core_browser_or_standalone"></a> Prohlížeč nebo samostatné aplikace

Můžete napsat ovládací prvky ActiveX, které jsou vloženy do stránku HTML a servery pro aktivní dokumenty, které jsou zobrazená v prohlížeči. Můžete napsat stránky HTML, které obsahuje tlačítko Odeslat požadavek na spuštění aplikace rozhraní ISAPI na webovém serveru. Můžete napsat samostatné aplikace, která používá Internetové protokoly Pokud chcete soubory uložit a zobrazit informace na uživatele, bez někdy pomocí aplikace prohlížeče.

##  <a name="_core_com_on_the_internet"></a> COM na Internetu

Ovládací prvky ActiveX, Active dokumenty a asynchronní monikery pomocí technologie modelu COM (Component Object Model).

Ovládací prvky ActiveX poskytují dynamický obsah k dokumentům a stránky na internetové weby. S modelem COM můžete vytvořit ovládací prvky ActiveX a plně rámce dokumentů pomocí aktivní dokumenty.

Asynchronní monikery poskytují funkce, které umožňují provádět i v prostředí sítě Internet, včetně přírůstkové ovládací prvek nebo postupné znamená, že se stáhnout data. Ovládací prvky musí také měla fungovat s další ovládací prvky, které může také být načítání svá data asynchronně ve stejnou dobu.

##  <a name="_core_client_data_download_services"></a> Stáhnout Data klientů služby

Dvě sady rozhraní API, která vám pomůže přenos dat do vašeho klienta jsou WinInet a asynchronních monikerů. Pokud máte velké .gif a souborů AVI a ovládací prvky ActiveX na stránce HTML, můžete zvýšit rychlost odezvy pro uživatele stažením asynchronně, buď pomocí asynchronní monikery nebo pomocí rozhraní WinInet asynchronně.

Běžnou úlohou na Internetu přenáší data. Pokud už používáte aktivní technologii (například pokud máte ovládací prvek ActiveX), můžete použít asynchronní monikery postupně vykreslit data během stahování. Wininet – slouží k přenosu dat s využitím běžných Internetové protokoly, jako jsou HTTP, FTP a gopher. Obě metody poskytují nezávislost protokolu a abstraktní vrstvu pomocí rozhraní WinSock a protokolu TCP/IP. Můžete dál používat [WinSock](../mfc/windows-sockets-in-mfc.md) přímo.

Následující tabulka shrnuje několik možností, jak pomocí knihovny MFC pro přenos dat přes Internet.

|Pomocí tohoto protokolu|Za těchto podmínek|Použití těchto tříd|
|-----------------------|----------------------------|-------------------------|
|[Internet stahování pomocí asynchronní Monikery](../mfc/asynchronous-monikers-on-the-internet.md)|Pro asynchronní přenos používání modelu COM, ovládací prvky ActiveX a jakékoli Internet protocol.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Pro internetové protokoly HTTP, FTP a gopher. Data lze přenést synchronně nebo asynchronně a uložená v mezipaměti na celý systém.|[Cinternetsession –](../mfc/reference/cinternetsession-class.md), [cftpfilefind –](../mfc/reference/cftpfilefind-class.md), [cgopherfilefind –](../mfc/reference/cgopherfilefind-class.md)a mnoho dalších.|
|[WinSock](../mfc/windows-sockets-in-mfc.md)|Pro dosažení maximální efektivity a ovládací prvek. Vyžaduje pochopení soketů a protokolů TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Viz také:

[Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Asynchronní monikery na internetu](../mfc/asynchronous-monikers-on-the-internet.md)
