---
title: Zápis obslužné rutiny výjimek
ms.date: 11/04/2016
helpviewer_keywords:
- structured exception handling [C++], exception handlers
- exception handling [C++], exception handlers
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
ms.openlocfilehash: 201dcaa6a90584d1f9535df11d5722a37bdceb89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187281"
---
# <a name="writing-an-exception-handler"></a>Zápis obslužné rutiny výjimek

Obslužné rutiny výjimek se obvykle používají jako reakce na konkrétní chyby. Pomocí syntaxe zpracování výjimek lze odfiltrovat všechny výjimky kromě těch, u kterých víte, jak se mají zpracovat. Ostatní výjimky by měly být předány jiné obslužné rutině (případně v knihovně modulu runtime nebo operačního systému) napsané pro vyhledání těchto specifických výjimek.

Obslužné rutiny výjimek používají příkaz try-except.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Příkaz try-except](../cpp/try-except-statement.md)

- [Zápis filtru výjimek](../cpp/writing-an-exception-filter.md)

- [Vyvolávání výjimek softwaru](../cpp/raising-software-exceptions.md)

- [Výjimky hardwaru](../cpp/hardware-exceptions.md)

- [Omezení obslužných rutin výjimek](../cpp/restrictions-on-exception-handlers.md)

## <a name="see-also"></a>Viz také

[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
