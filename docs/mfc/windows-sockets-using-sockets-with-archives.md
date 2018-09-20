---
title: 'Windows Sockets: Použití soketů s archivy | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 217dcd1d5e999ea640795c656bbf40f7adad3d7d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398742"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets: Použití soketů s archivy

Tento článek popisuje [csocket – programovací model](#_core_the_csocket_programming_model). Třída [csocket –](../mfc/reference/csocket-class.md) poskytuje podporu soketu na vyšší úrovni abstrakce než třída [CAsyncSocket](../mfc/reference/casyncsocket-class.md). `CSocket` používá verzi protokolu MFC serializace k předání dat do a z objekt soketu pomocí knihovny MFC [CArchive](../mfc/reference/carchive-class.md) objektu. `CSocket` poskytuje blokování (při správě zpracování na pozadí zpráv Windows) a umožňuje vám přístup k `CArchive`, která spravuje mnoho aspektů komunikaci, která budete muset provést sami pomocí nezpracované rozhraní API nebo třída `CAsyncSocket`.

> [!TIP]
>  Třídu lze použít `CSocket` samostatně jako pohodlnější verzi `CAsyncSocket`, ale je nejjednodušší programovací model použití `CSocket` s `CArchive` objektu.

Další informace o tom, jak implementaci soketů s archivy funguje, najdete v části [rozhraní Windows Sockets: jak sokety s archivy pracovní](../mfc/windows-sockets-how-sockets-with-archives-work.md). Příklad kódu naleznete v tématu [rozhraní Windows Sockets: posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md) a [rozhraní Windows Sockets: příklad z Sockets pomocí archivy](../mfc/windows-sockets-example-of-sockets-using-archives.md). Informace o některých funkcí můžete získat vaše vlastní třídy odvozené z tříd soketů, naleznete v tématu [rozhraní Windows Sockets: odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md).

> [!NOTE]
>  Při psaní aplikace knihovny MFC klienta ke komunikaci se servery zavedené (non-MFC) objektů jazyka C++ prostřednictvím archivu neodesílají. Pokud je server aplikace knihovny MFC, která analyzuje typy objektů, které chcete odeslat, nebude moci přijímat a deserializaci objektů. Související materiál o komunikaci s aplikacemi non-MFC také najdete v článku [rozhraní Windows Sockets: pořadí bajtů](../mfc/windows-sockets-byte-ordering.md).

##  <a name="_core_the_csocket_programming_model"></a> Csocket – programovací Model

Použití `CSocket` objekt zahrnuje vytvoření a přiřazení několik objektů tříd MFC dohromady. V následující obecný postup je každý krok provedenou serverového soketu a klientského soketu, s výjimkou kroku 3, ve kterém každý typ soketu vyžaduje jinou akci.

> [!TIP]
>  V době běhu serverová aplikace obvykle začíná nejprve připravené a "naslouchání", pokud klientská aplikace snaží o připojení. Pokud server není připraven, když se klient pokusí připojit, obvykle vyžadují uživatelská aplikace, zkuste to znovu později.

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>Chcete-li nastavit komunikaci mezi serverového soketu a klientského soketu

1. Vytvoření [csocket –](../mfc/reference/csocket-class.md) objektu.

1. Pomocí objektu k vytvoření základního **SOKETU** zpracovat.

     Pro `CSocket` objektu klienta, obvykle, abyste používali výchozí parametry [vytvořit](../mfc/reference/casyncsocket-class.md#create), pokud potřebujete datagram soketu. Pro `CSocket` objekt serveru, je nutné zadat port v `Create` volání.

    > [!NOTE]
    >  `CArchive` nefunguje s sokety datagramu. Pokud chcete použít `CSocket` pro datagram soketu, je nutné použít třídu jako `CAsyncSocket`, to znamená bez archivu. Protože datagramy nespolehlivé (není zaručeno, že můžete přejít a může opakovat nebo mimo pořadí), nejsou kompatibilní s serializace prostřednictvím archivu. Očekáváte, že serializace operace dokončete spolehlivě a v pořadí. Pokud se pokusíte použít `CSocket` s `CArchive` objekt pro datagram, MFC kontrolní výraz selže.

1. Soket je klient, kontaktujte [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect) připojovaný objekt soketu serverového soketu.

     -nebo-

     Pokud soketu je na serveru, zavolejte [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen) zahájíte pokusů o naslouchá pro připojení z klienta. Při přijetí požadavku na připojení, přijmout tak, že volání [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

    > [!NOTE]
    >  `Accept` Členská funkce používá odkaz na nový, prázdný `CSocket` objektu jako svůj parametr. Je nutné vytvořit tento objekt před voláním `Accept`. Pokud tento objekt dostane mimo rozsah, připojení se ukončí. Nevolejte `Create` pro tento nový objekt soketu.

1. Vytvoření [csocketfile –](../mfc/reference/csocketfile-class.md) objektu, přidružení `CSocket` objektu s ním.

1. Vytvoření [CArchive](../mfc/reference/carchive-class.md) objekt pro načítání (přijímání) nebo ukládání dat (odesílání). Archiv je přidružené k `CSocketFile` objektu.

     Mějte na paměti, která `CArchive` nefunguje s sokety datagramu.

1. Použití `CArchive` objekt k předávání dat mezi klientem a serverem sokety.

     Mějte na paměti, který danou `CArchive` objekt přesouvá data jenom v jednom směru: buď pro načítání (přijímání) nebo ukládání (odesílání). V některých případech budete používat dvě `CArchive` objekty: jeden pro odesílání dat, druhou pro příjem potvrzení.

     Po přijetí připojení a nastavení archiv, můžete provádět úkoly, jako je ověřování hesla.

1. Zničte archivu, soubor soketu a objekty soketu.

    > [!NOTE]
    >  Třída `CArchive` poskytuje `IsBufferEmpty` členskou funkci speciálně pro použití s třídou `CSocket`. Pokud vyrovnávací paměť obsahuje více dat zpráv, například budete muset opakovat, dokud všechny z nich se čtou a vyrovnávací paměť je zrušeno. V opačném případě další oznámení, že jsou data pro další přijetí může být jsou odložené na neurčito. Použití `IsBufferEmpty` , aby zajistil, že můžete načíst všechna data.

Tento článek [rozhraní Windows Sockets: posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md) ukazuje obě strany tohoto procesu s ukázkovým kódem.

Další informace naleznete v tématu:

- [Windows Sockets: Sokety streamu](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket::Create](../mfc/reference/csocket-class.md#create)

