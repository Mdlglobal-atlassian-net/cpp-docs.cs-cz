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
ms.openlocfilehash: b6df50d483a6e2958de3100a07c18b89b0c4f12f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233057"
---
# <a name="if-statement-c"></a>if – příkaz (C)

Příkaz **if** řídí podmíněné větvení. Tělo příkazu **if** je provedeno, pokud je hodnota výrazu nenulová. Syntaxe příkazu **if** má dva formuláře.

## <a name="syntax"></a>Syntaxe

*Selection – příkaz*: **if (***Expression***)**–*příkaz*      

**if**–*příkaz* *výrazu***)***statement***Else**          

V obou formách příkazu **if** jsou vyhodnoceny výrazy, které mohou mít libovolnou hodnotu kromě struktury, včetně všech vedlejších účinků.

V první formě syntaxe, pokud je *výraz* true (nenulový), je proveden *příkaz* . Pokud je *výraz* false, *příkaz* se ignoruje. V druhé formě syntaxe, která používá **jiný**, je spuštěn druhý *příkaz* , pokud je *výraz* nepravdivý. Pomocí obou forem ovládací prvek předává z příkazu **if** do dalšího příkazu v programu, pokud některý z příkazů neobsahuje **přerušení**, **pokračování**nebo `goto`.

Níže jsou uvedeny příklady příkazu **if** :

```
if ( i > 0 )
    y = x / i;
else
{
    x = i;
    y = f( x );
}
```

V tomto příkladu je příkaz `y = x/i;` proveden, pokud `i` je větší než 0. Pokud `i` `i` je menší nebo rovno 0, je přiřazena `x` `f( x )` k. `y` Všimněte si, že příkaz, který tvoří klauzuli **if** , končí středníkem.

Při vnořování v klauzulích klauzule a **Else** použijte závorky k **seskupení příkazů a** klauzulí do složených příkazů, které objasňují svůj záměr. Pokud nejsou k dispozici žádné složené závorky, kompilátor vyřeší nejednoznačnost přiřazením každého **dalšího** k nejbližšímu, **Pokud** nemá **jiný**.

```
if ( i > 0 )           /* Without braces */
    if ( j > i )
        x = j;
    else
        x = i;
```

Klauzule **Else** je přidružená k vnitřnímu příkazu **if** v tomto příkladu. Pokud `i` je menší nebo rovno 0, není přiřazena žádná hodnota `x`.

```
if ( i > 0 )
{                      /* With braces */
    if ( j > i )
        x = j;
}
else
    x = i;
```

Složené závorky sousedící s vnitřním příkazem **if** v tomto příkladu vedou k části klauzule **Else** vnějšího příkazu **if** . Pokud `i` je menší nebo rovno 0, `i` je přiřazeno. `x`

## <a name="see-also"></a>Viz také

[if-else – příkaz (C++)](../cpp/if-else-statement-cpp.md)
