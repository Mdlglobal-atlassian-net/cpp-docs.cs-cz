---
title: Delegování konstruktorů (C++)
description: Použití delegování konstruktory v jazyce C++ vyvolat jiné konstruktory a snížit opakování kódu.
ms.date: 11/19/2019
ms.openlocfilehash: f26a013aa3c081d900ffc3eb32649acc77505db0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316676"
---
# <a name="delegating-constructors"></a>Delegování konstruktorů

Mnoho tříd má více konstruktorů, které dělají podobné věci – například ověřit parametry:

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

Můžete snížit opakující se kód přidáním funkce, která provádí všechny ověření, `class_c` ale kód pro by bylo snazší pochopit a udržovat, pokud jeden konstruktor mohl delegovat některé práce na jinou. Chcete-li přidat delegující konstruktory, použijte syntaxi: `constructor (. . .) : constructor (. . .)`

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

Při procházení předchozího příkladu si všimněte, že `class_c(int, int, int)` `class_c(int, int)`konstruktor nejprve `class_c(int)`volá konstruktor , který zase volá . Každý z konstruktorů provádí pouze práci, která není provedena jinými konstruktory.

První konstruktor, který se nazývá inicializovat objekt tak, aby všechny jeho členy jsou inicializovány v tomto okamžiku. Nelze provést inicializaci člena v konstruktoru, který deleguje na jiný konstruktor, jak je znázorněno zde:

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

Následující příklad ukazuje použití nestatických inicializátorů datových členů. Všimněte si, že pokud konstruktor také inicializuje daný datový člen, inicializátor člena je přepsán:

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

Syntaxe delegování konstruktoru nebrání náhodnému vytvoření rekurze konstruktoru – Constructor1 volá Constructor2, který volá Constructor1 – a žádné chyby jsou vyvolány, dokud není přetečení zásobníku. Je vaší zodpovědností vyhnout se cyklům.

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
