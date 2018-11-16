---
title: Konstruktory (C++)
ms.date: 04/06/2018
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: e2027d967aebe68618e44e454ec268770b53ee4b
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694059"
---
# <a name="constructors-c"></a>Konstruktory (C++)

Přizpůsobit, jak se inicializují členy třídy nebo volání funkce, když je vytvořen objekt třídy, definovat *konstruktor*. Konstruktor má stejný název jako třída a žádnou návratovou hodnotu. Můžete definovat tolik přetížených konstruktorů, podle potřeby přizpůsobit inicializace různými způsoby. Konstruktory obvykle mít přístupnost public, aby kód mimo hierarchii definice nebo dědičnosti tříd můžete vytvořit objekty třídy. Ale můžete také deklarovat konstruktor jako **chráněné** nebo **privátní**.

Konstruktory volitelně může trvat člena seznamu init. Toto je efektivnější způsob, jak inicializovat členy třídy než přiřazení hodnoty v těle konstruktoru. Následující příklad ukazuje třídu `Box` s třemi přetížené konstruktory. Poslední dva použijte seznamy členů init:

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

Při deklaraci instance třídy kompilátor volí, která konstruktoru na základě pravidel rozlišení přetížení:

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

- Konstruktory mohou být deklarovány jako **vložené**, [explicitní](#explicit_constructors), **friend** nebo [constexpr](#constexpr_constructors).
- Konstruktor lze inicializovat objekt, který je deklarovaný jako **const**, **volatile** nebo **const volatile**. Objekt stane **const** po dokončení konstruktoru.
- Chcete-li definovat konstruktor v implementační soubor, pojmenujte ho kvalifikovaný stejně jako u jakékoli jiné členské funkce: `Box::Box(){...}`.

## <a name="member_init_list"></a> Seznamy inicializátorů členů

Konstruktor můžou mít seznam inicializátorů členů, která inicializuje členy třídy před provedením těla konstruktoru. (Všimněte si, že seznam inicializátorů členů není totéž jako *seznam inicializátorů* typu [std::initializer_list\<T >](../standard-library/initializer-list-class.md).)

Pomocí seznamu inicializátorů členů je upřednostňované nad přiřazením hodnoty v těle konstruktoru, protože přímo inicializuje člen. Následující příklad ukazuje inicializátor členu obsahuje seznam všech **identifier(argument)** výrazech za dvojtečku:

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

Identifikátor musí odkazovat na člen třídy; je inicializován s hodnotou argumentu. Argument může být jeden z parametrů konstruktoru, volání funkce nebo [std::initializer_list\<T >](../standard-library/initializer-list-class.md).

**Const** členy a členy typu odkazu musí být inicializován v seznamu inicializátorů členů.

Volání konstruktorů parametrizované základní třídy je třeba v seznamu inicializátorů Ujistěte se, že základní třídy je plně inicializován před spuštěním konstruktoru odvozené.

## <a name="default_constructors"></a> Výchozí konstruktory

*Výchozí konstruktory* obvykle mít žádné parametry, ale mohou mít parametry s výchozími hodnotami.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Výchozí konstruktory jsou jedním z [speciálních členských funkcí](special-member-functions.md). Pokud žádné konstruktory jsou deklarovány ve třídě, kompilátor poskytuje implicitní **vložené** výchozí konstruktor.

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

Pokud se spoléháte na implicitní výchozí konstruktor, je potřeba inicializovat členů v definici třídy, jak je znázorněno v předchozím příkladu. Bez těchto inicializátorů členů by být inicializována a volání Volume() byste mohli vytvořit hodnotu uvolňování paměti. Obecně je vhodné k inicializaci členy tímto způsobem, i když není spoléhat na implicitní výchozí konstruktor.

Kompilátor může zabránit generování implicitní výchozí konstruktor tak, že definujete ho jako [odstranit](#explicitly_defaulted_and_deleted_constructors):

```cpp
    // Default constructor
    Box() = delete;
```

Odstranit, pokud nejsou žádné členy třídy constructible výchozí konstruktor vygenerovaný kompilátorem default budou definovány. Například všechny členy typu třídy a jejich členy typu třídy, musí mít výchozí konstruktor a destruktory, které jsou k dispozici. Zadejte všechny datové členy odkazu, stejně jako **const** členy musí mít výchozí inicializátor členu.

Při volání vygenerovaný kompilátorem výchozí konstruktor a zkusíte použít závorky, objeví se upozornění:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Toto je příklad problému Most Vexing Parse. Protože příklad výrazu může být interpretován jako deklarace funkce nebo jako vyvolání výchozího konstruktoru a protože deklarace analyzátoru jazyka C++ mají přednost před ostatními možnostmi, výraz je považován za deklaraci funkce. Další informace najdete v tématu [Most Vexing Parse](http://en.wikipedia.org/wiki/Most_vexing_parse).

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

Ale můžete použít sadu inicializačních seznamů pro inicializaci pole objektů pole:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Další informace najdete v tématu [inicializátory](initializers.md).

## <a name="copy_and_move_constructors"></a> Kopírovací konstruktory

A *kopírovací konstuktor* inicializace objektu tak, že zkopírujete hodnoty členů z objektu stejného typu. Pokud vaše členy třídy jsou všechny jednoduché typy, jako jsou skalární hodnoty, stačí konstruktor vygenerovaný kompilátorem a nepotřebujete k definování vlastní. Pokud vaše třída vyžaduje složitější inicializace, budete muset implementovat vlastní kopírovací konstruktor. Například pokud je ukazatel člen třídy musíte definovat konstruktor kopie přidělit novou paměť a zkopírujte hodnoty z druhé strany odkazuje na objekt. Konstruktor vygenerovaný kompilátorem jednoduše zkopíruje ukazatele, takže stále nový ukazatel odkazuje na druhé strany umístění v paměti.

Kopírovací konstruktor může mít jednu z těchto podpisy:

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Při definování konstruktoru kopie, měli byste také definovat kopírovacího operátoru přiřazení (=). Další informace najdete v tématu [přiřazení](assignment.md) a [kopírovací konstruktory a operátory přiřazení pro kopírování](copy-constructors-and-copy-assignment-operators-cpp.md).

Objekt můžete zabránit v kopírování definováním kopírovací konstruktor se odstranil:

```cpp
    Box (const Box& other) = delete;
```

Chyba pokusu o zkopírování objekt vytváří *C2280: Pokus o odkazování na odstraněnou funkci*.

## <a name="move_constructors"></a> Konstruktory přesunutí

A *konstruktor přesunu* je zvláštní členská funkce, který přesouvá vlastnictví existujícího objektu data do nové proměnné bez kopírování původní data. Bere odkaz rvalue jako svůj první parametr a žádné další parametry musí mít výchozí hodnoty. Přesun konstruktorů může významně zvýšit efektivitu vašeho programu při předávání za velké objekty. Konstruktor přesunu bere odkaz rvalue jako svůj první parametr. Všechny ostatní parametry musí mít výchozí hodnoty.

```cpp
Box(Box&& other);
```

Kompilátor volí konstruktor přesunutí v určitých situacích, kde objekt je inicializován jiným objektem stejného typu, který má být zničeny a již nepotřebuje prostředky. Následující příklad ukazuje jeden případ. při výběru konstruktoru přesunu podle řešení přetížení. Proměnná *pole* vrácený get_Box() je *xvalue* (u nichž vyprší platnost hodnoty) který se chystáte se přejít mimo rozsah. K poskytování motivace pro účely tohoto příkladu, Pojďme pole velké vektor řetězců, které představují její obsah. Místo kopírování vektoru a jeho řetězce, konstruktor přesunutí "ukradne" ho z u nichž vyprší platnost hodnoty "pole" tak, aby vektoru nyní patří do nového objektu. Volání `std::move` je vše, co potřebujete, protože obě `vector` a `string` třídy implementovat vlastní konstruktorů.

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

Pokud třída nedefinuje konstruktor přesunutí, kompilátor vygeneruje implicitní jeden, pokud není žádný uživatelem deklarované kopírovacího konstruktoru, operátor přiřazení kopie, operátor přiřazení přesunu nebo destruktor. Pokud není definován žádný konstruktor přesunu explicitní nebo implicitní, pomocí operace, které by jinak použijte konstruktor přesunutí konstruktoru kopie. Pokud třída deklaruje přenosový konstruktor nebo operátor přiřazení přesunutí, implicitně deklarovanou kopírovací konstuktor je definovaný jako odstraněný.

Konstruktor implicitně deklarovanou přesunu je definovaný jako odstraněný Pokud nemají žádné členy, které jsou typy tříd destruktor nebo kompilátor nemůže určit konstruktoru, který chcete použít pro operaci přesunutí.

Další informace o tom, jak zapsat konstruktor přesunutí netriviální, naleznete v tématu [konstruktory přesunutí a operátory přiřazení přesunutí (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly_defaulted_and_deleted_constructors"></a> Explicitně přednastavené a výchozí konstruktory

Můžete explicitně *výchozí* kopírovací konstruktory, výchozí konstruktory, konstruktory přesunutí, operátory přiřazení pro kopírování, přesunutí, operátory přiřazení a destruktorech. Můžete explicitně *odstranit* všech zvláštních členských funkcí.

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

Další informace najdete v tématu [explicitně nastavena jako výchozí a odstranit funkce](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr_constructors"></a> konstruktory constexpr.

Konstruktoru mohou být deklarovány jako [constexpr](constexpr-cpp.md) Pokud

- je buď deklarované jako nastavit na výchozí hodnotu, jinak splňuje všechny podmínky pro [funkce constexpr](constexpr-cpp.md#constexpr_functions) obecně;
- Třída nemá žádné virtuální základní třídy;
- Každý z parametrů [typ literálu](trivial-standard-layout-and-pod-types.md#literal_types);
- text není funkce zkušební blok;
- všechny nestatické datové členy a podřízených objektů základní třídy jsou inicializovány;
- Pokud třída je (a) s variant členů sjednocení nebo (b) má anonymní sjednocení, pouze jeden z členů sjednocení inicializovaný.
- Každý nestatický datový člen typu třídy a všech podřízených objektů základní třídy mají konstruktor constexpr

## <a name="init_list_constructors"></a> Inicializátor seznamu konstruktory

Pokud má konstruktor [std::initializer_list\<T\> ](../standard-library/initializer-list-class.md) jako svůj parametr a všechny ostatní parametry mají výchozí argumenty, tento konstruktor vybrané v řešení přetížení, když je třída vytvořit instanci prostřednictvím přímé inicializaci. Objekt initializer_list můžete použít k inicializaci žádný člen, který může přijmout. Předpokládejme například, má pole třídy (viz dříve) `std::vector<string>` člen `m_contents`. Můžete zadat konstruktor takto:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

A pak vytvořte objekty pole následujícím způsobem:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a> Explicitní konstruktory

Pokud třída nemá konstruktor s jedním parametrem, nebo pokud všechny parametry s výjimkou jednoho mají výchozí hodnotu, typ parametru lze implicitně převést na typ třídy. Například pokud `Box` třída nemá konstruktor takto:

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

Je možné inicializovat pole následujícím způsobem:

```cpp
Box b = 42;
```

Nebo int předat funkci, která přijímá pole:

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

Tyto převody může být užitečné v některých případech ale častěji může vést k drobným ale závažné chyby v kódu. Obecně platí, měli byste použít **explicitní** – klíčové slovo v konstruktor (a operátory definované uživatelem), aby se zabránilo tento druh implicitní převod typu:

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Pokud je explicitní konstruktor, tento řádek způsobí chybu kompilátoru: `ShippingOrder so(42, 10.8);`.  Další informace najdete v tématu [uživatelem definovaných převodů typu](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order_of_construction"></a> Pořadí konstrukce

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

Konstruktor odvozené třídy vždy volá konstruktor základní třídy, aby se před provedením jakékoli další práce mohl spolehnout na zcela konstruované základní třídy. Konstruktory základní třídy jsou volány v pořadí podle odvození – například pokud `ClassA` je odvozen z `ClassB`, který je odvozen z `ClassC`, `ClassC` konstruktor je jako první, pak bude `ClassB` konstruktoru, pak bude `ClassA` konstruktoru.

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

## <a name="virtual_functions_in_constructors"></a> Virtuální funkce v konstruktorech

Doporučujeme vám, abyste byli při volání virtuálních funkcí v konstruktorech opatrní. Vzhledem k tomu, že konstruktor základní třídy je vždy vyvolán před konstruktorem odvozené třídy, funkce, která je volána v konstruktoru základny, je verze základní třídy, nikoli verze odvozené třídy. V následujícím příkladu sestavením `DerivedClass` způsobí, že `BaseClass` provádění `print_it()` ke spuštění před `DerivedClass` konstruktoru způsobí, že `DerivedClass` provádění `print_it()` ke spuštění:

```cpp
#include <iostream>
using namespace std;

class BaseClass{
public:
    BaseClass(){
        print_it();
    }
    virtual void print_it() {
        cout << "BaseClass print_it" << endl;
    }
};

class DerivedClass : public BaseClass {
public:
    DerivedClass() {
        print_it();
    }
    virtual void print_it(){
        cout << "Derived Class print_it" << endl;
    }
};

int main() {

    DerivedClass dc;
}
```

Zde je výstup:

```Output
BaseClass print_it
Derived Class print_it
```

## <a name="delegating_constructors"></a> Delegování konstruktorů

A *delegování konstruktorů* volá jiný konstruktor ve stejné třídě, aby provedl některé úkoly inicializace. To je užitečné v případě, že máte více konstruktorů, které mají podobné úkoly provádět. Můžete napsat Hlavní logika v jeden konstruktor a vyvolání od ostatních. V následujícím příkladu triviálních deleguje Box(int) svou práci do Box(int,int,int):

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

Objekt vytvořený pomocí konstruktorů je plně inicializován ihned po dokončení jakéhokoli konstruktoru. Další informace najdete v tématu [jednotná inicializace a delegování konstruktorů](../cpp/uniform-initialization-and-delegating-constructors.md).

## <a name="inheriting_constructors"></a> Dědění konstruktorů (C ++ 11)

Odvozená třída může dědit konstruktory z přímé základní třídy pomocí **pomocí** prohlášení, jak je znázorněno v následujícím příkladu:

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

**Visual Studio 2017 verze 15.7 nebo novější**: **pomocí** výroky **/std: c ++ 17** režimu přináší do oboru všechny konstruktory ze základní třídy s výjimkou těch, které mají stejnou signaturu jako konstruktorů v odvozené třídě. Obecně je nejvhodnější použít dědičné konstruktorů nebo konstruktorů při odvozená třída nedeklaruje žádné nové datové členy. Viz také [vylepšení v sadě Visual Studio 2017 verze 15.7](../cpp-conformance-improvements-2017.md#improvements_157).

Šablony třídy lze dědit všechny konstruktory z argumentu typu, pokud tento typ určuje základní třídu:

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

Odvozená třída nemůže dědit z více základních tříd, pokud tyto základní třídy mají konstruktory se stejnou signaturou.

## <a name="constructors_in_composite_classes"></a> Konstruktory a složené třídy

Třídy, které obsahují členy typu třídy jsou označovány jako *složené třídy*. Při vytvoření člena typu třídy pro složenou třídu je konstruktor volán před vlastním konstruktorem třídy. Pokud obsažená třída nemá výchozí konstruktor, musíte použít seznam inicializace v konstruktoru složené třídy. V předchozím `StorageBox` příklad, pokud změníte typ `m_label` členské proměnné do nového `Label` třídy, musíte volat konstruktor základní třídy a také inicializovat `m_label` proměnné v `StorageBox` konstruktor:

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
