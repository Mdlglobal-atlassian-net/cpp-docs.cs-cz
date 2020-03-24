---
title: Přehled příkazů jazyka C++
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++]
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
ms.openlocfilehash: 9aba5deddca6fbf480cd9d573606b16b7ab047db
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188425"
---
# <a name="overview-of-c-statements"></a>Přehled příkazů jazyka C++

Příkazy jazyka C++ jsou spouštěny postupně, s výjimkou případů, kdy příkaz výrazu, příkaz výběru, příkaz iterace nebo příkaz jump konkrétně upravuje danou sekvenci.

Příkazy mohou být následujících typů:

```
labeled-statement
expression-statement
compound-statement
selection-statement
iteration-statement
jump-statement
declaration-statement
try-throw-catch
```

Ve většině případů je syntaxe C++ příkazu shodná se specifikací ANSI C. Hlavní rozdíl mezi těmito dvěma možnostmi je, že deklarace v jazyce C jsou povoleny pouze na začátku bloku; C++ přidá *příkaz deklarace*, který efektivně odstraní toto omezení. To umožňuje zavést proměnné v aplikaci na místě, kde lze vypočítat předzpracovanou inicializační hodnotu.

Deklarování proměnných uvnitř bloků také umožňuje vykonávat přesnou kontrolu rozsahu a životnosti těchto proměnných.

Témata příkazů popisují následující klíčová slova jazyka C++:

|||||
|-|-|-|-|
|[break](../cpp/break-statement-cpp.md)|[ostatních](../cpp/if-else-statement-cpp.md)|[__if_exists](../cpp/if-exists-statement.md)|[__try](../cpp/structured-exception-handling-c-cpp.md)|
|[case](../cpp/switch-statement-cpp.md)|[__except](../cpp/structured-exception-handling-c-cpp.md)|[__if_not_exists](../cpp/if-not-exists-statement.md)|[Zkuste](../cpp/try-throw-and-catch-statements-cpp.md)|
|[catch](../cpp/try-throw-and-catch-statements-cpp.md)|[for](../cpp/for-statement-cpp.md)|[__leave](../c-language/try-finally-statement-c.md)|[while](../cpp/while-statement-cpp.md)|
|[continue](../cpp/continue-statement-cpp.md)|[goto](../cpp/goto-statement-cpp.md)|[return](../cpp/return-statement-cpp.md)||
|[default](../cpp/switch-statement-cpp.md)|[__finally](../cpp/structured-exception-handling-c-cpp.md)|[switch](../cpp/switch-statement-cpp.md)||
|[do](../cpp/do-while-statement-cpp.md)|[Přestože](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||

## <a name="see-also"></a>Viz také

[Příkazy](../cpp/statements-cpp.md)
