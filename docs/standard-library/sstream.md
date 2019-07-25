---
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: 8284e56e8afb1e5518cbcbb772079b4f19d57b18
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451734"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

Definuje několik šablon třídy, které podporují operace iostreams na sekvencích uložených v přiděleném objektu Array. Tyto sekvence jsou snadno převedeny na objekty šablony třídy [basic_string](../standard-library/basic-string-class.md)a z nich.

## <a name="syntax"></a>Syntaxe

```cpp
namespace std {
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringbuf;
typedef basic_stringbuf<char>
stringbuf;
typedef basic_stringbuf<wchar_t> wstringbuf;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_istringstream;
typedef basic_istringstream<char>
istringstream;
typedef basic_istringstream<wchar_t> wistringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_ostringstream;
typedef basic_ostringstream<char>
ostringstream;
typedef basic_ostringstream<wchar_t> wostringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringstream;
typedef basic_stringstream<char>
stringstream;
typedef basic_stringstream<wchar_t> wstringstream;
// TEMPLATE FUNCTIONS
template <class CharType, class Traits, class Allocator>
void swap(
    basic_stringbuf<CharType, Traits, Allocator>& left,
    basic_stringbuf<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_istringstream<CharType, Traits, Allocator>& left,
    basic_istringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_ostringstream<CharType, Traits, Allocator>& left,
    basic_ostringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap (
    basic_stringstream<CharType, Traits, Allocator>& left,
    basic_stringstream<CharType, Traits, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*zbývá*|Odkaz na `sstream` objekt.|
|*Kliknutím*|Odkaz na `sstream` objekt.|

## <a name="remarks"></a>Poznámky

Objekty typu `char *` můžou používat [ \<funkce strstream >](../standard-library/strstream.md) pro streamování. Strstream > ale jsou zastaralé a je doporučováno \<použití sstream >. \<

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|Vytvoří typ `basic_istringstream` specializovaný na parametr **znak** šablony.|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|Vytvoří typ `basic_ostringstream` specializovaný na parametr **znak** šablony.|
|[stringbuf –](../standard-library/sstream-typedefs.md#stringbuf)|Vytvoří typ `basic_stringbuf` specializovaný na parametr **znak** šablony.|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|Vytvoří typ `basic_stringstream` specializovaný na parametr **znak** šablony.|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|Vytvoří typ `basic_istringstream` specializovaný na parametr šablony **wchar_t** .|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|Vytvoří typ `basic_ostringstream` specializovaný na parametr šablony **wchar_t** .|
|[wstringbuf –](../standard-library/sstream-typedefs.md#wstringbuf)|Vytvoří typ `basic_stringbuf` specializovaný na parametr šablony **wchar_t** .|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|Vytvoří typ `basic_stringstream` specializovaný na parametr šablony **wchar_t** .|

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|Vyměňuje hodnoty mezi dvěma `sstream` objekty.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|Popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků typu `Elem`, jejichž vlastnosti znaků jsou určeny třídou `Tr`, na a z sekvence prvků uložených v objektu Array.|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|Popisuje objekt, který ovládá extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**elem**, **TR**, `Alloc`>, s prvky typu `Elem`, jejichž znak vlastnosti jsou určeny třídou `Tr`a jejichž prvky jsou přiděleny pomocí přidělování třídy. `Alloc`|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|Popisuje objekt, který řídí vložení prvků a zakódovaných objektů do vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**elem**, **TR**, `Alloc`>, s prvky typu `Elem`, jejichž vlastnosti znaku jsou. jsou určeny třídou `Tr`a jejichž prvky jsou přiděleny pomocí přidělování třídy `Alloc`.|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|Popisuje objekt, který ovládá vkládání a extrakci prvků a kódovaných objektů pomocí vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**elem**, **TR**, `Alloc`>, s prvky typu `Elem`, jejichž vlastnosti znaků jsou určeny třídou `Tr`a jejichž prvky jsou přiděleny pomocí přidělování třídy. `Alloc`|

## <a name="requirements"></a>Požadavky

- **Hlavička:** \<sstream >

- **Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
