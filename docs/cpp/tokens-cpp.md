---
title: TokenyC++()
ms.date: 11/04/2016
helpviewer_keywords:
- tokens [C++]
- parsing, C++ tokens
- translation units
- white space, in C++ tokens
ms.assetid: aa812fd0-6d47-4f3f-aee0-db002ee4d8b9
ms.openlocfilehash: cd104b7308716ca182374bbff2df61731c84d574
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376252"
---
# <a name="tokens-c"></a>TokenyC++()

Token je nejmenší prvek programu C++, který je smysluplný pro kompilátor. Analyzátor jazyka C++ rozpoznává tyto druhy tokenů: identifikátory, klíčová slova, literály, operátory, interpunkční znaky a jiné oddělovače. Proud těchto tokenů tvoří jednotku překladu.

Tokeny jsou obvykle odděleny *prázdným znakem*. Prázdný znak může být jeden nebo jich může být více:

- Prázdné hodnoty

- Vodorovné nebo svislé tabulátory

- Nové řádky

- Informační kanály formuláře

- Komentáře

Analyzátor rozpozná klíčová slova, identifikátory, literály, operátory a interpunkční znaky. Informace o konkrétních typech tokenů naleznete v [tématu Klíčová slova](../cpp/keywords-cpp.md), [identifikátory](../cpp/identifiers-cpp.md), [číselné, logické a literály ukazatelů](../cpp/numeric-boolean-and-pointer-literals-cpp.md), [řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md), uživatelsky [definované literály](../cpp/user-defined-literals-cpp.md), [ C++ předdefinované operátory, Priority a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)a [interpunkční znaky](../cpp/punctuators-cpp.md). Prázdné znaky jsou ignorovány, s výjimkou požadavků na samostatné tokeny.

Tokeny předběžného zpracování se používají ve fázích předzpracování ke generování streamu tokenu předaného kompilátoru. Kategorie tokenu předběžného zpracování jsou názvy hlaviček, identifikátory, předzpracovaná čísla, literály znaků, řetězcové literály, operátory předzpracování a interpunkční znaky a jednoduché neprázdné znaky, které se neshodují s jednou z ostatních kategorií. Literály znaků a řetězce můžou být uživatelsky definované literály. Tokeny předběžného zpracování mohou být odděleny mezerami nebo komentáři.

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