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
ms.openlocfilehash: aa25c379e47bbe22efc78d65b3f6745e98098cbd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453513"
---
# <a name="basicostringstream-class"></a>basic_ostringstream – třída

Popisuje objekt, který řídí vložení prvků a zakódovaných objektů do vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR** `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Vyhrazen*\
Třída alokátoru

*Elem*\
Typ základního prvku řetězce.

*Recenzent*\
Vlastnosti znaků specializované na základní prvek řetězce.

## <a name="remarks"></a>Poznámky

Třída popisuje objekt, který řídí vložení prvků a zakódovaných objektů do vyrovnávací paměti datového proudu s prvky typu `Elem`, jejichž znaky jsou určeny třídou `Tr`a jejichž prvky jsou přiděleny pomocí přidělování Třída `Alloc`. Objekt ukládá objekt třídy basic_stringbuf < **elem**, **TR**, `Alloc`>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|Vytvoří objekt typu `basic_ostringstream`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ je synonymum pro *přidělení*parametru šablony.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rdbuf](#rdbuf)|Vrátí adresu vyrovnávací `pointer` paměti uloženého datového proudu typu do [](../standard-library/basic-stringbuf-class.md)<  `Alloc`basic_stringbuf`Elem`, `Tr`>.|
|[str](#str)|Nastaví nebo získá text v bufferu řetězce beze změny pozice zápisu.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<sstream >

**Obor názvů:** std

## <a name="allocator_type"></a>basic_ostringstream::allocator_type

Typ je synonymum pro *přidělení*parametru šablony.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstream"></a>basic_ostringstream::basic_ostringstream

Vytvoří objekt typu basic_ostringstream.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Mode*\
Jeden z výčtů v [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*str*\
Objekt typu `basic_string`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_ostream](../standard-library/basic-ostream-class.md)( **SB**), kde `sb` je uložený objekt `Alloc`třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR**>. Inicializuje také sestavovatele systému **SB** voláním basic_stringbuf < **elem**, `Alloc` **TR**, `_Mode` > ( &#124; `ios_base::out`).

Druhý konstruktor inicializuje základní třídu voláním basic_ostream ( **SB**). Inicializuje `sb` se také voláním basic_stringbuf < **elem**, **TR**, `Alloc`> (_ *str*, `_Mode` &#124; `ios_base::out`).

## <a name="rdbuf"></a>basic_ostringstream:: rdbuf

Vrátí adresu vyrovnávací paměti uloženého datového proudu typu `pointer` do [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR** `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa vyrovnávací `pointer` paměti uloženého datového proudu typu do basic_stringbuf < **elem**, **TR**, `Alloc`>.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uložené vyrovnávací paměti datového `pointer` proudu typu do basic_stringbuf < **elem**, **TR**, `Alloc`>.

### <a name="example"></a>Příklad

Příklad, který používá `rdbuf`, naleznete v tématu [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) .

## <a name="str"></a>  basic_ostringstream::str

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

Vrátí objekt třídy [basic_string](../standard-library/basic-string-class.md)< **elem**, **TR**, `Alloc`>, jehož řízená sekvence je kopií sekvence řízené  **\*tímto**nastavením.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Druhá členská funkce volá `rdbuf`  ->  **str**( `_Newstr`).

### <a name="example"></a>Příklad

Příklad, který používá `str`, naleznete v tématu [basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str) .

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
