---
title: 'Windows Sockets: Oznámení soketů'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: df7bfe8a95221682d0f7f4ebb123bd15b79144d5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774331"
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets: Oznámení soketů

Tento článek popisuje funkce oznámení ve třídách soketu. Tyto členské funkce jsou funkce zpětného volání, které volá framework oznámit objekt soketu o důležitých událostech. Funkce oznámení jsou:

- [Události OnReceive](../mfc/reference/casyncsocket-class.md#onreceive): Upozorní tento soket má data ve vyrovnávací paměti, aby se načíst voláním [Receive](../mfc/reference/casyncsocket-class.md#receive).

- [OnSend](../mfc/reference/casyncsocket-class.md#onsend): Upozorní tento soket, aby ho teď může odesílat data voláním [odeslat](../mfc/reference/casyncsocket-class.md#send).

- [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept): Upozorní tento naslouchání soketu, ve kterém lze přijmout čekající žádosti o připojení pomocí volání [přijmout](../mfc/reference/casyncsocket-class.md#accept).

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect): Upozorní tento připojování soketu došlo k pokusu o jeho dokončení: možná úspěšně, nebo možná chybu.

- [Při zavření](../mfc/reference/casyncsocket-class.md#onclose): Upozorní tento soket, který má uzavřený soket, ke kterému je připojený k.

    > [!NOTE]
    >  Je další oznamovací funkci [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata). Toto oznámení informuje příjmu soketu, že odesílání soket má "out-of-band" data k odeslání. Out-of-band data jsou logicky nezávislý channel spojené s každou dvojici sokety datového proudu připojené. Out-of-band kanálu se obvykle používá k odesílání dat "urgentní". MFC podporuje out-of-band data. Zkušení uživatelé pracovat s třídou [CAsyncSocket](../mfc/reference/casyncsocket-class.md) může být potřeba použít out-of-band kanálu, ale uživatelé třídy [csocket –](../mfc/reference/csocket-class.md) se nedoporučuje používat. Vytvořit druhý soket pro předávání těchto dat je jednodušší způsob. Další informace o datech out-of-band najdete v tématu Specifikace rozhraní Windows Sockets k dispozici v sadě Windows SDK.

Pokud odvozujete od třídy `CAsyncSocket`, je nutné přepsat funkce oznámení pro tyto síťové událostí, které vás zajímají do vaší aplikace. Pokud odvodíte třídu od třídy `CSocket`, je podle vašeho výběru, jestli se má přepsat funkce oznámení, které vás zajímají. Můžete také použít `CSocket` samostatně, v takovém případě oznámení funkce výchozí nicneděláním.

Tyto funkce jsou overridable zpětného volání funkce. `CAsyncSocket` a `CSocket` převést zprávy pro oznámení, ale je nutné implementovat funkci reakce na oznámení Pokud budete chtít využít. Funkce oznámení jsou volány v době, kdy vaše soketu obdrží oznámení události, které vás zajímají, jako je například přítomnosti dat pro čtení.

MFC volá funkce oznámení umožňuje přizpůsobit chování k soketu. v době, kdy je upozornění. Například můžete volat `Receive` z vaší `OnReceive` funkce oznámení, tedy na vrácení oznámeno data ke čtení, můžete volat `Receive` k jeho čtení. Tento přístup není nezbytné, ale je platný scénář. Jako alternativu můžete použít funkci oznámení můžete sledovat postup prací, vytisknout **trasování** zprávy a tak dále.

Můžete využít tato oznámení podle přepsání funkce oznámení v třídě odvozené soketu a zajistit pomocí implementace.

Během operace, jako je příjem a odesílání dat `CSocket` objekt se stane synchronní. Během synchronního stavu jsou všechna naše oznámení určená pro jinými sokety ve frontě době aktuální soketu čeká na oznámení, které chce. (Například během `Receive` volání, soketu chce, aby se oznámení ke čtení.) Jakmile soketu synchronní operaci dokončí a opět asynchronní, můžete začít jinými sokety ve frontě oznámení.

> [!NOTE]
>  V `CSocket`, `OnConnect` nebude nikdy volána funkce oznámení. Pro připojení, můžete volat `Connect`, která vrátí po dokončení připojení (ať už úspěšně nebo s chybou). Zpracování oznámení připojení je podrobnosti implementace MFC.

Podrobnosti o jednotlivých funkcích notification, najdete v části funkce v rámci třídy `CAsyncSocket` v *odkaz knihovny MFC*. Zdrojový kód a informace o ukázky knihovny MFC naleznete v tématu [ukázky knihovny MFC](../overview/visual-cpp-samples.md).

Další informace naleznete v tématu:

- [Windows Sockets: Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Jak pracují sokety s archivy](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Blokování](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: Pořadí bajtů](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: Převádění řetězců](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Viz také:

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)
