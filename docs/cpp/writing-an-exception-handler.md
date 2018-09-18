---
title: Zápis obslužné rutiny výjimek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], exception handlers
- exception handling [C++], exception handlers
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8956bb673c756224a886dede90cf23d84c3f20c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050967"
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