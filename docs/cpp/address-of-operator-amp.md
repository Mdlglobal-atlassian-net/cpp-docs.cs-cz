---
title: 'Address-of – operátor: &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
ms.openlocfilehash: 4c9ae9aedaec202c8798ab454ee5df1a68278a6d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181600"
---
# <a name="address-of-operator-amp"></a>Address-of – operátor: &amp;

## <a name="syntax"></a>Syntaxe

```
& cast-expression
```

## <a name="remarks"></a>Poznámky

Unární operátor address-of ( **&** ) přebírá adresu svého operandu. Operandem operátoru address-of může být buď specifikátor funkce, nebo l-hodnota, která určuje objekt, který není bitové pole.

Operátor address-of lze použít pouze pro proměnné se základními typy, struktura, třída nebo sjednocení, které jsou deklarovány na úrovni souboru nebo na podskriptované odkazy na pole. V těchto výrazech konstantní výraz, který neobsahuje operátor address-of, lze přidat nebo odečíst od výrazu adresy.

Při použití na funkce nebo l hodnoty je výsledkem výrazu typ ukazatele (hodnota r) odvozená od typu operandu. Například pokud je operand typu **char**, výsledek výrazu je typu ukazatel na **char**. Operátor address-of, aplikovaný na objekty **const** nebo **volatile** , je vyhodnocen jako `const type *` nebo `volatile type *`, kde **Type** je typ původního objektu.

Při použití operátoru address-of na úplný název závisí výsledek na tom, zda *kvalifikovaný název* Určuje statický člen. V takovém případě je výsledkem ukazatel na typ zadaný v deklaraci členu. Pokud člen není statický, je výsledkem ukazatel na *název* členu třídy, která je označena *kvalifikováním názvu třídy*. (Další informace o *kvalifikovaném názvu třídy*naleznete v tématu [primární výrazy](../cpp/primary-expressions.md) .) Následující fragment kódu ukazuje, jak se výsledek liší v závislosti na tom, zda je člen statický:

```cpp
// expre_Address_Of_Operator.cpp
// C2440 expected
class PTM {
public:
    int iValue;
    static float fValue;
};

int main() {
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static
   float *spfValue     = &PTM::fValue;  // OK
}
```

V tomto příkladu výraz `&PTM::fValue` poskytne typ `float *` namísto typu `float PTM::*`, protože `fValue` je statický člen.

Adresa přetížené funkce může být provedena pouze v případě, že je jasné, na kterou verzi funkce odkazujete. Informace o tom, jak získat adresu konkrétní přetížené funkce naleznete v tématu [přetížení funkce](function-overloading.md) .

Použití operátoru address-of na odkazový typ poskytuje stejný výsledek jako aplikování operátoru na objekt, ke kterému je odkaz vázán. Příklad:

## <a name="example"></a>Příklad

```cpp
// expre_Address_Of_Operator2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   double d;        // Define an object of type double.
   double& rd = d;  // Define a reference to the object.

   // Obtain and compare their addresses
   if( &d == &rd )
      cout << "&d equals &rd" << endl;
}
```

## <a name="output"></a>Výstup

```Output
&d equals &rd
```

Následující příklad používá operátor address-of k předání argumentu ukazatele funkci:

```cpp
// expre_Address_Of_Operator3.cpp
// compile with: /EHsc
// Demonstrate address-of operator &

#include <iostream>
using namespace std;

// Function argument is pointer to type int
int square( int *n ) {
   return (*n) * (*n);
}

int main() {
   int mynum = 5;
   cout << square( &mynum ) << endl;   // pass address of int
}
```

## <a name="output"></a>Výstup

```Output
25
```

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Deklarátor odkazu l-hodnoty: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Dereferenční operátory a operátory adresy](../c-language/indirection-and-address-of-operators.md)
