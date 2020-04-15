---
title: 'Windows Sockets: Použití soketů s archivy'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
ms.openlocfilehash: 55b4f9a5412c1447fe2b3bde10cb934b91abf008
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359956"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets: Použití soketů s archivy

Tento článek popisuje [programovací model CSocket](#_core_the_csocket_programming_model). Třída [CSocket](../mfc/reference/csocket-class.md) poskytuje podporu soketu na vyšší úrovni abstrakce než třída [CAsyncSocket](../mfc/reference/casyncsocket-class.md). `CSocket`Používá verzi protokolu serializace knihovny MFC k předání dat do a z objektu soketu prostřednictvím objektu [CArchive](../mfc/reference/carchive-class.md) knihovny MFC. `CSocket`Poskytuje blokování (při správě zpracování zpráv systému `CArchive`Windows na pozadí) a poskytuje přístup k aplikaci , která spravuje `CAsyncSocket`mnoho aspektů komunikace, kterou byste museli provést sami pomocí raw API nebo třídy .

> [!TIP]
> Třídu `CSocket` můžete použít samostatně, jako pohodlnější `CAsyncSocket`verzi aplikace , ale nejjednodušší `CSocket` programovací model je použití s objektem. `CArchive`

Další informace o tom, jak funguje implementace soketů s archivy, naleznete v [tématu Windows Sockets: How Sockets with Archives Work](../mfc/windows-sockets-how-sockets-with-archives-work.md). Například kód, najdete [v tématu Windows Sockets: Posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md) a [Windows Sockets: Příklad soketů pomocí archivů](../mfc/windows-sockets-example-of-sockets-using-archives.md). Informace o některých funkcích, které můžete získat odvozením vlastních tříd z tříd soketů, naleznete v [tématu Windows Sockets: Deriving from Socket Classes](../mfc/windows-sockets-deriving-from-socket-classes.md).

> [!NOTE]
> Pokud píšete klientský program knihovny MFC pro komunikaci se zavedenými servery (jiné než MFC), neodesílejte objekty jazyka C++ prostřednictvím archivu. Pokud server není aplikace knihovny MFC, která rozumí typy objektů, které chcete odeslat, nebude moci přijímat a rekonstruovat objekty. Související materiál týkající se komunikace s aplikacemi, které nejsou součástí knihovny MFC, naleznete také v článku [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md).

## <a name="the-csocket-programming-model"></a><a name="_core_the_csocket_programming_model"></a>Programovací model CSocket

Použití `CSocket` objektu zahrnuje vytvoření a spojení několika objektů třídy knihovny MFC. V níže uvedeném obecném postupu je každý krok proveden soketem serveru i soketem klienta, s výjimkou kroku 3, ve kterém každý typ soketu vyžaduje jinou akci.

> [!TIP]
> V době běhu serverová aplikace obvykle spustí nejprve být připraven a "naslouchání", když klientská aplikace hledá připojení. Pokud server není připraven, když se klient pokusí připojit, obvykle vyžadujete, aby se uživatelská aplikace pokusila připojit později.

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>Nastavení komunikace mezi soketem serveru a soketem klienta

1. Vytvořte objekt [CSocket.](../mfc/reference/csocket-class.md)

1. Pomocí objektu vytvořte základní popisovač **SOCKET.**

   Pro `CSocket` objekt klienta byste měli obvykle použít výchozí parametry [k vytvoření](../mfc/reference/casyncsocket-class.md#create), pokud nepotřebujete soket datagramu. Pro `CSocket` objekt serveru je nutné zadat `Create` port v volání.

    > [!NOTE]
    >  `CArchive`nefunguje se sokety datagramu. Pokud chcete použít `CSocket` pro soket datagramu, musíte použít `CAsyncSocket`třídu tak, jak byste použili , to znamená bez archivu. Vzhledem k tomu, že datagramy jsou nespolehlivé (není zaručeno, že dorazí a mohou být opakovány nebo mimo pořadí), nejsou kompatibilní s serializací prostřednictvím archivu. Očekáváte, že operace serializace k dokončení spolehlivě a v pořadí. Pokud se pokusíte `CSocket` `CArchive` použít s objektem pro datagram, kontrolní výraz knihovny MFC se nezdaří.

1. Pokud je soket klientem, volejte [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect) pro připojení objektu soketu k soketu serveru.

     -nebo-

   Pokud je soket server, volejte [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen) začít naslouchat pokusům o připojení z klienta. Po obdržení žádosti o připojení jej přijměte voláním [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

    > [!NOTE]
    >  Členská `Accept` funkce přebírá jako svůj `CSocket` parametr odkaz na nový prázdný objekt. Tento objekt je nutné `Accept`vytvořit před voláním . Pokud tento objekt soketu přejde mimo rozsah, připojení se zavře. Nevolejte `Create` tento nový objekt soketu.

1. Vytvořte objekt [CSocketFile,](../mfc/reference/csocketfile-class.md) který s `CSocket` ním přisazuje objekt.

1. Vytvořte objekt [CArchive](../mfc/reference/carchive-class.md) pro načítání (příjem) nebo ukládání (odesílání) dat. Archiv je přidružen `CSocketFile` k objektu.

   Mějte na `CArchive` paměti, že nefunguje s datagram sokety.

1. Pomocí `CArchive` objektu předavte data mezi klientskými a serverovými sokety.

   Mějte na paměti, že daný `CArchive` objekt přesouvá data pouze v jednom směru: buď pro načítání (příjem) nebo ukládání (odesílání). V některých případech použijete dva `CArchive` objekty: jeden pro odesílání dat, druhý pro příjem potvrzení.

   Po přijetí připojení a nastavení archivu můžete provádět takové úkoly, jako je ověřování hesel.

1. Zničte objekty archivu, soketu a soketu.

    > [!NOTE]
    >  Class `CArchive` dodává `IsBufferEmpty` členské funkce speciálně `CSocket`pro použití s class . Pokud vyrovnávací paměť obsahuje více datových zpráv, například je třeba opakovat, dokud všechny z nich jsou čteny a vyrovnávací paměti je vymazána. V opačném případě může být další oznámení, že jsou přijata data, zpožděno na dobu neurčitou. Slouží `IsBufferEmpty` k zajištění, že načtete všechna data.

V článku [Windows Sockets: Posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md) ilustruje obě strany tohoto procesu s ukázkovým kódem.

Další informace naleznete v tématu:

- [Windows Sockets: Sokety datového proudu](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket::Vytvořit](../mfc/reference/csocket-class.md#create)
