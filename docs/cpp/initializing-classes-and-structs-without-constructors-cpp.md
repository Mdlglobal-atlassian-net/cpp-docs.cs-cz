---
title: Inicializace ortézy pro třídy, struktury a sjednocení
description: Použití inicializace složených závorek s libovolnou třídou, strukturou nebo sjednocením jazyka C++
ms.date: 11/19/2019
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 4628ffe8935fc32e86468c631d5d9e9622d63d2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374077"
---
# <a name="brace-initialization"></a>Inicializace složenými závorkami

Není vždy nutné definovat konstruktor pro třídu, zejména ty, které jsou poměrně jednoduché. Uživatelé mohou inicializovat objekty třídy nebo struktury pomocí jednotné inicializace, jak je znázorněno v následujícím příkladu:

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

Všimněte si, že když třída nebo struktura nemá žádný konstruktor, zadáte prvky seznamu v pořadí, ve které jsou členové deklarováni ve třídě. Pokud třída má konstruktor, zadejte prvky v pořadí parametrů. Pokud má typ výchozí konstruktor, implicitně nebo explicitně deklarovaný, můžete použít výchozí inicializaci závorky (s prázdnými závorkami). Například následující třída může být inicializována pomocí výchozí i nevýchozí inicializace závorky:

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

Pokud třída má nevýchozí konstruktory, pořadí, ve kterém se členové třídy zobrazují v inicializátoru závorky, je pořadí, `class_a` ve kterém se odpovídající parametry zobrazují v konstruktoru, nikoli pořadí, ve kterém jsou členy deklarovány (jako v předchozím příkladu). V opačném případě, pokud typ nemá deklarovaný konstruktor, pořadí, ve kterém se členy zobrazí v inicializátoru závorky, je stejné jako pořadí, ve kterém jsou deklarovány; V takovém případě můžete inicializovat libovolný počet veřejných členů, ale nelze přeskočit žádného člena. Následující příklad ukazuje pořadí, které se používá v inicializaci závorky, pokud neexistuje žádný deklarovaný konstruktor:

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

Pokud je výchozí konstruktor explicitně deklarován, ale označen jako odstraněný, nelze použít výchozí inicializaci složených závorek:

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

Inicializaci složených závorek můžete použít kdekoli, kde obvykle inicializaci provést – například jako parametr funkce nebo vrácenou hodnotu nebo s **novým** klíčovým slovem:

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

V režimu **/std:c++17** jsou pravidla pro inicializaci prázdné závorky o něco restriktivnější. Viz [Odvozené konstruktory a rozšířené agregace inicializace](constructors-cpp.md#extended_aggregate).

## <a name="initializer_list-constructors"></a>initializer_list konstruktory

[Initializer_list Class](../standard-library/initializer-list-class.md) představuje seznam objektů zadaného typu, které lze použít v konstruktoru a v jiných kontextech. Initializer_list můžete vytvořit pomocí inicializace závorky:

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
> Chcete-li použít tuto třídu, [ \<](../standard-library/initializer-list.md) musíte zahrnout initializer_list>záhlaví.

A `initializer_list` lze zkopírovat. V tomto případě jsou členy nového seznamu odkazy na členy původního seznamu:

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

Standardní třídy kontejnerů `string`knihovny `regex`a `initializer_list` také , `wstring`a , mají konstruktory. Následující příklady ukazují, jak provést inicializaci svorek s těmito konstruktory:

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{ 'x', 'y', 'z' };
```

## <a name="see-also"></a>Viz také

[Třídy a struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Konstruktory](../cpp/constructors-cpp.md)
