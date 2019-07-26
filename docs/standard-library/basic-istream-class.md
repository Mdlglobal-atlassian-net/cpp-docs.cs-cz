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
ms.openlocfilehash: d1a76e9c639ac56ca693527543ecff5c597456f0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452556"
---
# <a name="basicistream-class"></a>basic_istream – třída

Popisuje objekt, který ovládá extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu pomocí prvků `Elem`typu, označovaného také jako [char_type](../standard-library/basic-ios-class.md#char_type), jejichž vlastnosti znaků jsou určeny třídou *TR*, označovanou také jako [traits_. Zadejte](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_istream : virtual public basic_ios<Elem, Tr>
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

Obě skupiny funkcí volají [setstate](../standard-library/basic-ios-class.md#setstate)(`eofbit`), pokud při extrakci prvků narazí na konec souboru.

`basic_istream`Objekt třídy < TR>ukládá : `Elem`

- Virtuální veřejný objekt základní třídy [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, *TR*> `.`

- Počet extrakcí poslední neformátované operace vstupu (volána `count` v předchozím kódu).

## <a name="example"></a>Příklad

Další informace o vstupních streamech najdete v příkladu pro [třídu basic_ifstream](../standard-library/basic-ifstream-class.md) .

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
|[ignore](#ignore)|Způsobí, že se z aktuální pozice pro čtení přeskočí počet prvků.|
|[prohlížet](#peek)|Vrátí další znak, který se má přečíst.|
|[putback](#putback)|Vloží zadaný znak do datového proudu.|
|[read](#read)|Přečte zadaný počet znaků z datového proudu a uloží je do pole.|
|[readsome](#readsome)|Čtení z vyrovnávací paměti.|
|[seekg](#seekg)|Přesune pozici pro čtení v datovém proudu.|
|[Ukázka](#sentry)|Vnořená Třída popisuje objekt, jehož deklarace strukturuje formátované vstupní funkce a neformátované vstupní funkce.|
|[swap](#swap)|Vyměňuje `basic_istream` tento objekt pro zadaný `basic_istream` parametr objektu.|
|[sync](#sync)|Synchronizuje vstupní zařízení přidružené ke streamu s vyrovnávací pamětí streamu.|
|[tellg](#tellg)|Oznamuje aktuální pozici pro čtení v datovém proudu.|
|[unget](#unget)|Vloží poslední přečtený znak zpět do datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor > >](#op_gt_gt)|Volá funkci na vstupním streamu nebo čte formátovaná data ze vstupního datového proudu.|
|[operátor =](#op_eq)|Přiřadí k tomuto objektu napravéstraněoperátora.`basic_istream` Toto je přiřazení přesunutí zahrnující `rvalue` odkaz, který neopouští kopii.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<IStream >

**Obor názvů:** std

## <a name="basic_istream"></a>basic_istream::basic_istream

Vytvoří objekt typu `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*strbuf*\
Objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**true** , pokud se jedná o standardní datový proud; v opačném případě **false**.

*Kliknutím*\
`basic_istream` Objekt ke zkopírování.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním metody [init](../standard-library/basic-ios-class.md#init)(_s `trbuf`). Také v počtu extrakce ukládá nula. Další informace o tomto počtu extrakcí naleznete v části poznámky v tématu Přehled [třídy basic_istream](../standard-library/basic-istream-class.md) .

Druhý konstruktor inicializuje základní třídu voláním metody `move( right)`. Také ukládá _r `ight.gcount()` do počtu extrakcí a v počtu extrakce pro _r `ight`ukládá nula.

### <a name="example"></a>Příklad

Další informace o vstupních streamech najdete v příkladu pro [basic_ifstream:: basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) .

## <a name="gcount"></a>basic_istream::gcount

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

basic_istream<Elem, Tr>& get(Elem& Ch);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count, Elem Delim);

basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf);
basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf, Elem Delim);
```

### <a name="parameters"></a>Parametry

*výpočtu*\
Počet znaků, ze `strbuf`kterých se má číst.

*Delim*\
Znak, který má ukončit čtení, pokud je zjištěn před *počtem*.

*str*\
Řetězec, do kterého se má zapisovat.

*Zvolte*\
Znak, který se má načíst

*strbuf*\
Vyrovnávací paměť, do které se má zapisovat.

### <a name="return-value"></a>Návratová hodnota

Bezparametrový typ Get vrací prvek čten jako celé číslo nebo konec souboru. Zbývající formuláře vrátí datový proud (* `this`).

### <a name="remarks"></a>Poznámky

První z těchto neformátovaných vstupních funkcí extrahuje element, pokud je to možné, jako kdybyste `rdbuf`vrátili ->  `sbumpc`. V opačném případě vrátí **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof). Pokud funkce extrahuje žádný prvek, volá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

Druhá funkce extrahuje `meta` element [int_type](../standard-library/basic-ios-class.md#int_type) stejným způsobem. Pokud `meta` porovná hodnotu **traits_type:: EOF**, funkce volá `setstate`( **failbit**). V opačném případě ukládá **traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( `meta`) `Ch`v. Funkce vrátí  **\*tuto**hodnotu.

Třetí funkce vrátí **Get**(_ *str*, `count`, `widen`(' \ **n**')).

Čtvrtá funkce extrahuje až do *počtu* 1 prvků a ukládá je v poli začínajícím na _ *str*. Vždycky ukládá `char_type` po všech extrahovaných prvcích, které ukládá. V pořadí testování se zastaví extrakce:

- Na konci souboru.

- Poté, co funkce extrahuje prvek, který se porovná s *delim*, v takovém případě se element vrátí do kontrolované sekvence.

- Poté, co funkce extrahuje prvky *Count* -1.

Pokud funkce extrahuje žádné elementy, volá `setstate`( **failbit**). V každém případě  **\*to vrátí.**

Pátá funkce vrátí **Get**( **strbuf**, `widen`(' \ **n**')).

Šestá funkce extrahuje prvky a vloží je `strbuf`do. Extrakce se zastaví na konci souboru nebo na elementu, který porovná hodnotu _ *delim,* která není extrahována. Také se zastaví, aniž by došlo k extrakci daného elementu, pokud vložení neuspěje nebo vyvolá výjimku (která je zachycena, ale nebyla znovu vyvolána). Pokud funkce extrahuje žádné elementy, volá `setstate`( **failbit**). V každém případě funkce  **\*to**vrací.

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
basic_istream<Elem, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Elem, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type Delim);
```

### <a name="parameters"></a>Parametry

*výpočtu*\
Počet znaků, ze `strbuf`kterých se má číst.

*Delim*\
Znak, který má ukončit čtení, pokud je zjištěn před *počtem*.

*str*\
Řetězec, do kterého se má zapisovat.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*this**).

### <a name="remarks"></a>Poznámky

První z těchto neformátovaných vstupních funkcí vrátí **getline**(_ *str*, `count`, `widen`(' `\` **n**')).

Druhá funkce extrahuje až do *počtu* 1 prvků a ukládá je v poli začínajícím na _ *str*. Vždy ukládá znak ukončení řetězce po všech extrahovaných prvcích, které ukládá. V pořadí testování se zastaví extrakce:

- Na konci souboru.

- Poté, co funkce extrahuje prvek, který porovnává hodnotu *delim*, v takovém případě element není ani vrácen zpět ani připojen ke řízené sekvenci.

- Poté, co funkce extrahuje prvky *Count* -1.

Pokud funkce extrahuje žádné elementy nebo *počet* prvků-1, volá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). V každém případě  **\*to vrátí.**

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
basic_istream<Elem, Tr>& ignore(
    streamsize count = 1,
    int_type Delim = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*výpočtu*\
Počet prvků, které se mají přeskočit z aktuální pozice pro čtení.

*Delim*\
Element, který, pokud byl zjištěn před počtem, `ignore` způsobuje vrácení a povolení všech prvků po *delim* čtení.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*this**).

### <a name="remarks"></a>Poznámky

Neformátovaná vstupní funkce extrahuje až do *počtu* prvků a zahodí je. Pokud se *počet* rovná **numeric_limits\<int >:: max**, je však pořízena jako libovolně velká. Extrakce se zastaví `Ch` na konci souboru nebo na element tak, aby se **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `Ch`) porovnaly jako *delim* (což je také extrakce). Funkce vrátí  **\*tuto**hodnotu.

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

## <a name="op_gt_gt"></a>Basic\_IStream:: operator > >

Volá funkci na vstupním streamu nebo čte formátovaná data ze vstupního datového proudu.

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));
basic_istream& operator>>(basic_streambuf<Elem, Tr>* strbuf);
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

*PFN*\
Ukazatel na funkci.

*strbuf*\
Objekt typu `stream_buf`.

*počítává*\
Hodnota, která má být načtena z datového proudu.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*this**).

### <a name="remarks"></a>Poznámky

Hlavička \<> IStream také definuje několik globálních operátorů extrakce. Další informace najdete v tématu [operátor > > (\<IStream >)](../standard-library/istream-operators.md#op_gt_gt).

První členská funkce zajišťuje, že výraz ve formátu **ISTR**  >>  `ws` volá [WS](../standard-library/istream-functions.md#ws)( **ISTR**) a pak  **\*ho vrátí.** Druhá a třetí funkce zajišťují, aby se podobným způsobem chovali další manipulace, například [hex](../standard-library/ios-functions.md#hex). Zbývající funkce tvoří formátované vstupní funkce.

Funkce:

```cpp
basic_istream& operator>>(
    basic_streambuf<Elem, Tr>* strbuf);
```

extrahuje prvky, pokud _ *strbuf* není ukazatel s hodnotou null a vloží je do *strbuf*. Extrakce se zastaví na konci souboru. Také se zastaví bez extrakce prvku, pokud vložení neuspěje nebo vyvolá výjimku (která je zachycena, ale nebyla znovu vyvolána). Pokud funkce extrahuje žádné prvky, volá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). V každém případě funkce  **\*to**vrací.

Funkce:

```cpp
basic_istream& operator>>(bool& val);
```

extrahuje pole a převede ho na logickou hodnotu voláním [use_facet](../standard-library/basic-filebuf-class.md#open)  <  `num_get` \< **elem**, **init**> ( [getloc](../standard-library/ios-base-class.md#getloc)). [získat](../standard-library/ios-base-class.md#getloc) ( **Init**( [rdbuf](../standard-library/basic-ios-class.md#rdbuf)); `Init`(0)  **\*; this**, `getloc`, `val`). V tomto příkladu je **init** definováno jako [istreambuf_iterator](../standard-library/istreambuf-iterator-class.md) \< **elem**, **TR**>. Funkce vrátí  **\*tuto**hodnotu.

Funkce:

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

Každý extrahuje pole a převede ho na číselnou `use_facet` hodnotu voláním `num_get` <  \< **elem**, **init**> ( `getloc`). [získat](#get) ( **Init**( `rdbuf`); `Init`(0),  **\*this**, `getloc`, `val`). V tomto příkladu je **init** definováno `istreambuf_iterator` jako \< **elem**, **TR**> a `val` má typu **Long**, **unsigned long**nebo **void** <strong>\*</strong> podle potřeby.

Pokud převedená hodnota nemůže být reprezentována jako `val`typ, funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). V každém případě funkce  **\*to**vrací.

Funkce:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

Každý extrahuje pole a převede ho na číselnou `use_facet` hodnotu voláním `num_get` <  \< **elem**, **init**> ( `getloc`). **získat** ( **Init**( `rdbuf`); `Init`(0),  **\*this**, `getloc`, `val`). `istreambuf_iterator`  `val`    Zde je definován jako \< elem, TR > a v případě potřeby má typ Double nebo long double. `InIt`

Pokud převedená hodnota nemůže být reprezentována jako `val`typ, volání `setstate`funkce ( **failbit**). V každém případě  **\*to vrátí.**

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

Přiřadí k tomuto objektu napravéstraněoperátora.`basic_istream` Toto je přiřazení přesunutí zahrnující `rvalue` odkaz, který neopouští kopii.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
`rvalue` Odkaz`basic_ifstream` na objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí * this.

### <a name="remarks"></a>Poznámky

Operátor členu volá swap `( right)`.

## <a name="peek"></a>basic_istream::p EEK

Vrátí další znak, který se má přečíst.

```cpp
int_type peek();
```

### <a name="return-value"></a>Návratová hodnota

Další znak, který bude načten.

### <a name="remarks"></a>Poznámky

Neformátovaná vstupní funkce extrahuje element, pokud je to možné, jako kdybyste `rdbuf`vrátili  ->  [sgetc –](../standard-library/basic-streambuf-class.md#sgetc). V opačném případě vrátí **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof).

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
basic_istream<Elem, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Parametry

*Zvolte*\
Znak, který se má vrátit do proudu.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*this**).

### <a name="remarks"></a>Poznámky

Neformátovaná [Vstupní funkce](../standard-library/basic-istream-class.md) vrátí back- *ch*, pokud je to možné, jako if voláním [rdbuf](../standard-library/basic-ios-class.md#rdbuf)`->`[sputbackc](../standard-library/basic-streambuf-class.md#sputbackc). Pokud je rdbuf ukazatel s hodnotou null, nebo pokud `sputbackc` volání vrátí **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)(`badbit`). V každém případě  **\*to vrátí.**

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
basic_istream<Elem, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*str*\
Pole, ve kterém se mají číst znaky

*výpočtu*\
Počet znaků, které mají být čteny.

### <a name="return-value"></a>Návratová hodnota

Datový proud ( `*this`).

### <a name="remarks"></a>Poznámky

Neformátovaná vstupní funkce extrahuje až do *počtu* prvků a ukládá je v poli začínajícím _ `Str`. Extrakce se ukončí na konci souboru. v takovém případě funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). V každém případě vrátí `*this`.

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

## <a name="readsome"></a>basic_istream::readsome

Přečte zadaný počet znakových hodnot.

Tato metoda je potenciálně nebezpečná, protože spoléhá volajícího na kontrolu správnosti předaných hodnot.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*str*\
Pole, ve kterém `readsome` jsou uloženy znaky, které čte.

*výpočtu*\
Počet znaků, které mají být čteny.

### <a name="return-value"></a>Návratová hodnota

Počet znaků, které jsou ve skutečnosti čteny, [gcount](#gcount).

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

## <a name="seekg"></a>  basic_istream::seekg

Přesune pozici pro čtení v datovém proudu.

```cpp
basic_istream<Elem, Tr>& seekg(pos_type pos);

basic_istream<Elem, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parametry

*POS*\
Absolutní pozice, ve které má být ukazatel pro čtení přesunut.

*zaokrouhl*\
Posun pro přesunutí ukazatele pro čtení relativně k *cestě*.

*Podobně*\
Jeden z výčtů [ios_base:: seekdir](../standard-library/ios-base-class.md#seekdir) .

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*this**).

### <a name="remarks"></a>Poznámky

První členská funkce provede absolutní hledání, druhá členská funkce provede relativní hledání.

> [!NOTE]
> Nepoužívejte druhou členskou funkci s textovými soubory, protože standard C++ nepodporuje relativní hledání v textových souborech.

Pokud je [selhání](../standard-library/basic-ios-class.md#fail) false, První členská funkce volá **newpos** = [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)( `pos`) pro nějaký `pos_type` dočasný objekt `newpos`. Pokud `fail` je hodnota false, druhá funkce volá **newpos** = **rdbuf** -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)( `off`, `way`). V obou případech, pokud ( `off_type`) **newpos** = = ( `off_type`) (-1) (operace umístění se nezdařila), volání `istr`funkce. [setstate](../standard-library/basic-ios-class.md#setstate) (`failbit`). Obě funkce  **\*to**vrací.

Pokud je [Chyba](../standard-library/basic-ios-class.md#fail) pravdivá, členské funkce nedělají nic.

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

Třída Sentry {Public: Explicit Sentry (basic_istream\<elem, TR > & _Istr, bool _Noskip = false); operátor bool () const;};

### <a name="remarks"></a>Poznámky

Pokud `_Istr.`je [dobrá](../standard-library/basic-ios-class.md#good) hodnota true, konstruktor:

- Volání `_Istr`. [](../standard-library/basic-ios-class.md#tie)vyprázdnit `_Istr`, pokud.[](../standard-library/basic-ostream-class.md#flush)  ->  `tie`není ukazatel s hodnotou null.

- Efektivně volá [WS](../standard-library/istream-functions.md#ws)( `_Istr`), `_Istr`Pokud. [](../standard-library/ios-base-class.md#flags)**příznaky&** [skipws](../standard-library/ios-functions.md#skipws) jsou nenulové.

Pokud po každé takové přípravě, `_Istr`. `good`je false, volá `_Istr`konstruktor. [setstate](../standard-library/basic-ios-class.md#setstate) (`failbit`). V každém případě konstruktor ukládá hodnotu vrácenou `_Istr`. `good`v `status`. Pozdější volání, které `operator bool` poskytuje tuto uloženou hodnotu.

## <a name="swap"></a>  basic_istream::swap

Vyměňuje obsah dvou `basic_istream` objektů.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Odkaz l-hodnoty na `basic_istream` objekt.

### <a name="remarks"></a>Poznámky

Členská funkce volá metodu [basic_ios:: swap](../standard-library/basic-ios-class.md#swap)`(right)`. Také vyměňuje počet extrakcí s počtem extrakce *vpravo*.

## <a name="sync"></a>  basic_istream::sync

Synchronizuje vstupní zařízení přidružené ke streamu s vyrovnávací pamětí streamu.

```cpp
int sync();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je [rdbuf](../standard-library/basic-ios-class.md#rdbuf) ukazatel s hodnotou null, funkce vrátí hodnotu-1. V opačném případě `rdbuf`volá  ->  [pubsync](../standard-library/basic-streambuf-class.md#pubsync). Pokud to vrátí-1, funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)(`badbit`) a vrátí-1. V opačném případě vrátí funkce hodnotu nula.

## <a name="tellg"></a>basic_istream::tellg

Oznamuje aktuální pozici pro čtení v datovém proudu.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální pozice v datovém proudu.

### <a name="remarks"></a>Poznámky

Pokud je [selhání](../standard-library/basic-ios-class.md#fail) false, vrátí členská funkce [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **v**). V opačném případě `pos_type`vrátí (-1).

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

## <a name="unget"></a>basic_istream::unget

Vloží poslední přečtený znak zpět do datového proudu.

```cpp
basic_istream<Elem, Tr>& unget();
```

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*this**).

### <a name="remarks"></a>Poznámky

Neformátovaná [Vstupní funkce](../standard-library/basic-istream-class.md) vrátí předchozí prvek v datovém proudu, pokud je to možné, jako if voláním `rdbuf`  ->  [sungetc](../standard-library/basic-streambuf-class.md#sungetc). Pokud [je rdbuf](../standard-library/basic-ios-class.md#rdbuf) ukazatel s hodnotou null, nebo `sungetc` Pokud volání vrátí **traits_type::** [EOF](../standard-library/basic-ios-class.md#eof), funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)(`badbit`). V každém případě  **\*to vrátí.**

Informace o tom, `unget` jak může selhat, najdete v tématu [basic_streambuf:: sungetc](../standard-library/basic-streambuf-class.md#sungetc).

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

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
