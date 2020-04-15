---
title: basic_stringstream – třída
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
ms.openlocfilehash: f08689b1080837f042abfb3c4c52bb0ad558a448
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364874"
---
# <a name="basic_stringstream-class"></a>basic_stringstream – třída

Popisuje objekt, který řídí vkládání a extrakci prvků a kódovaných objektů pomocí vyrovnávací paměti `Alloc` datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alloc*\
Třída alokátoru

*Elem*\
Typ základního prvku řetězce.

*Tr*\
Znakové znaky specializované na základní prvek řetězce.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který řídí vkládání a extrakci prvků a kódovaných objektů pomocí `Alloc` vyrovnávací paměti datového `Elem`proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>, s prvky `Alloc`typu , jehož znakové znaky jsou určeny třídou `Tr`a jejichž prvky jsou přiděleny alokátorem třídy . Objekt ukládá objekt třídy basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_stringstream](#basic_stringstream)|Vytvoří objekt typu `basic_stringstream`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ je synonymem pro `Alloc`parametr šablony .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rdbuf](#rdbuf)|Vrátí adresu uložené vyrovnávací paměti `pointer` datového proudu `Alloc` typu [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`,>.|
|[Str](#str)|Nastaví nebo získá text ve vyrovnávací paměti řetězce bez změny polohy zápisu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<sstream>

**Obor názvů:** std

## <a name="basic_stringstreamallocator_type"></a><a name="allocator_type"></a>basic_stringstream::allocator_type

Typ je synonymem pro `Alloc`parametr šablony .

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstreambasic_stringstream"></a><a name="basic_stringstream"></a>basic_stringstream::basic_stringstream

Vytvoří objekt typu `basic_stringstream`.

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Mode*\
Jeden z výčtů v [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Objekt typu `basic_string`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_iostream](../standard-library/basic-iostream-class.md)( **sb** `sb` ), kde je uložený objekt třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>. Inicializuje `sb` se také na basic_stringbuf< `Alloc` **Elem**, **Tr**,>( `_Mode`).

Druhý konstruktor inicializuje základní třídu voláním basic_iostream( **sb**). Inicializuje `sb` se také na basic_stringbuf< `Alloc` **Elem**, `_Mode` **Tr**,>(_ *Str*).

## <a name="basic_stringstreamrdbuf"></a><a name="rdbuf"></a>basic_stringstream::rdbuf

Vrátí adresu uložené vyrovnávací paměti datového proudu **ukazatele** typu `Alloc` [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa uložené vyrovnávací paměti `pointer` datového proudu typu basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Příklad

Viz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `rdbuf`.

## <a name="basic_stringstreamstr"></a><a name="str"></a>basic_stringstream::str

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
