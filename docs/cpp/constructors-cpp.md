---
title: Konstruktory (C++)
ms.date: 12/27/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: 985c63c5c937f9e85b6898cdbcc61f347688b96d
ms.sourcegitcommit: 00f50ff242031d6069aa63c81bc013e432cae0cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/30/2019
ms.locfileid: "75546390"
---
# <a name="constructors-c"></a>Konstruktory (C++)

Chcete-li přizpůsobit způsob inicializace členů třídy nebo vyvolat funkce při vytvoření objektu třídy, definujte *konstruktor*. Konstruktor má stejný název jako třída a žádná návratová hodnota. Můžete definovat tolik přetížených konstruktorů, kolik jich je potřeba k přizpůsobení inicializace různým způsobem. Obvykle konstruktory mají veřejnou přístupnost, takže kód mimo definici třídy nebo Hierarchie dědičnosti může vytvořit objekty třídy. Můžete ale také deklarovat konstruktor jako **chráněný** nebo **soukromý**.

Konstruktory mohou volitelně převzít seznam inicializace členů. Toto je efektivnější způsob, jak inicializovat členy třídy než přiřazení hodnot v těle konstruktoru. Následující příklad ukazuje třídu `Box` se třemi přetíženými konstruktory. Poslední dva seznamy pro inicializaci členů použití:

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    explicit Box(int i) : m_width(i), m_length(i), m_height(i) // member init list
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}

    int Volume() { return m_width * m_length * m_height; }

private:
    // Will have value of 0 when default constructor is called.
    // If we didn't zero-init here, default constructor would
    // leave them uninitialized with garbage values.
    int m_width{ 0 };
    int m_length{ 0 };
    int m_height{ 0 };
};
```

Při deklaraci instance třídy kompilátor zvolí, který konstruktor se má vyvolat, na základě pravidel řešení přetížení:

```cpp
int main()
{
    Box b; // Calls Box()

    // Using uniform initialization (preferred):
    Box b2 {5}; // Calls Box(int)
    Box b3 {5, 8, 12}; // Calls Box(int, int, int)

    // Using function-style notation:
    Box b4(2, 4, 6); // Calls Box(int, int, int)
}
```

- Konstruktory mohou být deklarovány jako **inline**, [Explicit](#explicit_constructors), **Friend** nebo [constexpr](#constexpr_constructors).
- Konstruktor může inicializovat objekt, který byl deklarován jako **const**, **volatile** nebo **const volatile**. Objekt se bude **const** po dokončení konstruktoru.
- Chcete-li definovat konstruktor v implementačním souboru, poskytněte mu kvalifikovaný název jako u jakékoli jiné členské funkce: `Box::Box(){...}`.

## <a name="member_init_list"></a>Seznamy inicializátorů členů

Konstruktor může volitelně mít seznam inicializátorů členů, který inicializuje členy třídy před spuštěním těla konstruktoru. (Všimněte si, že seznam inicializátorů členů není stejný jako *seznam inicializátorů* typu [std:: initializer_list\<t >](../standard-library/initializer-list-class.md).)

Použití seznamu inicializátoru členů je upřednostňováno při přiřazování hodnot v těle konstruktoru, protože přímo inicializuje člen. V následujícím příkladu ukazuje seznam inicializátorů členů se skládá ze všech výrazů **identifikátoru (Argument)** za dvojtečkou:

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

Identifikátor musí odkazovat na člena třídy; je inicializován s hodnotou argumentu. Argument může být jeden z parametrů konstruktoru, volání funkce nebo [std:: initializer_list\<t >](../standard-library/initializer-list-class.md).

v seznamu inicializátoru členů musí být inicializovány **konstantní** členy a členy typu odkazu.

Volání parametrizovaných konstruktorů základní třídy by měla být provedena v seznamu inicializátorů, aby bylo zajištěno, že základní třída bude plně inicializována před spuštěním odvozeného konstruktoru.

## <a name="default_constructors"></a>Výchozí konstruktory

*Výchozí konstruktory* nemají obvykle žádné parametry, ale mohou mít parametry s výchozími hodnotami.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Výchozí konstruktory jsou jednou ze [speciálních členských funkcí](special-member-functions.md). Pokud nejsou deklarovány žádné konstruktory ve třídě, kompilátor poskytuje implicitní **vložený** výchozí konstruktor.

```cpp
#include <iostream>
using namespace std;

class Box {
public:
    int Volume() {return m_width * m_height * m_length;}
private:
    int m_width { 0 };
    int m_height { 0 };
    int m_length { 0 };
};

int main() {
    Box box1; // Invoke compiler-generated constructor
    cout << "box1.Volume: " << box1.Volume() << endl; // Outputs 0
}
```

Pokud spoléháte na implicitní výchozí konstruktor, nezapomeňte inicializovat členy v definici třídy, jak je znázorněno v předchozím příkladu. Bez těchto inicializátorů by členové byli neinicializovaná a volání Volume () by vytvořilo hodnotu uvolnění paměti. Obecně je vhodné inicializovat členy tímto způsobem i v případě, že se nespoléhá na implicitní výchozí konstruktor.

Kompilátoru můžete zabránit v generování implicitního výchozího konstruktoru tak, že ho definujete jako [Odstraněný](#explicitly_defaulted_and_deleted_constructors):

```cpp
    // Default constructor
    Box() = delete;
```

Výchozí konstruktor generovaný kompilátorem bude definován jako odstraněný, pokud některé členy třídy nejsou default-constructible. Například všichni členové typu třídy a jejich členové typu třídy musí mít výchozí konstruktor a destruktory, které jsou přístupné. Všechny datové členy typu odkazu, stejně jako členové **const** musí mít výchozí inicializátor členu.

Při volání výchozího konstruktoru generovaného kompilátorem a pokusu o použití závorek je vydána výstraha:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Toto je příklad problému Most Vexing Parse. Protože příklad výrazu může být interpretován jako deklarace funkce nebo jako vyvolání výchozího konstruktoru a protože deklarace analyzátoru jazyka C++ mají přednost před ostatními možnostmi, výraz je považován za deklaraci funkce. Další informace najdete v tématu [co je Vexing Parse](https://en.wikipedia.org/wiki/Most_vexing_parse).

Nejsou-li deklarovány žádné nevýchozí konstruktory, kompilátor neposkytuje výchozí konstruktor:

```cpp
class Box {
public:
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height){}
private:
    int m_width;
    int m_length;
    int m_height;

};

int main(){

    Box box1(1, 2, 3);
    Box box2{ 2, 3, 4 };
    Box box3; // C2512: no appropriate default constructor available
}
```

Pokud třída nemá žádný výchozí konstruktor, pole objektů této třídy nemůže být vytvořeno pomocí syntaxe samostatných hranatých závorek. Například s ohledem na předchozí blok kódu nemůže být pole oken deklarováno takto:

```cpp
Box boxes[3]; // C2512: no appropriate default constructor available
```

Můžete však použít sadu inicializačních seznamů pro inicializaci pole objektů boxu:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Další informace naleznete v tématu [Inicializátory](initializers.md).

## <a name="copy_and_move_constructors"></a>Kopírovací konstruktory

*Kopírovací konstruktor* inicializuje objekt zkopírováním hodnot členů z objektu stejného typu. Pokud jsou členy vaší třídy všechny jednoduché typy, jako jsou skalární hodnoty, je kopírovací konstruktor generovaný kompilátorem dostačující a nemusíte definovat vlastní. Pokud vaše třída vyžaduje složitější inicializaci, je nutné implementovat vlastní kopírovací konstruktor. Například pokud je člen třídy ukazatel, je nutné definovat kopírovací konstruktor pro přidělení nové paměti a zkopírování hodnot z objektu s ukazatelem na objekt. Kopírovací konstruktor generovaný kompilátorem jednoduše zkopíruje ukazatel, aby nový ukazatel stále odkazoval na umístění v paměti.

Kopírovací konstruktor může mít jednu z těchto signatur:

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Při definování kopírovacího konstruktoru byste také měli definovat operátor přiřazení kopie (=). Další informace najdete v tématu konstruktory [přiřazení](assignment.md) a [kopírování a operátory přiřazení pro kopírování](copy-constructors-and-copy-assignment-operators-cpp.md).

Můžete zabránit kopírování objektu definováním kopírovacího konstruktoru jako odstraněného:

```cpp
    Box (const Box& other) = delete;
```

Pokus o zkopírování objektu vyvolá chybu *C2280: pokus o odkaz na odstraněnou funkci*.

## <a name="move_constructors"></a>Přesunout konstruktory

*Konstruktor přesunu* je speciální členská funkce, která přesouvá vlastnictví dat existujícího objektu na novou proměnnou bez kopírování původních dat. Jako svůj první parametr převezme odkaz rvalue a všechny další parametry musí mít výchozí hodnoty. Konstruktory přesunutí můžou významně zvýšit efektivitu vašeho programu při předávání velkých objektů.

```cpp
Box(Box&& other);
```

Kompilátor zvolí konstruktor přesunu v určitých situacích, kdy je objekt inicializován jiným objektem stejného typu, který má být zničen a již nepotřebuje své prostředky. Následující příklad ukazuje jeden případ, když je vybrán konstruktor Move v rámci řešení přetížení. V konstruktoru, který volá `get_Box()`, vrácená hodnota je *hodnotu XValue* (hodnota vypršení platnosti). Není přiřazená k žádné proměnné a proto se chystá přejít mimo rozsah. Pro poskytnutí motivace pro tento příklad dejte krabici velký vektor řetězců, které představují jeho obsah. Spíše než zkopírování vektoru a jeho řetězců, konstruktor Move "" ukrást "z hodnoty" box ", aby vektor nyní patřil do nového objektu. Volání `std::move` je vše potřebné, protože třídy `vector` a `string` implementují své vlastní konstruktory Move.

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

class Box {
public:
    Box() { std::cout << "default" << std::endl; }
    Box(int width, int height, int length)
       : m_width(width), m_height(height), m_length(length)
    {
        std::cout << "int,int,int" << std::endl;
    }
    Box(Box& other)
       : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        std::cout << "copy" << std::endl;
    }
    Box(Box&& other) : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        m_contents = std::move(other.m_contents);
        std::cout << "move" << std::endl;
    }
    int Volume() { return m_width * m_height * m_length; }
    void Add_Item(string item) { m_contents.push_back(item); }
    void Get_Contents()
    {
        for (const auto& item : m_contents)
        {
            cout << item << " ";
        }
    }
private:
    int m_width{ 0 };
    int m_height{ 0 };
    int m_length{ 0 };
    vector<string> m_contents;
};

Box get_Box()
{
    Box b(5, 10, 18); // "int,int,int"
    b.Add_Item("Toupee");
    b.Add_Item("Megaphone");
    b.Add_Item("Suit");

    return b;
}

int main()
{
    Box b; // "default"
    Box b1(b); // "copy"
    Box b2(get_Box()); // "move"
    cout << "b2 contents: ";
    b2.Get_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

Pokud třída nedefinuje konstruktor Move, kompilátor vygeneruje implicitní výjimku, pokud není k dispozici žádný uživatelem deklarovaný kopírovací konstruktor, kopírovat operátor přiřazení, operátor přiřazení přesunutí nebo destruktor. Pokud není definován explicitní nebo implicitní konstruktor Move, operace, které by jinak používaly konstruktor Move, místo toho používají konstruktor Copy. Pokud třída deklaruje konstruktor přesunu nebo operátor přiřazení přesunutí, implicitně deklarovaný konstruktor Copy je definován jako odstraněný.

Implicitně deklarovaný konstruktor Move je definován jako odstraněný, pokud některý z členů, kteří mají typy třídy chybí destruktor, nebo kompilátor nemůže určit, který konstruktor použít pro operaci přesunutí.

Další informace o tom, jak napsat konstruktor bez triviálního přesunu, naleznete v tématu [Move konstruktors and Move AssignmentC++Operators ()](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly_defaulted_and_deleted_constructors"></a>Explicitně nastavené a odstraněné konstruktory

Můžete explicitně *výchozí* konstruktory kopírování, výchozí konstruktory, přesunout konstruktory, operátory přiřazení kopie, operátory přiřazení přesunu a destruktory. Můžete explicitně *Odstranit* všechny zvláštní členské funkce.

```cpp
class Box
{
public:
    Box2() = delete;
    Box2(const Box2& other) = default;
    Box2& operator=(const Box2& other) = default;
    Box2(Box2&& other) = default;
    Box2& operator=(Box2&& other) = default;
    //...
};
```

Další informace najdete v tématu [explicitně nastavené a odstraněné funkce](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr_constructors"></a>konstruktory constexpr

Konstruktor se může deklarovat jako [constexpr](constexpr-cpp.md) , pokud

- je buď deklarován jako výchozí, nebo jinak splňuje všechny podmínky pro [funkce constexpr](constexpr-cpp.md#constexpr_functions) obecně;
- Třída nemá žádné virtuální základní třídy;
- Každý z parametrů je [typ literálu](trivial-standard-layout-and-pod-types.md#literal_types);
- tělo není blok try funkce;
- všechny nestatické datové členy a dílčí objekty základní třídy jsou inicializovány;
- Pokud je třída (a) sjednocení, které mají členy variant, nebo (b) má anonymní sjednocení, inicializuje se pouze jeden člen sjednocení;
- Každý nestatický datový člen typu třídy a všechny dílčí objekty základní třídy mají konstruktor constexpr.

## <a name="init_list_constructors"></a>Konstruktory seznamu inicializátorů

Pokud konstruktor přebírá jako svůj parametr [std:: initializer_list\<t\>](../standard-library/initializer-list-class.md) a všechny ostatní parametry mají výchozí argumenty, tento konstruktor bude vybrán v řešení přetížení při vytváření instance pomocí přímé inicializace. Můžete použít initializer_list k inicializaci libovolného člena, který ho může přijmout. Předpokládejme například, že třída box (uvedená dříve) má `m_contents``std::vector<string>` členů. Můžete zadat konstruktor podobný tomuto:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

A pak vytvořte objekty box takto:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a>Explicitní konstruktory

Pokud má třída konstruktor s jedním parametrem, nebo pokud všechny parametry s výjimkou jednoho mají výchozí hodnotu, typ parametru lze implicitně převést na typ třídy. Například pokud má třída `Box` konstruktor podobný tomuto:

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

Je možné inicializovat například toto pole:

```cpp
Box b = 42;
```

Nebo předejte int funkci, která má pole:

```cpp
class ShippingOrder
{
public:
    ShippingOrder(Box b, double postage) : m_box(b), m_postage(postage){}

private:
    Box m_box;
    double m_postage;
}
//elsewhere...
    ShippingOrder so(42, 10.8);
```

Tyto převody mohou být užitečné v některých případech, ale častěji můžou vést k drobným, ale vážným chybám v kódu. Jako obecné pravidlo byste měli použít **explicitní** klíčové slovo pro konstruktor (a uživatelsky definované operátory), aby se zabránilo tomuto druhu implicitního převodu typu:

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Pokud je konstruktor explicitní, tento řádek způsobí chybu kompilátoru: `ShippingOrder so(42, 10.8);`.  Další informace naleznete v tématu [uživatelsky definované převody typů](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order_of_construction"></a>Pořadí konstrukce

Konstruktor provádí svou práci v tomto pořadí:

1. Volá základní třídu a členské konstruktory v pořadí deklarace.

1. Pokud je třída odvozena z virtuálních základních tříd, inicializuje virtuální základní ukazatele na objekt.

1. Pokud třída má nebo dědí virtuální funkce, inicializuje ukazatele virtuální funkce objektu. Virtuální funkce ukazatelů ukazuje na tabulku virtuální funkce třídy umožňující správnou vazbu volání virtuální funkce na kód.

1. Je spuštěn libovolný kód v těle jeho funkce.

Následující příklad zobrazuje pořadí, ve kterém jsou volány základní třídy a konstruktory členů v konstruktoru pro odvozenou třídu. Nejprve se volá základní konstruktor, poté se inicializují členy základní třídy v pořadí, v jakém se zobrazují v deklaraci třídy, a poté je volán odvozený konstruktor.

```cpp
#include <iostream>

using namespace std;

class Contained1 {
public:
    Contained1() { cout << "Contained1 ctor\n"; }
};

class Contained2 {
public:
    Contained2() { cout << "Contained2 ctor\n"; }
};

class Contained3 {
public:
    Contained3() { cout << "Contained3 ctor\n"; }
};

class BaseContainer {
public:
    BaseContainer() { cout << "BaseContainer ctor\n"; }
private:
    Contained1 c1;
    Contained2 c2;
};

class DerivedContainer : public BaseContainer {
public:
    DerivedContainer() : BaseContainer() { cout << "DerivedContainer ctor\n"; }
private:
    Contained3 c3;
};

int main() {
    DerivedContainer dc;
}
```

Zde je výstup:

```Output
Contained1 ctor
Contained2 ctor
BaseContainer ctor
Contained3 ctor
DerivedContainer ctor
```

Konstruktor odvozené třídy vždy volá konstruktor základní třídy, aby se před provedením jakékoli další práce mohl spolehnout na zcela konstruované základní třídy. Konstruktory základní třídy jsou volány v pořadí odvození – například pokud `ClassA` je odvozena z `ClassB`, která je odvozena od `ClassC`, je nejprve volán konstruktor `ClassC`, poté konstruktor `ClassB`, poté konstruktor `ClassA`.

Pokud základní třída nemá výchozí konstruktor, musíte zadat parametry konstruktoru základní třídy v konstruktoru odvozené třídy:

```cpp
class Box {
public:
    Box(int width, int length, int height){
       m_width = width;
       m_length = length;
       m_height = height;
    }

private:
    int m_width;
    int m_length;
    int m_height;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, const string label&) : Box(width, length, height){
        m_label = label;
    }
private:
    string m_label;
};

int main(){

    const string aLabel = "aLabel";
    StorageBox sb(1, 2, 3, aLabel);
}
```

Pokud konstruktor vyvolá výjimku, pořadí zničení je obrácené pořadí konstrukce:

1. Kód v těle funkce konstruktoru je oddělen.

1. Základní třída a členské objekty jsou zničeny v obráceném pořadí deklarace.

1. Pokud je konstruktor bez delegování, jsou zničeny všechny úplně vytvořené objekty a členy. Vzhledem k tomu, že objekt samotný není úplně vytvořen, není spuštěn destruktor.

## <a name="extended_aggregate"></a>Odvozené konstruktory a rozšířená agregovaná inicializace

Pokud je konstruktor základní třídy neveřejný, ale přístupný pro odvozenou třídu, pak v části **/std: c++ 17** v systému Visual Studio 2017 a novějších nelze použít prázdné složené závorky pro inicializaci objektu odvozeného typu.

Následující příklad ukazuje vyhovující chování C++ 14:

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};

Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

V C++ 17 se `Derived` nyní považuje za agregovaný typ. To znamená, že inicializace `Base` přes privátní výchozí konstruktor probíhá přímo, jako součást rozšířeného agregačního pravidla inicializace. Dříve byl pomocí konstruktoru `Derived` volán privátní konstruktor `Base` a úspěšně se zdařil z důvodu deklarace typu Friend.

Následující příklad ukazuje chování C++ 17 v aplikaci Visual Studio 2017 a novější v **/std: režim c++ 17** :

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};

Derived d1; // OK. No aggregate init involved.

Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Konstruktory pro třídy, které mají vícenásobnou dědičnost

Pokud je třída odvozena z více základních tříd, konstruktory základní třídy jsou vyvolány v pořadí, ve kterém jsou uvedeny v deklaraci odvozené třídy:

```cpp
#include <iostream>
using namespace std;

class BaseClass1 {
public:
    BaseClass1() { cout << "BaseClass1 ctor\n"; }
};
class BaseClass2 {
public:
    BaseClass2() { cout << "BaseClass2 ctor\n"; }
};
class BaseClass3 {
public:
    BaseClass3() { cout << "BaseClass3 ctor\n"; }
};
class DerivedClass : public BaseClass1,
                     public BaseClass2,
                     public BaseClass3
                     {
public:
    DerivedClass() { cout << "DerivedClass ctor\n"; }
};

int main() {
    DerivedClass dc;
}
```

Můžete očekávat následující výstup:

```Output
BaseClass1 ctor
BaseClass2 ctor
BaseClass3 ctor
DerivedClass ctor
```

## <a name="delegating_constructors"></a>Delegování konstruktorů

*Konstruktor delegování* volá jiný konstruktor ve stejné třídě, aby bylo možné provést některé operace inicializace. To je užitečné v případě, že máte více konstruktorů, které musí provádět podobné práce. Můžete napsat hlavní logiku v jednom konstruktoru a vyvolat ji od ostatních. V následujícím triviálním příkladu box (int) deleguje svou práci do boxu (int, int, int):

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```

Objekt vytvořený pomocí konstruktorů je plně inicializován ihned po dokončení jakéhokoli konstruktoru. Další informace naleznete v tématu [delegování konstruktorů](../cpp/delegating-constructors.md).

## <a name="inheriting_constructors"></a>Dědění konstruktorů (C++ 11)

Odvozená třída může dědit konstruktory z přímé základní třídy pomocí deklarace **using** , jak je znázorněno v následujícím příkladu:

```cpp
#include <iostream>
using namespace std;

class Base
{
public:
    Base() { cout << "Base()" << endl; }
    Base(const Base& other) { cout << "Base(Base&)" << endl; }
    explicit Base(int i) : num(i) { cout << "Base(int)" << endl; }
    explicit Base(char c) : letter(c) { cout << "Base(char)" << endl; }

private:
    int num;
    char letter;
};

class Derived : Base
{
public:
    // Inherit all constructors from Base
    using Base::Base;

private:
    // Can't initialize newMember from Base constructors.
    int newMember{ 0 };
};

int main()
{
    cout << "Derived d1(5) calls: ";
    Derived d1(5);
    cout << "Derived d1('c') calls: ";
    Derived d2('c');
    cout << "Derived d3 = d2 calls: " ;
    Derived d3 = d2;
    cout << "Derived d4 calls: ";
    Derived d4;
}

/* Output:
Derived d1(5) calls: Base(int)
Derived d1('c') calls: Base(char)
Derived d3 = d2 calls: Base(Base&)
Derived d4 calls: Base()*/
```

::: moniker range=">=vs-2017"

**Visual Studio 2017 a novější**: příkaz **using** v **/std: režim c++ 17** přináší do rozsahu všechny konstruktory ze základní třídy s výjimkou těch, které mají stejný podpis na konstruktory v odvozené třídě. Obecně je nejvhodnější použít dědění konstruktorů, pokud odvozená třída deklaruje žádné nové datové členy nebo konstruktory. Viz také [vylepšení v aplikaci Visual Studio 2017 verze 15,7](https://docs.microsoft.com/cpp/overview/cpp-conformance-improvements?view=vs-2017#improvements_157).

::: moniker-end

Šablona třídy může dědit všechny konstruktory z argumentu typu, pokud tento typ Určuje základní třídu:

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

Odvozená třída nemůže dědit z více základních tříd, pokud mají tyto základní třídy konstruktory, které mají stejný podpis.

## <a name="constructors_in_composite_classes"></a>Konstruktory a složené třídy

Třídy, které obsahují členy typu třídy, jsou označovány jako *složené třídy*. Při vytvoření člena typu třídy pro složenou třídu je konstruktor volán před vlastním konstruktorem třídy. Pokud obsažená třída nemá výchozí konstruktor, musíte použít seznam inicializace v konstruktoru složené třídy. V předchozím příkladu `StorageBox`, pokud změníte typ `m_label` členské proměnné na novou třídu `Label`, je nutné volat konstruktor základní třídy a inicializovat `m_label` proměnnou v konstruktoru `StorageBox`:

```cpp
class Label {
public:
    Label(const string& name, const string& address) { m_name = name; m_address = address; }
    string m_name;
    string m_address;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, Label label)
        : Box(width, length, height), m_label(label){}
private:
    Label m_label;
};

int main(){
// passing a named Label
    Label label1{ "some_name", "some_address" };
    StorageBox sb1(1, 2, 3, label1);

    // passing a temporary label
    StorageBox sb2(3, 4, 5, Label{ "another name", "another address" });

    // passing a temporary label as an initializer list
    StorageBox sb3(1, 2, 3, {"myname", "myaddress"});
}
```

## <a name="in-this-section"></a>V tomto oddílu

- [Kopírovací konstruktory a operátory přiřazení pro kopírování](copy-constructors-and-copy-assignment-operators-cpp.md)
- [Konstruktory přesunutí a operátory přiřazení přesunutí](move-constructors-and-move-assignment-operators-cpp.md)
- [Delegování konstruktorů](delegating-constructors.md)

## <a name="see-also"></a>Viz také:

[Třídy a struktury](classes-and-structs-cpp.md)
