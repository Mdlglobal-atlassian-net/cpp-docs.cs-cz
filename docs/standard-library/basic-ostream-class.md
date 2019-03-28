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
ms.openlocfilehash: 64a32513e9dc151e64fccdb0ef678a75588f0a41
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565724"
---
# <a name="basicostream-class"></a>basic_ostream – třída

Tato třída šablony popisuje objekt, který řídí vkládání prvků a kódovaného objekty do vyrovnávací paměti datového proudu s prvky typu `Elem`, označované také jako [char_type](../standard-library/basic-ios-class.md#char_type), jehož vlastnosti znaků jsou určené třídy `Tr`, označované také jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
A `char_type`.

*tr*<br/>
Znak `traits_type`.

## <a name="remarks"></a>Poznámky

Většinu člena funkce, které přetěžují [operátor <<](#basic_ostream_operator_lt_lt) jsou formátovaný výstup functions. Jsou podle tohoto vzoru vytvořené:

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

Dva další členské funkce jsou funkce neformátovaný výstup. Jsou podle tohoto vzoru vytvořené:

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

Obě volání funkce [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**) v případě, že dojde k chybě při vkládání prvků.

Basic_istream – třída objektu\< **Elem**, **Tr**> ukládá pouze virtuální základní objekt veřejné třídy [basic_ios –](../standard-library/basic-ios-class.md)  **\<Elem**, **Tr >**.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [basic_ofstream – třída](../standard-library/basic-ofstream-class.md) získat další informace o výstupní datové proudy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ostream](#basic_ostream)|Vytvoří `basic_ostream` objektu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Vyprázdnění](#flush)|Vyprázdní vyrovnávací paměť.|
|[Vložit](#put)|Vloží znak do datového proudu.|
|[seekp](#seekp)|Resetovat pozici v výstupního datového proudu.|
|[sentry](#sentry)|Vnořené třídy popisuje objekt, jehož deklarace struktur formátovaný výstup functions a funkce neformátovaný výstup.|
|[swap](#swap)|Vymění hodnoty tohoto `basic_ostream` objektu pro ty ze zadaných `basic_ostream` objektu.|
|[tellp](#tellp)|Umístění sestavy ve výstupní datový proud.|
|[write](#write)|Převádí znaky v datovém proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnotu ze zadaných `basic_ostream` objektu parametr s tímto objektem.|
|[operátor <<](#basic_ostream_operator_lt_lt)|Zapíše do datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<ostream >

**Namespace:** std

## <a name="basic_ostream"></a>  basic_ostream::basic_ostream

Vytvoří `basic_ostream` objektu.

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>Parametry

*strbuf*<br/>
Objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*<br/>
**Hodnota TRUE** pokud jde standardní datový proud; v opačném případě **false**.

*doprava*<br/>
Odkaz rvalue na objekt typu `basic_ostream`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [init](../standard-library/basic-ios-class.md#init)(`strbuf`). Druhý konstruktor inicializuje základní třídu voláním [basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) získat další informace o výstupní datové proudy.

## <a name="flush"></a>  basic_ostream::Flush

Vyprázdní vyrovnávací paměť.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream –.

### <a name="remarks"></a>Poznámky

Pokud [rdbuf –](../standard-library/basic-ios-class.md#rdbuf) není ukazatel s hodnotou null, volání funkce **-> rdbuf –**[pubsync –](../standard-library/basic-streambuf-class.md#pubsync). Pokud, která vrátí hodnotu -1, funkce zavolá [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**). Vrátí  **\*to**.

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

## <a name="basic_ostream_operator_lt_lt"></a>  basic_ostream::operator&lt;&lt;

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

*Pfn*<br/>
Ukazatel na funkci.

*strbuf*<br/>
Ukazatel `stream_buf` objektu.

*Val*<br/>
Element k zápisu do datového proudu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream –.

### <a name="remarks"></a>Poznámky

\<Ostream > záhlaví také definuje několik operátorů globální vložení. Další informace najdete v tématu [operátor <<](../standard-library/ostream-operators.md#op_lt_lt).

První členská funkce zajišťuje, že výraz ve tvaru `ostr << endl` volání [endl](../standard-library/ostream-functions.md#endl)**(ostr)** a vrátí  **\*to**. Druhý a třetí funkce zajišťují další manipulátory, jako například [hex](../standard-library/ios-functions.md#hex), se chovají podobně. Zbývající funkce jsou všechny funkce formátovaný výstup.

Funkce

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

Extrahuje prvky z *strbuf*, pokud *strbuf* není ukazatel s hodnotou null a vloží je. Extrakce zastaví na konec souboru, nebo pokud je extrakce vyvolá výjimku (což je znovu vyvolána). Také zastaví, bez extrahování elementu Nejistá, pokud se nezdaří vložení. Pokud funkce vloží žádné elementy, nebo pokud je extrakce vyvolá výjimku, funkce zavolá [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). V každém případě funkce vrací  **\*to**.

Funkce

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

Převede `_Val` na logickou hodnotu pole a vloží ho voláním [use_facet](../standard-library/basic-filebuf-class.md#open)**< num_put –\<Elem, OutIt >**`(`[getloc –](../standard-library/ios-base-class.md#getloc)). [Vložit](#put)(**OutIt**([rdbuf –](../standard-library/basic-ios-class.md#rdbuf)),  **\*to**, `getloc`, **val**). Tady `OutIt` je definován jako [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<Elem, Tr >**. Funkce vrátí  **\*to**.

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

Každý převod *val* číselného pole a vložit ho voláním **use_facet < num_put –\<Elem, OutIt >**(`getloc`). **Vložit**(**OutIt**(`rdbuf`),  **\*to**, `getloc`, **val**). Tady **OutIt** je definován jako **ostreambuf_iterator\<Elem, Tr >**. Funkce vrátí  **\*to**.

Funkce

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

Každý převod *val* číselného pole a vložit ho voláním **use_facet < num_put –\<Elem, OutIt >**(`getloc`)**. Umístěte**(**OutIt**(`rdbuf`),  **\*to**, `getloc`, **val**). Tady **OutIt** je definován jako **ostreambuf_iterator\<Elem, Tr >**. Funkce vrátí  **\*to**.

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

## <a name="op_eq"></a>  basic_ostream::Operator =

Přiřadí hodnoty poskytnuté `basic_ostream` objektu parametr s tímto objektem.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
`rvalue` Odkaz `basic_ostream` objektu.

### <a name="remarks"></a>Poznámky

Členský operátor volá prohození `(right)`.

## <a name="put"></a>  basic_ostream::Put

Vloží znak do datového proudu.

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*<br/>
Znak.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream –.

### <a name="remarks"></a>Poznámky

Funkce neformátovaný výstupní vloží prvek *_Ch*. Vrátí  **\*to**.

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

## <a name="seekp"></a>  basic_ostream::seekp

Obnovte pozici v výstupního datového proudu.

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>Parametry

*_Pos*<br/>
Pozice ve streamu.

*_Off*<br/>
Posun vzhledem k *_Way*.

*_Way*<br/>
Jeden z [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) výčty.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream –.

### <a name="remarks"></a>Poznámky

Pokud [selhání](../standard-library/basic-ios-class.md#fail) je **false**, první volání členských funkcí **newpos =** [rdbuf –](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos –](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*), pro některé `pos_type` dočasný objekt `newpos`. Pokud `fail` má hodnotu false, druhé volání funkce **newpos = rdbuf – - >** [pubseekoff –](../standard-library/basic-streambuf-class.md#pubseekoff)(*_Off _Way*). V obou případech Pokud (`off_type`)**newpos ==** (`off_type`)(-1) (umístění operace selže), pak funkce volá **istr.** [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Obě funkce vrátí  **\*to**.

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

## <a name="sentry"></a>  basic_ostream::sentry

Vnořené třídy popisuje objekt, jehož deklarace struktur formátovaný výstup functions a funkce neformátovaný výstup.

Třída sentry {public: explicitní sentry (basic_ostream –\<Elem, Tr > & _Ostr); operator bool() const; ~ sentry();};

### <a name="remarks"></a>Poznámky

Vnořené třídy popisuje objekt, jehož deklarace struktur formátovaný výstup functions a funkce neformátovaný výstup. Pokud **ostr.** [dobré](../standard-library/basic-ios-class.md#good) je **true** a **ostr.** [tie](../standard-library/basic-ios-class.md#tie) není ukazatel s hodnotou null, volá konstruktor **-> ostr.tie**[vyprázdnění](#flush). Konstruktor pak uloží hodnotu vrácenou příkazem `ostr.good` v `status`. Pozdější volání `operator bool` poskytuje tuto uloženou hodnotu.

Pokud `uncaught_exception` vrátí **false** a [příznaky](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) nenulové, volání destruktoru [vyprázdnění](#flush).

## <a name="swap"></a>  basic_ostream::swap

Vymění hodnoty tohoto `basic_ostream` objektu pro hodnoty ze zadaných `basic_ostream`.

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Odkaz na `basic_ostream` objektu.

### <a name="remarks"></a>Poznámky

Volání členských funkcí [basic_ios::swap](../standard-library/basic-ios-class.md#swap) `(right)` k výměně obsahu tohoto objektu pro obsah *správné*.

## <a name="tellp"></a>  basic_ostream::tellp

Umístění sestavy ve výstupní datový proud.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Návratová hodnota

Pozice v výstupního datového proudu.

### <a name="remarks"></a>Poznámky

Pokud [selhání](../standard-library/basic-ios-class.md#fail) je **false**, členská funkce vrátí [rdbuf –](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekoff –](../standard-library/basic-streambuf-class.md#pubseekoff) (0, `cur`, **v**). V opačném případě vrátí `pos_type`(-1).

### <a name="example"></a>Příklad

Zobrazit [seekp –](#seekp) příklad použití `tellp`.

## <a name="write"></a>  basic_ostream::Write

Vložení znaků v datovém proudu.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Parametry

*Počet*<br/>
Počet znaků k vložení do datového proudu.

*str*<br/>
Znaky do datového proudu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt basic_ostream –.

### <a name="remarks"></a>Poznámky

[Funkce neformátovaný výstupní](../standard-library/basic-ostream-class.md) vloží sekvenci *počet* prvky počínaje *str*.

### <a name="example"></a>Příklad

Zobrazit [streamsize](../standard-library/ios-typedefs.md#streamsize) příklad použití `write`.

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
