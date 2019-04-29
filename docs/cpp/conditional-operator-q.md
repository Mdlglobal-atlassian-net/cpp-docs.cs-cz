---
title: 'Podmíněný operátor:? :'
ms.date: 11/04/2016
f1_keywords:
- '?:'
- '?'
helpviewer_keywords:
- conditional operators [C++]
- '? : operator'
ms.assetid: 88643ee8-7100-4f86-880a-705ec22b6271
ms.openlocfilehash: 8744ca8546d48e9283cc0dfa9d80babf5076f8b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399145"
---
# <a name="conditional-operator--"></a>Podmíněný operátor:? :

## <a name="syntax"></a>Syntaxe

```
expression ? expression : expression
```

## <a name="remarks"></a>Poznámky

Podmíněný operátor (**?:**) je tříhodnotový operátor (má tři operandy). Podmíněný operátor pracuje následujícím způsobem:

- První operand je implicitně převeden na **bool**. Je vyhodnocen a před pokračováním jsou dokončeny všechny vedlejší účinky.

- Pokud je první operand vyhodnocen jako **true** (1), je vyhodnocen Druhý operand.

- Pokud je první operand vyhodnocen jako **false** (0), je vyhodnocen třetí operand.

Výsledek podmíněného operátoru je určen podle toho, který operand je vyhodnocen, zda druhý nebo třetí. V podmíněném výrazu je vyhodnocen pouze jeden z posledních dvou operandů.

Podmíněné výrazy mají asociativitu zprava doleva. První operand musí být celočíselného typu nebo typu ukazatele. Do druhého a třetího operandu, platí následující pravidla:

- Pokud jsou oba operandy stejného typu, je výsledek tohoto typu.

- Pokud jsou oba operandy aritmetického nebo výčtového typu, obvyklé aritmetické převody (popsané v [standardní převody](standard-conversions.md)) jsou provedeny je převést na společný typ.

- Pokud jsou oba operandy typů ukazatele nebo pokud je jeden typ ukazatele a druhý je konstantní výraz, který se vyhodnotí na hodnotu 0, jsou provedeny převody pro převod na společný typ.

- Pokud jsou oba operandy typů odkazů, který je převede na společný typ. jsou provedeny převody odkazů.

- Pokud jsou oba operandy typu void, společný typ je typ void.

- Pokud jsou oba operandy stejného typu definovaný uživatelem, je společný typ tohoto typu.

- Pokud mají různé typy operandů a alespoň jeden z operandů má uživatelem definovaný typ jazykových pravidel slouží k určení společný typ. (Viz následující upozornění.)

Jakékoli kombinace druhého a třetího operandu, které nejsou uvedeny v předchozím seznamu, jsou neplatné. Typ výsledku je společný typ a je to l-hodnota, pokud jsou druhý i třetí operand stejného typu a oba jsou l-hodnoty.

> [!WARNING]
>  Pokud nejsou identické typy druhého a třetího operandu, jsou vyvolány pravidla převodu komplexní typ, jak je uvedeno ve standardu jazyka C++. Tyto převody může vést k neočekávanému chování, včetně vytváření a zničení dočasné objekty. Z tohoto důvodu důrazně vám buď (1) vyhnout jako operandy s podmíněným operátorem pomocí uživatelem definované typy nebo (2) Pokud pomocí uživatelem definovaných typů, pak explicitně přetypovat operandem na společný typ.

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

## <a name="see-also"></a>Viz také:

[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operátor podmíněného výrazu](../c-language/conditional-expression-operator.md)