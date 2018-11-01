---
title: Vztah k rozhraní API jazyka C
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: 8f58a33d3accb8eb81299877df1b0c8a4ebe0576
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525694"
---
# <a name="relationship-to-the-c-language-api"></a>Vztah k rozhraní API jazyka C

Jednu vlastnost, která nastavuje knihovny Microsoft Foundation Class (MFC) kromě jiných knihoven tříd pro Windows je velmi podobné mapování rozhraní Windows API, napsané v jazyce C. Kromě toho můžete obecně kombinovat volání knihovny tříd volně s přímými voláními rozhraní API Windows. Tento přímý přístup, ale neznamená, že třídy jsou o úplné nahrazení pro toto rozhraní API. Vývojáři musí stále příležitostně přímé volání některých funkcí Windows, jako [SetCursor](/windows/desktop/api/winuser/nf-winuser-setcursor) a [GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics), např. Funkce Windows je zabalena členskou funkci třídy pouze v případě, že je výhodu uděláte.

Protože je někdy potřeba vytvářet nativní volání funkce Windows, byste měli mít přístup k dokumentaci k rozhraní API jazyka C Windows. Tato dokumentace je součástí Microsoft Visual C++.

> [!NOTE]
>  Přehled fungování rozhraní knihovny MFC, naleznete v tématu [použití tříd pro zápis aplikace pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Viz také

[Obecná filozofie návrhu tříd](../mfc/general-class-design-philosophy.md)
