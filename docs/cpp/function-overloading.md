---
title: Přetížení funkcí
ms.date: 03/27/2019
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
ms.openlocfilehash: fe390ae190f422f7951f7101a7c08808b1c6a526
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179780"
---
# <a name="function-overloading"></a>Přetížení funkcí

Jazyk C++ umožňuje zadat více než jednu funkci stejného názvu ve stejném oboru. Tyto funkce se nazývají *přetížené* funkce. Přetížené funkce umožňují poskytovat různé sémantiky pro funkci v závislosti na typech a počtu argumentů.

Například funkce `print`, která přebírá `std::string` argument může provádět velmi odlišné úlohy než ta, která přebírá argument typu **Double**. Přetížení šetří, že nemusíte používat názvy, například `print_string` nebo `print_double`. V době kompilace kompilátor zvolí, které přetížení se má použít, na základě typu argumentů předaných volajícím.  Pokud zavoláte `print(42.0)`, bude vyvolána funkce `void print(double d)`. Pokud zavoláte `print("hello world")`, bude vyvoláno přetížení `void print(std::string)`.

Můžete přetížit jak členské funkce, tak i nečlenské funkce. Následující tabulka ukazuje, které části deklarace funkce používá jazyk C++ k rozlišení skupin funkcí stejného názvu ve stejném oboru.

### <a name="overloading-considerations"></a>Okolnosti přetížení

|Prvek deklarace funkce|Použito pro přetížení?|
|----------------------------------|---------------------------|
|Návratový typ funkce|Ne|
|Počet argumentů|Ano|
|Typ argumentů|Ano|
|Přítomnost nebo absence tří teček|Ano|
|Použití názvů **typedef**|Ne|
|Nespecifikované hranice pole|Ne|
|**const** nebo **volatile**|Ano, při použití na celou funkci|
|[Kvalifikátory ref](#ref-qualifiers)|Ano|

## <a name="example"></a>Příklad

Následující příklad znázorňuje, jak lze přetížení použít.

```cpp
// function_overloading.cpp
// compile with: /EHsc
#include <iostream>
#include <math.h>
#include <string>

// Prototype three print functions.
int print(std::string s);             // Print a string.
int print(double dvalue);            // Print a double.
int print(double dvalue, int prec);  // Print a double with a
                                     //  given precision.
using namespace std;
int main(int argc, char *argv[])
{
    const double d = 893094.2987;
    if (argc < 2)
    {
        // These calls to print invoke print( char *s ).
        print("This program requires one argument.");
        print("The argument specifies the number of");
        print("digits precision for the second number");
        print("printed.");
        exit(0);
    }

    // Invoke print( double dvalue ).
    print(d);

    // Invoke print( double dvalue, int prec ).
    print(d, atoi(argv[1]));
}

// Print a string.
int print(string s)
{
    cout << s << endl;
    return cout.good();
}

// Print a double in default precision.
int print(double dvalue)
{
    cout << dvalue << endl;
    return cout.good();
}

//  Print a double in specified precision.
//  Positive numbers for precision indicate how many digits
//  precision after the decimal point to show. Negative
//  numbers for precision indicate where to round the number
//  to the left of the decimal point.
int print(double dvalue, int prec)
{
    // Use table-lookup for rounding/truncation.
    static const double rgPow10[] = {
        10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1,
        10E0, 10E1,  10E2,  10E3,  10E4, 10E5,  10E6 };
    const int iPowZero = 6;

    // If precision out of range, just print the number.
    if (prec < -6 || prec > 7)
    {
        return print(dvalue);
    }
    // Scale, truncate, then rescale.
    dvalue = floor(dvalue / rgPow10[iPowZero - prec]) *
        rgPow10[iPowZero - prec];
    cout << dvalue << endl;
    return cout.good();
}
```

Předchozí kód ukazuje přetížení funkce `print` v oboru souboru.

Výchozí argument není považován za součást typu funkce. Proto se nepoužívá při výběru přetížených funkcí. Dvě funkce, které se liší pouze v jejich výchozích argumentech, jsou považovány za vícenásobné definice spíše než za přetížené funkce.

Pro přetížené operátory nelze zadat výchozí argumenty.

## <a name="argument-matching"></a>Porovnávání argumentů

Přetížené funkce jsou vybrány pro nejlepší shodu deklarací funkcí v aktuálním rozsahu s argumenty dodanými ve volání funkce. Pokud je nalezena vhodná funkce, je volána Tato funkce. "Vhodné" v tomto kontextu znamená:

- Našla se přesná shoda.

- Byl proveden triviální převod.

- Byla provedena celočíselná propagace.

- Existuje standardní převod na požadovaný typ argumentu.

- Uživatelem definovaný převod (buď operátor převodu, nebo konstruktor) na požadovaný typ argumentu existuje.

- Byly nalezeny argumenty reprezentované třemi tečkami.

Kompilátor vytvoří sadu kandidátních funkcí pro každý argument. Kandidátské funkce jsou funkce, ve kterých lze aktuální argument na této pozici převést na typ formálního argumentu.

Sada "nejlépe vyhovující funkce" je sestavena pro každý argument a vybraná funkce je průnik všech sad. Pokud průnik obsahuje více než jednu funkci, přetížení je nejednoznačné a generuje chybu. Funkce, která je nakonec vybraná, je vždy lepší, než každá jiná funkce ve skupině pro alespoň jeden argument. Pokud neexistuje žádný jasný vítěz, volání funkce vygeneruje chybu.

Vezměte v úvahu následující deklarace (funkce jsou označené `Variant 1`, `Variant 2`a `Variant 3`pro identifikaci v následující diskuzi):

```cpp
Fraction &Add( Fraction &f, long l );       // Variant 1
Fraction &Add( long l, Fraction &f );       // Variant 2
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3

Fraction F1, F2;
```

Vezměte v úvahu následující příkaz:

```cpp
F1 = Add( F2, 23 );
```

Předchozí příkaz vytvoří dvě sady:

|Nastavte 1: Kandidátské funkce, které mají první argument typu zlomek|Nastavte 2: Kandidátské funkce, jejichž druhý argument lze převést na typ **int**|
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
|Varianta 1|Varianta 1 (**int** se dá převést na **Long** pomocí standardního převodu)|
|Varianta 3||

Funkce v množině 2 jsou funkce, pro které existují implicitní převody ze skutečného typu parametru na formální typ parametru a mezi těmito funkcemi je funkce, pro kterou je převedená cena za převod skutečného typu parametru na jeho formální typ parametru je nejúspornější.

Průnik těchto dvou sad je variantou 1. Příkladem nejednoznačného volání funkce je:

```cpp
F1 = Add( 3, 6 );
```

Předchozí volání funkce vytvoří následující sady:

|Nastavte 1: Kandidátské funkce, které mají první argument typu **int**|Nastavte 2: Kandidátské funkce, které mají druhý argument typu **int**|
|---------------------------------------------------------------------|----------------------------------------------------------------------|
|Variant 2 (**int** se dá převést na **Long** pomocí standardního převodu)|Varianta 1 (**int** se dá převést na **Long** pomocí standardního převodu)|

Vzhledem k tomu, že průnik těchto dvou sad je prázdný, kompilátor vygeneruje chybovou zprávu.

Pro porovnání argumentů je funkce s *n* výchozími argumenty považována za *n*+ 1 samostatné funkce, každý s jiným počtem argumentů.

Tři tečky (...) fungují jako zástupný znak; odpovídá jakémukoli skutečnému argumentu. Může vést k mnoha nejednoznačným sadám, pokud nenavrhnete vaše přetížené sady funkcí s mimořádnou péčí.

> [!NOTE]
>  Nejednoznačnost přetížených funkcí se nedá určit, dokud nezjistíte volání funkce. V tomto okamžiku jsou sady vytvořeny pro každý argument ve volání funkce a můžete určit, zda existuje jednoznačné přetížení. To znamená, že nejednoznačnosti mohou zůstat ve vašem kódu, dokud nejsou evoked pomocí konkrétního volání funkce.

## <a name="argument-type-differences"></a>Rozdíly typu argumentů

Přetížené funkce rozlišují mezi typy argumentů přijímajícími různé inicializátory. Proto argument daného typu a reference na tento typ jsou pro účely přetížení považovány za totéž. Za shodné jsou považovány, protože přijímají stejné inicializátory. Například zápis `max( double, double )` je považován za shodný se zápisem `max( double &, double & )`. Deklarace dvou takových funkcí způsobí chybu.

Ze stejného důvodu nejsou argumenty funkce typu upraveného pomocí **const** nebo **volatile** pro účely přetížení zpracovány jinak než základní typ.

Mechanismus přetěžování funkcí však může rozlišovat mezi odkazy, které jsou kvalifikovány **const** a **volatile** a odkazy na základní typ. K tomu je možné použít následující kód:

```cpp
// argument_type_differences.cpp
// compile with: /EHsc /W3
// C4521 expected
#include <iostream>

using namespace std;
class Over {
public:
   Over() { cout << "Over default constructor\n"; }
   Over( Over &o ) { cout << "Over&\n"; }
   Over( const Over &co ) { cout << "const Over&\n"; }
   Over( volatile Over &vo ) { cout << "volatile Over&\n"; }
};

int main() {
   Over o1;            // Calls default constructor.
   Over o2( o1 );      // Calls Over( Over& ).
   const Over o3;      // Calls default constructor.
   Over o4( o3 );      // Calls Over( const Over& ).
   volatile Over o5;   // Calls default constructor.
   Over o6( o5 );      // Calls Over( volatile Over& ).
}
```

### <a name="output"></a>Výstup

```Output
Over default constructor
Over&
Over default constructor
const Over&
Over default constructor
volatile Over&
```

Ukazatele na objekty **const** a **volatile** se také považují za odlišné od ukazatelů na základní typ pro účely přetížení.

## <a name="argument-matching-and-conversions"></a>Porovnání argumentů a převody

Když se kompilátor pokusí vyhledat skutečné argumenty proti argumentům v deklaracích funkcí, může zadat standardní nebo uživatelsky definované převody, aby získal správný typ, pokud nelze najít přesnou shodu. Pro aplikaci převodů se vztahují tato pravidla:

- Sekvence převodů, které obsahují více než jeden uživatelsky definovaný převod, se nepovažují za.

- Sekvence převodů, které lze zkrátit odebráním mezilehlého převodu, se nepovažují za.

Výsledná sekvence převodů (pokud existuje) se označuje jako nejvhodnější sekvence. Existuje několik způsobů, jak převést objekt typu **int** na typ **unsigned long** pomocí standardních převodů (popsaných v tématu [standardní převody](../cpp/standard-conversions.md)):

- Převeďte z **int** na **Long** a pak z **Long** na **unsigned long**.

- Převod z typu **int** na **unsigned long**.

První sekvence, i když dosahuje požadovaného cíle, není nejlepší odpovídající sekvence – existuje kratší sekvence.

Následující tabulka ukazuje skupinu převodů označované jako triviální převody, které mají omezený vliv na určení, která sekvence je nejlepší shodě. Instance, ve kterých jsou možnosti triviálních převodů ovlivněny volbou sekvence, jsou popsány v seznamu následujícím v tabulce.

### <a name="trivial-conversions"></a>Triviální převody

|Převést z typu|Převést na typ|
|-----------------------|---------------------|
|*název typu*|*název typu* **&**|
|*název typu* **&**|*název typu*|
|*název typu* **[]**|*název typu* __\*__|
|*název typu* **(** *argument-seznam* **)**|**(** __\*__ *název typu* **) (** *seznam argumentů* **)**|
|*název typu*|typ **const** *– název*|
|*název typu*|typ **volatile** *– název*|
|*název typu* __\*__|typ **const** *– název* __\*__|
|*název typu* __\*__|typ **volatile** *– název* __\*__|

Pořadí, ve kterém se zkouší převody, je následující:

1. Přesná shoda. Přesná shoda mezi typy, se kterými je funkce volána, a typy deklarované v prototypu funkce jsou vždy nejlepší shody. Sekvence triviálních převodů jsou klasifikovány jako přesné shody. Nicméně sekvence, které nevytvářejí žádný z těchto převodů, jsou považovány za lepší než sekvence, které převádějí:

   - Z ukazatele na ukazatel na **const** (`type` <strong>\*</strong> na **const** `type` <strong>\*</strong>).

   - Z ukazatele na ukazatel na **volatile** (`type` <strong>\*</strong> na **volatili** `type` <strong>\*</strong>).

   - Z odkazu na odkaz na **const** (`type` **&** na **const** `type` **&** ).

   - Z reference na odkaz na **volatili** (`type` **&** na **volatili** `type` **&** ).

1. Porovnávání pomocí propagačních akcí. Jakákoli sekvence není klasifikována jako přesná shoda, která obsahuje pouze integrální propagační akce, převody z **typu float** na hodnotu **Double**a triviální převody jsou klasifikovány jako shoda pomocí propagačních akcí. I když není stejně vyhovující porovnávání jako jakákoli přesná shoda, porovnávání pomocí propagačních akcí je lepší než porovnávání pomocí standardních převodů.

1. Porovnávání pomocí standardních převodů. Jakákoli sekvence, která není klasifikována jako přesná shoda, nebo jako shoda pomocí propagačních akcí, které obsahují pouze standardní převody a triviální převody, jsou klasifikovány jako shoda pomocí standardních převodů. V rámci této kategorie platí následující pravidla:

   - Převod z ukazatele na odvozenou třídu, na ukazatel na přímou nebo nepřímou základní třídu, je vhodnější pro převod na `void *` nebo `const void *`.

   - Převod z ukazatele na odvozenou třídu, na ukazatel na základní třídu, vytvoří lepší shodu s bližším základem základní třídy je přímá základní třída. Předpokládejme, že hierarchie třídy je znázorněna na následujícím obrázku.

![Graf upřednostňovaných převodů](../cpp/media/vc391t1.gif "Graf upřednostňovaných převodů") <br/>
Graf znázorňující preferované převody

Převod typu `D*` na typ `C*` je vhodnější pro převod z typu `D*` na typ `B*`. Podobně převod typu `D*` na typ `B*` je vhodnější pro převod z typu `D*` na typ `A*`.

Toto pravidlo se vztahuje na převody odkazů. Převod typu `D&` na typ `C&` je vhodnější pro převod z typu `D&` na typ `B&`a tak dále.

Toto pravidlo se vztahuje na převody ukazatele na člena. Převod typu `T D::*` na typ `T C::*` je vhodnější pro převod z typu `T D::*` na typ `T B::*`a tak dále (kde `T` je typ členu).

Předchozí pravidlo se vztahuje pouze na danou cestu odvození. Vezměte v úvahu graf uvedený na následujícím obrázku.

![Vícenásobná&#45;dědičnost, která zobrazuje preferované převody](../cpp/media/vc391t2.gif "Vícenásobná&#45;dědičnost, která zobrazuje preferované převody") <br/>
Graf vícenásobné dědičnosti, který zobrazuje preferované převody

Převod typu `C*` na typ `B*` je vhodnější pro převod z typu `C*` na typ `A*`. Důvodem je, že jsou na stejné cestě a `B*` je blíž. Převod typu `C*` na typ `D*` však není vhodnější pro převod na typ `A*`; k dispozici není žádná preference, protože převody následují jiné cesty.

1. Porovnává s uživatelem definovanými převody. Tato sekvence nemůže být klasifikována jako přesná shoda, porovnávání pomocí propagačních akcí, nebo porovnávání pomocí standardních převodů. Sekvence musí obsahovat pouze uživatelsky definované převody, standardní převody nebo triviální převody, které mají být klasifikovány jako shoda s uživatelem definovanými převody. Porovnávání s uživatelsky definovanými převody se považuje za lepší shodu než shoda se třemi tečkami, ale ne jako vyhovující porovnávání se standardními převody.

1. Porovnává se třemi tečkami. Libovolná sekvence, která odpovídá třem teček v deklaraci, je klasifikována jako shoda se třemi tečkami. Je považována za slabou shodu.

Uživatelem definované převody jsou aplikovány, pokud neexistuje žádná předdefinovaná propagace nebo převod. Tyto převody jsou vybrány na základě typu argumentu, který odpovídá. Vezměte v úvahu následující kód:

```cpp
// argument_matching1.cpp
class UDC
{
public:
   operator int()
   {
      return 0;
   }
   operator long();
};

void Print( int i )
{
};

UDC udc;

int main()
{
   Print( udc );
}
```

Dostupné uživatelsky definované převody pro třídu `UDC` jsou typu **int** a typu **Long**. Proto kompilátor považuje převody pro typ objektu, který odpovídá: `UDC`. Existuje převod na **int** a je vybrán.

Během procesu porovnání argumentů lze standardní převody použít jak pro argument, tak pro výsledek uživatelsky definovaného převodu. Proto následující kód funguje:

```cpp
void LogToFile( long l );
...
UDC udc;
LogToFile( udc );
```

V předchozím příkladu je vyvolán uživatelem definovaný převod **operátor Long**, který převede `udc` na typ **Long**. Pokud nebyl definován uživatelsky definovaný převod na typ **Long** , převod by byl pokračovat následujícím způsobem: Typ `UDC` by byl převeden na typ **int** pomocí uživatelsky definovaného převodu. Pak bude standardní převod z typu **int** na typ **Long** použit tak, aby odpovídal argumentu v deklaraci.

Pokud jsou vyžadovány uživatelsky definované převody, které odpovídají argumentu, nejsou standardní převody použity při vyhodnocování nejlepší shody. I v případě, že více než jedna kandidátská funkce vyžaduje uživatelem definovaný převod, jsou funkce považovány za stejné. Příklad:

```cpp
// argument_matching2.cpp
// C2668 expected
class UDC1
{
public:
   UDC1( int );  // User-defined conversion from int.
};

class UDC2
{
public:
   UDC2( long ); // User-defined conversion from long.
};

void Func( UDC1 );
void Func( UDC2 );

int main()
{
   Func( 1 );
}
```

Obě verze `Func` vyžadují uživatelem definovaný převod na převod typu **int** na argument typu třídy. Možné převody:

- Převést typ **int** na typ `UDC1` (uživatelem definovaný převod).

- Převést typ **int** na typ **Long**; pak proveďte převod na typ `UDC2` (převod na dva kroky).

I když druhá z nich vyžaduje standardní převod i uživatelsky definovaný převod, jsou tyto dva převody stále považovány za stejné.

> [!NOTE]
>  Uživatelsky definované převody se považují za převod pomocí konstrukce nebo převodu inicializací (funkce pro převod). Obě metody jsou považovány za stejné při zvažování nejlepší shody.

## <a name="argument-matching-and-the-this-pointer"></a>Shoda argumentů a ukazatel this

Členské funkce třídy jsou zpracovány odlišně v závislosti na tom, zda jsou deklarovány jako **statické**. Vzhledem k tomu, že nestatické funkce mají implicitní argument, který poskytuje **Tento** ukazatel, nestatické funkce jsou považovány za jeden argument než statické funkce; v opačném případě jsou deklarovány stejným způsobem.

Tyto nestatické členské funkce vyžadují, aby **Tento** ukazatel odpovídal typu objektu, pomocí kterého je funkce volána, nebo pro přetížené operátory vyžadují, aby se první argument shodoval s objektem, ve kterém je operátor použit. (Další informace o přetížených operátorech naleznete v tématu [přetížené operátory](../cpp/operator-overloading.md).)

Na rozdíl od jiných argumentů v přetížených funkcích nejsou zavedeny žádné dočasné objekty a při pokusu o shodu s **tímto** argumentem ukazatele se nezkouší žádné převody.

Když je pro přístup k členské funkci třídy `class_name`použit operátor výběru členů `->`, má **Tento** argument ukazatele typ `class_name * const`. Pokud jsou členy deklarovány jako **const** nebo **volatile**, typy jsou `const class_name * const` a `volatile class_name * const`, v uvedeném pořadí.

Operátor volby členu `.` funguje přesně stejným způsobem s výjimkou, že je před název objektu přidán implicitní operátor `&` (adresa). Následující příklad ukazuje tuto funkci:

```cpp
// Expression encountered in code
obj.name

// How the compiler treats it
(&obj)->name
```

Levý operand operátorů `->*` a `.*` (ukazatel na člen) se zpracovává stejným způsobem jako operátory `.` a `->` (člen výběru členů) s ohledem na shodu argumentů.

## <a name="ref-qualifiers-on-member-functions"></a><a name="ref-qualifiers"></a>Kvalifikátory ref pro členské funkce

Kvalifikátory ref umožňují přetížit členskou funkci na základě toho, zda objekt, na který odkazuje **, je rvalue** nebo lvalue.  Tato funkce se dá použít k tomu, aby nedocházelo k zbytečným operacím kopírování ve scénářích, kdy se rozhodnete neposkytovat přístup k datům pomocí ukazatele. Předpokládejme například, že třída `C` inicializuje některá data v konstruktoru a vrátí kopii těchto dat v rámci členské funkce `get_data()`. Pokud je objekt typu `C` rvalue, který má být zničen, pak kompilátor zvolí `get_data() &&` přetížení, které přesune data namísto kopírování.

```cpp
#include <iostream>
#include <vector>

using namespace std;

class C
{

public:
    C() {/*expensive initialization*/}
    vector<unsigned> get_data() &
    {
        cout << "lvalue\n";
        return _data;
    }
    vector<unsigned> get_data() &&
    {
        cout << "rvalue\n";
        return std::move(_data);
    }

private:
    vector<unsigned> _data;
};

int main()
{
    C c;
    auto v = c.get_data(); // get a copy. prints "lvalue".
    auto v2 = C().get_data(); // get the original. prints "rvalue"
    return 0;
}
```

## <a name="restrictions-on-overloading"></a>Omezení při přetížení

Několik omezení řídí přijatelnou sadu přetížených funkcí:

- Všechny dvě funkce v sadě přetížených funkcí musí mít různé seznamy argumentů.

- Přetížení funkcí se seznamy argumentů stejného typu, na základě samotného návratového typu, je chyba.

     **Specifické pro společnost Microsoft**

Můžete přetížit **operátor New** výhradně na základě návratového typu – konkrétně na základě určeného modifikátoru paměťového modelu.

**Specifické pro konec Microsoftu**

- Členské funkce nemohou být přetíženy pouze na základě statické a jiné nestatické.

- deklarace **typedef** nedefinují nové typy; představují synonyma pro existující typy. Neovlivňují mechanismus přetížení. Vezměte v úvahu následující kód:

    ```cpp
    typedef char * PSTR;

    void Print( char *szToPrint );
    void Print( PSTR szToPrint );
    ```

   Předchozí dvě funkce mají stejné seznamy argumentů. `PSTR` je synonymum pro typ `char *`. V oboru člena tento kód vygeneruje chybu.

- Výčtové typy jsou odlišné typy a lze je použít k rozlišení mezi přetíženými funkcemi.

- Typy "pole typu" a "ukazatel na" jsou považovány za identické pro účely rozlišování mezi přetíženými funkcemi, ale pouze pro pole s dimenzemi v jednom poli. To je důvod, proč tyto přetížené funkce kolidují a generují chybovou zprávu:

    ```cpp
    void Print( char *szToPrint );
    void Print( char szToPrint[] );
    ```

   Pro násobení polí dimenzí se sekunda a všechny následující dimenze považují za součást typu. Proto se používají při odlišení mezi přetíženými funkcemi:

    ```cpp
    void Print( char szToPrint[] );
    void Print( char szToPrint[][7] );
    void Print( char szToPrint[][9][42] );
    ```

## <a name="overloading-overriding-and-hiding"></a>Přetížení, přepsání a skrytí

Jakékoli dvě deklarace funkcí se stejným názvem ve stejném oboru mohou odkazovat na stejnou funkci nebo na dvě samostatné funkce, které jsou přetížené. Pokud seznam deklarací argumentu obsahuje argumenty ekvivalentních typů (jak je popsáno v předchozí části), deklarace funkce odkazují na stejnou funkci. V opačném případě odkazují na dvě různé funkce, které jsou vybrány pomocí přetížení.

Obor třídy je striktně pozorován; Proto funkce deklarovaná v základní třídě není ve stejném oboru jako funkce deklarovaná v odvozené třídě. Je-li funkce v odvozené třídě deklarována se stejným názvem jako virtuální funkce v základní třídě, *přepíše* funkce odvozené třídy funkci základní třídy. Další informace najdete v tématu [virtuální funkce](../cpp/virtual-functions.md).

Pokud není funkce základní třídy deklarována jako ' Virtual ', pak funkce odvozené třídy je pro její *skrytí* uvedena. Přepisování i skrývání se liší od přetížení.

Rozsah bloku je striktně pozorován; Proto funkce deklarovaná v rozsahu souboru není ve stejném oboru jako funkce deklarovaná místně. Pokud má funkce deklarovaná místně stejný název jako funkce deklarovaná v rozsahu souboru, funkce deklarovaná místně skryje funkci s rozsahem souboru místo toho, aby způsobila přetížení. Příklad:

```cpp
// declaration_matching1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void func( int i )
{
    cout << "Called file-scoped func : " << i << endl;
}

void func( char *sz )
{
   cout << "Called locally declared func : " << sz << endl;
}

int main()
{
   // Declare func local to main.
   extern void func( char *sz );

   func( 3 );   // C2664 Error. func( int ) is hidden.
   func( "s" );
}
```

Předchozí kód zobrazí dvě definice z funkce `func`. Definice, která přebírá argument typu `char *`, je místní pro `main` v důsledku příkazu **extern** . Proto je definice, která přebírá argument typu **int** , skrytá a první volání `func` je chyba.

U přetížených členských funkcí lze různým verzím funkce předat různá přístupová oprávnění. Tyto jsou stále považovány za součást oboru nadřazené třídy, a jsou tedy přetíženými funkcemi. Uvažujme následující kód, ve kterém je členská funkce `Deposit` přetížena. Jedna verze je veřejná, druhá soukromá.

Záměrem tohoto příkladu je poskytnout třídu `Account`, ve které je požadováno správné heslo pro provedení vkladů. Provádí se pomocí přetížení.

Volání `Deposit` v `Account::Deposit` volá soukromou členskou funkci. Toto volání je správné, protože `Account::Deposit` je členskou funkcí a má přístup k soukromým členům třídy.

```cpp
// declaration_matching2.cpp
class Account
{
public:
   Account()
   {
   }
   double Deposit( double dAmount, char *szPassword );

private:
   double Deposit( double dAmount )
   {
      return 0.0;
   }
   int Validate( char *szPassword )
   {
      return 0;
   }

};

int main()
{
    // Allocate a new object of type Account.
    Account *pAcct = new Account;

    // Deposit $57.22. Error: calls a private function.
    // pAcct->Deposit( 57.22 );

    // Deposit $57.22 and supply a password. OK: calls a
    //  public function.
    pAcct->Deposit( 52.77, "pswd" );
}

double Account::Deposit( double dAmount, char *szPassword )
{
   if ( Validate( szPassword ) )
      return Deposit( dAmount );
   else
      return 0.0;
}
```

## <a name="see-also"></a>Viz také:

[Funkce (C++)](../cpp/functions-cpp.md)
