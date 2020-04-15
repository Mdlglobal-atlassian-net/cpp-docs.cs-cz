---
title: basic_ofstream – třída
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
ms.openlocfilehash: f2d0facd92e0ef1935f8218a6d323a62edb81e5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376786"
---
# <a name="basic_ofstream-class"></a>basic_ofstream – třída

Popisuje objekt, který řídí vkládání prvků a kódovaných objektů do [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`vyrovnávací `Tr` paměti datového proudu `Elem`třídy basic_filebuf ,> `Tr`s prvky typu , jejichž znakové znaky jsou určeny třídou .

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Základní prvek vyrovnávací paměti souboru.

*Tr*\
Vlastnosti základního prvku vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Poznámky

Když **wchar_t** specializace `basic_ofstream` zápisů do souboru, pokud je soubor otevřen v textovém režimu, napíše sekvenci MBCS. Vnitřní reprezentace bude používat `wchar_t` vyrovnávací paměť znaků.

Objekt ukládá objekt třídy `basic_filebuf` <  `Elem`, `Tr`>.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `basic_ofstream` vytvořit objekt a napsat do něj text.

```cpp
// basic_ofstream_class.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ofstream](#basic_ofstream)|Vytvoří objekt typu `basic_ofstream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Zavřete](#close)|Zavře soubor.|
|[is_open](#is_open)|Určuje, zda je soubor otevřený.|
|[Otevřít](#open)|Otevře soubor.|
|[rdbuf](#rdbuf)|Vrátí adresu uložené vyrovnávací paměti datového proudu.|
|[Swap](#swap)|Vyměňte jejich `basic_ofstream` obsah za obsah poskytnutého `basic_ofstream`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí obsah tohoto objektu datového proudu. Jedná se o přesunutí `rvalue reference` přiřazení zahrnující, který nezanechává kopii za sebou.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fstream>

**Obor názvů:** std

## <a name="basic_ofstreambasic_ofstream"></a><a name="basic_ofstream"></a>basic_ofstream::basic_ofstream

Vytvoří objekt typu `basic_ofstream`.

```cpp
basic_ofstream();

explicit basic_ofstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ofstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_ofstream(
    basic_ofstream&& right);
```

### <a name="parameters"></a>Parametry

*_Filename*\
Název souboru, který chcete otevřít.

*_Mode*\
Jeden z výčtů v [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Výchozí ochrana při otevírání `shflag` souborů, která odpovídá parametru v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

*Právo*\
Rvalue odkaz na `basic_ofstream` objekt, který se `basic_ofstream` používá k inicializaci tohoto objektu.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu`sb`voláním `sb` [basic_ostream](../standard-library/basic-ostream-class.md)( ), kde `Tr` je uložený objekt třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`,>. Inicializuje se `sb` také `basic_filebuf` <  `Elem` `Tr` voláním ,>.

Druhý a třetí konstruktory inicializuje základní `basic_ostream`třídy voláním ( **sb**). Také inicializuje `sb` `basic_filebuf` <  `Elem`voláním `Tr` , `sb`> a potom . [otevřeno](../standard-library/basic-filebuf-class.md#open) `_Filename`( `_Mode` `ios_base::out`, &#124; ). Pokud druhá funkce vrátí ukazatel null, konstruktor`failbit`volá [setstate](../standard-library/basic-ios-class.md#setstate)( ).

Čtvrtý konstruktor je funkce kopírování. Inicializuje objekt s obsahem *right*, považován za rvalue odkaz.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `basic_ofstream` vytvořit objekt a napsat do něj text.

```cpp
// basic_ofstream_ctor.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("C:\\ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

## <a name="basic_ofstreamclose"></a><a name="close"></a>basic_ofstream::zavřít

Zavře soubor.

```cpp
void close();
```

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf)**->**[close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Příklad

Viz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `close`.

## <a name="basic_ofstreamis_open"></a><a name="is_open"></a>basic_ofstream::is_open

Označuje, zda je soubor otevřen.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je soubor otevřený, **false** jinak.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [funkci rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Příklad

```cpp
// basic_ofstream_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   // Open and close with a basic_filebuf
   file.rdbuf( )->open( "basic_ofstream_is_open.txt", ios::in );
   file.close( );
   if (file.is_open())
      cout << "it's open" << endl;
   else
      cout << "it's closed" << endl;
}
```

## <a name="basic_ofstreamopen"></a><a name="open"></a>basic_ofstream::otevřít

Otevře soubor.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Parametry

*_Filename*\
Název souboru, který chcete otevřít.

*_Mode*\
Jeden z výčtů v [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Výchozí ochrana při otevírání `shflag` souborů, která odpovídá parametru v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Název souboru*, `_Mode` &#124; `ios_base::out`). Pokud tato funkce vrátí ukazatel null, funkce`failbit`volá [setstate](../standard-library/basic-ios-class.md#setstate)( ).

### <a name="example"></a>Příklad

Viz [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) pro příklad, který používá `open`.

## <a name="basic_ofstreamoperator"></a><a name="op_eq"></a>basic_ofstream::operátor=

Přiřadí obsah tohoto objektu datového proudu. Jedná se o přesunutí `rvalue reference` přiřazení zahrnující, který nezanechává kopii za sebou.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Rvalue odkaz na `basic_ofstream` objekt.

### <a name="return-value"></a>Návratová hodnota

Vrací objekt `*this`.

### <a name="remarks"></a>Poznámky

Operátor člena nahradí obsah objektu pomocí obsahu *right*, považovaného za odkaz na rvalue.

## <a name="basic_ofstreamrdbuf"></a><a name="rdbuf"></a>basic_ofstream::rdbuf

Vrátí adresu uložené vyrovnávací paměti datového proudu.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu uložené vyrovnávací paměti datového proudu.

### <a name="example"></a>Příklad

Viz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `rdbuf`.

## <a name="basic_ofstreamswap"></a><a name="swap"></a>basic_ofstream::swap

Vyměňuje obsah `basic_ofstream` dvou objektů.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Odkaz `lvalue` na `basic_ofstream` jiný objekt.

### <a name="remarks"></a>Poznámky

Členská funkce vyměňuje obsah tohoto objektu za obsah *right*.

## <a name="see-also"></a>Viz také

[basic_ostream třída](../standard-library/basic-ostream-class.md)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
