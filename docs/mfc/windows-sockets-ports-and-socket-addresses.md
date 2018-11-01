---
title: 'Windows Sockets: Porty a adresy soketů'
ms.date: 11/04/2016
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
ms.openlocfilehash: d132001cb792877e3d476508a6a5bb456dfb5987
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631358"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets: Porty a adresy soketů

Tento článek vysvětluje podmínky "portu" a "address" jako použít pomocí rozhraní Windows Sockets.

##  <a name="_core_port"></a> Port

Port identifikuje jedinečné proces, na kterém mohou být poskytnuty služby. V rámci tohoto portu je přidružený k aplikaci, která podporuje rozhraní Windows Sockets. Cílem je jednoznačně identifikovat každou aplikaci rozhraní Windows Sockets tak může mít více než jednu rozhraní Windows Sockets aplikaci spuštěnou na počítači ve stejnou dobu.

Některé porty jsou vyhrazené pro běžné služby, jako je například FTP. Neměli byste pomocí těchto portů, pokud zadáváte tento druh služby. Specifikace rozhraní Windows Sockets obsahuje podrobnosti o těchto vyhrazené porty. Soubor rozhraní WINSOCK. H také uvádí je.

Aby mohl Windows Sockets knihovny DLL vyberte použitelné port pro vás, předejte 0, jako hodnotu portu. MFC vybere větší než 1 024 Desítková hodnota portu. Můžete načíst hodnotu portu, který MFC vybrali voláním [CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) členskou funkci.

##  <a name="_core_socket_address"></a> Adres soketu

Každý objekt soketu souvisí adresou Internet Protocol (IP) v síti. Adresa je obvykle název počítače, jako je například "ftp.microsoft.com", nebo desítkovým číslem, například "128.56.22.8".

Při hledání vytvořit soket, obvykle není potřeba zadat svou vlastní adresu.

> [!NOTE]
>  Je možné, že váš počítač má několik síťových karet (nebo vaše aplikace mohla běžet někdy takový počítač), každý představující jinou síť. Pokud ano, je potřeba uvést adresu k určení, které síťové karty budou používat soketu. Toto je některé pokročilé využití a problém s přenositelností je to možné.

Další informace naleznete v tématu:

- [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Jak pracují sokety s archivy](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Sokety streamu](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)

