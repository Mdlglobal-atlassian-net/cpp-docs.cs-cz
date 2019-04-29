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
ms.openlocfilehash: 894ac0bf7703bf68c9125d11023dbc32cfbb5941
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400668"
---
# <a name="basicfstream-class"></a>basic_fstream – třída

Popisuje objekt, který řídí vkládání a extrakci prvků a kódovaného objektů pomocí vyrovnávací paměť datového proudu třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, s prvky typu `Elem`, jehož vlastnosti znaků určuje třídu `Tr`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Základní prvek vyrovnávací paměti souboru.

*tr*<br/>
Vlastnosti základního prvku vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Poznámky

Objekt ukládá objekt třídy `basic_filebuf` <  `Elem`, `Tr`>.

> [!NOTE]
> Ukazatel get a put ukazatel objektu fstream – jsou **není** nezávisle na sobě navzájem. Pokud se přesune ukazatel get zločinců se stejně put ukazatele.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `basic_fstream` objekt, který může číst a zapisovat do.

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
|[close](#close)|Soubor se zavře.|
|[is_open](#is_open)|Určuje, zda je soubor otevřený.|
|[open](#open)|Otevře se soubor.|
|[rdbuf](#rdbuf)|Vrátí adresu uloženou streamu, typu ukazatele do [basic_filebuf –](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>.|
|[swap](#swap)|Vymění obsahu tohoto objektu s obsahem jiného `basic_fstream` objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fstream – >

**Namespace:** std

## <a name="basic_fstream"></a>  basic_fstream::basic_fstream

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

*Náze_v souboru*<br/>
Název souboru, který se otevře.

*_Mode*<br/>
Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Výchozí soubor otevřít ochranu, odpovídá *shflag* parametr [_fsopen – _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_iostream –](../standard-library/basic-iostream-class.md)(`sb`), kde `sb` je uložený objekt třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>. Také inicializuje `sb` voláním `basic_filebuf` \< **Elem**, **Tr**>.

Druhý a třetí konstruktor inicializuje základní třídu voláním `basic_iostream`( **sb**). Také inicializuje `sb` voláním `basic_filebuf` \< **Elem**, **Tr**> a potom **sb.**[otevřete](../standard-library/basic-filebuf-class.md#open)() _ *Filename*, `_Mode`). Pokud druhá funkce vrátí ukazatel s hodnotou null, volá konstruktor [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

Čtvrtý konstruktor inicializuje objekt s obsahem `right`, považován za odkaz rvalue.

### <a name="example"></a>Příklad

Zobrazit [streampos](../standard-library/ios-typedefs.md#streampos) příklad, který používá `basic_fstream`.

## <a name="close"></a>  basic_fstream::Close

Soubor se zavře.

```cpp
void close();
```

### <a name="remarks"></a>Poznámky

Volání členských funkcí [rdbuf –](#rdbuf) **->** [zavřete](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad, jak používat `close`.

## <a name="is_open"></a>  basic_fstream::is_open

Určuje, zda je soubor otevřený.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je soubor otevřen, **false** jinak.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf –](#rdbuf)**->**[is_open –](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) příklad, jak používat `is_open`.

## <a name="open"></a>  basic_fstream::Open

Otevře se soubor.

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

*Náze_v souboru*<br/>
Název souboru, který se otevře.

*_Mode*<br/>
Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Výchozí soubor otevřít ochranu, odpovídá *shflag* parametr [_fsopen – _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

Volání členských funkcí [rdbuf –](#rdbuf) **->** [otevřete](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode`). Pokud se tato funkce vrátí ukazatel s hodnotou null, funkce zavolá [setstate](../standard-library/basic-ios-class.md#setstate)( `failbit`).

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) příklad, jak používat `open`.

## <a name="op_eq"></a>  basic_fstream::Operator =

Přiřadí k tomuto objektu obsah z objektu zadaného datového proudu. Toto je přiřazení pro přesun, která zahrnuje rvalue kopii nenechává za sebou.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Odkaz na lvalue k `basic_fstream` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `*this`.

### <a name="remarks"></a>Poznámky

Členský operátor nahradí obsah objektu s použitím obsah *správné*, považován za odkaz rvalue.

## <a name="rdbuf"></a>  basic_fstream::rdbuf

Vrátí adresu uloženou streamu, typu ukazatele do [basic_filebuf –](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Adresa uložené datový proud vyrovnávací paměti.

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad, jak používat `rdbuf`.

## <a name="swap"></a>  basic_fstream::swap

Vyměňuje obsahy dvě `basic_fstream` objekty.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
`lvalue` Odkaz `basic_fstream` objektu.

### <a name="remarks"></a>Poznámky

Členská funkce vyměňuje obsahy tento objekt a obsah *správné*.

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
