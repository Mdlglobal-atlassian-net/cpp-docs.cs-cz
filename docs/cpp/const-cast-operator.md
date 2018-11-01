---
title: const_cast – operátor
ms.date: 11/04/2016
f1_keywords:
- const_cast_cpp
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
ms.openlocfilehash: 389ef84149031fd602ff9ded15d34869258ffd52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613990"
---
# <a name="constcast-operator"></a>const_cast – operátor

Odebere **const**, **volatile**, a **__unaligned** atributy ze třídy.

## <a name="syntax"></a>Syntaxe

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>Poznámky

Ukazatel na libovolný typ objektu nebo ukazatel na datový člen lze explicitně převést na typ, který je totožný s výjimkou **const**, **volatile**, a **__unaligned** kvalifikátory. Pro ukazatele a odkazy bude výsledek odkazovat na původní objekt. Pro ukazatele na datové členy bude výsledek odkazovat na stejný člen jako původní (nepřetypovaný) ukazatel na datový člen. V závislosti na typu odkazovaného objektu mohou operace zápisu skrz výsledný ukazatel, odkaz nebo ukazatel na datový člen mít za následek nedefinované chování.

Nelze použít **const_cast** operátor pro přímé přepsání konstantního stavu konstantní proměnné.

**Const_cast** operátor převede hodnotu ukazatele null na hodnotu ukazatele null cílového typu.

## <a name="example"></a>Příklad

```cpp
// expre_const_cast_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CCTest {
public:
   void setNumber( int );
   void printNumber() const;
private:
   int number;
};

void CCTest::setNumber( int num ) { number = num; }

void CCTest::printNumber() const {
   cout << "\nBefore: " << number;
   const_cast< CCTest * >( this )->number--;
   cout << "\nAfter: " << number;
}

int main() {
   CCTest X;
   X.setNumber( 8 );
   X.printNumber();
}
```

Na řádku obsahujícím operátor **const_cast**, datový typ **to** ukazatel `const CCTest *`. **Const_cast** operátor změní datový typ **to** ukazatel na `CCTest *`, umožňuje změnu členu `number` má být upraven. Toto přetypování trvá pouze po zbytek příkazu, ve kterém se zobrazí.

## <a name="see-also"></a>Viz také:

[Operátory přetypování](../cpp/casting-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)