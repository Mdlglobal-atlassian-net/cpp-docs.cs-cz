---
title: basic_ostream – třída
ms.date: 03/27/2019
f1_keywords:
- ostream/std::basic_ostream
- ostream/std::basic_ostream::flush
- ostream/std::basic_ostream::put
- ostream/std::basic_ostream::seekp
- ostream/std::basic_ostream::sentry
- ostream/std::basic_ostream::swap
- ostream/std::basic_ostream::tellp
- ostream/std::basic_ostream::write
helpviewer_keywords:
- std::basic_ostream [C++]
- std::basic_ostream [C++], flush
- std::basic_ostream [C++], put
- std::basic_ostream [C++], seekp
- std::basic_ostream [C++], sentry
- std::basic_ostream [C++], swap
- std::basic_ostream [C++], tellp
- std::basic_ostream [C++], write
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
ms.openlocfilehash: e074eb30d31c316411dd43f9a7a019defb64e9fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376767"
---
# <a name="basic_ostream-class"></a>basic_ostream – třída

Tato šablona třídy popisuje objekt, který řídí vkládání prvků a kódovaných objektů `Elem`do vyrovnávací paměti datového proudu s prvky typu , označované také jako [char_type](../standard-library/basic-ios-class.md#char_type), jehož znakové znaky jsou určeny třídou `Tr`, označovanou také jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Úloha `char_type`.

*Tr*\
Znak `traits_type`.

## <a name="remarks"></a>Poznámky

Většina členských funkcí, které přetížení [operátor<<](#basic_ostream_operator_lt_lt) jsou formátované výstupní funkce. Řídí se vzorem:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{try
{<convert and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
width(0);
// Except for operator<<(Elem)
setstate(state);

return (*this);
```

Dvě další členské funkce jsou neformátované výstupní funkce. Řídí se vzorem:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (!ok)
    state |= badbit;
else
{try
{<obtain and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
setstate(state);

return (*this);
```

Obě skupiny funkcí volání [setstate](../standard-library/basic-ios-class.md#setstate)**(badbit),** pokud dojde k selhání při vkládání prvků.

Objekt třídy\< basic_istream **Elem**, **Tr**> ukládá pouze virtuální objekt veřejné základny třídy [basic_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr>**.

## <a name="example"></a>Příklad

Další informace o výstupních datových proudech najdete v příkladu třídy [basic_ofstream.](../standard-library/basic-ofstream-class.md)

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ostream](#basic_ostream)|Vytvoří `basic_ostream` objekt.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[flush](#flush)|Vyprázdní vyrovnávací paměť.|
|[Dát](#put)|Vloží znak do datového proudu.|
|[hledat](#seekp)|Obnoví pozici ve výstupním datovém proudu.|
|[Sentry](#sentry)|Vnořená třída popisuje objekt, jehož deklarace strukturuje formátované výstupní funkce a neformátované výstupní funkce.|
|[Swap](#swap)|Vymění hodnoty `basic_ostream` tohoto objektu za `basic_ostream` hodnoty poskytnutého objektu.|
|[tellp](#tellp)|Hlásí pozici ve výstupním datovém proudu.|
|[Zápis](#write)|Vloží znaky do datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí tomuto objektu `basic_ostream` hodnotu zadaný parametr objektu.|
|[operátor<<](#basic_ostream_operator_lt_lt)|Zapíše do datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<ostream>

**Obor názvů:** std

## <a name="basic_ostreambasic_ostream"></a><a name="basic_ostream"></a>basic_ostream::basic_ostream

Vytvoří `basic_ostream` objekt.

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>Parametry

*strbuf (Strbuf)*\
Objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**true,** pokud se jedná o standardní datový proud; jinak **false**.

*Právo*\
Rvalue odkaz na objekt `basic_ostream`typu .

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [init](../standard-library/basic-ios-class.md#init)(`strbuf`). Druhý konstruktor inicializuje základní třídu voláním [basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)`.

### <a name="example"></a>Příklad

Další informace o výstupních datových proudech najdete v příkladu [pro basic_ofstream::basic_ofstream.](../standard-library/basic-ofstream-class.md#basic_ofstream)

## <a name="basic_ostreamflush"></a><a name="flush"></a>basic_ostream::vyprázdnění

Vyprázdní vyrovnávací paměť.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream.

### <a name="remarks"></a>Poznámky

Pokud [rdbuf](../standard-library/basic-ios-class.md#rdbuf) není ukazatel null, funkce volá **rdbuf->** [pubsync](../standard-library/basic-streambuf-class.md#pubsync). Pokud to vrátí -1, funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)**(badbit**). Vrátí ** \*toto**.

### <a name="example"></a>Příklad

```cpp
// basic_ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "test";
   cout.flush();
}
```

```Output
test
```

## <a name="basic_ostreamoperatorltlt"></a><a name="basic_ostream_operator_lt_lt"></a>basic_ostream::operátor&lt;&lt;

Zapíše do datového proudu.

```cpp
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& (* Pfn)(basic_ostream<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(
    ios_base& (* Pfn)(ios_base&));

basic_ostream<Elem, Tr>& operator<<(
    basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
basic_ostream<Elem, Tr>& operator<<(bool val);
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int __w64  val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long __w64  val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

### <a name="parameters"></a>Parametry

*Pfn*\
Ukazatel funkce.

*strbuf (Strbuf)*\
Ukazatel na `stream_buf` objekt.

*Val*\
Prvek pro zápis do datového proudu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream.

### <a name="remarks"></a>Poznámky

Záhlaví \<> ostream také definuje několik globálních operátorů vložení. Další informace naleznete v [tématu operátor<<](../standard-library/ostream-operators.md#op_lt_lt).

První členská funkce zajišťuje, že `ostr << endl` výraz formuláře volá [endl](../standard-library/ostream-functions.md#endl)**(ostr)** a potom vrátí ** \*toto**. Druhá a třetí funkce zajišťují, že ostatní manipulátory, například [hex](../standard-library/ios-functions.md#hex), se chovají podobně. Zbývající funkce jsou všechny formátované výstupní funkce.

Funkce

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

extrahuje prvky z *strbuf*, pokud *strbuf* není ukazatel null a vloží je. Extrakce zastaví na konci souboru, nebo pokud extrakce vyvolá výjimku (která je znovu vyvolána). Také zastaví, bez extrahování prvek v otázce, pokud se nezdaří vložení. Pokud funkce vloží žádné prvky nebo pokud extrakce vyvolá výjimku, funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). V každém případě funkce vrátí ** \*toto**.

Funkce

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

převede `_Val` na logické pole a vloží jej voláním [use_facet](../standard-library/basic-filebuf-class.md#open) **<num_put\<Elem, OutIt>** `(` [getloc](../standard-library/ios-base-class.md#getloc)). [(OutIt](#put)[),](../standard-library/basic-ios-class.md#rdbuf) ** \*toto**, `getloc`, **val**).**OutIt** Zde `OutIt` je definován jako [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<Elem, Tr>**. Funkce vrátí ** \*tuto**funkci .

Funkce

```cpp
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

každý převeďte *val* na číselné pole a vložte jej`getloc`voláním use_facet<**num_put\<Elem, OutIt>**( ). **(OutIt****OutIt**(`rdbuf`), ** \*** `getloc`to , , **val**). Zde, **OutIt** je definován jako **ostreambuf_iterator\<Elem, Tr>**. Funkce vrátí ** \*tuto**funkci .

Funkce

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

každý převést *val* na číselné pole a vložte jej voláním **use_facet<num_put\<Elem, OutIt>**(`getloc`)**. dát**(**OutIt**`rdbuf`( ), `getloc` ** \*to**, , **val**). Zde, **OutIt** je definován jako **ostreambuf_iterator\<Elem, Tr>**. Funkce vrátí ** \*tuto**funkci .

### <a name="example"></a>Příklad

```cpp
// basic_ostream_op_write.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_ostream<char, char_traits<char> >& somefunc(basic_ostream<char, char_traits<char> > &i)
{
    if (i == cout)
    {
        i << "i is cout" << endl;
    }
    return i;
}

class CTxtStreambuf : public basic_streambuf< char, char_traits< char > >
{
public:
    CTxtStreambuf(char *_pszText)
    {
        pszText = _pszText;
        setg(pszText, pszText, pszText + strlen(pszText));
    };
    char *pszText;
};

int main()
{
    cout << somefunc;
    cout << 21 << endl;

    hex2(cout);
    cout << 21 << endl;

    CTxtStreambuf f("text in streambuf");
    cout << &f << endl;
}
```

## <a name="basic_ostreamoperator"></a><a name="op_eq"></a>basic_ostream::operátor=

Přiřadí tomuto objektu hodnoty pro zadaný `basic_ostream` parametr objektu.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Odkaz `rvalue` na `basic_ostream` objekt.

### <a name="remarks"></a>Poznámky

Operátor člena volá `(right)`swap .

## <a name="basic_ostreamput"></a><a name="put"></a>basic_ostream::put

Vloží znak do datového proudu.

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Postava.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream.

### <a name="remarks"></a>Poznámky

Neformátovaná výstupní funkce vloží prvek *_Ch*. Vrátí ** \*toto**.

### <a name="example"></a>Příklad

```cpp
// basic_ostream_put.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout.put( 'v' );
   cout << endl;
   wcout.put( L'l' );
}
```

```Output
v
l
```

## <a name="basic_ostreamseekp"></a><a name="seekp"></a>basic_ostream::vyhledat

Obnovit pozici ve výstupním proudu.

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>Parametry

*_Pos*\
Pozice v proudu.

*_Off*\
Posun vzhledem k *_Way*.

*_Way*\
Jeden z [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) výčty.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream.

### <a name="remarks"></a>Poznámky

Pokud [fail](../standard-library/basic-ios-class.md#fail) je **false**, první členská funkce volá **newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*), pro některé `pos_type` dočasné objekt . `newpos` Pokud `fail` je false, druhá funkce volá **newpos = rdbuf->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(*_Off, _Way*). V obou případech,`off_type`pokud ( )`off_type`**newpos ==** ( )(-1) (operace umístění selže), pak funkce volá **istr.** [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Obě funkce ** \*vrátí tento**.

### <a name="example"></a>Příklad

```cpp
// basic_ostream_seekp.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main()
{
    using namespace std;
    ofstream x("basic_ostream_seekp.txt");
    streamoff i = x.tellp();
    cout << i << endl;
    x << "testing";
    i = x.tellp();
    cout << i << endl;
    x.seekp(2);   // Put char in third char position in file
    x << " ";

    x.seekp(2, ios::end);   // Put char two after end of file
    x << "z";
}
```

```Output
0
7
```

## <a name="basic_ostreamsentry"></a><a name="sentry"></a>basic_ostream::hlídka

Vnořená třída popisuje objekt, jehož deklarace strukturuje formátované výstupní funkce a neformátované výstupní funkce.

třída strážní { veřejná:\<explicitní hlídka (basic_ostream Elem, Tr>& _Ostr); operátor bool() const; ~sentry(); };

### <a name="remarks"></a>Poznámky

Vnořená třída popisuje objekt, jehož deklarace strukturuje formátované výstupní funkce a neformátované výstupní funkce. Pokud **ostr.** [dobré](../standard-library/basic-ios-class.md#good) je **pravda** **a ostr.** [kravata](../standard-library/basic-ios-class.md#tie) není ukazatel null, konstruktor volá **ostr.tie->** [flush](#flush). Konstruktor pak uloží hodnotu `ostr.good` `status`vrácenou v . Pozdější volání `operator bool` doručuje tuto uloženou hodnotu.

Pokud `uncaught_exception` vrátí **false** a [příznaky](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) je nenulová, destruktor volá [flush](#flush).

## <a name="basic_ostreamswap"></a><a name="swap"></a>basic_ostream::swap

Vymění hodnoty `basic_ostream` tohoto objektu za hodnoty `basic_ostream`poskytnutého objektu .

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Odkaz na `basic_ostream` objekt.

### <a name="remarks"></a>Poznámky

Členská funkce volá [basic_ios::swap](../standard-library/basic-ios-class.md#swap) `(right)` k výměně obsahu tohoto objektu za obsah *right*.

## <a name="basic_ostreamtellp"></a><a name="tellp"></a>basic_ostream::tellp

Pozice sestavy ve výstupním datovém proudu.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Návratová hodnota

Pozice ve výstupním proudu.

### <a name="remarks"></a>Poznámky

Pokud [fail](../standard-library/basic-ios-class.md#fail) je **false**, funkce člena vrátí [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **in**). V opačném `pos_type`případě vrátí (-1).

### <a name="example"></a>Příklad

Viz [seekp](#seekp) pro `tellp`příklad pomocí .

## <a name="basic_ostreamwrite"></a><a name="write"></a>basic_ostream::zápis

Vložte znaky do datového proudu.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Parametry

*Počet*\
Počet znaků, které chcete vložit do datového proudu.

*Str*\
Znaky, které chcete vložit do datového proudu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream.

### <a name="remarks"></a>Poznámky

[Neformátovaná výstupní funkce](../standard-library/basic-ostream-class.md) vloží sekvenci elementů *počtu* začínajících na *str*.

### <a name="example"></a>Příklad

Viz [velikost datového](../standard-library/ios-typedefs.md#streamsize) `write`proudu pro příklad pomocí .

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
