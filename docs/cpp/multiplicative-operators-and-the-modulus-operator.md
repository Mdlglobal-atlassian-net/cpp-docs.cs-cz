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
ms.openlocfilehash: bc6359d3d7d2045d44af07f80b3e101da356d4b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179351"
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

- Násobení (<strong>\*</strong>)

- Dělení ( **/** )

- Zbytek (zbytek z dělení) ( **%** )

Tyto binární operátory mají asociativitu zleva doprava.

Operátory násobení vezmou operandy aritmetických typů. Operátor zbytku ( **%** ) má přísnější požadavek v tom, že jeho operandy musí být integrálního typu. (Chcete-li získat zbytek dělení s plovoucí desetinnou čárkou, použijte funkci run-time [FMOD –](../c-runtime-library/reference/fmod-fmodf.md).) Převody zahrnuté ve [standardních převodech](standard-conversions.md) jsou aplikovány na operandy a výsledek je převedeného typu.

Operátor násobení dává výsledek vynásobení prvního operandu druhým.

Operátor dělení dává výsledek vydělení prvního operandu druhým.

Operátor zbytku vrací zbytek zadaný následujícím výrazem, kde *E1* je první operand a *E2* je druhý: *E1* -(*E1* / *E2*) \* *E2*, kde jsou oba operandy integrálního typu.

Dělení nulou ve výrazu dělení nebo zbytku není definováno a způsobí chybu modulu run-time. Následující výrazy proto způsobí nedefinované chybné výsledky:

```cpp
i % 0
f / 0.0
```

Pokud jsou oba operandy na výraz násobení, dělení, nebo zbytku mají stejné znaménko, výsledek je kladný. Jinak je výsledek záporný. Výsledek znaménka operace modulus je definován implementací.

> [!NOTE]
>  Vzhledem k tomu, že převody prováděné operátory násobení nepočítají s podmínkami přetečení nebo podtečení, informace se mohou ztratit, pokud výsledek operace násobení nelze reprezentovat v typu operandu po převodu.

**Specifické pro společnost Microsoft**

V programu Microsoft C++ výsledek výrazu zbytku je vždy stejný jako znaménko prvního operandu.

**Specifické pro konec Microsoftu**

Pokud je vypočítané dělení dvou celých čísel nepřesné a pouze jeden operand je záporný, výsledkem je největší celé číslo (v rozsahu bez ohledu na znaménko) menší než přesná hodnota, kterou by byla výsledkem operace dělení. Například vypočítaná hodnota-11/3 je-3,666666666. Výsledek tohoto integrálního dělení je-3.

Vztah mezi operátory multiplikativní je dán identitou (*e1* / *E2*) \* *e2* + *E1* % *E2* == *E1*.

## <a name="example"></a>Příklad

Následující program ukazuje operátory násobení. Všimněte si, že jeden operand `10 / 3` musí být explicitně převeden na typ **float** , aby se zabránilo zkrácení, aby oba operandy byly typu **float** před dělení.

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

## <a name="see-also"></a>Viz také

[Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Multiplikativní operátory jazyka C](../c-language/c-multiplicative-operators.md)
