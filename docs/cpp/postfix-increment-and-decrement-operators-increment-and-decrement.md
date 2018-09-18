---
title: 'Operátory přírůstku a snížení přípony: ++ a--| Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4591f9f4fed8b3b8dd1c24b8200b3365d87194b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044662"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>Operátory přírůstku a snížení přípony: ++ a --

## <a name="syntax"></a>Syntaxe

```
postfix-expression ++
postfix-expression --
```

## <a name="remarks"></a>Poznámky

Jazyk C++ poskytuje předponové a příponové operátory inkrementace a dekrementace. Tato část popisuje pouze příponové operátory inkrementace a dekrementace. (Další informace najdete v tématu [operátory Prefix Inkrementace a dekrementace](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md).) Rozdíl mezi těmito dvěma spočívá v tom, že v notaci příponový operátor, který se zobrazí po *postfix-expression*, zatímco v předponovém, se operátor vyskytuje před *výrazu.* Následující příklad ukazuje příponový operátor inkrementace:

```cpp
i++;
```

Účinkem použití příponového operátoru Inkrementace (**++**) je, že je zvýšení hodnoty operandu o jednu jednotku příslušného typu. Obdobně, účinkem použití příponového operátoru dekrementace (**--**) je, že je snížení hodnoty operandu o jednu jednotku příslušného typu.

Je důležité si uvědomit, že příponový zvýšení nebo snížení výraz vyhodnocen jako hodnota výrazu *před* aplikací použitím daného operátoru. Dojde k operaci zvýšení nebo snížení *po* operand je vyhodnocen. K tomuto problému dochází pouze v případě výskytu příponové operace inkrementace či dekrementace v kontextu rozsáhlejšího výrazu.

Je-li příponový operátor použit v argumentu funkce, není zaručeno, že hodnota argumentu bude zvýšena nebo snížena před jeho předáním funkci.  Další informace naleznete v oddílu 1.9.17 standardu jazyka C++.

Použití příponového operátoru Inkrementace u ukazatele na pole objektů typu **dlouhé** skutečně přičte hodnotu 4 na vnitřní reprezentaci ukazatele. Toto chování způsobí, že ukazatel, který dříve odkazoval *n*-tém prvku pole k odkazování (*n*+ 1) tý prvek.

Operandy Příponové operátory Inkrementace a dekrementace operátory přípony musí být upravitelné (nikoli **const**) l hodnoty aritmetického typu nebo typu ukazatele. Typ výsledku je stejný jako *postfix-expression*, ale už nejsou l hodnotou.

**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): operand příponového přírůstek nebo snížení operátor nesmí být typu **bool**.

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

## <a name="see-also"></a>Viz také:

[Výrazy přípony](../cpp/postfix-expressions.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operátory inkrementace a dekrementace přípony jazyka C](../c-language/c-postfix-increment-and-decrement-operators.md)