---
title: 'Windows Sockets: Blokování'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
ms.openlocfilehash: 87d4f0eb57f9e26dbf73da06b5d7ca6d61d6c174
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359998"
---
# <a name="windows-sockets-blocking"></a>Windows Sockets: Blokování

Tento článek a dva doprovodné články vysvětlují několik problémů v programování windows sockets. Tento článek popisuje blokování. Další problémy jsou popsány v článcích: [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md) a [Windows Sockets: Převod řetězců](../mfc/windows-sockets-converting-strings.md).

Pokud používáte nebo odvodit z třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), budete muset spravovat tyto problémy sami. Pokud používáte nebo odvodit z třídy [CSocket](../mfc/reference/csocket-class.md), MFC spravuje je za vás.

## <a name="blocking"></a>Blokování

Soket může být v "režimu blokování" nebo "neblokovací režim." Funkce soketů v režimu blokování (nebo synchronní) nevrátí, dokud mohou dokončit svou akci. To se nazývá blokování, protože soket, jehož funkce byla volána nemůže dělat nic – je blokován – dokud se vrátí volání. Volání `Receive` členské funkce, například může trvat libovolně dlouhou dobu k dokončení, protože čeká na odeslání odesílající `CSocket`aplikace `CAsyncSocket` odeslat (to je, pokud používáte , nebo pomocí s blokováním). Pokud `CAsyncSocket` je objekt v neblokujícím režimu (pracuje asynchronně), volání se okamžitě vrátí a aktuální kód chyby, který lze načíst pomocí členské funkce [GetLastError,](../mfc/reference/casyncsocket-class.md#getlasterror) je **WSAEWOULDBLOCK**, což znamená, že by volání bylo blokováno, kdyby nebylo okamžitě vráceno z důvodu režimu. (`CSocket` nikdy nevrátí **WSAEWOULDBLOCK**. Třída spravuje blokování za vás.)

Chování soketů se liší v rámci 32bitových a 64bitových operačních systémů (například Windows 95 nebo Windows 98) než pod 16bitovými operačními systémy (například Windows 3.1). Na rozdíl od 16bitových operačních systémů používají 32bitové a 64bitové operační systémy preemptivní multitasking a poskytují multithreading. V rámci 32bitových a 64bitových operačních systémů můžete umístit sokety do samostatných pracovních vláken. Soket ve vlákně můžete blokovat bez zásahu do jiných aktivit ve vaší aplikaci a bez výdajů výpočetní čas na blokování. Informace o programování s více vlákny naleznete v článku [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

> [!NOTE]
> V aplikacích s více vlákny můžete `CSocket` použít blokovací povahu ke zjednodušení návrhu programu bez ovlivnění odezvy uživatelského rozhraní. Zpracováním interakcí uživatelů v hlavním `CSocket` vlákně a zpracováním v alternativních vláknech můžete tyto logické operace oddělit. V aplikaci, která není vícevláknové, tyto dvě aktivity musí být kombinovány `CAsyncSocket` a zpracovány jako jedno vlákno, `CSocket::OnMessagePending` což obvykle znamená použití, takže můžete zpracovávat požadavky na komunikaci na vyžádání nebo přepsání pro zpracování akcí uživatele během dlouhé synchronní aktivity.

Zbytek této diskuse je určen pro programátory zaměřené na 16bitové operační systémy:

Za normálních okolností, pokud používáte `CAsyncSocket`, měli byste se vyhnout použití blokování operací a pracovat asynchronně místo. V asynchronních operacích od okamžiku, kdy obdržíte kód chyby **WSAEWOULDBLOCK** po `Receive` `OnReceive` volání , například počkejte, až je volána členská funkce, která vás upozorní, že můžete číst znovu. Asynchronní volání jsou prováděny voláním zpět vašeho socket je vhodné funkce oznámení zpětného volání, [například OnReceive](../mfc/reference/casyncsocket-class.md#onreceive).

V systému Windows blokování volání jsou považovány za špatné praxe. Ve výchozím nastavení [CAsyncSocket](../mfc/reference/casyncsocket-class.md) podporuje asynchronní volání a je nutné spravovat blokování sami pomocí oznámení zpětného volání. Třída [CSocket](../mfc/reference/csocket-class.md), na druhé straně je synchronní. Pumpuje zprávy systému Windows a spravuje blokování za vás.

Další informace o blokování naleznete ve specifikaci Windows Sockets. Další informace o funkcích "Zapnuto" naleznete [v tématu Windows Sockets: Socket Notifications](../mfc/windows-sockets-socket-notifications.md) a [Windows Sockets: Deriving from Socket Classes](../mfc/windows-sockets-deriving-from-socket-classes.md).

Další informace naleznete v tématu:

- [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sokety datového proudu](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)
