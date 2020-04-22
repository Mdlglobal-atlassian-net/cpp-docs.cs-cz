---
title: Konstruktory (C++)
ms.date: 12/27/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: 4640bcf5f21bbe018a8744a6c5206bdd09509c98
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749641"
---
# <a name="constructors-c"></a>Konstruktory (C++)

Chcete-li přizpůsobit způsob inicializování členů třídy nebo vyvolat funkce při vytvoření objektu třídy, definujte *konstruktor*. Konstruktor má stejný název jako třída a žádná vrácená hodnota. Můžete definovat tolik přetížené konstruktory podle potřeby přizpůsobit inicializaci různými způsoby. Konstruktory mají obvykle veřejnou přístupnost, takže kód mimo hierarchii definice třídy nebo dědičnosti může vytvářet objekty třídy. Můžete však také deklarovat konstruktor jako **chráněný** nebo **soukromý**.

Konstruktory mohou volitelně vzít seznam init člena. Toto je efektivnější způsob, jak inicializovat členy třídy než přiřazování hodnot v těle konstruktoru. Následující příklad ukazuje `Box` třídu se třemi přetíženými konstruktory. Poslední dva seznamy init členů použití:

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

Když deklarujete instanci třídy, kompilátor zvolí, který konstruktor vyvolá na základě pravidel řešení přetížení:

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

- Konstruktory mohou být deklarovány jako **inline**, [explicitní](#explicit_constructors), **friend** nebo [constexpr](#constexpr_constructors).
- Konstruktor může inicializovat objekt, který byl deklarován jako **const**, **volatile** nebo **const volatile**. Objekt se stane **const** po dokončení konstruktoru.
- Chcete-li definovat konstruktor v souboru implementace, přiřazujte `Box::Box(){...}`mu kvalifikovaný název jako u jakékoli jiné členské funkce: .

## <a name="member-initializer-lists"></a><a name="member_init_list"></a>Seznamy inicializačních seznamů členů

Konstruktor může mít volitelně seznam inicializátoru členů, který inicializuje členy třídy před spuštěním těla konstruktoru. (Všimněte si, že seznam inicializátoru člena není totéž jako *inicializační seznam* typu [std::initializer_list\<T>](../standard-library/initializer-list-class.md).)

Použití seznamu inicializátoru členů je upřednostňováno před přiřazením hodnot v těle konstruktoru, protože přímo inicializuje člen. V následujícím příkladu ukazuje, že seznam inicializátoru členů se skládá ze všech výrazů **identifikátor(argument)** za dvojtečkou:

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

Identifikátor musí odkazovat na člena třídy; je inicializován s hodnotou argumentu. Argumentem může být jeden z parametrů konstruktoru, volání funkce nebo [\<std::initializer_list T>](../standard-library/initializer-list-class.md).

**const** členy a členy typu odkazu musí být inicializovány v seznamu inicializátoru členů.

Volání parametrizovaných konstruktorů základní třídy by měla být provedena v seznamu inicializátoru, aby bylo zajištěno, že základní třída je plně inicializována před spuštěním odvozeného konstruktoru.

## <a name="default-constructors"></a><a name="default_constructors"></a>Výchozí konstruktory

*Výchozí konstruktory* obvykle nemají žádné parametry, ale mohou mít parametry s výchozími hodnotami.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Výchozí konstruktory jsou jednou ze [zvláštních členských funkcí](special-member-functions.md). Pokud žádné konstruktory jsou deklarovány ve třídě, kompilátor poskytuje implicitní **vsazený** výchozí konstruktor.

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

Pokud spoléháte na implicitní výchozí konstruktor, nezapomeňte inicializovat členy v definici třídy, jak je znázorněno v předchozím příkladu. Bez těchto inicializačních zařízení by členy byly neinicializovány a volání Volume() by vytvořilo hodnotu odpadků. Obecně je vhodné inicializovat členy tímto způsobem i v případě, že se nespoléháte na implicitní výchozí konstruktor.

Kompilátoru můžete zabránit ve generování implicitního výchozího konstruktoru tím, že ho definujete jako [odstraněný](#explicitly_defaulted_and_deleted_constructors):

```cpp
    // Default constructor
    Box() = delete;
```

Výchozí konstruktor generovaný kompilátorem bude definován jako odstraněný, pokud nejsou všechny členy třídy konstrukční. Například všichni členové typu třídy a jejich členy typu třídy musí mít výchozí konstruktor a destruktory, které jsou přístupné. Všechny datové členy typu odkazu, stejně jako **const** členy musí mít výchozí člen inicializátor.

Při volání výchozíkonstruktor generovaný kompilátorem a pokusu o použití závorek se zobrazí upozornění:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Toto je příklad problému Most Vexing Parse. Protože příklad výrazu může být interpretován jako deklarace funkce nebo jako vyvolání výchozího konstruktoru a protože deklarace analyzátoru jazyka C++ mají přednost před ostatními možnostmi, výraz je považován za deklaraci funkce. Další informace naleznete [v tématu Most Vexing Parse](https://en.wikipedia.org/wiki/Most_vexing_parse).

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

Sadu seznamů inicializátoru však můžete použít k inicializaci pole objektů Box:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Další informace naleznete v tématu [Initializers](initializers.md).

## <a name="copy-constructors"></a><a name="copy_and_move_constructors"></a>Kopírovat konstruktory

*Konstruktor kopie* inicializuje objekt zkopírováním hodnot členů z objektu stejného typu. Pokud vaše členové třídy jsou všechny jednoduché typy, jako jsou skalární hodnoty, konstruktor kopie generované kompilátorem je dostačující a není nutné definovat vlastní. Pokud vaše třída vyžaduje složitější inicializace, pak je třeba implementovat vlastní konstruktor kopie. Například pokud člen třídy je ukazatel pak je třeba definovat konstruktor kopie přidělit novou paměť a zkopírovat hodnoty z druhé špičaté objektu. Konstruktor kopie generované kompilátorem jednoduše zkopíruje ukazatel, takže nový ukazatel stále odkazuje na umístění paměti druhého.

Konstruktor kopie může mít jeden z těchto podpisů:

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Když definujete konstruktor kopie, měli byste také definovat operátor přiřazení kopie (=). Další informace naleznete v tématu [Přiřazení](assignment.md) a [kopírování konstruktorů a kopírovacích operátorů přiřazení](copy-constructors-and-copy-assignment-operators-cpp.md).

Zkopírování objektu můžete zabránit definováním konstruktoru kopie jako odstraněný:

```cpp
    Box (const Box& other) = delete;
```

Při pokusu o zkopírování objektu dojde k chybě *C2280: pokus o odkaz na odstraněnou funkci*.

## <a name="move-constructors"></a><a name="move_constructors"></a>Přesunout konstruktory

*Move konstruktor* je speciální členská funkce, která přesune vlastnictví dat existujícího objektu do nové proměnné bez kopírování původních dat. Trvá rvalue odkaz jako jeho první parametr a všechny další parametry musí mít výchozí hodnoty. Přesunout konstruktory může výrazně zvýšit efektivitu programu při předávání kolem velkých objektů.

```cpp
Box(Box&& other);
```

Kompilátor zvolí konstruktor move v určitých situacích, kdy je objekt inicializován jiným objektem stejného typu, který má být zničen a již nepotřebuje své prostředky. Následující příklad ukazuje jeden případ, kdy je konstruktor move vybrán pomocí rozlišení přetížení. V konstruktoru, `get_Box()`který volá , vrácená hodnota je *xvalue* (eXpiring hodnota). Není přiřazena žádné proměnné, a proto se chystá přejít mimo rozsah. Chcete-li poskytnout motivaci pro tento příklad, dejme Box velký vektor řetězců, které představují jeho obsah. Spíše než kopírování vektoru a jeho řetězců, konstruktor move "ukradne" z končící hodnoty "box" tak, aby vektor nyní patří k novému objektu. Volání `std::move` je vše, co je `vector` potřeba, protože oba a `string` třídy implementovat své vlastní konstruktory přesunout.

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
    void Print_Contents()
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
    b2.Print_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

Pokud třída nedefinuje konstruktor move, kompilátor generuje implicitní, pokud neexistuje žádný konstruktor kopírování deklarovaný uživatelem, operátor přiřazení kopírování, operátor přiřazení přesunutí nebo destruktor. Pokud není definován žádný explicitní nebo implicitní konstruktor move, operace, které by jinak používaly konstruktor move, místo toho používají konstruktor copy. Pokud třída deklaruje konstruktor move nebo operátor přiřazení přesunutí, implicitně deklarovaný konstruktor kopie je definován jako odstraněný.

Implicitně deklarovaný konstruktor move je definován jako odstraněný, pokud všechny členy, které jsou typy tříd, postrádají destruktor nebo kompilátor nemůže určit, který konstruktor má být určen pro operaci přesunutí.

Další informace o tom, jak napsat netriviální konstruktor přesunutí, naleznete v tématu [Přesunutí konstruktorů a operátorů přiřazení přesunutí (C++).](../cpp/move-constructors-and-move-assignment-operators-cpp.md)

## <a name="explicitly-defaulted-and-deleted-constructors"></a><a name="explicitly_defaulted_and_deleted_constructors"></a>Explicitně výchozí a odstraněné konstruktory

Můžete explicitně *výchozí* kopie konstruktory, výchozí konstruktory, přesunout konstruktory, kopírovat operátory přiřazení, přesunout operátory přiřazení a destruktory. Můžete explicitně *odstranit* všechny speciální členské funkce.

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

Další informace naleznete [v tématu Explicitdefaulted and Deleted Functions](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr-constructors"></a><a name="constexpr_constructors"></a>konstruktory constexpr

Konstruktor může být deklarován jako [constexpr,](constexpr-cpp.md) pokud

- je buď deklarována jako výchozí, nebo splňuje všechny podmínky pro [funkce constexpr](constexpr-cpp.md#constexpr_functions) obecně;
- třída nemá žádné virtuální základní třídy;
- každý z parametrů je [doslovný typ](trivial-standard-layout-and-pod-types.md#literal_types);
- tělo není funkce try-blok;
- všechny nestatické datové členy a dílčí objekty základní třídy jsou inicializovány.
- pokud je třída (a) sjednocením s variantními členy nebo (b) má anonymní sjednocení, je inicializován pouze jeden z členů unie;
- každý nestatický datový člen typu třídy a všechny podobjekty základní třídy mají konstruktor constexpr

## <a name="initializer-list-constructors"></a><a name="init_list_constructors"></a>Konstruktory seznamu inicializátorů

Pokud konstruktor trvá [\<std::initializer_list\> T](../standard-library/initializer-list-class.md) jako jeho parametr a všechny ostatní parametry mají výchozí argumenty, tento konstruktor bude vybrán v rozlišení přetížení při vytvoření instance třídy prostřednictvím přímé inicializace. Initializer_list můžete použít k inicializaci libovolného člena, který jej může přijmout. Předpokládejme například, že třída Box `std::vector<string>` (zobrazená dříve) má člena `m_contents`. Můžete zadat konstruktor, jako je tento:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

A pak vytvořte box objekty, jako je tento:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit-constructors"></a><a name="explicit_constructors"></a>Explicitní konstruktory

Pokud třída má konstruktor s jedním parametrem, nebo pokud všechny parametry s výjimkou jednoho mají výchozí hodnotu, typ parametru lze implicitně převést na typ třídy. Například pokud `Box` třída má konstruktor, jako je tento:

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

Box je možné inicializovat takto:

```cpp
Box b = 42;
```

Nebo předat int na funkci, která trvá Box:

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

Takové převody mohou být užitečné v některých případech, ale častěji mohou vést k jemné, ale závažné chyby ve vašem kódu. Obecně platí, že byste měli použít **explicitní** klíčové slovo na konstruktoru (a uživatelem definované operátory) zabránit tento druh implicitní převod typu:

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Pokud je konstruktor explicitní, tento řádek způsobí `ShippingOrder so(42, 10.8);`chybu kompilátoru: .  Další informace naleznete [v tématu User-Defined Type Conversions](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order-of-construction"></a><a name="order_of_construction"></a>Pořadí výstavby

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

Konstruktor odvozené třídy vždy volá konstruktor základní třídy, aby se před provedením jakékoli další práce mohl spolehnout na zcela konstruované základní třídy. Konstruktory základní třídy jsou volány v pořadí odvození `ClassA` – například pokud je odvozen `ClassB`z , který je odvozen `ClassC`z , `ClassC` konstruktor se nazývá první, pak `ClassB` konstruktor, pak `ClassA` konstruktor.

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

## <a name="derived-constructors-and-extended-aggregate-initialization"></a><a name="extended_aggregate"></a>Odvozené konstruktory a rozšířená agregátní inicializace

Pokud je konstruktor základní třídy neveřejný, ale přístupný pro odvozenou třídu, pak v režimu **/std:c++17** v sadě Visual Studio 2017 a později nelze použít prázdné závorky k inicializaci objektu odvozeného typu.

Následující příklad ukazuje chování konformní ho shody jazyka C++14:

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

V jazyce C++17 `Derived` je nyní považován za agregační typ. To znamená, že `Base` inicializace prostřednictvím soukromého výchozího konstruktoru probíhá přímo jako součást rozšířeného pravidla agregace inicializace. Dříve `Base` byl soukromý konstruktor volán prostřednictvím konstruktoru `Derived` a byl úspěšný z důvodu deklarace friend.

Následující příklad ukazuje chování C++ 17 v sadě Visual Studio 2017 a novější v režimu **/std:c++17:**

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

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Konstruktory pro třídy, které mají více dědičnosti

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

## <a name="delegating-constructors"></a><a name="delegating_constructors"></a>Delegování konstruktorů

*Delegující konstruktor* volá jiný konstruktor ve stejné třídě k provádění některých prací inicializace. To je užitečné, pokud máte více konstruktory, které všechny mají provádět podobnou práci. Hlavní logiku můžete napsat v jednom konstruktoru a vyvolat ji od ostatních. V následujícím triviálním příkladu Box(int) deleguje svou práci na Box(int,int,int):

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

Objekt vytvořený pomocí konstruktorů je plně inicializován ihned po dokončení jakéhokoli konstruktoru. Další informace naleznete v [tématu Delegování konstruktorů](../cpp/delegating-constructors.md).

## <a name="inheriting-constructors-c11"></a><a name="inheriting_constructors"></a>Dědění konstruktorů (C++11)

Odvozená třída může dědit konstruktory z přímé základní třídy pomocí **příkazu using,** jak je znázorněno v následujícím příkladu:

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

**Visual Studio 2017 a novější**: **Using** prohlášení v **režimu /std:c++17** přináší do oboru všechny konstruktory ze základní třídy s výjimkou těch, které mají stejný podpis konstruktory v odvozené třídě. Obecně je nejlepší použít dědící konstruktory, když odvozené třídy deklaruje žádné nové datové členy nebo konstruktory. Viz také [vylepšení visual studia 2017 verze 15.7](https://docs.microsoft.com/cpp/overview/cpp-conformance-improvements?view=vs-2017#improvements_157).

::: moniker-end

Šablona třídy může dědit všechny konstruktory z argumentu typu, pokud tento typ určuje základní třídu:

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

Odvozená třída nemůže dědit z více základních tříd, pokud tyto základní třídy mají konstruktory, které mají stejný podpis.

## <a name="constructors-and-composite-classes"></a><a name="constructors_in_composite_classes"></a>Konstruktory a složené třídy

Třídy, které obsahují členy typu třídy, jsou označovány jako *složené třídy*. Při vytvoření člena typu třídy pro složenou třídu je konstruktor volán před vlastním konstruktorem třídy. Pokud obsažená třída nemá výchozí konstruktor, musíte použít seznam inicializace v konstruktoru složené třídy. V předchozím `StorageBox` příkladu pokud změníte `m_label` typ členské proměnné `Label` na novou třídu, musíte volat konstruktor `m_label` základní třídy a inicializovat proměnnou v konstruktoru: `StorageBox`

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

- [Kopírování konstruktorů a operátorů přiřazení kopírování](copy-constructors-and-copy-assignment-operators-cpp.md)
- [Přesunutí konstruktorů a přesunutí operátorů přiřazení](move-constructors-and-move-assignment-operators-cpp.md)
- [Delegování konstruktorů](delegating-constructors.md)

## <a name="see-also"></a>Viz také

[Třídy a struktury](classes-and-structs-cpp.md)
