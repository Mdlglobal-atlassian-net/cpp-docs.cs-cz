---
title: Přiřazení
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: f1697a8de3dff6c46de01db6bbff5447c03b6282
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190700"
---
# <a name="assignment"></a>Přiřazení

Operátor přiřazení ( **=** ) je, striktně řečeno, binární operátor. Jeho deklarace je stejná jako u ostatních binárních operátorů, s následujícími výjimkami:

- Musí to být funkce nestatického členu. **Operátor No =** nelze deklarovat jako nečlenskou funkci.
- Není zděděn z odvozené třídy.
- Výchozí **operátor =** funkce může být generován kompilátorem pro typy tříd, pokud žádná neexistuje.

Následující příklad ukazuje, jak deklarovat operátor přiřazení:

```cpp
class Point
{
public:
    int _x, _y;

    // Right side of copy assignment is the argument.
    Point& operator=(const Point&);
};

// Define copy assignment operator.
Point& Point::operator=(const Point& otherPoint)
{
    _x = otherPoint._x;
    _y = otherPoint._y;

    // Assignment operator returns left side of assignment.
    return *this;
}

int main()
{
    Point pt1, pt2;
    pt1 = pt2;
}
```

Zadaný argument je pravá strana výrazu. Operátor vrací objekt pro zachování chování operátoru přiřazení, který po dokončení přiřazení vrací hodnotu levé strany. To umožňuje řetězení přiřazení, například:

```cpp
pt1 = pt2 = pt3;
```

Operátor přiřazení kopie Nepleťe s kopírovacím konstruktorem. Druhá je volána během vytváření nového objektu z existujícího objektu:

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> Doporučuje se postupovat podle [pravidla tři](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) , které třída, která definuje operátor přiřazení kopie, musí explicitně definovat konstruktor Copy, destruktor a, počínaje c++ 11, přesunout konstruktor a operátor přiřazení přesunutí.

## <a name="see-also"></a>Viz také

- [Přetížení operátoru](../cpp/operator-overloading.md)
- [Konstruktory a operátory přiřazení pro kopírování (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)
