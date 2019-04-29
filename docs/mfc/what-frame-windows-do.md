---
title: Jak fungují okna s rámečkem
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], about frame windows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
ms.openlocfilehash: 594700ef1cbe0030bbe452adaa40b29b4a72f4d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405674"
---
# <a name="what-frame-windows-do"></a>Jak fungují okna s rámečkem

Kromě zobrazení jednoduše rámců, oken s rámečkem zodpovídají za mnoho úkolů, které jsou součástí koordinace rámec s jeho zobrazení a aplikace. [CMDIFrameWnd –](../mfc/reference/cmdiframewnd-class.md) a [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) dědí [CFrameWnd](../mfc/reference/cframewnd-class.md), takže mají `CFrameWnd` funkce, jakož i nové možnosti, které si přidají. Podřízená okna příklady zobrazení, ovládací prvky jako tlačítka a pole se seznamem a ovládacích panelů, včetně dialogové pruhy, panely nástrojů a stavové řádky.

Okno rámce zodpovídá za správu rozložení jeho podřízených oken. V rámci MFC okno rámce umístí libovolné ovládací pruhy, zobrazení a další podřízených oken v klientské oblasti.

Okno rámce také předá příkazy k jeho zobrazení a můžou reagovat na zprávy s oznámením ovládacího prvku systému Windows.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Ovládací pruhy (jak se vešly do okna rámce)](../mfc/control-bars.md)

- [Správa nabídek, ovládacích pruhů a akcelerátorů (jak se vešly do okna rámce)](../mfc/managing-menus-control-bars-and-accelerators.md)

- [Příkaz směrování (z okna rámce a jeho zobrazení a další cíle příkazů)](../mfc/command-routing.md)

- [Architektury dokument/View](../mfc/document-view-architecture.md)

- [Ovládací pruhy](../mfc/control-bars.md)

- [Ovládací prvky](../mfc/controls-mfc.md)

## <a name="see-also"></a>Viz také:

[Okna s rámečkem](../mfc/frame-windows.md)
