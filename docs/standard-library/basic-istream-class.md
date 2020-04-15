---
title: basic_istream – třída
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_istream
- istream/std::basic_istream::gcount
- istream/std::basic_istream::get
- istream/std::basic_istream::getline
- 'istream/std::basic_istream::'
- istream/std::basic_istream::peek
- istream/std::basic_istream::putback
- istream/std::basic_istream::read
- istream/std::basic_istream::readsome
- istream/std::basic_istream::seekg
- istream/std::basic_istream::sentry
- istream/std::basic_istream::swap
- istream/std::basic_istream::sync
- istream/std::basic_istream::tellg
- istream/std::basic_istream::unget
helpviewer_keywords:
- std::basic_istream [C++]
- std::basic_istream [C++], gcount
- std::basic_istream [C++], get
- std::basic_istream [C++], getline
- std::basic_istream [C++], OVERWRITE
- std::basic_istream [C++], peek
- std::basic_istream [C++], putback
- std::basic_istream [C++], read
- std::basic_istream [C++], readsome
- std::basic_istream [C++], seekg
- std::basic_istream [C++], sentry
- std::basic_istream [C++], swap
- std::basic_istream [C++], sync
- std::basic_istream [C++], tellg
- std::basic_istream [C++], unget
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
ms.openlocfilehash: 03a6e3a65d6dc8c2fa896949855bd23a01578e5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376830"
---
# <a name="basic_istream-class"></a>basic_istream – třída

Popisuje objekt, který řídí extrakci prvků a kódovaných objektů z `Char_T`vyrovnávací paměti datového proudu s prvky typu , označované také jako [char_type](../standard-library/basic-ios-class.md#char_type), jehož znakové znaky jsou určeny třídou *Tr*, označovanou také jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_istream : virtual public basic_ios<Char_T, Tr>
```

## <a name="remarks"></a>Poznámky

Většina členských funkcí, které přetížení [operátor>>](#op_gt_gt) jsou formátované vstupní funkce. Řídí se vzorem:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{
    try
    {
        /*extract elements and convert
            accumulate flags in state.
            store a successful conversion*/
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);

return (*this);
```

Mnoho dalších členských funkcí jsou neformátované vstupní funkce. Řídí se vzorem:

```cpp
iostate state = goodbit;
count = 0;    // the value returned by gcount
const sentry ok(*this, true);

if (ok)
{
    try
    {
        /* extract elements and deliver
            count extracted elements in count
            accumulate flags in state */
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);
```

Obě skupiny [`setstate`](../standard-library/basic-ios-class.md#setstate) `(eofbit)` funkcí volání, pokud narazí na konec souboru při extrahování prvků.

Objekt úložiště `basic_istream<Char_T, Tr>` třídy:

- Virtuální objekt veřejné základny třídy [`basic_ios`](../standard-library/basic-ios-class.md) `<Char_T, Tr>`.

- Počet extrakce pro poslední neformátovanou `count` vstupní operaci (volanou v předchozím kódu).

## <a name="example"></a>Příklad

Další informace o vstupních datových proudech najdete v příkladu [třídy basic_ifstream.](../standard-library/basic-ifstream-class.md)

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_istream](#basic_istream)|Vytvoří objekt typu `basic_istream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[gcount](#gcount)|Vrátí počet znaků přečtených během posledního neformátovaného vstupu.|
|[get](#get)|Přečte jeden nebo více znaků ze vstupního datového proudu.|
|[getline](#getline)|Přečte řádek ze vstupního datového proudu.|
|[Ignorovat](#ignore)|Způsobí, že počet prvků, které mají být přeskočeny z aktuální pozice pro čtení.|
|[Peek](#peek)|Vrátí další znak, který má být přečten.|
|[putback](#putback)|Vloží zadaný znak do datového proudu.|
|[Číst](#read)|Přečte zadaný počet znaků z datového proudu a uloží je do pole.|
|[readsome](#readsome)|Pouze pro čtení z vyrovnávací paměti.|
|[seekg](#seekg)|Přesune pozici pro čtení v datovém proudu.|
|[Sentry](#sentry)|Vnořená třída popisuje objekt, jehož deklarace strukturuje formátované vstupní funkce a neformátované vstupní funkce.|
|[Swap](#swap)|Vymění `basic_istream` tento objekt `basic_istream` za zadaný parametr objektu.|
|[synchronizace](#sync)|Synchronizuje přidružené vstupní zařízení datového proudu s vyrovnávací pamětí datového proudu.|
|[tellg](#tellg)|Hlásí aktuální pozici čtení v datovém proudu.|
|[unget](#unget)|Vloží naposledy přečtený znak zpět do datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor>>](#op_gt_gt)|Volá funkci vstupního datového proudu nebo čte formátovaná data ze vstupního datového proudu.|
|[operátor =](#op_eq)|Přiřadí `basic_istream` na pravé straně operátoru k tomuto objektu. Je to úkol přesunu `rvalue` zahrnující odkaz, který nezanechává kopii.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<istream>

**Obor názvů:** std

## <a name="basic_istreambasic_istream"></a><a name="basic_istream"></a>basic_istream::basic_istream

Vytvoří objekt typu `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Char_T, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*strbuf (Strbuf)*\
Objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**true,** pokud se jedná o standardní proud; jinak **false**.

*Právo*\
Objekt `basic_istream` ke kopírování.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [`init`](../standard-library/basic-ios-class.md#init) `(strbuf)`. Také ukládá nulu v počtu extrakce. Další informace o tomto počtu extrakce naleznete v části Poznámky [basic_istream přehled třídy.](../standard-library/basic-istream-class.md)

Druhý konstruktor inicializuje základní třídu voláním `move(right)`. Ukládá také `right.gcount()` v počtu extrakce a ukládá nulu v počtu extrakce pro *right**.

### <a name="example"></a>Příklad

Další informace o vstupních datových proudech najdete v příkladu [pro basic_ifstream::basic_ifstream.](../standard-library/basic-ifstream-class.md#basic_ifstream)

## <a name="basic_istreamgcount"></a><a name="gcount"></a>basic_istream::gcount

Vrátí počet znaků přečtených během posledního neformátovaného vstupu.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet extrakcí.

### <a name="remarks"></a>Poznámky

Použijte [basic_istream::get](#get) ke čtení neformátovaných znaků.

### <a name="example"></a>Příklad

```cpp
// basic_istream_gcount.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   cout << "Type the letter 'a': ";

   ws( cin );
   char c[10];

   cin.get( &c[0],9 );
   cout << c << endl;

   cout << cin.gcount( ) << endl;
}
```

```Input
a
```

```Output
Type the letter 'a': a
1
```

## <a name="basic_istreamget"></a><a name="get"></a>basic_istream::získat

Přečte jeden nebo více znaků ze vstupního datového proudu.

```cpp
int_type get();

basic_istream<Char_T, Tr>& get(Char_T& Ch);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count, Char_T delimiter);

basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf);
basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf, Char_T delimiter);
```

### <a name="parameters"></a>Parametry

*Počet*\
Počet znaků číst z *strbuf*.

*Oddělovač*\
Znak, který by měl ukončit čtení, pokud je zjištěna před *count*.

*Str*\
Řetězec, ve kterém chcete psát.

*Ch*\
Postava, která se musí dostat.

*strbuf (Strbuf)*\
Vyrovnávací paměť, ve které chcete zapisovat.

### <a name="return-value"></a>Návratová hodnota

Bezparametrová forma get vrátí prvek přečtený jako celé číslo nebo konec souboru. Zbývající formuláře vrátí datový proud `this`(* ).

### <a name="remarks"></a>Poznámky

První neformátovaná vstupní funkce extrahuje prvek, pokud je `rdbuf->sbumpc`to možné, jako by vrácením . V opačném `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)případě vrátí . Pokud funkce extrahuje žádný [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`prvek, volá .

Druhá funkce extrahuje `meta` [int_type](../standard-library/basic-ios-class.md#int_type) prvek stejným způsobem. Pokud `meta` se porovná `traits_type::eof`s , `setstate(failbit)`funkce volá . V opačném `traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(meta)` případě se ukládá v *Ch*. Funkce vrátí __*this__.

Třetí funkce `get(str, count, widen('\n'))`vrátí .

Čtvrtá funkce extrahuje až do `count - 1` elementů a ukládá je do pole začínající na *str*. Vždy ukládá `char_type` po všech extrahovaných prvků, které ukládá. V pořadí testování se extrakce zastaví:

- Na konci souboru.

- Poté, co funkce extrahuje prvek, který porovnává rovná *oddělovač*. V tomto případě je prvek umístěn zpět do řízené sekvence.

- Po funkci extrahuje prvky. `count - 1`

Pokud funkce extrahuje žádné `setstate(failbit)`prvky, volá . V každém případě vrátí __*this__.

Vrátí pátá `get(strbuf, widen('\n'))`funkce .

Šestá funkce extrahuje prvky a vloží je do *strbuf*. Extrakce se zastaví na konci souboru nebo na elementu, který porovnává rovno *oddělovači*, který není extrahován. Také zastaví, bez extrahování prvek v otázce, pokud vložení selže nebo vyvolá výjimku (která je zachycena, ale není znovu vyvolána). Pokud funkce extrahuje žádné `setstate(failbit)`prvky, volá . V každém případě funkce vrátí __*this__.

### <a name="example"></a>Příklad

```cpp
// basic_istream_get.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   c[0] = cin.get( );
   cin.get( c[1] );
   cin.get( &c[2],3 );
   cin.get( &c[4], 4, '7' );

   cout << c << endl;
}
```

```Output
1111
```

## <a name="basic_istreamgetline"></a><a name="getline"></a>basic_istream::getline

Získá řádek ze vstupního datového proudu.

```cpp
basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type delimiter);
```

### <a name="parameters"></a>Parametry

*Počet*\
Počet znaků číst z *strbuf*.

*Oddělovač*\
Znak, který by měl ukončit čtení, pokud je zjištěna před *count*.

*Str*\
Řetězec, ve kterém chcete psát.

### <a name="return-value"></a>Návratová hodnota

Stream (__*to__).

### <a name="remarks"></a>Poznámky

První z těchto neformátovaných `getline(str, count, widen('\n'))`vstupních funkcí vrátí .

Druhá funkce extrahuje `count - 1` až do prvků a ukládá je v poli začínající na *str*. Vždy ukládá znak ukončení řetězce po všechny extrahované prvky, které ukládá. V pořadí testování se extrakce zastaví:

- Na konci souboru.

- Poté, co funkce extrahuje prvek, který porovnává rovná *oddělovač*. V tomto případě prvek není vrácena zpět a není připojen k řízené sekvence.

- Po funkci extrahuje prvky. `count - 1`

Pokud funkce extrahuje `count - 1` žádné prvky [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`nebo prvky, volání . V každém případě vrátí __*this__.

### <a name="example"></a>Příklad

```cpp
// basic_istream_getline.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   cin.getline( &c[0], 5, '2' );
   cout << c << endl;
}
```

```Output
121
```

## <a name="basic_istreamignore"></a><a name="ignore"></a>basic_istream::ignorovat

Způsobí, že počet prvků, které mají být přeskočeny z aktuální pozice pro čtení.

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*Počet*\
Počet prvků přeskočit z aktuální pozice čtení.

*Oddělovač*\
Prvek, který, pokud došlo před `ignore` count, způsobí návrat a povolení všechny prvky po *oddělovač* číst.

### <a name="return-value"></a>Návratová hodnota

Stream (__*to__).

### <a name="remarks"></a>Poznámky

Neformátovaná vstupní funkce extrahuje až *počítat* prvky a zahodí je. Pokud *se* `numeric_limits<int>::max`však počet rovná , je považován za libovolně velký. Extrakce se zastaví brzy na `Ch` konci `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(Ch)` souboru nebo na prvek takový, který porovnává rovná *oddělovač* (který je také extrahován). Funkce vrátí __*this__.

### <a name="example"></a>Příklad

```cpp
// basic_istream_ignore.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   char chararray[10];
   cout << "Type 'abcdef': ";
   cin.ignore( 5, 'c' );
   cin >> chararray;
   cout << chararray;
}
```

```Output
Type 'abcdef': abcdef
def
```

## <a name="basic_istreamoperator"></a><a name="op_gt_gt"></a>základní\_istream::>> operátora

Volá funkci vstupního datového proudu nebo čte formátovaná data ze vstupního datového proudu.

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Char_T, Tr>& (* Pfn)(basic_ios<Char_T, Tr>&));
basic_istream& operator>>(basic_streambuf<Char_T, Tr>* strbuf);
basic_istream& operator>>(bool& val);
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

### <a name="parameters"></a>Parametry

*Pfn*\
Ukazatel funkce.

*strbuf (Strbuf)*\
Objekt typu `stream_buf`.

*Val*\
Hodnota číst z datového proudu.

### <a name="return-value"></a>Návratová hodnota

Stream (__*to__).

### <a name="remarks"></a>Poznámky

Hlavička \<> istream také definuje několik globálních operátorů extrakce. Další informace naleznete [v\<tématu operátor>> ( istream>)](../standard-library/istream-operators.md#op_gt_gt).

První členská funkce zajišťuje, že `istr >> ws` výraz [`ws`](../standard-library/istream-functions.md#ws) `(istr)`formuláře volá a potom vrátí __*this__. Druhá a třetí funkce zajišťují, že ostatní [`hex`](../standard-library/ios-functions.md#hex)manipulátory, například , se chovají podobně. Zbývající funkce jsou formátované vstupní funkce.

Funkce:

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

extrahuje prvky, pokud *strbuf* není ukazatel null, a vloží je do *strbuf*. Extrakce se zastaví na konci souboru. Také se zastaví bez extrahování dotyčného prvku, pokud vložení selže nebo vyvolá výjimku (která je zachycena, ale není znovu vyvolána). Pokud funkce extrahuje žádné [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`prvky, volá . V každém případě funkce vrátí __*this__.

Funkce:

```cpp
basic_istream& operator>>(bool& val);
```

extrahuje pole a převede ho na [`use_facet`](../standard-library/basic-filebuf-class.md#open) `< num_get<Char_T, InIt>(` [`getloc`](../standard-library/ios-base-class.md#getloc) `).` [`get`](../standard-library/ios-base-class.md#getloc) `( InIt(` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `), Init(0), *this, getloc, val)`logickou hodnotu voláním . Zde `InIt` je definovánjako [`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md) `<Char_T, Tr>`. Funkce vrátí __*this__.

Každá z funkcí:

```cpp
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
```

extrahovat pole a převést jej `use_facet<num_get<Char_T, InIt>(getloc).` [`get`](#get) `(InIt(rdbuf), Init(0), *this, getloc, val)`na číselnou hodnotu voláním . Zde `InIt` je definován `istreambuf_iterator<Char_T, Tr>`jako , a *val* má typ **dlouhý**, **nepodepsaný dlouhý**nebo **void** <strong>\*</strong> podle potřeby.

Pokud převedenou hodnotu nelze reprezentovat jako typ *val*, [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`funkce volá . V každém případě funkce vrátí __*this__.

Každá z funkcí:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

extrahovat pole a převést jej `use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)`na číselnou hodnotu voláním . Zde `InIt` je definován `istreambuf_iterator<Char_T, Tr>`jako , a *val* má typ **double** nebo **long double** podle potřeby.

Pokud převedenou hodnotu nelze reprezentovat jako typ *val*, `setstate(failbit)`funkce volá . V každém případě vrátí __*this__.

### <a name="example"></a>Příklad

```cpp
// istream_basic_istream_op_is.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_istream<char, char_traits<char> >& somefunc(basic_istream<char, char_traits<char> > &i)
{
   if ( i == cin )
   {
      cerr << "i is cin" << endl;
   }
   return i;
}

int main( )
{
   int i = 0;
   cin >> somefunc;
   cin >> i;
   cout << i << endl;
   cin >> hex2;
   cin >> i;
   cout << i << endl;
}
```

## <a name="basic_istreamoperator"></a><a name="op_eq"></a>basic_istream::operátor=

Přiřadí `basic_istream` na pravé straně operátoru k tomuto objektu. Je to úkol přesunu `rvalue` zahrnující odkaz, který nezanechává kopii.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Odkaz `rvalue` na `basic_ifstream` objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí __*this__.

### <a name="remarks"></a>Poznámky

Operátor člena `swap(right)`volá .

## <a name="basic_istreampeek"></a><a name="peek"></a>basic_istream::peek

Vrátí další znak, který má být přečten.

```cpp
int_type peek();
```

### <a name="return-value"></a>Návratová hodnota

Další znak, který bude číst.

### <a name="remarks"></a>Poznámky

Neformátovaná vstupní funkce extrahuje prvek, pokud je `rdbuf->` [`sgetc`](../standard-library/basic-streambuf-class.md#sgetc)to možné, jako by vrácením . V opačném `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)případě vrátí .

### <a name="example"></a>Příklad

```cpp
// basic_istream_peek.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;
   cout << "Type 'abcde': ";

   c2 = cin.peek( );
   cin.getline( &c[0], 9 );

   cout << c2 << " " << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
a abcde
```

## <a name="basic_istreamputback"></a><a name="putback"></a>basic_istream::putback

Vloží zadaný znak do datového proudu.

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, který chcete vložit zpět do datového proudu.

### <a name="return-value"></a>Návratová hodnota

Stream (__*to__).

### <a name="remarks"></a>Poznámky

[Neformátovaná vstupní funkce](../standard-library/basic-istream-class.md) vrátí *Ch*, pokud je [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc)to možné, jako by voláním . Pokud `rdbuf` je ukazatel null nebo pokud `sputbackc` `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)volání vrátí [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)`, funkce volá . V každém případě vrátí __*this__.

### <a name="example"></a>Příklad

```cpp
// basic_istream_putback.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2, c3;

   c2 = cin.get( );
   c3 = cin.get( );
   cin.putback( c2 );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Output
qwq
```

## <a name="basic_istreamread"></a><a name="read"></a>basic_istream::číst

Přečte zadaný počet znaků z datového proudu a uloží je do pole.

Tato metoda je potenciálně nebezpečné, protože spoléhá na volajícího zkontrolovat, že předané hodnoty jsou správné.

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Str*\
Pole, ve kterém chcete číst znaky.

*Počet*\
Počet znaků ke čtení.

### <a name="return-value"></a>Návratová hodnota

Datový proud `*this`( ).

### <a name="remarks"></a>Poznámky

Neformátovaná vstupní funkce extrahuje až *počítat* prvky a ukládá je v poli začínající na *str*. Extrakce se zastaví brzy na konci souboru, v takovém případě funkce volá [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`. V každém případě vrátí __*this__.

### <a name="example"></a>Příklad

```cpp
// basic_istream_read.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
    char c[10];
    int count = 5;

    cout << "Type 'abcde': ";

    // Note: cin::read is potentially unsafe, consider
    // using cin::_Read_s instead.
    cin.read(&c[0], count);
    c[count] = 0;

    cout << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
abcde
```

## <a name="basic_istreamreadsome"></a><a name="readsome"></a>basic_istream::readsome

Přečte zadaný počet hodnot znaků.

Tato metoda je potenciálně nebezpečné, protože spoléhá na volajícího zkontrolovat, že předané hodnoty jsou správné.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Str*\
Pole, ve `readsome` kterém jsou uloženy znaky, které čte.

*Počet*\
Počet znaků ke čtení.

### <a name="return-value"></a>Návratová hodnota

Počet skutečně přečtených [`gcount`](#gcount)znaků .

### <a name="remarks"></a>Poznámky

Tato neformátovaná vstupní funkce extrahuje až *počítat* prvky ze vstupního datového proudu a ukládá je do pole *str*.

Tato funkce nečeká na vstup. Čte všechny údaje, které jsou k dispozici.

### <a name="example"></a>Příklad

```cpp
// basic_istream_readsome.cpp
// compile with: /EHsc /W3
#include <iostream>
using namespace std;

int main( )
{
   char c[10];
   int count = 5;

   cout << "Type 'abcdefgh': ";

   // cin.read blocks until user types input.
   // Note: cin::read is potentially unsafe, consider
   // using cin::_Read_s instead.
   cin.read(&c[0], 2);

   // Note: cin::readsome is potentially unsafe, consider
   // using cin::_Readsome_s instead.
   int n = cin.readsome(&c[0], count);  // C4996
   c[n] = 0;
   cout << n << " characters read" << endl;
   cout << c << endl;
}
```

## <a name="basic_istreamseekg"></a><a name="seekg"></a>basic_istream::seekg

Přesune pozici pro čtení v datovém proudu.

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parametry

*Pos*\
Absolutní pozice, ve které chcete přesunout ukazatel pro čtení.

*vypnuto*\
Posun pro přesunutí ukazatele pro čtení vzhledem k *cestě*.

*Způsob*\
Jeden z [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) výčty.

### <a name="return-value"></a>Návratová hodnota

Stream (__*to__).

### <a name="remarks"></a>Poznámky

První členská funkce provádí absolutní hledání, druhá členská funkce provádí relativní hledání.

> [!NOTE]
> Nepoužívejte druhou člennou funkci s textovými soubory, protože standardní c++ nepodporuje relativní hledá v textových souborech.

Pokud [`fail`](../standard-library/basic-ios-class.md#fail) je false, první `newpos =` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) `(pos)`členské funkce `pos_type` volá `newpos`, pro některé dočasný objekt . Pokud `fail` je false, druhá `newpos = rdbuf->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `( off, way)`funkce volá . V obou případech, `(off_type)newpos == (off_type)(-1)` pokud (operace umístění selže), funkce volá `istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`. Obě funkce vrátí __*this__.

Pokud [`fail`](../standard-library/basic-ios-class.md#fail) je true, členské funkce neprovede nic.

### <a name="example"></a>Příklad

```cpp
// basic_istream_seekg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
   using namespace std;
   ifstream file;
   char c, c1;

   file.open( "basic_istream_seekg.txt" );
   file.seekg(2);   // seek to position 2
   file >> c;
   cout << c << endl;
}
```

## <a name="basic_istreamsentry"></a><a name="sentry"></a>basic_istream::hlídka

Vnořená třída popisuje objekt, jehož deklarace strukturuje formátované a neformátované vstupní funkce.

```cpp
class sentry {
   public:
   explicit sentry(
      basic_istream<Char_T, Tr>& _Istr,
      bool _Noskip = false);
   operator bool() const;
   };
```

### <a name="remarks"></a>Poznámky

Pokud `_Istr.` [`good`](../standard-library/basic-ios-class.md#good) je true, konstruktor:

- `_Istr.` [`tie`](../standard-library/basic-ios-class.md#tie) `->` Volání, [`flush`](../standard-library/basic-ostream-class.md#flush) pokud `_Istr.tie` není ukazatel null.

- Účinně [`ws`](../standard-library/istream-functions.md#ws) `(_Istr)` volá, `_Istr.` [`flags`](../standard-library/ios-base-class.md#flags) `&` [`skipws`](../standard-library/ios-functions.md#skipws) pokud je nenulová.

Pokud po takové `_Istr.good` přípravy, je false, konstruktor volání `_Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`. V každém případě konstruktor ukládá hodnotu vrácenou `_Istr.good` v `status`. Pozdější volání `operator bool` doručuje tuto uloženou hodnotu.

## <a name="basic_istreamswap"></a><a name="swap"></a>basic_istream::swap

Vyměňuje obsah `basic_istream` dvou objektů.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Lvalue odkaz na `basic_istream` objekt.

### <a name="remarks"></a>Poznámky

Členské funkce [`basic_ios::swap`](../standard-library/basic-ios-class.md#swap) `(right)`volá . Také vyměňuje počet extrakcí s počtem extrakcí za *právo*.

## <a name="basic_istreamsync"></a><a name="sync"></a>basic_istream::synchronizace

Synchronizuje přidružené vstupní zařízení datového proudu s vyrovnávací pamětí datového proudu.

```cpp
int sync();
```

### <a name="return-value"></a>Návratová hodnota

Pokud [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) je ukazatel null, funkce vrátí -1. V opačném `rdbuf->` [`pubsync`](../standard-library/basic-streambuf-class.md#pubsync)případě volá . Pokud toto volání vrátí -1, funkce volá [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` a vrátí -1. V opačném případě vrátí funkce nulu.

## <a name="basic_istreamtellg"></a><a name="tellg"></a>basic_istream::tellg

Hlásí aktuální pozici čtení v datovém proudu.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální pozice v datovém proudu.

### <a name="remarks"></a>Poznámky

Pokud [`fail`](../standard-library/basic-ios-class.md#fail) je false, vrátí [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `(0, cur, in)`členská funkce . V opačném `pos_type(-1)`případě vrátí .

### <a name="example"></a>Příklad

```cpp
// basic_istream_tellg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;
    ifstream file;
    char c;
    streamoff i;

    file.open("basic_istream_tellg.txt");
    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;

    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;
}
```

## <a name="basic_istreamunget"></a><a name="unget"></a>basic_istream::unget

Vloží naposledy přečtený znak zpět do datového proudu.

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>Návratová hodnota

Stream (__*to__).

### <a name="remarks"></a>Poznámky

[Neformátovaná vstupní funkce](../standard-library/basic-istream-class.md) vrátí předchozí prvek v datovém proudu, `rdbuf->` [`sungetc`](../standard-library/basic-streambuf-class.md#sungetc)pokud je to možné, jako by voláním . Pokud [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) je ukazatel null nebo pokud `sungetc` `traits_type::` [`eof`](../standard-library/basic-ios-class.md#eof)volání vrátí [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)`, funkce volá . V každém případě vrátí __*this__.

Informace o `unget` tom, jak [`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc)může selhat, naleznete v tématu .

### <a name="example"></a>Příklad

```cpp
// basic_istream_unget.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;

   cout << "Type 'abc': ";
   c2 = cin.get( );
   cin.unget( );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Input
abc
```

```Output
Type 'abc': abc
abc
```

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
