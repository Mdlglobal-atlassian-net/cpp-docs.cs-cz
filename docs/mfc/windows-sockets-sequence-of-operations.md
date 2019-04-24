---
title: 'Windows Sockets: Posloupnost operací'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
ms.openlocfilehash: 0f9fd339fdbdfee9381ea693568f40473c2397e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296511"
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows Sockets: Posloupnost operací

Tento článek ukazuje vedle sebe, posloupnost operací při serverového soketu a klientského soketu. Protože sokety používají `CArchive` objekty, jsou nutně [sokety datového proudu](../mfc/windows-sockets-stream-sockets.md).

## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>Posloupnost operací při Soketovou komunikací Stream

Až do okamžiku vytváření `CSocketFile` objekt, je přesné (s několika rozdíly parametr) k následujícímu pořadí pro obě `CAsyncSocket` a `CSocket`. Od této chvíle je sekvence určené výhradně pro `CSocket`. Následující tabulka znázorňuje posloupnost operací při nastavení komunikace mezi klientem a serverem.

### <a name="setting-up-communication-between-a-server-and-a-client"></a>Nastavení komunikace mezi serverem a klientem

|Server|Klient|
|------------|------------|
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|
|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> -nebo-<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> - i -|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> -nebo-<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> - i -|
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> -nebo-<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> -nebo-<br /><br /> `arOut << dwValue;`6|

1. Kde *nPort* je číslo portu. Zobrazit [rozhraní Windows Sockets: Porty a adresy soketů](../mfc/windows-sockets-ports-and-socket-addresses.md) podrobnosti o portech.

2. Server musí vždy zadejte port, klienti můžou připojit. `Create` Volání někdy také určuje adresu. Na straně klienta použijte výchozí parametry, které požádejte MFC používat jakýkoli dostupný port.

3. Kde *nPort* je číslo portu a *strAddr* je počítač adresa nebo adresa Internet Protocol (IP).

4. Adresy počítačů lze provést několika způsoby: "ftp.microsoft.com", "microsoft.com". IP adresy pomocí formuláře "tečkované číslo" "127.54.67.32". `Connect` – Funkce kontroluje, jestli je adresa desítkovým číslem (i když nekontroluje zkontrolujte číslo je platný počítač v síti). V opačném případě `Connect` předpokládá název počítače z jednoho z jiných forem.

5. Při volání `Accept` na straně serveru, předáte odkaz na objekt soketu. Je nutné nejprve vytvořit tento objekt, ale Nevolejte `Create` pro něj. Mějte na paměti, která pokud je tento objekt soketu se odesílá z oboru, ukončí připojení. Nový objekt, který se připojí knihovny MFC **SOKETU** zpracovat. Můžete vytvořit soket v zásobníku, jak je znázorněno, nebo na haldě.

6. Archiv a soubor soketu se zavřou, při mizení z rozsahu. Také volání destruktoru objekt soketu [Zavřít](../mfc/reference/casyncsocket-class.md#close) členskou funkci pro objekt soketu, když dostane mimo rozsah nebo odstranění objektu.

## <a name="additional-notes-about-the-sequence"></a>Další poznámky o sekvence

Sekvence volání je uvedeno v předchozí tabulce je pro datový proud soketu. Sokety datagramu, které jsou bez připojení, nevyžadují [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect), [naslouchání](../mfc/reference/casyncsocket-class.md#listen), a [přijmout](../mfc/reference/casyncsocket-class.md#accept) volání (i když můžete volitelně použít `Connect`). Místo toho pokud používáte třídu `CAsyncSocket`, datagram sockets – použití `CAsyncSocket::SendTo` a `ReceiveFrom` členské funkce. (Pokud používáte `Connect` v datagramu soketu, použijete `Send` a `Receive`.) Protože `CArchive` nefunguje s datagramů, nepoužívejte `CSocket` s archiv datagram při soketu.

[Csocketfile –](../mfc/reference/csocketfile-class.md) nepodporuje všechny `CFile`vaší funkce. `CFile` členy jako `Seek`, které žádný smysl pro soketovou komunikací, nejsou k dispozici. Z tohoto důvodu některé výchozí knihovny MFC `Serialize` funkce nejsou kompatibilní s `CSocketFile`. To platí hlavně `CEditView` třídy. By se neměl pokoušet serializovat `CEditView` data prostřednictvím `CArchive` objekt připojen k `CSocketFile` pomocí `CEditView::SerializeRaw`; použijte `CEditView::Serialize` místo (není dokumentováno). [SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw) funkce očekává, že soubor objektu má funkce, jako například `Seek`, který `CSocketFile` nepodporuje.

Další informace naleznete v tématu:

- [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Porty a adresy soketů](../mfc/windows-sockets-ports-and-socket-addresses.md)

- [Windows Sockets: Stream Sockets](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramu](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také:

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket – třída](../mfc/reference/csocket-class.md)<br/>
[CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)<br/>
[CAsyncSocket::Close](../mfc/reference/casyncsocket-class.md#close)
