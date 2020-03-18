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
ms.openlocfilehash: 68c7f7ffa9c32c16654e57c8249348d74cc83a5b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416919"
---
# <a name="basic_istream-class"></a>basic_istream – třída

Popisuje objekt, který ovládá extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu pomocí prvků typu `Char_T`, označovaného také jako [char_type](../standard-library/basic-ios-class.md#char_type), jejichž znakové vlastnosti jsou určeny třídou *TR*, označovanou také jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_istream : virtual public basic_ios<Char_T, Tr>
```

## <a name="remarks"></a>Poznámky

Většina členských funkcí, které přetěžování [operátor > >](#op_gt_gt) jsou formátované vstupní funkce. Postupuje podle vzoru:

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

Mnoho dalších členských funkcí je neformátované vstupní funkce. Postupuje podle vzoru:

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

Obě skupiny funkcí volají [`setstate`](../standard-library/basic-ios-class.md#setstate)`(eofbit)`, pokud při extrakci prvků narazí na konec souboru.

Objekt třídy `basic_istream<Char_T, Tr>` ukládá:

- Virtuální veřejný objekt třídy [`basic_ios`](../standard-library/basic-ios-class.md)`<Char_T, Tr>`.

- Počet extrakcí poslední neformátované operace vstupu (s názvem `count` v předchozím kódu).

## <a name="example"></a>Příklad

Další informace o vstupních streamech najdete v příkladu [Basic_ifstream třídy](../standard-library/basic-ifstream-class.md) .

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_istream](#basic_istream)|Vytvoří objekt typu `basic_istream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[gcount](#gcount)|Vrátí počet čtených znaků během posledního neformátovaného vstupu.|
|[get](#get)|Přečte jeden nebo více znaků ze vstupního datového proudu.|
|[getline](#getline)|Přečte řádek ze vstupního streamu.|
|[ohled](#ignore)|Způsobí, že se z aktuální pozice pro čtení přeskočí počet prvků.|
|[prohlížet](#peek)|Vrátí další znak, který se má přečíst.|
|[putback](#putback)|Vloží zadaný znak do datového proudu.|
|[read](#read)|Přečte zadaný počet znaků z datového proudu a uloží je do pole.|
|[readsome](#readsome)|Čtení z vyrovnávací paměti.|
|[seekg](#seekg)|Přesune pozici pro čtení v datovém proudu.|
|[Ukázka](#sentry)|Vnořená Třída popisuje objekt, jehož deklarace strukturuje formátované vstupní funkce a neformátované vstupní funkce.|
|[adresu](#swap)|Vyměňuje tento objekt `basic_istream` pro zadaný parametr `basic_istream` objektu.|
|[brání](#sync)|Synchronizuje přiřazené vstupní zařízení datového proudu s vyrovnávací pamětí streamu.|
|[tellg](#tellg)|Oznamuje aktuální pozici pro čtení v datovém proudu.|
|[unget](#unget)|Vloží poslední přečtený znak zpět do datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor > >](#op_gt_gt)|Volá funkci na vstupním streamu nebo čte formátovaná data ze vstupního datového proudu.|
|[operátor =](#op_eq)|Přiřadí `basic_istream` na pravé straně operátoru tomuto objektu. Jedná se o přiřazení přesunutí zahrnující `rvalue` odkaz, který nenechává kopii na pozadí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<IStream >

**Obor názvů:** std

## <a name="basic_istream"></a>basic_istream:: basic_istream

Vytvoří objekt typu `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Char_T, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*strbuf*\
Objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**true** , pokud se jedná o standardní datový proud; v opačném případě **false**.

*pravé*\
Objekt `basic_istream` ke zkopírování.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [`init`](../standard-library/basic-ios-class.md#init)`(strbuf)`. Také v počtu extrakce ukládá nula. Další informace o tomto počtu extrakcí naleznete v části poznámky v přehledu [třídy basic_istream](../standard-library/basic-istream-class.md) .

Druhý konstruktor inicializuje základní třídu voláním `move(right)`. Také ukládá `right.gcount()` v počtu extrakcí a v počtu extrakce v případě * Right * * ukládá nula.

### <a name="example"></a>Příklad

Další informace o vstupních streamech najdete v příkladu pro [basic_ifstream:: basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) .

## <a name="gcount"></a>basic_istream:: gcount

Vrátí počet čtených znaků během posledního neformátovaného vstupu.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet extrakcí.

### <a name="remarks"></a>Poznámky

Použijte [basic_istream:: Get](#get) ke čtení neformátovaných znaků.

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

## <a name="get"></a>basic_istream:: Get

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

*počet*\
Počet znaků, které mají být načteny z *strbuf*.

\ *oddělovače*
Znak, který má ukončit čtení, pokud byl zjištěn před *počtem*.

\ *str*
Řetězec, do kterého se má zapisovat.

*Ch*\
Znak, který se má načíst

*strbuf*\
Vyrovnávací paměť, do které se má zapisovat.

### <a name="return-value"></a>Návratová hodnota

Bezparametrový typ Get vrací prvek čten jako celé číslo nebo konec souboru. Zbývající formuláře vrátí datový proud (* `this`).

### <a name="remarks"></a>Poznámky

První neformátovaná vstupní funkce extrahuje prvek, pokud je to možné, jako kdybyste vrátili `rdbuf->sbumpc`. V opačném případě vrátí `traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof). Pokud funkce extrahuje žádný prvek, volá [`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`.

Druhá funkce extrahuje prvek [int_type](../standard-library/basic-ios-class.md#int_type) `meta` stejným způsobem. Pokud se `meta` porovnává jako `traits_type::eof`, funkce volá `setstate(failbit)`. V opačném případě ukládá `traits_type::`[`to_char_type`](../standard-library/char-traits-struct.md#to_char_type)`(meta)` v *ch*. Funkce vrátí hodnotu __* This__.

Třetí funkce vrátí `get(str, count, widen('\n'))`.

Čtvrtá funkce extrahuje až `count - 1` prvky a uloží je do pole, které začíná na *str*. Vždy ukládá `char_type` po všech extrahovaných prvcích, které ukládá. V pořadí testování se zastaví extrakce:

- Na konci souboru.

- Poté, co funkce extrahuje prvek, který se porovná s *oddělovačem*. V tomto případě je element vrácen do kontrolované sekvence.

- Poté, co funkce získá `count - 1` prvky.

Pokud funkce neextrahuje žádné prvky, volá `setstate(failbit)`. V každém případě vrátí __* This__.

Pátá funkce vrací `get(strbuf, widen('\n'))`.

Šestá funkce extrahuje prvky a vloží je do *strbuf*. Extrakce se zastaví na konci souboru nebo na elementu, který porovnává stejný *oddělovač*, který není extrahován. Také se zastaví, aniž by došlo k extrakci daného elementu, pokud vložení neuspěje nebo vyvolá výjimku (která je zachycena, ale nebyla znovu vyvolána). Pokud funkce neextrahuje žádné prvky, volá `setstate(failbit)`. V každém případě funkce vrátí __* This__.

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

## <a name="getline"></a>basic_istream:: getline

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

*počet*\
Počet znaků, které mají být načteny z *strbuf*.

\ *oddělovače*
Znak, který má ukončit čtení, pokud byl zjištěn před *počtem*.

\ *str*
Řetězec, do kterého se má zapisovat.

### <a name="return-value"></a>Návratová hodnota

Datový proud ( __* This__).

### <a name="remarks"></a>Poznámky

První z těchto neformátovaných vstupních funkcí vrátí `getline(str, count, widen('\n'))`.

Druhá funkce extrahuje až `count - 1` prvky a ukládá je do pole, které začíná na *str*. Vždy ukládá znak ukončení řetězce po všech extrahovaných prvcích, které ukládá. V pořadí testování se zastaví extrakce:

- Na konci souboru.

- Poté, co funkce extrahuje prvek, který se porovná s *oddělovačem*. V tomto případě se element nevrátí a není připojený k řízené sekvenci.

- Poté, co funkce získá `count - 1` prvky.

Pokud funkce extrahuje žádné elementy nebo prvky `count - 1`, volá [`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. V každém případě vrátí __* This__.

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

## <a name="ignore"></a>basic_istream:: ignore

Způsobí, že se z aktuální pozice pro čtení přeskočí počet prvků.

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*počet*\
Počet prvků, které se mají přeskočit z aktuální pozice pro čtení.

\ *oddělovače*
Element, který, pokud byl zjištěn před počtem, způsobí, že `ignore` vrátí a povolí čtení všech prvků po *oddělovači* .

### <a name="return-value"></a>Návratová hodnota

Datový proud ( __* This__).

### <a name="remarks"></a>Poznámky

Neformátovaná vstupní funkce extrahuje až do *počtu* prvků a zahodí je. Pokud se *počet* rovná `numeric_limits<int>::max`je však pořízen jako libovolně velký. Extrakce se zastaví na konci souboru nebo na elementu `Ch` tak, že `traits_type::`[`to_int_type`](../standard-library/char-traits-struct.md#to_int_type)`(Ch)` porovná s *oddělovačem* (který se také extrahuje). Funkce vrátí hodnotu __* This__.

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

## <a name="op_gt_gt"></a>základní\_IStream:: operator > >

Volá funkci na vstupním streamu nebo čte formátovaná data ze vstupního datového proudu.

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
Ukazatel na funkci.

*strbuf*\
Objekt typu `stream_buf`.

\ *Val*
Hodnota, která má být načtena z datového proudu.

### <a name="return-value"></a>Návratová hodnota

Datový proud ( __* This__).

### <a name="remarks"></a>Poznámky

Záhlaví > \<IStream definuje také několik globálních operátorů extrakce. Další informace najdete v tématu [operátor > > (\<istream >)](../standard-library/istream-operators.md#op_gt_gt).

První členská funkce zajišťuje, že výraz formuláře `istr >> ws` volá [`ws`](../standard-library/istream-functions.md#ws)`(istr)`a vrátí hodnotu __* This__. Druhá a třetí funkce zajišťují, aby se podobným způsobem chovaly i další manipulace, například [`hex`](../standard-library/ios-functions.md#hex). Zbývající funkce jsou formátované vstupní funkce.

Funkce:

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

extrahuje prvky, pokud *strbuf* není ukazatel s hodnotou null a vloží je do *strbuf*. Extrakce se zastaví na konci souboru. Také se zastaví bez extrakce prvku, pokud vložení neuspěje nebo vyvolá výjimku (která je zachycena, ale nebyla znovu vyvolána). Pokud funkce neextrahuje žádné prvky, volá [`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. V každém případě funkce vrátí __* This__.

Funkce:

```cpp
basic_istream& operator>>(bool& val);
```

extrahuje pole a převede ho na logickou hodnotu voláním [`use_facet`](../standard-library/basic-filebuf-class.md#open)`< num_get<Char_T, InIt>(`[`getloc`](../standard-library/ios-base-class.md#getloc)`).`[`get`](../standard-library/ios-base-class.md#getloc)`( InIt(`[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)`), Init(0), *this, getloc, val)`. Zde je `InIt` definováno jako [`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md)`<Char_T, Tr>`. Funkce vrátí hodnotu __* This__.

Každá z těchto funkcí:

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

Rozbalte pole a převeďte jej na číselnou hodnotu voláním `use_facet<num_get<Char_T, InIt>(getloc).`[`get`](#get)`(InIt(rdbuf), Init(0), *this, getloc, val)`. Zde je `InIt` definován jako `istreambuf_iterator<Char_T, Tr>`a hodnota *Val* má podle potřeby typ **Long**, **unsigned long**nebo **void** <strong>\*</strong> .

Pokud převedená hodnota nemůže být reprezentována jako typ *Val*, funkce volá [`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. V každém případě funkce vrátí __* This__.

Každá z těchto funkcí:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

Rozbalte pole a převeďte jej na číselnou hodnotu voláním `use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)`. Zde je `InIt` definováno jako `istreambuf_iterator<Char_T, Tr>`a *Val* má podle potřeby typ **Double** nebo **Long Double** .

Pokud převedená hodnota nemůže být reprezentována jako typ *Val*, funkce volá `setstate(failbit)`. V každém případě vrátí __* This__.

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

## <a name="op_eq"></a>basic_istream:: operator =

Přiřadí `basic_istream` na pravé straně operátoru tomuto objektu. Jedná se o přiřazení přesunutí zahrnující `rvalue` odkaz, který nenechává kopii na pozadí.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
`rvalue` odkaz na objekt `basic_ifstream`.

### <a name="return-value"></a>Návratová hodnota

Vrátí __* This__.

### <a name="remarks"></a>Poznámky

Operátor členu volá `swap(right)`.

## <a name="peek"></a>basic_istream::p EEK

Vrátí další znak, který se má přečíst.

```cpp
int_type peek();
```

### <a name="return-value"></a>Návratová hodnota

Další znak, který bude načten.

### <a name="remarks"></a>Poznámky

Neformátovaná vstupní funkce extrahuje element, pokud je to možné, jako if vrácením `rdbuf->`[`sgetc`](../standard-library/basic-streambuf-class.md#sgetc). V opačném případě vrátí `traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof).

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

## <a name="putback"></a>basic_istream::p utback

Vloží zadaný znak do datového proudu.

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, který se má vrátit do proudu.

### <a name="return-value"></a>Návratová hodnota

Datový proud ( __* This__).

### <a name="remarks"></a>Poznámky

[Funkce unformátovaného vstupu](../standard-library/basic-istream-class.md) vrací back *-ch*, pokud je to možné, jako if voláním [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)`->`[`sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc). Pokud je `rdbuf` ukazatel s hodnotou null, nebo pokud volání `sputbackc` vrátí `traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof), funkce volá [`setstate`](../standard-library/basic-ios-class.md#setstate)`(badbit)`. V každém případě vrátí __* This__.

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

## <a name="read"></a>basic_istream:: Read

Přečte zadaný počet znaků z datového proudu a uloží je do pole.

Tato metoda je potenciálně nebezpečná, protože spoléhá volajícího na kontrolu správnosti předaných hodnot.

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

\ *str*
Pole, ve kterém se mají číst znaky

*počet*\
Počet znaků, které mají být čteny.

### <a name="return-value"></a>Návratová hodnota

Datový proud (`*this`).

### <a name="remarks"></a>Poznámky

Neformátovaná vstupní funkce extrahuje až do *počtu* prvků a ukládá je do pole, které začíná na *str*. Extrakce se ukončí na konci souboru. v takovém případě funkce volá [`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. V každém případě vrátí __* This__.

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

## <a name="readsome"></a>basic_istream:: readsome

Přečte zadaný počet znakových hodnot.

Tato metoda je potenciálně nebezpečná, protože spoléhá volajícího na kontrolu správnosti předaných hodnot.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

\ *str*
Pole, ve kterém `readsome` ukládá znaky, které čte.

*počet*\
Počet znaků, které mají být čteny.

### <a name="return-value"></a>Návratová hodnota

Počet znaků, které jsou ve skutečnosti čteny, [`gcount`](#gcount).

### <a name="remarks"></a>Poznámky

Tato neformátovaná vstupní funkce extrahuje *Celkový počet* prvků ze vstupního datového proudu a ukládá je do pole *str*.

Tato funkce nečeká na vstup. Čte všechna data, která jsou k dispozici.

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

## <a name="seekg"></a>basic_istream:: seekg

Přesune pozici pro čtení v datovém proudu.

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parametry

\ *POS*
Absolutní pozice, ve které má být ukazatel pro čtení přesunut.

*vypnuto*\
Posun pro přesunutí ukazatele pro čtení relativně k *cestě*.

*způsob*\
Jeden z [ios_base výčet:: seekdir](../standard-library/ios-base-class.md#seekdir) .

### <a name="return-value"></a>Návratová hodnota

Datový proud ( __* This__).

### <a name="remarks"></a>Poznámky

První členská funkce provede absolutní hledání, druhá členská funkce provede relativní hledání.

> [!NOTE]
> Nepoužívejte druhou členskou funkci s textovými soubory, protože standard C++ nepodporuje relativní hledání v textových souborech.

Pokud je [`fail`](../standard-library/basic-ios-class.md#fail) false, První členská funkce volá `newpos = `[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)`->`[`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)`(pos)`pro některý `pos_type` dočasný objekt `newpos`. Pokud je `fail` false, druhá funkce volá `newpos = rdbuf->`[`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff)`( off, way)`. V obou případech, pokud `(off_type)newpos == (off_type)(-1)` (operace umístění selhává), funkce volá `istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. Obě funkce vrátí __* This__.

Pokud je [`fail`](../standard-library/basic-ios-class.md#fail) true, členské funkce nedělají nic.

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

## <a name="sentry"></a>basic_istream:: Sentry

Vnořená Třída popisuje objekt, jehož deklarace strukturuje formátované a neformátované vstupní funkce.

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

Pokud je `_Istr.`[`good`](../standard-library/basic-ios-class.md#good) true, konstruktor:

- Volá `_Istr.`[`tie`](../standard-library/basic-ios-class.md#tie)`->`[`flush`](../standard-library/basic-ostream-class.md#flush) Pokud `_Istr.tie` není ukazatel s hodnotou null.

- Efektivně volá [`ws`](../standard-library/istream-functions.md#ws)`(_Istr)`, pokud `_Istr.`[`flags`](../standard-library/ios-base-class.md#flags)` & `[`skipws`](../standard-library/ios-functions.md#skipws) není nula.

Pokud je po každé takové přípravě `_Istr.good` false, volá konstruktor `_Istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. V každém případě konstruktor ukládá hodnotu vrácenou `_Istr.good` v `status`. Pozdější volání `operator bool` doručuje tuto uloženou hodnotu.

## <a name="swap"></a>basic_istream:: swap

Vyměňuje obsah dvou `basic_istream` objektů.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Odkaz l-hodnoty na objekt `basic_istream`.

### <a name="remarks"></a>Poznámky

Členská funkce volá [`basic_ios::swap`](../standard-library/basic-ios-class.md#swap)`(right)`. Také vyměňuje počet extrakcí s počtem extrakce *vpravo*.

## <a name="sync"></a>basic_istream:: Sync

Synchronizuje přiřazené vstupní zařízení datového proudu s vyrovnávací pamětí streamu.

```cpp
int sync();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) ukazatel s hodnotou null, funkce vrátí hodnotu-1. V opačném případě volá `rdbuf->`[`pubsync`](../standard-library/basic-streambuf-class.md#pubsync). Pokud volání vrátí hodnotu-1, funkce volá [`setstate`](../standard-library/basic-ios-class.md#setstate)`(badbit)` a vrátí-1. V opačném případě vrátí funkce hodnotu nula.

## <a name="tellg"></a>basic_istream:: tellg

Oznamuje aktuální pozici pro čtení v datovém proudu.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální pozice v datovém proudu.

### <a name="remarks"></a>Poznámky

Pokud je [`fail`](../standard-library/basic-ios-class.md#fail) false, vrátí členská funkce [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)`->`[`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff)`(0, cur, in)`. V opačném případě vrátí `pos_type(-1)`.

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

## <a name="unget"></a>basic_istream:: unget

Vloží poslední přečtený znak zpět do datového proudu.

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>Návratová hodnota

Datový proud ( __* This__).

### <a name="remarks"></a>Poznámky

[Funkce unformátovalal Input](../standard-library/basic-istream-class.md) vrátí předchozí prvek v datovém proudu, pokud je to možné, jako if voláním `rdbuf->`[`sungetc`](../standard-library/basic-streambuf-class.md#sungetc). Pokud je [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) ukazatel s hodnotou null, nebo pokud volání `sungetc` vrátí `traits_type::`[`eof`](../standard-library/basic-ios-class.md#eof), funkce volá [`setstate`](../standard-library/basic-ios-class.md#setstate)`(badbit)`. V každém případě vrátí __* This__.

Informace o tom, jak `unget` může selhat, najdete v tématu [`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc).

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

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream – programování](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
