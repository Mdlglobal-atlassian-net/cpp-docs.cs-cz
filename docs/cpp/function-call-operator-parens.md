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
ms.openlocfilehash: 3194c34bacfe7b2ed758ab245c5858eadb18e64e
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301519"
---
# <a name="function-call-operator-"></a>Operátor volání funkce: ()

Výraz přípony následovaný operátorem volání funkce, **()** , určuje volání funkce.

## <a name="syntax"></a>Syntaxe

```
postfix-expression
( [argument-expression-list ] )
```

## <a name="remarks"></a>Poznámky

Argumenty operátoru volání funkce jsou nula nebo více výrazů oddělených čárkami – skutečné argumenty funkce.

*Výraz přípony* musí být vyhodnocen jako adresa funkce (například identifikátor funkce nebo hodnota ukazatele na funkci) a *argument-expression-list* je seznam výrazů (oddělených čárkami), jejichž hodnoty (argumenty) jsou předány funkci. Argument *-Expression-list* může být prázdný.

*Výraz přípony* musí být jednoho z těchto typů:

- Funkce vracející typ `T`. Ukázková deklarace je

    ```cpp
    T func( int i )
    ```

- Ukazatel na funkci vracející typ `T`. Ukázková deklarace je

    ```cpp
    T (*func)( int i )
    ```

- Odkaz na funkci vracející typ `T`. Ukázková deklarace je

    ```cpp
    T (&func)(int i)
    ```

- Funkce ukazatele na člen odkazuje na vrácení typu `T`. Příklady volání funkcí jsou

    ```cpp
    (pObject->*pmf)();
    (Object.*pmf)();
    ```

## <a name="example"></a>Příklad

Následující příklad volá funkci standardní knihovny `strcat_s` se třemi argumenty:

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

Předchozí kód definuje třídu s názvem `Point`, která obsahuje soukromé datové objekty, které reprezentují souřadnice *x* a *y* . Tyto datové objekty musejí být upraveny a jejich hodnoty načteny. Tento program je pouze jednou z několika možností pro takovou třídu. Použití funkcí `GetX` a `SetX` nebo `GetY` a `SetY` představuje další možnost.

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

Funkce lze volat rekurzivně. Další informace o deklaracích funkcí naleznete v tématu [Functions](functions-cpp.md). Související materiál je v [jednotkách překladu a propojení](../cpp/program-and-linkage-cpp.md).

## <a name="see-also"></a>Viz také:

[Výrazy přípony](../cpp/postfix-expressions.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Volání funkcí](../c-language/function-call-c.md)