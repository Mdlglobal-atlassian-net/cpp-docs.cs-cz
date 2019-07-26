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
ms.openlocfilehash: 8d26d0fe0e4e4152cf05476f546b753650209dfe
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459592"
---
# <a name="basicfstream-class"></a>basic_fstream – třída

Popisuje objekt, který ovládá vkládání a extrakci prvků a kódovaných objektů pomocí vyrovnávací paměti datového proudu [](../standard-library/basic-filebuf-class.md)< třídy basic_filebuf `Tr``Elem`, >, s prvky typu `Elem`, jejichž znak vlastnosti jsou určeny třídou `Tr`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Základní prvek vyrovnávací paměti souboru.

*Recenzent*\
Vlastnosti základního prvku vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Poznámky

`basic_filebuf`Objekt ukládá objekt třídy <  `Elem`> .`Tr`

> [!NOTE]
> Ukazatel get a ukazatel Put objektu fstream – nejsou **nezávisle** na sobě navzájem nezávislé. Pokud se ukazatel get přesune, tak ukazatel vložení.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `basic_fstream` objekt, který lze číst a zapisovat do.

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
|[close](#close)|Zavře soubor.|
|[is_open](#is_open)|Určuje, zda je soubor otevřen.|
|[open](#open)|Otevře soubor.|
|[rdbuf](#rdbuf)|Vrátí adresu vyrovnávací paměti uloženého datového proudu typu ukazatel na [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>.|
|[swap](#swap)|Vyměňuje obsah tohoto objektu s obsahem jiného `basic_fstream` objektu.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<fstream – >

**Obor názvů:** std

## <a name="basic_fstream"></a>basic_fstream::basic_fstream

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
Název souboru, který se má otevřít

*_Mode*\
Jeden z výčtů v [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Výchozí ochrana při otevírání souborů, která odpovídá parametru *Shflag* v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_iostream](../standard-library/basic-iostream-class.md)(`sb`), kde `sb` je uložený objekt třídy [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **elem**, **TR**>. Inicializuje `sb` se také voláním `basic_filebuf` \< **elem**, **TR**>.

Druhý a třetí konstruktor inicializuje základní třídu voláním `basic_iostream`( **SB**). Inicializuje `sb` se také voláním `basic_filebuf` \< **elem**, **TR**> a potom **Sb.** [Open](../standard-library/basic-filebuf-class.md#open)(_ *filename*, `_Mode`). Pokud druhá funkce vrátí ukazatel s hodnotou null, konstruktor volá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

Čtvrtý konstruktor inicializuje objekt s obsahem `right`, který se považuje za odkaz rvalue.

### <a name="example"></a>Příklad

Příklad [](../standard-library/ios-typedefs.md#streampos) , který používá `basic_fstream`, naleznete v tématu streampos.

## <a name="close"></a>basic_fstream:: Close

Zavře soubor.

```cpp
void close();
```

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](#rdbuf) **->** [Close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Příklad

Příklad použití `close`naleznete v tématu [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) .

## <a name="is_open"></a>basic_fstream::is_open

Určuje, zda je soubor otevřen.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je soubor otevřený, jinak **false** .

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Příklad

Příklad použití `is_open`naleznete v tématu [basic_filebuf:: is_open](../standard-library/basic-filebuf-class.md#is_open) .

## <a name="open"></a>basic_fstream:: Open

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
Název souboru, který se má otevřít

*_Mode*\
Jeden z výčtů v [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Výchozí ochrana při otevírání souborů, která odpovídá parametru *Shflag* v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](#rdbuf) **->** [Open](../standard-library/basic-filebuf-class.md#open)(_ *filename*, `_Mode`). Pokud tato funkce vrací ukazatel s hodnotou null, funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)( `failbit`).

### <a name="example"></a>Příklad

Příklad použití `open`naleznete v tématu [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) .

## <a name="op_eq"></a>basic_fstream:: operator =

Přiřadí tomuto objektu obsah ze zadaného objektu streamu. Toto je přiřazení přesunutí, které zahrnuje rvalue, který neopouští kopii.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Odkaz l-hodnoty na `basic_fstream` objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí `*this`.

### <a name="remarks"></a>Poznámky

Členský operátor nahradí obsah objektu pomocí obsahu *vpravo*, který se považuje za odkaz rvalue.

## <a name="rdbuf"></a>basic_fstream:: rdbuf

Vrátí adresu vyrovnávací paměti uloženého datového proudu typu ukazatel na [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **elem**, **TR**>.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Adresa vyrovnávací paměti uloženého datového proudu.

### <a name="example"></a>Příklad

Příklad použití `rdbuf`naleznete v tématu [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) .

## <a name="swap"></a>basic_fstream:: swap

Vyměňuje obsah dvou `basic_fstream` objektů.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
`lvalue` Odkaz`basic_fstream` na objekt.

### <a name="remarks"></a>Poznámky

Členská funkce vyměňuje obsah tohoto objektu a obsahu *vpravo*.

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
