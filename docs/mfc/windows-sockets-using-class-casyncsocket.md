---
title: 'Windows Sockets: Použití třídy CAsyncSocket'
ms.date: 11/04/2016
f1_keywords:
- CAsyncSocket
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: 51274791393d95517bd8de5ae7248dc634018037
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399561"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets: Použití třídy CAsyncSocket

Tento článek vysvětluje, jak použít třídu [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Mějte na paměti, že tato třída zapouzdří rozhraní Windows Sockets API na velmi nízké úrovni. `CAsyncSocket` je určena pro programátory, kteří vědět síťovou komunikaci podrobně ale chcete pohodlí zpětná volání pro oznámení o událostech sítě. Podle tento předpoklad, tento článek obsahuje pouze základní instrukce. Pravděpodobně byste zvážit použití `CAsyncSocket` Pokud má Windows Sockets usnadnění řešení problémů s několika síťových protokolů v aplikaci knihovny MFC, ale nechtějí obětovat flexibilitu. Může také pocit, že můžete získat lepší efektivity tím, že další komunikace přímo sami než na kolik máte může pomocí modelu obecnější alternativní třídy `CSocket`.

`CAsyncSocket` dokumentovány v článku *odkaz knihovny MFC*. Visual C++ poskytuje také specifikace rozhraní Windows Sockets, nachází v sadě Windows SDK. Podrobnosti jsou ponechána na vás. Jazyk Visual C++ neposkytuje ukázkovou aplikaci pro `CAsyncSocket`.

Pokud nejsou vysoce informovanosti ohledně síťovou komunikaci a chcete jednoduché řešení, použijte třídu [csocket –](../mfc/reference/csocket-class.md) s `CArchive` objektu. Zobrazit [rozhraní Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md) Další informace.

Tento článek se týká:

- Vytváření a používání `CAsyncSocket` objektu.

- [Vaše odpovědnosti s CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> Vytváření a používání casyncsocket – objekt

#### <a name="to-use-casyncsocket"></a>Chcete-li použít CAsyncSocket

1. Vytvoření [CAsyncSocket](../mfc/reference/casyncsocket-class.md) objektu a použít objekt k vytvoření základního **SOKETU** zpracovat.

   Vytvoření soket má následující formát, MFC dvoufázová konstrukce.

   Příklad:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     -nebo-

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   První konstruktor výše uvedené vytvoří `CAsyncSocket` objekt v zásobníku. Druhý konstruktor vytvoří `CAsyncSocket` na haldě. První [vytvořit](../mfc/reference/casyncsocket-class.md#create) volání výše používá výchozí hodnoty parametrů k vytvoření soketu datového proudu. Druhá `Create` volání vytvoří datagram soketu se zadaný port a adresa. (Můžete použít buď `Create` verze pomocí některé z metod konstrukce.)

   Parametry tak, aby `Create` jsou:

   - "Portu": krátké celé číslo.

         For a server socket, you must specify a port. For a client socket, you typically accept the default value for this parameter, which lets Windows Sockets select a port.

   - Typ soketu: **SOCK_STREAM** (výchozí) nebo **SOCK_DGRAM**.

   - Soket "address" jako je například "ftp.microsoft.com" nebo "128.56.22.8".

         This is your Internet Protocol (IP) address on the network. You will probably always rely on the default value for this parameter.

   Podmínky "portu" a "adresa soketu" je podrobně popsaný v [rozhraní Windows Sockets: Porty a adresy soketů](../mfc/windows-sockets-ports-and-socket-addresses.md).

1. Pokud soketu je klient, připojení k serveru pro objekt soketu soketu, pomocí [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect).

     -nebo-

   Pokud soketu je server, nastavte soketu. Chcete-li začít naslouchání (s [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) pro pokusy o připojení z klienta. Při přijetí požadavku na připojení, přijměte ji [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

   Po přijetí připojení, můžete provádět úkoly, jako je ověřování hesla.

    > [!NOTE]
    >  `Accept` Členská funkce používá odkaz na nový, prázdný `CSocket` objektu jako svůj parametr. Je nutné vytvořit tento objekt před voláním `Accept`. Pokud tento objekt dostane mimo rozsah, připojení se ukončí. Nevolejte `Create` pro tento nový objekt soketu. Příklad najdete v článku [rozhraní Windows Sockets: Posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md).

1. Provádění komunikaci s jinými sokety voláním `CAsyncSocket` členské funkce objektu, které zapouzdřují funkce rozhraní Windows Sockets API.

   V tématu Specifikace rozhraní Windows Sockets a třída [CAsyncSocket](../mfc/reference/casyncsocket-class.md) v *odkaz knihovny MFC*.

1. Zničit `CAsyncSocket` objektu.

   Pokud jste vytvořili objekt soketu v zásobníku, jeho destruktor je volána, když obsahující funkce dostane mimo rozsah. Pokud jste vytvořili objekt soketu v haldě, pomocí **nové** operátoru, zodpovídáte za použití **odstranit** operátor zrušení objektu.

   Volá destruktor objektu [Zavřít](../mfc/reference/casyncsocket-class.md#close) členskou funkci před zničení objektu.

Příklad této sekvence v kódu (ve skutečnosti pro `CSocket` objektu), najdete v článku [rozhraní Windows Sockets: Posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md).

##  <a name="_core_your_responsibilities_with_casyncsocket"></a> Vaše odpovědnosti s CAsyncSocket

Při vytváření objektu třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), objekt zapouzdřuje Windows **SOKETU** zpracování a poskytuje operace na popisovače. Při použití `CAsyncSocket`, musí řešit všechny problémy, na které se může setkat při použití rozhraní API přímo. Příklad:

- "Blokování" scénáře.

- Rozdíly pořadí bajtů mezi odesílajícím a přijímajícím počítače.

- Převod mezi kódování Unicode a vícebajtových znaků sady (MBCS) řetězce.

Definice těchto podmínek a další informace naleznete v tématu [rozhraní Windows Sockets: Blokování](../mfc/windows-sockets-blocking.md), [rozhraní Windows Sockets: Pořadí bajtů](../mfc/windows-sockets-byte-ordering.md), [rozhraní Windows Sockets: Převádění řetězců](../mfc/windows-sockets-converting-strings.md).

Bez ohledu na tyto problémy třídy `CAsycnSocket` může být správnou volbou pro vás, pokud vaše aplikace vyžaduje všechny flexibility a kontroly můžete získat. Pokud ne, měli byste zvážit použití třídy `CSocket` místo. `CSocket` Skryje velké množství podrobností, které od vás: it čerpadel Windows zprávy během neblokují volání a získáte přístup k `CArchive`, která spravuje rozdíly pořadí bajtů a převodu řetězce za vás.

Další informace naleznete v tématu:

- [Windows Sockets: Podrobnosti](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sokety datového proudu](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramu](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také:

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)
