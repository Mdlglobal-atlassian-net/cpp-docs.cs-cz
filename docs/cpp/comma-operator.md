---
title: Operátor čárky:, | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '%2C'
dev_langs:
- C++
helpviewer_keywords:
- comma operator
ms.assetid: 38e0238e-19da-42ba-ae62-277bfdab6090
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 626243da557362626b5d17ed01a8023e36704f54
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114784"
---
# <a name="comma-operator-"></a>Operátor čárky: ,

Umožňuje seskupení dvou příkazů tam, kde se očekává jen jeden příkaz.

## <a name="syntax"></a>Syntaxe

```
expression , expression
```

## <a name="remarks"></a>Poznámky

Operátor čárka je asociativní zleva doprava. Dva příkazy oddělené čárkou jsou vyhodnoceny zleva doprava. Levý operand je vyhodnocen vždy a před vyhodnocením pravého operandu jsou dokončeny všechny vedlejší účinky.

V některých kontextech, například v seznamech argumentů funkcí, mohou být čárky použity jako oddělovače. Nezaměňujte použití čárky jako oddělovače s jejím použitím jako operátoru. Tato dvě použití jsou zcela odlišná.

Vezměte v úvahu výraz `e1, e2`. Typ a hodnota výrazu jsou typu a hodnoty *e2*; výsledek vyhodnocení výrazu *e1* se zahodí. Je-li pravý operand l-hodnotou, je i tento výsledek l-hodnotou.

Na místech, kde se čárka obvykle používá jako oddělovač (například ve vlastních argumentech funkcí nebo v inicializátorech agregace), musí být operátor čárky a jeho operandy uzavřeny do závorek. Příklad:

```cpp
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

Ve volání funkce `func_one` výše jsou předány tři argumenty oddělené čárkami: `x`, `y + 2` a `z`. Ve volání funkce `func_two` donutí závorky kompilátor interpretovat první čárku jako operátor sekvenčního vyhodnocení. Toto volání funkce předává do funkce `func_two` dva argumenty. Prvním argumentem je výsledek operace sekvenčního vyhodnocení `(x--, y + 2)`, který má hodnotu a typ výrazu `y + 2`, druhým argumentem je proměnná `z`.

## <a name="example"></a>Příklad

```cpp
// cpp_comma_operator.cpp
#include <stdio.h>
int main () {
   int i = 10, b = 20, c= 30;
   i = b, c;
   printf("%i\n", i);

   i = (b, c);
   printf("%i\n", i);
}
```

```Output
20
30
```

## <a name="see-also"></a>Viz také:

[Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operátor sekvenčního vyhodnocení](../c-language/sequential-evaluation-operator.md)