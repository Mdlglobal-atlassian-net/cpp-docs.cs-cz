---
title: Inicializátory
ms.date: 11/19/2018
helpviewer_keywords:
- array-element initializers
- initializing arrays [C++], initializers
- arrays [C++], array-element initializers
- declarators, as initializers
- initializers, array element
ms.assetid: ce301ed8-aa1c-47b2-bb39-9f0541b4af85
ms.openlocfilehash: 1890899fb2ad63bff06d514ae8b18f9dc3ff9e21
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183525"
---
# <a name="initializers"></a>Inicializátory

Inicializátor určuje počáteční hodnotu proměnné. Můžete inicializovat proměnné v těchto kontextech:

- V definici proměnné:

    ```cpp
    int i = 3;
    Point p1{ 1, 2 };
    ```

- Jako jeden z parametrů funkce:

    ```cpp
    set_point(Point{ 5, 6 });
    ```

- Jako návratovou hodnotu funkce:

    ```cpp
    Point get_new_point(int x, int y) { return { x, y }; }
    Point get_new_point(int x, int y) { return Point{ x, y }; }
    ```

Inicializátory mohou mít tyto formy:

- Výraz (nebo seznam výrazů oddělených čárkami) v závorkách:

    ```cpp
    Point p1(1, 2);
    ```

- Znaménko rovná se za výrazem:

    ```cpp
    string s = "hello";
    ```

- Seznam inicializátorů v závorkách. Seznam může být prázdný, nebo může sestávat z několika seznamů, jako v následujícím příkladu:

    ```cpp
    struct Point{
        int x;
        int y;
    };
    class PointConsumer{
    public:
        void set_point(Point p){};
        void set_points(initializer_list<Point> my_list){};
    };
    int main() {
        PointConsumer pc{};
        pc.set_point({});
        pc.set_point({ 3, 4 });
        pc.set_points({ { 3, 4 }, { 5, 6 } });
    }
    ```

## <a name="kinds-of-initialization"></a>Druhy inicializace

Existuje několik druhů inicializace, které mohou nastat v různých fázích provádění programu. Různé druhy inicializace se vzájemně nevylučují, například inicializační seznam může spustit inicializační hodnotu a za jiných okolností to může spustit agregační inicializaci.

### <a name="zero-initialization"></a>Inicializace nula

Inicializace nula je nastavení proměnné na hodnotu nula implicitně převedenou na typ:

- Číselné proměnné jsou inicializovány na hodnotu 0 (nebo 0,0 nebo 0,0000000000 atd.).

- Proměnné typu CHAR jsou inicializovány na hodnotu `'\0'`.

- Ukazatele jsou inicializovány na hodnotu **nullptr**.

- Pole, [POD](../standard-library/is-pod-class.md) třídy, struktury a sjednocení mají své členy inicializovány na hodnotu nula.

Inicializace nula je provedena v různých časech:

- Při spuštění programu pro všechny pojmenované proměnné, které mají statické trvání. Tyto proměnné mohou být později znovu inicializovány.

- Během inicializace hodnoty pro skalární typy a typy tříd POD, které jsou inicializovány pomocí prázdné závorky.

- Pro pole, která mají inicializovánu pouze podmnožinu svých členů.

Zde jsou některé příklady inicializace nula:

```cpp
struct my_struct{
    int i;
    char c;
};

int i0;              // zero-initialized to 0
int main() {
    static float f1;  // zero-initialized to 0.000000000
    double d{};     // zero-initialized to 0.00000000000000000
    int* ptr{};     // initialized to nullptr
    char s_array[3]{'a', 'b'};  // the third char is initialized to '\0'
    int int_array[5] = { 8, 9, 10 };  // the fourth and fifth ints are initialized to 0
    my_struct a_struct{};   // i = 0, c = '\0'
}
```

### <a name="default_initialization"></a> Výchozí inicializace

Výchozí inicializace pro třídy, struktury a sjednocení je inicializace s výchozím konstruktorem. Výchozí konstruktor může být volána bez výrazu inicializace nebo s **nové** – klíčové slovo:

```cpp
MyClass mc1;
MyClass* mc3 = new MyClass;
```

Pokud třída, struktura nebo sjednocení nemá výchozí konstruktor, kompilátor vydává chybu.

Skalární proměnné jsou inicializované, když jsou definovány bez výraz inicializace ve výchozím nastavení. Mají neurčité hodnoty.

```cpp
int i1;
float f;
char c;
```

Pole jsou inicializované, když jsou definovány bez výraz inicializace ve výchozím nastavení. Pokud je pole inicializována ve výchozím nastavení, jeho členové jsou inicializované ve výchozím nastavení a mají neurčité hodnoty, jako v následujícím příkladu:

```cpp
int int_arr[3];
```

Pokud členové pole nemají výchozí konstruktor, kompilátor vydává chybu.

#### <a name="default-initialization-of-constant-variables"></a>Výchozí inicializace konstantních proměnných

Konstantní proměnné musí být deklarovány společně s inicializátorem. Pokud jsou Skalární typy způsobí chybu kompilátoru, a pokud jsou typy tříd, které mají výchozí konstruktor, způsobují upozornění:

```cpp
class MyClass{};
int main() {
    //const int i2;   // compiler error C2734: const object must be initialized if not extern
    //const char c2;  // same error
    const MyClass mc1; // compiler error C4269: 'const automatic data initialized with compiler generated default constructor produces unreliable results
}
```

#### <a name="default-initialization-of-static-variables"></a>Výchozí inicializace statických proměnných

Statické proměnné, které jsou deklarovány pomocí žádný inicializátor jsou inicializovány na hodnotu 0 (implicitně převeden na typ).

```cpp
class MyClass {
private:
    int m_int;
    char m_char;
};

int main() {
    static int int1;       // 0
    static char char1;     // '\0'
    static bool bool1;   // false
    static MyClass mc1;     // {0, '\0'}
}
```

Další informace o inicializaci globálních statických objektů naleznete v tématu [Additional Startup Considerations](../cpp/additional-startup-considerations.md).

### <a name="value-initialization"></a>Inicializace hodnoty

V následujících případech dojde k inicializaci hodnoty:

- Pojmenovaná hodnota je inicializována pomocí inicializace prázdné závorky

- anonymní dočasný objekt je inicializován pomocí prázdných kulatých závorek nebo složených závorek

- objekt je inicializován s **nové** – klíčové slovo a prázdných kulatých závorek nebo složených závorek

Inicializace hodnoty provede následující akce:

- u tříd s nejméně jeden veřejný konstruktor je zavolán výchozí konstruktor

- pro třídy mimo sjednocení s žádné deklarované konstruktory je objekt inicializován nulou a je zavolán výchozí konstruktor

- pro pole je každý prvek inicializovat pomocí hodnoty.

- ve všech ostatních případech je proměnná inicializována nula

```cpp
class BaseClass {
private:
    int m_int;
};

int main() {
    BaseClass bc{};     // class is initialized
    BaseClass*  bc2 = new BaseClass();  // class is initialized, m_int value is 0
    int int_arr[3]{};  // value of all members is 0
    int a{};     // value of a is 0
    double b{};  // value of b is 0.00000000000000000
}
```

### <a name="copy-initialization"></a>Kopírovat inicializaci

Kopírování inicializace je inicializace jednoho objektu pomocí jiného objektu. Vyvolá se v následujících případech:

- Proměnná je inicializována pomocí znaménko rovná se

- argument předaný do funkce

- objekt je vrácen z funkce

- Výjimka je vyvolána nebo zachycena

- Nestatický datový člen je inicializován pomocí znaménko rovná se

- třídy, struktury a unie členy jsou inicializovány kopírováním inicializace během inicializace agregace. Zobrazit [inicializace agregace](#agginit) příklady.

Následující kód ukazuje několik příkladů Inicializace kopírování:

```cpp
#include <iostream>
using namespace std;

class MyClass{
public:
    MyClass(int myInt) {}
    void set_int(int myInt) { m_int = myInt; }
    int get_int() const { return m_int; }
private:
    int m_int = 7; // copy initialization of m_int

};
class MyException : public exception{};
int main() {
    int i = 5;              // copy initialization of i
    MyClass mc1{ i };
    MyClass mc2 = mc1;      // copy initialization of mc2 from mc1
    MyClass mc1.set_int(i);    // copy initialization of parameter from i
    int i2 = mc2.get_int(); // copy initialization of i2 from return value of get_int()

    try{
        throw MyException();
    }
    catch (MyException ex){ // copy initialization of ex
        cout << ex.what();
    }
}
```

Inicializace kopírování nemůže vyvolat explicitní konstruktory.

```cpp
vector<int> v = 10; // the constructor is explicit; compiler error C2440: cannot convert from 'int' to 'std::vector<int,std::allocator<_Ty>>'
regex r = "a.*b"; // the constructor is explicit; same error
shared_ptr<int> sp = new int(1729); // the constructor is explicit; same error
```

V některých případech, pokud je kopírovací konstruktu třídy odstraněn nebo nepřístupný, kopírování inicializace způsobí chybu kompilátoru.

### <a name="direct-initialization"></a>Přímá inicializace

Přímá inicializace je inicializace pomocí složených závorek (prázdný) nebo složených závorek. Na rozdíl od kopírování inicializace nemůže vyvolat explicitní konstruktory. Vyvolá se v následujících případech:

- Proměnná je inicializována s neprázdný závorek nebo složených závorek

- Proměnná je inicializována s **nové** – klíčové slovo a neprázdný závorek nebo složených závorek

- Proměnná je inicializována s **static_cast**

- v konstruktoru jsou základní třídy a nestatické členy inicializovány pomocí seznamu inicializátorů

- v kopii zachycené proměnné ve výrazu lambda

Následující kód ukazuje některé příklady přímé inicializace:

```cpp
class BaseClass{
public:
    BaseClass(int n) :m_int(n){} // m_int is direct initialized
private:
    int m_int;
};

class DerivedClass : public BaseClass{
public:
    // BaseClass and m_char are direct initialized
    DerivedClass(int n, char c) : BaseClass(n), m_char(c) {}
private:
    char m_char;
};
int main(){
    BaseClass bc1(5);
    DerivedClass dc1{ 1, 'c' };
    BaseClass* bc2 = new BaseClass(7);
    BaseClass bc3 = static_cast<BaseClass>(dc1);

    int a = 1;
    function<int()> func = [a](){  return a + 1; }; // a is direct initialized
    int n = func();
}
```

### <a name="list-initialization"></a>Inicializace seznamu

Inicializační seznam se vyvolá při proměnná je inicializována pomocí seznamu inicializátorů v závorkách. V následujících případech můžete použít seznamy inicializátorů v závorkách:

- Proměnná je inicializována.

- Třída je inicializována s **nové** – klíčové slovo

- objekt je vrácen z funkce

- argument předaný do funkce

- jeden z argumentů v přímé inicializaci

- v inicializátoru nestatický datový člen

- v seznamu inicializátorů konstruktoru

Následující kód ukazuje některé příklady Inicializace seznamu:

```cpp
class MyClass {
public:
    MyClass(int myInt, char myChar) {}
private:
    int m_int[]{ 3 };
    char m_char;
};
class MyClassConsumer{
public:
    void set_class(MyClass c) {}
    MyClass get_class() { return MyClass{ 0, '\0' }; }
};
struct MyStruct{
    int my_int;
    char my_char;
    MyClass my_class;
};
int main() {
    MyClass mc1{ 1, 'a' };
    MyClass* mc2 = new MyClass{ 2, 'b' };
    MyClass mc3 = { 3, 'c' };

    MyClassConsumer mcc;
    mcc.set_class(MyClass{ 3, 'c' });
    mcc.set_class({ 4, 'd' });

    MyStruct ms1{ 1, 'a', { 2, 'b' } };
}
```

### <a name="agginit"></a> Inicializace agregace

Inicializace agregace je forma inicializace seznamu pro pole nebo typy tříd (často struktury nebo sjednocení), které mají:

- žádné soukromé nebo chráněné členy

- žádné uživatelem zadané konstruktory s výjimkou výslovně nastavených výchozích nebo odstraněných konstruktorů

- žádné základní třídy

- žádné virtuální členské funkce

> [!NOTE]
> <!--conformance note-->V sadě Visual Studio 2015 a starší agregace není povoleno mít inicializátory složenou závorku nebo rovná pro nestatické členy. Toto omezení byl v C ++ 14 standard odebrána a implementovaná v sadě Visual Studio 2017.

Inicializátory agregace se skládají z inicializačního seznamu v závorkách, s nebo bez něj znak rovná se, stejně jako v následujícím příkladu:

```cpp
#include <iostream>
using namespace std;

struct MyAggregate{
    int myInt;
    char myChar;
};

int main() {
    MyAggregate agg1{ 1, 'c' };

    cout << "agg1: " << agg1.myChar << ": " << agg1.myInt << endl;
    cout << "agg2: " << agg2.myChar << ": " << agg2.myInt << endl;

    int myArr1[]{ 1, 2, 3, 4 };
    int myArr2[3] = { 5, 6, 7 };
    int myArr3[5] = { 8, 9, 10 };

    cout << "myArr1: ";
    for (int i : myArr1){
        cout << i << " ";
    }
    cout << endl;

    cout << "myArr3: ";
    for (auto const &i : myArr3) {
        cout << i << " ";
    }
    cout << endl;
}
```

Byste měli vidět následující výstup:

```Output
agg1: c: 1
agg2: d: 2
myArr1: 1 2 3 4
myArr3: 8 9 10 0 0
```

> [!IMPORTANT]
> Členy pole, které jsou deklarovány, ale během inicializace agregace nebyly explicitně inicializovány inicializovány nulou, stejně jako v `myArr3` výše.

#### <a name="initializing-unions-and-structs"></a>Inicializace sjednocení a struktur

Pokud sjednocení nemá konstruktor, inicializovat s jedinou hodnotu (nebo pomocí jiné instance sjednocení). Hodnota slouží k inicializaci prvního nestatické pole. Tím se liší od inicializace struktury, ve které první hodnota v inicializátoru slouží k inicializaci prvního pole, druhá k inicializaci druhé pole a tak dále. Porovnejte inicializace sjednocení a struktur v následujícím příkladu:

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
union MyUnion {
    int my_int;
    char my_char;
    bool my_bool;
    MyStruct my_struct;
};

int main() {
    MyUnion mu1{ 'a' };  // my_int = 97, my_char = 'a', my_bool = true, {myInt = 97, myChar = '\0'}
    MyUnion mu2{ 1 };   // my_int = 1, my_char = 'x1', my_bool = true, {myInt = 1, myChar = '\0'}
    MyUnion mu3{};      // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    MyUnion mu4 = mu3;  // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    //MyUnion mu5{ 1, 'a', true };  // compiler error: C2078: too many initializers
    //MyUnion mu6 = 'a';            // compiler error: C2440: cannot convert from 'char' to 'MyUnion'
    //MyUnion mu7 = 1;              // compiler error: C2440: cannot convert from 'int' to 'MyUnion'

    MyStruct ms1{ 'a' };            // myInt = 97, myChar = '\0'
    MyStruct ms2{ 1 };              // myInt = 1, myChar = '\0'
    MyStruct ms3{};                 // myInt = 0, myChar = '\0'
    MyStruct ms4{1, 'a'};           // myInt = 1, myChar = 'a'
    MyStruct ms5 = { 2, 'b' };      // myInt = 2, myChar = 'b'
}
```

#### <a name="initializing-aggregates-that-contain-aggregates"></a>Inicializace agregátů, které obsahují agregáty

Typy agregátů mohou obsahovat další typy agregátů, pro příklad pole polí, pole struktur a tak dále. Tyto typy jsou inicializovány pomocí vnořených sad závorek, například:

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
int main() {
    int intArr1[2][2]{{ 1, 2 }, { 3, 4 }};
    int intArr3[2][2] = {1, 2, 3, 4};
    MyStruct structArr[]{ { 1, 'a' }, { 2, 'b' }, {3, 'c'} };
}
```

### <a name="reference-initialization"></a>Inicializace odkazu

Proměnné typu odkazu je nutné inicializovat objektem typu, ze kterého je typ odkazu odvozen, nebo objektem typu, jenž lze převést na typ, ze kterého je odvozen typ odkazu. Příklad:

```cpp
// initializing_references.cpp
int iVar;
long lVar;
int main()
{
    long& LongRef1 = lVar;        // No conversion required.
    long& LongRef2 = iVar;        // Error C2440
    const long& LongRef3 = iVar;  // OK
    LongRef1 = 23L;               // Change lVar through a reference.
    LongRef2 = 11L;               // Change iVar through a reference.
    LongRef3 = 11L;               // Error C3892
}
```

Jediný způsob, jak inicializovat odkaz na dočasný objekt, je inicializovat objekt dočasné konstanty. Po inicializaci bude proměnná typu odkazu vždy odkazovat na stejný objekt. Nelze jej změnit pro odkazování na jiný objekt.

Přestože je syntaxe stejná, inicializace proměnných typu odkazu a přiřazení proměnné referenčního typu jsou sémanticky rozdílné. V předchozím příkladu se přiřazení, která mění `iVar` a `lVar`, jeví inicializacím totožně, ale mají různé účinky. Inicializace určuje objekt, na který odkazuje proměnná typu odkazu. Přiřazení se přiřadí prostřednictvím odkazu na odkazovaný objekt.

Protože předání argumentu typu odkazu na funkci a návratová hodnota typu odkazu funkce inicializace, jsou formální argumenty funkce inicializovány správně, stejně jako vrácené odkazy.

Proměnné typu odkazu mohou být deklarovány bez použití inicializátorů pouze v následujících případech:

- Deklarace funkce (prototypy). Příklad:

    ```cpp
    int func( int& );
    ```

- Deklarace návratového typu funkce. Příklad:

    ```cpp
    int& func( int& );
    ```

- Deklarace členu třídy typu odkazu. Příklad:

    ```cpp
    class c {public:   int& i;};
    ```

- Deklarace proměnné explicitně zadané jako **extern**. Příklad:

    ```cpp
    extern int& iVal;
    ```

Při inicializaci proměnné typu odkazu používá kompilátor graf rozhodnutí zobrazený na následujícím obrázku pro výběr mezi vytvořením odkazu na objekt nebo vytvořením dočasného objektu, na který odkaz směřuje.

![Graf rozhodnutí inicializace typů odkazů](../cpp/media/vc38s71.gif "graf rozhodnutí inicializace typů odkazů") <br/>
Graf rozhodnutí inicializace typů odkazů

Odkazy na **volatile** typy (deklarované jako **volatile** *typename* <strong>&</strong> *identifikátor*) mohou být inicializovány pomocí **volatile** objekty stejného typu nebo objekty, které nejsou deklarovány jako **volatile**. Nelze je však, inicializovat pomocí **const** objekty daného typu. Podobně, odkazy na **const** typy (deklarované jako **const** *typename* <strong>&</strong> *identifikátor* ) mohou být inicializovány pomocí **const** objekty stejného typu (nebo čímkoli, kde existuje převod na daný typ nebo pomocí objektů, které nejsou deklarovány jako **const**). Nelze je však, inicializovat pomocí **volatile** objekty daného typu.

Odkazy, které nejsou kvalifikovány buď pomocí **const** nebo **volatile** – klíčové slovo lze inicializovat pouze objekty deklarovanými jako **const** ani  **volatile**.

### <a name="initialization-of-external-variables"></a>Inicializace externích proměnných

Deklarace automatické, statických a externích proměnných mohou obsahovat inicializátory. Deklarace externích proměnných však mohou obsahovat inicializátory, pouze v případě, že proměnné nejsou deklarovány jako **extern**.