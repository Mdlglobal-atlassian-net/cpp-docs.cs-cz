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
ms.openlocfilehash: b88411316ae247499100a044a0a2dfb3c53bc84f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689987"
---
# <a name="basic_istringstream-class"></a>basic_istringstream – třída

Popisuje objekt, který ovládá extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **elem**, **TR**, `Alloc` >.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

@No__t_1 *přidělení*
Třída alokátoru

*Elem* \
Typ základního prvku řetězce.

*Tr* \
Vlastnosti znaků specializované na základní prvek řetězce.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který řídí extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **elem**, **TR**, `Alloc` >, s prvky typu *elem*, jejichž znak vlastnosti jsou určeny třídou *TR*a jejichž prvky jsou přiděleny přidělováním *přidělení*třídy. Objekt ukládá objekt třídy basic_stringbuf < **elem**, **Tr**, `Alloc` >.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_istringstream](#basic_istringstream)|Vytvoří objekt typu `basic_istringstream`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ je synonymum pro parametr šablony `Alloc`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rdbuf](#rdbuf)|Vrátí adresu vyrovnávací paměti uloženého datového proudu typu `pointer` do [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem`, `Tr` `Alloc` >.|
|[str](#str)|Nastaví nebo získá text v bufferu řetězce beze změny pozice zápisu.|
|[adresu](#swap)|Vyměňuje hodnoty v tomto objektu `basic_istringstream` pro objekty poskytnutého objektu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnoty tomuto objektu `basic_istringstream` z parametru objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<sstream >

**Obor názvů:** std

## <a name="allocator_type"></a>basic_istringstream::allocator_type

Typ je synonymum pro parametr šablony `Alloc`.

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

*_Mode* \
Jeden z výčtů v [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

\ *str*
Objekt typu `basic_string`.

*pravé* \
Odkaz rvalue objektu `basic_istringstream`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_istream](../standard-library/basic-istream-class.md)(`sb`), kde `sb` je uložený objekt třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem`, `Tr` `Alloc` >. Inicializuje také `sb` voláním `basic_stringbuf` <  `Elem`, `Tr` `Alloc` > `_Mode` (`ios_base::in` &#124; ).

Druhý konstruktor inicializuje základní třídu voláním `basic_istream(sb)`. Inicializuje taky `sb` voláním `basic_stringbuf` <  `Elem`, `Tr` `Alloc` > `str` (`_Mode`, `ios_base::in` &#124; ).

Třetí konstruktor inicializuje objekt pomocí obsahu *vpravo*, který se považuje za odkaz rvalue.

## <a name="op_eq"></a>basic_istringstream:: operator =

Přiřadí hodnoty tomuto objektu `basic_istringstream` z parametru objektu.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Odkaz rvalue na objekt `basic_istringstream`.

### <a name="remarks"></a>Poznámky

Členský operátor nahradí obsah objektu obsahem *Right*, který je považován za přiřazení odkazu rvalue.

## <a name="rdbuf"></a>basic_istringstream:: rdbuf

Vrátí adresu vyrovnávací paměti uloženého datového proudu typu `pointer` do [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**, **TR**`Alloc` >.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa vyrovnávací paměti uloženého datového proudu typu `pointer` do basic_stringbuf < **elem**, **TR**`Alloc` >.

### <a name="example"></a>Příklad

Příklad, který používá `rdbuf`, naleznete v tématu [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) .

## <a name="str"></a>basic_istringstream:: str

Nastaví nebo získá text v bufferu řetězce beze změny pozice zápisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr* \
Nový řetězec.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt třídy [basic_string](../standard-library/basic-string-class.md) < **elem**, **TR**, `Alloc` >, jehož řízená sekvence je kopií sekvence řízené **\*this**.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [rdbuf](#rdbuf)  -> [str](../standard-library/basic-stringbuf-class.md#str). Druhá členská funkce volá `rdbuf`  -> **str**(`_Newstr`).

### <a name="example"></a>Příklad

Příklad, který používá `str`, naleznete v tématu [basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str) .

## <a name="swap"></a>basic_istringstream:: swap

Vyměňuje hodnoty dvou `basic_istringstream` objektů.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Kliknutím*|@No__t_0 odkaz na objekt `basic_istringstream`.|

### <a name="remarks"></a>Poznámky

Členská funkce vyměňuje hodnoty tohoto objektu a hodnoty *Right*.

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[iostream – programování](../standard-library/iostream-programming.md) \
[iostreams – konvence](../standard-library/iostreams-conventions.md)
