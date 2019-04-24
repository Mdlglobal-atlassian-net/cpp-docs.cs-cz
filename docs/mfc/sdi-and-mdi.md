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
ms.openlocfilehash: 725249e5a71e8ee097c641e5972e3cc8bb0e3e33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308527"
---
# <a name="sdi-and-mdi"></a>Rozhraní SDI a knihovna MDI

MFC usnadňuje práci s rozhraní jednoho dokumentu (SDI) a aplikace rozhraní více dokumentů (MDI).

Pouze jeden dokument otevřít okno rámce aplikace SDI povolit najednou. Aplikace MDI povolit více dokumentů, oken s rámečkem otevřené ve stejné instanci aplikace. Aplikace MDI má okno podřízených oken, které jsou oken s rámečkem v samotné, lze otevřít v rámci které více MDI, každá obsahuje samostatný dokument. V některých aplikacích může být podřízená okna různých typů, jako je například windows graf a tabulka windows. V takovém případě nabídek můžete změnit, protože se aktivují podřízených oken MDI různých typů.

> [!NOTE]
>  V části Windows 95 a později aplikace jsou obvykle SDI vzhledem k tomu, že operační systém přijala zobrazení "dokumentu střed".

Další informace najdete v tématu [dokumenty, zobrazení a Framework](../mfc/documents-views-and-the-framework.md).

## <a name="see-also"></a>Viz také:

[Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
