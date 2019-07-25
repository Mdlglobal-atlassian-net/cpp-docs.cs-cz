---
title: '&lt;definice typedef&gt; řetězce'
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: a1ade5547b98e4376a00f33d45d695a328b772d3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459237"
---
# <a name="ltstringgt-typedefs"></a>&lt;definice typedef&gt; řetězce

||||
|-|-|-|
|[string](#string)|[u16string](#u16string)|[u32string](#u32string)|
|[wstring](#wstring)|

## <a name="string"></a>řetezce

Typ, který popisuje specializaci třídy šablony [basic_string](../standard-library/basic-string-class.md) s elementy typu **char**.

`basic_string` Mezi další definice typedef, které specializují, patří [wstring](../standard-library/string-typedefs.md#wstring), [u16string](../standard-library/string-typedefs.md#u16string)a [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>Poznámky

Níže jsou uvedené ekvivalentní deklarace:

```cpp
string str("");

basic_string<char> str("");
```

Seznam konstruktorů řetězců naleznete v tématu [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string"></a>u16string

Typ, který popisuje specializaci třídy šablony [basic_string](../standard-library/basic-string-class.md) s prvky typu `char16_t`.

`basic_string` Mezi další definice typedef, které specializují, patří [wstring](../standard-library/string-typedefs.md#wstring), [String](../standard-library/string-typedefs.md#string)a [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>Poznámky

Seznam konstruktorů řetězců naleznete v tématu [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string"></a>u32string

Typ, který popisuje specializaci třídy šablony [basic_string](../standard-library/basic-string-class.md) s prvky typu `char32_t`.

`basic_string` Mezi další definice typedef, které specializují, patří [řetězec](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)a [wstring](../standard-library/string-typedefs.md#wstring).

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>Poznámky

Seznam konstruktorů řetězců naleznete v tématu [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring"></a>wstring

Typ, který popisuje specializaci třídy šablony [basic_string](../standard-library/basic-string-class.md) s prvky typu **wchar_t**.

`basic_string` Mezi další definice typedef, které specializují, patří [řetězec](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)a [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>Poznámky

Níže jsou uvedené ekvivalentní deklarace:

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

Seznam konstruktorů řetězců naleznete v tématu [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Velikost **wchar_t** je definovaná implementací. Pokud váš kód závisí na konkrétní velikosti příznakem **wchar_t** , ověřte implementaci vaší platformy (například pomocí `sizeof(wchar_t)`). Pokud potřebujete typ řetězce znaků s šířkou, která je zaručena, aby zůstala stejná na všech platformách, použijte [řetězec](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)nebo [u32string](../standard-library/string-typedefs.md#u32string).

## <a name="see-also"></a>Viz také:

[\<> řetězců](../standard-library/string.md)
