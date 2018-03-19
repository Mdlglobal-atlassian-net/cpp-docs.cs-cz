---
title: "Přetížení funkcí | Microsoft Docs"
ms.custom: 
ms.date: 1/25/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d21ecfb649748c9bf7e190d4857ce93ebee61dd1
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="function-overloading"></a>Přetížení funkcí
Jazyk C++ umožňuje zadat více než jednu funkci stejného názvu ve stejném oboru. Toto nastavení se nazývá *přetížený* funkce. Přetížené funkce umožňují zadat jiný sémantiku pro funkci, v závislosti na typy a počet argumentů. 
  
 Například **tisku** funkce, která přebírá **std::string** argument může provádět velmi jiné úlohy než ten, který používá argument typu **dvojité**. Přetížení ušetří můžete s pomocí názvů, jako například `print_string` nebo `print_double`. Při kompilaci kompilátor zvolí, které přetížení pro použití na základě typu argumentů předaná volající funkcí.  Když zavoláte **print(42.0)** potom **void tisk (dvojité d)** funkce bude volána. Když zavoláte **tisku ("hello world")** potom **void print(std::string)** přetížení bude volána.

Můžete použít přetížení členských funkcí a třetí funkce. Následující tabulka ukazuje, které části deklarace funkce používá jazyk C++ k rozlišení skupin funkcí stejného názvu ve stejném oboru.  
  
### <a name="overloading-considerations"></a>Okolnosti přetížení  
  
|Prvek deklarace funkce|Použito pro přetížení?|  
|----------------------------------|---------------------------|  
|Návratový typ funkce|Ne|  
|Počet argumentů|Ano|  
|Typ argumentů|Ano|  
|Přítomnost nebo absence tří teček|Ano|  
|Použití názvů `typedef`|Ne|  
|Nespecifikované hranice pole|Ne|  
|**Const** nebo `volatile`|Ano, při použití celý – funkce|
|[ref-qualifier](#ref-qualifier)|Ano|  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje, jak lze přetížení použít.  
  
```  
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
 Přetížené funkce jsou vybrány pro nejlepší shodu deklarace funkce v aktuálním oboru pro zadané argumenty ve volání funkce. Pokud se nenajde vhodný funkce, že funkce je volána. V tomto kontextu "vhodný" znamená jednu z těchto možností:  
  
-   Byla nalezena přesná shoda.  
  
-   Byla provedena triviálního převodu.  
  
-   Integrální povýšení byla provedena.  
  
-   Standardní převod na typ požadovaný argument existuje.  
  
-   Uživatelem definované převod (operátor převodu nebo konstruktor) na požadovaný argument typu existuje.  
  
-   Argumenty reprezentována třemi tečkami nebyly nalezeny.  
  
 Kompilátor vytvoří sadu candidate funkce pro každý argument. Candidate funkce jsou funkce, ve kterých skutečné argument na této pozici můžete převést na typ formální argumentu.  
  
 Sadu "nejlépe odpovídající funkce" se vytváří pro každý argument a vybrané funkce je průnik všech sad. Pokud průnik obsahuje více než jednu funkci, přetížení je nejednoznačný a vygeneruje se chyba. Funkce, která je vybrána nakonec je vždy lepší shodu než každá další funkce, které jsou ve skupině alespoň jeden argument. Pokud to tak není (Pokud není žádná zrušte Vítěz), volání funkce generuje chybu.  
  
 Vezměte v úvahu následující deklarace (funkce jsou označeny `Variant 1`, `Variant 2`, a `Variant 3`, pro identifikaci v následující diskusi):  
  
```  
Fraction &Add( Fraction &f, long l );       // Variant 1  
Fraction &Add( long l, Fraction &f );       // Variant 2  
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3  
  
Fraction F1, F2;  
```  
  
 Vezměte v úvahu následující příkaz:  
  
```  
F1 = Add( F2, 23 );  
```  
  
 Předchozí příkaz vytvoří dvě sady:  
  
|Sada 1: Candidate funkce, které mají první Argument typu zlomek|Sada 2: Candidate funkce jejichž druhý Argument lze převést na typ int|  
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Variant 1|Variant 1 (`int` lze převést na `long` pomocí standardní převod)|  
|Variant 3||  
  
 Funkce v nastavení 2 jsou funkce, pro které jsou implicitní převod z typu skutečný parametr typ formálního parametru a mezi takové funkce je funkce, pro kterou je "náklady" převod skutečný parametr typu pro typ formálního parametru nejmenší.  
  
 Průnik tyto dvě sady je Variant 1. Je například volání funkce nejednoznačný:  
  
```  
F1 = Add( 3, 6 );  
```  
  
 Předchozí volání funkce sestavení následující sady:  
  
|Sada 1: Candidate funkce, mít první Argument služby typ int|Sada 2: Candidate funkce, mít druhý Argument služby typ int|  
|---------------------------------------------------------------------|----------------------------------------------------------------------|  
|Variant 2 (`int` lze převést na `long` pomocí standardní převod)|Variant 1 (`int` lze převést na `long` pomocí standardní převod)|  
  
 Všimněte si, že nastaví průnik mezi tyto dva je prázdný. Proto kompilátor generuje chybovou zprávu.  
  
 Argument funkce s porovnávání *n* výchozí argumentů je považován za *n*funkce samostatné + 1, každý s různým počtem argumentů.  
  
 Jednání třemi tečkami (...) jako zástupný znak; odpovídá některý skutečné argument. To může vést k mnoha nejednoznačný sad, pokud není návrh vaší sady přetížené funkce s mimořádně pečlivě.  
  
> [!NOTE]
>  Nejednoznačnosti přetížených funkcí nelze určit, dokud je došlo k volání funkce. V tomto bodě sady jsou vytvořeny pro každý argument ve volání funkce, a můžete určit, zda existuje jednoznačným přetížení. To znamená, že nejednoznačnosti může zůstat ve vašem kódu, dokud jsou evoked voláním konkrétní funkce.  
  
## <a name="argument-type-differences"></a>Rozdíly typu argumentů  
 Přetížené funkce rozlišují mezi typy argumentů přijímajícími různé inicializátory. Proto argument daného typu a reference na tento typ jsou pro účely přetížení považovány za totéž. Za shodné jsou považovány, protože přijímají stejné inicializátory. Například zápis `max( double, double )` je považován za shodný se zápisem `max( double &, double & )`. Deklarace dvou takových funkcí způsobí chybu.  
  
 Ze stejného důvodu, funkce argumenty typu upraveném **const** nebo `volatile` nejsou považovány jinak než základní typ pro účely přetížení.  
  
 Však můžete funkci přetížení mechanismus rozlišovat odkazy, které jsou kvalifikovaný **const** a `volatile` a odkazy na základní typ. To umožňuje psaní například následujícího kódu:  
  
```  
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
  
```  
Over default constructor  
Over&  
Over default constructor  
const Over&  
Over default constructor  
volatile Over&  
```  
  
 Ukazatelé na **const** a `volatile` objekty jsou také považovány za liší od ukazatele na základní typ pro účely přetížení.  
  
## <a name="argument-matching-and-conversions"></a>Porovnávání a převody argumentů  
 Když kompilátor pokusí o odpovídat skutečné argumenty proti argumenty v deklaracích funkce, ho můžete zadat standardní nebo uživatelem definované převody k získání správného typu, pokud se nenašla žádná shoda. Aplikace převody podléhá tato pravidla:  
  
-   Nejsou považovány za pořadí převody, které obsahují více než jeden převod definovaný uživatelem.  
  
-   Pořadí přepočty, které lze zkrátit odebráním zprostředkující převody nejsou považovány za.  
  
 Výsledné pořadí převody, pokud existuje, se nazývá nejlépe odpovídající pořadí. Existuje několik způsobů, jak převést objekt typu `int` na typ `unsigned long` pomocí standardní převody (popsané v [standardní převody](../cpp/standard-conversions.md)):  
  
-   Převést z `int` k `long` a potom z `long` k `unsigned long`.  
  
-   Převést z `int` k `unsigned long`.  
  
 První pořadí, i když dosahuje požadované cílem není nejvhodnější pořadí – kratší pořadí existuje.  
  
 V následující tabulce jsou uvedeny skupinu převody, názvem trivial převody, které mají omezený účinek na při zjišťování, které pořadí je nejlepší shody. Instance, ve kterých trivial převody ovlivnit volbu pořadí jsou popsané v seznamu následující tabulky.  
  
### <a name="trivial-conversions"></a>Trivial převody  
  
|Převod z typu|Převést na typ|  
|-----------------------|---------------------|  
|*type-name*|*Název typu* **&**|  
|*Název typu* **&**|*type-name*|  
|*Název typu* **]**|*type-name\***|  
|*Název typu* **(** *seznam argumentů* **)**|**(**  *\*název typu* **) (** *seznam argumentů* **)**|  
|*type-name*|**Const** *název typu*|  
|*type-name*|`volatile` *Název typu*|  
|*type-name\***|**Const** *název typu\***|  
|*type-name\***|`volatile` *Název typu\**|  
  
 Pořadí, ve které jsou aplikovány převody vypadá takto:  
  
1.  Přesná shoda. Přesnou shodu mezi typy, pomocí kterých je tato funkce volána a typy deklarované v prototyp funkce je vždy nejlepší shodu. Pořadí trivial převody jsou klasifikovány jako přesné shody. Ale pořadí, ve které žádný z těchto převody neprovádějte jsou považovány za lepší, než pořadí, které převést:  
  
    -   Z ukazatel na ukazatel na **const** (`type`  **\***  k **const** `type`  **\***  ).  
  
    -   Z ukazatel na ukazatel na `volatile` (`type`  **\***  k `volatile` `type`  **\*** ).  
  
    -   Z odkazů na odkaz na **const** (`type`  **&**  k **const** `type`  **&** ).  
  
    -   Z odkazů na odkaz na `volatile` (`type`  **&**  k `volatile` `type`  **&** ).  
  
2.  Porovnávat pomocí reklamními nabídkami. Žádné pořadí není klasifikovaný přesnou shodu, která obsahuje jenom zvýšení úrovně celého čísla, převody z **float** k **dvojité**, a trivial převody je klasifikován jako odpovídající pomocí reklamními nabídkami. I když jako dobrý shodu jako jakékoli přesná shoda, je lepší, než odpovídající pomocí standardní převody odpovídající pomocí reklamními nabídkami.  
  
3.  Porovnávat pomocí standardní převody. Žádné pořadí není klasifikovaný přesně nebo shoda pomocí reklamní akce, který obsahuje pouze standardní převody a trivial převody je klasifikován tak odpovídající pomocí standardní převody. V rámci této kategorie se používají následující pravidla:  
  
    -   Převod z ukazatel na odvozené třídy, za účelem ukazatel na přímý nebo nepřímý základní třída je vhodnější převodu na **void \***  nebo **const void \*** .  
  
    -   Převod z ukazatel na odvozené třídy, za účelem ukazatel na základní třídu vytvoří lepší shodu, že Čím bližší je základní třída přímé základní třídu. Předpokládejme, že je hierarchie tříd, jak je znázorněno na následujícím obrázku.  
  
 ![Upřednostňovaný převody](../cpp/media/vc391t1.gif "vc391T1")  
Graf ilustrující upřednostňované převody  
  
 Převod z typu `D*` na typ `C*` je vhodnější pro převod z typu `D*` na typ `B*`. Podobně, převod z typu `D*` na typ `B*` je vhodnější pro převod z typu `D*` na typ `A*`.  
  
 Toto pravidlo stejné platí pro převody odkazů. Převod z typu `D&` na typ `C&` je vhodnější pro převod z typu `D&` na typ `B&`a tak dále.  
  
 Toto pravidlo stejné platí pro převody ukazatele na člena. Převod z typu `T D::*` na typ `T C::*` je vhodnější pro převod z typu `T D::*` na typ `T B::*`a tak dále (kde `T` je typ člena).  
  
 Předchozí pravidlo se vztahuje pouze podél dané cestě odvození. Vezměte v úvahu graf znázorňuje následující obrázek.  
  
 ![Více&#45;dědičnosti, který ukazuje upřednostňované převody](../cpp/media/vc391t2.gif "vc391T2")  
Vícenásobné dědičnosti grafu ilustrující upřednostňované převody  
  
 Převod z typu `C*` na typ `B*` je vhodnější pro převod z typu `C*` na typ `A*`. Důvodem je, že jsou na stejnou cestu, a `B*` blíže. Ale převod z typu `C*` na typ `D*` není vhodnější převod na typ `A*`; neexistuje žádná priorita, protože převody podle různé cesty.  
  
1.  Shodná s uživatelem definované převody. Toto pořadí nelze zařadit jako přesnou shodu, odpovídající pomocí povýšení nebo odpovídající pomocí standardní převody. Pořadí musí obsahovat pouze uživatelem definované převody, standardní převody nebo trivial převody být označeny jako shody s uživatelem definované převody. Porovnání s uživatelem definované převody považuje za lepší shodu než shoda se třemi tečkami ale stejně dobře shody jako shody s standardní převody.  
  
2.  Shodovat se třemi tečkami. Všechny sekvenci, která odpovídá tři tečky v deklaraci je klasifikován jako shoda se třemi tečkami. Je to nejslabších shody.  
  
 Uživatelem definované převody se použijí, pokud neexistuje žádná předdefinované povýšení nebo převod. Tyto převody jsou vybrané na základě typu argumentu se porovnat. Vezměte v úvahu následující kód:  
  
```  
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
  
 K dispozici uživatelem definované převody pro třídu `UDC` jsou z typu `int` a typ **dlouho**. Proto kompilátor zvažuje převody pro typ objektu, který se shodoval: `UDC`. Převod na `int` existuje, a je vybraná.  
  
 Během procesu odpovídajících argumenty můžete použít standardní převody argument a výsledek převodu z uživatelem definované. Proto lze použít následující kód:  
  
```  
void LogToFile( long l );  
...  
UDC udc;  
LogToFile( udc );  
```  
  
 V předchozím příkladu, uživatelem definovaný převod **operátor long**, je vyvolána k převést `udc` na typ **dlouho**. Pokud žádný definovaný uživatelem převod na typ **dlouho** je definován, převod bude pokračovat následujícím způsobem: typ `UDC` by převést na typ `int` pomocí převodu definovaný uživatelem. Potom standardní převod z typu `int` na typ **dlouho** by byly použity tak, aby odpovídaly argumentem v deklaraci.  
  
 Pokud žádné uživatelem definované převody musí odpovídat argument, standardní převody se nepoužívají při vyhodnocování nejlepší shodu. To platí i v případě, že více než jednu funkci kandidáta vyžaduje uživatelem definovaný převod; v takovém případě jsou považovány za shodné funkce. Příklad:  
  
```  
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
  
 Obě verze `Func` vyžadují uživatelem definovaný převod na typ převést `int` pro argument typu třídy. Možné převody jsou:  
  
-   Převod z typu `int` na typ `UDC1` (uživatelem definované převodu z).  
  
-   Převod z typu `int` na typ **dlouho**; potom převést na typ `UDC2` (dvoustupňové převodu).  
  
 I když druhý z nich vyžaduje standardní převod, jakož i převod definovaný uživatelem, dvě převody jsou stále považovány za shodné.  
  
> [!NOTE]
>  Uživatelem definované převody jsou považovány za převod konstrukce nebo převod podle inicializace (funkci pro převod). Obě metody jsou považovány za shodné při zvažování nejlepší shodu.  
  
## <a name="argument-matching-and-the-this-pointer"></a>Porovnávání argumentů a tento ukazatel  
 Členské funkce tříd jsou zpracovávány jinak v závislosti na tom, zda jsou deklarovány jako `static`. Protože mají nestatické funkce implicitní argument, který poskytuje ukazatel `this`, jsou oproti statickým funkcím považovány za funkce mající o jeden argument více. Jinak jsou deklarovány shodně.  
  
 Tyto nestatické členské funkce vyžadují, aby implicitní ukazatel `this` odpovídal typu objektu, ze kterého je funkce volána, nebo v případě přetížených operátorů vyžadují, aby se první argument shodoval s objektem, pro který je operátor použit. (Další informace o přetížené operátory najdete v tématu [přetížený operátory](../cpp/operator-overloading.md).)  
  
 Na rozdíl od ostatních argumentů v přetížených funkcích nejsou při pokusu o nalezení shody s argumentem ukazatele `this` zavedeny žádné dočasné objekty a nedochází k pokusům o převody.  
  
 Když `->` výběru členů operátor slouží k přístupu funkce člena třídy `class_name`, `this` ukazatel argument má typ `class_name * const`. Pokud jsou členy deklarované jako `const` nebo `volatile`, jsou typy `const class_name * const` a `volatile class_name * const`, v uvedeném pořadí.  
  
 Operátor volby členu `.` funguje přesně stejným způsobem s výjimkou, že je před název objektu přidán implicitní operátor `&` (adresa). Následující příklad ukazuje tuto funkci:  
  
```  
// Expression encountered in code  
obj.name  
  
// How the compiler treats it  
(&obj)->name  
```  
  
 Levý operand `->*` a `.*` operátory (ukazatel na člena) jsou zpracovány stejným způsobem jako `.` a `->` operátory (výběru členů) s ohledem na porovnávání argumentů.  

## <a name="ref-qualifiers"></a> REF – kvalifikátory na členské funkce  
REF kvalifikátory umožňují přetížení členské funkce na základě objekt propojená tímto `this` rvalue nebo lvalue.  Tuto funkci lze použít předejdete operace nepotřebné kopírování ve scénářích, kde rozhodnete poskytovat ukazatel přístup k datům. Předpokládejme například, třída **C** některá data v jeho konstruktor inicializuje a vrátí kopii dat – členská funkce **get_data()**. Pokud objekt typu **C** je rvalue, který má být zničený, pak bude vyberte kompilátor **get_data() & &** přetížení, které se přesouvají data než ho zkopírovat. 

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
 Několik omezení řídí přijatelné sadu přetížených funkcí:  
  
-   Jakékoli dvě funkce v sadě přetížených funkcí musí mít jiný argument seznamy.  
  
-   Přetížení funkcí s argumentem seznam stejné typy, podle návratový typ samostatně, je k chybě.  
  
     **Microsoft Specific**  
  
 Můžete použít přetížení **new – operátor** výhradně na základě těchto návratový typ – konkrétně na základě modifikátor modelu paměti zadaná.  
  
**Konkrétní Microsoft END**  
  
-   Členské funkce nemohou být přetíženy na základě jeden se statické a dalších nonstatic.  
  
-   `typedef` deklarace nedefinují nové typy; jejich zavést synonyma pro existující typy. Neovlivňují overloading mechanismus. Vezměte v úvahu následující kód:  
  
    ```  
    typedef char * PSTR;  
  
    void Print( char *szToPrint );  
    void Print( PSTR szToPrint );  
    ```  
  
     Předchozí dvě funkce mít identické argument seznamy. `PSTR` je synonymum pro typ **char \*** . Tento kód v oboru člen, vygeneruje chybu.  
  
-   Výčtové typy jsou odlišné typy a může sloužit k rozlišení mezi přetížených funkcí.  
  
-   Typy "pole" a "ukazatel na" jsou považovány za shodné pro účely rozlišovány přetížených funkcí. To platí pouze pro samostatně rozměry pole. Proto následující přetížených funkcí konfliktu a generovat chybovou zprávu:  
  
    ```  
    void Print( char *szToPrint );  
    void Print( char szToPrint[] );  
    ```  
  
     Pro násobkem rozměry pole druhý a všechny následné dimenze jsou považovány za součást typu. Proto se používají v rozlišování přetížených funkcí:  
  
    ```  
    void Print( char szToPrint[] );  
    void Print( char szToPrint[][7] );  
    void Print( char szToPrint[][9][42] );  
    ```  
  
## <a name="overloading-overriding-and-hiding"></a>Přetížení, přepsání a skrytí
  
 Jakékoli dvě deklarace funkcí se stejným názvem ve stejném oboru mohou odkazovat na stejnou funkci nebo na dvě samostatné funkce, které jsou přetížené. Pokud seznam deklarací argumentu obsahuje argumenty ekvivalentních typů (jak je popsáno v předchozí části), deklarace funkce odkazují na stejnou funkci. V opačném případě odkazují na dvě různé funkce, které jsou vybrány pomocí přetížení.  
  
 Obor třídy je přísně respektován. Proto se funkce deklarovaná v základní třídě nenachází ve stejném oboru jako funkce deklarovaná v odvozené třídě. Pokud je funkce v odvozené třídě deklarovaný se stejným názvem jako virtuální funkce ve funkci odvozené třídy základní třídy *přepsání* funkce základní třídy. Další informace najdete v tématu [virtuální funkce](../cpp/virtual-functions.md).

Pokud funkce základní třída není deklarovaný jako virtuální, pak funkce odvozené třídy říká, že je *skrýt* ho. Přepsání i skrytí se liší od přetížení.  
  
 Obor bloku je přísně respektován. Proto se funkce deklarovaná v rozsahu souboru nenachází ve stejném oboru jako funkce deklarovaná místně. Pokud má funkce deklarovaná místně stejný název jako funkce deklarovaná v rozsahu souboru, funkce deklarovaná místně skryje funkci s rozsahem souboru místo toho, aby způsobila přetížení. Příklad:  
  
```  
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
  
 Předchozí kód zobrazí dvě definice z funkce `func`. Definice, která přebírá argument typu `char *`, je kvůli příkazu `main` pro `extern` místní. Proto je definice, která přebírá argument typu `int`, skrytá a při prvním volání `func` dojde k chybě.  
  
 U přetížených členských funkcí lze různým verzím funkce předat různá přístupová oprávnění. Tyto jsou stále považovány za součást oboru nadřazené třídy, a jsou tedy přetíženými funkcemi. Uvažujme následující kód, ve kterém je členská funkce `Deposit` přetížena. Jedna verze je veřejná, druhá soukromá.  
  
 Záměrem tohoto příkladu je poskytnout třídu `Account`, ve které je požadováno správné heslo pro provedení vkladů. To lze provést pomocí přetížení.  
  
 Všimněte si, že volání `Deposit` v `Account::Deposit` volá funkci soukromého členu. Toto volání je správné, protože `Account::Deposit` je členskou funkcí, a proto má přístup k soukromým členům třídy.  
  
```  
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