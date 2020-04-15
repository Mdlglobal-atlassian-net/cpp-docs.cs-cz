---
title: 'Podmíněný operátor: &quest; :'
ms.date: 11/04/2016
f1_keywords:
- '?:'
- '?'
helpviewer_keywords:
- conditional operators [C++]
- '? : operator'
ms.assetid: 88643ee8-7100-4f86-880a-705ec22b6271
ms.openlocfilehash: 4ba4c80d40450fd5975b047a1a4fca63146c5773
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337266"
---
# <a name="conditional-operator-quest-"></a>Podmíněný operátor: &quest; :

## <a name="syntax"></a>Syntaxe

```
expression ? expression : expression
```

## <a name="remarks"></a>Poznámky

Podmíněný operátor (**? :**) je ternární operátor (trvá tři operandy). Podmíněný operátor pracuje následujícím způsobem:

- První operand je implicitně převeden na **bool**. Je vyhodnocen a před pokračováním jsou dokončeny všechny vedlejší účinky.

- Pokud první operand vyhodnotí **true** (1), druhý operand je vyhodnocena.

- Pokud první operand vyhodnotí **na false** (0), třetí operand je vyhodnocena.

Výsledek podmíněného operátoru je určen podle toho, který operand je vyhodnocen, zda druhý nebo třetí. V podmíněném výrazu je vyhodnocen pouze jeden z posledních dvou operandů.

Podmíněné výrazy mají asociativitu zprava doleva. První operand musí být celočíselného typu nebo typu ukazatele. Pro druhý a třetí operandy platí tato pravidla:

- Pokud jsou oba operandy stejného typu, výsledek je tohoto typu.

- Pokud jsou oba operandy aritmetické nebo výčtu typy, obvyklé aritmetické převody (uvedené v [standardní převody](standard-conversions.md)) jsou prováděny převést na běžný typ.

- Pokud oba operandy jsou typy ukazatelů nebo pokud jeden je typ ukazatele a druhý je konstantní výraz, který vyhodnocuje na 0, jsou provedeny převody ukazatele převést na běžný typ.

- Pokud oba operandy jsou typy odkazů, jsou provedeny převody odkazů převést na běžný typ.

- Pokud jsou oba operandy typu void, běžný typ je typ void.

- Pokud jsou oba operandy stejného uživatelem definovaného typu, běžným typem je tento typ.

- Pokud operandy mají různé typy a alespoň jeden z operandů má uživatelem definovaný typ, pak se k určení společného typu používají jazyková pravidla. (Viz upozornění níže.)

Jakékoli kombinace druhého a třetího operandu, které nejsou uvedeny v předchozím seznamu, jsou neplatné. Typ výsledku je společný typ a je to l-hodnota, pokud jsou druhý i třetí operand stejného typu a oba jsou l-hodnoty.

> [!WARNING]
> Pokud typy druhého a třetího operandu nejsou identické, jsou vyvolána komplexní pravidla převodu typu, jak je uvedeno ve standardu C++. Tyto převody může vést k neočekávané chování, včetně konstrukce a zničení dočasných objektů. Z tohoto důvodu důrazně doporučujeme buď (1) vyhnout se použití uživatelem definované typy jako operandy s podmíněnýoperátor nebo (2) pokud používáte uživatelem definované typy, pak explicitně přetypovat každý operand na běžný typ.

## <a name="example"></a>Příklad

```cpp
// expre_Expressions_with_the_Conditional_Operator.cpp
// compile with: /EHsc
// Demonstrate conditional operator
#include <iostream>
using namespace std;
int main() {
   int i = 1, j = 2;
   cout << ( i > j ? i : j ) << " is greater." << endl;
}
```

## <a name="see-also"></a>Viz také

[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operátor podmíněného výrazu](../c-language/conditional-expression-operator.md)
