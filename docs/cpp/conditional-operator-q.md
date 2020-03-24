---
title: 'Podmíněný operátor: &quest;:'
ms.date: 11/04/2016
f1_keywords:
- '?:'
- '?'
helpviewer_keywords:
- conditional operators [C++]
- '? : operator'
ms.assetid: 88643ee8-7100-4f86-880a-705ec22b6271
ms.openlocfilehash: 8c00db06ed5c0347cb9c720e35bd3e517df2a13c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189572"
---
# <a name="conditional-operator-quest-"></a>Podmíněný operátor: &quest;:

## <a name="syntax"></a>Syntaxe

```
expression ? expression : expression
```

## <a name="remarks"></a>Poznámky

Podmíněný operátor ( **?:** ) je Ternární operátor (používá tři operandy). Podmíněný operátor pracuje následujícím způsobem:

- První operand je implicitně převeden na **bool**. Je vyhodnocen a před pokračováním jsou dokončeny všechny vedlejší účinky.

- Pokud je první operand vyhodnocen jako **true** (1), je vyhodnocen druhý operand.

- Pokud je první operand vyhodnocen jako **false** (0), je vyhodnocen třetí operand.

Výsledek podmíněného operátoru je určen podle toho, který operand je vyhodnocen, zda druhý nebo třetí. V podmíněném výrazu je vyhodnocen pouze jeden z posledních dvou operandů.

Podmíněné výrazy mají asociativitu zprava doleva. První operand musí být celočíselného typu nebo typu ukazatele. Následující pravidla platí pro druhý a třetí operand:

- Jsou-li oba operandy stejného typu, je výsledek tohoto typu.

- Jsou-li oba operandy aritmetických nebo výčtových typů, jsou provedeny běžné aritmetické převody (pokryté [standardními převody](standard-conversions.md)) pro jejich převod na společný typ.

- Jsou-li oba operandy typu ukazatele, nebo pokud je jeden typ ukazatele a druhý je konstantní výraz, který je vyhodnocen na hodnotu 0, jsou provedeny převody ukazatelů pro jejich převod na společný typ.

- Jsou-li oba operandy typu odkazu, jsou provedeny převody odkazů pro jejich převod na společný typ.

- Pokud jsou oba operandy typu void, společný typ je typ void.

- Pokud jsou oba operandy stejného uživatelsky definovaného typu, společný typ je tento typ.

- Pokud mají operandy různé typy a nejméně jeden z operandů má uživatelsky definovaný typ, použijí se pravidla jazyka pro určení společného typu. (Viz upozornění níže.)

Jakékoli kombinace druhého a třetího operandu, které nejsou uvedeny v předchozím seznamu, jsou neplatné. Typ výsledku je společný typ a je to l-hodnota, pokud jsou druhý i třetí operand stejného typu a oba jsou l-hodnoty.

> [!WARNING]
>  Pokud typy druhý a třetí operand nejsou totožné, pak jsou vyvolány komplexní pravidla konverze typu, jak je uvedeno ve C++ standardu. Tyto převody mohou vést k neočekávanému chování, včetně konstrukce a zničení dočasných objektů. Z tohoto důvodu se důrazně doporučuje buď (1) Nepoužívat uživatelsky definované typy jako operandy s podmíněným operátorem nebo (2), pokud použijete uživatelsky definované typy, a pak explicitně přetypovat každý operand na společný typ.

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
