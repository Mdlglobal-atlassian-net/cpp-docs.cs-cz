---
title: Zápis obslužné rutiny ukončení
ms.date: 11/04/2016
helpviewer_keywords:
- structured exception handling [C++], termination handlers
- exceptions [C++], terminating
- termination handlers [C++], writing
- handlers [C++]
- handlers [C++], termination
- termination handlers
- exception handling [C++], termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
ms.openlocfilehash: 8a243281e0d984a42cd4b4d9f249d867812d8bca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187307"
---
# <a name="writing-a-termination-handler"></a>Zápis obslužné rutiny ukončení

Na rozdíl od obslužné rutiny výjimky je obslužná rutina ukončení spuštěna vždy, bez ohledu na to, zda je chráněný blok kódu ukončen normálně. Jediným účelem obslužné rutiny ukončení by mělo být zajištění, že prostředky, jako například paměť, popisovače a soubory, jsou správně uzavřeny bez ohledu na to, jak část kódu dokončí provádění.

Obslužné rutiny ukončení používají příkaz try-finally.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Příkaz try-finally](../cpp/try-finally-statement.md)

- [Čištění prostředků](../cpp/cleaning-up-resources.md)

- [Časování akcí při zpracování výjimek](../cpp/timing-of-exception-handling-a-summary.md)

- [Omezení obslužných rutin ukončení](../cpp/restrictions-on-termination-handlers.md)

## <a name="see-also"></a>Viz také

[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
