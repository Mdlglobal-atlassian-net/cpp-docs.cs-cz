---
title: "Sjednocení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: union_cpp
dev_langs: C++
helpviewer_keywords:
- class types [C++], unions as
- union keyword [C++]
ms.assetid: 25c4e219-fcbb-4b7b-9b64-83f3252a92ca
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9371aaf978f2ea9498445d0124b9be16cf3b0fa7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="unions"></a>Sjednocení
A `union` je uživatelsky definovaný typ., ve kterém všichni členové sdílet stejné umístění paměti. To znamená, že v každém okamžiku sjednocení může obsahovat více než jeden objekt z jeho seznam členů. Taky to znamená, že bez ohledu na to, kolik členů sjednocení má vždy používá jenom dostatek paměti k uložení největší člena.  
  
 Sjednocení může být užitečné při zachovávání paměti, když máte velký počet objektů nebo omezené pamětí. Ale vyžadují zvláštní pozornost použít správně, protože jste zodpovědní za posledním členem, která byla zapsána do vždy přístup zajistí. Pokud všechny typy členů nejsou v netriviálních konstruktor, musíte napsat další kód explicitně vytvořit a zrušení tohoto člena. Před použitím spojení, zvažte, jestli problému, který se snažíte vyřešit může lépe vyjádřit pomocí základní třída a odvozené třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
union [name]  { member-list };  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název typu sjednocení.  
  
 `member-list`  
 Členové, které mohou obsahovat sjednocení. V části poznámky.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="declaring-a-union"></a>Deklarace sjednocení  
 Zahájit deklarace sjednocení s `union` – klíčové slovo a seznam členů uzavřít do složených závorek:  
  
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
    t.f = 7.25 // t now holds a float   
}  
```  
  
## <a name="using-unions"></a>Pomocí sjednocení  
 V předchozím příkladu je potřeba vědět, které člen není podržíte data kód, který přistupuje k sjednocení. Nejběžnější řešení tohoto problému je uzavřete sjednocení v společně s člena další výčtu, který označuje typ dat, které jsou aktuálně uloženy v sjednocení struktury. Tento postup se nazývá *rozlišované sjednocení* a následující příklad ukazuje základní vzor.  
  
```cpp  
#include "stdafx.h"  
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
  
 V předchozím příkladu Všimněte si, že sjednocení v vstup struktura nemá žádný název. Toto je anonymní sjednocení a její členy přístupná, jako kdyby byly přímé členy dané struktury. Další informace o anonymní sjednocení najdete v části níže.  
  
 Samozřejmě ukazuje předchozí příklad problém, který může také vyřešit pomocí třídy, které jsou odvozeny od obecná základní třída a vytvoření větve kódu na základě typu runtime jednotlivých objektů v kontejneru. To může mít za následek kódu, že jednodušší je spravovat a pochopit, ale může být také pomalejší než použití sjednocení. Navíc s union, můžete ukládat zcela nesouvisejícími typy a dynamicky měnit typ hodnotou, která je uložená beze změny typu union proměnné sám sebe. Můžete vytvořit tak heterogenní pole MyUnionType, jehož elementy uložení různých hodnot různých typů.  
  
 Všimněte si, že `Input` struktura v předchozím příkladu lze snadno chybná. Je zcela uživateli umožňuje využít diskriminátoru správně pro přístup k členovi, který obsahuje data. Můžete se chránit proti zneužití tím, že privátní sjednocení a poskytování zvláštní přístup funguje, jak je znázorněno v následujícím příkladu.  
  
## <a name="unrestricted-unions-c11"></a>Neomezený sjednocení (C ++ 11)  
 V C ++ 03 a starší sjednocení mohou obsahovat členy nestatické dat s typu třídy, tak dlouho, dokud typ nemá žádnou uživatel zadal konstruktory, destruktory nebo operátory přiřazení. V C ++ 11 Tato omezení odebrané. Pokud zahrnete tento člen vaší sjednocení pak kompilátor automaticky označíte žádné speciální členské funkce, které nejsou uživatel zadal jako odstraněný. Pokud anonymní – typ union ve třídě nebo struktuře sjednocení se žádné speciální členské funkce tříd nebo struktura, které nejsou uživatel zadal jsou označeny jako odstraněné. Následující příklad ukazuje, jak zpracovávat tento případ, kdy jednoho z členů sjednocení má člena, který vyžaduje tento zvláštní zacházení:  
  
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
  
 Sjednocení nelze uložit odkazy. Sjednocení nepodporují dědičnosti, proto spojení sama nelze použít jako základní třída, dědí z jiné třídy nebo na virtuální funkce.  
  
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
  
 ![Úložiště dat v číselného typu union](../cpp/media/vc38ul1.png "vc38UL1")  
Uložení dat ve sjednocení NumericType  
  
## <a name="anonymous_unions"></a>Anonymní sjednocení  
 Anonymní sjednocení jsou spojení, které jsou deklarované bez *název třídy* nebo *deklarátor seznamu*.  
  
```cpp  
union  {  member-list  }    
```  
  
Názvy deklarované v anonymním sjednocení se používají přímo jako nečlenské proměnné. Názvy v anonymní sjednocení deklarována proto musí být jedinečné v okolního oboru.  
  
Kromě omezení pro pojmenované sjednocení anonymní sjednocení se vztahují tyto další omezení:  
  
-   Musí být také deklarována jako **statické** Pokud deklarován v souboru nebo oboru názvů oboru.  
  
-   Mohou mít pouze veřejné členy. Soukromé a chráněné členy v anonymních sjednoceních generují chyby.  
  
-   Členské funkce nemohou mít.  
  
## <a name="see-also"></a>Viz také  
 [Třídy a struktury](../cpp/classes-and-structs-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [– Třída](../cpp/class-cpp.md)   
 [struct](../cpp/struct-cpp.md)