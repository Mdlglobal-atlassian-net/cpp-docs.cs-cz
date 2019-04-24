---
title: Zápis obslužné rutiny výjimek
ms.date: 11/04/2016
helpviewer_keywords:
- structured exception handling [C++], exception handlers
- exception handling [C++], exception handlers
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
ms.openlocfilehash: 6f1bcecf3aaed2bf2b7ebbe511f11cdb5ec1ca5e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209400"
---
# <a name="writing-an-exception-handler"></a>Zápis obslužné rutiny výjimek

Obslužné rutiny výjimek se obvykle používají jako reakce na konkrétní chyby. Pomocí syntaxe zpracování výjimek lze odfiltrovat všechny výjimky kromě těch, u kterých víte, jak se mají zpracovat. Ostatní výjimky by měly být předány jiné obslužné rutině (případně v knihovně modulu runtime nebo operačního systému) napsané pro vyhledání těchto specifických výjimek.

Obslužné rutiny výjimek používají příkaz try-except.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Try-except – příkaz](../cpp/try-except-statement.md)

- [Zápis filtru výjimek](../cpp/writing-an-exception-filter.md)

- [Vyvolávání výjimek softwaru](../cpp/raising-software-exceptions.md)

- [Výjimky hardwaru](../cpp/hardware-exceptions.md)

- [Omezení obslužných rutin výjimek](../cpp/restrictions-on-exception-handlers.md)

## <a name="see-also"></a>Viz také:

[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)