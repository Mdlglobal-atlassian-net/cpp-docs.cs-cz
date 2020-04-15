---
title: Přetížení operátoru inkrementace a dekrementace (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
ms.openlocfilehash: 40ae12130fdced9fd958c3b8316fa3b718ca9b5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374121"
---
# <a name="increment-and-decrement-operator-overloading-c"></a>Přetížení operátoru inkrementace a dekrementace (C++)

Operátory zvýšení a snížení spadají do zvláštní kategorie, protože existují dvě varianty každého z nich:

- Preinkrement a postinkrement

- Predekrement a postdekrement

Při zápisu funkcí přetížených operátorů může být užitečné implementovat samostatné verze pro předponovou a příponovou verzi těchto operátorů. Chcete-li rozlišovat mezi těmito dvěma, je dodrženo následující pravidlo: Předpona forma operátoru je deklarována přesně stejným způsobem jako jakýkoli jiný unární operátor; Formulář přípony přijímá další argument typu **int**.

> [!NOTE]
> Při zadávání přetížené operátor pro formulář přípony přírůstek nebo snížení operátoru, další argument musí být typu **int**; zadání jiného typu vygeneruje chybu.

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

Argument typu **int,** který označuje formulář přípony operátoru přírůstek nebo snížení, se běžně nepoužívá k předání argumentů. Obvykle obsahuje hodnotu 0. Lze jej však použít následujícím způsobem:

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

Neexistuje žádná syntaxe pro použití operátorů zvýšení nebo snížení pro předání těchto hodnot jinak než explicitním voláním, jak je uvedeno v předchozím kódu. Jednodušší způsob, jak implementovat tuto funkci je přetížení**+=** operátor sčítání/přiřazení ( ).

## <a name="see-also"></a>Viz také

[Přetížení operátora](../cpp/operator-overloading.md)
