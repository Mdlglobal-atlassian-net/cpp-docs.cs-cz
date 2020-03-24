---
title: Přetížení operátoru inkrementace a dekrementace (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
ms.openlocfilehash: 8d64f0af994f88d0f4ecd3a5921de4a16b8bdaaa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178282"
---
# <a name="increment-and-decrement-operator-overloading-c"></a>Přetížení operátoru inkrementace a dekrementace (C++)

Operátory zvýšení a snížení spadají do zvláštní kategorie, protože existují dvě varianty každého z nich:

- Preinkrement a postinkrement

- Predekrement a postdekrement

Při zápisu funkcí přetížených operátorů může být užitečné implementovat samostatné verze pro předponovou a příponovou verzi těchto operátorů. Aby bylo možné rozlišovat mezi nimi, je zjištěno následující pravidlo: předponová forma operátoru je deklarována přesně stejným způsobem jako jakýkoli jiný unární operátor; formulář přípony přijímá další argument typu **int**.

> [!NOTE]
>  Při zadání přetíženého operátoru pro příponový tvar operátoru zvýšení nebo snížení musí být dodatečný argument typu **int**; zadání jiného typu vygeneruje chybu.

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

Argument typu **int** , který označuje příponový tvar operátoru zvýšení nebo snížení, se běžně nepoužívá k předávání argumentů. Obvykle obsahuje hodnotu 0. Lze jej však použít následujícím způsobem:

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

Neexistuje žádná syntaxe pro použití operátorů zvýšení nebo snížení pro předání těchto hodnot jinak než explicitním voláním, jak je uvedeno v předchozím kódu. Jednodušší způsob implementace této funkce je přetížení operátoru sčítání a přiřazení ( **+=** ).

## <a name="see-also"></a>Viz také

[Přetížení operátoru](../cpp/operator-overloading.md)
