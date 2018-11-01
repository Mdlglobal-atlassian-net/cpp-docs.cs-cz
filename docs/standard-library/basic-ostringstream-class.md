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
ms.openlocfilehash: 45a7eb1384c70b488e057fb9df8ad4c496272316
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582767"
---
# <a name="basicostringstream-class"></a>basic_ostringstream – třída

Popisuje objekt, který řídí vkládání prvků a kódovaného objekty do vyrovnávací paměti datového proudu třídy [basic_stringbuf –](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*ALLOC*<br/>
Třída alokátoru

*Elem*<br/>
Typ základního prvku objektu řetězec.

*tr*<br/>
Vlastnosti znaků specializované na základního elementu řetězce.

## <a name="remarks"></a>Poznámky

Tato třída popisuje objekt, který řídí vkládání prvků a kódovaného objekty do vyrovnávací paměti datového proudu s prvky typu `Elem`, jehož vlastnosti znaků určuje třídu `Tr`, jehož prvky jsou přiděluje přidělování z Třída `Alloc`. Objekt ukládá objekt basic_stringbuf – třída < **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_ostringstream –](#basic_ostringstream)|Vytvoří objekt typu `basic_ostringstream`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ je synonymum pro parametr šablony *alokační*.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rdbuf](#rdbuf)|Vrátí adresu uloženou datový proud vyrovnávací paměti typu `pointer` k [basic_stringbuf –](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Nastaví nebo získá text ve vyrovnávací paměti řetězce beze změny pozici zápisu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<sstream >

**Namespace:** std

## <a name="allocator_type"></a>  basic_ostringstream::allocator_type

Typ je synonymum pro parametr šablony *alokační*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstream"></a>  basic_ostringstream::basic_ostringstream

Vytvoří objekt basic_ostringstream – typu.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

*Reži_m*<br/>
Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*str*<br/>
Objekt typu `basic_string`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_ostream –](../standard-library/basic-ostream-class.md)( **sb**), kde `sb` je uložený objekt třídy [basic_stringbuf –](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`>. Také inicializuje **sb** ve volání basic_stringbuf – < **Elem**, **Tr**, `Alloc`> ( `_Mode` &#124; `ios_base::out`).

Druhý konstruktor inicializuje pomocí volání basic_ostream – základní třídy ( **sb**). Také inicializuje `sb` ve volání basic_stringbuf – < **Elem**, **Tr**, `Alloc`> (_ *Str*, `_Mode` &#124; `ios_base::out`).

## <a name="rdbuf"></a>  basic_ostringstream::rdbuf

Vrátí adresu uloženou datový proud vyrovnávací paměti typu `pointer` k [basic_stringbuf –](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa uložené datový proud vyrovnávací paměti typu `pointer` k basic_stringbuf – < **Elem**, **Tr**, `Alloc`>.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uloženou datový proud vyrovnávací paměti typu `pointer` k basic_stringbuf – < **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad, který používá `rdbuf`.

## <a name="str"></a>  basic_ostringstream::str

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
