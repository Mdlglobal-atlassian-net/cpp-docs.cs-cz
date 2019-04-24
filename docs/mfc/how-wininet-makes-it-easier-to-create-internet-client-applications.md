---
title: Jak rozhraní WinInet usnadňuje tvorbu internetových klientských aplikací
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
ms.openlocfilehash: 6da2ef1595e525bcfd407d67c806aa80cf90f1c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262707"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>Jak rozhraní WinInet usnadňuje tvorbu internetových klientských aplikací

Win32 – internetová rozšíření nebo rozhraní WinInet, poskytují přístup ke common Internetové protokoly, včetně gopher, FTP, HTTP. Pomocí rozhraní WinInet, můžete napsat internetových klientských aplikací na vyšší úrovni programování, aniž byste museli řešit WinSock, TCP/IP nebo podrobnosti o konkrétní protokolů sítě Internet. Wininet – poskytuje konzistentní sadu funkcí pro všechny tři protokoly pomocí známých rozhraní API systému Win32. Taková konzistence minimalizuje změn kódu, které je potřeba udělat, pokud se změní na základním protokolu (například z protokolu FTP pro HTTP).

Visual C++ poskytuje dva způsoby, jak použít rozhraní WinInet. Bude možné volat funkce Win32 Internet přímo (dokumentace OLE v sadě Windows SDK pro další informace najdete v článku) nebo můžete použít rozhraní WinInet prostřednictvím [tříd WinInet knihovny MFC](../mfc/mfc-classes-for-creating-internet-client-applications.md).

**Můžete použít rozhraní WinInet na:**

- Stáhněte si stránky HTML.

   HTTP je protokol, který slouží k přenosu stránky HTML ze serveru do prohlížeče klienta.

- Odesílání požadavků FTP pro nahrávání nebo stahování souborů nebo získat výpisech adresářů.

   Typické požadavek je anonymní přihlášení ke stažení souboru.

- Použijte systém nabídek na gopher pro přístup k prostředkům v síti Internet.

   Položky nabídky může být několik typů, včetně jiných nabídek, indexované databáze, můžete hledat, diskusní skupiny nebo soubor.

Pro všechny tři protokoly navázat připojení, zkontrolujte požadavky na server a ukončete připojení.

**Tříd WinInet knihovny MFC usnadňuje:**

- Přečtěte si informace ze serverů protokolu HTTP, FTP a gopher stejně snadno, jako čtení souborů z pevného disku.

- Použijte protokoly HTTP, FTP a gopher bez přímé programování rozhraní WinSock nebo protokolu TCP/IP.

   Vývojáři, kteří používají Win32 Internet funkce není potřeba znát TCP/IP nebo rozhraní Windows Sockets. Můžete stále naprogramovat na úrovni soketu WinSock a TCP/IP protokoly pomocí přímo, ale je ještě snadnější použití tříd WinInet knihovny MFC pro přístup k protokolu HTTP, FTP a protokoly gopher přes Internet. Pro mnoho běžných operací vývojáři není nutné znát podrobnosti o konkrétní protokolu, který používají.

Mnoho operací, které můžete provádět v počítači jako klienta na jiné počítače na Internetu může trvat dlouhou dobu. Rychlost těchto operací je obvykle limitována rychlostí síťového připojení, ale může mít také vliv tak, že provoz v síti a složitosti operaci. Připojování ke vzdálenému serveru FTP, například vyžaduje, že počítač nejprve vyhledat název tohoto serveru na její adresu. Aplikace se pak pokusí připojit k serveru na této adrese. Jakmile je otevřeno připojení, počítačem a vzdáleným serverem opraví, zahájí se konverzace s protokol pro přenos souborů předtím, než ve skutečnosti můžete připojení k načtení souborů.

## <a name="see-also"></a>Viz také:

[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Jak prostředí MFC usnadňuje tvorbu internetových klientských aplikací](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)
