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
ms.openlocfilehash: 9025d595e79eed9f81aff77b931a2585359a8c3a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689979"
---
# <a name="basic_ostream-class"></a>basic_ostream – třída

Tato šablona třídy popisuje objekt, který řídí vložení prvků a zakódovaných objektů do vyrovnávací paměti datového proudu pomocí prvků typu `Elem`, označovaného také jako [char_type](../standard-library/basic-ios-class.md#char_type), jejichž znakové vlastnosti jsou určeny třídou `Tr`, označovanou také jako [ traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem* \
@No__t_0.

*Tr* \
Znak `traits_type`.

## <a name="remarks"></a>Poznámky

Většina členských funkcí, které přetěžování [operátor < <](#basic_ostream_operator_lt_lt) jsou formátované výstupní funkce. Postupuje podle vzoru:

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

Dvě další členské funkce jsou neformátované výstupní funkce. Postupuje podle vzoru:

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

Obě skupiny funkcí volají [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**), pokud při vkládání prvků narazí na selhání.

Objekt třídy basic_istream \< **elem**, **TR**> ukládá pouze virtuální veřejný objekt Base třídy [basic_ios](../standard-library/basic-ios-class.md)  **\<Elem**, **TR >** .

## <a name="example"></a>Příklad

Další informace o výstupních streamech najdete v příkladu pro [třídu basic_ofstream](../standard-library/basic-ofstream-class.md) .

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ostream](#basic_ostream)|Vytvoří objekt `basic_ostream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[zaznamenány](#flush)|Vyprázdní vyrovnávací paměť.|
|[převést](#put)|Vloží znak do datového proudu.|
|[seekp](#seekp)|Obnoví pozici ve výstupním datovém proudu.|
|[Ukázka](#sentry)|Vnořená Třída popisuje objekt, jehož deklarace strukturuje formátované výstupní funkce a neformátované výstupní funkce.|
|[adresu](#swap)|Vyměňuje hodnoty tohoto objektu `basic_ostream` pro objekty poskytnutého `basic_ostream`.|
|[tellp](#tellp)|Pozice sestav ve výstupním datovém proudu.|
|[write](#write)|Vloží znaky do datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnotu zadaného `basic_ostream` parametru objektu tomuto objektu.|
|[operátor < <](#basic_ostream_operator_lt_lt)|Zapisuje do datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<ostream >

**Obor názvů:** std

## <a name="basic_ostream"></a>basic_ostream::basic_ostream

Vytvoří objekt `basic_ostream`.

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>Parametry

*strbuf* \
Objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd* \
**true** , pokud se jedná o standardní datový proud; v opačném případě **false**.

*pravé* \
Odkaz rvalue na objekt typu `basic_ostream`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním metody [init](../standard-library/basic-ios-class.md#init)(`strbuf`). Druhý konstruktor inicializuje základní třídu voláním [basic_ios:: move](../standard-library/basic-ios-class.md#move) `(right)`.

### <a name="example"></a>Příklad

Další informace o výstupních streamech najdete v příkladu pro [basic_ofstream:: basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) .

## <a name="flush"></a>basic_ostream:: flush

Vyprázdní vyrovnávací paměť.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream.

### <a name="remarks"></a>Poznámky

Pokud [rdbuf](../standard-library/basic-ios-class.md#rdbuf) není ukazatel s hodnotou null, funkce volá **rdbuf->** [pubsync](../standard-library/basic-streambuf-class.md#pubsync). Pokud vrátí hodnotu-1, funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**). Vrátí **\*this**.

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

## <a name="basic_ostream_operator_lt_lt"></a>basic_ostream:: operator &lt; &lt;

Zapisuje do datového proudu.

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

*Pfn* \
Ukazatel na funkci.

*strbuf* \
Ukazatel na objekt `stream_buf`.

\ *Val*
Element, který se má zapsat do datového proudu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream.

### <a name="remarks"></a>Poznámky

Hlavička \<ostream > také definuje několik globálních operátorů vložení. Další informace najdete v tématu [operátor < <](../standard-library/ostream-operators.md#op_lt_lt).

První členská funkce zajistí, že výraz formuláře `ostr << endl` volá [endl](../standard-library/ostream-functions.md#endl) **(OSTR)** a potom vrátí **\*this**. Druhá a třetí funkce zajišťují, aby se podobným způsobem chovali další manipulace, například [hex](../standard-library/ios-functions.md#hex). Zbývající funkce jsou všechny formátované výstupní funkce.

Funkce

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

extrahuje prvky z *strbuf*, pokud *strbuf* není ukazatel s hodnotou null a vloží je. Extrakce se zastaví na konci souboru, nebo pokud extrakce vyvolá výjimku (která se znovu vyvolala). Také se zastaví, aniž by došlo k extrakci daného elementu, pokud vložení neproběhne úspěšně. Pokud funkce nevloží žádné elementy nebo pokud extrakce vyvolá výjimku, funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). V každém případě vrátí funkce **\*this**.

Funkce

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

Převede `_Val` na logické pole a vloží ho voláním [use_facet](../standard-library/basic-filebuf-class.md#open) **< Num_put \<Elem, OutIt >** `(`[getloc](../standard-library/ios-base-class.md#getloc)). [Put](#put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)), **\*this**, `getloc`, **Val**). Zde je `OutIt` definováno jako [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)  **\<Elem, TR >** . Funkce vrátí **\*this**.

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

Každý z nich převede *Val* na číselné pole a vloží ho voláním **use_facet < Num_put \<Elem, OutIt >** (`getloc`). **Put**(**OutIt**(`rdbuf`), **\*this**, `getloc`, **Val**). Zde je **OutIt** definován jako **Ostreambuf_iterator \<Elem, TR >** . Funkce vrátí **\*this**.

Funkce

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

Každý z nich převede *Val* na číselné pole a vloží ho voláním **use_facet < Num_put \<Elem, OutIt >** (`getloc` **). put**(**OutIt**(`rdbuf`), **\*this**, `getloc`, **Val**). Zde je **OutIt** definován jako **Ostreambuf_iterator \<Elem, TR >** . Funkce vrátí **\*this**.

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

## <a name="op_eq"></a>basic_ostream:: operator =

Přiřadí hodnoty pro zadaný `basic_ostream` parametr objektu tomuto objektu.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
@No__t_0 odkaz na objekt `basic_ostream`.

### <a name="remarks"></a>Poznámky

Operátor členu volá swap `(right)`.

## <a name="put"></a>basic_ostream::p UT

Vloží znak do datového proudu.

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch* \
Znak.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream.

### <a name="remarks"></a>Poznámky

Funkce naformátovaná Output vloží element *_Ch*. Vrátí **\*this**.

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

## <a name="seekp"></a>basic_ostream::seekp

Resetovat pozici ve výstupním datovém proudu.

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>Parametry

*_Pos* \
Pozice v datovém proudu.

*_Off* \
Posun vzhledem k *_Way*.

*_Way* \
Jeden z výčtů [ios_base:: seekdir](../standard-library/ios-base-class.md#seekdir) .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream.

### <a name="remarks"></a>Poznámky

Pokud [](../standard-library/basic-ios-class.md#fail) je selhání **false**, První členská funkce volá **newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf)  **->** [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)( *_Pos*) pro některé `pos_type` dočasné `newpos` objektů. Pokud je `fail` false, druhá funkce volá **newpos = rdbuf->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)( *_Off, _Way*). V obou případech, pokud (`off_type`)**newpos = =** (`off_type`) (-1) (operace umístění se nezdařila), funkce volá **ISTR.** [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Obě funkce vrací **\*this**.

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

## <a name="sentry"></a>basic_ostream:: Sentry

Vnořená Třída popisuje objekt, jehož deklarace strukturuje formátované výstupní funkce a neformátované výstupní funkce.

Třída Sentry {Public: Explicit Sentry (basic_ostream \<Elem, TR > & _Ostr); operátor bool () const; ~ Sentry ();};

### <a name="remarks"></a>Poznámky

Vnořená Třída popisuje objekt, jehož deklarace strukturuje formátované výstupní funkce a neformátované výstupní funkce. IF **OSTR.** [dobrá](../standard-library/basic-ios-class.md#good) **hodnota je true** a **OSTR.** propojení [není ukazatel](../standard-library/basic-ios-class.md#tie) s hodnotou null, konstruktor volá **OSTR. >** [vyprázdnění](#flush). Konstruktor pak uloží hodnotu vrácenou `ostr.good` v `status`. Pozdější volání `operator bool` doručuje tuto uloženou hodnotu.

Pokud `uncaught_exception` vrátí **hodnotu false** a [příznaky](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) je nenulové, volá destruktor [vyprázdnění](#flush).

## <a name="swap"></a>basic_ostream:: swap

Vyměňuje hodnoty tohoto `basic_ostream` objektu pro hodnoty poskytnuté `basic_ostream`.

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Odkaz na objekt `basic_ostream`.

### <a name="remarks"></a>Poznámky

Členská funkce volá [basic_ios:: swap](../standard-library/basic-ios-class.md#swap) `(right)` pro výměnu obsahu tohoto objektu pro obsah *vpravo*.

## <a name="tellp"></a>basic_ostream::tellp

Pozice sestavy ve výstupním datovém proudu.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Návratová hodnota

Pozice ve výstupním datovém proudu.

### <a name="remarks"></a>Poznámky

Pokud [](../standard-library/basic-ios-class.md#fail) je selhání **false**, vrátí členská funkce [rdbuf](../standard-library/basic-ios-class.md#rdbuf)  **->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur` **v**). V opačném případě vrátí `pos_type` (-1).

### <a name="example"></a>Příklad

Příklad použití `tellp` naleznete v tématu [seekp](#seekp) .

## <a name="write"></a>basic_ostream:: Write

Vložení znaků do datového proudu.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Parametry

*počet* \
Počet znaků, které mají být vloženy do datového proudu.

\ *str*
Znaky, které mají být vloženy do datového proudu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream.

### <a name="remarks"></a>Poznámky

[Funkce naformátovaná Output](../standard-library/basic-ostream-class.md) vloží sekvenci prvků *Count* začínající na *str*.

### <a name="example"></a>Příklad

Příklad použití `write` naleznete v tématu [StreamSize](../standard-library/ios-typedefs.md#streamsize) .

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[iostream – programování](../standard-library/iostream-programming.md) \
[iostreams – konvence](../standard-library/iostreams-conventions.md)
