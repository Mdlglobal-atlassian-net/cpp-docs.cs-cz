---
title: Použití jazyka C nebo C++ v blocích __asm
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, mixing instructions with C/C++ statements
- symbols, in __asm blocks
- macros, __asm blocks
- preprocessor directives, used in __asm blocks
- type names, used in __asm blocks
- preprocessor directives
- preprocessor, directives
- constants, in __asm blocks
- comments, in __asm blocks
- typedef names, used in __asm blocks
- __asm keyword [C++], C/C++ elements in
ms.assetid: ae8b2b52-6b75-42e3-ac0c-ad02d922ed97
ms.openlocfilehash: 16b298b92a4ba40d9091499a1821ad4f3c413d6c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854521"
---
# <a name="using-c-or-c-in-__asm-blocks"></a>Použití jazyka C nebo C++ v blocích __asm

**Specifické pro společnost Microsoft**

Vzhledem k tomu, že instrukce vloženého sestavení mohou C++ být smíchány s příkazy jazyka c nebo C++ , mohou odkazovat na jazyk c nebo proměnné podle názvu a použít mnoho dalších prvků těchto jazyků.

Blok `__asm` může používat následující prvky jazyka:

- Symboly, včetně popisků a názvů proměnných a funkcí

- Konstanty, včetně symbolických konstant a `enum` členů

- Makra a direktivy preprocesoru

- Komentáře ( __/\* \*/__ a __//__ )

- Názvy typů (všude, kde by byl typ MASM přípustný)

- názvy `typedef` obecně používané s operátory jako **PTR** a **Type** nebo k určení členů struktury nebo sjednocení

V rámci `__asm` bloku můžete zadat celočíselné konstanty pomocí zápisu C nebo notace assembleru (0x100 a 100h jsou ekvivalentní, například). To umožňuje definovat (pomocí `#define`) konstantu v jazyce C a pak ji použít v částech programu C nebo C++ i sestavení. Můžete také zadat konstanty v osmičkových čísla, které předchází 0. Například 0777 určuje osmičkovou konstantu.

## <a name="what-do-you-want-to-know-more-about"></a>O čem chcete vědět více?

- [Používání operátorů v blocích __asm](../../assembler/inline/using-operators-in-asm-blocks.md)

- [Použití bloků jazyka C++ C nebo Symbols_in __asm](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [Přístup k datům jazyka C nebo C++ v blocích __asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [Zápis funkcí s vloženým sestavením](../../assembler/inline/writing-functions-with-inline-assembly.md)

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>
