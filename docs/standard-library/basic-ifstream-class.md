---
title: basic_ifstream – třída
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ifstream
- fstream/std::basic_ifstream::close
- fstream/std::basic_ifstream::is_open
- fstream/std::basic_ifstream::open
- fstream/std::basic_ifstream::rdbuf
- fstream/std::basic_ifstream::swap
helpviewer_keywords:
- std::basic_ifstream [C++]
- std::basic_ifstream [C++], close
- std::basic_ifstream [C++], is_open
- std::basic_ifstream [C++], open
- std::basic_ifstream [C++], rdbuf
- std::basic_ifstream [C++], swap
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
ms.openlocfilehash: 85a315ee393a002da4d0999569d4af6c34a37ee3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376844"
---
# <a name="basic_ifstream-class"></a>basic_ifstream – třída

Popisuje objekt, který řídí extrakci prvků a kódovaných objektů z `Tr` vyrovnávací paměti datového proudu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> s prvky typu `Elem`, jejichž znakové rysy jsou určeny třídou .

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Základní prvek vyrovnávací paměti souboru.

*Tr*\
Vlastnosti základního prvku vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Poznámky

Objekt ukládá objekt třídy `basic_filebuf` <  `Elem`, `Tr`>.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak číst v textu ze souboru.

```cpp
// basic_ifstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_class.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="input-basic_ifstream_classtxt"></a>Vstup: basic_ifstream_class.txt

```cpp
This is the contents of basic_ifstream_class.txt.
```

## <a name="output"></a>Výstup

```cpp
This is the contents of basic_ifstream_class.txt.
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ifstream](#basic_ifstream)|Inicializuje novou instanci objektu. `basic_ifstream`|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Zavřete](#close)|Zavře soubor.|
|[is_open](#is_open)|Určuje, zda je soubor otevřený.|
|[Otevřít](#open)|Otevře soubor.|
|[rdbuf](#rdbuf)|Vrátí adresu uložené vyrovnávací paměti datového proudu.|
|[Swap](#swap)|Vymění obsah `basic_ifstream` tohoto obsahu za obsah `basic_ifstream`poskytnutých .|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí obsah tohoto objektu datového proudu. Jedná se o přesunutí `rvalue` přiřazení zahrnující, který nezanechává kopii za sebou.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fstream>

**Obor názvů:** std

## <a name="basic_ifstreambasic_ifstream"></a><a name="basic_ifstream"></a>basic_ifstream::basic_ifstream

Vytvoří objekt typu `basic_ifstream`.

```cpp
basic_ifstream();

explicit basic_ifstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ifstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

basic_ifstream(basic_ifstream&& right);
```

### <a name="parameters"></a>Parametry

*_Filename*\
Název souboru, který chcete otevřít.

*_Mode*\
Jeden z výčtů v [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Výchozí ochrana při otevírání `shflag` souborů, která odpovídá parametru v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu `sb`voláním `sb` [basic_istream](../standard-library/basic-istream-class.md)( ), kde `Tr` je uložený objekt třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`,>. Inicializuje se `sb` také `basic_filebuf` <  `Elem` `Tr` voláním ,>.

Druhý a třetí konstruktory inicializuje základní `basic_istream` `sb`třídy voláním ( ). Inicializuje se `sb` také voláním [basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`> `sb`. [otevřeno](../standard-library/basic-filebuf-class.md#open) `_Filename`( `_Mode` `ios_base::in`, &#124; ). Pokud druhá funkce vrátí ukazatel null, konstruktor `failbit`volá **setstate**( ).

Čtvrtý konstruktor inicializuje objekt s `right`obsahem , považován za odkaz rvalue.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak číst v textu ze souboru. Chcete-li soubor vytvořit, podívejte se na příklad [pro basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).

```cpp
// basic_ifstream_ctor.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_ctor.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="basic_ifstreamclose"></a><a name="close"></a>basic_ifstream::zavřít

Zavře soubor.

```cpp
void close();
```

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Příklad

Viz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `close`.

## <a name="basic_ifstreamis_open"></a><a name="is_open"></a>basic_ifstream::is_open

Určuje, zda je soubor otevřený.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je soubor otevřený, **false** jinak.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [funkci rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Příklad

Viz [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) příklad, `is_open`který používá .

## <a name="basic_ifstreamopen"></a><a name="open"></a>basic_ifstream::otevřít

Otevře soubor.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
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

Členská funkce volá [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Název souboru*, `_Mode` &#124; **ios_base::in).** Pokud se nezdaří open,`failbit`funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)( ), který může vyvolat výjimku ios_base::selhání.

### <a name="example"></a>Příklad

Viz [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) pro příklad, který používá `open`.

## <a name="basic_ifstreamoperator"></a><a name="op_eq"></a>basic_ifstream::operátor=

Přiřadí obsah tohoto objektu datového proudu. Toto je přiřazení move zahrnující rvalue, která nezanechává kopii za sebou.

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Rvalue odkaz na `basic_ifstream` objekt.

### <a name="return-value"></a>Návratová hodnota

Vrací objekt `*this`.

### <a name="remarks"></a>Poznámky

Operátor člena nahradí obsah objektu pomocí obsahu *right*, považovaného za odkaz na rvalue. Další informace naleznete v tématu [Lvalues a Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md).

## <a name="basic_ifstreamrdbuf"></a><a name="rdbuf"></a>basic_ifstream::rdbuf

Vrátí adresu uložené vyrovnávací paměti datového proudu.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [basic_filebuf](../standard-library/basic-filebuf-class.md) objekt představující uloženou vyrovnávací paměť datového proudu.

### <a name="example"></a>Příklad

Viz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `rdbuf`.

## <a name="basic_ifstreamswap"></a><a name="swap"></a>basic_ifstream::swap

Vyměňuje obsah `basic_ifstream` dvou objektů.

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Odkaz na jinou vyrovnávací paměť datového proudu.

### <a name="remarks"></a>Poznámky

Členská funkce vyměňuje obsah tohoto objektu za obsah *right*.

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
