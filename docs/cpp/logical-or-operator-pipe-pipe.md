---
title: 'Logický operátor OR: || | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '||'
dev_langs:
- C++
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37a7591e185b1436bb3cd0f8b56a625f71bf8ed2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073641"
---
# <a name="logical-or-operator-"></a>Logický operátor OR: ||

## <a name="syntax"></a>Syntaxe

> *logické nebo expression* **||** *logické a expression*

## <a name="remarks"></a>Poznámky

Logický operátor OR (**||**) vrátí logickou hodnotu TRUE, pokud nebo oba operandy hodnotu TRUE a v opačném případě vrátí hodnotu FALSE. Operandy jsou implicitně převedeny na typ **bool** před hodnocení a výsledek je typu **bool**. Logická operace OR je asociativní zleva doprava.

Operandy logického operátoru OR nemusí být stejného typu, musí však být typy celého čísla nebo ukazatele. Operandy jsou obvykle relační výrazy nebo výrazy rovnosti.

První operand je zcela vyhodnocen a před pokračováním ve vyhodnocování logického výrazu OR jsou dokončeny všechny vedlejší účinky.

Druhý operand je vyhodnocen pouze v případě, že je první operand vyhodnocen na hodnotu false (0). Tím jsou odstraněna nepotřebná vyhodnocení druhého operandu, je-li logický výraz OR vyhodnocen na hodnotu true.

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

Rovná-li se v příkladu výše proměnná `x` proměnné `w`, `y` nebo `z`, je druhý argument funkce `printf` vyhodnocen na hodnotu true a dojde k vypsání hodnoty 1. V opačném případě je vyhodnocen jako NEPRAVDA a vytisknout hodnotu 0. Poté, co byla jedna z podmínek vyhodnotí jako true, přestane hodnocení.

## <a name="operator-keyword-for-124124"></a>Klíčové slovo pro operátor&#124;&#124;

**Nebo** operátor je textový ekvivalent operátoru **||**. Existují dva způsoby přístupu k **nebo** operátor ve svých programech: zahrnutím souboru hlaviček \<soubor iso646.h >, nebo kompilací s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázání jazykových rozšíření).

## <a name="example"></a>Příklad

```cpp
// expre_Logical_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate logical OR
#include <iostream>
using namespace std;
int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b || b > c yields "
         << (a < b || b > c) << endl
         << "The false expression "
         << "a > b || b > c yields "
         << (a > b || b > c) << endl;
}
```

## <a name="see-also"></a>Viz také:

[Integrované operátory C++ Priorita a asociativita](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Logické operátory jazyka C](../c-language/c-logical-operators.md)