---
title: basic_ios – třída
ms.date: 11/04/2016
f1_keywords:
- ios/std::basic_ios
- ios/std::basic_ios::char_type
- ios/std::basic_ios::int_type
- ios/std::basic_ios::off_type
- ios/std::basic_ios::pos_type
- ios/std::basic_ios::traits_type
- ios/std::basic_ios::bad
- ios/std::basic_ios::clear
- ios/std::basic_ios::copyfmt
- ios/std::basic_ios::eof
- ios/std::basic_ios::exceptions
- ios/std::basic_ios::fail
- ios/std::basic_ios::fill
- ios/std::basic_ios::good
- ios/std::basic_ios::imbue
- ios/std::basic_ios::init
- ios/std::basic_ios::move
- ios/std::basic_ios::narrow
- ios/std::basic_ios::rdbuf
- ios/std::basic_ios::rdstate
- ios/std::basic_ios::set_rdbuf
- ios/std::basic_ios::setstate
- ios/std::basic_ios::swap
- ios/std::basic_ios::tie
- ios/std::basic_ios::widen
- ios/std::basic_ios::explicit operator bool
helpviewer_keywords:
- std::basic_ios [C++]
- std::basic_ios [C++], char_type
- std::basic_ios [C++], int_type
- std::basic_ios [C++], off_type
- std::basic_ios [C++], pos_type
- std::basic_ios [C++], traits_type
- std::basic_ios [C++], bad
- std::basic_ios [C++], clear
- std::basic_ios [C++], copyfmt
- std::basic_ios [C++], eof
- std::basic_ios [C++], exceptions
- std::basic_ios [C++], fail
- std::basic_ios [C++], fill
- std::basic_ios [C++], good
- std::basic_ios [C++], imbue
- std::basic_ios [C++], init
- std::basic_ios [C++], move
- std::basic_ios [C++], narrow
- std::basic_ios [C++], rdbuf
- std::basic_ios [C++], rdstate
- std::basic_ios [C++], set_rdbuf
- std::basic_ios [C++], setstate
- std::basic_ios [C++], swap
- std::basic_ios [C++], tie
- std::basic_ios [C++], widen
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
ms.openlocfilehash: 9787775acec6ffeb8eaeaad96af6e152d8cb1bac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537225"
---
# <a name="basicios-class"></a>basic_ios – třída

Třída šablony popisuje funkce úložiště a člena, které jsou společné pro oba vstupní datové proudy (třídy šablony [basic_istream](../standard-library/basic-istream-class.md)) tak za výstupní datové proudy (třídy šablony [basic_ostream –](../standard-library/basic-ostream-class.md)), který závisí na Parametry šablony. (Třída [ios_base –](../standard-library/ios-base-class.md) popisuje, co je běžné a není závislá na parametry šablony.) Objekt třídy **basic_ios –\<třídy Elem, třída vlastností >** pomáhá řídit datový proud s prvky typu `Elem`, jehož vlastnosti znaků určuje třídu `Traits`.

## <a name="syntax"></a>Syntaxe

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Typ.

*Osobnostní rysy*<br/>
Proměnné typu `char_traits`.

## <a name="remarks"></a>Poznámky

Objekt třídy **basic_ios –\<třídy Elem, třída vlastností >** ukládá:

- Tie ukazatel na objekt typu [basic_istream](../standard-library/basic-istream-class.md)**\<Elem, osobnostní rysy >**.

- Datový proud vyrovnávací paměti ukazatel na objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, osobnostní rysy >**.

- [Informace o formátování](../standard-library/ios-base-class.md).

- [Informace o stavu Stream](../standard-library/ios-base-class.md) v základní objekt typu [ios_base –](../standard-library/ios-base-class.md).

- Výplň znak v objektu typu `char_type`.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ios –](#basic_ios)|Vytvoří `basic_ios` třídy.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Synonymum pro parametr šablony `Elem`.|
|[int_type](#int_type)|Synonymum pro `Traits::int_type`.|
|[off_type](#off_type)|Synonymum pro `Traits::off_type`.|
|[pos_type](#pos_type)|Synonymum pro `Traits::pos_type`.|
|[traits_type](#traits_type)|Synonymum pro parametr šablony `Traits`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Špatné](#bad)|Označuje ztrátu integrity vyrovnávací paměť datového proudu.|
|[Vymazat](#clear)|Vymaže všechny příznaky chyby.|
|[copyfmt –](#copyfmt)|Kopíruje příznaky z jednoho datového proudu do jiného.|
|[eof](#eof)|Označuje, pokud bylo dosaženo konce datového proudu.|
|[Výjimky](#exceptions)|Určuje, které výjimky budou vyvolány metodou datového proudu.|
|[Selhání](#fail)|Indikuje selhání platné pole extrahovat z datového proudu.|
|[Výplň](#fill)|Určuje nebo vrátí znak, který se použije, když text není stejně široká jako datový proud.|
|[Dobré](#good)|Označuje, že datový proud je v dobrém stavu.|
|[imbue –](#imbue)|Změní národní prostředí.|
|[init](#init)|Volané `basic_ios` konstruktory.|
|[Přesunutí](#move)|Přesune všechny hodnoty, s výjimkou ukazatelů do vyrovnávací paměti datového proudu z parametru do aktuálního objektu.|
|[Upřesněte](#narrow)|Najde odpovídající znak danou `char_type`.|
|[rdbuf](#rdbuf)|Datový proud trasy do zadané vyrovnávací paměti.|
|[rdstate –](#rdstate)|Přečte stav bity příznaky.|
|[set_rdbuf](#set_rdbuf)|Vyrovnávací paměť datového proudu do vyrovnávací paměti pro čtení pro tento objekt stream se přiřadí.|
|[setstate](#setstate)|Nastaví další příznaky.|
|[Prohození](#swap)|Vymění hodnoty v tomto `basic_ios` objektu pro ty z jiného `basic_ios` objektu. Ukazatele na vyrovnávací paměť datového proudu se prohodit.|
|[Tie](#tie)|Zajišťuje, že tento jeden datový proud se zpracovává před jiného datového proudu.|
|[widen](#widen)|Najde odpovídající `char_type` na daný znak.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[explicitní operátor bool](#op_bool)|Umožňuje používat `basic_ios` objektu jako **bool**. Aby se běžných, nežádoucí vedlejší účinky je zakázané automatického převodu typu.|
|[operátor void *](#op_void_star)|Určuje, zda datový proud je pořád dobré.|
|[operátor!](#op_not)|Označuje, pokud datový proud není chybný.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<ios >

**Namespace:** std

## <a name="bad"></a>  basic_ios::bad

Označuje ztrátu integrity vyrovnávací paměť datového proudu

```cpp
bool bad() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `rdstate & badbit` je nenulové; v opačném případě **false**.

Další informace o `badbit`, naleznete v tématu [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Příklad

```cpp
// basic_ios_bad.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.bad( );
    cout << boolalpha;
    cout << b << endl;

    b = cout.good( );
    cout << b << endl;
}
```

## <a name="basic_ios"></a>  basic_ios::basic_ios

Basic_ios – třída vytvoří.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>Parametry

*sb*<br/>
Standardní vyrovnávací paměti k uložení vstupních nebo výstupních elementy.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje její členské objekty voláním [init](#init)(_ *Sb*). Druhý konstruktor (chráněný) opustí její členské objekty inicializovat. Pozdější volání `init` musí inicializovat objekt předtím, než může být bezpečně zničen.

## <a name="char_type"></a>  basic_ios::char_type

Synonymum pro parametr šablony `Elem`.

```cpp
typedef Elem char_type;
```

## <a name="clear"></a>  basic_ios::clear

Vymaže všechny příznaky chyby.

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
(Volitelné) Příznaky, které chcete nastavit po vymazání všech příznaků. Výchozí hodnota je `goodbit`.

*reraise*<br/>
(Volitelné) Určuje, zda má být výjimka znovu vyvolána. Výchozí hodnota je **false** (nebude znovu vyvolat výjimku).

### <a name="remarks"></a>Poznámky

Příznaky jsou `goodbit`, `failbit`, `eofbit`, a `badbit`. Test pro tyto příznaky se [dobré](#good), [chybný](#bad), [eof](#eof), a [selhání](#fail)

Členská funkce se nahradí informace o stavu uložené datového proudu s:

`state` &#124;`(` [rdbuf –](#rdbuf) ! = 0 **goodbit** : **badbit**)

Pokud `state` **&** [výjimky](#exceptions) je nenulovou hodnotu, pak vyvolá objekt třídy [selhání](../standard-library/ios-base-class.md#failure).

### <a name="example"></a>Příklad

Zobrazit [rdstate –](#rdstate) a [getline](../standard-library/string-functions.md#getline) příklady použití `clear`.

## <a name="copyfmt"></a>  basic_ios::copyfmt

Kopíruje příznaky z jednoho datového proudu do jiného.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Datový proud, jehož příznaky, které chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

**To** objektu pro datový proud, do které se kopírují příznaky.

### <a name="remarks"></a>Poznámky

Členská funkce sestavy událostí zpětného volání **vymazat\_události**. Potom zkopíruje z *správné* do  **\*to** výplňovým znakem, tie ukazatele a informace o formátování. Před změnou masku výjimky, oznámí události zpětného volání `copyfmt_event`. Pokud po dokončení kopírování **stav &**[výjimky](#exceptions) je nenulovou hodnotu, funkce efektivně volá [vymazat](#clear) s argumentem [rdstate –](#rdstate). Vrátí  **\*to**.

### <a name="example"></a>Příklad

```cpp
// basic_ios_copyfmt.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream x( "test.txt" );
    int i = 10;

    x << showpos;
    cout << i << endl;
    cout.copyfmt( x );
    cout << i << endl;
}

```

## <a name="eof"></a>  basic_ios::EOF

Označuje, pokud bylo dosaženo konce datového proudu.

```cpp
bool eof() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud bylo dosaženo konce datového proudu, **false** jinak.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí **true** Pokud [rdstate –](#rdstate) `& eofbit` nenulové. Další informace o `eofbit`, naleznete v tématu [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Příklad

```cpp
// basic_ios_eof.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

int main( int argc, char* argv[] )
{
    fstream   fs;
    int n = 1;
    fs.open( "basic_ios_eof.txt" );   // an empty file
    cout << boolalpha
    cout << fs.eof() << endl;
    fs >> n;   // Read the char in the file
    cout << fs.eof() << endl;
}
```

## <a name="exceptions"></a>  basic_ios::Exceptions

Určuje, které výjimky budou vyvolány metodou datového proudu.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>Parametry

*Newexcept*<br/>
Příznaky, které chcete vrátit výjimku.

### <a name="return-value"></a>Návratová hodnota

Příznaky, které jsou aktuálně zadaný na výjimku pro datový proud.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí masku výjimky uložené. Druhá funkce úložišť člen *_Except* masku výjimky a vrátí jeho předchozí uloženou hodnotu. Všimněte si, že ukládání nového masku výjimky může vyvolat výjimku, stejně jako volání [vymazat](#clear)( [rdstate –](#rdstate) ).

### <a name="example"></a>Příklad

```cpp
// basic_ios_exceptions.cpp
// compile with: /EHsc /GR
#include <iostream>

int main( )
{
    using namespace std;

    cout << cout.exceptions( ) << endl;
    cout.exceptions( ios::eofbit );
    cout << cout.exceptions( ) << endl;
    try
    {
        cout.clear( ios::eofbit );   // Force eofbit on
    }
    catch ( exception &e )
    {
        cout.clear( );
        cout << "Caught the exception." << endl;
        cout << "Exception class: " << typeid(e).name()  << endl;
        cout << "Exception description: " << e.what() << endl;
    }
}
```

```Output
0
1
Caught the exception.
Exception class: class std::ios_base::failure
Exception description: ios_base::eofbit set
```

## <a name="fail"></a>  basic_ios::Fail

Indikuje selhání platné pole extrahovat z datového proudu.

```cpp
bool fail() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud [rdstate –](#rdstate) `& (badbit|failbit)` je nenulová, v opačném případě **false**.

Další informace o `failbit`, naleznete v tématu [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Příklad

```cpp
// basic_ios_fail.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.fail( );
    cout << boolalpha;
    cout << b << endl;
}

```

## <a name="fill"></a>  basic_ios::Fill

Určuje nebo vrátí znak, který se použije, když text není stejně široká jako datový proud.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>Parametry

*Char*<br/>
Znak, který chcete, aby jako výplňovým znakem.

### <a name="return-value"></a>Návratová hodnota

Aktuální znak výplně.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí znak uložené výplně. Druhá funkce úložišť člen *Char* výplňovým znakem a vrátí jeho předchozí uloženou hodnotu.

### <a name="example"></a>Příklad

```cpp
// basic_ios_fill.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( )
{
    using namespace std;

    cout << setw( 5 ) << 'a' << endl;
    cout.fill( 'x' );
    cout << setw( 5 ) << 'a' << endl;
    cout << cout.fill( ) << endl;
}
```

```Output
a
xxxxa
x
```

## <a name="good"></a>  basic_ios::Good

Označuje, že datový proud je v dobrém stavu.

```cpp
bool good() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud [rdstate –](#rdstate) `== goodbit` (žádné příznaky stavu jsou nastavené), v opačném případě **false**.

Další informace o `goodbit`, naleznete v tématu [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Příklad

Zobrazit [basic_ios::bad](#bad) pro příklad použití `good`.

## <a name="imbue"></a>  basic_ios::imbue

Změní národní prostředí.

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Umístění*<br/>
Řetězec národního prostředí.

### <a name="return-value"></a>Návratová hodnota

Předchozí národní prostředí.

### <a name="remarks"></a>Poznámky

Pokud [rdbuf –](#rdbuf) je volání funkce není ukazatel s hodnotou null, člena

`rdbuf`-> [pubimbue –](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)

V každém případě vrátí [ios_base::imbue](../standard-library/ios-base-class.md#imbue)(_ *Loc*).

### <a name="example"></a>Příklad

```cpp
// basic_ios_imbue.cpp
// compile with: /EHsc
#include <iostream>
#include <locale>

int main( )
{
    using namespace std;

    cout.imbue( locale( "french_france" ) );
    double x = 1234567.123456;
    cout << x << endl;
}
```

## <a name="init"></a>  basic_ios::init

Je voláno basic_ios – konstruktory.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>Parametry

*_Sb*<br/>
Standardní vyrovnávací paměti k uložení vstupních nebo výstupních elementy.

*_Isstd*<br/>
Určuje, zda se jedná o standardní datový proud.

### <a name="remarks"></a>Poznámky

Členská funkce ukládá hodnoty všechny členské objekty tak, aby:

- [rdbuf –](#rdbuf) vrátí *_Sb.*

- [Tie](#tie) vrátí ukazatel s hodnotou null.

- [rdstate –](#rdstate) vrátí [goodbit](../standard-library/ios-base-class.md#iostate) Pokud *_Sb* je nenulové; v opačném případě vrátí [badbit](../standard-library/ios-base-class.md#iostate).

- [výjimky](#exceptions) vrátí `goodbit`.

- [příznaky](../standard-library/ios-base-class.md#flags) vrátí [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags).

- [Šířka](../standard-library/ios-base-class.md#width) vrátí hodnotu 0.

- [přesnost](../standard-library/ios-base-class.md#precision) vrátí 6.

- [Výplň](#fill) vrátí znak mezery.

- [getloc –](../standard-library/ios-base-class.md#getloc) vrátí `locale::classic`.

- [iword –](../standard-library/ios-base-class.md#iword) hodnotu nula, a [pword –](../standard-library/ios-base-class.md#pword) vrátí ukazatel s hodnotou null pro všechny hodnoty argumentů.

## <a name="int_type"></a>  basic_ios::int_type

Synonymum pro `traits_type::int_type`.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="move"></a>  basic_ios::Move

Přesune všechny hodnoty, s výjimkou ukazatelů do vyrovnávací paměti datového proudu z parametru do aktuálního objektu.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
`ios_base` Objektu přesunout hodnoty z.

### <a name="remarks"></a>Poznámky

Chráněný člen funkce přesune všechny hodnoty uložené v *správné* k `*this` s výjimkou uloženou `stream buffer pointer`, což je beze změny v *správné* a nastavte na ukazatel s hodnotou null v `*this`. Uložený `tie pointer` je nastavena na ukazatel s hodnotou null v *správné*.

## <a name="narrow"></a>  basic_ios::Narrow

Najde odpovídající znak danou `char_type`.

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>Parametry

*Char*<br/>
**Char** pro převod.

*Default*<br/>
**Char** , že se mají vracet Pokud se nenajde žádný ekvivalent.

### <a name="return-value"></a>Návratová hodnota

Ekvivalent **char** do danou `char_type`.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [use_facet](../standard-library/basic-filebuf-class.md#open)\<ctype\<E >> ( [getloc –](../standard-library/ios-base-class.md#getloc)()).`narrow` ( `Char`, `Default`).

### <a name="example"></a>Příklad

```cpp
// basic_ios_narrow.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    wchar_t *x = L"test";
    char y[10];
    cout << x[0] << endl;
    wcout << x << endl;
    y[0] = wcout.narrow( x[0] );
    cout << y[0] << endl;
}
```

## <a name="off_type"></a>  basic_ios::off_type

Synonymum pro `traits_type::off_type`.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_void_star"></a>  basic_ios::Operator void *

Určuje, zda datový proud je pořád dobré.

```cpp
operator void *() const;
```

### <a name="return-value"></a>Návratová hodnota

Operátor vrátí ukazatel s hodnotou null pouze v případě [selhání](#fail).

### <a name="example"></a>Příklad

```cpp
// basic_ios_opgood.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << (bool)(&cout != 0) << endl;   // Stream is still good
}
```

```Output
1
```

## <a name="op_not"></a>  basic_ios::Operator!

Označuje, pokud datový proud není chybný.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí [selhání](#fail).

### <a name="example"></a>Příklad

```cpp
// basic_ios_opbad.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << !cout << endl;   // Stream is not bad
}
```

```Output
0
```

## <a name="op_bool"></a>  basic_ios::Operator bool

Umožňuje používat `basic_ios` objektu jako **bool**. Aby se běžných, nežádoucí vedlejší účinky je zakázané automatického převodu typu.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Poznámky

Operátor vrací lze převést na typ hodnota **false** pouze tehdy, pokud `fail()`. Návratový typ je lze převést pouze na **bool**, nikoli k `void *` nebo jiný skalární typ a známé.

## <a name="pos_type"></a>  basic_ios::pos_type

Synonymum pro `traits_type::pos_type`.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="rdbuf"></a>  basic_ios::rdbuf

Datový proud trasy do zadané vyrovnávací paměti.

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>Parametry

*_Sb*<br/>
Datový proud.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí ukazatel uložené datový proud vyrovnávací paměti.

Druhá funkce úložišť člen *_Sb* v ukazateli uložené datový proud vyrovnávací paměti a vrátí dříve uloženou hodnotu.

### <a name="example"></a>Příklad

```cpp
// basic_ios_rdbuf.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream file( "rdbuf.txt" );
    streambuf *x = cout.rdbuf( file.rdbuf( ) );
    cout << "test" << endl;   // Goes to file
    cout.rdbuf(x);
    cout << "test2" << endl;
}
```

```Output
test2
```

## <a name="rdstate"></a>  basic_ios::rdstate

Přečte stav bity příznaky.

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>Návratová hodnota

Informace o stavu uložené datového proudu.

### <a name="example"></a>Příklad

```cpp
// basic_ios_rdstate.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>
using namespace std;

void TestFlags( ios& x )
{
    cout << ( x.rdstate( ) & ios::badbit ) << endl;
    cout << ( x.rdstate( ) & ios::failbit ) << endl;
    cout << ( x.rdstate( ) & ios::eofbit ) << endl;
    cout << endl;
}

int main( )
{
    fstream x( "c:\test.txt", ios::out );
    x.clear( );
    TestFlags( x );
    x.clear( ios::badbit | ios::failbit | ios::eofbit );
    TestFlags( x );
}
```

```Output
0
0
0

4
2
1
```

## <a name="setstate"></a>  basic_ios::setstate

Nastaví další příznaky.

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>Parametry

*_Stavu*<br/>
Nastavení další příznaky.

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [vymazat](#clear)(_ *stavu* &#124; [rdstate –](#rdstate)).

### <a name="example"></a>Příklad

```cpp
// basic_ios_setstate.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
using namespace std;

int main( )
{
    bool b = cout.bad( );
    cout << b << endl;   // Good
    cout.clear( ios::badbit );
    b = cout.bad( );
    // cout.clear( );
    cout << b << endl;   // Is bad, good
    b = cout.fail( );
    cout << b << endl;   // Not failed
    cout.setstate( ios::failbit );
    b = cout.fail( );
    cout.clear( );
    cout << b << endl;   // Is failed, good
    return 0;
}
```

```Output
0
1
```

## <a name="set_rdbuf"></a>  basic_ios::set_rdbuf

Vyrovnávací paměť datového proudu do vyrovnávací paměti pro čtení pro tento objekt stream se přiřadí.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>Parametry

*strbuf*<br/>
Vyrovnávací paměť datového proudu k vyrovnávací paměti pro čtení.

### <a name="remarks"></a>Poznámky

Funkce úložiště chráněný člen *strbuf* v `stream buffer pointer`. Nevolá `clear`.

## <a name="tie"></a>  basic_ios::Tie

Zajišťuje, že tento jeden datový proud se zpracovává před jiného datového proudu.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Datový proud.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí ukazatel uložené rovnosti. Druhá funkce úložišť člen *str* tie ukazatele a vrátí jeho předchozí uloženou hodnotu.

### <a name="remarks"></a>Poznámky

`tie` způsobí, že dva proudy se dá provést synchronizace, se tak, že operace na jednoho datového proudu vyskytnout po dokončení operací na jiný datový proud.

### <a name="example"></a>Příklad

V tomto příkladu pomocí propojí cin cout, je zaručeno, "Zadejte číslo:" řetězec přejdou do konzoly před číslo samotné se extrahují z cin. Tím se eliminuje možnost, která "Zadejte číslo:" řetězec stále nachází ve vyrovnávací paměti při čtení číslo, tak, že jsme si jisti, že uživatel má ve skutečnosti některé řádku na. Ve výchozím nastavení jsou svázány cin a cout.

```cpp
#include <ios>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    cin.tie( &cout );
    cout << "Enter a number:";
    cin >> i;
}
```

## <a name="traits_type"></a>  basic_ios::traits_type

Synonymum pro parametr šablony `Traits`.

```cpp
typedef Traits traits_type;
```

## <a name="widen"></a>  basic_ios::widen

Najde odpovídající `char_type` do danou **char**.

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>Parametry

*Char*<br/>
Znak pro převod.

### <a name="return-value"></a>Návratová hodnota

Najde odpovídající `char_type` do danou **char**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **E**>> ( [getloc –](../standard-library/ios-base-class.md#getloc)). `widen`( `Char`).

### <a name="example"></a>Příklad

```cpp
// basic_ios_widen.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    char *z = "Hello";
    wchar_t y[2] = {0,0};
    cout << z[0] << endl;
    y[0] = wcout.widen( z[0] );
    wcout << &y[0] << endl;
}

```

## <a name="swap"></a>  basic_ios::swap

Vymění hodnoty v tomto `basic_ios` objektu pro ty z jiného `basic_ios` objektu. Však nejsou prohodily ukazatelů do vyrovnávací paměti datového proudu.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
`basic_ios` Objekt, který se používá k výměně hodnot.

### <a name="remarks"></a>Poznámky

Chráněný člen funkce vymění všechny hodnoty uložené v *správné* s `*this` s výjimkou uloženou `stream buffer pointer`.

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
