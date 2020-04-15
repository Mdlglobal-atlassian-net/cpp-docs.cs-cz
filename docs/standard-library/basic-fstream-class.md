---
title: basic_fstream – třída
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_fstream
- fstream/std::basic_fstream::close
- fstream/std::basic_fstream::is_open
- fstream/std::basic_fstream::open
- fstream/std::basic_fstream::rdbuf
- fstream/std::basic_fstream::swap
helpviewer_keywords:
- std::basic_fstream [C++]
- std::basic_fstream [C++], close
- std::basic_fstream [C++], is_open
- std::basic_fstream [C++], open
- std::basic_fstream [C++], rdbuf
- std::basic_fstream [C++], swap
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
ms.openlocfilehash: 80992430d6bef6fc46106452dfaa44cc0ed9e71c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376851"
---
# <a name="basic_fstream-class"></a>basic_fstream – třída

Popisuje objekt, který řídí vkládání a extrakci prvků a kódovaných objektů pomocí `Tr` vyrovnávací paměti datového proudu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> s prvky typu `Elem`, jejichž znakové znaky jsou určeny třídou .

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Základní prvek vyrovnávací paměti souboru.

*Tr*\
Vlastnosti základního prvku vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Poznámky

Objekt ukládá objekt třídy `basic_filebuf` <  `Elem`, `Tr`>.

> [!NOTE]
> Get ukazatel a umístit ukazatel fstream objektu **nejsou** nezávislé na sobě navzájem. Pokud se přesune ukazatel get, tak se ukazatel put.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `basic_fstream` vytvořit objekt, který lze číst a zapisovat do.

```cpp
// basic_fstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    fstream fs("fstream.txt", ios::in | ios::out | ios::trunc);
    if (!fs.bad())
    {
        // Write to the file.
        fs << "Writing to a basic_fstream object..." << endl;
        fs.close();

        // Dump the contents of the file to cout.
        fs.open("fstream.txt", ios::in);
        cout << fs.rdbuf();
        fs.close();
    }
}
```

```Output
Writing to a basic_fstream object...
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_fstream](#basic_fstream)|Vytvoří objekt typu `basic_fstream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Zavřete](#close)|Zavře soubor.|
|[is_open](#is_open)|Určuje, zda je soubor otevřený.|
|[Otevřít](#open)|Otevře soubor.|
|[rdbuf](#rdbuf)|Vrátí adresu uložené vyrovnávací paměti datového proudu, `Tr` ukazatele typu [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`,>.|
|[Swap](#swap)|Vymění obsah tohoto objektu s `basic_fstream` obsahem jiného objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fstream>

**Obor názvů:** std

## <a name="basic_fstreambasic_fstream"></a><a name="basic_fstream"></a>basic_fstream::basic_fstream

Vytvoří objekt typu `basic_fstream`.

```cpp
basic_fstream();

explicit basic_fstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_fstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_fstream(basic_fstream&& right);
```

### <a name="parameters"></a>Parametry

*_Filename*\
Název souboru, který chcete otevřít.

*_Mode*\
Jeden z výčtů v [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Výchozí ochrana při otevírání souborů, která odpovídá parametru *shflag* v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu`sb`voláním `sb` [basic_iostream](../standard-library/basic-iostream-class.md)( ), kde je uložený objekt třídy [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>. To `sb` také inicializuje `basic_filebuf` \< voláním **Elem**, **Tr**>.

Druhý a třetí konstruktory inicializuje základní `basic_iostream`třídy voláním ( **sb**). Také inicializuje `sb` `basic_filebuf` \< voláním **Elem**, **Tr**> a potom **sb.**[open](../standard-library/basic-filebuf-class.md#open)(_ Název *souboru*, `_Mode`). Pokud druhá funkce vrátí ukazatel null, konstruktor`failbit`volá [setstate](../standard-library/basic-ios-class.md#setstate)( ).

Čtvrtý konstruktor inicializuje objekt s `right`obsahem , považován za odkaz rvalue.

### <a name="example"></a>Příklad

Viz [streampos](../standard-library/ios-typedefs.md#streampos) pro příklad, který používá `basic_fstream`.

## <a name="basic_fstreamclose"></a><a name="close"></a>basic_fstream::zavřít

Zavře soubor.

```cpp
void close();
```

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Příklad

Viz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad použití `close`.

## <a name="basic_fstreamis_open"></a><a name="is_open"></a>basic_fstream::is_open

Určuje, zda je soubor otevřený.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je soubor otevřený, **false** jinak.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [funkci rdbuf](#rdbuf)**->**[is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Příklad

Příklad použití `is_open` [viz basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open)

## <a name="basic_fstreamopen"></a><a name="open"></a>basic_fstream::otevřít

Otevře soubor.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
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
Výchozí ochrana při otevírání souborů, která odpovídá parametru *shflag* v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Název souboru*, `_Mode`). Pokud tato funkce vrátí ukazatel null, funkce `failbit`volá [setstate](../standard-library/basic-ios-class.md#setstate)( ).

### <a name="example"></a>Příklad

Příklad použití [viz basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) `open`

## <a name="basic_fstreamoperator"></a><a name="op_eq"></a>basic_fstream::operátor=

Přiřadí tomuto objektu obsah ze zadaného objektu datového proudu. Toto je přesunutí přiřazení, které zahrnuje rvalue, která nezanechává kopii za sebou.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Lvalue odkaz na `basic_fstream` objekt.

### <a name="return-value"></a>Návratová hodnota

Vrací objekt `*this`.

### <a name="remarks"></a>Poznámky

Operátor člena nahradí obsah objektu pomocí obsahu *right*, považovaného za odkaz na rvalue.

## <a name="basic_fstreamrdbuf"></a><a name="rdbuf"></a>basic_fstream::rdbuf

Vrátí adresu uložené vyrovnávací paměti datového proudu, ukazatele typu [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Adresa uložené vyrovnávací paměti datového proudu.

### <a name="example"></a>Příklad

Viz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad použití `rdbuf`.

## <a name="basic_fstreamswap"></a><a name="swap"></a>basic_fstream::swap

Vyměňuje obsah `basic_fstream` dvou objektů.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Odkaz `lvalue` na `basic_fstream` objekt.

### <a name="remarks"></a>Poznámky

Členská funkce si vyměňuje obsah tohoto objektu a obsah *right*.

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
