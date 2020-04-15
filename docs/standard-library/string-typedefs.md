---
title: '&lt;řetězcové&gt; příkazy'
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 1ee36d67d137c74e17fff845f9d412b2673f311e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376628"
---
# <a name="ltstringgt-typedefs"></a>&lt;řetězcové&gt; příkazy

||||
|-|-|-|
|[Řetězec](#string)|[u16řetězec](#u16string)|[u32řetězec](#u32string)|
|[wstring](#wstring)|

## <a name="string"></a><a name="string"></a>Řetězec

Typ, který popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) s prvky typu **char**.

Mezi další typedefs, `basic_string` které se specializují, patří [wstring](../standard-library/string-typedefs.md#wstring), [u16string](../standard-library/string-typedefs.md#u16string)a [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>Poznámky

Rovnocenná prohlášení jsou:

```cpp
string str("");

basic_string<char> str("");
```

Seznam konstruktorů řetězců naleznete [v tématu basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string"></a><a name="u16string"></a>u16řetězec

Typ, který popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) `char16_t`s prvky typu .

Mezi další typedefs, které se `basic_string` specializují, patří [wstring](../standard-library/string-typedefs.md#wstring), [string](../standard-library/string-typedefs.md#string)a [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>Poznámky

Seznam konstruktorů řetězců naleznete [v tématu basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string"></a><a name="u32string"></a>u32řetězec

Typ, který popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) `char32_t`s prvky typu .

Mezi `basic_string` další typedefs, které se specializují, patří [řetězec](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)a [wstring](../standard-library/string-typedefs.md#wstring).

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>Poznámky

Seznam konstruktorů řetězců naleznete [v tématu basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring"></a><a name="wstring"></a>wstring

Typ, který popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) s prvky typu **wchar_t**.

Mezi další typedefs, `basic_string` které se specializují, patří [řetězec](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)a [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>Poznámky

Rovnocenná prohlášení jsou:

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

Seznam konstruktorů řetězců naleznete [v tématu basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Velikost **wchar_t** je definována implementací. Pokud váš kód závisí na **tom, wchar_t** má určitou velikost, `sizeof(wchar_t)`zkontrolujte implementaci platformy (například s). Pokud potřebujete typ znaku řetězce s šířkou, která zaručeně zůstane stejná na všech platformách, použijte [řetězec](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)nebo [u32string](../standard-library/string-typedefs.md#u32string).

## <a name="see-also"></a>Viz také

[\<řetězec>](../standard-library/string.md)
