---
title: Operátor podmíněného výrazu
ms.date: 11/04/2016
helpviewer_keywords:
- conditional operators
- operators [C++], conditional
- expressions [C++], conditional
ms.assetid: c4f1a5ca-0844-44a7-a384-eca584d4e3dd
ms.openlocfilehash: a64317c75e48111148053cc7efb62fb5a6d79f7f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749191"
---
# <a name="conditional-expression-operator"></a>Operátor podmíněného výrazu

C má jeden Ternární operátor: operátor podmíněného výrazu (**?:**).

## <a name="syntax"></a>Syntaxe

*podmíněný výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz or*  **?**  *výraz*  **:**  *podmíněný výraz*

*Logický operátor OR* musí mít typ integrál, float nebo Pointer. Vyhodnotí se v souvislosti s jeho rovnocenným ekvivalentem 0. Bod sekvence se řídí *logickým výrazem or*. Vyhodnocení operandů pokračuje následujícím způsobem:

- Pokud *logický výraz or* není rovno 0, je vyhodnocen *výraz* . Výsledek vyhodnocení výrazu je dán nekonečným *výrazem*. (To znamená, že *výraz* je vyhodnocen pouze v případě, že je *logická hodnota nebo výraz* true.)

- Pokud se *logický operátor OR* rovná 0, je vyhodnocen *podmíněný výraz* . Výsledek výrazu je hodnota *podmíněného výrazu*. (To znamená, že *podmíněný výraz* je vyhodnocen pouze v případě, že *logický-nebo-Expression* je false.)

Všimněte si, že je vyhodnocen buď *výraz* , nebo *podmíněný výraz* , ale ne obojí.

Typ výsledku podmíněné operace závisí na typu *výrazu* nebo operandu *podmíněného výrazu* , a to následujícím způsobem:

- Pokud má *výraz* nebo *podmíněný výraz* celočíselný nebo plovoucí typ (jejich typy mohou být rozdílné), operátor provádí běžné aritmetické převody. Typ výsledku je typ operandů po převodu.

- Pokud má *výraz* i *podmíněný výraz* stejnou strukturu, sjednocení nebo typ ukazatele, typ výsledku je stejný typ struktury, sjednocení nebo ukazatele.

- Pokud oba operandy mají typ `void`, výsledek je typu `void`.

- Pokud je jeden z operandů ukazatel na objekt libovolného typu a druhý operand je ukazatel na `void`, je ukazatel na objekt převeden na ukazatel na `void` a výsledek je ukazatel na. `void`

- Pokud je *výraz* nebo *podmíněný výraz* ukazatel a druhý operand je konstantní výraz s hodnotou 0, typ výsledku je typ ukazatele.

V porovnání s typem pro ukazatele mají jakékoli kvalifikátory typu (**const** nebo `volatile`) v typu, na který ukazatele ukazatelů jsou nevýznamné, ale výsledný typ dědí kvalifikátory z obou komponent podmíněného.

## <a name="examples"></a>Příklady

Následující příklady ukazují použití podmíněného operátoru:

```
j = ( i < 0 ) ? ( -i ) : ( i );
```

Tento příklad přiřadí absolutní hodnotu `i` k. `j` Pokud `i` je menší než 0, `-i` je přiřazeno `j`. Pokud `i` je větší než nebo rovno 0, `i` je přiřazeno `j`.

```cpp
void f1( void );
void f2( void );
int x;
int y;
    .
    .
    .
( x == y ) ? ( f1() ) : ( f2() );
```

V tomto příkladu jsou deklarovány dvě `f1` funkce `f2`, a a dvě proměnné `x` a `y`. Pokud mají dvě proměnné stejnou hodnotu, je funkce `f1` volána později v programu. V opačném případě `f2` se zavolá.

## <a name="see-also"></a>Viz také

[Podmíněný operátor: ?:](../cpp/conditional-operator-q.md)
