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
ms.openlocfilehash: c8f883dd4f946c03aaa22dffcf5a3164a539d041
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364922"
---
# <a name="basic_ios-class"></a>basic_ios – třída

Šablona třídy popisuje funkce úložiště a členské funkce společné jak vstupním datovým proudům (šablony třídy [basic_istream),](../standard-library/basic-istream-class.md)tak výstupním datovým proudům (šablony třídy [basic_ostream),](../standard-library/basic-ostream-class.md)které závisí na parametrech šablony. (Třída [ios_base](../standard-library/ios-base-class.md) popisuje, co je běžné a není závislé na parametrech šablony.) Objekt třídy **\<basic_ios třídy Elem, vlastnosti třídy**>`Elem`pomáhá řídit datový proud s prvky typu , jehož znakové znaky jsou určeny třídou `Traits`.

## <a name="syntax"></a>Syntaxe

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ.

*Vlastnosti*\
Proměnná typu `char_traits`.

## <a name="remarks"></a>Poznámky

Objekt třídy **\<basic_ios třídy Elem, třídy Vlastnosti>** ukládá:

- Ukazatel kravaty k objektu typu [basic_istream](../standard-library/basic-istream-class.md)**\<Elem, Vlastnosti>**.

- Ukazatel vyrovnávací paměti datového proudu na objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, Vlastnosti >**.

- [Informace o formátování](../standard-library/ios-base-class.md).

- [Streamovat informace o stavu](../standard-library/ios-base-class.md) v základním objektu typu [ios_base](../standard-library/ios-base-class.md).

- Znak výplně v objektu typu `char_type`.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ios](#basic_ios)|Vytvoří třídu. `basic_ios`|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Synonymum pro `Elem`parametr šablony .|
|[int_type](#int_type)|Synonymum `Traits::int_type`pro .|
|[off_type](#off_type)|Synonymum `Traits::off_type`pro .|
|[pos_type](#pos_type)|Synonymum `Traits::pos_type`pro .|
|[traits_type](#traits_type)|Synonymum pro `Traits`parametr šablony .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Špatné](#bad)|Označuje ztrátu integrity vyrovnávací paměti datového proudu.|
|[Jasné](#clear)|Vymaže všechny příznaky chyb.|
|[copyfmt](#copyfmt)|Kopíruje příznaky z jednoho datového proudu do druhého.|
|[eof](#eof)|Označuje, zda bylo dosaženo konce datového proudu.|
|[Výjimky](#exceptions)|Označuje, které výjimky budou vyvolány datovým proudem.|
|[Selhání](#fail)|Označuje selhání extrahování platného pole z datového proudu.|
|[fill](#fill)|Určuje nebo vrací znak, který bude použit, pokud text není tak široký jako datový proud.|
|[Dobré](#good)|Označuje, že datový proud je v dobrém stavu.|
|[Naplnit](#imbue)|Změní národní prostředí.|
|[init](#init)|Volána `basic_ios` konstruktory.|
|[Přesunout](#move)|Přesune všechny hodnoty kromě ukazatele do vyrovnávací paměti datového proudu z parametru na aktuální objekt.|
|[Úzké](#narrow)|Najde ekvivalentní char k `char_type`dané .|
|[rdbuf](#rdbuf)|Trasy datového proudu do zadané vyrovnávací paměti.|
|[rdstate](#rdstate)|Přečte stav bitů pro příznaky.|
|[set_rdbuf](#set_rdbuf)|Přiřadí vyrovnávací paměť datového proudu jako vyrovnávací paměť pro čtení pro tento objekt datového proudu.|
|[setstate](#setstate)|Nastaví další příznaky.|
|[Swap](#swap)|Vymění hodnoty `basic_ios` v tomto objektu za hodnoty jiného `basic_ios` objektu. Ukazatele na vyrovnávací paměti datového proudu nejsou prohozeny.|
|[Kravatu](#tie)|Zajišťuje, že jeden datový proud je zpracován před jiným datovým proudem.|
|[Rozšířit](#widen)|Najde ekvivalent `char_type` dané char.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[explicitní operátor bool](#op_bool)|Umožňuje použití `basic_ios` objektu jako **bool**. Automatický převod typu je zakázán, aby se zabránilo běžným, nezamýšleným vedlejším účinkům.|
|[operátor void *](#op_void_star)|Označuje, zda je datový proud stále dobrý.|
|[Operátor!](#op_not)|Označuje, zda datový proud není špatný.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<ios>

**Obor názvů:** std

## <a name="basic_iosbad"></a><a name="bad"></a>basic_ios::špatné

Označuje ztrátu integrity vyrovnávací paměti datového proudu.

```cpp
bool bad() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `rdstate & badbit` je nenulová; jinak **false**.

Další informace `badbit`naleznete v [tématu ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="basic_iosbasic_ios"></a><a name="basic_ios"></a>basic_ios::basic_ios

Vytvoří basic_ios třídy.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>Parametry

*Sb*\
Standardní vyrovnávací paměť pro uložení vstupních nebo výstupních prvků.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje své členské objekty voláním [init](#init)(_ *Sb).* Druhý (chráněný) konstruktor ponechá své členské objekty bez inicializovány. Pozdější volání `init` musí inicializovat objekt před jej lze bezpečně zničit.

## <a name="basic_ioschar_type"></a><a name="char_type"></a>basic_ios::char_type

Synonymum pro `Elem`parametr šablony .

```cpp
typedef Elem char_type;
```

## <a name="basic_iosclear"></a><a name="clear"></a>basic_ios::vymazat

Vymaže všechny příznaky chyb.

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>Parametry

*Státu*\
(Nepovinné) Příznaky, které chcete nastavit po vymazání všech příznaků. Výchozí hodnota `goodbit`je na .

*reraise*\
(Nepovinné) Určuje, zda má být výjimka znovu vyvolána. Výchozí hodnota **je nepravdivá** (výjimku znovu nevyvolá).

### <a name="remarks"></a>Poznámky

Příznaky jsou `goodbit` `failbit`, `eofbit`, `badbit`, a . Test pro tyto příznaky s [dobrou](#good), [špatné](#bad), [eof](#eof), a [selhání](#fail)

Členská funkce nahradí informace o stavu uloženého datového proudu:

`state`&#124; `(` [rdbuf](#rdbuf) != 0 **goodbit** : **badbit**)

Pokud `state` **&** [výjimky](#exceptions) je nenulová, pak vyvolá objekt [selhání](../standard-library/ios-base-class.md#failure)třídy .

### <a name="example"></a>Příklad

Viz [rdstate](#rdstate) a [getline](../standard-library/string-functions.md#getline) `clear`pro příklady pomocí .

## <a name="basic_ioscopyfmt"></a><a name="copyfmt"></a>basic_ios::copyfmt

Kopíruje příznaky z jednoho datového proudu do druhého.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Datový proud, jehož příznaky chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

**Tento** objekt pro datový proud, do kterého kopírujete příznaky.

### <a name="remarks"></a>Poznámky

Členská funkce hlásí **událost vymazání\_** události zpětného volání . Potom zkopíruje *zpravé* do ** \*tohoto** výplně znak, ukazatel kravaty a informace o formátování. Před změnou masky výjimky hlásí `copyfmt_event`událost zpětného volání . Pokud po dokončení kopírování **stav &** [výjimky](#exceptions) je nenulová, funkce efektivně volá [clear](#clear) s argumentem [rdstate](#rdstate). Vrátí ** \*toto**.

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

## <a name="basic_ioseof"></a><a name="eof"></a>basic_ios::eof

Označuje, zda bylo dosaženo konce datového proudu.

```cpp
bool eof() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud bylo dosaženo konce datového proudu, **false** jinak.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí **hodnotu true,** pokud je [stav rdstate](#rdstate) `& eofbit` nenulový. Další informace `eofbit`naleznete v [tématu ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="basic_iosexceptions"></a><a name="exceptions"></a>basic_ios::výjimky

Označuje, které výjimky budou vyvolány datovým proudem.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>Parametry

*Nové kromě*\
Příznaky, které chcete vyvolat výjimku.

### <a name="return-value"></a>Návratová hodnota

Příznaky, které jsou aktuálně zadány vyvolat výjimku pro datový proud.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí masku uložené výjimky. Druhá členská funkce ukládá *_Except* v masce výjimky a vrací jeho předchozí uloženou hodnotu. Všimněte si, že ukládání nové masky výjimky může vyvolat výjimku stejně jako volání [clear](#clear)( [rdstate](#rdstate) ).

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

## <a name="basic_iosfail"></a><a name="fail"></a>basic_ios::selhání

Označuje selhání extrahování platného pole z datového proudu.

```cpp
bool fail() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** pokud [rdstate](#rdstate) `& (badbit|failbit)` je nenulová, jinak **false**.

Další informace `failbit`naleznete v [tématu ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="basic_iosfill"></a><a name="fill"></a>basic_ios::výplň

Určuje nebo vrací znak, který bude použit, pokud text není tak široký jako datový proud.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>Parametry

*Char*\
Znak, který chcete jako znak výplně.

### <a name="return-value"></a>Návratová hodnota

Aktuální znak výplně.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí uložený znak výplně. Druhá členská funkce uloží *Char* ve znaku výplně a vrátí jeho předchozí uloženou hodnotu.

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

## <a name="basic_iosgood"></a><a name="good"></a>basic_ios::dobrý

Označuje, že datový proud je v dobrém stavu.

```cpp
bool good() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** pokud [rdstate](#rdstate) `== goodbit` (nejsou nastaveny žádné příznaky stavu), jinak **false**.

Další informace `goodbit`naleznete v [tématu ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Příklad

Viz [basic_ios::bad](#bad) pro příklad `good`použití .

## <a name="basic_iosimbue"></a><a name="imbue"></a>basic_ios::imbue

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

Pokud [rdbuf](#rdbuf) není nulový ukazatel, členská funkce volá

`rdbuf`-> [pubimbue](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)

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

## <a name="basic_iosinit"></a><a name="init"></a>basic_ios::init

Volána basic_ios konstruktory.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>Parametry

*_Sb*\
Standardní vyrovnávací paměť pro uložení vstupních nebo výstupních prvků.

*_Isstd*\
Určuje, zda se jedná o standardní datový proud.

### <a name="remarks"></a>Poznámky

Členská funkce ukládá hodnoty ve všech členských objektech tak, aby:

- [rdbuf](#rdbuf) se *vrací _Sb.*

- [tie](#tie) vrátí ukazatel null.

- [rdstate](#rdstate) vrátí [goodbit,](../standard-library/ios-base-class.md#iostate) pokud *je _Sb* nenulová; v opačném případě vrátí [badbit](../standard-library/ios-base-class.md#iostate).

- [výjimky](#exceptions) `goodbit`vrátí .

- [příznaky](../standard-library/ios-base-class.md#flags) vrátí [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags).

- [šířka](../standard-library/ios-base-class.md#width) vrátí 0.

- [přesnost](../standard-library/ios-base-class.md#precision) vrátí 6.

- [fill](#fill) vrátí znak mezery.

- [getloc](../standard-library/ios-base-class.md#getloc) `locale::classic`vrátí .

- [iword](../standard-library/ios-base-class.md#iword) vrátí nulu a [formula vrátí](../standard-library/ios-base-class.md#pword) nulový ukazatel pro všechny hodnoty argumentů.

## <a name="basic_iosint_type"></a><a name="int_type"></a>basic_ios::int_type

Synonymum `traits_type::int_type`pro .

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_iosmove"></a><a name="move"></a>basic_ios::přesunout

Přesune všechny hodnoty kromě ukazatele do vyrovnávací paměti datového proudu z parametru na aktuální objekt.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Objekt, `ios_base` ze který chcete přesunout hodnoty.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce přesune všechny `*this` hodnoty uložené `stream buffer pointer`v *pravo* na s výjimkou uložené , `*this`která je nezměněna v *pravo* a nastavena na nulový ukazatel v . Uloženo `tie pointer` je nastavena na ukazatel null v *pravém*.

## <a name="basic_iosnarrow"></a><a name="narrow"></a>basic_ios::úzké

Najde ekvivalentní char k `char_type`dané .

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>Parametry

*Char*\
**Znak** převést.

*Výchozí*\
**Char,** který chcete vrácena, pokud není nalezen žádný ekvivalent.

### <a name="return-value"></a>Návratová hodnota

Ekvivalentní **znak** k `char_type`danému .

### <a name="remarks"></a>Poznámky

Členská funkce [use_facet](../standard-library/basic-filebuf-class.md#open)\<vrátí\<use_facet ctype E> >( [getloc](../standard-library/ios-base-class.md#getloc)( ) ). `narrow`( `Char`, `Default`).

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

## <a name="basic_iosoff_type"></a><a name="off_type"></a>basic_ios::off_type

Synonymum `traits_type::off_type`pro .

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_iosoperator-void-"></a><a name="op_void_star"></a>basic_ios::operátor void *

Označuje, zda je datový proud stále dobrý.

```cpp
operator void *() const;
```

### <a name="return-value"></a>Návratová hodnota

Operátor vrátí ukazatel null pouze v případě [selhání](#fail).

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

## <a name="basic_iosoperator"></a><a name="op_not"></a>basic_ios::operátor!

Označuje, zda datový proud není špatný.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí [se nezdaří](#fail).

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

## <a name="basic_iosoperator-bool"></a><a name="op_bool"></a>basic_ios::obsluha bool

Umožňuje použití `basic_ios` objektu jako **bool**. Automatický převod typu je zakázán, aby se zabránilo běžným, nezamýšleným vedlejším účinkům.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Poznámky

Operátor vrátí hodnotu **false** převoditelné `fail()`na false pouze v případě , Návratový typ je konvertibilní pouze na **bool**, nikoli nebo `void *` jiný známý skalární typ.

## <a name="basic_iospos_type"></a><a name="pos_type"></a>basic_ios::pos_type

Synonymum `traits_type::pos_type`pro .

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_iosrdbuf"></a><a name="rdbuf"></a>basic_ios::rdbuf

Trasy datového proudu do zadané vyrovnávací paměti.

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>Parametry

*_Sb*\
Potok.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí ukazatel vyrovnávací paměti uloženého datového proudu.

Druhá členská funkce ukládá *_Sb* v ukazateli vyrovnávací paměti uloženého datového proudu a vrací dříve uloženou hodnotu.

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

## <a name="basic_iosrdstate"></a><a name="rdstate"></a>basic_ios::rdstate

Přečte stav bitů pro příznaky.

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložené informace o stavu datového proudu.

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

## <a name="basic_iossetstate"></a><a name="setstate"></a>basic_ios::setstate

Nastaví další příznaky.

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>Parametry

*_State*\
Další příznaky nastavit.

### <a name="remarks"></a>Poznámky

Členská funkce účinně volá [clear](#clear)(_ *State* &#124; [rdstate](#rdstate)).

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

## <a name="basic_iosset_rdbuf"></a><a name="set_rdbuf"></a>basic_ios::set_rdbuf

Přiřadí vyrovnávací paměť datového proudu jako vyrovnávací paměť pro čtení pro tento objekt datového proudu.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>Parametry

*strbuf (Strbuf)*\
Vyrovnávací paměť datového proudu, která se stane vyrovnávací pamětí pro čtení.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce ukládá `stream buffer pointer` *strbuf* v . Nevolá `clear`.

## <a name="basic_iostie"></a><a name="tie"></a>basic_ios::kravata

Zajišťuje, že jeden datový proud je zpracován před jiným datovým proudem.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>Parametry

*Str*\
Potok.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí uložený ukazatel kravaty. Druhá členská funkce ukládá *str* v ukazatel kravatu a vrátí jeho předchozí uloženou hodnotu.

### <a name="remarks"></a>Poznámky

`tie`způsobí, že dva datové proudy, které mají být synchronizovány, tak, aby operace na jeden datový proud dojít po dokončení operací na druhý datový proud.

### <a name="example"></a>Příklad

V tomto příkladu vázaným odkazem cin na cout je zaručeno, že řetězec "Enter a number:" přejde do konzoly před extrahováním samotného čísla z cin. Tím se eliminuje možnost, že řetězec "Zadejte číslo:" je stále sedí ve vyrovnávací paměti při čtení čísla, takže jsme si jisti, že uživatel skutečně má nějakou výzvu k odpovědi. Ve výchozím nastavení jsou cin a cout svázané.

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

## <a name="basic_iostraits_type"></a><a name="traits_type"></a>basic_ios::traits_type

Synonymum pro `Traits`parametr šablony .

```cpp
typedef Traits traits_type;
```

## <a name="basic_ioswiden"></a><a name="widen"></a>basic_ios::rozšířit

Najde ekvivalent `char_type` daného **znaku**.

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>Parametry

*Char*\
Znak převést.

### <a name="return-value"></a>Návratová hodnota

Najde ekvivalent `char_type` daného **znaku**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **E**> >( [getloc](../standard-library/ios-base-class.md#getloc)). `widen`( `Char`).

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

## <a name="basic_iosswap"></a><a name="swap"></a>basic_ios::swap

Vymění hodnoty `basic_ios` v tomto objektu za hodnoty jiného `basic_ios` objektu. Ukazatele na vyrovnávací paměti datového proudu však nejsou prohozeny.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Objekt, `basic_ios` který se používá k výměně hodnot.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce vyměňuje všechny `*this` hodnoty `stream buffer pointer`uložené v *právu* s výjimkou uložené .

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
