---
title: 'Operátory sčítání: + a -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- operators [C++], addition
- subtraction operator [C++], additive operators
- + operator [C++], additive operators
- additive operators [C++]
- arithmetic operators [C++], additive operators
- '- operator [C++], additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
ms.openlocfilehash: 2601debb0a21c4ab9cdcedb25b26085a1aff0a1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370200"
---
# <a name="additive-operators--and--"></a>Operátory sčítání: + a -

## <a name="syntax"></a>Syntaxe

```
expression + expression
expression - expression
```

## <a name="remarks"></a>Poznámky

Mezi aditivní operátory patří:

- Sčítání**+**( )

- Odčítání**-**( )

Tyto binární operátory mají asociativitu zleva doprava.

Aditivní operátory přebírají operandy aritmetických typů nebo typů ukazatele. Výsledkem operátoru**+** sčítání ( ) je součet operandů. Výsledkem operátoru odčítání (**-**) je rozdíl mezi operandy. Jsou-li jeden nebo oba operandy ukazateli, musí být ukazateli na objekt, nikoli na funkce. Jsou-li oba operandy ukazateli, nedávají výsledky smysl, pokud nebudou oba operandy ukazateli na objekty stejného pole.

Aditivní operátory mají operandy *aritmetické*, *integrální*a *skalární* typy. Ty jsou definovány v následující tabulce.

### <a name="types-used-with-additive-operators"></a>Typy použité spolu s aditivními operátory

|Typ|Význam|
|----------|-------------|
|*Aritmetické*|Celočíselné typy a typy s plovoucí desetinnou čárkou se společně nazývají „aritmetické“ typy.|
|*Integrální*|Typy char a int všech velikostí (long, short) a výčty jsou „celočíselné“ typy.|
|*Skalár*|Skalární operandy jsou operandy aritmetického typu nebo typu ukazatele.|

Platnými kombinacemi pro tyto operátory jsou:

*aritmetické* + *aritmetiky*

*skalární* + *integrál*

*integrální* + *skalární*

*aritmetické* - *aritmetiky*

*skalární* - *skalární*

Všimněte si, že sčítání a odčítání nejsou ekvivalentními operacemi.

Pokud jsou oba operandy aritmetické typu, převody uvedené v [standardní převody](standard-conversions.md) jsou použity na operandy a výsledek je převedeného typu.

## <a name="example"></a>Příklad

```cpp
// expre_Additive_Operators.cpp
// compile with: /EHsc
#include <iostream>
#define SIZE 5
using namespace std;
int main() {
   int i = 5, j = 10;
   int n[SIZE] = { 0, 1, 2, 3, 4 };
   cout  << "5 + 10 = " << i + j << endl
         << "5 - 10 = " << i - j << endl;

   // use pointer arithmetic on array

   cout << "n[3] = " << *( n + 3 ) << endl;
}
```

## <a name="pointer-addition"></a>Přidání ukazatele

Pokud je jeden z operandů při operaci sčítání ukazatelem na pole objektů, ostatní musí být celočíselného typu. Výsledkem je ukazatel, který je stejného typu jako původní ukazatel a odkazuje na jiný prvek pole. Tento koncept dokládá následující příklad části kódu:

```cpp
short IntArray[10]; // Objects of type short occupy 2 bytes
short *pIntArray = IntArray;

for( int i = 0; i < 10; ++i )
{
    *pIntArray = i;
    cout << *pIntArray << "\n";
    pIntArray = pIntArray + 1;
}
```

Přestože je celočíselná hodnota 1 přičtena k ukazateli `pIntArray`, neznamená to „přičíst 1 k adrese“, spíše znamená „nastavit ukazatel na další objekt v poli“, který je 2 bajty (nebo `sizeof( int )`) daleko.

> [!NOTE]
> Kód ve tvaru `pIntArray = pIntArray + 1` se v programech jazyka C++ nachází jen zřídka. K provedení zvýšení jsou vhodnější tvary `pIntArray++` nebo `pIntArray += 1`.

## <a name="pointer-subtraction"></a>Odečtení ukazatele

Jsou-li oba operandy ukazateli, výsledek odčítání je rozdíl (v prvcích pole) mezi operandy. Výraz odčítání poskytuje podepsaný integrální výsledek typu `ptrdiff_t` \<(definovaný ve standardním include file stddef.h>).

Jeden z operandů může být celočíselného typu, pokud jde o druhý operand. Výsledek odčítání je stejného typu jako původní ukazatel. Hodnota odčítání je ukazatel na element (*n* - *i*)th pole, kde *n* je prvek, na který odkazuje původní ukazatel a *i* je integrální hodnota druhého operandu.

## <a name="see-also"></a>Viz také

[Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operátory sčítání jazyka C](../c-language/c-additive-operators.md)
