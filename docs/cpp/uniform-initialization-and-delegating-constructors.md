---
title: Jednotná inicializace a delegování konstruktorů
ms.date: 11/04/2016
ms.assetid: aa4daa64-eaec-4a3c-ade4-d9325e31e9d4
ms.openlocfilehash: 5c5cb6421d9c8ce20f0c5e24de986ee50d9b2238
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62162106"
---
# <a name="uniform-initialization-and-delegating-constructors"></a>Jednotná inicializace a delegování konstruktorů

V moderním jazyce C++, můžete použít *složených závorek inicializace* pro každý typ, bez znaménko rovná se. Také vám pomůže Delegující konstruktory zjednodušit kód, když máte víc konstruktorů, které provádějí podobné úkoly.

## <a name="brace-initialization"></a>Inicializace složenou závorku

Inicializaci složenými můžete použít pro všechny třídy, struktury nebo sjednocení. Pokud má typ výchozí konstruktor, implicitně nebo explicitně deklarován, můžete použít výchozí inicializace složenou závorku (pomocí prázdné závorky). Například následující třídy mohou být inicializovány pomocí výchozí a inicializaci složenými nevýchozí:

```cpp
#include <string>
using namespace std;

class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : m_string{ str }, m_double{ dbl } {}
double m_double;
string m_string;
};

int main()
{
    class_a c1{};
    class_a c1_1;

    class_a c2{ "ww" };
    class_a c2_1("xx");

    // order of parameters is the same as the constructor
    class_a c3{ "yy", 4.4 };
    class_a c3_1("zz", 5.5);
}
```

Pokud třída má nevýchozí konstruktory, je pořadí, ve kterém se zobrazí odpovídající parametry v konstruktoru, není pořadí, ve kterém jsou členy deklarované pořadí, ve které třídy členů zobrazují v inicializátoru složenou závorku (stejně jako u `class_a` v předchozí příklad). Jinak Pokud typ nemá žádný konstruktor deklarovaný, pořadí, ve kterém se zobrazí členy v inicializátoru složenou závorku je stejné jako pořadí, ve kterém jsou deklarovány; v takovém případě můžete inicializovat tolik veřejné členy jak chcete, ale nelze přeskočit žádný člen. Následující příklad ukazuje pořadí, ve kterém se používá v inicializaci složenými, pokud neexistuje žádná deklarovaná konstruktor:

```cpp
class class_d {
public:
    float m_float;
    string m_string;
    wchar_t m_char;
};

int main()
{
    class_d d1{};
    class_d d1{ 4.5 };
    class_d d2{ 4.5, "string" };
    class_d d3{ 4.5, "string", 'c' };

    class_d d4{ "string", 'c' }; // compiler error
    class_d d5("string", 'c', 2.0 }; // compiler error
}
```

Pokud výchozí konstruktor explicitně deklarován ale označena k odstranění, nelze ji použít výchozí inicializaci složenými:

```cpp
class class_f {
public:
    class_f() = delete;
    class_f(string x): m_string { x } {}
    string m_string;
};
int main()
{
    class_f cf{ "hello" };
    class_f cf1{}; // compiler error C2280: attempting to reference a deleted function
}
```

Můžete použít k inicializaci složenými kdekoli by obvykle provést inicializaci – například jako funkce parametr nebo návratovou hodnotu, nebo se **nové** – klíčové slovo:

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

## <a name="initializerlist-constructors"></a>objekt initializer_list konstruktory

[Initializer_list – třída](../standard-library/initializer-list-class.md) reprezentuje seznam objektů zadaného typu, který lze použít v konstruktoru a v jiném kontextu. Objekt initializer_list můžete sestavit s využitím inicializaci složenými:

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
>  Chcete-li použít tuto třídu, musíte zahrnout [ \<initializer_list >](../standard-library/initializer-list.md) záhlaví.

`initializer_list` Je možné zkopírovat. V takovém případě členy nového seznamu jsou odkazy na členy původního seznamu:

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

Třídy kontejnerů standardní knihovny a také `string`, `wstring`, a `regex`, mají `initializer_list` konstruktory. Následující příklady znázorňují způsob inicializace pomocí těchto konstruktorů uzavírat do složených závorek:

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{'x', 'y', 'z'};
```

## <a name="delegating-constructors"></a>Delegování konstruktorů

Mnoho třídy mají více konstruktorů, které podobné práce – například ověřit parametry:

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

Může omezení opakování kódu tak, že přidáte funkci, která nemá všech ověření, ale kód `class_c` bude snadněji pochopit a udržovat-li jeden konstruktor může delegovat některé úkoly ke druhé hodnotě. Chcete-li přidat Delegující konstruktory, použijte `constructor (. . .) : constructor (. . .)` syntaxi:

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

Krocích předchozího příkladu, Všimněte si, že konstruktor `class_c(int, int, int)` nejprve volá konstruktor `class_c(int, int)`, která pak volá `class_c(int)`. Každá z konstruktorů provádí pouze práce, která neprovádí se konstruktory.

První konstruktor, který se nazývá inicializuje objekt tak, aby všichni její členové jsou inicializovány v daném okamžiku. Inicializace členů v konstruktoru, který se delegoval vůči jiným konstruktorem, nelze provést, jak je znázorněno zde:

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

Následující příklad ukazuje použití inicializátory nestatických dat člena. Všimněte si, že pokud konstruktor inicializuje také členem daného data, je přepsána inicializátor členu:

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

Syntaxe delegování konstruktoru není zabránit náhodnému vytvoření konstruktoru rekurze – Constructor1 volá Constructor2, která volá Constructor1 – a nejsou vyvolány žádné chyby, dokud nedojde k přetečení zásobníku. Je vaší odpovědností, abyste se vyhnuli cykly.

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