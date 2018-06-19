---
title: basic_stringstream – třída | Microsoft Docs
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
ms.openlocfilehash: 50ec60ef094660dfa722a3a5c1f73fd9141aeef4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912755"
---
# <a name="basicstringstream-class"></a>basic_stringstream – třída

Popisuje objekt, který řídí vložení a extrakce elementů a kódovaného objekty pomocí datového proudu vyrovnávací paměti třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

`Alloc` Allocator – třída.

`Elem` Typ elementu základní řetězce.

*Tr* vlastnosti znak specializuje na základní prvek řetězce.

## <a name="remarks"></a>Poznámky

Šablony třídy popisuje objekt, který řídí vložení a extrakce elementů a kódovaného objekty pomocí datového proudu vyrovnávací paměti třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>, elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**, a jehož elementy jsou přidělena Allocator – třída `Alloc`. Objekt ukládá objekt basic_stringbuf – třída < **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_stringstream](#basic_stringstream)|Vytvoří objekt typu `basic_stringstream`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type –](#allocator_type)|Typ je synonymum pro parametr šablony `Alloc`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rdbuf](#rdbuf)|Vrátí adresu uložené datového proudu vyrovnávací paměti typu `pointer` k [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str –](#str)|Nastaví nebo získá beze změny na pozici zápis textu do vyrovnávací paměti řetězců.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<sstream – >

**Namespace:** – std

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

`_Mode` Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

`str` Objekt typu `basic_string`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_iostream](../standard-library/basic-iostream-class.md)( **sb**), kde **sb** je objekt uložené třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`>. Také inicializuje **sb** ve volání basic_stringbuf < **Elem**, **Tr**, `Alloc`> ( `_Mode`).

Druhý konstruktor inicializuje základní třídu volání basic_iostream ( **sb**). Také inicializuje **sb** ve volání basic_stringbuf < **Elem**, **Tr**, `Alloc`> (_ *Str*, `_Mode`).

## <a name="rdbuf"></a>  basic_stringstream::rdbuf

Vrátí adresu uložené datového proudu vyrovnávací paměti typu **ukazatel** k [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresu uložené datového proudu vyrovnávací paměti typu **ukazatel** k basic_stringbuf < **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Příklad

V tématu [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `rdbuf`.

## <a name="str"></a>  basic_stringstream::str

Nastaví nebo získá beze změny na pozici zápis textu do vyrovnávací paměti řetězců.

```cpp
basic_string<Elem, Tr, Alloc> str() const;


void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

`_Newstr` Nový řetězec.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt třídy [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, jehož kopii pořadí řízené je řízené sekvenci  **\*to**.

### <a name="remarks"></a>Poznámky

Vrátí první členská funkce [rdbuf –](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Druhé volání funkce člen `rdbuf`  ->  **str**( `_Newstr`).

### <a name="example"></a>Příklad

V tématu [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) pro příklad, který používá **str**.

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
