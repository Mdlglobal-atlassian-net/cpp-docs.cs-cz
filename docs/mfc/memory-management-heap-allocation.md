---
title: 'Správa paměti: Přidělení haldy'
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC], detecting leaks
- delete operator [MFC], using with debug MFC
- heap allocation [MFC], described
- memory allocation [MFC], heap memory
- memory leaks [MFC], detecting
- new operator [MFC], using with debug MFC
- heap allocation [MFC]
- detecting memory leaks [MFC]
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
ms.openlocfilehash: 0c669fa611193b9a04e4854c84dec604e585991c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641152"
---
# <a name="memory-management-heap-allocation"></a>Správa paměti: Přidělení haldy

Haldy je vyhrazený pro potřeby přidělování paměti programu. To je oblast kromě programového kódu a zásobníku. Typické programů jazyka C pomocí funkce **malloc** a **bezplatné** přidělit a uvolnit paměť haldy. Ladicí verze knihovny MFC poskytuje upravenou verzí integrované operátory C++ **nové** a **odstranit** přidělit a uvolnit objekty v paměti haldy.

Při použití **nové** a **odstranit** místo **malloc** a **bezplatné**, budete moct využít výhod knihovny tříd Správa paměti ladění rozšíření, které mohou být užitečné při zjištění nevracení paměti. Při sestavení programu s prodejní verze knihovny MFC, standardní verze **nové** a **odstranit** operátory poskytovat účinný způsob, jak přidělit a uvolnit paměť (verzi knihovny MFC neposkytuje upravené verze těchto operátorů).

Mějte na paměti, celková velikost objektů přidělených do je omezen pouze váš systém dostupná virtuální paměť.

## <a name="see-also"></a>Viz také

[Správa paměti](../mfc/memory-management.md)

