---
title: const_cast – operátor
ms.date: 11/04/2016
f1_keywords:
- const_cast_cpp
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
ms.openlocfilehash: d2711142e4aa73cc0119949876e7e593067cd45d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180339"
---
# <a name="const_cast-operator"></a>const_cast – operátor

Odebere atributy **const**, **volatile**a **__unaligned** z třídy.

## <a name="syntax"></a>Syntaxe

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>Poznámky

Ukazatel na libovolný typ objektu nebo ukazatel na datový člen může být explicitně převeden na typ, který je totožný s výjimkou kvalifikátorů **const**, **volatile**a **__unaligned** . Pro ukazatele a odkazy bude výsledek odkazovat na původní objekt. Pro ukazatele na datové členy bude výsledek odkazovat na stejný člen jako původní (nepřetypovaný) ukazatel na datový člen. V závislosti na typu odkazovaného objektu mohou operace zápisu skrz výsledný ukazatel, odkaz nebo ukazatel na datový člen mít za následek nedefinované chování.

Operátor **const_cast** nelze použít k přímému přepsání konstantního stavu konstantní proměnné.

Operátor **const_cast** převede hodnotu ukazatele null na hodnotu ukazatele null cílového typu.

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

Na řádku obsahujícím **const_cast**je datový typ **tohoto** ukazatele `const CCTest *`. Operátor **const_cast** změní datový typ **tohoto** ukazatele na `CCTest *`, což umožňuje upravovat členské `number`. Toto přetypování trvá pouze po zbytek příkazu, ve kterém se zobrazí.

## <a name="see-also"></a>Viz také

[Operátory přetypování](../cpp/casting-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
