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
ms.openlocfilehash: 0949eba769bed33da8fe39bb41500a2ba02af224
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602147"
---
# <a name="using-c-or-c-in-asm-blocks"></a>Použití jazyka C nebo C++ v blocích __asm

** Specifické pro Microsoft **

Protože pokyny vložené sestavení lze kombinovat s příkazy jazyka C nebo C++, mohou odkazovat na proměnné jazyka C nebo C++ podle názvu a použít mnoho prvků z těchto jazyků.

`__asm` Blok můžete použít následující prvky jazyka:

- Symboly, včetně popisků a názvů proměnných a funkcí

- Konstanty, včetně Symbolické konstanty a `enum` členy

- Makra a preprocesor – direktivy

- Komentáře (obojí __/ \* \* /__ a __//__ )

- Zadejte jména (všude, kde typ MASM bude právní)

- `typedef` názvy, které se obecně používají s operátory, jako **PTR** a **typ** nebo chcete-li určit členy struktury nebo sjednocení

V rámci `__asm` blok, můžete určit celočíselné konstanty s zápis v jazyce C nebo zápis základ číselné soustavy assembler (0x100 a 100 h jsou ekvivalentní, například). To vám umožňuje definovat (pomocí `#define`) konstanta v jazyce C a používat ho v části programu jazyka C nebo C++ a sestavení. Můžete také určit konstanty v osmičkové před s 0. Například 0777 určuje osmičkové konstanty.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Používání operátorů v blocích __asm](../../assembler/inline/using-operators-in-asm-blocks.md)

- [Pomocí jazyka C nebo C++ Symbols_in bloků __asm](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [Přístup k datům jazyka C nebo C++ v blocích __asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [Zápis funkcí s vloženým sestavením](../../assembler/inline/writing-functions-with-inline-assembly.md)

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>
