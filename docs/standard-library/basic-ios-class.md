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
ms.openlocfilehash: e2341dcc0f2f03fbfa212d1ea49993016e193638
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460105"
---
# <a name="basicios-class"></a>basic_ios – třída

Třída šablony popisuje funkce úložiště a členů společné pro vstupní datové proudy (ze třídy template [basic_istream](../standard-library/basic-istream-class.md)) a výstupní datové proudy (ze třídy template [basic_ostream](../standard-library/basic-ostream-class.md)), která závisí na parametrech šablony. (Třída [ios_base](../standard-library/ios-base-class.md) popisuje, co je běžné a není závislé na parametrech šablony.) Objekt třídy **basic_ios\<třídy elem, vlastnosti třídy >** pomáhá řídit datový proud pomocí prvků typu `Elem`, jejichž znaky jsou určeny třídou `Traits`.

## <a name="syntax"></a>Syntaxe

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ.

*Traits*\
Proměnná typu `char_traits`.

## <a name="remarks"></a>Poznámky

Objekt třídy **basic_ios\<třídy elem, vlastnosti třídy >** obchody:

- Odkaz na objekt typu [basic_istream](../standard-library/basic-istream-class.md) **\<elem, vlastnosti >** .

- Ukazatel vyrovnávací paměti streamu na objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md) **\<elem, vlastnosti >** .

- [Informace o formátování](../standard-library/ios-base-class.md).

- [Informace o stavu datového proudu](../standard-library/ios-base-class.md) v základním objektu typu [ios_base](../standard-library/ios-base-class.md).

- Znak výplně v objektu typu `char_type`.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ios](#basic_ios)|Sestaví `basic_ios` třídu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Synonymum pro parametr `Elem`šablony.|
|[int_type](#int_type)|Synonymum pro `Traits::int_type`.|
|[off_type](#off_type)|Synonymum pro `Traits::off_type`.|
|[pos_type](#pos_type)|Synonymum pro `Traits::pos_type`.|
|[traits_type](#traits_type)|Synonymum pro parametr `Traits`šablony.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Špatné](#bad)|Označuje ztrátu integrity vyrovnávací paměti datového proudu.|
|[jejich](#clear)|Vymaže všechny chybové příznaky.|
|[copyfmt](#copyfmt)|Zkopíruje příznaky z jednoho datového proudu do druhého.|
|[eof](#eof)|Určuje, zda byl dosažen konec datového proudu.|
|[výjimek](#exceptions)|Označuje, které výjimky bude vyvoláno datovým proudem.|
|[proběhne](#fail)|Označuje selhání extrakce platného pole z datového proudu.|
|[vyplnění](#fill)|Určuje nebo vrátí znak, který se použije, když text není jako datový proud stejně velký.|
|[Dobré](#good)|Indikuje, že datový proud je v dobrém stavu.|
|[imbue –](#imbue)|Změní národní prostředí.|
|[init](#init)|Voláno `basic_ios` konstruktory.|
|[Pøesunout](#move)|Přesune všechny hodnoty kromě ukazatele do vyrovnávací paměti datového proudu z parametru na aktuální objekt.|
|[dále](#narrow)|Vyhledá ekvivalentní znak k danému `char_type`typu.|
|[rdbuf](#rdbuf)|Směruje datový proud do zadané vyrovnávací paměti.|
|[rdstate](#rdstate)|Přečte stav bitů pro příznaky.|
|[set_rdbuf](#set_rdbuf)|Přiřadí vyrovnávací paměť datového proudu jako vyrovnávací paměť pro čtení tohoto objektu streamu.|
|[setstate](#setstate)|Nastaví další příznaky.|
|[swap](#swap)|Vyměňuje hodnoty v tomto `basic_ios` objektu pro objekty jiného `basic_ios` objektu. Ukazatele na vyrovnávací paměti datového proudu nejsou prohozeny.|
|[propojují](#tie)|Zajišťuje, aby byl jeden datový proud zpracován před jiným datovým proudem.|
|[widen](#widen)|Najde ekvivalent `char_type` daného znaku.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[explicitní operátor bool](#op_bool)|Povoluje použití `basic_ios` objektu jako **bool**. Automatický převod typu je zakázán, aby nedocházelo k běžným, nezamýšleným vedlejším účinkům.|
|[operátor void *](#op_void_star)|Určuje, zda je datový proud stále dobrý.|
|[podnikatel!](#op_not)|Určuje, zda datový proud není chybný.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> pro iOS

**Obor názvů:** std

## <a name="bad"></a>basic_ios:: Bad

Označuje ztrátu integrity vyrovnávací paměti datového proudu.

```cpp
bool bad() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , `rdstate & badbit` Pokud je nenulový; v opačném případě **false**.

Další informace o naleznete `badbit`v tématu [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="basic_ios"></a>basic_ios::basic_ios

Sestaví třídu basic_ios.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>Parametry

*SB*\
Standardní vyrovnávací paměť pro ukládání vstupních nebo výstupních prvků.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje své členské objekty voláním metody [init](#init)(_ *SB*). Druhý (chráněný) konstruktor opustí své členské objekty jako neinicializované. Pozdější volání `init` musí inicializovat objekt před tím, než může být bezpečně zničeno.

## <a name="char_type"></a>basic_ios::char_type

Synonymum pro parametr `Elem`šablony.

```cpp
typedef Elem char_type;
```

## <a name="clear"></a>basic_ios:: Clear

Vymaže všechny chybové příznaky.

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>Parametry

*státech*\
Volitelné Příznaky, které chcete nastavit po vymazání všech příznaků. Výchozí hodnota je `goodbit`.

*reraise*\
Volitelné Určuje, zda má být výjimka znovu vyvolána. Výchozí **hodnota je false** (výjimka nebude znovu vyvolána).

### <a name="remarks"></a>Poznámky

Příznaky jsou `goodbit`, `failbit`, `eofbit`a. `badbit` Testování těchto příznaků pomocí [dobrého](#good), [chybného](#bad), [konce](#eof)souboru a [selhání](#fail)

Členská funkce nahradí informace o stavu uloženého datového proudu pomocí:

`state`&#124;   [](#rdbuf) rdbuf! = 0 goodbit: badbit) `(`

Pokud `state` [](../standard-library/ios-base-class.md#failure) [](#exceptions) jsou výjimky nenulové, vyvolá objekt selhání třídy. **&**

### <a name="example"></a>Příklad

Příklady použití [](../standard-library/string-functions.md#getline) `clear`naleznete v tématu [rdstate](#rdstate) a getline.

## <a name="copyfmt"></a>basic_ios::copyfmt

Zkopíruje příznaky z jednoho datového proudu do druhého.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Datový proud, jehož příznaky chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

**Tento** objekt pro datový proud, do kterého chcete příznaky kopírovat.

### <a name="remarks"></a>Poznámky

Členská funkce hlásí **událost vymazání\_** události zpětného volání. Pak je nakopíruje *přímo*  **\*na znak** výplně, ukazatel na vazbu a informace o formátování. Před změnou masky výjimky ohlásí událost `copyfmt_event`zpětného volání. Pokud po dokončení kopírování je **stav &** [výjimky](#exceptions) nenulové, funkce [efektivně volá](#clear) [rdstate](#rdstate)argumentem. Vrátí  **\*tuto**hodnotu.

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

## <a name="eof"></a>basic_ios:: EOF

Určuje, zda byl dosažen konec datového proudu.

```cpp
bool eof() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byl dosažen konec datového proudu, jinak **false** .

### <a name="remarks"></a>Poznámky

Členská funkce vrátí **hodnotu true** , pokud je [rdstate](#rdstate) `& eofbit` nenulová. Další informace o naleznete `eofbit`v tématu [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="exceptions"></a>basic_ios:: Exceptions

Označuje, které výjimky bude vyvoláno datovým proudem.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>Parametry

*Newexcept*\
Příznaky, které mají vyvolat výjimku.

### <a name="return-value"></a>Návratová hodnota

Příznaky, které jsou aktuálně určeny k vyvolání výjimky pro datový proud.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí uloženou masku výjimky. Druhá členská funkce ukládá *_Except* do masky výjimky a vrátí její předchozí uloženou hodnotu. Všimněte si, že uložení nové masky výjimky může vyvolat výjimku stejně jako volání [clear](#clear)( [rdstate](#rdstate) ).

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

## <a name="fail"></a>basic_ios:: selhání

Označuje selhání extrakce platného pole z datového proudu.

```cpp
bool fail() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud [rdstate](#rdstate) `& (badbit|failbit)` je nenulové, jinak **false**.

Další informace o naleznete `failbit`v tématu [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="fill"></a>basic_ios:: Fill

Určuje nebo vrátí znak, který se použije, když text není jako datový proud stejně velký.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>Parametry

*Char*\
Znak, který chcete vyplnit jako znak výplně.

### <a name="return-value"></a>Návratová hodnota

Aktuální znak výplně.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí uložený znak výplně. Druhá členská *funkce ukládá znak* do výplně znaku a vrátí jeho předchozí uloženou hodnotu.

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

## <a name="good"></a>basic_ios:: dobrý

Indikuje, že datový proud je v dobrém stavu.

```cpp
bool good() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud [rdstate](#rdstate) `== goodbit` (nejsou nastaveny žádné příznaky stavu), jinak **false**.

Další informace o naleznete `goodbit`v tématu [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Příklad

Příklad použití `good`prvku naleznete v tématu [basic_ios:: Bad](#bad) .

## <a name="imbue"></a>basic_ios:: imbue –

Změní národní prostředí.

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Řetězec národního prostředí.

### <a name="return-value"></a>Návratová hodnota

Předchozí národní prostředí.

### <a name="remarks"></a>Poznámky

Pokud [rdbuf](#rdbuf) není ukazatel s hodnotou null, členská funkce volá

`rdbuf`-> [pubimbue](../standard-library/basic-streambuf-class.md#pubimbue) (_ *Loc*)

V každém případě vrátí [ios_base:: imbue –](../standard-library/ios-base-class.md#imbue)(_ *Loc*).

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

## <a name="init"></a>basic_ios:: init

Volá se basic_ios konstruktory.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>Parametry

*_Sb*\
Standardní vyrovnávací paměť pro ukládání vstupních nebo výstupních prvků.

*_Isstd*\
Určuje, zda se jedná o standardní datový proud.

### <a name="remarks"></a>Poznámky

Členská funkce ukládá hodnoty ve všech členských objektech, takže:

- [rdbuf](#rdbuf) vrátí *_Sb.*

- funkce [kravat](#tie) vrátí ukazatel s hodnotou null.

- [rdstate](#rdstate) vrátí [goodbit](../standard-library/ios-base-class.md#iostate) , pokud *_Sb* není nula; v opačném případě vrátí [badbit](../standard-library/ios-base-class.md#iostate).

- [výjimky](#exceptions) vrátí `goodbit`.

- [příznaky](../standard-library/ios-base-class.md#flags) vrací [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [prosinec](../standard-library/ios-base-class.md#fmtflags).

- [Šířka](../standard-library/ios-base-class.md#width) vrátí hodnotu 0.

- [přesnost](../standard-library/ios-base-class.md#precision) vrátí 6.

- funkce [Fill](#fill) vrátí znak mezery.

- [getloc](../standard-library/ios-base-class.md#getloc) vrátí `locale::classic`.

- [iword](../standard-library/ios-base-class.md#iword) vrací hodnotu nula a [pword](../standard-library/ios-base-class.md#pword) vrátí nulový ukazatel pro všechny hodnoty argumentů.

## <a name="int_type"></a>basic_ios::int_type

Synonymum pro `traits_type::int_type`.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="move"></a>  basic_ios::move

Přesune všechny hodnoty kromě ukazatele do vyrovnávací paměti datového proudu z parametru na aktuální objekt.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
`ios_base` Objekt, ze kterého se mají přesunout hodnoty.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce přesune všechny hodnoty uložené *přímo* `*this` do s výjimkou uloženého `stream buffer pointer`, které se nemění napravo a nastaví na ukazatel `*this`s hodnotou null v. Uložený `tie pointer` je nastaven na ukazatel s hodnotou null *vpravo*.

## <a name="narrow"></a>basic_ios:: Narrow

Vyhledá ekvivalentní znak k danému `char_type`typu.

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>Parametry

*Char*\
**Znak** , který se má převést.

*Výchozí*\
**Znak** , který se má vrátit, pokud se nenajde žádný ekvivalent.

### <a name="return-value"></a>Návratová hodnota

Ekvivalentní **znak** k danému `char_type`typu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [use_facet](../standard-library/basic-filebuf-class.md#open)\<CType\<E > > ( [getloc](../standard-library/ios-base-class.md#getloc)()).`narrow` ( `Char`, `Default`).

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

## <a name="op_void_star"></a>basic_ios:: operator void *

Určuje, zda je datový proud stále dobrý.

```cpp
operator void *() const;
```

### <a name="return-value"></a>Návratová hodnota

Operátor vrací ukazatel s hodnotou null pouze v případě [selhání](#fail).

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

## <a name="op_not"></a>basic_ios:: operator!

Určuje, zda datový proud není chybný.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí [chybu](#fail).

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

## <a name="op_bool"></a>basic_ios:: operator bool

Povoluje použití `basic_ios` objektu jako **bool**. Automatický převod typu je zakázán, aby nedocházelo k běžným, nezamýšleným vedlejším účinkům.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Poznámky

Operátor vrátí hodnotu převoditelnou na **hodnotu false** pouze v `fail()`případě, že. Návratový typ je převoditelný pouze na **bool**, nikoli `void *` nebo jiný známý skalární typ.

## <a name="pos_type"></a>  basic_ios::pos_type

Synonymum pro `traits_type::pos_type`.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="rdbuf"></a>basic_ios:: rdbuf

Směruje datový proud do zadané vyrovnávací paměti.

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>Parametry

*_Sb*\
Datový proud.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí ukazatel vyrovnávací paměti uloženého datového proudu.

Druhá členská funkce ukládá *_Sb* do vyrovnávací paměti uloženého datového proudu a vrátí dříve uloženou hodnotu.

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

## <a name="rdstate"></a>basic_ios::rdstate

Přečte stav bitů pro příznaky.

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>Návratová hodnota

Informace o stavu uloženého datového proudu.

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

## <a name="setstate"></a>basic_ios:: setstate

Nastaví další příznaky.

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>Parametry

*_State*\
Další příznaky k nastavení.

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [clear](#clear)(_ *State* &#124; [rdstate](#rdstate)).

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

Přiřadí vyrovnávací paměť datového proudu jako vyrovnávací paměť pro čtení tohoto objektu streamu.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>Parametry

*strbuf*\
Vyrovnávací paměť streamu, která se má stát vyrovnávací pamětí pro čtení.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce ukládá *strbuf* do `stream buffer pointer`. Nevolá `clear`.

## <a name="tie"></a>basic_ios:: kravata

Zajišťuje, aby byl jeden datový proud zpracován před jiným datovým proudem.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>Parametry

*str*\
Datový proud.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí uložený ukazatel na vazbu. Druhá členská funkce ukládá *str* do ukazatele na propojení a vrátí jeho předchozí uloženou hodnotu.

### <a name="remarks"></a>Poznámky

`tie`způsobí synchronizaci dvou datových proudů, což znamená, že operace s jedním datovým proudem se objeví po dokončení operací na jiném streamu.

### <a name="example"></a>Příklad

V tomto příkladu, při vázání CIN na cout, je zaručeno, že řetězec "zadat číslo:" přejde do konzoly před extrahováním samotného čísla z CIN. Tím se eliminuje možnost, že řetězec "zadat číslo:" je ve vyrovnávací paměti stále uložený, když je číslo čteno, takže jsme si jisti, že uživatel má ve skutečnosti, že na odpověď odkazuje. Ve výchozím nastavení jsou CIN a cout svázané.

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

## <a name="traits_type"></a>basic_ios::traits_type

Synonymum pro parametr `Traits`šablony.

```cpp
typedef Traits traits_type;
```

## <a name="widen"></a>basic_ios:: rozšířit

Najde ekvivalent `char_type` daného **znaku**.

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>Parametry

*Char*\
Znak, který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Najde ekvivalent `char_type` daného **znaku**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [use_facet](../standard-library/basic-filebuf-class.md#open)< **CType** \< **E**> > ( [getloc](../standard-library/ios-base-class.md#getloc)). `widen`( `Char`).

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

Vyměňuje hodnoty v tomto `basic_ios` objektu pro objekty jiného `basic_ios` objektu. Odkazy na vyrovnávací paměti datového proudu však nebudou prohozeny.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
`basic_ios` Objekt, který se používá k výměně hodnot.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce vyměňuje všechny hodnoty uložené *přímo* s `*this` výjimkou uložených `stream buffer pointer`.

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
