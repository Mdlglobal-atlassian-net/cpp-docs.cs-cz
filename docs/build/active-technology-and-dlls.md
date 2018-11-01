---
title: Technologie Active a knihovny DLL
ms.date: 11/04/2016
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
ms.openlocfilehash: 270c64df9af792a73acf1ad408aca02e7fadc30f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535808"
---
# <a name="active-technology-and-dlls"></a>Technologie Active a knihovny DLL

Technologie Active umožňuje objektových serverů uvnitř knihovny DLL úplnou implementaci. Tento typ serveru je volána v procesový server. MFC nepodporuje zcela vnitroprocesové servery pro úpravy s náhledem, všechny funkce hlavně, protože technologie Active neposkytuje způsob, jak integrovat do kontejneru hlavní smyčka zpráv serveru. MFC vyžaduje přístup k smyčky zpráv aplikace typu kontejner pro zpracování přístupové klávesy a doby nečinnosti zpracování.

Pokud píšete automatizační server a server nemá žádné uživatelské rozhraní, můžete nastavit váš server v procesový server a kompletně umístit do knihovny DLL.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Automatizační servery](../mfc/automation-servers.md)

## <a name="see-also"></a>Viz také

[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)