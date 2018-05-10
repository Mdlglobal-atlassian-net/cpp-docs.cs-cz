---
title: basic_istream – třída | Microsoft Docs
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
ms.openlocfilehash: 22dc1282dc165941c1a611583138c2d9aed51090
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="basicistream-class"></a>basic_istream – třída

Popisuje objekt, který řídí extrakce elementů a kódovaného objekty z datového proudu vyrovnávací paměť elementy typu `Elem`, také známé jako [char_type –](../standard-library/basic-ios-class.md#char_type), jehož vlastnosti znak určuje třídu *Tr* , také známé jako [traits_type –](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_istream : virtual public basic_ios<Elem, Tr>
```

## <a name="remarks"></a>Poznámky

Většina člena funkce této přetížení [operátor >>](#op_gt_gt) jsou formátovány vstupní funkce. Budou vyhovovat vzoru:

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

Mnoho funkcí člen je neformátovaný vstupní funkce. Budou vyhovovat vzoru:

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

Obě skupiny volání funkce [setstate –](../standard-library/basic-ios-class.md#setstate)( **eofbit**) když narazí při extrahování elementy konec souboru.

Třída objektu `basic_istream` <  `Elem`, *Tr*> ukládá:

- Základní virtuální veřejné objekt třídy [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, *Tr*> `.`

- Extrakci počet pro poslední neformátovaný vstupní operace (nazývá **počet** v předchozí kód).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [basic_ifstream – třída](../standard-library/basic-ifstream-class.md) Další informace o vstupní datové proudy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_istream](#basic_istream)|Vytvoří objekt typu `basic_istream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[gcount –](#gcount)|Vrátí počet znaků pro čtení během poslední neformátovaný vstup.|
|[get](#get)|Přečte jeden nebo více znaků ze vstupního datového proudu.|
|[getline](#getline)|Přečte řádek ze vstupního datového proudu.|
|[Ignorovat](#ignore)|Způsobí, že počet elementů přeskočil z aktuální číst pozici.|
|[Prohlížení](#peek)|Vrací další znak, který má být číst.|
|[putback –](#putback)|Vloží zadaný znak do datového proudu.|
|[read](#read)|Přečte zadaný počet znaků z datového proudu a ukládá je do pole.|
|[readsome –](#readsome)|Čtení z jenom vyrovnávací paměti.|
|[seekg –](#seekg)|Přesune čtení pozici v datovém proudu.|
|[SENTRY](#sentry)|Vnořené třídy popisuje objekt, jehož deklarace struktur formátovaný vstupní funkce a neformátovaný vstupní funkce.|
|[Swap](#swap)|To výměny `basic_istream` objekt pro poskytnutého `basic_istream` parametru objektu.|
|[sync](#sync)|Synchronizuje vstupní zařízení přidružená datový proud s vyrovnávací paměti datový proud.|
|[tellg –](#tellg)|Hlásí, že aktuální číst pozici v datovém proudu.|
|[unget –](#unget)|PUT naposledy přečíst znak zpět do datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor >>](#op_gt_gt)|Volání funkce na vstupního datového proudu nebo čte formátovaná data z vstupního datového proudu.|
|[operátor =](#op_eq)|Přiřadí `basic_istream` na pravé straně operátoru k tomuto objektu. Jedná se o přesunutí přiřazení zahrnující `rvalue` odkaz, který kopii nenechává za sebou.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<IStream on Request >

**Namespace:** – std

## <a name="basic_istream"></a>  basic_istream::basic_istream

Vytvoří objekt typu `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

`strbuf` Objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

`_Isstd` `true` Pokud se jedná o standardní datový proud; v opačném `false`.

`right` A `basic_istream` objekt, který chcete kopírovat.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [init](../standard-library/basic-ios-class.md#init)(_Malá `trbuf`). Také ukládá nula počet extrakce. Další informace o tento počet extrakce, najdete v části poznámky [basic_istream – třída](../standard-library/basic-istream-class.md) přehledu.

Druhý konstruktor inicializuje základní třídu voláním `move( right)`. Ukládá také _R `ight.gcount()` v extrakce počet a úložišť nula počet extrakce pro _R `ight`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) Další informace o vstupní datové proudy.

## <a name="gcount"></a>  basic_istream::gcount

Vrátí počet znaků pro čtení během poslední neformátovaný vstup.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet extrakce.

### <a name="remarks"></a>Poznámky

Použití [basic_istream::get](#get) číst neformátovaný znaků.

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

`count` Počet znaků ke čtení z `strbuf`.

`Delim` Znak, který by měl ukončit čtení, pokud je zjištěna před `count`.

`str` Řetězec, ve kterém se má zapisovat.

`Ch` Znak pro získání.

`strbuf` Vyrovnávací paměť ve kterém se má zapisovat.

### <a name="return-value"></a>Návratová hodnota

Bez parametrů formu get vrátí prvek přečíst jako celé číslo nebo číslo konec souboru. Zbývající formuláře vrátit datový proud (* `this`).

### <a name="remarks"></a>Poznámky

První z těchto funkcí neformátovaný vstupní extrahuje elementu, pokud je to možné, jako kdyby nástrojem vrácení `rdbuf` ->  `sbumpc`. Funkce **traits_type –::**[eof](../standard-library/char-traits-struct.md#eof). Pokud funkci extrahuje žádné elementy, zavolá [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**).

Extrahuje funkce second [int_type –](../standard-library/basic-ios-class.md#int_type) element `meta` stejným způsobem. Pokud `meta` porovná rovno **traits_type::eof**, volání funkce `setstate`( **failbit**). Jinak, ukládá **traits_type –::**[to_char_type –](../standard-library/char-traits-struct.md#to_char_type)( `meta`) v `Ch`. Funkce vrátí hodnotu  **\*to**.

Vrátí třetí funkce **získat**(_ *Str*, `count`, `widen`('\ **n**.)).

Čtvrtý funkce extrahuje až `count` – 1 elementy a ukládá je do pole počínaje _ *Str*. Vždy ukládá `char_type` po žádné extrahování elementy ukládá. V pořadí podle testování zastaví extrakce:

- Na konci souboru.

- Po funkce extrahuje element, který porovnává rovna `Delim`, v takovém případě je element vrátit zpět k řízené sekvenci.

- Po extrahuje funkce `count` – 1 elementy.

Pokud funkci extrahuje žádné elementy, zavolá `setstate`( **failbit**). V každém případě vrátí  **\*to**.

Páté funkce vrátí hodnotu **získat**( **strbuf**, `widen`('\ **n**.)).

Funkci šesté extrahuje prvky a vloží je do **strbuf**. Extrakce zastaví na koncové souboru nebo na element, který porovnává rovna _ *Delim,* které není extrahovat. Zastaví také, bez extrahování dotyčná, pokud vložení selže nebo vyvolá výjimku, (což je zachycena, ale není znovu vyvolány). Pokud funkci extrahuje žádné elementy, zavolá `setstate`( **failbit**). V každém případě funkce vrátí hodnotu  **\*to**.

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

Získá řádku ze vstupního datového proudu.

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

`count` Počet znaků ke čtení z **strbuf**.

`Delim` Znak, který by měl ukončit čtení, pokud je zjištěna před `count`.

`str` Řetězec, ve kterém se má zapisovat.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*to**).

### <a name="remarks"></a>Poznámky

První z nich neformátovaný vstup funkce vrátí **getline**(_ *Str*, `count`, `widen`(' `\` **n**.)).

Funkce second extrahuje až `count` – 1 elementy a ukládá je do pole počínaje _ *Str*. Vždy ukládá ukončovací znak řetězec po extrahované prvků, které ukládají. V pořadí podle testování zastaví extrakce:

- Na konci souboru.

- Po funkce extrahuje element, který porovnává rovna `Delim`, v takovém případě elementu je vrátit zpět ani připojenou k řízené sekvenci.

- Po extrahuje funkce `count` – 1 elementy.

Pokud funkci extrahuje žádné elementy nebo `count` – 1 elementy, zavolá [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**). V každém případě vrátí  **\*to**.

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

Způsobí, že počet elementů přeskočil z aktuální číst pozici.

```cpp
basic_istream<Elem, Tr>& ignore(
    streamsize count = 1,
    int_type Delim = traits_type::eof());
```

### <a name="parameters"></a>Parametry

`count` Počet elementů tak, aby přeskočil z aktuální pozici pro čtení.

`Delim` Element, který, pokud došlo k před počet, způsobí, že **Ignorovat** vrátit a umožní všechny elementy po `Delim` čtení.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*to**).

### <a name="remarks"></a>Poznámky

Neformátovaný tvar vstupní funkce extrahuje až `count` elementy a je ignoruje. Pokud `count` rovná **numeric_limits\<int >:: maximální**, ale je provedena jako libovolně velké. Extrakce zastaví již v rané fázi na konec souboru nebo na element `Ch` tak, aby **traits_type –::**[to_int_type –](../standard-library/char-traits-struct.md#to_int_type)( `Ch`) porovnává rovno *Delim* (který je také extrahovat). Funkce vrátí hodnotu  **\*to**.

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

Volání funkce na vstupního datového proudu nebo čte formátovaná data z vstupního datového proudu.

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

`Pfn` Ukazatel na funkci.

`strbuf` Objekt typu **stream_buf**.

`val` Hodnoty ke čtení z datového proudu.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*to**).

### <a name="remarks"></a>Poznámky

\<IStream on Request > záhlaví také definuje několik globální extraction – operátory. Další informace najdete v tématu [operátor >> (\<IStream on Request >)](../standard-library/istream-operators.md#op_gt_gt).

První člen funkce zajišťuje, že výrazu ve formátu **istr**  >>  `ws` volání [ws](../standard-library/istream-functions.md#ws)( **istr**) a vrátí  **\*to**. Druhý a třetí funkce, jako zajistěte, aby další manipulátory [šestnáctkových](../standard-library/ios-functions.md#hex), chovají podobně. Zbývající funkce tvoří formátovaný vstupní funkce.

Funkce:

```cpp
basic_istream& operator>>(
    basic_streambuf<Elem, Tr>* strbuf);
```

Extrahuje prvky, pokud _ *Strbuf* není nulový ukazatel a vloží je do `strbuf`. Extrakce zastaví na konec souboru. Zastaví také bez extrahování dotyčná, pokud vložení selže nebo vyvolá výjimku, (což je zachycena, ale není znovu vyvolány). Pokud funkci extrahuje žádné elementy, zavolá [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**). V každém případě funkce vrátí hodnotu  **\*to**.

Funkce:

```cpp
basic_istream& operator>>(bool& val);
```

extrahuje pole a převede jej na logickou hodnotu voláním [use_facet](../standard-library/basic-filebuf-class.md#open)  <  `num_get` \< **Elem**, **InIt**> ( [getloc –](../standard-library/ios-base-class.md#getloc)). [získat](../standard-library/ios-base-class.md#getloc)( **InIt**( [rdbuf –](../standard-library/basic-ios-class.md#rdbuf)), `Init`(0),  **\*to**, `getloc`, `val`). Zde **InIt** je definován jako [istreambuf_iterator](../standard-library/istreambuf-iterator-class.md) \< **Elem**, **Tr**>. Funkce vrátí hodnotu  **\*to**.

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

každé pole extrahovat a převést jej do číselnou hodnotu voláním `use_facet` <  `num_get` \< **Elem**, **InIt**> ( `getloc`). [získat](#get)( **InIt**( `rdbuf`), `Init`(0),  **\*to**, `getloc`, `val`). Zde **InIt** je definován jako `istreambuf_iterator` \< **Elem**, **Tr**>, a `val` má typ **dlouho**,`unsigned long`, nebo **void \***  podle potřeby.

Pokud převedenou hodnotu nelze reprezentovat jako typ `val`, volání funkce [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**). V každém případě funkce vrátí hodnotu  **\*to**.

Funkce:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

každé pole extrahovat a převést jej do číselnou hodnotu voláním `use_facet` <  `num_get` \< **Elem**, **InIt**> ( `getloc`). **získat**( **InIt**( `rdbuf`), `Init`(0),  **\*to**, `getloc`, `val`). Zde **InIt** je definován jako `istreambuf_iterator` \< **Elem**, **Tr**>, a `val` má typ **dvojité** nebo `long double` podle potřeby.

Pokud převedenou hodnotu nelze reprezentovat jako typ `val`, volání funkce `setstate`( **failbit**). V každém případě vrátí  **\*to**.

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

Přiřadí `basic_istream` na pravé straně operátoru k tomuto objektu. Jedná se o přesunutí přiřazení zahrnující `rvalue` odkaz, který kopii nenechává za sebou.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

`right` `rvalue` Odkaz na `basic_ifstream` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí * to.

### <a name="remarks"></a>Poznámky

Operátor členů volá swap `( right)`.

## <a name="peek"></a>  basic_istream::Peek

Vrací další znak, který má být číst.

```cpp
int_type peek();
```

### <a name="return-value"></a>Návratová hodnota

Další znak, který bude číst.

### <a name="remarks"></a>Poznámky

Neformátovaný tvar vstupní funkce extrahuje elementu, pokud je to možné, jako kdyby nástrojem vrácení `rdbuf`  ->  [sgetc –](../standard-library/basic-streambuf-class.md#sgetc). Funkce **traits_type –::**[eof](../standard-library/char-traits-struct.md#eof).

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

`Ch` Znak pro vrátit zpět do datového proudu.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*to**).

### <a name="remarks"></a>Poznámky

[Neformátovaný vstupní funkce](../standard-library/basic-istream-class.md) vrátí zpět `Ch`, pokud je to možné, jako kdyby pomocí volání metody [rdbuf –](../standard-library/basic-ios-class.md#rdbuf)`->`[sputbackc –](../standard-library/basic-streambuf-class.md#sputbackc). Pokud je rdbuf – ukazatele null, nebo pokud volání `sputbackc` vrátí **traits_type –::**[eof](../standard-library/char-traits-struct.md#eof), volání funkce [setstate –](../standard-library/basic-ios-class.md#setstate)( **badbit**). V každém případě vrátí  **\*to**.

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

Přečte zadaný počet znaků z datového proudu a ukládá je do pole.

Tato metoda je potenciálně nebezpečné, jako je závislé na volajícího, aby zkontrolujte správnost předané hodnoty.

```cpp
basic_istream<Elem, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

`str` Pole, ve kterém se má číst znaky.

`count` Počet znaků ke čtení.

### <a name="return-value"></a>Návratová hodnota

Datový proud ( `*this`).

### <a name="remarks"></a>Poznámky

Neformátovaný tvar vstupní funkce extrahuje až `count` elementy a ukládá je do pole počínaje _ `Str`. Extrakce zastaví již v rané fázi na konci souboru, ve kterém případ funkce volá [setstate –](../standard-library/basic-ios-class.md#setstate)( `failbit`). V každém případě vrátí `*this`.

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

Tato metoda je potenciálně nebezpečné, jako je závislé na volajícího, aby zkontrolujte správnost předané hodnoty.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

`str` Pole, ve kterém `readsome` ukládá přečte znaky.

`count` Počet znaků ke čtení.

### <a name="return-value"></a>Návratová hodnota

Počet znaků, které jsou ve skutečnosti číst, [gcount –](#gcount).

### <a name="remarks"></a>Poznámky

Neformátovaný tvar vstupní funkce extrahuje až `count` elementy ze vstupu datového proudu a ukládá je v poli `str`.

Tato funkce nečeká na vstup. Kromě toho přečte ať data nejsou k dispozici.

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

Přesune čtení pozici v datovém proudu.

```cpp
basic_istream<Elem, Tr>& seekg(pos_type pos);

basic_istream<Elem, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parametry

`pos` Absolutní umístění, ve kterém se má přesunout ukazatel pro čtení.

`off` Posun přesunout ukazatel čtení vzhledem k `way`.

`way` Jeden z [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) výčty.

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*to**).

### <a name="remarks"></a>Poznámky

První člen funkce provede absolutní seek, druhý členská funkce provede relativní seek.

> [!NOTE]
> Nepoužívejte funkci druhý člen s textovými soubory, protože standardní C++ nepodporuje relativní bude hledat v textových souborů.

Pokud [nezdaří](../standard-library/basic-ios-class.md#fail) je nastavena hodnota false, první volání funkce člen **newpos** = [rdbuf –](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekpos –](../standard-library/basic-streambuf-class.md#pubseekpos)( `pos`), pro některé **pos_type –** dočasný objekt **newpos**. Pokud **nezdaří** je nastavena hodnota false, druhé volání funkce **newpos** = **rdbuf –** -> [pubseekoff –](../standard-library/basic-streambuf-class.md#pubseekoff)( `off`, `way`). V obou případech Pokud ( `off_type`) **newpos** == ( `off_type`)(-1) (umísťovací operace selže), volání funkce **istr**. [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**). Obě funkce vrátí  **\*to**.

Pokud [nezdaří](../standard-library/basic-ios-class.md#fail) má hodnotu true, členské funkce Neprovádět žádnou akci.

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

Vnořené třídy popisuje objekt, jehož deklarace struktur vstupní funkce formátovaný a neformátovaný tvar.

Třída sentry {veřejné: explicitní sentry (basic_istream\<Elem, Tr > & _Istr, bool _Noskip = false); operátor bool() const;};

### <a name="remarks"></a>Poznámky

Pokud `_Istr.` [dobrý](../standard-library/basic-ios-class.md#good) je nastavena hodnota true, konstruktoru:

- Volání `_Istr`. [Tie –](../standard-library/basic-ios-class.md#tie) -> [vyprázdnění](../standard-library/basic-ostream-class.md#flush) Pokud `_Istr`. `tie` není ukazatele null.

- Efektivně volá [ws](../standard-library/istream-functions.md#ws)( `_Istr`) Pokud `_Istr`. [příznaky](../standard-library/ios-base-class.md#flags)**&**[skipws](../standard-library/ios-functions.md#skipws) je nenulové hodnoty

Pokud po takové přípravy `_Istr`. **Dobrý** je nastavena hodnota false, volání konstruktoru `_Istr`. [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**). V každém případě konstruktoru ukládá hodnoty vrácené `_Istr`. **Dobrý** v **stav**. Novější volání **operátor bool** přináší tato uložené hodnoty.

## <a name="swap"></a>  basic_istream::swap

Výměny obsahu dvou `basic_istream` objekty.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parametry

`right` Odkaz na lvalue `basic_istream` objektu.

### <a name="remarks"></a>Poznámky

Volání členských funkcí [basic_ios::swap](../standard-library/basic-ios-class.md#swap)`(right)`. Také k výměně počet extrakce se počet extrakce pro `right`.

## <a name="sync"></a>  basic_istream::Sync

Synchronizuje vstupní zařízení přidružená datový proud s vyrovnávací paměti datový proud.

```cpp
int sync();
```

### <a name="return-value"></a>Návratová hodnota

Pokud [rdbuf –](../standard-library/basic-ios-class.md#rdbuf) je ukazatel s hodnotou null, funkce vrátí hodnotu -1. Jinak zavolá `rdbuf`  ->  [pubsync –](../standard-library/basic-streambuf-class.md#pubsync). Pokud, vrátí hodnotu -1, zavolá funkci [setstate –](../standard-library/basic-ios-class.md#setstate)( **badbit**) a vrátí hodnotu -1. Funkce, jinak vrátí hodnotu nula.

## <a name="tellg"></a>  basic_istream::tellg

Hlásí, že aktuální číst pozici v datovém proudu.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální pozici v datovém proudu.

### <a name="remarks"></a>Poznámky

Pokud [nezdaří](../standard-library/basic-ios-class.md#fail) je nastavena hodnota false, vrátí funkce člena [rdbuf –](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekoff –](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **v**). Funkce `pos_type`(-1).

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

PUT naposledy přečíst znak zpět do datového proudu.

```cpp
basic_istream<Elem, Tr>& unget();
```

### <a name="return-value"></a>Návratová hodnota

Datový proud (  **\*to**).

### <a name="remarks"></a>Poznámky

[Neformátovaný vstupní funkce](../standard-library/basic-istream-class.md) vrátí zpět předchozí prvek v datovém proudu, pokud je to možné, jako kdyby pomocí volání metody `rdbuf`  ->  [sungetc –](../standard-library/basic-streambuf-class.md#sungetc). Pokud [rdbuf –](../standard-library/basic-ios-class.md#rdbuf) je ukazatel s hodnotou null, nebo pokud volání `sungetc` vrátí **traits_type –::**[eof](../standard-library/basic-ios-class.md#eof), volání funkce [setstate –](../standard-library/basic-ios-class.md#setstate)() **badbit**). V každém případě vrátí  **\*to**.

Informace o tom `unget` může selhat, najdete v části [basic_streambuf::sungetc](../standard-library/basic-streambuf-class.md#sungetc).

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

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
