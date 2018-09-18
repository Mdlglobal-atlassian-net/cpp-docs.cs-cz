---
title: Zápis obslužné rutiny ukončení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85241d9dde87e929b02328a6e7d0c75b5ce068ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116227"
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