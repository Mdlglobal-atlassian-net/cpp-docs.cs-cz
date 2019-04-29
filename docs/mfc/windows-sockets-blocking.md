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
ms.openlocfilehash: 26a361bc63da5f6e75144cc91fe837498a7f656b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371961"
---
# <a name="windows-sockets-blocking"></a>Windows Sockets: Blokování

V tomto článku a dva doprovodné články popisují několik problémů v programování v rozhraní Windows Sockets. Tento článek se týká blokování. Tyto problémy jsou popsané v článcích: [Windows Sockets: Pořadí bajtů](../mfc/windows-sockets-byte-ordering.md) a [rozhraní Windows Sockets: Převádění řetězců](../mfc/windows-sockets-converting-strings.md).

Pokud používáte nebo odvozen od třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), budete muset spravovat tyto problémy sami. Pokud používáte nebo odvozen od třídy [csocket –](../mfc/reference/csocket-class.md), knihovna MFC je spravuje za vás.

## <a name="blocking"></a>Blokování

Soket může být v "režim blokování" nebo "neblokový režim." Funkce sokety režimu blokování (nebo synchronní) vracet, dokud, můžete provést akci. Tento postup se nazývá blokování, protože soketu, jehož funkce jmenovala nemůže provádět žádné akce – blokovaný, dokud volání se vrátí. Volání `Receive` členskou funkci, například může trvat libovolně dlouhý čas dokončit, protože se čeká na odeslání aplikace pro odesílání (to je, pokud používáte `CSocket`, nebo pomocí `CAsyncSocket` s blokování). Pokud `CAsyncSocket` objektu je v neblokový režimu (provozní asynchronně), volání se vrátí okamžitě a aktuální kód chyby, retrievable s [GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror) členská funkce je **WSAEWOULDBLOCK**, byl označující, že volání bude blokováno z důvodu režimu nevrací se, okamžitě. (`CSocket` nikdy nevrátí **WSAEWOULDBLOCK**. Třída spravuje blokování za vás.)

Chování sockets se liší podle 32bitové a 64bitové operační systémy (například Windows 95 nebo Windows 98) než v 16bitových operačních systémů (například Windows 3.1). Na rozdíl od 16bitových operačních systémů 32bitová verze a 64bitová verze operačních systémů použijte preemptive multitaskingu a zadejte multithreadingu. V části 32bitové a 64bitové operační systémy můžete umístit vaše sockets v samostatných pracovních vláknech. Soket ve vlákně můžete zablokovat, aniž by zasahovala do další aktivity v aplikaci a bez blokování zbavuje výpočetní čas. Informace o programování s více vlákny, najdete v článku [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

> [!NOTE]
>  Ve vícevláknových aplikacích, můžete použít k blokování povaze `CSocket` zjednodušit návrh vašeho programu bez ovlivnění rychlosti odezvy uživatelského rozhraní. Díky zpracování interakcí s uživateli v hlavním vlákně a `CSocket` zpracování v alternativní vlákna, můžete oddělit tyto logické operace. V aplikaci, která není s více vlákny, musí být obě aktivity kombinovat a spravovány jako jedno vlákno, které obvykle znamená, že používá `CAsyncSocket` tak může zpracovávat požadavky na komunikaci na vyžádání nebo přepsání `CSocket::OnMessagePending` pro zpracování uživatelské akce během dlouhých synchronní aktivity.

Zbytek této diskuse je usnadňuje práci programátorům cílení 16bitových operačních systémů:

Za normálních okolností používáte `CAsyncSocket`, byste měli vyhnout blokující operace a pracovat místo asynchronně. V asynchronních operací z bodu, ve kterém se zobrazí **WSAEWOULDBLOCK** kód chyby: po volání `Receive`, třeba počkat do vaší `OnReceive` členská funkce je volána s upozorněním, že si můžete přečíst znovu. Byla zahájena asynchronní volání jsou provedeny voláním zpět k soketu odpovídající funkce zpětného volání oznámení, jako například [události OnReceive](../mfc/reference/casyncsocket-class.md#onreceive).

V části Windows se považují blokování volání chybný postup. Ve výchozím nastavení [CAsyncSocket](../mfc/reference/casyncsocket-class.md) podporuje asynchronní volání a vy musíte spravovat blokování sami pomocí zpětné volání oznámení. Třída [csocket –](../mfc/reference/csocket-class.md), na druhé straně je synchronní. Čerpadla zpráv Windows a spravuje blokování za vás.

Další informace o blokování najdete v tématu Specifikace rozhraní Windows Sockets. Další informace o "U" funkcí najdete v tématu [rozhraní Windows Sockets: Soketu oznámení](../mfc/windows-sockets-socket-notifications.md) a [rozhraní Windows Sockets: Odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md).

Další informace naleznete v tématu:

- [Windows Sockets: Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Podrobnosti](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sokety datového proudu](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramu](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také:

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)
