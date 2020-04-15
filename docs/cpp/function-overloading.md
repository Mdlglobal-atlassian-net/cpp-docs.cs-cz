---
title: Přetížení funkcí
ms.date: 03/27/2019
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
ms.openlocfilehash: a59c0e27a4500cb20ef42e9a55b4eb0004e07f65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368913"
---
# <a name="function-overloading"></a>Přetížení funkcí

Jazyk C++ umožňuje zadat více než jednu funkci stejného názvu ve stejném oboru. Tyto funkce se nazývají *přetížené* funkce. Přetížené funkce umožňují zadat různé sémantiky pro funkci, v závislosti na typech a počtu argumentů.

Například `print` funkce, která `std::string` přebírá argument může provádět velmi odlišné úkoly než ten, který má argument typu **double**. Přetížení ušetří nutnosti používat názvy `print_string` jako `print_double`nebo . V době kompilace kompilátor zvolí přetížení použít na základě typu argumentů předaných volajícím.  Pokud zavoláte `print(42.0)`, `void print(double d)` bude funkce vyvolána. Pokud zavoláte `print("hello world")`, `void print(std::string)` bude vyvoláno přetížení.

Můžete přetížení jak členské funkce a nečlenské funkce. Následující tabulka ukazuje, které části deklarace funkce používá jazyk C++ k rozlišení skupin funkcí stejného názvu ve stejném oboru.

### <a name="overloading-considerations"></a>Okolnosti přetížení

|Prvek deklarace funkce|Použito pro přetížení?|
|----------------------------------|---------------------------|
|Návratový typ funkce|Ne|
|Počet argumentů|Ano|
|Typ argumentů|Ano|
|Přítomnost nebo absence tří teček|Ano|
|Použití názvů **typedef**|Ne|
|Nespecifikované hranice pole|Ne|
|**const** nebo **těkavé**|Ano, při aplikaci na celou funkci|
|[Ref-kvalifikátory](#ref-qualifiers)|Ano|

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

Výchozí argument není považován za součást typu funkce. Proto se nepoužívá při výběru přetížené funkce. Dvě funkce, které se liší pouze v jejich výchozích argumentech, jsou považovány za vícenásobné definice spíše než za přetížené funkce.

Výchozí argumenty nelze poskytnout pro přetížené operátory.

## <a name="argument-matching"></a>Porovnávání argumentů

Přetížené funkce jsou vybrány pro nejlepší shodu deklarací funkce v aktuálním oboru s argumenty zadanými ve volání funkce. Pokud je nalezena vhodná funkce, je tato funkce volána. "Vhodné" v této souvislosti znamená buď:

- Byla nalezena přesná shoda.

- Byl proveden triviální převod.

- Byla provedena integrální propagace.

- Existuje standardní převod na požadovaný typ argumentu.

- Existuje uživatelem definovaný převod (operátor převodu nebo konstruktor) na požadovaný typ argumentu.

- Byly nalezeny argumenty reprezentované třemi tečkami.

Kompilátor vytvoří sadu kandidátských funkcí pro každý argument. Kandidátní funkce jsou funkce, ve kterých lze skutečný argument v této pozici převést na typ formálního argumentu.

Pro každý argument je vytvořena sada "nejlepších odpovídajících funkcí" a vybraná funkce je průsečík všech sad. Pokud průsečík obsahuje více než jednu funkci, přetížení je nejednoznačné a generuje chybu. Funkce, která je nakonec vybrána, je vždy lepší shoda než všechny ostatní funkce ve skupině pro alespoň jeden argument. Pokud neexistuje žádný jasný vítěz, volání funkce generuje chybu.

Zvažte následující prohlášení (funkce `Variant 1`jsou `Variant 2`označeny , a `Variant 3`, pro identifikaci v následující diskusi):

```cpp
Fraction &Add( Fraction &f, long l );       // Variant 1
Fraction &Add( long l, Fraction &f );       // Variant 2
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3

Fraction F1, F2;
```

Zamyslete se nad tímto tvrzením:

```cpp
F1 = Add( F2, 23 );
```

Předchozí příkaz vytvoří dvě sady:

|Sada 1: Kandidátské funkce, které mají první argument zlomku typu|Sada 2: Kandidátské funkce, jejichž druhý argument lze převést na typ **int**|
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
|Varianta 1|Varianta 1 (**int** lze převést na **dlouhou** pomocí standardního převodu)|
|Varianta 3||

Funkce v sadě 2 jsou funkce, pro které existují implicitní převody ze skutečného typu parametru na formální typ parametru a mezi těmito funkcemi je funkce, pro kterou je "cena" převodu skutečného typu parametru na jeho formální typ parametru nejmenší.

Průsečík těchto dvou sad je Varianta 1. Příkladem nejednoznačného volání funkce je:

```cpp
F1 = Add( 3, 6 );
```

Předchozí volání funkce vytvoří následující sady:

|Sada 1: Kandidátské funkce, které mají první argument typu **int**|Sada 2: Kandidátské funkce, které mají druhý argument typu **int**|
|---------------------------------------------------------------------|----------------------------------------------------------------------|
|Varianta 2 (**int** lze převést na **dlouhou** pomocí standardního převodu)|Varianta 1 (**int** lze převést na **dlouhou** pomocí standardního převodu)|

Vzhledem k tomu, že průsečík těchto dvou sad je prázdný, kompilátor vygeneruje chybovou zprávu.

Pro porovnávání argumentů je funkce s *n* výchozí argumenty považována za samostatné funkce *n*+1, z nichž každá má jiný počet argumentů.

Tři tečky (...) slouží jako zástupný znak; odpovídá jakémukoli skutečnému argumentu. To může vést k mnoha nejednoznačným mase, pokud nenavrhujete přetížené sady funkcí s extrémní péčí.

> [!NOTE]
> Nejednoznačnost přetížených funkcí nelze určit, dokud není zjištěno volání funkce. V tomto okamžiku sady jsou vytvořeny pro každý argument ve volání funkce a můžete určit, zda existuje jednoznačné přetížení. To znamená, že nejasnosti mohou zůstat ve vašem kódu, dokud nejsou vyvolány voláním určité funkce.

## <a name="argument-type-differences"></a>Rozdíly typu argumentů

Přetížené funkce rozlišují mezi typy argumentů přijímajícími různé inicializátory. Proto argument daného typu a reference na tento typ jsou pro účely přetížení považovány za totéž. Za shodné jsou považovány, protože přijímají stejné inicializátory. Například zápis `max( double, double )` je považován za shodný se zápisem `max( double &, double & )`. Deklarace dvou takových funkcí způsobí chybu.

Ze stejného důvodu argumenty funkce typu upravené **const** nebo **volatile** nejsou pro účely přetížení zpracovány jinak než základní typ.

Mechanismus přetížení funkce však může rozlišovat mezi odkazy, které jsou kvalifikovány **const** a **volatile** a odkazy na základní typ. Umožňuje kód, jako je následující možné:

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

Ukazatele na **const** a **volatile** objekty jsou také považovány za odlišné od ukazatelů na základní typ pro účely přetížení.

## <a name="argument-matching-and-conversions"></a>Párování argumentů a převody

Když kompilátor pokusí porovnat skutečné argumenty proti argumenty v deklaracích funkce, může poskytnout standardní nebo uživatelem definované převody získat správný typ, pokud nelze nalézt přesnou shodu. Použití převodů podléhá těmto pravidlům:

- Sekvence převody, které obsahují více než jeden převod definovaný uživatelem nejsou považovány za.

- Sekvence převody, které lze zkrátit odebráním mezilehlé převody nejsou považovány.

Výsledná posloupnost převodů, pokud existuje, se nazývá nejlepší odpovídající sekvence. Existuje několik způsobů, jak převést objekt typu **int** na typ **nepodepsané dlouhé** pomocí standardní převody (popsané v [standardní převody](../cpp/standard-conversions.md)):

- Převést z **int** na **dlouhé** a potom z **dlouhé** na **nepodepsané dlouhé**.

- Převést z **int** na **nepodepsané dlouhé**.

První sekvence, i když dosáhne požadovaného cíle, není nejlepší odpovídající sekvence – kratší sekvence existuje.

V následující tabulce je uvedena skupina převodů, nazývaných triviální převody, které mají omezený vliv na určení, která sekvence je nejlepší odpovídající. Instance, ve kterých triviální převody ovlivňují výběr sekvence jsou popsány v seznamu za tabulkou.

### <a name="trivial-conversions"></a>Triviální převody

|Převést z textu|Převést na text|
|-----------------------|---------------------|
|*název typu*|*název typu***&**|
|*název typu***&**|*název typu*|
|*název typu* **[ ]**|*název typu*__\*__|
|*název typu* **(** *argument-list* **)**|**(** __\*__ *typ-název* **) (** *argument-list* **)**|
|*název typu*|**const** *typ-name*|
|*název typu*|**nestálý** *název typu*|
|*název typu*__\*__|**const** *typ-name*__\*__|
|*název typu*__\*__|**nestálý** *název typu*__\*__|

Pořadí, ve kterém jsou pokusy o převody je následující:

1. Přesná shoda. Přesná shoda mezi typy, se kterými je funkce volána, a typy deklarované v prototypu funkce je vždy nejlepší shoda. Sekvence triviální převody jsou klasifikovány jako přesné shody. Sekvence, které neprovádějí žádné z těchto převodů, jsou však považovány za lepší než sekvence, které převádějí:

   - Od ukazatele k ukazateli`type` <strong>\*</strong> na **const** ( na **const** `type` <strong>\*</strong>).

   - Od ukazatele k ukazateli`type` <strong>\*</strong> na **těkavé** (na **těkavé).** `type` <strong>\*</strong>

   - Z odkazu, na odkaz`type` **&** na **const** ( na **const** `type` **&**).

   - Od odkazu, k odkazu`type` **&** na **těkavé** (na **těkavé** `type` **&**).

1. Zápas pomocí propagačních akcí. Jakákoli sekvence, která není klasifikována jako přesná shoda, která obsahuje pouze integrální propagační akce, převody z **plovoucí** na **dvojité**a triviální převody, je klasifikována jako shoda pomocí propagačních akcí. I když ne tak dobrý zápas jako jakýkoli přesný zápas, shoda pomocí propagačních akcí je lepší než shoda pomocí standardních konverzí.

1. Shoda pomocí standardních konverzí. Každá sekvence, která není klasifikována jako přesná shoda nebo shoda pomocí propagačních akcí, která obsahuje pouze standardní konverze a triviální konverze, je klasifikována jako shoda pomocí standardních konverzí. V rámci této kategorie se používají následující pravidla:

   - Převod z ukazatele na odvozenou třídu na ukazatel na přímou nebo nepřímou `void *` základní `const void *`třídu je vhodnější než převod do nebo .

   - Převod z ukazatele na odvozenou třídu na ukazatel na základní třídu vytváří lepší shodu, čím blíže je základní třída k přímé základní třídě. Předpokládejme, že hierarchie tříd je znázorněna na následujícím obrázku.

![Graf upřednostňovaných konverzí](../cpp/media/vc391t1.gif "Graf upřednostňovaných konverzí") <br/>
Graf zobrazující upřednostňované převody

Převod z `D*` typu `C*` na typ je `D*` vhodnější `B*`než převod z typu na typ . Podobně je převod `D*` z `B*` typu na typ vhodnější `D*` než `A*`převod z typu na typ .

Stejné pravidlo platí pro převody odkazů. Převod z `D&` typu `C&` na typ je `D&` vhodnější `B&`než převod z typu na typ a tak dále.

Stejné pravidlo platí pro převody ukazatele na člen. Převod z `T D::*` typu `T C::*` na typ je `T D::*` vhodnější `T B::*`než převod z `T` typu na typ a tak dále (kde je typ člena).

Předchozí pravidlo platí pouze po dané cestě odvození. Vezměme si graf zobrazený na následujícím obrázku.

![Více násobná dědičnost&#45;, která zobrazuje upřednostňované převody](../cpp/media/vc391t2.gif "Více násobná dědičnost&#45;, která zobrazuje upřednostňované převody") <br/>
Graf s více násobnou dědičností, který zobrazuje upřednostňované převody

Převod z `C*` typu `B*` na typ je `C*` vhodnější `A*`než převod z typu na typ . Důvodem je, že jsou na `B*` stejné cestě, a je blíže. Převod z typu `C*` na `D*` typ však není vhodnější `A*`než převod na typ ; neexistuje žádná preference, protože konverze následují různé cesty.

1. Shodovat s uživatelem definovanými převody. Tuto sekvenci nelze klasifikovat jako přesnou shodu, shodu pomocí propagačních akcí nebo shodu pomocí standardních konverzí. Pořadí musí obsahovat pouze uživatelem definované převody, standardní převody nebo triviální převody, které mají být klasifikovány jako shody s uživatelem definovanými převody. Shoda s uživatelem definovanými konverzemi je považována za lepší shodu než shoda se třemi tečkami, ale není tak dobrá jako shoda se standardními konverzemi.

1. Zápas se třemi tečkami. Každá sekvence, která odpovídá třem tečkám v deklaraci, je klasifikována jako shoda se třemi tečkami. Je to považováno za nejslabší zápas.

Uživatelem definované konverze se použijí, pokud neexistuje žádná předdefinovaná propagace nebo konverze. Tyto převody jsou vybrány na základě typu argumentu, který je spárován. Uvažujte následující kód:

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

Dostupné uživatelem definované převody `UDC` pro třídu jsou z typu **int** a **typu long**. Proto kompilátor považuje převody pro typ objektu, `UDC`který odpovídá: . Převod **na int** existuje a je vybrán.

Během procesu párování argumentů lze standardní převody použít jak na argument, tak na výsledek uživatelem definovaného převodu. Proto funguje následující kód:

```cpp
void LogToFile( long l );
...
UDC udc;
LogToFile( udc );
```

V předchozím příkladu je uživatelem definovaný převod, **operátor**long `udc` , vyvolán k převodu na typ **long**. Pokud by nebyl definován žádný uživatelem definovaný převod na typ **long,** `UDC` převod by probíhal následovně: Typ by byl převeden na type **int** pomocí uživatelem definovaného převodu. Pak standardní převod z typu **int** na typ **long** by byly použity tak, aby odpovídaly argument v deklaraci.

Pokud jsou všechny uživatelem definované převody vyžadovány tak, aby odpovídaly argumentu, standardní převody se nepoužívají při vyhodnocování nejlepší shody. I v případě, že více než jedna funkce kandidáta vyžaduje převod definovaný uživatelem, funkce jsou považovány za rovné. Příklad:

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

Obě verze `Func` vyžadují uživatelem definovaný převod, aby se typ **int** převedl na argument typu třídy. Možné převody jsou:

- Převést z typu `UDC1` **int** na typ (uživatelem definovaný převod).

- Převést z typu **int** na typ **long**; a pak `UDC2` převést na typ (dvoustupňový převod).

I když druhý vyžaduje standardní převod i uživatelem definovaný převod, jsou tyto dva převody stále považovány za rovnocenné.

> [!NOTE]
> Uživatelem definované převody jsou považovány za převod podle konstrukce nebo převodu inicializací (funkce převodu). Obě metody jsou považovány za rovné při zvažování nejlepší shodu.

## <a name="argument-matching-and-the-this-pointer"></a>Porovnávání argumentů a ukazatel this

Funkce členů třídy jsou zpracovány odlišně, v závislosti na tom, zda jsou deklarovány jako **statické**. Protože nestatické funkce mají implicitní argument, který poskytuje **tento** ukazatel, nestatické funkce jsou považovány za jeden další argument než statické funkce; v opačném případě jsou deklarovány stejně.

Tyto nestatické členské funkce vyžadují, aby implicitní **tento** ukazatel odpovídal typu objektu, jehož prostřednictvím je funkce volána, nebo pro přetížené operátory vyžadují, aby první argument odpovídal objektu, na který je operátor aplikován. (Další informace o přetížených operátorech naleznete v [tématu Přetížené operátory](../cpp/operator-overloading.md).)

Na rozdíl od jiných argumentů v přetížených funkcích nejsou zavedeny žádné dočasné objekty a při pokusu o shodu argumentu **tohoto** ukazatele se nepokusí tese tečovat žádné převody.

Pokud `->` je operátor výběru členů použit pro `class_name`přístup k členské funkci třídy , má argument **tento** ukazatel typ `class_name * const`. Pokud jsou členy deklarovány jako **const** nebo **volatile**, typy jsou `const class_name * const` a `volatile class_name * const`, v uvedeném pořadí.

Operátor volby členu `.` funguje přesně stejným způsobem s výjimkou, že je před název objektu přidán implicitní operátor `&` (adresa). Následující příklad ukazuje tuto funkci:

```cpp
// Expression encountered in code
obj.name

// How the compiler treats it
(&obj)->name
```

Levé operand `->*` a `.*` (ukazatel na člen) operátory jsou zpracovány stejným způsobem jako `.` a `->` (výběr členů) operátory s ohledem na porovnání argumentů.

## <a name="ref-qualifiers-on-member-functions"></a><a name="ref-qualifiers"></a>Ref-qualifiers na členské funkce

Ref kvalifikátory umožňují přetížení členské funkce na základě toho, zda objekt, na který se **poukazuje toto** je rvalue nebo lvalue.  Tuto funkci lze použít k zabránění zbytečným operacím kopírování ve scénářích, kde se rozhodnete neposkytnout přístup ukazatele k datům. Například assume `C` class inicializuje některá data ve svém konstruktoru a `get_data()`vrátí kopii těchto dat v členské funkci . Pokud je objekt `C` typu rvalue, který se chystá zničit, pak `get_data() &&` kompilátor zvolí přetížení, který přesune data spíše než zkopírovat.

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

## <a name="restrictions-on-overloading"></a>Omezení přetížení

Přijatelnou sadu přetížených funkcí řídí několik omezení:

- Všechny dvě funkce v sadě přetížených funkcí musí mít různé seznamy argumentů.

- Přetížení funkce se seznamy argumentů stejné typy, založené na návratový typ sám, je chyba.

     **Specifické pro Microsoft**

Můžete přetížení **operátor nové** výhradně na základě návratového typu – konkrétně na základě modifikátoru paměťového modelu zadané.

**END Microsoft Specifické**

- Členské funkce nelze přetížit pouze na základě jednoho statické a ostatní nestatické.

- **deklarace typedef** nedefinují nové typy; zavádějí synonyma pro stávající typy. Neovlivňují mechanismus přetížení. Uvažujte následující kód:

    ```cpp
    typedef char * PSTR;

    void Print( char *szToPrint );
    void Print( PSTR szToPrint );
    ```

   Předchozí dvě funkce mají identické seznamy argumentů. `PSTR`je synonymem `char *`pro typ . V oboru člena tento kód generuje chybu.

- Výčet typy jsou odlišné typy a lze rozlišovat mezi přetížené funkce.

- Typy "pole " a "pointer to" jsou považovány za identické pro účely rozlišení mezi přetížené funkce, ale pouze pro singly dimenzované pole. To je důvod, proč tyto přetížené funkce konfliktu a generovat chybovou zprávu:

    ```cpp
    void Print( char *szToPrint );
    void Print( char szToPrint[] );
    ```

   Pro násobení dimenzovaných polí jsou druhá a všechny následující dimenze považovány za součást typu. Proto se používají při rozlišování mezi přetížené funkce:

    ```cpp
    void Print( char szToPrint[] );
    void Print( char szToPrint[][7] );
    void Print( char szToPrint[][9][42] );
    ```

## <a name="overloading-overriding-and-hiding"></a>Přetížení, přepsání a skrytí

Jakékoli dvě deklarace funkcí se stejným názvem ve stejném oboru mohou odkazovat na stejnou funkci nebo na dvě samostatné funkce, které jsou přetížené. Pokud seznam deklarací argumentu obsahuje argumenty ekvivalentních typů (jak je popsáno v předchozí části), deklarace funkce odkazují na stejnou funkci. V opačném případě odkazují na dvě různé funkce, které jsou vybrány pomocí přetížení.

Rozsah třídy je přísně dodržován; proto funkce deklarovaná v základní třídě není ve stejném oboru jako funkce deklarovaná v odvozené třídě. Pokud je funkce v odvozené třídě deklarována se stejným názvem jako virtuální funkce v základní třídě, funkce odvozené třídy *přepíše* funkci základní třídy. Další informace naleznete v [tématu Virtuální funkce](../cpp/virtual-functions.md).

Pokud funkce základní třídy není deklarována jako "virtuální", pak se říká, že funkce odvozené třídy *ji skryje.* Přepsání i skrytí se liší od přetížení.

Rozsah bloku je přísně dodržován; proto funkce deklarovaná v oboru souboru není ve stejném oboru jako funkce deklarovaná místně. Pokud má funkce deklarovaná místně stejný název jako funkce deklarovaná v rozsahu souboru, funkce deklarovaná místně skryje funkci s rozsahem souboru místo toho, aby způsobila přetížení. Příklad:

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

Předchozí kód zobrazí dvě definice z funkce `func`. Definice, která přebírá argument `char *` typu `main` je místní z důvodu **extern** prohlášení. Proto je skryta definice, která přebírá argument typu **int** a první volání `func` je chybná.

U přetížených členských funkcí lze různým verzím funkce předat různá přístupová oprávnění. Tyto jsou stále považovány za součást oboru nadřazené třídy, a jsou tedy přetíženými funkcemi. Uvažujme následující kód, ve kterém je členská funkce `Deposit` přetížena. Jedna verze je veřejná, druhá soukromá.

Záměrem tohoto příkladu je poskytnout třídu `Account`, ve které je požadováno správné heslo pro provedení vkladů. Provádí se pomocí přetížení.

Volání `Deposit` v `Account::Deposit` volání v volá soukromé členské funkce. Toto volání `Account::Deposit` je správné, protože je členská funkce a má přístup k soukromé členy třídy.

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

## <a name="see-also"></a>Viz také

[Funkce (C++)](../cpp/functions-cpp.md)
