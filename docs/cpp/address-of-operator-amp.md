---
title: 'Operátor address-of: &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
ms.openlocfilehash: a03a6100c372e059bd9ef2ddde0558da307923dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385021"
---
# <a name="address-of-operator-amp"></a>Operátor address-of: &amp;

## <a name="syntax"></a>Syntaxe

```
& cast-expression
```

## <a name="remarks"></a>Poznámky

Operátor unární address-of (**&**) přebírá adresu svého operandu. Operand operátoru address-of může být označením funkce nebo l hodnotou označující objekt, který není bitového pole.

Operátor address-of lze použít pouze pro proměnné základních, struktury, třídy, nebo typy sjednocení, které jsou deklarovány na úrovni rozsahu souboru, nebo na indexované reference polí. V těchto výrazech lze konstantní výraz, který neobsahuje operátor address-of přičíst k nebo odečíst od výrazu adresy.

Při použití funkce nebo l hodnotami, výsledek výrazu je typ ukazatele (r) odvozen od typu operandu. Například, pokud je operand typu **char**, výsledek výrazu je typu ukazatele do **char**. Operátoru address-of, u **const** nebo **volatile** objektů, je vyhodnocen jako `const type *` nebo `volatile type *`, kde **typ** je typ původní objekt.

Při použití operátoru address-of na úplný název, výsledek závisí na tom, zda *kvalifikovaný název* Určuje statický člen. Pokud ano, výsledkem je ukazatel na typ zadaný v deklaraci člena. Pokud člen není statické, výsledkem je ukazatel na člen *název* třídy indikován *kvalifikovaný název třídy*. (Viz [primární výrazy](../cpp/primary-expressions.md) Další informace o tom *kvalifikovaný název třídy*.) Následující fragment kódu ukazuje, jak výsledek liší v závislosti na tom, zda je statický člen:

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

V tomto příkladu výraz `&PTM::fValue` vrací typ `float *` místo typu `float PTM::*` protože `fValue` je to statický člen.

Adresu přetížené funkce můžete provést pouze v případě, že je jasné, která verze funkce odkazují. Zobrazit [přetížení funkce](function-overloading.md) informace o tom, jak získat adresu konkrétní přetížení funkce.

Použití operátoru address-of na odkazový typ poskytuje stejný výsledek jako použití operátoru na objekt, ke kterému je vázán odkaz. Příklad:

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

Operátor address-of předat argument ukazatele na funkci v následujícím příkladu:

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

## <a name="see-also"></a>Viz také:

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Deklarátor odkazu l-hodnoty: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Dereferenční operátory a operátory adresy](../c-language/indirection-and-address-of-operators.md)