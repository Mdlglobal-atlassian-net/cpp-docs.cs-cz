---
title: basic_ios – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 569b37f705bc974c9b16b1602c59983c58a2775c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848580"
---
# <a name="basicios-class"></a>basic_ios – třída

Šablony třídy popisuje funkce úložiště a člen, které jsou společné pro obě vstupní datové proudy (šablony třídy [basic_istream](../standard-library/basic-istream-class.md)) a výstupní datové proudy (šablony třídy [basic_ostream](../standard-library/basic-ostream-class.md)), závisí na Parametry šablony. (Třída [ios_base](../standard-library/ios-base-class.md) popisuje, co je to běžné a není závislá na parametry šablony.) Třída objektu **basic_ios\<Elem třídy, vlastnosti třídy >** pomáhá řídit datový proud s elementy typu **Elem**, jehož vlastnosti znak určuje třídu  **Vlastnosti**.

## <a name="syntax"></a>Syntaxe

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>Parametry

`Elem` Typ.

`Traits` Proměnné typu `char_traits`.

## <a name="remarks"></a>Poznámky

Třída objektu **basic_ios\<Elem třídy, vlastnosti třídy >** ukládá:

- Ukazatel vazbě k objektu typu [basic_istream](../standard-library/basic-istream-class.md)**\<Elem, vlastnosti >**.

- Datový proud vyrovnávací paměti ukazatele na objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, vlastnosti >**.

- [Informace o formátu](../standard-library/ios-base-class.md).

- [Informace o stavu Stream](../standard-library/ios-base-class.md) v základní objekt typu [ios_base](../standard-library/ios-base-class.md).

- Výplňovým znakem v objektu typu `char_type`.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ios –](#basic_ios)|Vytvoří `basic_ios` třídy.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Synonymum pro parametr šablony `Elem`.|
|[int_type](#int_type)|Synonymum pro `Traits::int_type`.|
|[off_type –](#off_type)|Synonymum pro `Traits::off_type`.|
|[pos_type](#pos_type)|Synonymum pro `Traits::pos_type`.|
|[traits_type](#traits_type)|Synonymum pro parametr šablony `Traits`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Špatné](#bad)|Určuje, ke ztrátě integrity vyrovnávací paměti datového proudu.|
|[Zrušte zaškrtnutí](#clear)|Vymaže všechny příznaky chyby.|
|[copyfmt –](#copyfmt)|Zkopíruje příznaky z jednoho datového proudu do jiného.|
|[eof](#eof)|Označuje, pokud byl dosažen konec datového proudu.|
|[Výjimky](#exceptions)|Označuje, výjimek, které bude vyvolána pomocí datového proudu.|
|[Selhání](#fail)|Označuje selhání platné pole extrahovat z datového proudu.|
|[výplně](#fill)|Určuje nebo vrátí znak, který se použije, když text není širší jako datový proud.|
|[Dobré](#good)|Označuje, že datový proud je v dobrém stavu.|
|[imbue –](#imbue)|Změní národní prostředí.|
|[init](#init)|Voláno rozhraním `basic_ios` konstruktory.|
|[Přesunutí](#move)|Přesune všechny hodnoty, s výjimkou má ukazatel na vyrovnávací paměť datový proud, z parametru pro aktuální objekt.|
|[zúžit](#narrow)|Vyhledá ekvivalentní char k danou `char_type`.|
|[rdbuf](#rdbuf)|Datový proud trasy do zadané vyrovnávací paměti.|
|[rdstate –](#rdstate)|Přečte stav služby bits pro příznaky.|
|[set_rdbuf](#set_rdbuf)|Přiřadí datový proud vyrovnávací paměti jako vyrovnávací paměti pro čtení pro tento objekt datového proudu.|
|[setstate –](#setstate)|Nastaví další příznaky.|
|[Swap](#swap)|Výměny hodnoty v tomto `basic_ios` objekt pro ty jiného `basic_ios` objektu. Ukazatelé na datový proud vyrovnávací paměti nejsou vzájemně zaměněny.|
|[Tie –](#tie)|Zajišťuje, že jeden datový proud se zpracují dříve, než jiné datového proudu.|
|[widen](#widen)|Vyhledá ekvivalent `char_type` na daný typ char.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[explicitní operátor bool](#op_bool)|Umožňuje použití `basic_ios` objekt jako `bool`. Převod typů automatické vypnutá aby běžné, neúmyslné vedlejší účinky.|
|[operátor void *](#op_void_star)|Určuje, zda je stále dobrý datového proudu.|
|[Operator – operátor!](#op_not)|Označuje, pokud není chybný datový proud.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<ios >

**Namespace:** – std

## <a name="bad"></a>  basic_ios::bad

Určuje, ke ztrátě integrity datového proudu vyrovnávací paměti

```cpp
bool bad() const;
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud `rdstate & badbit` nenulové hodnoty v opačném `false`.

Další informace o `badbit`, najdete v části [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

Vytvoří basic_ios – třída.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>Parametry

`sb` Standardní vyrovnávací paměti k uložení vstupních nebo výstupních elementy.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje jeho členských objektů voláním [init](#init)(_ *Sb*). Druhý konstruktor (chráněné) zanechává jeho členských objektů Neinicializovaný. Novější volání **init** musí inicializovat objekt, než může být bezpečně zničena.

## <a name="char_type"></a>  basic_ios::char_type

Synonymum pro parametr šablony **Elem**.

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

`state` (volitelné) Příznaky, které chcete nastavit po vymazání všech příznaků. Použije se výchozí hodnota `goodbit`.

`reraise` (volitelné) Určuje, zda má být výjimka znovu vyvolané. Použije se výchozí hodnota `false` (nebude znovu vyvolat výjimku).

### <a name="remarks"></a>Poznámky

Příznaky se **goodbit**, **failbit**, **eofbit**, a **badbit**. Test pro tyto příznaky s [dobrý](#good), [chybný](#bad), [eof](#eof), a [nezdaří](#fail)

Členská funkce nahrazuje informace o stavu uložené datového proudu s:

`state` &#124;`(` [rdbuf –](#rdbuf) ! = 0 **goodbit** : **badbit**)

Pokud `state` **&** [výjimky](#exceptions) je nenulové hodnoty, pak vyhodí objekt třídy [selhání](../standard-library/ios-base-class.md#failure).

### <a name="example"></a>Příklad

V tématu [rdstate –](#rdstate) a [getline](../standard-library/string-functions.md#getline) příklady použití **vymazat**.

## <a name="copyfmt"></a>  basic_ios::copyfmt

Zkopíruje příznaky z jednoho datového proudu do jiného.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>Parametry

`right` Datový proud, jejichž příznaky, které chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

**To** objekt pro datový proud, do které chcete kopírovat příznaků.

### <a name="remarks"></a>Poznámky

Členská funkce sestav událost zpětného volání **vymazat\_událostí**. Pak zkopíruje z `right` do  **\*to** znak výplně ukazatele vazbě a informace formátování. Před změnou maska výjimky, oznámí událost zpětného volání **copyfmt_event**. Pokud po dokončení kopírování **stav &**[výjimky](#exceptions) je nenulové hodnoty, funkce efektivně volá [vymazat](#clear) s argumentem [rdstate –](#rdstate). Vrátí  **\*to**.

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

Označuje, pokud byl dosažen konec datového proudu.

```cpp
bool eof() const;
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud byl dosažen konec datového proudu, `false` jinak.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu `true` Pokud [rdstate –](#rdstate) `& eofbit` nenulový. Další informace o `eofbit`, najdete v části [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

Označuje, výjimek, které bude vyvolána pomocí datového proudu.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>Parametry

*Newexcept* příznaky, které chcete vyvolat výjimku.

### <a name="return-value"></a>Návratová hodnota

Příznaky, které jsou aktuálně zadaný na vyvolala výjimku pro datový proud.

### <a name="remarks"></a>Poznámky

První člen funkce vrátí maska uložené výjimka. Druhý člen funkce úložiště *_Except* v maska výjimky a vrátí jeho předchozí uložené hodnoty. Všimněte si, že ukládání novou masku výjimka se může vyvolat výjimku stejně jako volání [vymazat](#clear)( [rdstate –](#rdstate) ).

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

Označuje selhání platné pole extrahovat z datového proudu.

```cpp
bool fail() const;
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud [rdstate –](#rdstate) `& (badbit|failbit)` je nenulové hodnoty, jinak `false`.

Další informace o `failbit`, najdete v části [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

Určuje nebo vrátí znak, který se použije, když text není širší jako datový proud.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>Parametry

`Char` Znak, který chcete používat jako výplňovým znakem.

### <a name="return-value"></a>Návratová hodnota

Aktuální znak výplně.

### <a name="remarks"></a>Poznámky

První člen funkce vrátí znak uložené výplně. Druhý člen funkce úložiště `Char` v výplně znaku a vrátí jeho předchozí uložené hodnoty.

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

`true` Pokud [rdstate –](#rdstate) `== goodbit` (jsou nastaveny žádné příznaky stavu), jinak `false`.

Další informace o `goodbit`, najdete v části [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Příklad

V tématu [basic_ios::bad](#bad) příklad použití `good`.

## <a name="imbue"></a>  basic_ios::imbue

Změní národní prostředí.

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>Parametry

`Loc` Řetězec, národní prostředí.

### <a name="return-value"></a>Návratová hodnota

Předchozí národní prostředí.

### <a name="remarks"></a>Poznámky

Pokud [rdbuf –](#rdbuf) není nulový ukazatel, člen volání funkcí

`rdbuf`-> [pubimbue –](../standard-library/basic-streambuf-class.md#pubimbue)(_ *umístění*)

V každém případě vrátí [ios_base::imbue](../standard-library/ios-base-class.md#imbue)(_ *umístění*).

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

Voláno rozhraním basic_ios konstruktory.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>Parametry

`_Sb` Standardní vyrovnávací paměti k uložení vstupních nebo výstupních elementy.

`_Isstd` Určuje, zda se jedná o standardní datového proudu.

### <a name="remarks"></a>Poznámky

Členská funkce ukládá hodnoty do všech objektů člen, tak, aby:

- [rdbuf –](#rdbuf) vrátí *_Sb.*

- [Tie –](#tie) vrátí ukazatele null.

- [rdstate –](#rdstate) vrátí [goodbit](../standard-library/ios-base-class.md#iostate) Pokud `_Sb` je nenulové hodnoty, jinak vrátí hodnotu [badbit](../standard-library/ios-base-class.md#iostate).

- [výjimky](#exceptions) vrátí **goodbit**.

- [příznaky](../standard-library/ios-base-class.md#flags) vrátí [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags).

- [Šířka](../standard-library/ios-base-class.md#width) vrátí hodnotu 0.

- [přesnost](../standard-library/ios-base-class.md#precision) vrátí hodnotu 6.

- [výplně](#fill) vrátí znak mezery.

- [getloc –](../standard-library/ios-base-class.md#getloc) vrátí `locale::classic`.

- [iword –](../standard-library/ios-base-class.md#iword) vrátí nula, a [pword –](../standard-library/ios-base-class.md#pword) vrátí ukazatel s hodnotou null pro všechny hodnoty argumentu.

## <a name="int_type"></a>  basic_ios::int_type

Synonymum pro **traits_type::int_type**.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="move"></a>  basic_ios::Move

Přesune všechny hodnoty, s výjimkou má ukazatel na vyrovnávací paměť datový proud, z parametru pro aktuální objekt.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

`right` `ios_base` Objekt, který chcete přesunout hodnot.

### <a name="remarks"></a>Poznámky

Funkce chráněného člena přesune všechny hodnoty, které jsou uložené v `right` k `*this` s výjimkou uložená `stream buffer pointer`, který se nemění `right` a nastavte na hodnotu null. ukazatel v `*this`. Uložených `tie pointer` je nastaven na hodnotu null. ukazatel v `right`.

## <a name="narrow"></a>  basic_ios::Narrow

Vyhledá ekvivalentní char k danou `char_type`.

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>Parametry

`Char` `char` Převést.

`Default` `char` Zda mají být vráceny Pokud se nenajde žádný ekvivalent.

### <a name="return-value"></a>Návratová hodnota

Ekvivalent `char` k danou `char_type`.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [use_facet](../standard-library/basic-filebuf-class.md#open)\<ctype\<E >> ( [getloc –](../standard-library/ios-base-class.md#getloc)()).`narrow` ( `Char`, `Default`).

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

Synonymum pro **traits_type::off_type**.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_void_star"></a>  basic_ios::Operator void *

Určuje, zda je stále dobrý datového proudu.

```cpp
operator void *() const;
```

### <a name="return-value"></a>Návratová hodnota

Operátor vrátí ukazatele null jenom v případě [nezdaří](#fail).

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

Označuje, pokud není chybný datový proud.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí [nezdaří](#fail).

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

Umožňuje použití `basic_ios` objekt jako `bool`. Převod typů automatické vypnutá aby běžné, neúmyslné vedlejší účinky.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu převoditelné na operátor `false` pouze v případě `fail()`. Návratový typ je převést pouze na `bool`, nikoli k `void *` nebo jiných známým skalárního typu.

## <a name="pos_type"></a>  basic_ios::pos_type

Synonymum pro **traits_type::pos_type**.

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

`_Sb` Datový proud.

### <a name="remarks"></a>Poznámky

První člen funkce vrátí vyrovnávací paměti ukazatele uložené datového proudu.

Druhý člen funkce úložiště `_Sb` ve vyrovnávací paměti ukazatele uložené datového proudu a vrátí hodnotu, dříve uložené.

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

Přečte stav služby bits pro příznaky.

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

`_State` Další příznaky nastavit.

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

Přiřadí datový proud vyrovnávací paměti jako vyrovnávací paměti pro čtení pro tento objekt datového proudu.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>Parametry

`strbuf` Datový proud vyrovnávací paměť k vyrovnávací paměti pro čtení.

### <a name="remarks"></a>Poznámky

Funkce úložiště chráněného člena `strbuf` v `stream buffer pointer`. Nevolá `clear`.

## <a name="tie"></a>  basic_ios::Tie

Zajišťuje, že jeden datový proud se zpracují dříve, než jiné datového proudu.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>Parametry

`str` Datový proud.

### <a name="return-value"></a>Návratová hodnota

První člen funkce vrátí ukazatel uložené vazbě. Druhý člen funkce úložiště `str` ve vazbě ukazatel a vrátí jeho předchozí uložená hodnota.

### <a name="remarks"></a>Poznámky

`tie` způsobí dvě streamů synchronizaci, tak, aby operace na jeden datový proud provést po dokončení operací na jiné datového proudu.

### <a name="example"></a>Příklad

V tomto příkladu pomocí příkazů cin k cout, bylo zaručeno, že "Zadejte číslo:" řetězec přejde ke konzole před číslo samotné se extrahují z cin. Tím se eliminuje možnost, "Zadejte číslo:" řetězec je stále uložený ve vyrovnávací paměti při čtení číslo, takže jsme si jisti, že uživatel má ve skutečnosti některé řádku reagovat na. Ve výchozím nastavení jsou svázané cin a cout.

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

Synonymum pro parametr šablony **vlastnosti**.

```cpp
typedef Traits traits_type;
```

## <a name="widen"></a>  basic_ios::widen

Vyhledá ekvivalent `char_type` k danou `char`.

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>Parametry

`Char` Znak, který se má převést.

### <a name="return-value"></a>Návratová hodnota

Vyhledá ekvivalent `char_type` k danou `char`.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **E**>> ( [getloc –](../standard-library/ios-base-class.md#getloc)). `widen`( `Char`).

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

Výměny hodnoty v tomto `basic_ios` objekt pro ty jiného `basic_ios` objektu. Ukazatelé na datový proud vyrovnávací paměti se však nejsou vzájemně zaměněny.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

`right` `basic_ios` Objekt, který se používá k výměně hodnoty.

### <a name="remarks"></a>Poznámky

Chráněný člen funkce výměny všechny hodnoty, které jsou uložené v `right` s `*this` s výjimkou uložené `stream buffer pointer`.

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
