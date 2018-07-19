---
title: basic_istringstream – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53760cd2d69067fd93a76a35b0ba29fcc82a4664
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960066"
---
# <a name="basicistringstream-class"></a>basic_istringstream – třída

Popisuje objekt, který řídí extrakce prvků a kódovaného objekty z vyrovnávací paměti datového proudu třídy [basic_stringbuf –](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*ALLOC* třídu alokátoru.

*Elem* typ základního elementu řetězce.

*Tr* vlastností specializované na základního elementu řetězce.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který řídí extrakce prvků a kódovaného objekty z vyrovnávací paměti datového proudu třídy [basic_stringbuf –](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>, s prvky typu *Elem*, jehož vlastnosti znaků určuje třídu *Tr*, jehož prvky jsou přiděluje alokátoru třídy  *ALLOC*. Objekt ukládá objekt basic_stringbuf – třída < **Elem**, **Tr**, `Alloc`>.

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
|[rdbuf](#rdbuf)|Vrátí adresu uloženou datový proud vyrovnávací paměti typu `pointer` k [basic_stringbuf –](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Nastaví nebo získá text ve vyrovnávací paměti řetězce beze změny pozici zápisu.|
|[Prohození](#swap)|Vymění hodnoty v tomto `basic_istringstream` objektu pro ty zadaného objektu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnoty k tomuto `basic_istringstream` objektu z objektu parametru.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<sstream >

**Namespace:** std

## <a name="allocator_type"></a>  basic_istringstream::allocator_type

Typ je synonymum pro parametr šablony `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstream"></a>  basic_istringstream::basic_istringstream

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

*Reži_m* jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str* objekt typu `basic_string`.

*správné* z odkaz rvalue `basic_istringstream` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní třídu voláním [basic_istream](../standard-library/basic-istream-class.md)(`sb`), kde `sb` je uložený objekt třídy [basic_stringbuf –](../standard-library/basic-stringbuf-class.md) <  `Elem`, `Tr`, `Alloc`>. Také inicializuje `sb` voláním `basic_stringbuf` <  `Elem`, `Tr`, `Alloc`> ( `_Mode` &#124; `ios_base::in`).

Druhý konstruktor inicializuje základní třídu voláním `basic_istream(sb)`. Také inicializuje `sb` voláním `basic_stringbuf` <  `Elem`, `Tr`, `Alloc`> ( `str`, `_Mode` &#124; `ios_base::in`).

Třetí konstruktor inicializuje objekt s obsahem *správné*, považován za odkaz rvalue.

## <a name="op_eq"></a>  basic_istringstream::Operator =

Přiřadí hodnoty k tomuto `basic_istringstream` objektu z objektu parametru.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Parametry

*správné* odkaz rvalue na `basic_istringstream` objektu.

### <a name="remarks"></a>Poznámky

Členský operátor nahradí obsah objektu s obsahem *správné*, ošetřených přiřazení přesunu odkaz rvalue.

## <a name="rdbuf"></a>  basic_istringstream::rdbuf

Vrátí adresu uloženou datový proud vyrovnávací paměti typu `pointer` k [basic_stringbuf –](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa vyrovnávací paměti datového proudu uložené typu `pointer` k basic_stringbuf – < **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad, který používá `rdbuf`.

## <a name="str"></a>  basic_istringstream::str

Nastaví nebo získá text ve vyrovnávací paměti řetězce beze změny pozici zápisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;


void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr* nový řetězec.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt třídy [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, jehož kopii sekvence řízenou parametrem je řízené sekvence  **\*to**.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [rdbuf –](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Druhé volání funkcí členských `rdbuf`  ->  **str**( `_Newstr`).

### <a name="example"></a>Příklad

Zobrazit [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) příklad, který používá `str`.

## <a name="swap"></a>  basic_istringstream::swap

Vymění hodnoty dvou `basic_istringstream` objekty.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|`lvalue` Odkaz `basic_istringstream` objektu.|

### <a name="remarks"></a>Poznámky

Členská funkce vymění hodnoty tohoto objektu a hodnoty *správné*.

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
