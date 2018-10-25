---
title: basic_stringstream – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7d874902b4bf3c92eaa3a5b3a5ac07ee19a0ef3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068869"
---
# <a name="basicstringstream-class"></a>basic_stringstream – třída

Popisuje objekt, který řídí vkládání a extrakci prvků a kódovaného objektů pomocí vyrovnávací paměť datového proudu třídy [basic_stringbuf –](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*ALLOC*<br/>
Třída alokátoru

*Elem*<br/>
Typ základního prvku objektu řetězec.

*tr*<br/>
Vlastnosti znaků specializované na základního elementu řetězce.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který řídí vkládání a extrakci prvků a kódovaného objektů pomocí vyrovnávací paměť datového proudu třídy [basic_stringbuf –](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>, s prvky typu `Elem`, jehož vlastnosti znaků určuje třídu `Tr`, jehož prvky jsou přiděluje alokátoru třídy `Alloc`. Objekt ukládá objekt basic_stringbuf – třída < **Elem**, **Tr**, `Alloc`>.

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
|[rdbuf](#rdbuf)|Vrátí adresu uloženou datový proud vyrovnávací paměti typu `pointer` k [basic_stringbuf –](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Nastaví nebo získá text ve vyrovnávací paměti řetězce beze změny pozici zápisu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<sstream >

**Namespace:** std

## <a name="allocator_type"></a>  basic_stringstream::allocator_type

Typ je synonymum pro parametr šablony `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstream"></a>  basic_stringstream::basic_stringstream

Vytvoří objekt typu `basic_stringstream`.

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*Reži_m*<br/>
Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*str*<br/>
Objekt typu `basic_string`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_iostream –](../standard-library/basic-iostream-class.md)( **sb**), kde `sb` je uložený objekt třídy [basic_stringbuf –](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`>. Také inicializuje `sb` ve volání basic_stringbuf – < **Elem**, **Tr**, `Alloc`> ( `_Mode`).

Druhý konstruktor inicializuje pomocí volání basic_iostream – základní třídy ( **sb**). Také inicializuje `sb` ve volání basic_stringbuf – < **Elem**, **Tr**, `Alloc`> (_ *Str*, `_Mode`).

## <a name="rdbuf"></a>  basic_stringstream::rdbuf

Vrátí adresu uloženou datový proud vyrovnávací paměti typu **ukazatel** k [basic_stringbuf –](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa vyrovnávací paměti datového proudu uložené typu `pointer` k basic_stringbuf – < **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad, který používá `rdbuf`.

## <a name="str"></a>  basic_stringstream::str

Nastaví nebo získá text ve vyrovnávací paměti řetězce beze změny pozici zápisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr*<br/>
Nový řetězec.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt třídy [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, jehož kopii sekvence řízenou parametrem je řízené sekvence  **\*to**.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [rdbuf –](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Druhé volání funkcí členských `rdbuf`  ->  **str**( `_Newstr`).

### <a name="example"></a>Příklad

Zobrazit [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) příklad, který používá `str`.

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
