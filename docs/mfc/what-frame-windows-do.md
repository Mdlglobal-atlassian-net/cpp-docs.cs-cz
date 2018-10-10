---
title: Co dělat rámce Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], about frame windows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf97fb086f9ede43f9679e66a7c917b800f97dc8
ms.sourcegitcommit: e4a690bf33b44432179de0bc537e26616d13c553
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48892186"
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

## <a name="see-also"></a>Viz také

[Okna s rámečkem](../mfc/frame-windows.md)

