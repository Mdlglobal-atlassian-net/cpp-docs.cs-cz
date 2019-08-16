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
ms.openlocfilehash: 44a4838a1cd863bd484701966a156be9f61f8988
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510625"
---
# <a name="windows-sockets-in-mfc"></a>Windows sockets v prostředí MFC

> [!NOTE]
>  Knihovna MFC podporuje rozhraní Windows Sockets 1, ale nepodporuje rozhraní [Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2). Rozhraní Windows Sockets 2 jsou poprvé dodávána se systémem Windows 98 a jsou součástí verze Windows 2000.

Knihovna MFC poskytuje dva modely pro psaní síťových komunikačních programů pomocí rozhraní Windows Sockets, které jsou součástí dvou tříd knihovny MFC. Tento článek popisuje tyto modely a další podrobnosti o podpoře soketů MFC. "Zásuvkou" je koncový bod komunikace: objekt, přes který vaše aplikace komunikuje s jinými aplikacemi rozhraní Windows Sockets v síti.

Informace o soketech Windows, včetně vysvětlení konceptu soketu, najdete v [tématu rozhraní Windows Sockets: Pozadí](../mfc/windows-sockets-background.md).

##  <a name="_core_sockets_programming_models"></a>Programovací modely soketů

Oba knihovny MFC rozhraní Windows Sockets jsou podporovány následujícími třídami:

- `CAsyncSocket`

   Tato třída zapouzdřuje rozhraní Windows Sockets API. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) je pro programátory, kteří znají síťové programování a chtějí pružně programovat přímo s rozhraním API soketů, ale také chtějí pohodlí funkcí zpětného volání pro oznamování událostí sítě. Kromě soketů pro balíčky v objektově orientovaném formuláři pro C++použití v je jediná další abstrakce této třídy, která převádí určité zprávy systému Windows související s sokety na zpětná volání. Další informace najdete v tématu [Windows Sockets: Oznámení](../mfc/windows-sockets-socket-notifications.md)soketu.

- `CSocket`

   Tato třída odvozená z `CAsyncSocket`obsahuje větší abstrakci úrovně pro práci s sokety prostřednictvím objektu [CArchive](../mfc/reference/carchive-class.md) knihovny MFC. Použití soketu s archivem se významně podobá použití protokolu serializace souborů knihovny MFC. To usnadňuje použití než `CAsyncSocket` model. [CSocket –](../mfc/reference/csocket-class.md) zdědí mnoho členských funkcí z `CAsyncSocket` těchto zapouzdřených rozhraní API Windows Sockets. budete muset použít některé z těchto funkcí a obecně porozumět programování soketů. Ale `CSocket` spravuje mnoho aspektů komunikace, které byste museli provádět pomocí nezpracovaného rozhraní API nebo třídy `CAsyncSocket`. Nejdůležitější je, `CSocket` že poskytuje blokování (se zpracováním zpráv systému Windows na pozadí), které je nezbytné pro synchronní `CArchive`operaci.

Vytváření a používání `CSocket` objektů `CAsyncSocket` a jsou popsány v [tématu Windows Sockets: Použití soketů s](../mfc/windows-sockets-using-sockets-with-archives.md) archivy a [Windows Sockets: Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).

##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Windows Sockets dll

Operační systémy Microsoft Windows poskytují knihovny DLL (Dynamic-Link Library) rozhraní Windows Sockets. Vizuál C++ poskytuje příslušné hlavičkové soubory a knihovny a specifikaci rozhraní Windows Sockets.

Další informace o Windows Sockets najdete v těchto tématech:

- [Windows Sockets: Sokety datového proudu](../mfc/windows-sockets-stream-sockets.md)

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
