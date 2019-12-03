---
title: Inicializace složené závorky pro třídy, struktury a sjednocení
description: Použití inicializace složené závorky s C++ libovolnou třídou, strukturou nebo sjednocením
ms.date: 11/19/2019
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: c746c6e4c17e5a55475d70f6dc3d927088af579f
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683006"
---
# <a name="brace-initialization"></a>Inicializace složenými závorkami

Není vždy nutné definovat konstruktor pro třídu, zejména ty, které jsou relativně jednoduché. Uživatelé mohou inicializovat objekty třídy nebo struktury pomocí jednotné inicializace, jak je znázorněno v následujícím příkladu:

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

Všimněte si, že pokud třída nebo struktura nemá žádný konstruktor, zadejte prvky seznamu v pořadí, ve kterém jsou členy deklarovány ve třídě. Pokud třída má konstruktor, poskytněte prvky v pořadí parametrů. Pokud má typ výchozí konstruktor, buď implicitně nebo explicitně deklarovaný, můžete použít výchozí inicializaci složené závorky (s prázdnými závorkami). Například následující třída může být inicializována pomocí výchozí a nevýchozí inicializace složené závorky:

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

Pokud třída obsahuje jiné než výchozí konstruktory, pořadí, ve kterém jsou členy třídy zobrazeny v inicializátoru závorky, je pořadí, ve kterém jsou příslušné parametry zobrazeny v konstruktoru, nikoli pořadí, ve kterém jsou členy deklarovány (stejně jako u `class_a` v předchozím příkladu). V opačném případě, pokud typ nemá žádný deklarovaný konstruktor, pořadí, ve kterém se členy objeví v inicializátoru závorky, je stejné jako pořadí, ve kterém jsou deklarovány. v tomto případě můžete inicializovat libovolný počet veřejných členů, jak si přejete, ale nemůžete přeskočit žádného člena. Následující příklad ukazuje pořadí, které je použito při inicializaci závorky, pokud neexistuje žádný deklarovaný konstruktor:

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
    class_d d5{ "string", 'c', 2.0 }; // compiler error
}
```

Pokud je výchozí konstruktor explicitně deklarován, ale označen jako odstraněný, nelze použít výchozí inicializaci složené závorky:

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

Inicializaci složené závorky můžete použít všude, kde se obvykle provádí inicializace – například jako parametr funkce nebo návratová hodnota nebo s klíčovým slovem **New** :

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

## <a name="initializer_list-constructors"></a>initializer_list konstruktory

[Třída initializer_list](../standard-library/initializer-list-class.md) představuje seznam objektů zadaného typu, které lze použít v konstruktoru, a v jiných kontextech. Initializer_list lze vytvořit pomocí inicializace závorky:

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
>  Chcete-li použít tuto třídu, je nutné zahrnout hlavičku [\<initializer_list >](../standard-library/initializer-list.md) .

`initializer_list` lze zkopírovat. V tomto případě jsou členové nového seznamu odkazy na členy původního seznamu:

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

Třídy kontejnerů standardní knihovny a také `string`, `wstring`a `regex`, mají `initializer_list` konstruktory. Následující příklady ukazují, jak provést inicializaci složené závorky pomocí těchto konstruktorů:

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{'x', 'y', 'z'};
```


## <a name="see-also"></a>Viz také:

[Třídy a struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Konstruktory](../cpp/constructors-cpp.md)
