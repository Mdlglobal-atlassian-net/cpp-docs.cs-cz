---
title: Konstruktory (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57854ec15d3104d80e8dbba68ebc33937222172f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="constructors-c"></a>Konstruktory (C++)
Konstruktor je druh členské funkce, která inicializuje novou instanci její třídy. Konstruktor má stejný název jako třída a žádnou návratovou hodnotu. Konstruktor může obsahovat libovolný počet parametrů a třída může mít libovolný počet přetížené konstruktory. Konstruktory může mít usnadnění, veřejné, chráněný nebo soukromé. Pokud nedefinujete žádné konstruktory, kompilátor vygeneruje výchozí konstruktor, které nepřijímá žádné parametry; Toto chování můžete přepsat pomocí deklarace výchozí konstruktor jako odstraněný.  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   [Pořadí vytváření](#order_of_construction)  
  
-   [Seznamu členů](#member_lists)  
  
-   [Explicitní konstruktory](#explicit_constructors)  
  
-   [Výchozí konstruktory](#default_constructors)  
  
-   [Kopírování a přesouvání konstruktory](#copy_and_move_constructors)  
  
-   [Explicitně přednastavené a odstraněné konstruktory](#explicitly_defaulted_and_deleted_constructors)  
  
-   [Konstruktorů v odvozených třídách](#constructors_in_derived_classes)  
  
-   [Virtuální funkce v konstruktorech](#virtual_functions_in_constructors)  
  
-   [Konstruktory a složené třídy](#constructors_in_composite_classes)  
  
-   [Delegování konstruktorů](#delegating_constructors)  
  
-   [Dědění konstruktory (C ++ 11)](#inheriting_constructors)  
  
-   [Pravidla deklarace konstruktorů](#rules_for_declaring_constructors)  
  
-   [Explicitní volání konstruktory](#explicitly_invoking_constructors)  
  
##  <a name="order_of_construction"></a>Pořadí vytváření  
 Konstruktor provádí svou práci v tomto pořadí:  
  
1.  Volá základní třídu a členské konstruktory v pořadí deklarace.  
  
2.  Pokud je třída odvozena z virtuálních základních tříd, inicializuje virtuální základní ukazatele na objekt.  
  
3.  Pokud třída má nebo dědí virtuální funkce, inicializuje ukazatele virtuální funkce objektu. Virtuální funkce ukazatelů ukazuje na tabulku virtuální funkce třídy umožňující správnou vazbu volání virtuální funkce na kód.  
  
4.  Je spuštěn libovolný kód v těle jeho funkce.  
  
 Následující příklad zobrazuje pořadí, ve kterém jsou volány základní třídy a konstruktory členů v konstruktoru pro odvozenou třídu. Nejprve se volá základní konstruktor, poté se inicializují členy základní třídy v pořadí, v jakém se zobrazují v deklaraci třídy, a poté je volán odvozený konstruktor.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class Contained1 {  
public:  
    Contained1() {  
        cout << "Contained1 constructor." << endl;  
    }  
};  
  
class Contained2 {  
public:  
    Contained2() {  
        cout << "Contained2 constructor." << endl;  
    }  
};  
  
class Contained3 {  
public:  
    Contained3() {  
        cout << "Contained3 constructor." << endl;  
    }  
};  
  
class BaseContainer {  
public:  
    BaseContainer() {  
        cout << "BaseContainer constructor." << endl;  
    }  
private:  
    Contained1 c1;  
    Contained2 c2;  
};  
  
class DerivedContainer : public BaseContainer {  
public:  
    DerivedContainer() : BaseContainer() {  
        cout << "DerivedContainer constructor." << endl;  
    }  
private:  
    Contained3 c3;  
};  
  
int main() {  
    DerivedContainer dc;  
    int x = 3;  
}  
  
```  
  
 Zde je výstup:  
  
```  
Contained1 constructor.  
Contained2 constructor.  
BaseContainer constructor.  
Contained3 constructor.  
DerivedContainer constructor.  
```  
  
 Pokud konstruktor vyvolá výjimku, pořadí zničení je obrácené pořadí konstrukce:  
  
1.  Kód v těle funkce konstruktoru je oddělen.  
  
2.  Základní třída a členské objekty jsou zničeny v obráceném pořadí deklarace.  
  
3.  Pokud je konstruktor bez delegování, jsou zničeny všechny úplně vytvořené objekty a členy. Vzhledem k tomu, že objekt samotný není úplně vytvořen, není spuštěn destruktor.  
  
##  <a name="member_lists"></a>Seznamu členů  
 Členy třídy z argumenty konstruktoru inicializujte pomocí inicializátoru seznamu členů. Tato metoda používá *přímé inicializace*, což je efektivnější než použití přiřazení operátory uvnitř těla konstruktoru.  
  
```cpp  
class Box {  
public:  
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height) // member init list  
    {}  
    int Volume() {return m_width * m_length * m_height; }  
private:  
    int m_width;  
    int m_length;  
    int m_height;  
  
};  
  
```  
  
 Vytvoření objektu pole:  
  
```  
Box b(42, 21, 12);  
cout << "The volume is " << b.Volume();  
```  
  
##  <a name="explicit_constructors"></a>Explicitní konstruktory  
 Pokud třída má konstruktor pomocí jediného parametru, nebo pokud mají všechny parametry s výjimkou jednu výchozí hodnotu, typ parametru můžete implicitně převést na typ třídy. Například pokud `Box` třída má konstruktor takto:  
  
```  
Box(int size): m_width(size), m_length(size), m_height(size){}  
```  
  
 Je možné k chybě při inicializaci pole takto:  
  
```  
Box b = 42;  
```  
  
 Nebo typ int předat funkce, která přebírá pole:  
  
```  
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
  
 Takové převody může být užitečná v některých případech, ale často může vést k jemně ale závažných chyb v kódu. Obecně platí, měli byste použít `explicit` – klíčové slovo v konstruktoru (a uživatelem definované operátory), aby se zabránilo tento druh typu implicitní převod:  
  
```  
  
explicit Box(int size): m_width(size), m_length(size), m_height(size){}  
```  
  
 Po explicitní konstruktor tohoto řádku způsobí, že chyba kompilátoru: `ShippingOrder so(42, 10.8);`.  Další informace najdete v tématu [uživatelem definované převody typů](../cpp/user-defined-type-conversions-cpp.md).  
  
##  <a name="default_constructors"></a>Výchozí konstruktory  
 *Výchozí konstruktory* mít žádné parametry; se řídí mírně odlišná pravidla:  
  
 Výchozí konstruktory jsou jedním z *speciální členské funkce*; Pokud žádné konstruktory jsou deklarované v třídě, kompilátor poskytuje výchozí konstruktor:  
  
```cpp  
class Box {  
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height){}  
};  
  
int main(){  
  
    Box box1{}; // call compiler-generated default ctor  
    Box box2;   // call compiler-generated default ctor  
}  
```  
  
 Když voláte výchozí konstruktor a zkusíte použít závorky, bude vytvořeno upozornění:  
  
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
    Box box4;     // compiler error C2512: no appropriate default constructor available  
}  
  
```  
  
 Pokud třída nemá žádný výchozí konstruktor, pole objektů této třídy nemůže být vytvořeno pomocí syntaxe samostatných hranatých závorek. Například s ohledem na předchozí blok kódu nemůže být pole oken deklarováno takto:  
  
```cpp  
Box boxes[3];    // compiler error C2512: no appropriate default constructor available  
  
```  
  
 Můžete však použít sadu inicializačních seznamů pro inicializaci pole oken:  
  
```cpp  
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };  
```  
  
##  <a name="copy_and_move_constructors"></a>Kopírování a přesouvání konstruktory  
 A *kopírovacího konstruktoru* je speciální členské funkce, která vezme jako vstupní odkaz na objekt stejný typ a vytvoří kopii ho. Další informace najdete v tématu [kopírovací konstruktory a operátory přiřazení kopírování (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md). A *přesunout konstruktor* je taky speciální členské funkce, která přemísťuje vlastnictví existující objekt data do nové proměnné bez kopírování původní data. Další informace najdete v tématu [přesunout konstruktory a operátory přesunout přiřazení (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).  
  
##  <a name="explicitly_defaulted_and_deleted_constructors"></a>Explicitně přednastavené a odstraněné konstruktory  
 Můžete explicitně *výchozí* zkopírujte konstruktory, výchozí konstruktory, přesunout konstruktory, zkopírujte operátory přiřazení, přesuňte operátory přiřazení a destruktory. Můžete explicitně *odstranit* všechny speciální členské funkce. Další informace najdete v tématu [explicitně uvedena a funkce, odstranit](../cpp/explicitly-defaulted-and-deleted-functions.md).  
  
##  <a name="constructors_in_derived_classes"></a>Konstruktorů v odvozených třídách  
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
  
### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Konstruktory pro třídy, které mají vícenásobnou dědičnost  
 Pokud je třída odvozena z více základních tříd, konstruktory základní třídy jsou vyvolány v pořadí, ve kterém jsou uvedeny v deklaraci odvozené třídy:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class BaseClass1 {  
public:  
    BaseClass1() {  
        cout << "BaseClass1 constructor." << endl;  
    }  
};  
class BaseClass2 {  
public:  
    BaseClass2() {  
        cout << "BaseClass2 constructor." << endl;  
    }  
};  
class BaseClass3{  
public:  
    BaseClass3() {  
        cout << "BaseClass3 constructor." << endl;  
    }  
};  
class DerivedClass : public BaseClass1, public BaseClass2, public BaseClass3  {  
public:  
    DerivedClass() {  
        cout << "DerivedClass constructor." << endl;  
    }  
};  
  
int main() {  
    DerivedClass dc;  
}  
  
```  
  
 Můžete očekávat následující výstup:  
  
```  
BaseClass1 constructor.  
BaseClass2 constructor.  
BaseClass3 constructor.  
DerivedClass constructor.  
```  
  
##  <a name="virtual_functions_in_constructors"></a>Virtuální funkce v konstruktorech  
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
  
```  
BaseClass print_it  
Derived Class print_it  
```  
  
##  <a name="constructors_in_composite_classes"></a>Konstruktory a složené třídy  
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
  
##  <a name="delegating_constructors"></a>Delegování konstruktorů  
 A *delegování konstruktor* volá jiný konstruktor ve stejné třídě udělat některé úkoly inicializace. V následujícím příkladu má odvozená třída tři konstruktory – druhý konstruktor deleguje na první a třetí konstruktor deleguje na druhý:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ConstructorDestructor {  
public:  
    ConstructorDestructor() {  
        cout << "ConstructorDestructor default constructor." << endl;  
    }  
    ConstructorDestructor(int int1) {  
        cout << "ConstructorDestructor constructor with 1 int." << endl;  
    }  
    ConstructorDestructor(int int1, int int2) : ConstructorDestructor(int1) {  
        cout << "ConstructorDestructor constructor with 2 ints." << endl;  
  
        throw exception();  
    }  
    ConstructorDestructor(int int1, int int2, int int3) : ConstructorDestructor(int1, int2) {  
        cout << "ConstructorDestructor constructor with 3 ints." << endl;  
    }  
    ~ConstructorDestructor() {  
        cout << "ConstructorDestructor destructor." << endl;  
    }  
};  
  
int main() {  
    ConstructorDestructor dc(1, 2, 3);  
}  
  
```  
  
 Zde je výstup:  
  
```  
ConstructorDestructor constructor with 1 int.  
ConstructorDestructor constructor with 2 ints.  
ConstructorDestructor constructor with 3 ints.  
```  
  
 Objekt vytvořený pomocí konstruktorů je plně inicializován ihned po dokončení jakéhokoli konstruktoru. `DerivedContainer(int int1)`úspěšné, ale `DerivedContainer(int int1, int int2)` selže a destruktoru je volána.  
  
```cpp  
class ConstructorDestructor {  
public:  
    ConstructorDestructor() {  
        cout << "ConstructorDestructor default constructor." << endl;  
    }  
    ConstructorDestructor(int int1) {  
        cout << "ConstructorDestructor constructor with 1 int." << endl;  
    }  
    ConstructorDestructor(int int1, int int2) : ConstructorDestructor(int1) {  
        cout << "ConstructorDestructor constructor with 2 ints." << endl;  
        throw exception();  
    }  
    ConstructorDestructor(int int1, int int2, int int3) : ConstructorDestructor(int1, int2) {  
        cout << "ConstructorDestructor constructor with 3 ints." << endl;  
    }  
  
    ~ConstructorDestructor() {  
        cout << "ConstructorDestructor destructor." << endl;  
    }  
};  
  
int main() {  
  
    try {  
        ConstructorDestructor cd{ 1, 2, 3 };  
    }  
    catch (const exception& ex){  
    }  
}  
  
```  
  
 Výstup:  
  
```  
ConstructorDestructor constructor with 1 int.  
ConstructorDestructor constructor with 2 ints.  
ConstructorDestructor destructor.  
```  
  
 Další informace najdete v tématu [jednotná inicializace a delegování konstruktorů](../cpp/uniform-initialization-and-delegating-constructors.md).  
  
##  <a name="inheriting_constructors"></a>Dědění konstruktory (C ++ 11)  
 Odvozená třída může dědit vlastnosti konstruktorů z přímé základní třídu pomocí pomocí deklarace, jak je znázorněno v následujícím příkladu:  
  
```  
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
  
int main(int argc, char argv[])  
{  
    cout << "Derived d1(5) calls: ";   
    Derived d1(5);  
    cout << "Derived d1('c') calls: ";  
    Derived d2('c');  
    cout << "Derived d3 = d2 calls: " ;  
    Derived d3 = d2;  
    cout << "Derived d4 calls: ";  
    Derived d4;   
  
    // Keep console open in debug mode:  
    cout << endl << "Press Enter to exit.";  
    char in[1];  
    cin.getline(in, 1);  
    return 0;  
}  
  
/* Output:  
Derived d1(5) calls: Base(int)  
Derived d1('c') calls: Base(char)  
Derived d3 = d2 calls: Base(Base&)  
Derived d4 calls: Base()  
  
Press Enter to exit.  
  
```  
  
 Pomocí příkazu přenese do oboru všechny konstruktory ze základní třídy kromě těch, které mají stejné definice virů, aby konstruktorů v odvozené třídě. Obecně platí je nejvhodnější použít dědičných konstruktory při odvozené třídy deklaruje žádné nové členy dat nebo konstruktory.  
  
 Šablona třídy lze dědit všechny konstruktory z argument typu, pokud tento typ určuje základní třídu:  
  
```  
template< typename T >  
class Derived : T {  
    using T::T;   // declare the constructors from T  
    // ...  
};  
  
```  
  
 Odvozená třída nelze z vícenásobné třídy base dědit, pokud tyto základní třídy mít konstruktory, které mají stejné podpis.  
  
##  <a name="rules_for_declaring_constructors"></a>Pravidla deklarace konstruktorů  
 Konstruktor má stejný název jako jeho třída. Podle pravidel přetížených funkcí lze deklarovat libovolný počet konstruktorů.  
  
 `argument-declaration-list` může být prázdný.  
  
 Jazyk C++ definuje dva zvláštní typy konstruktorů, výchozí a kopírovací konstruktory, které jsou popsány v následující tabulce.  
  
### <a name="default-and-copy-constructors"></a>Výchozí a kopírovací konstruktory  
  
|Druh konstrukce|Arguments|Účel|  
|--------------------------|---------------|-------------|  
|Výchozí konstruktor|Lze jej volat bez argumentů|Vytvoří výchozí objekt typu třídy|  
|Kopírovací konstruktor|Přijímá jediný argument odkazu na stejný typ třídy|Kopírování objektů typu třídy|  
  
 Výchozí konstruktory lze volat bez argumentů. Lze však deklarovat výchozí konstruktor se seznamem argumentů za předpokladu, že všechny argumenty mají výchozí hodnoty. Podobně musí kopírovací konstruktory přijímat jediný argument odkazu na stejný typ třídy. Lze zadat další argumenty za předpokladu, že všechny následující argumenty mají výchozí hodnoty.  
  
 Pokud nezadáte žádné konstruktory, kompilátor se pokusí vygenerovat výchozí konstruktor. Pokud nezadáte žádný kopírovací konstruktor, kompilátor se jej pokusí vygenerovat. Tyto konstruktory vygenerované kompilátorem jsou považovány za veřejné členské funkce. Pokud zadáte kopírovací konstruktor, jehož první argument je objekt a ne odkaz, je vygenerována chyba.  
  
 Výchozí konstruktor vygenerovaný kompilátorem nastaví objekt (inicializuje tabulky vftables a vbtables, jak je popsáno dříve) a zavolá výchozí konstruktory základních tříd a členů, ale neprovede žádné další akce. Konstruktory základních tříd a členů jsou zavolány pouze tehdy, pokud existují, jsou přístupné a jsou jednoznačné.  
  
 Kopírovací konstruktor vygenerovaný kompilátorem vytvoří nový objekt a provede kopírování členů obsahu objektu, který chcete zkopírovat. Pokud konstruktory základních tříd nebo členů existují, jsou zavolány. V opačném případě se provede operace bitového kopírování.  
  
 Pokud všechny základní a člena třídy třídy `type` mít kopírovací konstruktory, které přijímají **const** argument, generované kompilátorem kopírovací konstruktor přijímá jeden argument typu **const** `type` **&**. V opačném kopírování generované kompilátorem konstruktor přijímá jeden argument typu `type`  **&** .  
  
 Konstruktor můžete použít k chybě při inicializaci **const** nebo `volatile` objektu, ale samotný konstruktoru nelze deklarovat jako **const** nebo `volatile`. Třída platné úložiště pro konstruktor je **vložené**; použití jiných Modifikátor třídy úložiště včetně `__declspec` – klíčové slovo, s konstruktor způsobí chybu kompilátoru.  
  
 Stdcall konvence volání, které se používá na statické členské funkce a globální funkce deklarovat s **__stdcall** – klíčové slovo a že nepoužívejte seznam argumentů s proměnnou. Při použití **__stdcall** – klíčové slovo na nestatické členské funkce, jako je například konstruktor, kompilátor použije thiscall – konvence volání. "  
  
 Konstruktory základních tříd nejsou zděděny odvozenými třídami. Při vytvoření objektu typu odvozené třídy je objekt nejprve zkonstruován s komponentami základní třídy a poté se přesune na komponenty odvozené třídy. Kompilátor používá každý základní třída – konstruktor, jako je ta část kompletní objekt inicializovat (s výjimkou případů virtuální odvození.  
  
##  <a name="explicitly_invoking_constructors"></a>Explicitní volání konstruktory  
 Konstruktory mohou být v programu explicitně volány k vytvoření objektů daného typu. Chcete-li například vytvořit dva objekty `Point` popisující konce řádků, lze napsat následující kód:  
  
```  
DrawLine( Point( 13, 22 ), Point( 87, 91 ) );  
```  
  
 Jsou vytvořeny dva objekty typu `Point`, předány funkci `DrawLine` a na konci výrazu (volání funkce) zničeny.  
  
 Další kontext, ve kterém je konstruktor explicitně volán, je inicializace:  
  
```  
Point pt = Point( 7, 11 );  
```  
  
 Objekt typu `Point` je vytvořen a inicializován pomocí konstruktoru, který přijímá dva argumenty typu `int`.  
  
 Objekty vytvořené explicitním voláním konstruktorů (jako v předchozích dvou příkladech) jsou nepojmenované a mají životnost výrazu, ve kterém jsou vytvořeny. To je podrobněji větší v [dočasné objekty](../cpp/temporary-objects.md).  
  
 Obvykle je bezpečné volat všechny členské funkce v rámci konstruktoru, protože objekt byl zcela nastaven (virtuální tabulky byly inicializovány a podobně) před vykonáním prvního řádku kódu. Pro členskou funkci je však potenciálně nebezpečné volat virtuální členskou funkci pro abstraktní základní třídu během vytváření nebo zničení.  
  
 Konstruktory mohou volat virtuální funkce. Při volání virtuálních funkcí je vyvolána funkce definovaná pro vlastní třídu konstruktoru (nebo pro třídu zděděnou ze základní třídy). Následující příklad ukazuje, co se stane, když je volána virtuální funkce v rámci konstruktoru:  
  
```  
// specl_calling_virtual_functions.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Base  
{  
public:  
    Base();             // Default constructor.  
    virtual void f();   // Virtual member function.  
};  
  
Base::Base()  
{  
    cout << "Constructing Base sub-object\n";  
    f();                // Call virtual member function  
}                       //  from inside constructor.  
  
void Base::f()  
{  
    cout << "Called Base::f()\n";  
}  
  
class Derived : public Base  
{  
public:  
    Derived();          // Default constructor.  
    void f();           // Implementation of virtual  
};                      //  function f for this class.  
  
Derived::Derived()  
{  
    cout << "Constructing Derived object\n";  
}  
  
void Derived::f()  
{  
    cout << "Called Derived::f()\n";  
}  
  
int main()  
{  
    Derived d;  
}  
```  
  
 Po spuštění předchozího programu spustí deklarace `Derived d` následující posloupnost událostí:  
  
1.  Je volán konstruktor pro třídu `Derived` (`Derived::Derived`).  
  
2.  Před vstupem do těla konstruktoru třídy `Derived` je volán konstruktor třídy `Base` (`Base::Base`).  
  
 `Base::Base` volá funkci `f`, která je virtuální funkcí. Obvykle by byla volána funkce `Derived::f`, protože objekt `d` je typu `Derived`. Vzhledem k tomu, že funkce `Base::Base` je konstruktorem, objekt není ještě typu `Derived` a volá se funkce `Base::f`.  
  
