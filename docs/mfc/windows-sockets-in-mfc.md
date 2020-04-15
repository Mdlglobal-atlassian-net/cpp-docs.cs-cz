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
ms.openlocfilehash: 8e5562b028d3d9b7cba4b47716b63fd1392c514f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371100"
---
# <a name="windows-sockets-in-mfc"></a>Windows sockets v prostředí MFC

> [!NOTE]
> Knihovna MFC podporuje rozhraní Windows Sockets 1, ale nepodporuje [rozhraní Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2). Windows Sockets 2 byl poprvé dodán se systémem Windows 98 a je součástí systému Windows 2000.

Knihovna MFC dodává dva modely pro zápis síťových komunikačních programů se zásuvky Windows, které jsou součástí dvou tříd knihovny MFC. Tento článek popisuje tyto modely a další podrobnosti podpora soketů knihovny MFC. "Soket" je koncový bod komunikace: objekt, jehož prostřednictvím aplikace komunikuje s jinými aplikacemi Windows Sockets v síti.

Informace o náboži systému Windows, včetně vysvětlení konceptu soketu, naleznete v tématu [Windows Sockets: Background](../mfc/windows-sockets-background.md).

## <a name="sockets-programming-models"></a><a name="_core_sockets_programming_models"></a>Programyovací modely soketů

Dva programovací modely rozhraní MFC Windows Sockets jsou podporovány následujícími třídami:

- `CAsyncSocket`

   Tato třída zapouzdřuje rozhraní API rozhraní Windows Sockets. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) je určen pro programátory, kteří znají programování v síti a chtějí flexibilitu programování přímo do rozhraní API soketů, ale také chtějí pohodlí funkcí zpětného volání pro oznámení síťových událostí. Jiné než obalové sokety v objektově orientované podobě pro použití v jazyce C++ je jedinou další abstrakcí, kterou tato třída poskytuje, převod určitých zpráv systému Windows souvisejících se soketem na zpětná volání. Další informace naleznete v tématu [Windows Sockets: Socket Notifications](../mfc/windows-sockets-socket-notifications.md).

- `CSocket`

   Tato třída, odvozená z `CAsyncSocket`, poskytuje abstrakce vyšší úrovně pro práci s sokety prostřednictvím objektu [CArchive](../mfc/reference/carchive-class.md) knihovny MFC. Použití soketu s archivem se velmi podobá použití protokolu serializace souborů knihovny MFC. To usnadňuje použití než `CAsyncSocket` model. [CSocket](../mfc/reference/csocket-class.md) dědí mnoho `CAsyncSocket` členských funkcí z tohoto zapouzdření rozhraní API rozhraní Windows Sockets; budete muset použít některé z těchto funkcí a pochopit sockets programování obecně. Ale `CSocket` spravuje mnoho aspektů komunikace, které byste museli udělat sami pomocí `CAsyncSocket`buď raw API nebo třídy . A co `CSocket` je nejdůležitější, poskytuje blokování (se zpracováním zpráv systému `CArchive`Windows na pozadí), což je nezbytné pro synchronní provoz .

Vytváření a `CSocket` `CAsyncSocket` používání objektů a objektů je popsáno v [části Zásuvky systému Windows: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md) a [soketů systému Windows: Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).

## <a name="windows-sockets-dlls"></a><a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Knihovny DLL rozhraní Windows Sockets

Operační systémy Microsoft Windows poskytují knihovny dll (DLL) rozhraní Windows Sockets. Visual C++ poskytuje příslušné soubory hlaviček a knihovny a specifikace Windows Sockets.

Další informace o nástrčcích systému Windows naleznete v tématu:

- [Windows Sockets: Sokety datového proudu](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)

- [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Sockets: Příklady soketů využívajících archivy](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets: Jak pracují sokety s archivy](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Oznámení soketů](../mfc/windows-sockets-socket-notifications.md)

- [Windows Sockets: Blokování](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: Pořadí bajtů](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: Převádění řetězců](../mfc/windows-sockets-converting-strings.md)

- [Windows Sockets: Porty a adresy soketů](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>Viz také

[Rozhraní Windows Sockets](../mfc/windows-sockets.md)
