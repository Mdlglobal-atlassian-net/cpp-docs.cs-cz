---
title: Rozhraní SDI a knihovna MDI
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
ms.openlocfilehash: 9730e7baf9589c4b05a60703c619aae2e941bdec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372760"
---
# <a name="sdi-and-mdi"></a>Rozhraní SDI a knihovna MDI

Knihovna MFC usnadňuje práci s aplikacemi rozhraní SDI (Single Document) i s rozhraním mdi (multiple-document).

Aplikace SDI umožňují současně pouze jedno otevřené okno rámce dokumentu. Aplikace MDI umožňují otevření více oken rámečků dokumentu ve stejné instanci aplikace. Aplikace MDI má okno, ve kterém lze otevřít více podřízených oken MDI, které jsou samotnými okny rámce, z nichž každá obsahuje samostatný dokument. V některých aplikacích mohou být podřízená okna různých typů, například okna grafu a okna tabulky. V takovém případě se řádek nabídek může změnit, jak jsou aktivována podřízená okna MDI různých typů.

> [!NOTE]
> V systému Windows 95 a novějších jsou aplikace obvykle SDI, protože operační systém přijal zobrazení "zaměřené na dokumenty".

Další informace naleznete v [tématu Dokumenty, zobrazení a rozhraní Framework](../mfc/documents-views-and-the-framework.md).

## <a name="see-also"></a>Viz také

[Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
