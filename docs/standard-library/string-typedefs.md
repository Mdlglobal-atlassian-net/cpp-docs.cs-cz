---
title: '&lt;řetězec&gt; definice typedef'
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 950ca5ae34b6469c3d79b7297d4fe7b7644d2fcf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856503"
---
# <a name="ltstringgt-typedefs"></a>&lt;řetězec&gt; definice typedef

||||
|-|-|-|
|[string](#string)|[u16string](#u16string)|[u32string](#u32string)|
|[wstring](#wstring)|

## <a name="string"></a>řetezce

Typ, který popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) s elementy typu **char**.

Další definice typedef, které specializují `basic_string` zahrnují [wstring](../standard-library/string-typedefs.md#wstring), [u16string](../standard-library/string-typedefs.md#u16string)a [u32string](../standard-library/string-typedefs.md#u32string).

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

Typ, který popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) prvky typu `char16_t`.

Další definice typedef, které specializují `basic_string` zahrnují [wstring](../standard-library/string-typedefs.md#wstring), [String](../standard-library/string-typedefs.md#string)a [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>Poznámky

Seznam konstruktorů řetězců naleznete v tématu [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string"></a>u32string

Typ, který popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) prvky typu `char32_t`.

Další definice typedef, které specializují `basic_string` zahrnují [řetězec](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)a [wstring](../standard-library/string-typedefs.md#wstring).

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>Poznámky

Seznam konstruktorů řetězců naleznete v tématu [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring"></a>wstring

Typ, který popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) prvky typu **wchar_t**.

Další definice typedef, které specializují `basic_string` zahrnují [řetězec](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)a [u32string](../standard-library/string-typedefs.md#u32string).

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
> Velikost **wchar_t** je definovaná implementací. Pokud váš kód závisí na tom, **wchar_t** má být určitá velikost, ověřte implementaci vaší platformy (například pomocí `sizeof(wchar_t)`). Pokud potřebujete typ řetězce znaků s šířkou, která je zaručena, aby zůstala stejná na všech platformách, použijte [řetězec](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)nebo [u32string](../standard-library/string-typedefs.md#u32string).

## <a name="see-also"></a>Viz také

[\<řetězec >](../standard-library/string.md)
