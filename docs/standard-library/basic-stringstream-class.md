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
ms.openlocfilehash: ebf9b87b60cf790a2ca032eb805095f277324178
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866282"
---
# <a name="basic_stringstream-class"></a>basic_stringstream – třída

Popisuje objekt, který ovládá vkládání a extrakci prvků a kódovaných objektů pomocí vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR**, `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

\ *přidělení*
Třída alokátoru

*Elem*\
Typ základního prvku řetězce.

*Tr*\
Vlastnosti znaků specializované na základní prvek řetězce.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který ovládá vkládání a extrakci prvků a kódovaných objektů pomocí vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR**, `Alloc`>, s prvky typu `Elem`, jejichž znakové vlastnosti jsou určeny třídou `Tr`a jejichž prvky jsou přiděleny pomocí přidělování třídy `Alloc`. Objekt ukládá objekt třídy basic_stringbuf < **elem**, **TR**`Alloc`>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_stringstream](#basic_stringstream)|Vytvoří objekt typu `basic_stringstream`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ je synonymum pro parametr šablony `Alloc`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rdbuf](#rdbuf)|Vrátí adresu vyrovnávací paměti uloženého datového proudu typu `pointer` do [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr``Alloc`>.|
|[str](#str)|Nastaví nebo získá text v bufferu řetězce beze změny pozice zápisu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<sstream >

**Obor názvů:** std

## <a name="allocator_type"></a>basic_stringstream:: allocator_type

Typ je synonymum pro parametr šablony `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstream"></a>basic_stringstream:: basic_stringstream

Vytvoří objekt typu `basic_stringstream`.

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Mode*\
Jeden z výčtů ve [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

\ *str*
Objekt typu `basic_string`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_iostream](../standard-library/basic-iostream-class.md)( **SB**), kde `sb` je uložený objekt třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR**`Alloc`>. Inicializuje také `sb` voláním basic_stringbuf < **elem**, **TR**`Alloc`> (`_Mode`).

Druhý konstruktor inicializuje základní třídu voláním basic_iostream ( **SB**). Inicializuje také `sb` voláním basic_stringbuf < **elem**, **TR**`Alloc`> (_ *str*, `_Mode`).

## <a name="rdbuf"></a>basic_stringstream:: rdbuf

Vrátí adresu vyrovnávací paměti uloženého datového proudu typu **ukazatel** na [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR**`Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa vyrovnávací paměti uloženého datového proudu typu `pointer` do basic_stringbuf < **elem**, **TR**`Alloc`>.

### <a name="example"></a>Příklad

Příklad, který používá `rdbuf`, naleznete v tématu [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) .

## <a name="str"></a>basic_stringstream:: str

Nastaví nebo získá text v bufferu řetězce beze změny pozice zápisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr*\
Nový řetězec.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt třídy [basic_string](../standard-library/basic-string-class.md)< **elem**, **TR**, `Alloc`>, jehož řízená sekvence je kopií sekvence řízené **\*m**.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Druhá členská funkce volá `rdbuf` -> **str**(`_Newstr`).

### <a name="example"></a>Příklad

Příklad, který používá `str`, naleznete v tématu [basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str) .

## <a name="see-also"></a>Viz také

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream – programování](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
