---
title: 'Druhý&#39;operátor s doplňkem: ~'
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
ms.openlocfilehash: 777f253925caf38647863bdaa93fde8d5a03e3f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177713"
---
# <a name="one39s-complement-operator-"></a>Druhý&#39;operátor s doplňkem: ~

## <a name="syntax"></a>Syntaxe

```
~ cast-expression
```

## <a name="remarks"></a>Poznámky

Jeden z operátorů doplňku (`~`), někdy nazývaný operátor „bitového doplňku“, vrací jedničkový bitový doplněk svého operandu. To znamená, že každý bit, který je 1 v operandu, je 0 ve výsledku. A naopak, každý bit, který je 0 v operandu, je 1 ve výsledku. Operand operátoru jedničkového doplňku musí být celočíselného typu.

## <a name="operator-keyword-for-"></a>Klíčové slovo pro operátor ~

Operátor **comp** je textový ekvivalent `~`. Existují dva způsoby, jak získat přístup k operátoru **comp** ve svých programech: zahrňte hlavičkový soubor `iso646.h`nebo zkompilujte pomocí [/za](../build/reference/za-ze-disable-language-extensions.md).

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

Celočíselné povýšení proběhne na celočíselných operandech a výsledný typ je typ, na který je operand povýšen. Další informace o tom, jak se povýšení provádí, najdete v tématu [standardní převody](standard-conversions.md) .

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Unární aritmetické operátory](../c-language/unary-arithmetic-operators.md)
