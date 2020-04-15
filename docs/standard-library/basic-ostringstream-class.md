---
title: basic_ostringstream – třída
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
ms.openlocfilehash: 9e10474d3e4fb2a37e8ab52f77495758c37e8a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376778"
---
# <a name="basic_ostringstream-class"></a>basic_ostringstream – třída

Popisuje objekt, který řídí vkládání prvků a kódovaných objektů do vyrovnávací paměti datového `Alloc` proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alloc*\
Třída alokátoru

*Elem*\
Typ základního prvku řetězce.

*Tr*\
Znakové znaky specializované na základní prvek řetězce.

## <a name="remarks"></a>Poznámky

Třída popisuje objekt, který řídí vkládání prvků a kódovaných objektů do vyrovnávací paměti `Elem`datového proudu s prvky `Tr`typu , jejichž znakové vlastnosti jsou `Alloc`určeny třídou a jejichž prvky jsou přiděleny alokátorem třídy . Objekt ukládá objekt třídy basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|Vytvoří objekt typu `basic_ostringstream`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ je synonymem pro parametr šablony *Alloc*.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rdbuf](#rdbuf)|Vrátí adresu uložené vyrovnávací paměti `pointer` datového proudu `Alloc` typu [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`,>.|
|[Str](#str)|Nastaví nebo získá text ve vyrovnávací paměti řetězce bez změny polohy zápisu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<sstream>

**Obor názvů:** std

## <a name="basic_ostringstreamallocator_type"></a><a name="allocator_type"></a>basic_ostringstream::allocator_type

Typ je synonymem pro parametr šablony *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstreambasic_ostringstream"></a><a name="basic_ostringstream"></a>basic_ostringstream::basic_ostringstream

Vytvoří objekt typu basic_ostringstream.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Mode*\
Jeden z výčtů v [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Objekt typu `basic_string`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_ostream](../standard-library/basic-ostream-class.md)( **sb** `sb` ), kde je uložený objekt třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>. Inicializuje se také **na** basic_stringbuf< **Elem**, `_Mode` `ios_base::out` **Tr**, `Alloc`>( &#124;).

Druhý konstruktor inicializuje základní třídu voláním basic_ostream( **sb**). Inicializuje se `sb` také na telefonním čísle `Alloc` basic_stringbuf< `_Mode` **Elem**, **Tr**,>(_ *Str*, &#124; `ios_base::out`).

## <a name="basic_ostringstreamrdbuf"></a><a name="rdbuf"></a>basic_ostringstream::rdbuf

Vrátí adresu uložené vyrovnávací paměti `pointer` datového proudu typu `Alloc` [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa uložené vyrovnávací paměti datového `pointer` proudu typu basic_stringbuf< `Alloc` **Elem**, **Tr**,>.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uložené vyrovnávací `pointer` paměti datového proudu typu `Alloc` basic_stringbuf< **Elem**, **Tr**,>.

### <a name="example"></a>Příklad

Viz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `rdbuf`.

## <a name="basic_ostringstreamstr"></a><a name="str"></a>basic_ostringstream::str

Nastaví nebo získá text ve vyrovnávací paměti řetězce bez změny polohy zápisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr*\
Nový řetězec.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu objektu třídy `Alloc` [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**,>, jehož řízená sekvence je kopií sekvence řízené ** \*touto**hodnotou .

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Druhá členská `rdbuf`  -> funkce `_Newstr`volá **str**( ).

### <a name="example"></a>Příklad

Viz [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) pro příklad, který používá `str`.

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
