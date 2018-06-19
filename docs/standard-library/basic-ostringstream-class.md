---
title: basic_ostringstream – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce6e3a51cb63a448568f3cf31525f6f153637ec7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847114"
---
# <a name="basicostringstream-class"></a>basic_ostringstream – třída

Popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

`Alloc` Allocator – třída.

`Elem` Typ elementu základní řetězce.

*Tr* vlastnosti znak specializuje na základní prvek řetězce.

## <a name="remarks"></a>Poznámky

Třída popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**a jehož elementy jsou přidělena přidělení třídy `Alloc`. Objekt ukládá objekt basic_stringbuf – třída < **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ostringstream –](#basic_ostringstream)|Vytvoří objekt typu `basic_ostringstream`.|

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

## <a name="allocator_type"></a>  basic_ostringstream::allocator_type

Typ je synonymum pro parametr šablony `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstream"></a>  basic_ostringstream::basic_ostringstream

Vytvoří objekt basic_ostringstream typu.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

`_Mode` Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

`str` Objekt typu `basic_string`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_ostream](../standard-library/basic-ostream-class.md)( **sb**), kde **sb** je objekt uložené třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`>. Také inicializuje **sb** ve volání basic_stringbuf < **Elem**, **Tr**, `Alloc`> ( `_Mode` &#124; `ios_base::out`).

Druhý konstruktor inicializuje základní třídu volání basic_ostream ( **sb**). Také inicializuje **sb** ve volání basic_stringbuf < **Elem**, **Tr**, `Alloc`> (_ *Str*, `_Mode` &#124; `ios_base::out`).

## <a name="rdbuf"></a>  basic_ostringstream::rdbuf

Vrátí adresu uložené datového proudu vyrovnávací paměti typu **ukazatel** k [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresu uložené datového proudu vyrovnávací paměti typu **ukazatel** k basic_stringbuf < **Elem**, **Tr**, `Alloc`>.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uložené datového proudu vyrovnávací paměti typu **ukazatel** k basic_stringbuf < **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Příklad

V tématu [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `rdbuf`.

## <a name="str"></a>  basic_ostringstream::str

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
