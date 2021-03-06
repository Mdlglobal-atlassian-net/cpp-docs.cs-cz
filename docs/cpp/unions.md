---
title: Sjednocení
ms.date: 05/06/2019
f1_keywords:
- union_cpp
helpviewer_keywords:
- class types [C++], unions as
- union keyword [C++]
ms.assetid: 25c4e219-fcbb-4b7b-9b64-83f3252a92ca
ms.openlocfilehash: 74e215204ef334bb67e8f044622d35f4e76fe401
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187957"
---
# <a name="unions"></a>Sjednocení

> [!NOTE]
> V C++ 17 a novějších je třída **std:: variant** typově bezpečná alternativa pro sjednocení.

**Sjednocení** je uživatelem definovaný typ, ve kterém všichni členové sdílejí stejné umístění v paměti. To znamená, že v daném okamžiku sjednocení nemůže obsahovat více než jeden objekt ze svého seznamu členů. Také to znamená, že bez ohledu na to, kolik členů má sjednocení, vždy používá dostatek paměti k uložení největšího člena.

Sjednocení můžou být užitečná při zachování paměti, když máte spoustu objektů a/nebo omezené paměti. Vyžadují navíc správné použití, protože zodpovídáte za to, že budete mít vždycky přístup k poslednímu členovi, ke kterému jste se zapsali. Pokud kterýkoli typ člena má netriviální konstruktor, musíte napsat další kód pro explicitní sestavení a zničení tohoto člena. Před použitím sjednocení zvažte, jestli problém, který se snažíte vyřešit, může být lepší vyjádřit pomocí základní třídy a odvozených tříd.

## <a name="syntax"></a>Syntaxe

```cpp
union [name]  { member-list };
```

### <a name="parameters"></a>Parametry

*Jméno*<br/>
Název typu sjednocení.

*seznam členů*<br/>
Členy, které může sjednocení obsahovat. Viz poznámky.

## <a name="remarks"></a>Poznámky

## <a name="declaring-a-union"></a>Deklarace sjednocení

Zahajte deklaraci sjednocení s klíčovým slovem **Union** a vložte seznam členů do složených závorek:

```cpp
// declaring_a_union.cpp
union RecordType    // Declare a simple union type
{
    char   ch;
    int    i;
    long   l;
    float  f;
    double d;
    int *int_ptr;
};
int main()
{
    RecordType t;
    t.i = 5; // t holds an int
    t.f = 7.25; // t now holds a float
}
```

## <a name="using-unions"></a>Použití sjednocení

V předchozím příkladu musí jakýkoli kód, který přistupuje ke sjednocení, znát, který člen drží data. Nejběžnějším řešením tohoto problému je uzavření sjednocení do struktury spolu s dalším členem výčtu, který určuje typ dat, která jsou aktuálně ukládána do sjednocení. To se označuje jako *rozlišené sjednocení* a následující příklad ukazuje základní vzor.

```cpp
#include <queue>

using namespace std;

enum class WeatherDataType
{
    Temperature, Wind
};

struct TempData
{
    int StationId;
    time_t time;
    double current;
    double max;
    double min;
};

struct WindData
{
    int StationId;
    time_t time;
    int speed;
    short direction;
};

struct Input
{
    WeatherDataType type;
    union
    {
        TempData temp;
        WindData wind;
    };
};

// Functions that are specific to data types
void Process_Temp(TempData t) {}
void Process_Wind(WindData w) {}

// Container for all the data records
queue<Input> inputs;
void Initialize();

int main(int argc, char* argv[])
{
    Initialize();
    while (!inputs.empty())
    {
        Input i = inputs.front();
        switch (i.type)
        {
        case WeatherDataType::Temperature:
            Process_Temp(i.temp);
            break;
        case WeatherDataType::Wind:
            Process_Wind(i.wind);
            break;
        default:
            break;
        }
        inputs.pop();

    }
    return 0;
}

void Initialize()
{
    Input first, second;
    first.type = WeatherDataType::Temperature;
    first.temp = { 101, 1418855664, 91.8, 108.5, 67.2 };
    inputs.push(first);

    second.type = WeatherDataType::Wind;
    second.wind = { 204,1418859354, 14, 27 };
    inputs.push(second);
}
```

V předchozím příkladu si všimněte, že sjednocení ve vstupní struktuře nemá žádný název. Toto je anonymní sjednocení a jeho členové mají přístup, jako kdyby byli přímými členy struktury. Další informace o anonymních sjednoceních najdete v části níže.

Samozřejmě předchozí příklad ukazuje problém, který lze také vyřešit pomocí tříd odvozených ze společné základní třídy a větvení kódu na základě typu modulu runtime každého objektu v kontejneru. Výsledkem může být kód, který usnadňuje údržbu a pochopení, ale může být také pomalejší než použití sjednocení. Pomocí sjednocení můžete také ukládat zcela nesouvisející typy a dynamicky měnit typ hodnoty, která je uložena bez změny typu proměnné sjednocení. Proto můžete vytvořit heterogenní pole MyUnionType, jehož prvky ukládají různé hodnoty různých typů.

Všimněte si, že struktura `Input` v předchozím příkladu se dá snadno zneužít. Pro přístup ke členu, který obsahuje data, je zcela na uživatele správně použit diskriminátor. Ochranu před zneužitím můžete zajistit tak, že vytvoříte soukromou unii a poskytnete speciální funkce přístupu, jak je znázorněno v následujícím příkladu.

## <a name="unrestricted-unions-c11"></a>Neomezená sjednocení (C++ 11)

V jazyce C++ 03 a dříve může sjednocení obsahovat nestatické datové členy s typem třídy, pokud typ nemá žádné uživatelem poskytnuté konstruktory, destruktory nebo operátory přiřazení. V jazyce C++ 11 jsou tato omezení odebrána. Pokud zahrnete takového člena do vaší unie, kompilátor automaticky označí všechny zvláštní členské funkce, které nejsou zadány uživatelem jako odstraněné. Pokud je sjednocení anonymního sjednocení uvnitř třídy nebo struktury, pak jsou všechny zvláštní členské funkce třídy nebo struktury, které nejsou zadány uživatelem, označeny jako odstraněné. Následující příklad ukazuje, jak zpracovat případ, kdy jeden z členů sjednocení má člena, který vyžaduje Toto speciální zacházení:

```cpp
// for MyVariant
#include <crtdbg.h>
#include <new>
#include <utility>

// for sample objects and output
#include <string>
#include <vector>
#include <iostream>

using namespace std;

struct A
{
    A() = default;
    A(int i, const string& str) : num(i), name(str) {}

    int num;
    string name;
    //...
};

struct B
{
    B() = default;
    B(int i, const string& str) : num(i), name(str) {}

    int num;
    string name;
    vector<int> vec;
    // ...
};

enum class Kind { None, A, B, Integer };

#pragma warning (push)
#pragma warning(disable:4624)
class MyVariant
{
public:
    MyVariant()
        : kind_(Kind::None)
    {
    }

    MyVariant(Kind kind)
        : kind_(kind)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A();
            break;
        case Kind::B:
            new (&b_) B();
            break;
        case Kind::Integer:
            i_ = 0;
            break;
        default:
            _ASSERT(false);
            break;
        }
    }

    ~MyVariant()
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            a_.~A();
            break;
        case Kind::B:
            b_.~B();
            break;
        case Kind::Integer:
            break;
        default:
            _ASSERT(false);
            break;
        }
        kind_ = Kind::None;
    }

    MyVariant(const MyVariant& other)
        : kind_(other.kind_)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A(other.a_);
            break;
        case Kind::B:
            new (&b_) B(other.b_);
            break;
        case Kind::Integer:
            i_ = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
    }

    MyVariant(MyVariant&& other)
        : kind_(other.kind_)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A(move(other.a_));
            break;
        case Kind::B:
            new (&b_) B(move(other.b_));
            break;
        case Kind::Integer:
            i_ = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
        other.kind_ = Kind::None;
    }

    MyVariant& operator=(const MyVariant& other)
    {
        if (&other != this)
        {
            switch (other.kind_)
            {
            case Kind::None:
                this->~MyVariant();
                break;
            case Kind::A:
                *this = other.a_;
                break;
            case Kind::B:
                *this = other.b_;
                break;
            case Kind::Integer:
                *this = other.i_;
                break;
            default:
                _ASSERT(false);
                break;
            }
        }
        return *this;
    }

    MyVariant& operator=(MyVariant&& other)
    {
        _ASSERT(this != &other);
        switch (other.kind_)
        {
        case Kind::None:
            this->~MyVariant();
            break;
        case Kind::A:
            *this = move(other.a_);
            break;
        case Kind::B:
            *this = move(other.b_);
            break;
        case Kind::Integer:
            *this = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
        other.kind_ = Kind::None;
        return *this;
    }

    MyVariant(const A& a)
        : kind_(Kind::A), a_(a)
    {
    }

    MyVariant(A&& a)
        : kind_(Kind::A), a_(move(a))
    {
    }

    MyVariant& operator=(const A& a)
    {
        if (kind_ != Kind::A)
        {
            this->~MyVariant();
            new (this) MyVariant(a);
        }
        else
        {
            a_ = a;
        }
        return *this;
    }

    MyVariant& operator=(A&& a)
    {
        if (kind_ != Kind::A)
        {
            this->~MyVariant();
            new (this) MyVariant(move(a));
        }
        else
        {
            a_ = move(a);
        }
        return *this;
    }

    MyVariant(const B& b)
        : kind_(Kind::B), b_(b)
    {
    }

    MyVariant(B&& b)
        : kind_(Kind::B), b_(move(b))
    {
    }

    MyVariant& operator=(const B& b)
    {
        if (kind_ != Kind::B)
        {
            this->~MyVariant();
            new (this) MyVariant(b);
        }
        else
        {
            b_ = b;
        }
        return *this;
    }

    MyVariant& operator=(B&& b)
    {
        if (kind_ != Kind::B)
        {
            this->~MyVariant();
            new (this) MyVariant(move(b));
        }
        else
        {
            b_ = move(b);
        }
        return *this;
    }

    MyVariant(int i)
        : kind_(Kind::Integer), i_(i)
    {
    }

    MyVariant& operator=(int i)
    {
        if (kind_ != Kind::Integer)
        {
            this->~MyVariant();
            new (this) MyVariant(i);
        }
        else
        {
            i_ = i;
        }
        return *this;
    }

    Kind GetKind() const
    {
        return kind_;
    }

    A& GetA()
    {
        _ASSERT(kind_ == Kind::A);
        return a_;
    }

    const A& GetA() const
    {
        _ASSERT(kind_ == Kind::A);
        return a_;
    }

    B& GetB()
    {
        _ASSERT(kind_ == Kind::B);
        return b_;
    }

    const B& GetB() const
    {
        _ASSERT(kind_ == Kind::B);
        return b_;
    }

    int& GetInteger()
    {
        _ASSERT(kind_ == Kind::Integer);
        return i_;
    }

    const int& GetInteger() const
    {
        _ASSERT(kind_ == Kind::Integer);
        return i_;
    }

private:
    Kind kind_;
    union
    {
        A a_;
        B b_;
        int i_;
    };
};
#pragma warning (pop)

int main()
{
    A a(1, "Hello from A");
    B b(2, "Hello from B");

    MyVariant mv_1 = a;

    cout << "mv_1 = a: " << mv_1.GetA().name << endl;
    mv_1 = b;
    cout << "mv_1 = b: " << mv_1.GetB().name << endl;
    mv_1 = A(3, "hello again from A");
    cout << R"aaa(mv_1 = A(3, "hello again from A"): )aaa" << mv_1.GetA().name << endl;
    mv_1 = 42;
    cout << "mv_1 = 42: " << mv_1.GetInteger() << endl;

    b.vec = { 10,20,30,40,50 };

    mv_1 = move(b);
    cout << "After move, mv_1 = b: vec.size = " << mv_1.GetB().vec.size() << endl;

    cout << endl << "Press a letter" << endl;
    char c;
    cin >> c;
}
#include <queue>
#include <iostream>
using namespace std;

enum class WeatherDataType
{
    Temperature, Wind
};

struct TempData
{
    TempData() : StationId(""), time(0), current(0), maxTemp(0), minTemp(0) {}
    TempData(string id, time_t t, double cur, double max, double min)
        : StationId(id), time(t), current(cur), maxTemp(max), minTemp(0) {}
    string StationId;
    time_t time = 0;
    double current;
    double maxTemp;
    double minTemp;
};

struct WindData
{
    int StationId;
    time_t time;
    int speed;
    short direction;
};

struct Input
{
    Input() {}
    Input(const Input&) {}

    ~Input()
    {
        if (type == WeatherDataType::Temperature)
        {
            temp.StationId.~string();
        }
    }

    WeatherDataType type;
    void SetTemp(const TempData& td)
    {
        type = WeatherDataType::Temperature;

        // must use placement new because of string member!
        new(&temp) TempData(td);
    }

    TempData GetTemp()
    {
        if (type == WeatherDataType::Temperature)
            return temp;
        else
            throw logic_error("Can't return TempData when Input holds a WindData");
    }
    void SetWind(WindData wd)
    {
        // Explicitly delete struct member that has a
        // non-trivial constructor
        if (type == WeatherDataType::Temperature)
        {
            temp.StationId.~string();
        }
        wind = wd; //placement new not required.
    }
    WindData GetWind()
    {
        if (type == WeatherDataType::Wind)
        {
            return wind;
        }
        else
            throw logic_error("Can't return WindData when Input holds a TempData");
    }

private:

    union
    {
        TempData temp;
        WindData wind;
    };
};
```

Sjednocení nemůžou ukládat odkazy. Sjednocení nepodporují dědění, proto nejde samotného sjednocení použít jako základní třídu nebo dědit z jiné třídy nebo mít virtuální funkce.

## <a name="initializing-unions"></a>Inicializace sjednocení

Sjednocení lze deklarovat a inicializovat v jednom příkazu přiřazením výrazu uzavřeného v závorkách. Výraz je vyhodnocen a přiřazen do prvního pole ve sjednocení.

```cpp
#include <iostream>
using namespace std;

union NumericType
{
    short       iValue;
    long        lValue;
    double      dValue;
};

int main()
{
    union NumericType Values = { 10 };   // iValue = 10
    cout << Values.iValue << endl;
    Values.dValue = 3.1416;
    cout << Values.dValue) << endl;
}
/* Output:
10
3.141600
*/
```

Sjednocení `NumericType` je v paměti uspořádáno (obecně) tak, jak ukazuje následující obrázek.

![Úložiště dat v rámci sjednocení číselného typu](../cpp/media/vc38ul1.png "Ukládání dat v NumericType sjednocení") <br/>
Uložení dat ve sjednocení NumericType

## <a name="anonymous-unions"></a><a name="anonymous_unions"></a>Anonymní sjednocení

Anonymní sjednocení jsou sjednocení, která jsou deklarována bez *názvu třídy* nebo *deklarátor-list*.

```cpp
union  {  member-list  }
```

Názvy deklarované v anonymním sjednocení se používají přímo jako nečlenské proměnné. Proto názvy deklarované v anonymním sjednocení musí být v okolním oboru jedinečné.

Kromě omezení pro pojmenovaná sjednocení se anonymním sjednocením vztahují tato další omezení:

- Musí být také deklarovány jako **static** , pokud jsou deklarovány v oboru názvů File nebo Namespace.

- Můžou mít jenom **veřejné** členy; **soukromé** a **chráněné** členy v anonymních sjednoceních generují chyby.

- Nemohou mít členské funkce.

## <a name="see-also"></a>Viz také

[Třídy a struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[class](../cpp/class-cpp.md)<br/>
[struct](../cpp/struct-cpp.md)
