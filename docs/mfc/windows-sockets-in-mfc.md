---
title: Windows sockets v prostředí MFC
ms.date: 11/04/2016
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
ms.openlocfilehash: 9992d2054c04eea1b3b63d591601acf0091acb5e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266780"
---
# <a name="windows-sockets-in-mfc"></a>Windows sockets v prostředí MFC

> [!NOTE]
>  MFC podporuje Windows Sockets 1, ale nepodporuje [Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2). Windows Sockets 2 nejprve součástí Windows 98 a verze systému Windows 2000.

Knihovna MFC poskytuje dva modely pro psaní programů síťové komunikace pomocí rozhraní Windows Sockets, součástí dvě třídy knihovny MFC. Tento článek popisuje tyto modely a podpora soketů podrobnosti knihovny MFC. "Soket" je koncový bod komunikace: objekt, jehož prostřednictvím aplikace komunikuje s jinými aplikacemi Windows Sockets přes síť.

Informace o rozhraní Windows Sockets, včetně vysvětlení konceptu soketu, naleznete v tématu [rozhraní Windows Sockets: Pozadí](../mfc/windows-sockets-background.md).

##  <a name="_core_sockets_programming_models"></a> Sokety programovací modely

Dva Windows soketů knihovny MFC programovací modely jsou podporovány následující třídy:

- `CAsyncSocket`

   Tato třída zapouzdří rozhraní Windows Sockets API. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) je pro programátory, kteří vědět síťové programování a chtějí flexibilně využívat přímé programování soketů rozhraní API, ale také chcete pohodlné funkce zpětného volání pro oznámení o událostech sítě. Než balení soketů ve formuláři objektově orientované pro použití v jazyce C++, je převod jedinými dodatečnými abstrakce, kterou tato třída poskytuje některé zprávy související s soketu Windows na zpětná volání. Další informace najdete v tématu [rozhraní Windows Sockets: Soketu oznámení](../mfc/windows-sockets-socket-notifications.md).

- `CSocket`

   Tato třída odvozená z `CAsyncSocket`, poskytuje vyšší úroveň abstrakce pro práci s sockets pomocí knihovny MFC [CArchive](../mfc/reference/carchive-class.md) objektu. Použití soketu se archiv výrazně se podobá pomocí protokolu serializace soubor knihovny MFC. To usnadňuje použití než `CAsyncSocket` modelu. [Csocket –](../mfc/reference/csocket-class.md) dědí mnoho funkcí členů z `CAsyncSocket` zapouzdřují rozhraní Windows Sockets API, budete muset použít některé z těchto funkcí a pochopit obecně programování soketů. Ale `CSocket` spravuje mnoho aspektů komunikaci, která budete muset provést sami pomocí nezpracované rozhraní API nebo třída `CAsyncSocket`. Co je nejdůležitější `CSocket` poskytuje blokování (s zpracování na pozadí zpráv Windows), což je nezbytné pro synchronní operace `CArchive`.

Vytváření a používání `CSocket` a `CAsyncSocket` objekty je popsána v [rozhraní Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md) a [rozhraní Windows Sockets: Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).

##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Windows Sockets – knihovny DLL

Operační systémy Microsoft Windows zadat rozhraní Windows Sockets dynamické knihovny (DLL). Visual C++ poskytuje vhodné záhlaví souborů a knihoven a specifikace rozhraní Windows Sockets.

Další informace o rozhraní Windows Sockets naleznete v tématu:

- [Windows Sockets: Stream Sockets](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramu](../mfc/windows-sockets-datagram-sockets.md)

- [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Sockets: Příklady soketů využívajících archivy](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets: Jak pracují sokety s archivy](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Oznámení soketů](../mfc/windows-sockets-socket-notifications.md)

- [Windows Sockets: Blokování](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: Pořadí bajtů](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: Převádění řetězců](../mfc/windows-sockets-converting-strings.md)

- [Windows Sockets: Porty a adresy soketů](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>Viz také:

[Rozhraní Windows Sockets](../mfc/windows-sockets.md)
