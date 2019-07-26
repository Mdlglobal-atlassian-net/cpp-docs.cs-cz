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
ms.openlocfilehash: 685195b13960c325076f1a38461394ada374d4b1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452534"
---
# <a name="basicistringstream-class"></a>basic_istringstream – třída

Popisuje objekt, který ovládá extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR** `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Vyhrazen*\
Třída alokátoru

*Elem*\
Typ základního prvku řetězce.

*Recenzent*\
Vlastnosti znaků specializované na základní prvek řetězce.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který ovládá extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR**, `Alloc`>, s prvky typu *elem*, jejichž vlastnosti znaků jsou určeny třídou *TR*a jejichž prvky jsou přiděleny přidělováním *přidělení*třídy. Objekt ukládá objekt třídy basic_stringbuf < **elem**, **TR**, `Alloc`>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_istringstream](#basic_istringstream)|Vytvoří objekt typu `basic_istringstream`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ je synonymum pro parametr `Alloc`šablony.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rdbuf](#rdbuf)|Vrátí adresu vyrovnávací `pointer` paměti uloženého datového proudu typu do [](../standard-library/basic-stringbuf-class.md)<  `Alloc`basic_stringbuf`Elem`, `Tr`>.|
|[str](#str)|Nastaví nebo získá text v bufferu řetězce beze změny pozice zápisu.|
|[swap](#swap)|Vyměňuje hodnoty v tomto `basic_istringstream` objektu pro objekty poskytnuté objektem.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnoty tomuto `basic_istringstream` objektu z parametru objektu.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<sstream >

**Obor názvů:** std

## <a name="allocator_type"></a>basic_istringstream::allocator_type

Typ je synonymum pro parametr `Alloc`šablony.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstream"></a>basic_istringstream::basic_istringstream

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
Jeden z výčtů v [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*str*\
Objekt typu `basic_string`.

*Kliknutím*\
Odkaz `basic_istringstream` rvalue objektu.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_istream](../standard-library/basic-istream-class.md)(`sb` `sb` ), kde je uložený objekt třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`> . `sb` Inicializuje se také voláním `basic_stringbuf` &#124; ,, > (`ios_base::in`). `Tr` `_Mode` <  `Elem` `Alloc`

Druhý konstruktor inicializuje základní třídu voláním metody `basic_istream(sb)`. `sb` Inicializuje se také voláním `basic_stringbuf` &#124; ,, > (`ios_base::in`, )`_Mode` . `Tr` `Elem` <  `Alloc` `str`

Třetí konstruktor inicializuje objekt pomocí obsahu *vpravo*, který se považuje za odkaz rvalue.

## <a name="op_eq"></a>basic_istringstream:: operator =

Přiřadí hodnoty tomuto `basic_istringstream` objektu z parametru objektu.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Odkaz rvalue na `basic_istringstream` objekt.

### <a name="remarks"></a>Poznámky

Členský operátor nahradí obsah objektu obsahem *Right*, který je považován za přiřazení odkazu rvalue.

## <a name="rdbuf"></a>basic_istringstream:: rdbuf

Vrátí adresu vyrovnávací paměti uloženého datového proudu typu `pointer` do [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR** `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa vyrovnávací `pointer` paměti uloženého datového proudu typu do basic_stringbuf < **elem**, **TR**, `Alloc`>.

### <a name="example"></a>Příklad

Příklad, který používá `rdbuf`, naleznete v tématu [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) .

## <a name="str"></a>  basic_istringstream::str

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

## <a name="swap"></a>  basic_istringstream::swap

Vyměňuje hodnoty dvou `basic_istringstream` objektů.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Kliknutím*|`lvalue` Odkaz`basic_istringstream` na objekt.|

### <a name="remarks"></a>Poznámky

Členská funkce vyměňuje hodnoty tohoto objektu a hodnoty *Right*.

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
