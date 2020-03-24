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
ms.openlocfilehash: 32c210961c4966bb7b2cbcc597bd3c99f0d6ed24
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177661"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Operátory přírůstku a snížení předpony: ++ a --

## <a name="syntax"></a>Syntaxe

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>Poznámky

Operátor přírůstku předpony ( **++** ) přidá jeden k jeho operandu; Tato zvýšená hodnota je výsledkem výrazu. Operand musí být l-hodnota, která není typu **const**. Výsledkem je l-hodnota stejného typu jako operand.

Operátor snížení předpony ( **--** ) je podobný operátoru příznaku přírůstku s tím rozdílem, že operand je snížen o jednu a výsledkem je tato snížená hodnota.

**Visual Studio 2017 verze 15,3 a novější** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): Operand operátoru Increment nebo snížení nesmí být typu **bool**.

Operátory i modifikátor přípona i přípona mají vliv na jejich operandy. Klíčový rozdíl mezi nimi je pořadí, ve kterém dojde k přírůstku nebo snížení v vyhodnocení výrazu. (Další informace naleznete v tématu [operátory přírůstku a snížení přípon](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md).) Ve formuláři předpony se zvyšuje nebo snižuje počet před tím, než se hodnota použije při vyhodnocování výrazu, takže hodnota výrazu se liší od hodnoty operandu. Ve formuláři přípona probíhá přírůstek nebo snížení po použití hodnoty ve vyhodnocení výrazu, takže hodnota výrazu je stejná jako hodnota operandu. Například následující program vytiskne "`++i = 6`":

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

Operand integrálního nebo plovoucího typu se zvýší nebo sníží o celočíselnou hodnotu 1. Typ výsledku je stejný jako typ operandu. Operand typu ukazatele je zvětšen nebo snížen o velikost objektu, na který odkazuje. Zvýšený ukazatel ukazuje na další objekt; Snížený ukazatel ukazuje na předchozí objekt.

Vzhledem k tomu, že operátory přírůstku a snížení mají vedlejší účinky, mohou být pomocí výrazů s operátory zvýšení nebo snížení v [makru preprocesoru](../preprocessor/macros-c-cpp.md) nežádoucí výsledky. Vezměte v úvahu tento příklad:

```cpp
// expre_Increment_and_Decrement_Operators2.cpp
#define max(a,b) ((a)<(b))?(b):(a)

int main()
{
   int i = 0, j = 0, k;
   k = max( ++i, j );
}
```

Makro se rozbalí do:

```cpp
k = ((++i)<(j))?(j):(++i);
```

Pokud je `i` větší nebo rovna `j` nebo menší než `j` hodnotou 1, bude zvýšena dvakrát.

> [!NOTE]
>  C++vložené funkce jsou vhodnější pro makra v mnoha případech, protože odstraňují vedlejší účinky, jako jsou zde popsané, a umožňují jazyku provádět úplnější kontrolu typu.

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operátory inkrementace a dekrementace předpony](../c-language/prefix-increment-and-decrement-operators.md)
