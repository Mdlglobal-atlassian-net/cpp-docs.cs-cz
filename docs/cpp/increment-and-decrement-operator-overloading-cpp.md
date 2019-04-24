---
title: Přetížení operátoru inkrementace a dekrementace (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
ms.openlocfilehash: 4413c2bba600d1118870faca9a15b20398ec4dd4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183565"
---
# <a name="increment-and-decrement-operator-overloading-c"></a>Přetížení operátoru inkrementace a dekrementace (C++)

Operátory zvýšení a snížení spadají do zvláštní kategorie, protože existují dvě varianty každého z nich:

- Preinkrement a postinkrement

- Predekrement a postdekrement

Při zápisu funkcí přetížených operátorů může být užitečné implementovat samostatné verze pro předponovou a příponovou verzi těchto operátorů. K rozlišení mezi těmito dvěma, je dodržovat následující pravidlo: Předponový tvar operátoru je deklarován stejným způsobem jako ostatní unární operátory; příponový tvar přijímá další argument typu **int**.

> [!NOTE]
>  Při zadání přetíženého operátoru pro příponový tvar operátoru zvýšení nebo snížení, musí být další argument typu **int**; zadání jiného typu vygeneruje chybu.

Následující příklad ukazuje, jak definovat předponové a příponové operátory zvýšení a snížení třídy `Point`:

```cpp
// increment_and_decrement1.cpp
class Point
{
public:
   // Declare prefix and postfix increment operators.
   Point& operator++();       // Prefix increment operator.
   Point operator++(int);     // Postfix increment operator.

   // Declare prefix and postfix decrement operators.
   Point& operator--();       // Prefix decrement operator.
   Point operator--(int);     // Postfix decrement operator.

   // Define default constructor.
   Point() { _x = _y = 0; }

   // Define accessor functions.
   int x() { return _x; }
   int y() { return _y; }
private:
   int _x, _y;
};

// Define prefix increment operator.
Point& Point::operator++()
{
   _x++;
   _y++;
   return *this;
}

// Define postfix increment operator.
Point Point::operator++(int)
{
   Point temp = *this;
   ++*this;
   return temp;
}

// Define prefix decrement operator.
Point& Point::operator--()
{
   _x--;
   _y--;
   return *this;
}

// Define postfix decrement operator.
Point Point::operator--(int)
{
   Point temp = *this;
   --*this;
   return temp;
}
int main()
{
}
```

Stejné operátory lze definovat v rozsahu souboru (globálně) pomocí následujících záhlaví funkce:

```cpp
friend Point& operator++( Point& )      // Prefix increment
friend Point& operator++( Point&, int ) // Postfix increment
friend Point& operator--( Point& )      // Prefix decrement
friend Point& operator--( Point&, int ) // Postfix decrement
```

Argument typu **int** , který označuje příponový tvar přírůstek nebo operátor dekrementace se obvykle nepoužívá k předání argumentů. Obvykle obsahuje hodnotu 0. Lze jej však použít následujícím způsobem:

```cpp
// increment_and_decrement2.cpp
class Int
{
public:
    Int &operator++( int n );
private:
    int _i;
};

Int& Int::operator++( int n )
{
    if( n != 0 )    // Handle case where an argument is passed.
        _i += n;
    else
        _i++;       // Handle case where no argument is passed.
    return *this;
}
int main()
{
   Int i;
   i.operator++( 25 ); // Increment by 25.
}
```

Neexistuje žádná syntaxe pro použití operátorů zvýšení nebo snížení pro předání těchto hodnot jinak než explicitním voláním, jak je uvedeno v předchozím kódu. Jednodušším způsobem implementace této funkce je přetížení operátoru sčítání/přiřazení (**+=**).

## <a name="see-also"></a>Viz také:

[Přetížení operátoru](../cpp/operator-overloading.md)