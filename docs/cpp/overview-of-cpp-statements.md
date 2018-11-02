---
title: Přehled příkazů jazyka C++
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++]
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
ms.openlocfilehash: 9493860087331ee2d8ff05a5c0bd59c7a46ad51a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676548"
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

Ve většině případů je syntaxe příkazu jazyka C++ shodná s ANSI C. Hlavní rozdíl mezi nimi je, že v jazyce C, deklarace jsou povolené jenom na začátku bloku; Přidá C++ *příkazu deklarace*, které toto omezení účinně odstraní. To umožňuje zavést proměnné v aplikaci na místě, kde lze vypočítat předzpracovanou inicializační hodnotu.

Deklarování proměnných uvnitř bloků také umožňuje vykonávat přesnou kontrolu rozsahu a životnosti těchto proměnných.

Témata příkazů popisují následující klíčová slova jazyka C++:

|||||
|-|-|-|-|
|[break](../cpp/break-statement-cpp.md)|[else](../cpp/if-else-statement-cpp.md)|[__if_exists –](../cpp/if-exists-statement.md)|[__try](../cpp/structured-exception-handling-c-cpp.md)|
|[case](../cpp/switch-statement-cpp.md)|[__except](../cpp/structured-exception-handling-c-cpp.md)|[__if_not_exists –](../cpp/if-not-exists-statement.md)|[Zkuste](../cpp/try-throw-and-catch-statements-cpp.md)|
|[catch](../cpp/try-throw-and-catch-statements-cpp.md)|[for](../cpp/for-statement-cpp.md)|[__leave](../c-language/try-finally-statement-c.md)|[while](../cpp/while-statement-cpp.md)|
|[continue](../cpp/continue-statement-cpp.md)|[goto](../cpp/goto-statement-cpp.md)|[return](../cpp/return-statement-cpp.md)||
|[default](../cpp/switch-statement-cpp.md)|[__finally](../cpp/structured-exception-handling-c-cpp.md)|[switch](../cpp/switch-statement-cpp.md)||
|[do](../cpp/do-while-statement-cpp.md)|[if](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||

## <a name="see-also"></a>Viz také:

[Příkazy](../cpp/statements-cpp.md)