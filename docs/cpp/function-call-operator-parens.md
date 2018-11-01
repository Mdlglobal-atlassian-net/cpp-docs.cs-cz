---
title: 'Operátor volání funkce: ()'
ms.date: 11/04/2016
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
ms.openlocfilehash: 79c43ed11bfc73ec4bfaedad0a20b45fb6ca1ffb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676245"
---
# <a name="function-call-operator-"></a>Operátor volání funkce: ()

Výraz přípony následován operátorem volání funkce **()**, určuje volání funkce.

## <a name="syntax"></a>Syntaxe

```
postfix-expression
( [argument-expression-list ] )
```

## <a name="remarks"></a>Poznámky

Argumenty pro operátor volání funkce se nula nebo více výrazů oddělených čárkami, skutečné argumenty funkce.

*Postfix-expression* se musí vyhodnotit na adresu funkce (například identifikátor funkce nebo hodnota ukazatele na funkci), a *argument-expression-list* je seznamem výrazů (oddělených čárkami) jehož hodnoty (argumenty) jsou předány funkci. *Argument-expression-list* argument může být prázdný.

*Postfix-expression* musí být jeden z těchto typů:

- Funkce vracející typ `T`. Příklad deklarace

    ```cpp
    T func( int i )
    ```

- Ukazatel na funkci vracející typ `T`. Příklad deklarace

    ```cpp
    T (*func)( int i )
    ```

- Odkaz na funkci vracející typ `T`. Příklad deklarace

    ```cpp
    T (&func)(int i)
    ```

- Ukazatel na členskou funkci vracející typ přístupu přes ukazatel `T`. Příklad volání funkcí jsou

    ```cpp
    (pObject->*pmf)();
    (Object.*pmf)();
    ```

## <a name="example"></a>Příklad

Následující příklad volá funkce standardní knihovny `strcat_s` s tři argumenty:

```cpp
// expre_Function_Call_Operator.cpp
// compile with: /EHsc

#include <iostream>
#include <string>

// C++ Standard Library name space
using namespace std;

int main()
{
    enum
    {
        sizeOfBuffer = 20
    };

    char s1[ sizeOfBuffer ] = "Welcome to ";
    char s2[ ] = "C++";

    strcat_s( s1, sizeOfBuffer, s2 );

    cout << s1 << endl;
}
```

```Output
Welcome to C++
```

## <a name="function-call-results"></a>Výsledky volání funkce

Volání funkce vyhodnocuje r-hodnotu, pokud není funkce deklarována jako typ odkazu. Funkce s návratovým typem ve formě odkazu vyhodnocují l-hodnoty a lze je použít na levé straně příkazu přiřazení následujícím způsobem:

```cpp
// expre_Function_Call_Results.cpp
// compile with: /EHsc
#include <iostream>
class Point
{
public:
    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
private:
    unsigned _x;
    unsigned _y;
};

using namespace std;
int main()
{
    Point ThePoint;

    ThePoint.x() = 7;           // Use x() as an l-value.
    unsigned y = ThePoint.y();  // Use y() as an r-value.

    // Use x() and y() as r-values.
    cout << "x = " << ThePoint.x() << "\n"
         << "y = " << ThePoint.y() << "\n";
}
```

Předcházející kód definuje třídu s názvem `Point`, který obsahuje privátní dat objektů, které představují *x* a *y* souřadnice. Tyto datové objekty musejí být upraveny a jejich hodnoty načteny. Tento program je pouze jednou z několika možností pro takovou třídu. Použití funkcí `GetX` a `SetX` nebo `GetY` a `SetY` představuje další možnost.

Funkce vracející typy tříd, ukazatele na typy tříd nebo odkazy na typy tříd lze použít jako levý operand pro operátory výběru členů. Proto je platný následující kód:

```cpp
// expre_Function_Results2.cpp
class A {
public:
   A() {}
   A(int i) {}
   int SetA( int i ) {
      return (I = i);
   }

   int GetA() {
      return I;
   }

private:
   int I;
};

A func1() {
   A a = 0;
   return a;
}

A* func2() {
   A *a = new A();
   return a;
}

A& func3() {
   A *a = new A();
   A &b = *a;
   return b;
}

int main() {
   int iResult = func1().GetA();
   func2()->SetA( 3 );
   func3().SetA( 7 );
}
```

Funkce lze volat rekurzivně. Další informace o deklaracích funkcí naleznete v tématu [funkce](functions-cpp.md). Související materiál se nachází v [Program a propojení](../cpp/program-and-linkage-cpp.md).

## <a name="see-also"></a>Viz také:

[Výrazy přípony](../cpp/postfix-expressions.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Volání funkcí](../c-language/function-call-c.md)