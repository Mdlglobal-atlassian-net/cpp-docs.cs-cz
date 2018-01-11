---
title: "Jak rozhraní WinInet usnadňuje tvorbu internetových klientských aplikací | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9c79404f296df09afb177930897064b8455217d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>Jak rozhraní WinInet usnadňuje tvorbu internetových klientských aplikací
Win32 – internetová rozšíření nebo WinInet, poskytují přístup k běžné Internetové protokoly, včetně gopher, FTP a HTTP. Pomocí WinInet, můžete napsat internetové klientské aplikace na vyšší úrovni programování, aniž byste museli řešit rozhraní WinSock, protokolu TCP/IP nebo podrobnosti o konkrétní internetových protokolech. WinInet poskytuje konzistentní sadu funkcí pro všechny tři protokoly s známé rozhraní Win32 API. Tato konzistence minimalizuje změn kódu, které budete muset udělat, pokud se změní základního protokolu (například z FTP HTTP).  
  
 Visual C++ nabízí dva způsoby, budete moci použít WinInet. Funkce Win32 Internet můžete volat přímo (viz dokumentace OLE ve Windows SDK pro další informace) nebo můžete použít WinInet prostřednictvím [WinInet knihovny MFC – třídy](../mfc/mfc-classes-for-creating-internet-client-applications.md).  
  
 **Můžete použít WinInet na:**  
  
-   Stáhněte si stránky HTML.  
  
     HTTP je protokol, který slouží k přenosu stránky HTML ze serveru do prohlížeče klienta.  
  
-   Odesílat požadavky protokolu FTP odeslání nebo stažení souborů nebo získat výpisech adresářů.  
  
     Je typické požadavek anonymní přihlášení ke stažení souboru.  
  
-   Používejte systém nabídek na gopher pro přístup k prostředkům na Internetu.  
  
     Položky nabídky může být několik typů, včetně jiných nabídek, indexované databáze, můžete hledat, diskusní skupiny nebo souboru.  
  
 Pro všechny tři protokoly připojení, zkontrolujte požadavky na server a ukončení připojení.  
  
 **Třídy MFC WinInet usnadňují:**  
  
-   Načíst informace z protokolů HTTP, FTP a gopher servery snadno jako čtení souborů z pevného disku.  
  
-   Pomocí protokolů HTTP, FTP a gopher bez programování přímo na rozhraní WinSock nebo protokolu TCP/IP.  
  
     Není potřeba znát protokolu TCP/IP nebo Windows Sockets vývojáře, kteří používají funkce Win32 Internet. Můžete stále programovat na úrovni soketu, pomocí protokolů rozhraní WinSock a TCP/IP přímo, ale je snazší i pomocí tříd WinInet knihovny MFC přístup protokolu HTTP, FTP a protokoly gopher přes Internet. Pro mnoho běžných operací není potřeba vývojáři znát podrobnosti o konkrétní protokol, který používají.  
  
 Mnoho operací, které lze provést pomocí počítače jako klienta na jiné počítače na Internetu může trvat dlouhou dobu. Rychlost těchto operací je obvykle limitována rychlostí síťového připojení, ale budou mít vliv i provoz v síti a složitost operace. Připojení ke vzdálenému serveru FTP, například vyžaduje, že váš počítač nejprve vyhledat název tohoto serveru najít její adresu. Aplikace se potom pokusí připojit k serveru na tuto adresu. Po otevření připojení vaším počítačem a vzdáleným serverem zahájíte konverzace s protokol pro přenos souborů před připojení můžete použít ve skutečnosti k načtení souborů.  
  
## <a name="see-also"></a>Viz také  
 [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Jak prostředí MFC usnadňuje tvorbu internetových klientských aplikací](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)

