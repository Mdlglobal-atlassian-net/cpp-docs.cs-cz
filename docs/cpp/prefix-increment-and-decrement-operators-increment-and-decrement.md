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
ms.openlocfilehash: ce066a3349d56b278739f586fe851b020da78885
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366225"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Operátory přírůstku a snížení předpony: ++ a --

## <a name="syntax"></a>Syntaxe

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>Poznámky

Operátor přírůstku předpony**++**( ) přidá jeden do svého operandu; tato přírůstající hodnota je výsledkem výrazu. Operand musí být hodnota l, která není typu **const**. Výsledkem je hodnota l stejného typu jako operand.

Operátor snížení předpony (**--**) je analogický operátoru přírůstek předpony, s tím rozdílem, že operand je snížen o jeden a výsledkem je tato snížená hodnota.

**Visual Studio 2017 verze 15.3 a novější** (k dispozici s [/std:c++17):](../build/reference/std-specify-language-standard-version.md)Operand operátor u přírůstek nebo snížení nemusí být typu **bool**.

Operátory přírůstek předpony i přípony a snížení ovlivňují jejich operandy. Klíčovým rozdílem mezi nimi je pořadí, ve kterém se při hodnocení výrazu uskutečňuje přírůstek nebo úbytek. (Další informace naleznete v tématu [Postfix Přírůstek a Dekrement operátory](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md).) Ve formuláři předpony dojde k přírůstku nebo snížení před použitím hodnoty v vyhodnocení výrazu, takže hodnota výrazu se liší od hodnoty operandu. Ve formuláři přípony dojde k přírůstku nebo snížení po použití hodnoty v vyhodnocení výrazu, takže hodnota výrazu je stejná jako hodnota operandu. Například následující program vytiskne "`++i = 6`":

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

Operand integrálního nebo plovoucího typu se zintáží nebo sníží o celou hodnotu 1. Typ výsledku je stejný jako typ operandu. Operand typu ukazatele je zvětšován nebo snížen velikostí objektu, který řeší. Zpřísněný ukazatel odkazuje na další objekt; dekreed ukazatel odkazuje na předchozí objekt.

Vzhledem k tomu, že operátory přírůstek a snížení mají vedlejší účinky, může mít použití výrazů s operátory přírůstek nebo snížení v [makru preprocesoru](../preprocessor/macros-c-cpp.md) nežádoucí výsledky. Vezměme si tento příklad:

```cpp
// expre_Increment_and_Decrement_Operators2.cpp
#define max(a,b) ((a)<(b))?(b):(a)

int main()
{
   int i = 0, j = 0, k;
   k = max( ++i, j );
}
```

Makro se rozbalí na:

```cpp
k = ((++i)<(j))?(j):(++i);
```

Pokud `i` je větší nebo `j` rovno `j` nebo menší než 1, bude se zvýší dvakrát.

> [!NOTE]
> Vslaných funkcí jazyka C++ jsou v mnoha případech vhodnější než makra, protože eliminují vedlejší účinky, jako jsou zde popsané, a umožňují jazyku provádět úplnější kontrolu typu.

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operátory inkrementace a dekrementace předpony](../c-language/prefix-increment-and-decrement-operators.md)
