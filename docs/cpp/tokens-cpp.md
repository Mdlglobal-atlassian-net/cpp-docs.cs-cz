---
title: Tokeny (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- tokens [C++]
- parsing, C++ tokens
- translation units
- white space, in C++ tokens
ms.assetid: aa812fd0-6d47-4f3f-aee0-db002ee4d8b9
ms.openlocfilehash: 1606df56191ec00ffea543dedd3fd4eda98d01c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330437"
---
# <a name="tokens-c"></a>Tokeny (C++)

Token je nejmenší prvek programu C++, který je smysluplný pro kompilátor. Analyzátor jazyka C++ rozpoznává tyto druhy tokenů: identifikátory, klíčová slova, literály, operátory, interpunkční znaky a jiné oddělovače. Proud těchto tokenů tvoří jednotku překladu.

Tokeny jsou odděleny obvykle *prázdných*. Prázdný znak může být jeden nebo jich může být více:

- Prázdné hodnoty

- Vodorovné nebo svislé tabulátory

- Nové řádky

- Zakončení stránky

- Komentáře

Analyzátor rozpozná klíčová slova, identifikátory, literály, operátory a interpunkční znaky. Informace o konkrétní typy tokenů, naleznete v tématu [klíčová slova](../cpp/keywords-cpp.md), [identifikátory](../cpp/identifiers-cpp.md), [číselné, logické a literály typu ukazatele](../cpp/numeric-boolean-and-pointer-literals-cpp.md), [řetězcové a znakové literály ](../cpp/string-and-character-literals-cpp.md), [Uživateli definované literály](../cpp/user-defined-literals-cpp.md), [integrované operátory C++, Priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md), a [interpunkční znaky](../cpp/punctuators-cpp.md). Prázdné místo je ignorován, s výjimkou podle potřeby k oddělení tokeny.

Tokeny předběžného zpracování se používají ve fázích předběžného zpracování k vygenerování tokenu stream předány kompilátoru. Předzpracování token kategorií jsou názvy záhlaví, identifikátory, předzpracování čísla, znakových literálů, řetězcové literály, operátory předběžného zpracování a interpunkční znaky a jednotlivé znaky prázdné znaky, které se neshodují s některou z jiných kategorií. Znakové a řetězcové literály se dá uživateli definované literály. Tokeny předzpracování mohou být odděleny prázdným znakem nebo komentáře.

Analyzátor oddělí tokeny ze vstupního datového proudu vytvořením nejdelšího možného tokenu použitím vstupních znaků při skenování zleva doprava. Prohlédněte si tento fragment kódu:

```cpp
a = i+++j;
```

Programátor, který kód vytvořil, mohl zamýšlet jeden z těchto dvou příkazů:

```cpp
a = i + (++j)

a = (i++) + j
```

Vzhledem k tomu, že analyzátor vytvoří ze vstupního proudu nejdelší možný token, zvolí druhý výklad, díky čemuž tokeny budou `i++`, `+` a `j`.

## <a name="see-also"></a>Viz také:

[Lexikální konvence](../cpp/lexical-conventions.md)