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
ms.openlocfilehash: 791bf07c927e80e65e0fda79fae8a50235bc2def
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371047"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets: Porty a adresy soketů

Tento článek vysvětluje termíny "port" a "adresa", jak se používá s Windows Sockets.

## <a name="port"></a><a name="_core_port"></a>Port

Port identifikuje jedinečný proces, pro který lze službu poskytnout. V současném kontextu je port přidružen k aplikaci, která podporuje windows sockets. Cílem je identifikovat každou aplikaci Windows Sockets jedinečně, takže můžete mít více než jednu aplikaci Windows Sockets spuštěnou v počítači současně.

Některé porty jsou vyhrazeny pro běžné služby, například FTP. Měli byste se vyhnout použití těchto portů, pokud neposkytujete tento druh služby. Specifikace windows sockets podrobnosti tyto vyhrazené porty. Soubor WINSOCK. H také uvádí je.

Chcete-li, aby knihovna DLL rozhraní Windows Sockets vybrala použitelný port za vás, předajte hodnotu portu 0. Knihovna MFC vybere hodnotu portu větší než 1 024 desetinných míst. Hodnotu portu vybranou knihovnou MFC můžete načíst voláním členské funkce [CAsyncSocket::GetSockName.](../mfc/reference/casyncsocket-class.md#getsockname)

## <a name="socket-address"></a><a name="_core_socket_address"></a>Adresa soketu

Každý objekt soketu je přidružen k adrese IP (Internet Protocol) v síti. Adresa je obvykle název počítače, například "ftp.microsoft.com" nebo tečkované číslo, například "128.56.22.8".

Při hledání vytvořit soket, obvykle není nutné zadat vlastní adresu.

> [!NOTE]
> Je možné, že váš počítač má více síťových karet (nebo vaše aplikace může jednoho dne spustit na takovém počítači), z nichž každá představuje jinou síť. Pokud ano, možná budete muset zadat adresu, která určí, kterou síťovou kartu bude soket používat. To je určitě pokročilé použití a možný problém přenositelnosti.

Další informace naleznete v tématu:

- [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Jak pracují sokety s archivy](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Sokety datového proudu](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)
