---
title: Přiřazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4955fb16d76bc68166bf314b9e1e8c02cd8e244
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131470"
---
# <a name="assignment"></a>Přiřazení

Operátor přiřazení (**=**) je, přesněji řečeno, binární operátor. Jeho deklarace je stejná jako u ostatních binárních operátorů, s následujícími výjimkami:

- Musí to být funkce nestatického členu. Ne **operátoru =** lze deklarovat jako nečlenskou funkci.
- Není zděděn z odvozené třídy.
- Výchozí **operátoru =** funkce mohou být generovány kompilátoru pro typy tříd, pokud žádný neexistuje.

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

Zadaný argument představuje pravou stranu výrazu. Operátor vrací objekt pro zachování chování operátoru přiřazení, který po dokončení přiřazení vrací hodnotu levé strany. Díky tomu řetězení přiřazení, jako například:

```cpp
pt1 = pt2 = pt3;
```

Operátor přiřazení kopie se by se zaměňovat s kopírovacím konstruktorem. Ten je volána v průběhu procesu vytváření nového objektu z existující:

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> Je vhodné postupovat podle [pravidlo tří](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) třídu, která definuje operátor přiřazení kopie by měl také explicitně definovat kopírovací konstruktor, destruktor a od verze C ++ 11, přesuňte přiřazení přesunutí a konstruktor operátor.

## <a name="see-also"></a>Viz také:

- [Přetížení operátoru](../cpp/operator-overloading.md)
- [Konstruktory a operátory přiřazení pro kopírování (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)