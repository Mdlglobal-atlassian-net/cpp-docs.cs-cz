---
title: basic_istringstream – třída
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
ms.openlocfilehash: 6a8ead5f1014e7f750e01988241ab020431312da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376807"
---
# <a name="basic_istringstream-class"></a>basic_istringstream – třída

Popisuje objekt, který řídí extrakci prvků a kódovaných objektů z vyrovnávací paměti `Alloc` datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alloc*\
Třída alokátoru

*Elem*\
Typ základního prvku řetězce.

*Tr*\
Znakové znaky specializované na základní prvek řetězce.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který řídí extrakci prvků a kódovaných objektů z `Alloc` vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>, s prvky typu *Elem*, jehož znakové znaky jsou určeny třídou *Tr*a jejichž prvky jsou přiděleny alokátorem třídy *Alloc*. Objekt ukládá objekt třídy basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_istringstream](#basic_istringstream)|Vytvoří objekt typu `basic_istringstream`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ je synonymem pro `Alloc`parametr šablony .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rdbuf](#rdbuf)|Vrátí adresu uložené vyrovnávací paměti `pointer` datového proudu `Alloc` typu [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`,>.|
|[Str](#str)|Nastaví nebo získá text ve vyrovnávací paměti řetězce bez změny polohy zápisu.|
|[Swap](#swap)|Vymění hodnoty `basic_istringstream` v tomto objektu za hodnoty poskytnutého objektu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnoty tomuto `basic_istringstream` objektu z parametru objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<sstream>

**Obor názvů:** std

## <a name="basic_istringstreamallocator_type"></a><a name="allocator_type"></a>basic_istringstream::allocator_type

Typ je synonymem pro `Alloc`parametr šablony .

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstreambasic_istringstream"></a><a name="basic_istringstream"></a>basic_istringstream::basic_istringstream

Vytvoří objekt typu `basic_istringstream`.

```cpp
explicit basic_istringstream(
    ios_base::openmode _Mode = ios_base::in);

explicit basic_istringstream(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in);

basic_istringstream(
    basic_istringstream&& right);
```

### <a name="parameters"></a>Parametry

*_Mode*\
Jeden z výčtů v [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Objekt typu `basic_string`.

*Právo*\
Rvalue odkaz objektu. `basic_istringstream`

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu`sb`voláním `sb` [basic_istream](../standard-library/basic-istream-class.md)( ), kde `Tr` `Alloc` je uložený objekt třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`,>. Inicializuje se `sb` také `basic_stringbuf` <  `Elem` `Tr`na `Alloc` telefonním čísle , ,>( `_Mode` &#124; `ios_base::in`).

Druhý konstruktor inicializuje základní třídu voláním `basic_istream(sb)`. Inicializuje se `sb` také `basic_stringbuf` <  `Elem` `Tr`na `Alloc` telefonním čísle , ,>( `str`, `_Mode` &#124; `ios_base::in`).

Třetí konstruktor inicializuje objekt s obsahem *right*, považován za odkaz rvalue.

## <a name="basic_istringstreamoperator"></a><a name="op_eq"></a>basic_istringstream::operátor=

Přiřadí hodnoty tomuto `basic_istringstream` objektu z parametru objektu.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Rvalue odkaz na `basic_istringstream` objekt.

### <a name="remarks"></a>Poznámky

Operátor člena nahradí obsah objektu obsahem *right*, považovaný za přiřazení přesunutí odkazu na rvalue.

## <a name="basic_istringstreamrdbuf"></a><a name="rdbuf"></a>basic_istringstream::rdbuf

Vrátí adresu uložené vyrovnávací paměti `pointer` datového proudu typu `Alloc` [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa uložené vyrovnávací paměti `pointer` datového proudu typu basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Příklad

Viz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `rdbuf`.

## <a name="basic_istringstreamstr"></a><a name="str"></a>basic_istringstream::str

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

## <a name="basic_istringstreamswap"></a><a name="swap"></a>basic_istringstream::swap

Vymění hodnoty `basic_istringstream` dvou objektů.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Právo*|Odkaz `lvalue` na `basic_istringstream` objekt.|

### <a name="remarks"></a>Poznámky

Členská funkce vyměňuje hodnoty tohoto objektu a hodnoty *right*.

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
