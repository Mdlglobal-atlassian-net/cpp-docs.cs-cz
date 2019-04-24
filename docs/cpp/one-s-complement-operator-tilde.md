---
title: 'Jeden&#39;s vlastní operátor doplňku: ~'
ms.date: 11/04/2016
f1_keywords:
- "~"
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
ms.openlocfilehash: d8fb8ca56932669ff85646f2aa0c10691122013b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245017"
---
# <a name="one39s-complement-operator-"></a>Jeden&#39;s vlastní operátor doplňku: ~

## <a name="syntax"></a>Syntaxe

```
~ cast-expression
```

## <a name="remarks"></a>Poznámky

Jeden z operátorů doplňku (`~`), někdy nazývaný operátor „bitového doplňku“, vrací jedničkový bitový doplněk svého operandu. To znamená, že každý bit, který je 1 v operandu, je 0 ve výsledku. A naopak, každý bit, který je 0 v operandu, je 1 ve výsledku. Operand operátoru jedničkového doplňku musí být celočíselného typu.

## <a name="operator-keyword-for-"></a>Klíčové slovo pro operátor ~

**Compl** operátor je textový ekvivalent operátoru `~`. Existují dva způsoby přístupu k **compl** operátor ve svých programech: zahrnutím souboru hlaviček `iso646.h`, nebo kompilací s [/Za](../build/reference/za-ze-disable-language-extensions.md).

## <a name="example"></a>Příklad

```cpp
// expre_One_Complement_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main () {
   unsigned short y = 0xFFFF;
   cout << hex << y << endl;
   y = ~y;   // Take one's complement
   cout << hex << y << endl;
}
```

V tomto příkladu je nová hodnota přiřazená proměnné `y` jedničkovým doplňkem hodnoty bez znaménka 0xFFFF nebo 0x0000.

Celočíselné povýšení proběhne na celočíselných operandech a výsledný typ je typ, na který je operand povýšen. Zobrazit [standardní převody](standard-conversions.md) Další informace o tom, jak je povýšení provedeno.

## <a name="see-also"></a>Viz také:

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Unární aritmetické operátory](../c-language/unary-arithmetic-operators.md)