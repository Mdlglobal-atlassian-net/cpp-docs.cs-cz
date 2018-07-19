---
title: basic_istream – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca0b25f5df6d4efb70e27fea6ef2323568134b2e
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964460"
---
# <a name="basicistream-class"></a>basic_istream – třída

Popisuje objekt, který řídí extrakce prvků a kódovaného objekty z vyrovnávací paměti datového proudu s prvky typu `Elem`, označované také jako [char_type](../standard-library/basic-ios-class.md#char_type), jehož vlastnosti znaků určuje třídu *Tr* , označované také jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_istream : virtual public basic_ios<Elem, Tr>
```

## <a name="remarks"></a>Poznámky

Většinu člena funkce, které přetěžují [operátor >>](#op_gt_gt) jsou formátovány vstupní funkce. Jsou podle tohoto vzoru vytvořené:

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

Mnoho dalších funkcí členů je neformátovaný vstupní funkcí. Jsou podle tohoto vzoru vytvořené:

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

Obě volání funkce [setstate](../standard-library/basic-ios-class.md#setstate)(`eofbit`) pokud narazí při extrahování prvků konec souboru.

Objekt třídy `basic_istream` <  `Elem`, *Tr*> ukládá:

- Virtuální základní objekt veřejné třídy [basic_ios –](../standard-library/basic-ios-class.md)< `Elem`, *Tr*> `.`

- Extrakci počet pro poslední neformátovaný vstupní operace (volá `count` v předcházejícím kódu).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [basic_ifstream – třída](../standard-library/basic-ifstream-class.md) získat další informace o vstupní datové proudy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_istream](#basic_istream)|Vytvoří objekt typu `basic_istream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[gcount –](#gcount)|Vrátí počet znaků čtení během posledních neformátovaný vstup.|
|[get](#get)|Načte jeden nebo více znaků ze vstupního datového proudu.|
|[getline](#getline)|Přečte řádek ze vstupního datového proudu.|
|[Ignorovat](#ignore)|Způsobí, že počet prvků přeskočit z aktuální pozici čtení.|
|[Náhled](#peek)|Vrátí následující znak pro čtení.|
|[putback –](#putback)|Vloží zadaný znak do datového proudu.|
|[read](#read)|Přečte zadaný počet znaků z datového proudu a uloží je v poli.|
|[readsome –](#readsome)|Čtení z pouze vyrovnávací paměti.|
|[seekg –](#seekg)|Posune pozici v datovém proudu pro čtení.|
|[SENTRY](#sentry)|Vnořené třídy popisuje objekt, jehož deklarace struktur formátovaný vstupu funkce a neformátovaný vstupní funkce.|
|[Prohození](#swap)|Vymění to `basic_istream` objekt pro zadaný `basic_istream` parametru objektu.|
|[sync](#sync)|Synchronizuje vstupní zařízení spojené s datovým proudem s vyrovnávací paměť datového proudu.|
|[tellg –](#tellg)|Hlásí, že čtení aktuální pozici v datovém proudu.|
|[unget –](#unget)|Vloží naposledy čtení znak zpět do datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor >>](#op_gt_gt)|Volá funkci vstupního datového proudu nebo přečte formátovaná data ze vstupního datového proudu.|
|[operátor =](#op_eq)|Přiřadí `basic_istream` na pravé straně operátoru k tomuto objektu. Toto je zahrnující přiřazení pro přesun `rvalue` odkaz, který kopii nenechává za sebou.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<istream >

**Namespace:** std

## <a name="basic_istream"></a>  basic_istream::basic_istream –

Vytvoří objekt typu `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*strbuf* objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd* **true** pokud jde standardní datový proud; v opačném případě **false**.

*správné* A `basic_istream` objektu, který chcete zkopírovat.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [init](../standard-library/basic-ios-class.md#init)(_Malá `trbuf`). Také ukládá nula počet extrakce. Další informace o tento počet extrakce, najdete v části poznámky [basic_istream – třída](../standard-library/basic-istream-class.md) – téma s přehledem.

Druhý konstruktor inicializuje základní třídu voláním `move( right)`. Také ukládá _R `ight.gcount()` v počtu extrakce a úložišti nula počet extrakce pro _R `ight`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) získat další informace o vstupní datové proudy.

## <a name="gcount"></a>  basic_istream::gcount

Vrátí počet znaků čtení během posledních neformátovaný vstup.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet extrakce.

### <a name="remarks"></a>Poznámky

Použití [basic_istream::get](#get) ke čtení neformátovaný znaků.

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

```Output

a

```

```Output

      aType the letter 'a':
a
1
```

## <a name="get"></a>  basic_istream::Get

Načte jeden nebo více znaků ze vstupního datového proudu.

```cpp
int_type get();

basic_istream<Elem, Tr>& get(Elem& Ch);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count, Elem Delim);

basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf);
basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf, Elem Delim);
```

### <a name="parameters"></a>Parametry

*počet* počet znaků ke čtení z `strbuf`.

*Delim* znak, který by měla ukončit čtení, pokud je zjištěna před *počet*.

*Str* řetězec, do kterých chcete zapsat.

*Ch* znak zobrazíte.

*strbuf* do vyrovnávací paměti, do kterých chcete zapsat.

### <a name="return-value"></a>Návratová hodnota

Konstruktor bez parametrů formuláře get vrací element číst jako celé číslo nebo konec souboru. Zbývající formuláře vrátit datový proud (* `this`).

### <a name="remarks"></a>Poznámky

První z těchto funkcí neformátovaný vstupní extrahuje element, pokud je to možné, jako kdyby Autor vrácení `rdbuf` ->  `sbumpc`. V opačném případě vrátí **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). Pokud funkci extrahuje žádný element, volá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

Druhá funkce extrahuje [int_type](../standard-library/basic-ios-class.md#int_type) element `meta` stejným způsobem. Pokud `meta` porovná rovno **traits_type::eof**, volání funkce `setstate`( **failbit**). V opačném případě ukládá **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)( `meta`) v `Ch`. Funkce vrátí  **\*to**.

Třetí funkce vrátí **získat**(_ *Str*, `count`, `widen`('\ **n**")).

Čtvrtý funkce extrahuje až *počet* + 1 prvků a ukládá je do pole počínaje _ *Str*. Vždy ukládá `char_type` po žádné elementy, které je uložený. V pořadí podle testování zastaví extrakce:

- Na konci souboru.

- Po funkci extrahuje element, který při porovnání rovna *Delim*, v takovém případě je prvek zařadí zpět do řízené sekvence.

- Po funkci extrahuje *počet* + 1 prvků.

Pokud funkci extrahuje žádné elementy, zavolá `setstate`( **failbit**). V každém případě vrátí  **\*to**.

Pátý funkce vrátí **získat**( **strbuf**, `widen`('\ **n**")).

Šestý funkce extrahuje prvky a vloží je do `strbuf`. Extrakce zastaví na ukončení souboru nebo na element, který při porovnání rovna _ *Delim,* které se extrahují. Také zastaví, bez extrahování elementu Nejistá, pokud selže vložení nebo vyvolá výjimku (která je zachycena ale není znovu vyvolána). Pokud funkci extrahuje žádné elementy, zavolá `setstate`( **failbit**). V každém případě funkce vrací  **\*to**.

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

## <a name="getline"></a>  basic_istream::getline

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

*počet* počet znaků ke čtení z `strbuf`.

*Delim* znak, který by měla ukončit čtení, pokud je zjištěna před *počet*.

*Str* řetězec, do kterých chcete zapsat.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*to**).

### <a name="remarks"></a>Poznámky

První z těchto neformátovaný vstup funkce vrátí **getline**(_ *Str*, `count`, `widen`(" `\` **n**")).

Druhá funkce extrahuje až *počet* + 1 prvků a ukládá je do pole počínaje _ *Str*. Po extrahované prvků, které ukládají vždy ukládá znak ukončení řetězce. V pořadí podle testování zastaví extrakce:

- Na konci souboru.

- Po funkci extrahuje element, který při porovnání rovna *Delim*, v takovém případě elementu je vrátit ani připojenou k řízené sekvence.

- Po funkci extrahuje *počet* + 1 prvků.

Pokud funkci extrahuje žádné elementy nebo *počet* + 1 prvků, volá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). V každém případě vrátí  **\*to**.

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

## <a name="ignore"></a>  basic_istream::Ignore

Způsobí, že počet prvků přeskočit z aktuální pozici čtení.

```cpp
basic_istream<Elem, Tr>& ignore(
    streamsize count = 1,
    int_type Delim = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*počet* počet prvků, které se od aktuálního přeskočit čtení pozici.

*Delim* elementu, který, pokud došlo k před počet, způsobí, že `ignore` vrátit a umožňuje všechny prvky po *Delim* ke čtení.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*to**).

### <a name="remarks"></a>Poznámky

Neformátovaný vstupní funkce extrahuje až *počet* prvky a je ignoruje. Pokud *počet* rovná **numeric_limits –\<int >:: maximální**, ale se používá jako libovolně velké. Extrakce zastaví již v rané fázi na konec souboru nebo v elementu `Ch` tak, aby **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `Ch`) porovnává rovno *Delim* (který je také extrahován). Funkce vrátí  **\*to**.

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

## <a name="op_gt_gt"></a>  základní\_istream::operator >>

Volá funkci vstupního datového proudu nebo přečte formátovaná data ze vstupního datového proudu.

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

*Pfn* ukazatele na funkci.

*strbuf* objekt typu `stream_buf`.

*Val* hodnoty ke čtení z datového proudu.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*to**).

### <a name="remarks"></a>Poznámky

\<Istream > záhlaví také definuje několik operátorů globální extrakce. Další informace najdete v tématu [operátor >> (\<istream >)](../standard-library/istream-operators.md#op_gt_gt).

První členská funkce zajišťuje, že výraz ve tvaru **istr**  >>  `ws` volání [ws](../standard-library/istream-functions.md#ws)( **istr**) a vrátí  **\*to**. Druhý a třetí funkce zajišťují další manipulátory, jako například [hex](../standard-library/ios-functions.md#hex), se chovají podobně. Zbývající funkce představují formátovaný vstupní funkce.

Funkce:

```cpp
basic_istream& operator>>(
    basic_streambuf<Elem, Tr>* strbuf);
```

Extrahuje prvky, pokud _ *Strbuf* není ukazatel s hodnotou null a vloží je do *strbuf*. Extrakce zastaví na konec souboru. Zastaví také bez extrahování elementu Nejistá, pokud selže vložení nebo vyvolá výjimku (která je zachycena ale není znovu vyvolána). Pokud funkci extrahuje žádné elementy, zavolá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). V každém případě funkce vrací  **\*to**.

Funkce:

```cpp
basic_istream& operator>>(bool& val);
```

extrahuje pole a převede ho na hodnotu typu Boolean voláním [use_facet](../standard-library/basic-filebuf-class.md#open)  <  `num_get` \< **Elem**, **InIt**> ( [getloc –](../standard-library/ios-base-class.md#getloc)). [získat](../standard-library/ios-base-class.md#getloc)( **InIt**( [rdbuf –](../standard-library/basic-ios-class.md#rdbuf)), `Init`(0),  **\*to**, `getloc`, `val`). Tady **InIt** je definován jako [istreambuf_iterator](../standard-library/istreambuf-iterator-class.md) \< **Elem**, **Tr**>. Funkce vrátí  **\*to**.

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

Každá extrahovat pole a převést na číselnou hodnotu voláním `use_facet` <  `num_get` \< **Elem**, **InIt**> ( `getloc`). [získat](#get)( **InIt**( `rdbuf`), `Init`(0),  **\*to**, `getloc`, `val`). Tady **InIt** je definován jako `istreambuf_iterator` \< **Elem**, **Tr**>, a `val` má typ **dlouhé**,**unsigned long**, nebo **void \***  podle potřeby.

Pokud se převedená hodnota nemůže být reprezentovaný jako typ `val`, volání funkce [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). V každém případě funkce vrací  **\*to**.

Funkce:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

Každá extrahovat pole a převést na číselnou hodnotu voláním `use_facet` <  `num_get` \< **Elem**, **InIt**> ( `getloc`). **získat**( **InIt**( `rdbuf`), `Init`(0),  **\*to**, `getloc`, `val`). Tady `InIt` je definován jako `istreambuf_iterator` \< **Elem**, **Tr**>, a `val` má typ **double** nebo **dlouhý dvojité** podle potřeby.

Pokud se převedená hodnota nemůže být reprezentovaný jako typ `val`, volání funkce `setstate`( **failbit**). V každém případě vrátí  **\*to**.

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

## <a name="op_eq"></a>  basic_istream::Operator =

Přiřadí `basic_istream` na pravé straně operátoru k tomuto objektu. Toto je zahrnující přiřazení pro přesun `rvalue` odkaz, který kopii nenechává za sebou.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*správné* `rvalue` odkaz `basic_ifstream` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí * to.

### <a name="remarks"></a>Poznámky

Členský operátor volá prohození `( right)`.

## <a name="peek"></a>  basic_istream::Peek

Vrátí následující znak pro čtení.

```cpp
int_type peek();
```

### <a name="return-value"></a>Návratová hodnota

Další znak, který bude číst.

### <a name="remarks"></a>Poznámky

Neformátovaný vstupní funkce extrahuje element, pokud je to možné, jakoby Autor vrácení `rdbuf`  ->  [sgetc –](../standard-library/basic-streambuf-class.md#sgetc). V opačném případě vrátí **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

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

```Output

abcde

```

```Output

      abcdeType 'abcde': abcde
a abcde
```

## <a name="putback"></a>  basic_istream::putback

Vloží zadaný znak do datového proudu.

```cpp
basic_istream<Elem, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Parametry

*Ch* znak převést zpět do datového proudu.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*to**).

### <a name="remarks"></a>Poznámky

[Neformátovaný vstupní funkce](../standard-library/basic-istream-class.md) vrátí zpět *Ch*, pokud je to možné, jako kdyby volala [rdbuf –](../standard-library/basic-ios-class.md#rdbuf)`->`[sputbackc –](../standard-library/basic-streambuf-class.md#sputbackc). Pokud rdbuf – je ukazatel s hodnotou null, nebo pokud volání `sputbackc` vrátí **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), volání funkce [setstate](../standard-library/basic-ios-class.md#setstate)(`badbit`). V každém případě vrátí  **\*to**.

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

## <a name="read"></a>  basic_istream::Read

Přečte zadaný počet znaků z datového proudu a uloží je v poli.

Tato metoda je potenciálně nebezpečná, protože spoléhá na že volající zkontroluje správnost předaných hodnot.

```cpp
basic_istream<Elem, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Str* pole, ve kterém čtení znaků.

*počet* počet znaků pro čtení.

### <a name="return-value"></a>Návratová hodnota

Datový proud ( `*this`).

### <a name="remarks"></a>Poznámky

Neformátovaný vstupní funkce extrahuje až *počet* elementy a ukládá je do pole počínaje _ `Str`. Extrakce zastaví již v rané fázi na konec souboru, ve kterém případ funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). V každém případě vrátí `*this`.

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

```Output

abcde

```

```Output

      abcdeType 'abcde': abcde
abcde
```

## <a name="readsome"></a>  basic_istream::readsome

Přečte zadaný počet znaků hodnoty.

Tato metoda je potenciálně nebezpečná, protože spoléhá na že volající zkontroluje správnost předaných hodnot.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Str* pole, ve kterém `readsome` ukládá přečte znaky.

*počet* počet znaků pro čtení.

### <a name="return-value"></a>Návratová hodnota

Počet znaků ve skutečnosti čtení [gcount –](#gcount).

### <a name="remarks"></a>Poznámky

Tato funkce neformátovaný vstupní extrahuje až *počet* elementy ze vstupní datový proud stream a uloží je v poli *str*.

Tato funkce není počkat na vstup. Načte libovolná data je k dispozici.

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

Posune pozici v datovém proudu pro čtení.

```cpp
basic_istream<Elem, Tr>& seekg(pos_type pos);

basic_istream<Elem, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parametry

*POS* absolutní pozici, do kterého chcete přesunout ukazatel pro čtení.

*vypnout* posun čtení ukazatele vzhledem k *způsob*.

*způsob, jak* některou [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) výčty.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*to**).

### <a name="remarks"></a>Poznámky

První členská funkce provádí absolutní hledání, druhá členská funkce provádí relativní seek.

> [!NOTE]
> Druhá členská funkce s textovými soubory nepoužívejte, protože Standard C++ nepodporuje relativní vyhledá v textových souborech.

Pokud [selhání](../standard-library/basic-ios-class.md#fail) má hodnotu false, první volání členských funkcí **newpos** = [rdbuf –](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekpos –](../standard-library/basic-streambuf-class.md#pubseekpos)( `pos`), pro některé `pos_type` dočasný objekt `newpos`. Pokud `fail` má hodnotu false, druhé volání funkce **newpos** = **rdbuf –** -> [pubseekoff –](../standard-library/basic-streambuf-class.md#pubseekoff)( `off`, `way`). V obou případech Pokud ( `off_type`) **newpos** == ( `off_type`)(-1) (umístění operace selže), volání funkce `istr`. [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). Obě funkce vrátí  **\*to**.

Pokud [selhání](../standard-library/basic-ios-class.md#fail) má hodnotu true, členské funkce Neprovádět žádnou akci.

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

## <a name="sentry"></a>  basic_istream::SENTRY

Vnořené třídy popisuje objekt, jehož deklarace struktur vstupní funkce naformátovaný a je neformátovaný.

Třída sentry {public: explicitní sentry (basic_istream –\<Elem, Tr > & _Istr, bool _Noskip = false); operator bool() const;};

### <a name="remarks"></a>Poznámky

Pokud `_Istr.` [dobré](../standard-library/basic-ios-class.md#good) má hodnotu true, konstruktor:

- Volání `_Istr`. [Tie](../standard-library/basic-ios-class.md#tie) -> [vyprázdnění](../standard-library/basic-ostream-class.md#flush) Pokud `_Istr`. `tie` není ukazatel s hodnotou null

- Efektivně volá [ws](../standard-library/istream-functions.md#ws)( `_Istr`) Pokud `_Istr`. [příznaky](../standard-library/ios-base-class.md#flags)**&**[skipws](../standard-library/ios-functions.md#skipws) je nenulový

Pokud po těchto přípravy `_Istr`. `good` má hodnotu false, volá konstruktor `_Istr`. [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). V každém případě konstruktor ukládá hodnotu vrácenou příkazem `_Istr`. `good` v `status`. Pozdější volání `operator bool` poskytuje tuto uloženou hodnotu.

## <a name="swap"></a>  basic_istream::swap

Vyměňuje obsahy dvě `basic_istream` objekty.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parametry

*správné* reference na lvalue k `basic_istream` objektu.

### <a name="remarks"></a>Poznámky

Volání členských funkcí [basic_ios::swap](../standard-library/basic-ios-class.md#swap)`(right)`. Také vymění počet extrakce s počtem extrakce pro *správné*.

## <a name="sync"></a>  basic_istream::Sync

Synchronizuje vstupní zařízení spojené s datovým proudem s vyrovnávací paměť datového proudu.

```cpp
int sync();
```

### <a name="return-value"></a>Návratová hodnota

Pokud [rdbuf –](../standard-library/basic-ios-class.md#rdbuf) je ukazatel s hodnotou null, funkce vrátí hodnotu -1. V opačném případě volá `rdbuf`  ->  [pubsync –](../standard-library/basic-streambuf-class.md#pubsync). Pokud, která vrátí hodnotu -1, funkce zavolá [setstate](../standard-library/basic-ios-class.md#setstate)(`badbit`) a vrátí hodnotu -1. V opačném případě funkce vrátí hodnotu 0.

## <a name="tellg"></a>  basic_istream::tellg

Hlásí, že čtení aktuální pozici v datovém proudu.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální pozice v datovém proudu.

### <a name="remarks"></a>Poznámky

Pokud [selhání](../standard-library/basic-ios-class.md#fail) má hodnotu false, členská funkce vrátí [rdbuf –](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekoff –](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **v**). V opačném případě vrátí `pos_type`(-1).

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

## <a name="unget"></a>  basic_istream::unget

Vloží naposledy čtení znak zpět do datového proudu.

```cpp
basic_istream<Elem, Tr>& unget();
```

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*to**).

### <a name="remarks"></a>Poznámky

[Neformátovaný vstupní funkce](../standard-library/basic-istream-class.md) vrátí zpět předchozí prvek v datovém proudu, pokud je to možné, jako kdyby volala `rdbuf`  ->  [sungetc –](../standard-library/basic-streambuf-class.md#sungetc). Pokud [rdbuf –](../standard-library/basic-ios-class.md#rdbuf) je ukazatel s hodnotou null, nebo pokud volání `sungetc` vrátí **traits_type::**[eof](../standard-library/basic-ios-class.md#eof), volání funkce [setstate](../standard-library/basic-ios-class.md#setstate)() `badbit`). V každém případě vrátí  **\*to**.

Informace o tom, jak `unget` může selhat, naleznete v tématu [basic_streambuf::sungetc](../standard-library/basic-streambuf-class.md#sungetc).

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

```Output

abc

```

```Output

      abcType 'abc': abc
abc
```

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
