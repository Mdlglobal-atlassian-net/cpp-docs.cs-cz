---
title: Použití jazyka C nebo C++ v blocích __asm | Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96ed46cdf44ccacee806dd03bf7eacca26eec32d
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120940"
---
# <a name="using-c-or-c-in-asm-blocks"></a>Použití jazyka C nebo C++ v blocích __asm

** Microsoft konkrétní **

Protože vloženého sestavení pokynů můžete kombinovat s příkazy jazyka C nebo C++, můžou odkazují na proměnné jazyka C nebo C++ podle názvu a používat mnoho dalších prvků tyto jazyky.

`__asm` Bloku můžete použít následující prvky jazyka:

- Symboly, včetně popisků a názvy proměnné a funkcí

- Konstanty, včetně symbolický konstanty a `enum` členy

- Makra a preprocesor – direktivy

- Komentáře (obě __/ \* \* /__ a __//__ )

- Zadejte názvy (kdekoli typu MASM by právní)

- `typedef` názvy, které se obvykle používá s operátory, jako **PTR** a **typu** nebo k určení členů struktury nebo sjednocení

V rámci `__asm` blok, můžete zadat celočíselné konstanty zápis v jazyce C nebo assembleru základ – zápis (0x100 a 100 h ekvivalentní, jsou například). To umožňuje definovat (pomocí `#define`) konstanta v jazyce C a použít ho v části C nebo C++ a sestavení programu. Můžete také zadat konstanty v osmičková tak, že před jejich s 0. Například 0777 určuje osmičková konstanta.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?

- [Používání operátorů v blocích __asm](../../assembler/inline/using-operators-in-asm-blocks.md)

- [Použití jazyka C nebo C++ Symbols_in blocích __asm](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [Přístup k datům jazyka C nebo C++ v blocích __asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [Zápis funkcí s vloženým sestavením](../../assembler/inline/writing-functions-with-inline-assembly.md)

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)
