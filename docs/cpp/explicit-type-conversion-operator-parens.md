---
title: 'Operátor převodu explicitního typu: ()'
ms.date: 11/04/2016
helpviewer_keywords:
- explicit data type conversion operator
- conversions [C++], explicit
- operators [C++], explicit type conversion
- data type conversion [C++], explicit
- type conversion [C++], explicit conversions
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
ms.openlocfilehash: 9dc9440db9ea1ff7285ff9b682f6be9900c2a1ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184310"
---
# <a name="explicit-type-conversion-operator-"></a>Operátor převodu explicitního typu: ()

Jazyk C++ umožňuje explicitní převod typu pomocí syntaxe podobné syntaxi volání funkce.

## <a name="syntax"></a>Syntaxe

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>Poznámky

A *simple-type-name* následovaný *seznam výrazů* uzavřeným v závorkách vytvoří objekt zadaného typu pomocí zadaných výrazů. Následující příklad ukazuje explicitní převod typu na typ int:

```cpp
int i = int( d );
```

Následující příklad ukazuje `Point` třídy.

## <a name="example"></a>Příklad

```cpp
// expre_Explicit_Type_Conversion_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class Point
{
public:
    // Define default constructor.
    Point() { _x = _y = 0; }
    // Define another constructor.
    Point( int X, int Y ) { _x = X; _y = Y; }

    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
    void Show()   { cout << "x = " << _x << ", "
                         << "y = " << _y << "\n"; }
private:
    unsigned _x;
    unsigned _y;
};

int main()
{
    Point Point1, Point2;

    // Assign Point1 the explicit conversion
    //  of ( 10, 10 ).
    Point1 = Point( 10, 10 );

    // Use x() as an l-value by assigning an explicit
    //  conversion of 20 to type unsigned.
    Point1.x() = unsigned( 20 );
    Point1.Show();

    // Assign Point2 the default Point object.
    Point2 = Point();
    Point2.Show();
}
```

## <a name="output"></a>Výstup

```Output
x = 20, y = 10
x = 0, y = 0
```

Ačkoli předchozí příklad ukazuje explicitní převod typu s použitím konstant, stejný postup funguje při provádění těchto převodů s objekty. Následující fragment kódu to demonstruje:

```cpp
int i = 7;
float d;

d = float( i );
```

Explicitní převody typu lze zadat také pomocí syntaxe „přetypování“. Předchozí příklad přepsaný pomocí syntaxe přetypování je:

```cpp
d = (float)i;
```

Při převodu z jedné hodnoty vrací převody pomocí přetypování a převody stylu funkce stejné výsledky. Avšak u syntaxe stylu funkce lze zadat více než jeden argument převodu. Tento rozdíl je důležitý pro uživatelské typy. Vezměte v úvahu třídu `Point` a její převody:

```cpp
struct Point
{
    Point( short x, short y ) { _x = x; _y = y; }
    ...
    short _x, _y;
};
...
Point pt = Point( 3, 10 );
```

V předchozím příkladu, který používá převod stylu funkce, ukazuje, jak převést dvě hodnoty (jeden pro *x* a jeden pro *y*) pro uživatelem definovaný typ `Point`.

> [!CAUTION]
>  Explicitní převody typu používejte opatrně, protože přepisují vestavěnou kontrolu typů kompilátoru jazyka C++.

[Přetypování](../cpp/cast-operator-parens.md) musí být použit zápis převody na typy, které nemají *simple-type-name* (typy ukazatelů nebo odkazů, třeba). Převod na typy, které lze vyjádřit pomocí *simple-type-name* může být napsán v obou tvarech.

Definice typu v rámci přetypování je neplatná.

## <a name="see-also"></a>Viz také:

[Výrazy přípony](../cpp/postfix-expressions.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)