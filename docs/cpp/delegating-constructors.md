---
title: Delegování konstruktorů (C++)
description: Použijte delegování konstruktorů v C++ k vyvolání jiných konstruktorů a zmenšení opakování kódu.
ms.date: 11/19/2019
ms.openlocfilehash: 533cdfbeb882f3770cc554b0633611a4ffc2cfbd
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74250672"
---
# <a name="delegating-constructors"></a>Delegování konstruktorů

Mnoho tříd má více konstruktorů, které se podobají podobným účelům, například ověření parametrů:

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c() {}
    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
        middle = my_middle < max && my_middle > min ? my_middle : 5;
    }
};
```

Opakovaný kód můžete snížit přidáním funkce, která provádí všechna ověření, ale kód pro `class_c` by byl snazší pochopit a udržovat, pokud jeden konstruktor by mohl delegovat některé práce na jiný konstruktor. Chcete-li přidat konstruktory delegování, použijte syntaxi `constructor (. . .) : constructor (. . .)`:

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) : class_c(my_max) {
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){
        middle = my_middle < max && my_middle > min ? my_middle : 5;
}
};
int main() {

    class_c c1{ 1, 3, 2 };
}
```

Při procházení předchozího příkladu si všimněte, že konstruktor `class_c(int, int, int)` nejprve volá `class_c(int, int)`konstruktoru, který zase volá `class_c(int)`. Každý konstruktor provádí pouze práci, která není provedena jinými konstruktory.

První konstruktor, který je volán jako inicializuje objekt tak, aby všechny jeho členy byly inicializovány v daném okamžiku. Inicializace člena nelze provést v konstruktoru, který je delegátem jiného konstruktoru, jak je znázorněno zde:

```cpp
class class_a {
public:
    class_a() {}
    // member initialization here, no delegate
    class_a(string str) : m_string{ str } {}

    //can’t do member initialization here
    // error C3511: a call to a delegating constructor shall be the only member-initializer
    class_a(string str, double dbl) : class_a(str) , m_double{ dbl } {}

    // only member assignment
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string;
};
```

Následující příklad ukazuje použití nestatických inicializátorů členů dat. Všimněte si, že pokud konstruktor také inicializuje daný datový člen, inicializátor členu je přepsán:

```cpp
class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string{ m_double < 10.0 ? "alpha" : "beta" };
};

int main() {
    class_a a{ "hello", 2.0 };  //expect a.m_double == 2.0, a.m_string == "hello"
    int y = 4;
}
```

Syntaxe delegování konstruktoru nebrání nechtěnému vytvoření rekurze konstruktoru – Constructor1 volá Constructor2, která volá Constructor1 – a nejsou vyvolány žádné chyby, dokud nedojde k přetečení zásobníku. Je vaše zodpovědnost na to, abyste se vyhnuli cyklům.

```cpp
class class_f{
public:
    int max;
    int min;

    // don't do this
    class_f() : class_f(6, 3){ }
    class_f(int my_max, int my_min) : class_f() { }
};
```
