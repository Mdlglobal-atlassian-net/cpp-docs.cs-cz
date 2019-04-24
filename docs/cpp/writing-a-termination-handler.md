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
ms.openlocfilehash: f0b994075a8d59ce5d0955f10bf8c61d357d2db9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209465"
---
# <a name="writing-a-termination-handler"></a>Zápis obslužné rutiny ukončení

Na rozdíl od obslužné rutiny výjimky je obslužná rutina ukončení spuštěna vždy, bez ohledu na to, zda je chráněný blok kódu ukončen normálně. Jediným účelem obslužné rutiny ukončení by mělo být zajištění, že prostředky, jako například paměť, popisovače a soubory, jsou správně uzavřeny bez ohledu na to, jak část kódu dokončí provádění.

Obslužné rutiny ukončení používají příkaz try-finally.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Příkaz try-finally](../cpp/try-finally-statement.md)

- [Vymazání prostředků](../cpp/cleaning-up-resources.md)

- [Načasování akcí ve zpracování výjimek](../cpp/timing-of-exception-handling-a-summary.md)

- [Omezení obslužných rutin ukončení](../cpp/restrictions-on-termination-handlers.md)

## <a name="see-also"></a>Viz také:

[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)