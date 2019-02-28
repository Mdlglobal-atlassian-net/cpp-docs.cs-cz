---
title: Operátor podmíněného výrazu
ms.date: 11/04/2016
helpviewer_keywords:
- conditional operators
- operators [C++], conditional
- expressions [C++], conditional
ms.assetid: c4f1a5ca-0844-44a7-a384-eca584d4e3dd
ms.openlocfilehash: 9dc93a47d36af92fe370e3f56f504682d49bd1dd
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150620"
---
# <a name="conditional-expression-operator"></a>Operátor podmíněného výrazu

C má jeden Ternární operátor: operátor podmíněného výrazu (**?:**).

## <a name="syntax"></a>Syntaxe

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz logického OR* **?**   *výraz* **:** *podmíněného výrazu*

*Logického výrazu OR* musí mít typ integral, plovoucí nebo ukazatel. Vyhodnotí se z hlediska jeho ekvivalence na hodnotu 0. Následuje bod sekvence *logického výrazu OR*. Probíhá vyhodnocování operandů následujícím způsobem:

- Pokud *logického výrazu OR* není roven 0, *výraz* vyhodnocena. Výsledek vyhodnocení výrazu je dán neterminálu *výraz*. (To znamená, že *výraz* je vyhodnocen pouze v případě *logického výrazu OR* má hodnotu true.)

- Pokud *logického výrazu OR* rovná 0, *podmíněného výrazu* vyhodnocena. Výsledek výrazu je hodnota *podmíněného výrazu*. (To znamená, že *podmíněného výrazu* je vyhodnocen pouze v případě *logického výrazu OR* má hodnotu false.)

Všimněte si, že buď *výraz* nebo *podmíněného výrazu* je Vyhodnocená, ale ne obojí.

Typ výsledku podmíněné operace závisí na typu *výraz* nebo *podmíněného výrazu* operand, následujícím způsobem:

- Pokud *výraz* nebo *podmíněného výrazu* má integral nebo s plovoucí desetinnou čárkou typu (jejich typy mohou být jiné), operátor provádí běžné aritmetické převody. Typ výsledku je typ operandu po převodu.

- Pokud mají oba *výraz* a *podmíněného výrazu* stejnou strukturu, sjednocení nebo typ ukazatele, typ výsledku je stejný typ struktury, sjednocení nebo ukazatel.

- Pokud mají oba operandy typu `void`, výsledek je typu `void`.

- Pokud některý operand je ukazatel na objekt jakéhokoli typu, a druhý operand je ukazatel na `void`, ukazatele na objekt je převést na ukazatel na `void` a výsledkem je ukazatel na `void`.

- Pokud *výraz* nebo *podmíněného výrazu* ukazatel a druhý operand je konstantní výraz s hodnotou 0, typ výsledku je typ ukazatele.

Typ porovnání ukazatelů, jakýkoli typ kvalifikátory (**const** nebo `volatile`) v typu, na který ukazatel ukazuje jsou neplatné, ale typ výsledku kvalifikátory dědí z obou součásti zásad správy.

## <a name="examples"></a>Příklady

Následující příklady ukazují způsoby použití podmíněného operátoru:

```
j = ( i < 0 ) ? ( -i ) : ( i );
```

Tento příklad přiřadí absolutní hodnota `i` k `j`. Pokud `i` je menší než 0, `-i` přiřazen `j`. Pokud `i` je větší než nebo rovno 0, `i` přiřazen `j`.

```
void f1( void );
void f2( void );
int x;
int y;
    .
    .
    .
( x == y ) ? ( f1() ) : ( f2() );
```

V tomto příkladu dvě funkce `f1` a `f2`a dvě proměnné, `x` a `y`, jsou deklarovány. Dále v programu, pokud dvě proměnné, které mají stejnou hodnotu, funkce `f1` je volána. V opačném případě `f2` je volána.

## <a name="see-also"></a>Viz také:

[Podmíněný operátor: ?:](../cpp/conditional-operator-q.md)
