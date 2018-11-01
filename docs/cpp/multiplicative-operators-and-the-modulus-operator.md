---
title: Multiplikativní operátory a operátor numerického zbytku
ms.date: 11/04/2016
f1_keywords:
- '%'
- /
helpviewer_keywords:
- operators [C++], multiplicative
- arithmetic operators [C++], multiplicative operators
- modulus operator [C++]
- '* operator'
- division operator [C++], multiplicative operators
- '% operator'
- multiplication operator [C++], multiplicative operators
- multiplicative operators [C++]
- division operator
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
ms.openlocfilehash: d3f52e8ed2f631c93672ae74cf04b86910d1d185
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430846"
---
# <a name="multiplicative-operators-and-the-modulus-operator"></a>Multiplikativní operátory a operátor numerického zbytku

## <a name="syntax"></a>Syntaxe

```
expression * expression 
expression / expression 
expression % expression
```

## <a name="remarks"></a>Poznámky

Operátory násobení jsou:

- Násobení (<strong>\**</strong>)

- Dělení (**/**)

- Modulo (zbytek po dělení) (**%**)

Tyto binární operátory mají asociativitu zleva doprava.

Operátory násobení vezmou operandy aritmetických typů. Operátor numerického zbytku (**%**) má přísnější požadavky v tom, že jeho operandy musí být celočíselného typu. (Chcete-li získat zbytek po dělení s pohyblivou čárkou, použijte funkci run-time [fmod](../c-runtime-library/reference/fmod-fmodf.md).) Převody uvedené v [standardní převody](standard-conversions.md) jsou použity na operandy a výsledek je určen převedeným typem.

Operátor násobení dává výsledek vynásobení prvního operandu druhým.

Operátor dělení dává výsledek vydělení prvního operandu druhým.

Operátor numerického zbytku vrací zbytek daný následujícím výrazem, kde *e1* je první operand a *e2* je druhý: *e1* -(*e1*  /  *e2*) \* *e2*, kde jsou oba operandy integrální typy.

Dělení nulou ve výrazu dělení nebo zbytku není definováno a způsobí chybu modulu run-time. Následující výrazy proto způsobí nedefinované chybné výsledky:

```cpp
i % 0
f / 0.0
```

Pokud jsou oba operandy na výraz násobení, dělení, nebo zbytku mají stejné znaménko, výsledek je kladný. Jinak je výsledek záporný. Výsledek znaménka operace modulus je definován implementací.

> [!NOTE]
>  Vzhledem k tomu, že převody prováděné operátory násobení nepočítají s podmínkami přetečení nebo podtečení, informace se mohou ztratit, pokud výsledek operace násobení nelze reprezentovat v typu operandu po převodu.

**Specifické pro Microsoft**

V programu Microsoft C++ výsledek výrazu zbytku je vždy stejný jako znaménko prvního operandu.

**Specifické pro END Microsoft**

Pokud je vypočítané dělení dvou celých čísel nepřesné a pouze jeden operand je záporný, výsledkem je největší celé číslo (v rozsahu bez ohledu na znaménko) menší než přesná hodnota, kterou by byla výsledkem operace dělení. Například vypočítaná hodnota -11 / 3 je-3.666666666. Výsledek tohoto dělení celých čísel je -3.

Vztah mezi operátory násobení je dán identitou (*e1* / *e2*) \* *e2*  +  *e1* % *e2* == *e1*.

## <a name="example"></a>Příklad

Následující program ukazuje operátory násobení. Všimněte si, že každý operand `10 / 3` musí být explicitně přetypován na typ **float** aby se zabránilo zkrácení, takže oba operandy jsou typu **float** před dělení.

```cpp
// expre_Multiplicative_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   int x = 3, y = 6, z = 10;
   cout  << "3 * 6 is " << x * y << endl
         << "6 / 3 is " << y / x << endl
         << "10 % 3 is " << z % x << endl
         << "10 / 3 is " << (float) z / x << endl;
}
```

## <a name="see-also"></a>Viz také:

[Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Multiplikativní operátory jazyka C](../c-language/c-multiplicative-operators.md)