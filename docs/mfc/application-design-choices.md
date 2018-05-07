---
title: Volby při návrhu aplikací | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76a49d2ecfc79e35da55d1393cf3880b15fba7d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="application-design-choices"></a>Volby při návrhu aplikací
Tento článek popisuje některé problémy návrhu, které je třeba zvážit při programování pro Internet.  
  
 Témata popsaná v tomto článku:  
  
-   [Intranet a Internet](#_core_intranet_versus_internet)  
  
-   [Klientské nebo serverové aplikace](#_core_client_or_server_application)  
  
-   [](#_core_the_web_page)  
  
-   [Prohlížeč nebo samostatné aplikace](#_core_browser_or_standalone)  
  
-   [COM na Internetu](#_core_com_on_the_internet)  
  
-   [Klientská Data stažení služby](#_core_client_data_download_services)  
  
 Pokud jste připravení Zahájit zápis váš program nyní, najdete v článku [psaní aplikací MFC](../mfc/writing-mfc-applications.md).  
  
##  <a name="_core_intranet_versus_internet"></a> Intranet a Internet  
 Mnoho aplikací na Internetu a jsou přístupné všem uživatelům s prohlížeči a přístup k Internetu. Podniky jsou také implementace sítě intranet, které jsou sítím společnosti pomocí protokolů TCP/IP a webové prohlížeče. Intranetu nabízí snadno rozšiřitelný a centrální zdroje informace společnosti. Lze použít k upgradu softwaru, pro doručování a sestavování tabulek průzkumy, pro zákaznickou podporu a pro doručení informací. Následující tabulka porovnává funkce Internetu a intranetu.  
  
|Internet|Intranet|  
|--------------|--------------|  
|Malou šířkou pásma|Velká šířka pásma|  
|Menší zabezpečení dat a systémy|Řízený přístup k datům a systémy|  
|Minimální ovládací prvek obsahu|Vysoká řízení obsahu|  
  
##  <a name="_core_client_or_server_application"></a> Klientské nebo serverové aplikace  
 Aplikace může být na klientském počítači nebo na počítači serveru. Aplikace může také být uložené na serveru a pak stáhnout přes Internet a spustit na klientském počítači. WinInet knihovny MFC – třídy se používají pro klientské aplikace ke stažení souborů. Asynchronní Přezdívka třídy MFC a slouží k stažení souborů a vlastností ovládacího prvku. Třídy pro ovládací prvky ActiveX a aktivní dokumenty se používají pro klientské aplikace a aplikace, které se stahují ze serveru do spuštění v klientském počítači.  
  
##  <a name="_core_the_web_page"></a> Webové stránky: Ovládací prvky ActiveX HTML, aktivní dokumenty,  
 Společnost Microsoft nabízí několik způsobů poskytování obsahu na webové stránce. Webové stránky můžete použít standardní HTML nebo HTML rozšíření, jako je například značky object, k poskytování dynamický obsah, jako je například ovládací prvky ActiveX.  
  
 Webové prohlížeče obvykle zobrazení stránky HTML. Aktivní dokumenty, můžete také zobrazit data aplikace pro jednoduché rozhraní bodu a kliknutím podporou modelu COM prohlížeče. Server pro aktivní dokument můžete zobrazit dokumentu, úplná rámce v celého klienta, s vlastní nabídek a panelů nástrojů.  
  
 Ovládací prvky ActiveX, které můžete psát je možné stáhnout asynchronně ze serveru a zobrazí na webové stránce. Skriptovací jazyk, jako je například VBScript můžete použít k provedení ověření na straně klienta před odesláním informací na server.  
  
##  <a name="_core_browser_or_standalone"></a> Prohlížeč nebo samostatné aplikace  
 Můžete napsat ovládací prvky ActiveX, které jsou součástí na stránce HTML a servery pro aktivní dokumenty, které jsou zobrazeny v prohlížeči. Můžete napsat stránky HTML, které obsahují tlačítko Odeslat požadavek na spuštění aplikace rozhraní ISAPI na webovém serveru. Můžete napsat samostatná aplikace, která používá Internetové protokoly ke stahování souborů a zobrazit informace pro vaše uživatele bez někdy pomocí aplikace prohlížeče.  
  
##  <a name="_core_com_on_the_internet"></a> COM na Internetu  
 Ovládací prvky ActiveX, aktivní dokumenty a asynchronní monikery používat technologie COM (Component Object Model).  
  
 ActiveX – ovládací prvky poskytují dynamický obsah k dokumentům a stránky na internetové servery. U modelu COM můžete vytvořit ovládací prvky ActiveX a úplné rámce dokumentů pomocí aktivní dokumenty.  
  
 Asynchronní monikery poskytují funkce, které chcete povolit ovládacího prvku provést i v prostředí Internetu, včetně přírůstkové nebo znamená progresivního stahování dat. Ovládací prvky musí také měla fungovat s další ovládací prvky, které může také být načítání svá data asynchronně ve stejnou dobu.  
  
##  <a name="_core_client_data_download_services"></a> Klientská Data stažení služby  
 Dvě sady rozhraní API, která vám pomůže přenosu dat do klienta jsou WinInet a asynchronních monikerů. Pokud máte velké .gif a souborů AVI a ovládací prvky ActiveX na stránku HTML, můžete zvýšit rychlost odezvy pro uživatele tak, že stáhnete asynchronně, buď pomocí asynchronní monikery nebo WinInet asynchronně.  
  
 Běžné úlohy na Internetu přenáší data. Pokud už používáte technologie Active (například pokud máte ovládacího prvku ActiveX), můžete k progresivnímu vykreslení dat během stahování asynchronní monikery. WinInet může použít k přenosu dat pomocí běžných Internetové protokoly, jako je HTTP, FTP a gopher. Obě metody zadejte protokolu nezávislost a poskytnout abstraktní vrstvu pomocí rozhraní WinSock a protokolu TCP/IP. Můžete dál používat [rozhraní WinSock](../mfc/windows-sockets-in-mfc.md) přímo.  
  
 Následující tabulka shrnuje několik způsobů použití MFC pro přenos dat přes Internet.  
  
|Použít tento protokol|Za těchto podmínek|Pomocí těchto tříd|  
|-----------------------|----------------------------|-------------------------|  
|[Internet stahování pomocí asynchronní Monikery](../mfc/asynchronous-monikers-on-the-internet.md)|Pro asynchronní přenos pomocí modelu COM, ovládací prvky ActiveX a libovolný protokol pro Internet.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|  
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Pro internetové protokoly pro protokol HTTP, FTP a gopher. Data je možné přenést synchronně nebo asynchronně a je uložen v mezipaměti celého systému.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)a mnoho dalšího.|  
|[Rozhraní WinSock](../mfc/windows-sockets-in-mfc.md)|Pro maximální efektivity a řízení. Vyžaduje znalosti sockets a protokolů TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|  
  
## <a name="see-also"></a>Viz také  
 [Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Základy internetového programování MFC](../mfc/mfc-internet-programming-basics.md)   
 [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Asynchronní monikery na internetu](../mfc/asynchronous-monikers-on-the-internet.md)

