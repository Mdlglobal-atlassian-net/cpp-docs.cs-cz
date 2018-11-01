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
ms.openlocfilehash: 75ff46a829bd129c7f73bf11a303a67ab1526969
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641113"
---
# <a name="sdi-and-mdi"></a>Rozhraní SDI a knihovna MDI

MFC usnadňuje práci s rozhraní jednoho dokumentu (SDI) a aplikace rozhraní více dokumentů (MDI).

Pouze jeden dokument otevřít okno rámce aplikace SDI povolit najednou. Aplikace MDI povolit více dokumentů, oken s rámečkem otevřené ve stejné instanci aplikace. Aplikace MDI má okno podřízených oken, které jsou oken s rámečkem v samotné, lze otevřít v rámci které více MDI, každá obsahuje samostatný dokument. V některých aplikacích může být podřízená okna různých typů, jako je například windows graf a tabulka windows. V takovém případě nabídek můžete změnit, protože se aktivují podřízených oken MDI různých typů.

> [!NOTE]
>  V části Windows 95 a později aplikace jsou obvykle SDI vzhledem k tomu, že operační systém přijala zobrazení "dokumentu střed".

Další informace najdete v tématu [dokumenty, zobrazení a Framework](../mfc/documents-views-and-the-framework.md).

## <a name="see-also"></a>Viz také

[Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
