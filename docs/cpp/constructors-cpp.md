---
title: Konstruktory (C++) | Microsoft Docs
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d34dff9c04491c25b2babfd4e7f0574bf7c6c609
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="constructors-c"></a>Konstruktory (C++)

Chcete-li přizpůsobit, jak jsou inicializovány členy třídy, nebo k vyvolání funkce, když je vytvořen objekt vaší třídy, definovat *konstruktor*. Konstruktor má stejný název jako třída a žádnou návratovou hodnotu. Můžete definovat libovolný počet přetížené konstruktory podle potřeby přizpůsobit inicializace různými způsoby. Konstruktory obvykle mají veřejnou dostupnost tak, aby kód mimo hierarchie dědičnosti nebo definice třídy můžete vytvořit objekty třídy. Ale můžete také deklarovat konstruktor jako **chráněné** nebo **privátní**.

Konstruktory volitelně může trvat členem init seznamu. Toto je efektivnější k chybě při inicializaci členy třídy než přidělování hodnot v těle konstruktor. Následující příklad ukazuje třídu `Box` s třemi přetížené konstruktory. Poslední dva použijte seznamy init členů:

```cpp

class Box {
public:
    // Default constructor
    Box() {}

    // Initalize a Box with equal dimensions (i.e. a cube)
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

Při deklaraci instance třídy kompilátor rozhodne, které konstruktor, který má být vyvolán podle pravidel objektů rozlišení přetížení:

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

- Může být konstruktory deklarována jako **vložené**, [explicitní](#explicit_constructors), **friend** nebo [constexpr](#constexpr_constructors).
- Konstruktor může inicializovat objekt, který byl deklarován jako **const**, **volatile** nebo **const volatile**. Objekt stane **const** po dokončení konstruktoru.
- K definování konstruktor v souboru implementace, pojmenujte ho kvalifikovaný stejně jako u jiných – členská funkce: `Box::Box(){...}`.

## <a name="member_init_list"></a> Člen inicializační seznamy

Konstruktor může volitelně může mít inicializátoru seznam členů, která inicializuje členy třídy před provádění těla konstruktor. (Všimněte si, že seznam inicializátoru člen není totéž jako *inicializátoru seznamu* typu [std::initializer_list\<T >](../standard-library/initializer-list-class.md).)

Pomocí seznamu intializer člen je upřednostňovaný nad přiřazení hodnoty v těle konstruktoru, protože přímo inicializuje člen. Následující příklad ukazuje inicializátoru člen seznam se skládá ze všech **identifier(argument)** výrazy po dvojtečkou:

```cpp
  
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

Identifikátor musí odkazovat na člena třídy; inicializací s hodnotou argumentu. Argument může být jeden z parametrů konstruktor, volání funkce nebo [std::initializer_list\<T >](../standard-library/initializer-list-class.md). 

**Const** členy a členy odkaz na typ se musí inicializovat v inicializátoru seznamu členů.

Volání základní třída parametrizované konstruktory by měl provedené v seznamu inicializátoru Ujistěte se, že před jejich spuštěním konstruktoru odvozené plně inicializaci základní třídy.

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

Výchozí konstruktory jsou jedním z [speciální členské funkce](special-member-functions.md). Pokud žádné konstruktory jsou deklarované v třídě, kompilátor poskytuje implicitní **vložené** výchozí konstruktor.

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

Pokud byste tedy spoléhat na implicitní výchozí konstruktor, je nutné inicializovat členy v definici třídy, jak je znázorněno v předchozím příkladu. Bez těchto inicializátory členy by Neinicializovaný a volání Volume() byste mohli vytvořit hodnotu uvolňování paměti. Obecně je vhodné k chybě při inicializaci členy tímto způsobem, i když není spoléhat na implicitní výchozí konstruktor.

Můžete zabránit v kompilátoru generování implicitní výchozí konstruktor definováním jej jako [odstranit](#explicitly_defaulted_and_deleted_constructors):

```cpp

    // Default constructor
    Box() = delete;

```

Odstranit, pokud nejsou všechny členy třídy výchozí zkonstruovatelný budou definovány generované kompilátorem výchozí konstruktor. Například všechny členy typu třídy a jejich členové typu třídy, musí mít výchozí konstruktor a destruktory, které jsou dostupné. Všichni členové data tohoto odkazu na typ, stejně jako **const** inicializátoru výchozí člen musí mít členové.

Při volání generované kompilátorem výchozí konstruktor a pokuste se použít závorky, objeví se upozornění:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Toto je příklad problému Most Vexing Parse. Protože příklad výrazu může být interpretován jako deklarace funkce nebo jako vyvolání výchozího konstruktoru a protože deklarace analyzátoru jazyka C++ mají přednost před ostatními možnostmi, výraz je považován za deklaraci funkce. Další informace najdete v tématu [nejvíce Vexing analyzovat](http://en.wikipedia.org/wiki/Most_vexing_parse).

Nejsou-li deklarovány žádné nevýchozí konstruktory, kompilátor neposkytuje výchozí konstruktor:

```cpp
class Box {
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height){}
};
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

Můžete však použít sadu inicializační seznamy k chybě při inicializaci pole objektů pole:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Další informace najdete v tématu [inicializátory](initializers.md).

## <a name="copy_and_move_constructors"></a> Kopírovací konstruktory

A *kopírovacího konstruktoru* inicializuje objekt zkopírováním hodnoty členů z objektu stejného typu. Pokud vaše členy třídy jsou všechny jednoduché typy, jako je například skalárních hodnot, stačí konstruktor copy generované kompilátorem a není nutné definovat vlastní. Pokud vaše třída vyžaduje složitější inicializace, budete muset implementovat vlastní kopírovacího konstruktoru. Například pokud člena třídy. je zde ukazatel pak budete muset definovat kopírovacího konstruktoru přidělit novou paměť a zkopírujte hodnoty z druhého odkazoval na objektu. Kopírování generované kompilátorem konstruktoru jednoduše zkopíruje ukazatele, tak, aby nové ukazatel stále ukazuje do jiného umístění v paměti.

Kopírovací konstruktor může mít jednu z těchto podpisů:

```cpp

    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Když definujete kopírovacího konstruktoru, měli byste také operátor přiřazení (=) kopírování. Další informace najdete v tématu [přiřazení](assignment.md) a [zkopírujte konstruktory a operátory přiřazení pro kopírování](copy-constructors-and-copy-assignment-operators-cpp.md).

Objekt můžete zabránit kopírování definováním konstruktor copy odstranil:

```cpp
    Box (const Box& other) = delete;
```

Pokus o zkopírování objektu způsobil chybu *C2280: Probíhá pokus o odkazu na funkci odstraněné*.

## <a name="move_constructors"></a> Přesunout konstruktory
A *přesunout konstruktor* je speciální členské funkce, která přemísťuje vlastnictví existující objekt data do nové proměnné bez kopírování původní data. Jak dlouho trvá odkaz rvalue jako svůj první parametr a žádné další parametry musí mít výchozí hodnoty. Přesunutí konstruktory může značně zvýšit efektivitu vašeho programu při předávání kolem velké objekty. Konstruktor move trvá deklarátor odkazu jako svůj první parametr. Další parametry musí mít výchozí hodnoty.

```cpp
Box(Box&& other);
```

Kompilátor zvolí konstruktor move v určitých situacích, kde probíhá inicializace objektu jiný objekt stejného typu, který má být zničený a již nepotřebuje jeho prostředky. Následující příklad ukazuje jeden případ, když je vybraná konstruktor move rozlišení přetížení. Proměnná *pole* vrácený get_Box() je *xvalue* (kterým vyprší platnost hodnota) který se chystáte se dostala mimo rozsah. Zajistit motivace pro tento příklad umožňuje poskytuje pole velké vektoru řetězců, které reprezentují jeho obsah. Místo kopírování vektoru a jeho řetězce, konstruktor move "krade" jej od konce platnosti hodnoty "pole" tak, aby vektoru teď patří do nového objektu. Volání `std::move` je všechno, co je potřeba, protože obě `vector` a `string` třídy implementovat vlastní přesun konstruktory.

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

Pokud třída nedefinuje konstruktor move, kompilátor vygeneruje implicitní jeden případě není deklarován uživatele kopírovacího konstruktoru, operátor přiřazení kopírování, operátor přiřazení přesunutí nebo – destruktor. Pokud je definován žádný konstruktor move explicitní nebo implicitní, operace, které by jinak použít konstruktor move použijte konstruktor copy. Pokud třída deklaruje konstruktor move nebo operátor přiřazení přesunutí, implicitně deklarované kopírovacího konstruktoru je definována jako odstraněný.

Přesunutí implicitně deklarované konstruktor je definován jako odstranit, pokud žádné členy, které jsou typy třídy nemají destruktor nebo kompilátor nemůže určit, které konstruktor, který chcete použít pro operaci přesunutí.

Další informace o tom, jak psát konstruktor move netriviální najdete v tématu [přesunout konstruktory a operátory přesunout přiřazení (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly_defaulted_and_deleted_constructors"></a> Explicitně přednastavené a odstraněné konstruktory

Můžete explicitně *výchozí* zkopírujte konstruktory, výchozí konstruktory, přesunout konstruktory, zkopírujte operátory přiřazení, přesuňte operátory přiřazení a destruktory. Můžete explicitně *odstranit* všechny speciální členské funkce.

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

Další informace najdete v tématu [explicitně uvedena a funkce, odstranit](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr_constructors"></a> constexpr konstruktory

Konstruktor může být deklarována jako [constexpr](constexpr-cpp.md) Pokud

- je buď deklarovaných jako uvedena, jinak splňuje všechny podmínky pro [constexpr funkce](constexpr-cpp.md#constexpr_functions) obecně;
- Třída nemá žádné virtuální základní třídy;
- Každý z parametrů je [typu literálu](trivial-standard-layout-and-pod-types.md#literal_types);
- text není funkce-bloku try;
- všechny datové nestatické členy a základní třída dílčí objekty jsou inicializovány;
- Pokud třída (a) s variant členů sjednocení nebo (b) má anonymní sjednocení, pouze jednoho z členů sjednocení inicializovat;
- Každý člen nestatické datového typu třídy a všechny základní třídy dílčí objekty mají constexpr konstruktor


## <a name="init_list_constructors"></a> Inicializátoru seznamu konstruktory

Pokud konstruktor přijímá [std::initializer_list\<T\> ](../standard-library/initializer-list-class.md) jako její parametr a všechny ostatní parametry mají výchozí argumenty, tento konstruktor vybrané rozlišení přetížení, pokud je třída Vytvořit instance prostřednictvím přímé inicializace. Můžete initializer_list k chybě při inicializaci kteréhokoli člena, který může přijmout. Předpokládejme například, má pole třídy (viz dříve) `std::vector<string>` člen **m_contents**. Můžete zadat konstruktor takto:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

A pak vytvořit objekty pole takto:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a> Explicitní konstruktory

Pokud třída má konstruktor pomocí jediného parametru, nebo pokud mají všechny parametry s výjimkou jednu výchozí hodnotu, typ parametru můžete implicitně převést na typ třídy. Například pokud `Box` třída má konstruktor takto:

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

Je možné k chybě při inicializaci pole takto:

```cpp
Box b = 42;
```

Nebo typ int předat funkce, která přebírá pole:

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

Takové převody může být užitečná v některých případech, ale často může vést k jemně ale závažných chyb v kódu. Obecně platí, měli byste použít **explicitní** – klíčové slovo v konstruktoru (a uživatelem definované operátory), aby se zabránilo tento druh typu implicitní převod:

```cpp

explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Po explicitní konstruktor tohoto řádku způsobí, že chyba kompilátoru: `ShippingOrder so(42, 10.8);`.  Další informace najdete v tématu [uživatelem definované převody typů](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order_of_construction"></a> Pořadí vytváření

Konstruktor provádí svou práci v tomto pořadí:

1. Volá základní třídu a členské konstruktory v pořadí deklarace.

2. Pokud je třída odvozena z virtuálních základních tříd, inicializuje virtuální základní ukazatele na objekt.

3. Pokud třída má nebo dědí virtuální funkce, inicializuje ukazatele virtuální funkce objektu. Virtuální funkce ukazatelů ukazuje na tabulku virtuální funkce třídy umožňující správnou vazbu volání virtuální funkce na kód.

4. Je spuštěn libovolný kód v těle jeho funkce.

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

```output
Contained1 ctor
Contained2 ctor
BaseContainer ctor
Contained3 ctor
DerivedContainer ctor
```

Konstruktor odvozené třídy vždy volá konstruktor základní třídy, aby se před provedením jakékoli další práce mohl spolehnout na zcela konstruované základní třídy. Konstruktory základní třídy jsou volány v pořadí podle odvození – například pokud ClassA je odvozeno od ClassB, které je odvozeno od ClassC, je nejprve volán konstruktor ClassC, poté konstruktor ClassB a nakonec konstruktor ClassA.

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

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Konstruktory pro třídy, které mají vícenásobná dědičnost

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

```output

BaseClass1 ctor
BaseClass2 ctor
BaseClass3 ctor
DerivedClass ctor

```

## <a name="virtual_functions_in_constructors"></a> Virtuální funkce v konstruktorech

Doporučujeme vám, abyste byli při volání virtuálních funkcí v konstruktorech opatrní. Vzhledem k tomu, že konstruktor základní třídy je vždy vyvolán před konstruktorem odvozené třídy, funkce, která je volána v konstruktoru základny, je verze základní třídy, nikoli verze odvozené třídy. V následujícím příkladu vytváření `DerivedClass` způsobí, že `BaseClass` implementace `print_it()` ke spuštění před `DerivedClass` konstruktor příčiny `DerivedClass` implementace `print_it()` provést:

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

```output
BaseClass print_it
Derived Class print_it
```

## <a name="delegating_constructors"></a> Delegování konstruktorů

A *delegování konstruktor* volá jiný konstruktor ve stejné třídě udělat některé úkoly inicializace. To je užitečné, když máte více konstruktory, které mají pro podobné práci. Můžete napsat Hlavní logika v jedné konstruktoru a vyvolání od ostatních. V následujícím příkladu trivial deleguje Box(int) svou práci pro Box(int,int,int):

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initalize a Box with equal dimensions (i.e. a cube)
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

## <a name="inheriting_constructors"></a> Dědění konstruktory (C ++ 11)

Odvozená třída může dědit vlastnosti konstruktorů z přímé základní třídu pomocí pomocí deklarace, jak je znázorněno v následujícím příkladu:

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

Pomocí příkazu přenese do oboru všechny konstruktory ze základní třídy kromě těch, které mají stejné definice virů, aby konstruktorů v odvozené třídě. Obecně platí je nejvhodnější použít dědičných konstruktory při odvozené třídy deklaruje žádné nové členy dat nebo konstruktory.

Šablona třídy lze dědit všechny konstruktory z argument typu, pokud tento typ určuje základní třídu:

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};

```

Odvozená třída nelze z vícenásobné třídy base dědit, pokud tyto základní třídy mít konstruktory, které mají stejné podpis.

## <a name="constructors_in_composite_classes"></a> Konstruktory a složené třídy

Třídy, které obsahují členy typu třídy se označují jako *složené třídy*. Při vytvoření člena typu třídy pro složenou třídu je konstruktor volán před vlastním konstruktorem třídy. Pokud obsažená třída nemá výchozí konstruktor, musíte použít seznam inicializace v konstruktoru složené třídy. V dříve `StorageBox` příklad, pokud změníte typ `m_label` členské proměnné na nový `Label` třídu, musí volat konstruktor základní třídy a inicializace `m_label` proměnné v `StorageBox` konstruktor:

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