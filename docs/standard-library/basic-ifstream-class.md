---
title: basic_ifstream – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- fstream/std::basic_ifstream
- fstream/std::basic_ifstream::close
- fstream/std::basic_ifstream::is_open
- fstream/std::basic_ifstream::open
- fstream/std::basic_ifstream::rdbuf
- fstream/std::basic_ifstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_ifstream [C++]
- std::basic_ifstream [C++], close
- std::basic_ifstream [C++], is_open
- std::basic_ifstream [C++], open
- std::basic_ifstream [C++], rdbuf
- std::basic_ifstream [C++], swap
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2e641dbea0507c51987d67e78b3cd8ef8be0dc6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958501"
---
# <a name="basicifstream-class"></a>basic_ifstream – třída

Popisuje objekt, který řídí extrakce prvků a kódovaného objekty z vyrovnávací paměti datového proudu třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, s prvky typu `Elem`, jejichž vlastnosti znaků určuje třídu `Tr`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem* základního prvku vyrovnávací paměti souboru.

*Tr* osobnostní rysy základního prvku vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Poznámky

Objekt ukládá objekt třídy `basic_filebuf` <  `Elem`, `Tr`>.

## <a name="example"></a>Příklad

Následující příklad znázorňuje způsob čtení textu ze souboru.

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

## <a name="input-basicifstreamclasstxt"></a>Vstup: basic_ifstream_class.txt

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
|[basic_ifstream](#basic_ifstream)|Inicializuje novou instanci třídy `basic_ifstream` objektu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[close](#close)|Soubor se zavře.|
|[is_open](#is_open)|Určuje, zda je soubor otevřený.|
|[open](#open)|Otevře se soubor.|
|[rdbuf](#rdbuf)|Vrátí adresu uloženou datový proud vyrovnávací paměti.|
|[Prohození](#swap)|Vymění obsah této `basic_ifstream` obsahu poskytnutého `basic_ifstream`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí obsah tohoto objektu stream. Toto je zahrnující přiřazení pro přesun `rvalue` , nenechává kopii za sebou.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fstream – >

**Namespace:** std

## <a name="basic_ifstream"></a>  basic_ifstream::basic_ifstream

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

*Náze_v souboru* název souboru, který se otevře.

*Reži_m* jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot* výchozí soubor otevřít ochranu, odpovídá `shflag` parametr [_fsopen – _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_istream](../standard-library/basic-istream-class.md)( `sb`), kde `sb` je uložený objekt třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md) <  `Elem`, `Tr`>. Také inicializuje `sb` voláním `basic_filebuf` <  `Elem`, `Tr`>.

Druhý a třetí konstruktor inicializuje základní třídu voláním `basic_istream`( `sb`). Také inicializuje `sb` voláním [basic_filebuf –](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`>, pak `sb`. [Otevřete](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::in`). Pokud druhá funkce vrátí ukazatel s hodnotou null, volá konstruktor **setstate**( `failbit`).

Čtvrtý konstruktor inicializuje objekt s obsahem `right`, považován za odkaz rvalue.

### <a name="example"></a>Příklad

Následující příklad znázorňuje způsob čtení textu ze souboru. K vytvoření souboru, podívejte se na příklad pro [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).

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

## <a name="close"></a>  basic_ifstream::Close

Soubor se zavře.

```cpp
void close();
```

### <a name="remarks"></a>Poznámky

Volání členských funkcí [rdbuf –](#rdbuf) **->** [zavřete](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad, který používá `close`.

## <a name="is_open"></a>  basic_ifstream::is_open

Určuje, zda je soubor otevřený.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je soubor otevřen, **false** jinak.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf –](#rdbuf) **->** [is_open –](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) příklad, který používá `is_open`.

## <a name="open"></a>  basic_ifstream::Open

Otevře se soubor.

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

*Náze_v souboru* název souboru, který se otevře.

*Reži_m* jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot* výchozí soubor otevřít ochranu, odpovídá `shflag` parametr [_fsopen – _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Poznámky

Volání členských funkcí [rdbuf –](#rdbuf) **->** [otevřete](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124;  **ios_base::in**). Pokud otevřete selže, volání funkce [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`), který může vyvolat výjimku ios_base::failure.

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) příklad, který používá `open`.

## <a name="op_eq"></a>  basic_ifstream::Operator =

Přiřadí obsah tohoto objektu stream. Toto je přiřazení pro přesun zahrnující rvalue kopii nenechává za sebou.

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>Parametry

*správné* odkaz rvalue na `basic_ifstream` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `*this`.

### <a name="remarks"></a>Poznámky

Členský operátor nahradí obsah objektu s použitím obsah *správné*, považován za odkaz rvalue. Další informace najdete v tématu [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

## <a name="rdbuf"></a>  basic_ifstream::rdbuf

Vrátí adresu uloženou datový proud vyrovnávací paměti.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [basic_filebuf –](../standard-library/basic-filebuf-class.md) objekt představující uložené datový proud vyrovnávací paměti.

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad, který používá `rdbuf`.

## <a name="swap"></a>  basic_ifstream::swap

Vyměňuje obsahy dvě `basic_ifstream` objekty.

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>Parametry

*správné* odkaz na jiný datový proud vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Členská funkce vymění obsah tohoto objektu pro obsah *správné*.

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
