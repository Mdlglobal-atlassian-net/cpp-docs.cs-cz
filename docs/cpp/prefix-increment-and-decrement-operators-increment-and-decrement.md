---
title: 'Operátory přírůstku a snížení předpony: ++ a --'
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- ++ operator [C++], prefix increment operators
- operators [C++], decrement
- -- operator [C++], prefix decrement operators [C++]
- operators [C++], increment
- decrement operators [C++], syntax
- decrement operators [C++]
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
ms.openlocfilehash: deb8acc6c6a68c9a97f2f0efbdc4084b4937df46
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606021"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Operátory přírůstku a snížení předpony: ++ a --

## <a name="syntax"></a>Syntaxe

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>Poznámky

Prefixový operátor Inkrementace (**++**) z nich se má jeho operand; přidá tuto hodnotu zvýšena je výsledek výrazu. Operand musí být l hodnota není typu **const**. Výsledkem je l hodnota stejného typu jako operand.

Operátor dekrementace předpony (**--**) je obdobou operátoru Inkrementace předponu, s tím rozdílem, že operand je sníží o jedna a výsledkem je tato hodnota odečítají.

**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): operand operátoru Inkrementace nebo dekrementace nemůže být typu **bool**.

Jak předpony a přípony přírůstek a snížení operátory ovlivnit jejich operandy. Klíčovým rozdílem mezi nimi je v tom pořadí, ve kterém zvýšení nebo snížení dojde při vyhodnocení výrazu. (Další informace najdete v tématu [operátory Příponové operátory Inkrementace a dekrementace](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md).) Ve formuláři předponu zvýšení nebo snížení dojde před hodnota bude použita ve vyhodnocení výrazu, tak hodnota tohoto výrazu se liší od hodnoty operandu. V příponový tvar zvýšení nebo snížení dojde po hodnota se používá ve vyhodnocení výrazu, takže hodnota výrazu je stejná jako hodnota operandu. Například následující program vytiskne "`++i = 6`":

```cpp
// expre_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   int i = 5;
   cout << "++i = " << ++i << endl;
}
```

Typ s plovoucí desetinnou čárkou nebo celočíselné operandy je zvýšena nebo snížena celočíselnou hodnotu 1. Typ výsledku je stejný jako typ operandu. Operand typu ukazatel, je zvýšena nebo snížena velikost objektu, který se zaměřuje. Zvýšena ukazatel odkazuje na další objekt. snížen ukazatel odkazuje na předchozí objekt.

Protože operátory Inkrementace a dekrementace mají vedlejší účinky, pomocí operátorů zvýšení nebo snížení v výrazy [preprocesor makro](../preprocessor/macros-c-cpp.md) může mít nežádoucí výsledky. Podívejte se například:

```cpp
// expre_Increment_and_Decrement_Operators2.cpp
#define max(a,b) ((a)<(b))?(b):(a)

int main()
{
   int i = 0, j = 0, k;
   k = max( ++i, j );
}
```

Makro rozšíří na:

```cpp
k = ((++i)<(j))?(j):(++i);
```

Pokud `i` je větší než nebo rovna hodnotě `j` nebo menší než `j` o 1, to se zvýší dvakrát.

> [!NOTE]
>  Vložených funkcí jazyka C++ jsou upřednostňovány vůči makra v mnoha případech, protože odstraňují vedlejší účinky, jako jsou zde popsané a povolit jazyk, který chcete provést podrobnější kontrolu typu.

## <a name="see-also"></a>Viz také:

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operátory inkrementace a dekrementace předpony](../c-language/prefix-increment-and-decrement-operators.md)