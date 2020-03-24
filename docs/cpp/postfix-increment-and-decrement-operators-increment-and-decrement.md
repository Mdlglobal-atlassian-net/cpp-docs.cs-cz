---
title: 'Operátory přírůstku a snížení přípony: ++ a --'
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
ms.openlocfilehash: 44b1031376abd6c50c3b9706089042995994e495
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177674"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>Operátory přírůstku a snížení přípony: ++ a --

## <a name="syntax"></a>Syntaxe

```
postfix-expression ++
postfix-expression --
```

## <a name="remarks"></a>Poznámky

Jazyk C++ poskytuje předponové a příponové operátory inkrementace a dekrementace. Tato část popisuje pouze příponové operátory inkrementace a dekrementace. (Další informace najdete v tématu [operátory přírůstku a snížení předpony](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md).) Rozdíl mezi těmito dvěma hodnotami je, že v notaci přípony se operátor zobrazí za *výrazem přípony*, zatímco v zápisu předpony se operátor zobrazí před *výrazem.* Následující příklad ukazuje příponový operátor inkrementace:

```cpp
i++;
```

Účinek použití operátoru přírůstku přípony ( **++** ) je, že hodnota operandu se zvyšuje o jednu jednotku příslušného typu. Podobně platí, že účinek použití operátoru pro snížení přípony ( **--** ) je, že hodnota operandu se zmenší o jednu jednotku příslušného typu.

Je důležité si uvědomit, že výraz pro přírůstek nebo snížení přípony se vyhodnocuje na hodnotu výrazu *před* použitím příslušného operátoru. Operace zvýšení nebo snížení nastane *po* vyhodnocení operandu. K tomuto problému dochází pouze v případě výskytu příponové operace inkrementace či dekrementace v kontextu rozsáhlejšího výrazu.

Je-li příponový operátor použit v argumentu funkce, není zaručeno, že hodnota argumentu bude zvýšena nebo snížena před jeho předáním funkci.  Další informace naleznete v oddílu 1.9.17 standardu jazyka C++.

Použití operátoru příznaku **příznaku** na ukazatel na pole objektů typu Long ve skutečnosti přidá čtyři k vnitřní reprezentaci ukazatele. Toto chování způsobí, že ukazatel, který dříve odkazoval na *n*-tý prvek pole, odkazuje na element (*n*+ 1).

Operandy přírůstku a operátoru snížení přípony musí být možné upravovat ( **nekonstantní**) hodnoty typu aritmetického typu nebo typu ukazatele. Typ výsledku je stejný jako *příponový výraz*, ale již není l-value.

**Visual Studio 2017 verze 15,3 a novější** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): Operand operátoru příznaku nebo odečtení přípony nemůže být typu **bool**.

Následující kód znázorňuje příponový operátor inkrementace:

```cpp
// expre_Postfix_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
   int i = 10;
   cout << i++ << endl;
   cout << i << endl;
}
```

Operace následného zvýšení nebo snížení nejsou podporovány pro výčtové typy:

```cpp
enum Compass { North, South, East, West );
Compass myCompass;
for( myCompass = North; myCompass != West; myCompass++ ) // Error
```

## <a name="see-also"></a>Viz také

[Výrazy přípony](../cpp/postfix-expressions.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operátory inkrementace a dekrementace přípony jazyka C](../c-language/c-postfix-increment-and-decrement-operators.md)
