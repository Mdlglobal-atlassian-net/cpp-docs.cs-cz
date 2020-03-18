---
title: Vztah k rozhraní API jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: c52b11a7395e3972f8bf9d83501fbafb61e6f4a6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446384"
---
# <a name="relationship-to-the-c-language-api"></a>Vztah k rozhraní API jazyka C

Jediná vlastnost, která nastaví knihovnu knihovny MFC (Microsoft Foundation Class) kromě jiných knihoven tříd pro systém Windows, je velmi blízko mapování na rozhraní Windows API napsané v jazyce C. Kromě toho můžete obecně kombinovat volání knihovny tříd bez přímého volání rozhraní API systému Windows. Tento přímý přístup ale neznamená, že třídy jsou pro toto rozhraní API kompletní náhradou. Vývojáři musí stále občas dělat Přímá volání některých funkcí Windows, například [SetCursor](/windows/win32/api/winuser/nf-winuser-setcursor) a [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics), například. Funkce systému Windows je zabalena členskou funkcí třídy pouze v případě, že existuje jasná výhoda.

Vzhledem k tomu, že někdy potřebujete provádět nativní volání funkcí Windows, měli byste mít přístup k dokumentaci k rozhraní Windows API jazyka C-Language. Tato dokumentace je součástí Microsoft Visual C++.

> [!NOTE]
>  Přehled toho, jak architektura knihovny MFC funguje, najdete v tématu [použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Viz také

[Obecná filozofie návrhu tříd](../mfc/general-class-design-philosophy.md)
