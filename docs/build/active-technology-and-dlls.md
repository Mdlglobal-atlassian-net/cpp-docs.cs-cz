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
ms.openlocfilehash: f67fb9548601ac705ceda08d20d3049f0bf1e0a5
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220998"
---
# <a name="active-technology-and-dlls"></a>Technologie Active a knihovny DLL

Technologie Active umožňuje, aby se Objektové servery kompletně implementovaly v rámci knihovny DLL. Tento typ serveru se nazývá procesový Server. Knihovna MFC zcela nepodporuje vnitroprocesové servery pro všechny funkce vizuálních úprav, hlavně protože aktivní technologie neposkytuje způsob, jak se server připojovat do hlavní smyčky zpráv kontejneru. Knihovna MFC vyžaduje přístup ke smyčce zpráv aplikace typu kontejner, aby bylo možné zpracovat klávesové zkratky a zpracování nečinného času.

Pokud vytváříte automatizační server a váš server nemá žádné uživatelské rozhraní, můžete server vytvořit v procesovém serveru a kompletně ho uložit do knihovny DLL.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Automatizační servery](../mfc/automation-servers.md)

## <a name="see-also"></a>Viz také

[Vytváření knihoven DLL jazyka C/C++ v aplikaci Visual Studio](dlls-in-visual-cpp.md)
