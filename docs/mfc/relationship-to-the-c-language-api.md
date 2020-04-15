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
ms.openlocfilehash: 1fbd4d332f5ade1cb9415448b138ac5bc838307d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372831"
---
# <a name="relationship-to-the-c-language-api"></a>Vztah k rozhraní API jazyka C

Jedinou vlastností, která nastavuje knihovnu třídy Microsoft Foundation (MFC) na rozdíl od jiných knihoven tříd pro Windows, je velmi blízké mapování rozhraní API systému Windows napsané v jazyce C. Dále můžete obecně kombinovat volání do knihovny tříd volně s přímýmvoláním rozhraní API systému Windows. Tento přímý přístup však neznamená, že třídy jsou úplnou náhradou za toto rozhraní API. Vývojáři musí stále občas provádět přímé volání na některé funkce systému Windows, jako je [například SetCursor](/windows/win32/api/winuser/nf-winuser-setcursor) a [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics). Funkce systému Windows je zabalena členovou funkcí třídy pouze v případě, že je jasná výhoda.

Vzhledem k tomu, že někdy potřebujete volat nativní funkce systému Windows, měli byste mít přístup k dokumentaci rozhraní API jazyka C. Tato dokumentace je součástí aplikace Microsoft Visual C++.

> [!NOTE]
> Přehled fungování architektury knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny naleznete [v tématu Použití tříd k zápisu aplikací pro windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Viz také

[Obecná filozofie návrhu tříd](../mfc/general-class-design-philosophy.md)
