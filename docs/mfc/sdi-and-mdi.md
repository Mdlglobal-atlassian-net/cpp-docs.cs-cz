---
title: Rozhraní SDI a knihovna MDI | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8189af7939bfca0fd206fa72892098e373444879
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401443"
---
# <a name="sdi-and-mdi"></a>Rozhraní SDI a knihovna MDI

MFC usnadňuje práci s rozhraní jednoho dokumentu (SDI) a aplikace rozhraní více dokumentů (MDI).

Pouze jeden dokument otevřít okno rámce aplikace SDI povolit najednou. Aplikace MDI povolit více dokumentů, oken s rámečkem otevřené ve stejné instanci aplikace. Aplikace MDI má okno podřízených oken, které jsou oken s rámečkem v samotné, lze otevřít v rámci které více MDI, každá obsahuje samostatný dokument. V některých aplikacích může být podřízená okna různých typů, jako je například windows graf a tabulka windows. V takovém případě nabídek můžete změnit, protože se aktivují podřízených oken MDI různých typů.

> [!NOTE]
>  V části Windows 95 a později aplikace jsou obvykle SDI vzhledem k tomu, že operační systém přijala zobrazení "dokumentu střed".

Další informace najdete v tématu [dokumenty, zobrazení a Framework](../mfc/documents-views-and-the-framework.md).

## <a name="see-also"></a>Viz také

[Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
