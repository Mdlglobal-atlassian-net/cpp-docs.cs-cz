---
title: Přetížení funkcí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 1/25/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1506870ff0b5bb2aea55874d32f62b1da63c7302
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947535"
---
# <a name="function-overloading"></a>Přetížení funkcí
Jazyk C++ umožňuje zadat více než jednu funkci stejného názvu ve stejném oboru. Toto nastavení se nazývá *přetížené* funkce. Přetížené funkce umožňují poskytnout různé sémantiky funkce, v závislosti na typech a počtu argumentů. 
  
 Například `print` funkci, která přijímá `std::string` argument může provádět velmi odlišný úkol od funkce přijímající argument typu **double**. Přetížení uloží nebudou muset použít názvy například `print_string` nebo `print_double`. V době kompilace kompilátor volí, která přetížení pro použití na základě typu argumentů předaných v volajícím.  Při volání `print(42.0)` pak bude `void print(double d)` funkce se vyvolala. Při volání `print("hello world")` pak bude `void print(std::string)` přetížení, který bude vyvolán.

Přetížit lze členské funkce a nečlenské funkce. Následující tabulka ukazuje, které části deklarace funkce používá jazyk C++ k rozlišení skupin funkcí stejného názvu ve stejném oboru.  
  
### <a name="overloading-considerations"></a>Okolnosti přetížení  
  
|Prvek deklarace funkce|Použito pro přetížení?|  
|----------------------------------|---------------------------|  
|Návratový typ funkce|Ne|  
|Počet argumentů|Ano|  
|Typ argumentů|Ano|  
|Přítomnost nebo absence tří teček|Ano|  
|Použití **typedef** názvy|Ne|  
|Nespecifikované hranice pole|Ne|  
|**Const** nebo **volatile**|Ano, při použití na celou funkci|
|[ref-qualifier](#ref-qualifier)|Ano|  
  
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
  
 Výchozí argument není považován za součást typu funkce. Proto není použit při výběru přetížených funkcí. Dvě funkce, které se liší pouze v jejich výchozích argumentech, jsou považovány za vícenásobné definice spíše než za přetížené funkce.  
  
 Pro přetížené operátory nelze zadat výchozí argumenty.  
  
  
## <a name="argument-matching"></a>Porovnávání argumentů  
 Přetížené funkce jsou vybrány pro nejlepší shodu deklarace funkcí v aktuálním oboru na argumenty zadané ve volání funkce. Pokud se nenajde vhodné funkce, tato funkce je volána. V tomto kontextu "vhodná" znamená jednu z následujících akcí:  
  
-   Byla nalezena přesná shoda.  
  
-   Triviální převod byla provedena.  
  
-   Integrální propagace se provedla.  
  
-   Existuje standardní převod na typ požadovaného argumentu.  
  
-   Existuje uživatelem definovaný převod (operátor conversion nebo konstruktor) na typ požadovaného argumentu.  
  
-   Argumenty, které jsou reprezentovány pomocí tři teček nebyly nalezeny.  
  
 Kompilátor vytvoří sadu Release candidate funkce pro každý argument. Funkce Release Candidate jsou funkce, ve kterých je skutečný argument na této pozici lze převést na typ formálního argumentu.  
  
 Sadu "nejlépe odpovídající funkce" je vytvořená pro každý argument a vybrané funkce je určena průsečíkem všechny sady. Pokud je určena průsečíkem obsahuje více než jednu funkci, přetížení je nejednoznačný a dojde k chybě. Funkce, která je nakonec vybraná vždy je lepší shody než všechny ostatní funkce ve skupině pro alespoň jeden argument. Pokud to není případ (pokud neexistuje žádný jasný Vítěz), volání funkce vygeneruje chybu.  
  
 Vezměte v úvahu následující deklarace (funkce jsou označeny `Variant 1`, `Variant 2`, a `Variant 3`, k identifikaci následující diskuse):  
  
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
  
|Sada 1: Kandidátské funkce, které mají první Argument typu zlomku|Sada 2: Release Candidate funkce jejichž druhý Argument může být převeden na typ int|  
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Varianty 1|Varianty 1 (**int** lze převést na **dlouhé** pomocí standardního převodu)|  
|Varianty 3||  
  
 Funkce v nastavení 2 jsou funkce, pro kterou jsou implicitní převody z typ skutečného parametru na typ formálního parametru a mezi takové funkce je funkce, pro kterou je "cost" konverze typ skutečného parametru na typ formálního parametru nejmenší.  
  
 Je určena průsečíkem těmito dvěma sadami je Variant 1. Je například volání rozhraní nejednoznačnou funkci:  
  
```cpp 
F1 = Add( 3, 6 );  
```  
  
 Předchozí volání funkce vytvoří následující sady:  
  
|Sada 1: Release Candidate funkce, že jste první Argument typu int|Sada 2: Release Candidate funkce, že máte druhý Argument typu int|  
|---------------------------------------------------------------------|----------------------------------------------------------------------|  
|Varianty 2 (**int** lze převést na **dlouhé** pomocí standardního převodu)|Varianty 1 (**int** lze převést na **dlouhé** pomocí standardního převodu)|  
  
 Všimněte si, že je určena průsečíkem mezi těmito dvěma sadami je prázdný. Proto kompilátor vygeneruje chybovou zprávu.  
  
 Pro argument odpovídající funkce s *n* výchozích argumentů je považován za *n*+ 1 samostatné funkce, každý s různým počtem argumentů.  
  
 Tlačítko se třemi tečkami (...) slouží jako zástupný znak; odpovídá jakékoli skutečným argumentem. To může vést k mnoha sadách nejednoznačný, pokud nenavrhujte sady přetížené funkce extreme opatrně.  
  
> [!NOTE]
>  Nejednoznačnosti přetížených funkcí nelze určit, dokud nebude nalezen volání funkce. Od tohoto okamžiku sady jsou vytvořeny pro každý argument ve volání funkce a můžete určit, zda existuje jednoznačný přetížení. To znamená, že nejednoznačnosti může zůstat ve vašem kódu, dokud jsou evoked podle volání určité funkce.  
  
## <a name="argument-type-differences"></a>Rozdíly typu argumentů  
 Přetížené funkce rozlišují mezi typy argumentů přijímajícími různé inicializátory. Proto argument daného typu a reference na tento typ jsou pro účely přetížení považovány za totéž. Za shodné jsou považovány, protože přijímají stejné inicializátory. Například zápis `max( double, double )` je považován za shodný se zápisem `max( double &, double & )`. Deklarace dvou takových funkcí způsobí chybu.  
  
 Ze stejného důvodu argumenty typu upravil funkce **const** nebo **volatile** nejsou pro účely přetížení zpracovány jinak než jejich základní typy.  
  
 Však můžete mechanismus přetěžování funkcí rozlišit mezi referencemi kvalifikovanými **const** a **volatile** a odkazy na základní typy. To umožňuje psaní například následujícího kódu:  
  
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
  
## <a name="argument-matching-and-conversions"></a>Porovnávání a převody argumentů  
 Kompilátor se pokusí tak, aby odpovídala skutečné argumenty s argumenty v deklaracích funkcí, ho můžete zadat standardní nebo uživatelem definované převody na získat správný typ, pokud může být nenašla se přesná shoda. Aplikace převody se vztahují tato pravidla:  
  
-   Nejsou považovány za posloupností převody, které obsahují více než jeden uživatelsky definovaný převod.  
  
-   Pořadí převody, které lze zkrátit tak, že odeberete zprostředkující převodů nepovažují.  
  
 Výsledné pořadí převody, pokud existuje, se nazývá nejvhodnější pořadí. Existuje několik způsobů, jak převést objekt typu **int** na typ **unsigned long** pomocí standardní převody (popsané v [standardní převody](../cpp/standard-conversions.md)):  
  
-   Převod z **int** k **dlouhé** a potom z **dlouhé** k **unsigned long**.  
  
-   Převod z **int** k **unsigned long**.  
  
 První pořadí, i když dosahuje požadovaný cíl není nejvhodnější pořadí – existuje kratší pořadí.  
  
 V následující tabulce jsou uvedeny skupiny převodů, volá triviální převody, které mají omezenou platnost určující, které pořadí je nejlepší shody. Instance, ve kterých triviální převody mít vliv na výběr pořadí jsou popsány v následující tabulce seznamu.  
  
### <a name="trivial-conversions"></a>Triviální převody  
  
|Převod z typu|Převést na typ|  
|-----------------------|---------------------|  
|*Název typu*|*Název typu* **&**|  
|*Název typu* **&**|*Název typu*|  
|*Název typu* **[] č.**|*type-name\***|  
|*Název typu* **(** *seznam argumentů* **)**|**(**  *\*název typu* **) (** *seznam argumentů* **)**|  
|*Název typu*|**Const** *název typu*|  
|*Název typu*|**volatile** *název typu*|  
|*type-name\***|**Const** *název typu\***|  
|*type-name\***|**volatile** *název typu\**|  
  
 Pořadí, ve kterém nedochází k pokusům o převody vypadá takto:  
  
1.  Přesná shoda. Přesná shoda mezi typy, se kterými je volána funkce a typy deklarované v prototypu funkce se vždy nejlepší shodu. Pořadí triviální převody jsou klasifikovány jako přesné shody. Nicméně sekvence, které Nedovolte, aby byly všechny tyto převody jsou považovány za lepší než pořadí, které provádějí převod:  
  
    -   Z ukazatele na ukazatel na **const** (`type` **\*** k **const** `type` **\*** ).  
  
    -   Z ukazatele na ukazatel na **volatile** (`type` **\*** k **volatile** `type` **\***).  
  
    -   Z odkazu, odkaz na **const** (`type` **&** k **const** `type` **&**).  
  
    -   Z odkazu, odkaz na **volatile** (`type` **&** k **volatile** `type` **&**).  
  
2.  Shodovat s využitím propagační akce. Jakékoli sekvenci není jsou klasifikovány jako obsahující pouze celočíselné povýšení, převody z přesnou shodu **float** k **double**, a jednoduchého dotazu převody klasifikovaný jako shoda pomocí propagačních akcí. I když ne dobře shodu jako jakékoli přesná shoda, je lepší než shoda pomocí standardních převodů shoda pomocí propagačních akcí.  
  
3.  Porovná pomocí standardních převodů. Všechny sekvence nejsou klasifikovány jako přesnou shodu nebo shodou pomocí propagačních akcí, která obsahuje jenom standardní převody a převody jednoduchého dotazu je klasifikován tak shoda pomocí standardních převodů. V rámci této kategorie se použijí následující pravidla:  
  
    -   Převod z ukazatele na odvozenou třídu na ukazatel na přímou nebo nepřímou základní třídou je vhodnější pro převod na **void \***  nebo **const void \*** .  
  
    -   Převod z ukazatele na odvozenou třídu na ukazatel na základní třídu vytváří lepší shodu, čím blíž je základní třídou přímou základní třídu. Předpokládejme, že hierarchie tříd je, jak je znázorněno na následujícím obrázku.  
  
 ![Upřednostňovaný převody](../cpp/media/vc391t1.gif "vc391T1")  
Graf ilustrující upřednostňované převody  
  
 Převod z typu `D*` na typ `C*` je vhodnější pro převod z typu `D*` na typ `B*`. Podobně, převod z typu `D*` na typ `B*` je vhodnější pro převod z typu `D*` na typ `A*`.  
  
 Tato stejná pravidla platí pro převody odkazů. Převod z typu `D&` na typ `C&` je vhodnější pro převod z typu `D&` na typ `B&`, a tak dále.  
  
 Tato stejná pravidla platí pro převody ukazatele na člena. Převod z typu `T D::*` na typ `T C::*` je vhodnější pro převod z typu `T D::*` na typ `T B::*`, a tak dále (kde `T` je typ člena).  
  
 Předchozí pravidlo se vztahuje pouze na dané cestě odvození. Vezměte v úvahu graf je znázorněno na následujícím obrázku.  
  
 ![Více&#45;dědičnosti, který zobrazuje upřednostňované převody](../cpp/media/vc391t2.gif "vc391T2")  
Vícenásobné dědičnosti graf ilustrující upřednostňované převody  
  
 Převod z typu `C*` na typ `B*` je vhodnější pro převod z typu `C*` na typ `A*`. Důvodem je, že jsou na stejné cestě a `B*` nejblíže. Ale převod z typu `C*` na typ `D*` není vhodnější pro převod na typ `A*`; není žádná předvolba, protože převody podle různých cest.  
  
1.  Porovná s uživatelem definovaných převodů. Toto pořadí nelze zařadit jako přesná shoda, shoda pomocí propagační akce nebo shodou pomocí standardních převodů. Sekvence musí obsahovat pouze uživatelem definované převody, standardní převody nebo triviální převody na se považoval za shodu s uživatelem definovaných převodů. Shoda s uživatelem definované převody se považuje za lepší shody než shody s třemi tečkami, ale ne dobře shoda jako shoda s standardní převody.  
  
2.  Porovná se třemi tečkami. Všechny sekvence, která odpovídá tři tečky v deklaraci je klasifikován tak shody s třemi tečkami. To je považován za nejslabší shoda.  
  
 Uživatelem definované konverze se použijí, pokud neexistuje žádný převod ani integrovanou podporu. Tyto převody jsou vybrána na základě typu argumentu je nalezena shoda. Vezměte v úvahu následující kód:  
  
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
  
 K dispozici uživatelem definované převody pro třídu `UDC` jsou z typu **int** a typ **dlouhé**. Proto kompilátor považuje převody pro typ objektu je nalezena shoda: `UDC`. Převod na **int** existuje, a že je vybraná.  
  
 Během procesu porovnávání argumentů lze použít standardní převody na argument a výsledkem uživatelsky definovaný převod. Proto následující kód funguje:  
  
```cpp 
void LogToFile( long l );  
...  
UDC udc;  
LogToFile( udc );  
```  
  
 V předchozím příkladu, uživatelem definovaný převod **operátor long**, je vyvolána k převodu `udc` na typ **dlouhé**. Pokud žádný uživatelem definovaný převod na typ **dlouhé** byla definována, převod bude pokračovat následujícím způsobem: typ `UDC` by byl převeden na typ **int** pomocí uživatelem definované převod. Potom standardní převod z typu **int** na typ **dlouhé** by se použily tak, aby odpovídaly argument v deklaraci.  
  
 Pokud jsou všechny uživatelem definované převody vyžadovaný pro shodu argument, nejsou standardní převody použitý při vyhodnocení nejlepší shodu. To platí i v případě, že uživatelsky definovaný převod; vyžaduje více než jednu funkci Release candidate v takovém případě jsou považovány za shodné funkce. Příklad:  
  
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
  
 Obě verze `Func` vyžadují uživatelsky definovaný převod na typ převést **int** na argument typu třídy. Je to možné převody jsou:  
  
-   Převod z typu **int** na typ `UDC1` (uživatelem definovaný převod).  
  
-   Převod z typu **int** na typ **dlouhé**; potom převést na typ `UDC2` (dvoustupňové převod).  
  
 I když druhý z nich vyžaduje standardní převod, stejně jako uživatelem definovaný převod, dva převody jsou stále považovány za shodné.  
  
> [!NOTE]
>  Uživatelem definované převody jsou považovány za převod konstrukce nebo převod pomocí inicializace (funkce pro převod). Obě metody jsou považovány za shodné při zvažování nejlepší shodu.  
  
## <a name="argument-matching-and-the-this-pointer"></a>Porovnávání argumentů a tento ukazatel  
 Členské funkce tříd jsou zpracovávány jinak v závislosti na tom, zda jsou deklarovány jako **statické**. Protože mají nestatické funkce implicitní argument, který poskytuje **to** ukazatel myši, funkce jsou považovány za jeden argument více oproti statickým funkcím; v opačném případě jsou deklarovány shodně.  
  
 Tyto nestatické členské funkce vyžadují, aby implicitní **to** ukazatel odpovídat typu objektu, jejímž prostřednictvím je funkce volána, nebo pro přetížené operátory, vyžadují, že první argument shodoval s objektem, na kterém operátor použit. (Další informace o přetížených operátorech naleznete v tématu [přetížené operátory](../cpp/operator-overloading.md).)  
  
 Na rozdíl od ostatních argumentů v přetížených funkcí jsou zavedeny žádné dočasné objekty a žádné převody nedochází k pokusům o při pokusu o shodu **to** argument typu ukazatel.  
  
 Když `->` operátoru výběru členů se používá pro přístup k členské funkce třídy `class_name`, **to** má argument ukazatele typu `class_name * const`. Pokud členů jsou deklarovány jako **const** nebo **volatile**, jsou tyto typy `const class_name * const` a `volatile class_name * const`v uvedeném pořadí.  
  
 Operátor volby členu `.` funguje přesně stejným způsobem s výjimkou, že je před název objektu přidán implicitní operátor `&` (adresa). Následující příklad ukazuje tuto funkci:  
  
```cpp 
// Expression encountered in code  
obj.name  
  
// How the compiler treats it  
(&obj)->name  
```  
  
 Levý operand `->*` a `.*` operátory (ukazatel na člen) jsou zpracovány stejně jako `.` a `->` operátory (volba členu) s ohledem na odpovídající argument.  

## <a name="ref-qualifiers"></a> Kvalifikátory REF pro členské funkce  
Kvalifikátory REF umožňují přetížit členskou funkci na základě Určuje, zda objekt, na který podle **to** rvalue nebo l-hodnota.  Tato funkce umožňuje vyhnout se zbytečnému kopírování ve scénářích kde rozhodnete poskytnout ukazatel přístup k datům. Předpokládejme například, třída `C` inicializuje některá data ve svých konstruktorech a vrátí kopii těchto dat v členské funkci `get_data()`. Pokud objekt typu `C` je r-hodnota, která se chystá zničeny, a kompilátor zvolí `get_data() &&` přetížení, které se provádí přesun dat, spíše než zkopírovat. 

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
 Několik omezení řízení přijatelné sadu přetížených funkcí:  
  
-   Jakékoli dvě funkce sadu přetížených funkcí musí mít seznamy argumentů s jinou.  
  
-   Přetížení funkce se seznamy argumentů stejné typy založené na návratový typ samostatně, je chybou.  
  
     **Specifické pro Microsoft**  
  
 Můžete použít přetížení **operátor new** výhradně na základě těchto návratový typ – konkrétně na základě modelu paměti modifikátor zadán.  
  
**Specifické pro END Microsoft**  
  
-   Členské funkce nemohou být přetíženy pouze na základě jeden je statická a dalších nestatické.  
  
-   **Definice TypeDef** deklarace nemá definován nové typy; přinášejí synonyma pro existující typy. Neovlivňují mechanismu přetížení. Vezměte v úvahu následující kód:  
  
    ```cpp 
    typedef char * PSTR;  
  
    void Print( char *szToPrint );  
    void Print( PSTR szToPrint );  
    ```  
  
     Předchozí dvě funkce mít seznamy argumentů identické. `PSTR` je synonymum pro typ **char \*** . Tento kód v oboru člena, vygeneruje chybu.  
  
-   Výčtové typy jsou různé typy a slouží k rozlišení mezi přetížených funkcí.  
  
-   Typy "pole" a "ukazatel na" jsou považovány za shodné pro účely rozlišování mezi přetížených funkcí. To platí jenom pro jednotlivě rozměry pole. Proto následující přetížené funkce konflikt a generovat chybovou zprávu:  
  
    ```cpp 
    void Print( char *szToPrint );  
    void Print( char szToPrint[] );  
    ```  
  
     Pro vícenásobně rozměry pole dimenze druhé a všechny následné jsou považovány za součást typu. Proto jsou použity v přetížené funkce rozlišování:  
  
    ```cpp 
    void Print( char szToPrint[] );  
    void Print( char szToPrint[][7] );  
    void Print( char szToPrint[][9][42] );  
    ```  
  
## <a name="overloading-overriding-and-hiding"></a>Přetížení, přepisování a skrývání
  
 Jakékoli dvě deklarace funkcí se stejným názvem ve stejném oboru mohou odkazovat na stejnou funkci nebo na dvě samostatné funkce, které jsou přetížené. Pokud seznam deklarací argumentu obsahuje argumenty ekvivalentních typů (jak je popsáno v předchozí části), deklarace funkce odkazují na stejnou funkci. V opačném případě odkazují na dvě různé funkce, které jsou vybrány pomocí přetížení.  
  
 Obor třídy je přísně respektován. Proto se funkce deklarovaná v základní třídě nenachází ve stejném oboru jako funkce deklarovaná v odvozené třídě. Pokud je funkce v odvozené třídě deklarována se stejným názvem jako virtuální funkce v základní třídě, funkce odvozené třídy *přepíše* funkci základní třídy. Další informace najdete v tématu [virtuální funkce](../cpp/virtual-functions.md).

Pokud není deklarován jako virtuální funkce základní třídy, pak funkce odvozené třídy se říká, že *skrýt* ho. Jak přepisování a skrývání se liší od přetížení.  
  
 Obor bloku je přísně respektován. Proto se funkce deklarovaná v rozsahu souboru nenachází ve stejném oboru jako funkce deklarovaná místně. Pokud má funkce deklarovaná místně stejný název jako funkce deklarovaná v rozsahu souboru, funkce deklarovaná místně skryje funkci s rozsahem souboru místo toho, aby způsobila přetížení. Příklad:  
  
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
  
 Předchozí kód zobrazí dvě definice z funkce `func`. Definice, která přebírá argument typu `char *` je lokální vzhledem k `main` z důvodu **extern** příkazu. Proto je definice, která přebírá argument typu **int** je skrytá a při prvním volání do `func` došlo k chybě.  
  
 U přetížených členských funkcí lze různým verzím funkce předat různá přístupová oprávnění. Tyto jsou stále považovány za součást oboru nadřazené třídy, a jsou tedy přetíženými funkcemi. Uvažujme následující kód, ve kterém je členská funkce `Deposit` přetížena. Jedna verze je veřejná, druhá soukromá.  
  
 Záměrem tohoto příkladu je poskytnout třídu `Account`, ve které je požadováno správné heslo pro provedení vkladů. To lze provést pomocí přetížení.  
  
 Všimněte si, že volání `Deposit` v `Account::Deposit` volá funkci soukromého členu. Toto volání je správné, protože `Account::Deposit` je členskou funkcí, a proto má přístup k soukromým členům třídy.  
  
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