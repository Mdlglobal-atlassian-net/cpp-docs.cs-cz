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

C má jeden ternární operátor: operátor podmíněného výrazu (**? :**).

## <a name="syntax"></a>Syntaxe

*podmíněný výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický-OR-výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický-NEBO výraz?***?**    *výraz*  **:**  *podmíněný výraz*

*Logický výraz OR* musí mít integrální, plovoucí nebo ukazatel typu. Vyhodnocuje se z hlediska rovnocennosti 0. Bod sekvence následuje *za logickým výrazem OR*. Hodnocení operandů probíhá takto:

- Pokud *logický výraz OR* není rovna 0, je vyhodnocen *výraz.* Výsledek vyhodnocení výrazu je dán neterminálním *výrazem*. (To *znamená,* že výraz je vyhodnocen pouze *v případě, že* je splněn logický výraz OR.)

- Pokud *se logický výraz OR* rovná 0, je vyhodnocen podmíněný *výraz.* Výsledkem výrazu je hodnota *podmíněného výrazu*. (To znamená, že *podmíněný výraz* je vyhodnocen pouze v *případě, že je logický výraz OR* nepravdivý.)

Všimněte si, že je vyhodnocen *výraz* nebo *podmíněný výraz,* ale ne obojí.

Typ výsledku podmíněné operace závisí na typu *výrazu* nebo operandu *podmíněného výrazu* takto:

- Pokud *výraz* nebo *podmíněný výraz* má integrální nebo plovoucí typ (jejich typy se mohou lišit), operátor provádí obvyklé aritmetické převody. Typ výsledku je typ operandů po převodu.

- Pokud *výraz* i *podmíněný výraz* mají stejnou strukturu, sjednocení nebo typ ukazatele, je typ výsledku stejný typ struktury, sjednocení nebo ukazatele.

- Pokud oba operandy `void`mají typ `void`, výsledek má typ .

- Pokud buď operand je ukazatel na objekt libovolného typu a druhý `void`operand je ukazatel na , ukazatel `void` na objekt je `void`převeden na ukazatel a výsledkem je ukazatel na .

- Pokud *je výraz* nebo *podmíněný výraz* ukazatel a druhý operand je konstantní výraz s hodnotou 0, typ výsledku je typ ukazatele.

V porovnání typů pro ukazatele všechny kvalifikátory typu (**const** nebo `volatile`) v typu, na který jsou body ukazatele nevýznamné, ale typ výsledku dědí kvalifikátory z obou součástí podmíněného.

## <a name="examples"></a>Příklady

Následující příklady ukazují použití podmíněného operátoru:

```
j = ( i < 0 ) ? ( -i ) : ( i );
```

Tento příklad přiřazuje absolutní hodnotu `i` . `j` Pokud `i` je menší `-i` než 0, je přiřazen . `j` Pokud `i` je větší než nebo `i` rovno `j`0, je přiřazen .

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

V tomto příkladu `f1` jsou `f2`deklarovány `x` dvě `y`funkce a , a dvě proměnné a , a . Později v programu, pokud dvě proměnné mají stejnou `f1` hodnotu, je volána funkce. V `f2` opačném případě se nazývá.

## <a name="see-also"></a>Viz také

[Podmíněný operátor: ?:](../cpp/conditional-operator-q.md)
