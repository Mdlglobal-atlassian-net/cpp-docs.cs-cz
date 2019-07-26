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
ms.openlocfilehash: a73803f25c4fb9e54703b8bca93e68fedb63074e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452510"
---
# <a name="basicofstream-class"></a>basic_ofstream – třída

Popisuje objekt, který řídí vložení prvků a zakódovaných objektů do vyrovnávací paměti datového proudu [](../standard-library/basic-filebuf-class.md)< třídy basic_filebuf `Tr``Elem`, >, s prvky typu `Elem`, jejichž znaky jsou určeny. třídou `Tr`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Základní prvek vyrovnávací paměti souboru.

*Recenzent*\
Vlastnosti základního prvku vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Poznámky

V případě  , že specializace `basic_ofstream` wchar_t zapisuje do souboru, je-li soubor otevřen v textovém režimu, bude zapisovat posloupnost znakové sady MBCS. Vnitřní reprezentace použije vyrovnávací paměť `wchar_t` znaků.

`basic_filebuf`Objekt ukládá objekt třídy <  `Elem`> .`Tr`

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `basic_ofstream` objekt a zapsat do něj text.

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
|[close](#close)|Zavře soubor.|
|[is_open](#is_open)|Určuje, zda je soubor otevřen.|
|[open](#open)|Otevře soubor.|
|[rdbuf](#rdbuf)|Vrátí adresu vyrovnávací paměti uloženého datového proudu.|
|[swap](#swap)|Vymění obsah tohoto `basic_ofstream` obsahu pro obsah poskytnutého `basic_ofstream`obsahu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí obsah tohoto objektu streamu. Toto je přiřazení přesunutí zahrnující `rvalue reference` , které neopouští kopii.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<fstream – >

**Obor názvů:** std

## <a name="basic_ofstream"></a>  basic_ofstream::basic_ofstream

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
Název souboru, který se má otevřít

*_Mode*\
Jeden z výčtů v [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Výchozí ochrana při otevírání souborů, která odpovídá `shflag` parametru v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

*Kliknutím*\
Odkaz rvalue na `basic_ofstream` objekt používaný k inicializaci tohoto `basic_ofstream` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_ostream](../standard-library/basic-ostream-class.md)(`sb`), kde `sb` je uložený objekt třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>. `sb` Inicializuje se <  `basic_filebuf`také voláním`Elem`>. `Tr`

Druhý a třetí konstruktor inicializuje základní třídu voláním `basic_ostream`( **SB**). `sb` Inicializuje se také `basic_filebuf`voláním <  `Elem` >a`sb`potom. `Tr` [otevřít](../standard-library/basic-filebuf-class.md#open) ( `_Filename`, `_Mode` &#124; `ios_base::out`). Pokud druhá funkce vrátí ukazatel s hodnotou null, konstruktor volá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

Čtvrtý konstruktor je funkce kopírování. Inicializuje objekt s obsahem *vpravo*, který se považuje za odkaz rvalue.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `basic_ofstream` objekt a zapsat do něj text.

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

## <a name="close"></a>basic_ofstream:: Close

Zavře soubor.

```cpp
void close();
```

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf) **->** [Close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Příklad

Příklad, který používá `close`, naleznete v tématu [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) .

## <a name="is_open"></a>basic_ofstream::is_open

Označuje, zda je soubor otevřen.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je soubor otevřený, jinak **false** .

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

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

## <a name="open"></a>basic_ofstream:: Open

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
Název souboru, který se má otevřít

*_Mode*\
Jeden z výčtů v [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Výchozí ochrana při otevírání souborů, která odpovídá `shflag` parametru v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](#rdbuf) **->** [Open](../standard-library/basic-filebuf-class.md#open)(_ *filename*, `_Mode` &#124; `ios_base::out`). Pokud tato funkce vrací ukazatel s hodnotou null, funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

### <a name="example"></a>Příklad

Příklad, který používá `open`, naleznete v tématu [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) .

## <a name="op_eq"></a>basic_ofstream:: operator =

Přiřadí obsah tohoto objektu streamu. Toto je přiřazení přesunutí zahrnující `rvalue reference` , které neopouští kopii.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Odkaz rvalue na `basic_ofstream` objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí `*this`.

### <a name="remarks"></a>Poznámky

Členský operátor nahradí obsah objektu pomocí obsahu *vpravo*, který se považuje za odkaz rvalue.

## <a name="rdbuf"></a>basic_ofstream:: rdbuf

Vrátí adresu vyrovnávací paměti uloženého datového proudu.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu vyrovnávací paměti uloženého datového proudu.

### <a name="example"></a>Příklad

Příklad, který používá `rdbuf`, naleznete v tématu [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) .

## <a name="swap"></a>  basic_ofstream::swap

Vyměňuje obsah dvou `basic_ofstream` objektů.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Odkaz na jiný `basic_ofstream`objekt. `lvalue`

### <a name="remarks"></a>Poznámky

Členská funkce vyměňuje obsah tohoto objektu pro obsah *vpravo*.

## <a name="see-also"></a>Viz také:

[basic_ostream – třída](../standard-library/basic-ostream-class.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
