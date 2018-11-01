---
title: if – příkaz (C)
ms.date: 11/04/2016
f1_keywords:
- else
- if
helpviewer_keywords:
- if keyword [C]
- else clauses
- else keyword [C]
- if keyword [C], if statement syntax
- nested statements
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
ms.openlocfilehash: 3561bcb4edde35b72c6db801f5c32f3f0cfdf6fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555035"
---
# <a name="if-statement-c"></a>if – příkaz (C)

**Pokud** příkaz ovládá podmíněné větvení. Text **Pokud** je proveden příkaz, pokud je hodnota výrazu nenulovou hodnotu. Syntaxe **Pokud** příkaz má dva formuláře.

## <a name="syntax"></a>Syntaxe

*příkaz výběru*: **Pokud (**  *výraz*  **)**  *–příkaz*

**Pokud (**  *výraz*  **)**  *příkaz*  **else**  *– příkaz* 

V obou formách příkazu **Pokud** prohlášení, výrazy, které může mít libovolnou hodnotu, s výjimkou struktury, jsou vyhodnocovány, včetně všech vedlejších účinků.

V první forma syntaxe Pokud *výraz* hodnotu true (nenulovou), *příkaz* provádí. Pokud *výraz* má hodnotu false, *příkaz* se ignoruje. Ve druhé formě syntaxe, která používá **else**, druhý *příkaz* se spustí, pokud *výraz* má hodnotu false. S obě formy ovládací prvek pak předá z **Pokud** příkaz dalšímu příkazu v programu Pokud obsahuje některý z příkazů **přerušení**, **pokračovat**, nebo `goto`.

Následují příklady **Pokud** – příkaz:

```
if ( i > 0 )
    y = x / i;
else
{
    x = i;
    y = f( x );
}
```

V tomto příkladu příkaz `y = x/i;` se spustí, pokud `i` je větší než 0. Pokud `i` je menší než nebo rovno 0, `i` přiřazen `x` a `f( x )` přiřazen `y`. Všimněte si, že příkaz tvořící **Pokud** klauzule končí středníkem.

Při vnoření **Pokud** příkazy a **else** klauzule, pomocí složených závorek k seskupení příkazů a klauzule do složených příkazů, které objasňují vaším záměrem. Pokud neexistují žádné složené závorky, přeloží kompilátor nejednoznačnosti tím, že přidružíte každý **else** k nejbližšímu **Pokud** , která nemá **else**.

```
if ( i > 0 )           /* Without braces */
    if ( j > i )
        x = j;
    else
        x = i;
```

**Else** klauzule souvisí s vnitřní **Pokud** příkaz v tomto příkladu. Pokud `i` je menší než nebo rovna 0, není přiřazena žádná hodnota pro `x`.

```
if ( i > 0 )
{                      /* With braces */
    if ( j > i )
        x = j;
}
else
    x = i;
```

Složené závorky kolem vnitřního **Pokud** proveďte příkaz v tomto příkladu **else** část klauzule vnějšího **Pokud** příkaz. Pokud `i` je menší než nebo rovno 0, `i` přiřazen `x`.

## <a name="see-also"></a>Viz také

[if-else – příkaz (C++)](../cpp/if-else-statement-cpp.md)