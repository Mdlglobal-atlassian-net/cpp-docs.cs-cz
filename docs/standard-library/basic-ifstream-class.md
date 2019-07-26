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
ms.openlocfilehash: 1e5e22c837ca2d6389591cec6d2cdd256ca50b1a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455520"
---
# <a name="basicifstream-class"></a>basic_ifstream – třída

Popisuje objekt, který ovládá extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu [](../standard-library/basic-filebuf-class.md)< třídy basic_filebuf `Tr``Elem`, >, s prvky typu `Elem`, jejichž znaky jsou určeno třídou `Tr`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Základní prvek vyrovnávací paměti souboru.

*Recenzent*\
Vlastnosti základního prvku vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Poznámky

`basic_filebuf`Objekt ukládá objekt třídy <  `Elem`> .`Tr`

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

## <a name="input-basicifstreamclasstxt"></a>Vstup: basic_ifstream_class. txt

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
|[basic_ifstream](#basic_ifstream)|Inicializuje novou instanci `basic_ifstream` objektu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[close](#close)|Zavře soubor.|
|[is_open](#is_open)|Určuje, zda je soubor otevřen.|
|[open](#open)|Otevře soubor.|
|[rdbuf](#rdbuf)|Vrátí adresu vyrovnávací paměti uloženého datového proudu.|
|[swap](#swap)|Vyměňuje obsah tohoto `basic_ifstream` obsahu pro obsah poskytnutého `basic_ifstream`obsahu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí obsah tohoto objektu streamu. Toto je přiřazení přesunutí zahrnující `rvalue` , které neopouští kopii.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<fstream – >

**Obor názvů:** std

## <a name="basic_ifstream"></a>basic_ifstream::basic_ifstream

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
Název souboru, který se má otevřít

*_Mode*\
Jeden z výčtů v [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Výchozí ochrana při otevírání souborů, která odpovídá `shflag` parametru v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_istream](../standard-library/basic-istream-class.md)( `sb`), kde `sb` je uložený objekt třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>. `sb` Inicializuje se <  `basic_filebuf`také voláním`Elem`>. `Tr`

Druhý a třetí konstruktor inicializuje základní třídu voláním `basic_istream`( `sb`). Inicializuje `sb` se také voláním [basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`> a potom `sb`. [otevřít](../standard-library/basic-filebuf-class.md#open) ( `_Filename`, `_Mode` &#124; `ios_base::in`). Pokud druhá funkce vrátí ukazatel s hodnotou null, konstruktor volá **setstate**( `failbit`).

Čtvrtý konstruktor inicializuje objekt s obsahem `right`, který se považuje za odkaz rvalue.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak číst v textu ze souboru. Chcete-li vytvořit soubor, přečtěte si příklad pro [basic_ofstream:: basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).

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

## <a name="close"></a>basic_ifstream:: Close

Zavře soubor.

```cpp
void close();
```

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](#rdbuf) **->** [Close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Příklad

Příklad, který používá `close`, naleznete v tématu [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) .

## <a name="is_open"></a>basic_ifstream::is_open

Určuje, zda je soubor otevřen.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je soubor otevřený, jinak **false** .

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Příklad

Příklad, který používá `is_open`, naleznete v tématu [basic_filebuf:: is_open](../standard-library/basic-filebuf-class.md#is_open) .

## <a name="open"></a>basic_ifstream:: Open

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
Název souboru, který se má otevřít

*_Mode*\
Jeden z výčtů v [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Výchozí ochrana při otevírání souborů, která odpovídá `shflag` parametru v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](#rdbuf) **->** [Open](../standard-library/basic-filebuf-class.md#open)(_ *filename*, `_Mode` &#124; **ios_base:: in**). Pokud se otevření nezdaří, funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`), která může vyvolat výjimku ios_base:: Failure.

### <a name="example"></a>Příklad

Příklad, který používá `open`, naleznete v tématu [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) .

## <a name="op_eq"></a>basic_ifstream:: operator =

Přiřadí obsah tohoto objektu streamu. Toto je přiřazení přesunutí zahrnující rvalue, které neopouští kopii.

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Odkaz rvalue na `basic_ifstream` objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí `*this`.

### <a name="remarks"></a>Poznámky

Členský operátor nahradí obsah objektu pomocí obsahu *vpravo*, který se považuje za odkaz rvalue. Další informace najdete v tématu [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

## <a name="rdbuf"></a>basic_ifstream:: rdbuf

Vrátí adresu vyrovnávací paměti uloženého datového proudu.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [basic_filebuf](../standard-library/basic-filebuf-class.md) představující vyrovnávací paměť uloženého datového proudu.

### <a name="example"></a>Příklad

Příklad, který používá `rdbuf`, naleznete v tématu [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) .

## <a name="swap"></a>  basic_ifstream::swap

Vyměňuje obsah dvou `basic_ifstream` objektů.

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Odkaz na jinou vyrovnávací paměť datového proudu.

### <a name="remarks"></a>Poznámky

Členská funkce vyměňuje obsah tohoto objektu pro obsah *vpravo*.

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
