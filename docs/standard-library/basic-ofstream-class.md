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
ms.openlocfilehash: 9a8255a02c46a4ade33bd95635516e5d36fe8e64
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409795"
---
# <a name="basicofstream-class"></a>basic_ofstream – třída

Popisuje objekt, který řídí vkládání prvků a kódovaného objekty do vyrovnávací paměti datového proudu třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, s prvky typu `Elem`, jejichž vlastnosti znaků určuje třídu `Tr`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Základní prvek vyrovnávací paměti souboru.

*tr*<br/>
Vlastnosti základního prvku vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Poznámky

Když **wchar_t** specializace `basic_ofstream` zapíše do souboru, pokud je soubor otevřený v textovém režimu bude zapisovat sekvenci znakové sady MBCS. Vnitřní reprezentaci použije rezervu `wchar_t` znaků.

Objekt ukládá objekt třídy `basic_filebuf` <  `Elem`, `Tr`>.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `basic_ofstream` objektu a zapsat do něj text.

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
|[close](#close)|Soubor se zavře.|
|[is_open](#is_open)|Určuje, zda je soubor otevřený.|
|[open](#open)|Otevře se soubor.|
|[rdbuf](#rdbuf)|Vrátí adresu uloženou datový proud vyrovnávací paměti.|
|[swap](#swap)|Zamění obsah proměnných to `basic_ofstream` pro obsah ze zadaných `basic_ofstream`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí obsah tohoto objektu stream. Toto je zahrnující přiřazení pro přesun `rvalue reference` , nenechává kopii za sebou.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fstream – >

**Namespace:** std

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

*Náze_v souboru*<br/>
Název souboru, který se otevře.

*_Mode*<br/>
Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Výchozí soubor otevřít ochranu, odpovídá `shflag` parametr [_fsopen – _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md).

*doprava*<br/>
Odkaz rvalue na `basic_ofstream` objektů se používají k inicializaci to `basic_ofstream` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_ostream –](../standard-library/basic-ostream-class.md)(`sb`), kde `sb` je uložený objekt třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md) <  `Elem`, `Tr`>. Také inicializuje `sb` voláním `basic_filebuf` <  `Elem`, `Tr`>.

Druhý a třetí konstruktor inicializuje základní třídu voláním `basic_ostream`( **sb**). Také inicializuje `sb` voláním `basic_filebuf` <  `Elem`, `Tr`> a pak `sb`. [Otevřete](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::out`). Pokud druhá funkce vrátí ukazatel s hodnotou null, volá konstruktor [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

Čtvrtý konstruktor je funkce kopírování. Inicializuje objekt s obsahem *správné*, považován za odkaz rvalue.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `basic_ofstream` objektu a zapsat do něj text.

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

## <a name="close"></a>  basic_ofstream::Close

Soubor se zavře.

```cpp
void close();
```

### <a name="remarks"></a>Poznámky

Volání členských funkcí [rdbuf –](../standard-library/basic-ifstream-class.md#rdbuf)**->**[zavřete](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad, který používá `close`.

## <a name="is_open"></a>  basic_ofstream::is_open

Určuje, zda je soubor otevřen.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je soubor otevřen, **false** jinak.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf –](#rdbuf) **->** [is_open –](../standard-library/basic-filebuf-class.md#is_open).

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

## <a name="open"></a>  basic_ofstream::Open

Otevře se soubor.

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

*Náze_v souboru*<br/>
Název souboru, který se otevře.

*_Mode*<br/>
Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Výchozí soubor otevřít ochranu, odpovídá `shflag` parametr [_fsopen – _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

Volání členských funkcí [rdbuf –](#rdbuf) **->** [otevřete](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; `ios_base::out` ). Pokud se tato funkce vrátí ukazatel s hodnotou null, funkce zavolá [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) příklad, který používá `open`.

## <a name="op_eq"></a>  basic_ofstream::Operator =

Přiřadí obsah tohoto objektu stream. Toto je zahrnující přiřazení pro přesun `rvalue reference` , nenechává kopii za sebou.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Odkaz rvalue na `basic_ofstream` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `*this`.

### <a name="remarks"></a>Poznámky

Členský operátor nahradí obsah objektu s použitím obsah *správné*, považován za odkaz rvalue.

## <a name="rdbuf"></a>  basic_ofstream::rdbuf

Vrátí adresu uloženou datový proud vyrovnávací paměti.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu uloženou datový proud vyrovnávací paměti.

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad, který používá `rdbuf`.

## <a name="swap"></a>  basic_ofstream::swap

Vyměňuje obsahy dvě `basic_ofstream` objekty.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
`lvalue` Odkazovat na jiný `basic_ofstream` objektu.

### <a name="remarks"></a>Poznámky

Členská funkce vymění obsah tohoto objektu pro obsah *správné*.

## <a name="see-also"></a>Viz také:

[basic_ostream – třída](../standard-library/basic-ostream-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
