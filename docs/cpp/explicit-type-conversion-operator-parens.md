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
ms.openlocfilehash: c168653a82b4d4c5023de1f76a1e6269625c74d8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354863"
---
# <a name="explicit-type-conversion-operator-"></a>Operátor převodu explicitního typu: ()

Jazyk C++ umožňuje explicitní převod typu pomocí syntaxe podobné syntaxi volání funkce.

## <a name="syntax"></a>Syntaxe

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>Poznámky

*Název typu simple* následovaný *seznamem výrazů* uzavřeným v závorcích vytvoří objekt zadaného typu pomocí zadaných výrazů. Následující příklad ukazuje explicitní převod typu na typ int:

```cpp
int i = int( d );
```

Následující příklad ukazuje `Point` třídu.

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

Předchozí příklad, který používá převod ve stylu funkce, ukazuje, jak převést dvě hodnoty (jedna `Point`pro *x* a jedna pro *y*) na uživatelem definovaný typ .

> [!CAUTION]
> Explicitní převody typu používejte opatrně, protože přepisují vestavěnou kontrolu typů kompilátoru jazyka C++.

Zápis [přetypování](../cpp/cast-operator-parens.md) musí být použit pro převody na typy, které nemají *název jednoduchého typu* (například ukazatel nebo typy odkazů). Převod na typy, které mohou být vyjádřeny *pomocí jednoduchého názvu typu,* lze zapsat v obou formách.

Definice typu v rámci přetypování je neplatná.

## <a name="see-also"></a>Viz také

[Postfix výrazy](../cpp/postfix-expressions.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
