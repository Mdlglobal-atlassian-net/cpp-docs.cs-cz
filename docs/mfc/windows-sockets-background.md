---
title: "Windows Sockets: Pozadí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record-oriented data [MFC]
- e-mail [MFC]
- Internet Protocol Suite
- mail [MFC]
- communications [MFC], domain
- Windows Sockets [MFC], stream sockets
- mail [MFC], programming for
- sockets [MFC], stream sockets
- datagram sockets [MFC]
- SOCKET handle
- data types [MFC], socket
- e-mail [MFC], programming for
- X Window servers
- sequenced data flow
- stream sockets [MFC]
ms.assetid: f60d4ed2-bf23-4a0e-98d2-fee77e8473dd
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 418b0d76292667da6a4083dc0565867b9d2c1f13
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="windows-sockets-background"></a>Windows Sockets: Pozadí
Tento článek popisuje povahu a účel rozhraní Windows Sockets. Tento článek také:  
  
-   [Definuje termín "soketu"](#_core_definition_of_a_socket).  
  
-   [Popisuje datový typ popisovač SOKETU](#_core_the_socket_data_type).  
  
-   [Popisuje využití sockets](#_core_uses_for_sockets).  
  
 Specifikace rozhraní Windows Sockets definuje binárně kompatibilní programovací rozhraní sítě systému Microsoft Windows. Rozhraní Windows Sockets jsou založena na implementaci soketů systému UNIX v distribuci Berkeley Software Distribution (BSD, verze 4.3) z Univerzity v Berkeley v Kalifornii. Tato specifikace obsahuje rutiny soketu ve stylu distribuce BSD a rozšíření specifické pro systém Windows. Rozhraní Windows Sockets umožňuje aplikaci komunikovat v síti, která odpovídá rozhraní Windows Sockets API. V systému Win32 rozhraní Windows Sockets zajišťuje bezpečný přístup z více vláken.  
  
 Mnoho výrobců síťového softwaru podporuje rozhraní Windows Sockets pomocí síťových protokolů včetně protokolů TCP/IP (Transmission Control Protocol/Internet Protocol), XNS (Xerox Network System), protokolu DECNet společnosti Digital Equipment Corporation, protokolu IPX/SPX (Internet Packet Exchange/Sequenced Packed Exchange) společnosti Novell Corporation a dalších. Přestože současná specifikace rozhraní Windows Sockets definuje abstrakce soketů pro protokol TCP/IP, všechny síťové protokoly mohou rozhraní Windows Sockets vyhovět dodáním vlastní verze dynamické knihovny (DLL), která implementuje rozhraní Windows Sockets. Příklady komerčních aplikací napsaných pomocí rozhraní Windows Sockets jsou servery X Windows, emulátory terminálů a systémy elektronické pošty.  
  
> [!NOTE]
>  Účelem rozhraní Windows Sockets je provádět abstrakci podkladové sítě, abyste o této síti nemuseli znát podrobnosti a vaše aplikace fungovala s jakoukoli sítí podporující sokety. Tato dokumentace se proto nezabývá podrobnostmi síťových protokolů.  
  
 Knihovna MFC (Microsoft Foundation Class Library) pro podporu programování pomocí rozhraní Windows Sockets API poskytuje dvě třídy. Jedna z těchto tříd, `CSocket`, přináší vysokou úroveň abstrakce pro zjednodušení programování síťové komunikace.  
  
 Specifikace rozhraní Windows Sockets, Rozhraní Windows Sockets: Otevřené rozhraní pro síťovou komunikaci v systému Microsoft Windows, nyní ve verzi 1.1, bylo vyvinuto jako otevřený síťový standard velkou skupinou jednotlivců a podniků komunity protokolu TCP/IP a je volně k dispozici. Programovací model soketů podporuje aktuálně jednu „doménu komunikace“ pomocí sady protokolů sítě Internet. Specifikace je k dispozici v sadě Windows SDK.  
  
> [!TIP]
>  Protože sokety používají sadu protokolů sítě Internet, jsou upřednostňovanou trasou pro aplikace, které podporují komunikaci na Internetu prostřednictvím „informační dálnice“.  
  
##  <a name="_core_definition_of_a_socket"></a>Definice soket  
 Soket je koncový bod komunikace – objekt, jehož prostřednictvím aplikace rozhraní Windows Sockets odesílá nebo přijímá pakety dat v síti. Soket má typ, je přidružen ke spuštěnému procesu a může mít název. V současné době sokety obecně vyměňují data pouze s jinými sokety ve stejné „doméně komunikace“, která používá sadu protokolů sítě Internet.  
  
 Oba druhy soketů jsou obousměrné. Jsou to datové toky, kterými lze komunikovat současně v obou směrech (plně duplexní).  
  
 K dispozici jsou dva typy soketu:  
  
-   Sokety datového proudu  
  
     Sokety datového proudu zajišťují tok dat bez hranic záznamů, je to proud bajtů. Datové proudy zaručují doručení, správné seřazení a zamezují duplicitám.  
  
-   Sokety datagramu  
  
     Sokety datagramu podporují datový tok orientovaný na záznam, který nezaručuje doručení, správné seřazení ani nezamezuje duplicitám.  
  
 „Správným seřazením“ se rozumí, že pakety budou doručeny v pořadí odeslání. „Zamezení duplicitám“ znamená získání konkrétního paketu pouze jednou.  
  
> [!NOTE]
>  V některých síťových protokolech, například XNS, mohou být datové proudy orientované na záznamy a nikoli na proudy bajtů. V rámci běžnějšího protokolu TCP/IP však datové proudy představují proudy bajtů. Rozhraní Windows Sockets poskytuje úroveň abstrakce, která je nezávislá na základním protokolu.  
  
 Informace o těchto typech a jaký druh soketu používat v situacích, které, najdete v článku [Windows Sockets: sokety datového proudu](../mfc/windows-sockets-stream-sockets.md) a [Windows Sockets: sokety datagramů](../mfc/windows-sockets-datagram-sockets.md).  
  
##  <a name="_core_the_socket_data_type"></a>Datový typ SOKETŮ  
 Každý objekt soketu knihovny MFC zapouzdřuje popisovač objektu rozhraní Windows Sockets. Datový typ tento popisovač je **SOKETU**. A **SOKETU** obslužná rutina je podobná `HWND` v časovém období. Třídy soketů knihovny MFC poskytují operace zapouzdřené popisovačem.  
  
 **SOKETU** datový typ je podrobně popsaná v ve Windows SDK. Další informace naleznete v části „Datový typ soketu a chybové hodnoty“ v tématu Rozhraní Windows Sockets.  
  
##  <a name="_core_uses_for_sockets"></a>Používá pro Sockets  
 Sokety jsou velmi užitečné v nejméně třech kontextech komunikace:  
  
-   Modely klient/server.  
  
-   Scénáře sítě peer-to-peer, jako jsou například aplikace pro zasílání zpráv.  
  
-   Volání vzdálených procedur (RPC) tím, že umožňují přijímající aplikaci zprávu interpretovat jako volání funkce.  
  
> [!TIP]
>  Ideálním případem použití soketů knihovny MFC je, když vytváříte obě strany komunikace: používáte knihovnu MFC na obou koncích. Další informace v tomto tématu, včetně toho, jak ke správě případě, když komunikujete mimo MFC aplikace, najdete v části [Windows Sockets: pořadí bajtů](../mfc/windows-sockets-byte-ordering.md).  
  
 Další informace najdete v tématu Specifikace Windows Sockets: **ntohs**, **ntohl**, **htons**, **htonl**. Také si přečtěte následující témata:  
  
-   [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Příklady soketů využívajících archivy](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows Sockets: Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)
