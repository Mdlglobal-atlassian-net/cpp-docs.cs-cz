---
title: "Windows Sockets: Posloupnost operací | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f70765d94b0104cf905130ce043c2b0e35b26a41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows Sockets: Posloupnost operací
Tento článek ukazuje vedle sebe, posloupnost operací při soketu serveru a klienta soketu. Protože sockets používají `CArchive` objekty, jsou nutně [stream sockets](../mfc/windows-sockets-stream-sockets.md).  
  
## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>Posloupnost operací při Soketovou komunikací datového proudu  
 Až do okamžiku vytváření `CSocketFile` objekt, je přesné (s několika rozdíly parametr) k následujícímu pořadí pro obě `CAsyncSocket` a `CSocket`. Od této chvíle sekvenci je určené výhradně pro `CSocket`. Následující tabulka znázorňuje pořadí operací pro nastavení komunikace mezi klientem a serverem.  
  
### <a name="setting-up-communication-between-a-server-and-a-client"></a>Nastavení komunikace mezi serverem a klientem  
  
|Server|Klient|  
|------------|------------|  
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|  
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|  
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||  
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|  
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||  
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|  
|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> -nebo-<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> - nebo obě-|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> -nebo-<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> - nebo obě-|  
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> -nebo-<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> -nebo-<br /><br /> `arOut << dwValue;`6|  
  
 1. Kde `nPort` je číslo portu. V tématu [Windows Sockets: porty a adresy soketů](../mfc/windows-sockets-ports-and-socket-addresses.md) podrobnosti o portech.  
  
 2. Na server musíte určit port, klienti mohou připojit. **Vytvořit** volání někdy také určuje adresu. Na straně klienta použijte výchozí parametry, které požádejte MFC použít jakýkoli dostupný port.  
  
 3. Kde `nPort` je číslo portu a *strAddr* adresu počítače nebo adresu Internet Protocol (IP).  
  
 4. Adresy počítačů lze provést několika způsoby: "ftp.microsoft.com", "microsoft.com". IP adresy použijte formát "s tečkami číslo" "127.54.67.32". **Connect** funkce zkontroluje, pokud je na adresu desítkovém číslo (i když nekontroluje zkontrolujte číslo je platný počítač v síti). Pokud ne, **Connect** předpokládá název počítače jednoho z jiných formulářů.  
  
 5. Při volání **přijmout** na straně serveru, předáte odkaz na nový objekt soketu. Musíte nejprve vytvořit tento objekt, ale Nevolejte **vytvořit** pro ni. Mějte na paměti, že pokud tento objekt soketu prochází oboru, zavře připojení. MFC připojí nový objekt, který má **SOKETU** zpracování. Můžete vytvořit soket v zásobníku, jak je znázorněno, nebo v haldě.  
  
 6. Archiv a soubor soketu se uzavřít, když se dostala mimo rozsah. Objekt soketu destruktor také voláním [Zavřít](../mfc/reference/casyncsocket-class.md#close) – členská funkce pro objekt soketu při objekt ocitne mimo rozsah, nebo je odstranit.  
  
## <a name="additional-notes-about-the-sequence"></a>Další poznámky o sekvenci  
 Posloupnost volání, které jsou uvedené v předchozí tabulce je pro datový proud soketu. Sokety datagramu, které jsou bez připojení, nevyžadují [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect), [naslouchání](../mfc/reference/casyncsocket-class.md#listen), a [přijmout](../mfc/reference/casyncsocket-class.md#accept) volání (i když můžete volitelně použít **Připojit**). Místo toho pokud používáte třída `CAsyncSocket`, sokety datagramů používají `CAsyncSocket::SendTo` a `ReceiveFrom` členské funkce. (Pokud používáte **připojit** s datagram soketu a používáte **odeslat** a **Receive**.) Protože `CArchive` nefunguje s datagramy, nepoužívejte `CSocket` s archiv pokud datagram soketu.  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md) nepodporuje všechny `CFile`na funkce. `CFile` členy jako `Seek`, které žádný smysl pro komunikaci ve formě soketu, nejsou k dispozici. Z toho důvodu některé výchozí MFC `Serialize` funkce nejsou kompatibilní s `CSocketFile`. To platí hlavně z `CEditView` třídy. By se neměl pokoušet serializovat `CEditView` data prostřednictvím `CArchive` objekt připojený k `CSocketFile` pomocí `CEditView::SerializeRaw`; použít **CEditView::Serialize** místo (není zdokumentovaný). [SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw) funkce očekává objektu soubor do mají funkce, jako například `Seek`, že `CSocketFile` nepodporuje.  
  
 Další informace naleznete v tématu:  
  
-   [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Porty a adresy soketů](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
-   [Windows Sockets: Sokety streamu](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)   
 [CSocket – třída](../mfc/reference/csocket-class.md)   
 [CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)   
 [CAsyncSocket::Close](../mfc/reference/casyncsocket-class.md#close)

