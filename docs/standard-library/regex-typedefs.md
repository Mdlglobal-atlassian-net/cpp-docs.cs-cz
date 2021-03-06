---
title: '&lt;regex&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- regex/std::cmatch
- regex/std::cregex_iterator
- regex/std::cregex_token_iterator
- regex/std::csub_match
- regex/std::regex
- regex/std::smatch
- regex/std::sregex_iterator
- regex/std::sregex_token_iterator
- regex/std::ssub_match
- regex/std::wcmatch
- regex/std::wcregex_iterator
- regex/std::wcregex_token_iterator
- regex/std::wcsub_match
- regex/std::wregex
- regex/std::wsmatch
- regex/std::wsregex_iterator
- regex/std::wsregex_token_iterator
- regex/std::wssub_match
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
ms.openlocfilehash: 5dbda2df4877da7594dd633e9f203a3780b4adb1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368548"
---
# <a name="ltregexgt-typedefs"></a>&lt;regex&gt; typedefs

||||
|-|-|-|
|[cmatch](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|
|[csub_match](#csub_match)|[Regex](#regex)|[shodu](#smatch)|
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|
|[wcmatch](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|
|[wcsub_match](#wcsub_match)|[wregex](#wregex)|[wsmatch (wsmatch)](#wsmatch)|
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|

## <a name="cmatch-typedef"></a><a name="cmatch"></a>cmatch Typedef

Definice typu pro char match_results.

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [match_results Class](../standard-library/match-results-class.md) pro iterátory typu `const char*`.

## <a name="cregex_iterator-typedef"></a><a name="cregex_iterator"></a>cregex_iterator Typedef

Definice typu pro regex_iterator znaku.

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [regex_iterator Class](../standard-library/regex-iterator-class.md) pro iterátory typu `const char*`.

## <a name="cregex_token_iterator-typedef"></a><a name="cregex_token_iterator"></a>cregex_token_iterator Typedef

Definice typu pro regex_token_iterator znaku

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [regex_token_iterator Class](../standard-library/regex-token-iterator-class.md) pro iterátory typu `const char*`.

## <a name="csub_match-typedef"></a><a name="csub_match"></a>csub_match Typedef

Definice typu pro sub_match znaku

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [sub_match Class](../standard-library/sub-match-class.md) pro iterátory typu `const char*`.

## <a name="regex-typedef"></a><a name="regex"></a>regex Typedef

Definice typu pro basic_regex znaku.

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [basic_regex Class](../standard-library/basic-regex-class.md) pro prvky typu **char**.

> [!NOTE]
> High-bit znaky budou mít `regex`nepředvídatelné výsledky s . Hodnoty mimo rozsah 0 až 127 může mít za následek nedefinované chování.

## <a name="smatch-typedef"></a><a name="smatch"></a>shoda Typedef

Definice typu pro match_results řetězců.

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [match_results Class](../standard-library/match-results-class.md) pro iterátory typu `string::const_iterator`.

## <a name="sregex_iterator-typedef"></a><a name="sregex_iterator"></a>sregex_iterator Typedef

Definice typu pro regex_iterator řetězců.

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [regex_iterator Class](../standard-library/regex-iterator-class.md) pro iterátory typu `string::const_iterator`.

## <a name="sregex_token_iterator-typedef"></a><a name="sregex_token_iterator"></a>sregex_token_iterator Typedef

Definice typu pro regex_token_iterator řetězců.

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [regex_token_iterator Class](../standard-library/regex-token-iterator-class.md) pro iterátory typu `string::const_iterator`.

## <a name="ssub_match-typedef"></a><a name="ssub_match"></a>ssub_match Typedef

Definice typu pro sub_match řetězců.

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [sub_match Class](../standard-library/sub-match-class.md) pro iterátory typu `string::const_iterator`.

## <a name="wcmatch-typedef"></a><a name="wcmatch"></a>wcmatch Typedef

Definice typu pro wchar_t match_results.

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [match_results Class](../standard-library/match-results-class.md) pro iterátory typu `const wchar_t*`.

## <a name="wcregex_iterator-typedef"></a><a name="wcregex_iterator"></a>wcregex_iterator Typedef

Definice typu pro wchar_t regex_iterator.

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [regex_iterator Class](../standard-library/regex-iterator-class.md) pro iterátory typu `const wchar_t*`.

## <a name="wcregex_token_iterator-typedef"></a><a name="wcregex_token_iterator"></a>wcregex_token_iterator Typedef

Definice typu pro wchar_t regex_token_iterator.

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [regex_token_iterator Class](../standard-library/regex-token-iterator-class.md) pro iterátory typu `const wchar_t*`.

## <a name="wcsub_match-typedef"></a><a name="wcsub_match"></a>wcsub_match Typedef

Definice typu pro wchar_t sub_match.

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [sub_match Class](../standard-library/sub-match-class.md) pro iterátory typu `const wchar_t*`.

## <a name="wregex-typedef"></a><a name="wregex"></a>wregex Typedef

Definice typu pro wchar_t basic_regex.

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [basic_regex Class](../standard-library/basic-regex-class.md) pro prvky typu **wchar_t**.

## <a name="wsmatch-typedef"></a><a name="wsmatch"></a>wsmatch Typedef

Definice typu pro match_results wstring.

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [match_results Class](../standard-library/match-results-class.md) pro iterátory typu `wstring::const_iterator`.

## <a name="wsregex_iterator-typedef"></a><a name="wsregex_iterator"></a>wsregex_iterator Typedef

Definice typu pro regex_iterator wstring.

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [regex_iterator Class](../standard-library/regex-iterator-class.md) pro iterátory typu `wstring::const_iterator`.

## <a name="wsregex_token_iterator-typedef"></a><a name="wsregex_token_iterator"></a>wsregex_token_iterator Typedef

Definice typu pro regex_token_iterator wstring.

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [regex_token_iterator Class](../standard-library/regex-token-iterator-class.md) pro iterátory typu `wstring::const_iterator`.

## <a name="wssub_match-typedef"></a><a name="wssub_match"></a>wssub_match Typedef

Definice typu pro sub_match wstring.

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [sub_match Class](../standard-library/sub-match-class.md) pro iterátory typu `wstring::const_iterator`.

## <a name="see-also"></a>Viz také

[\<regulární>](../standard-library/regex.md)\
[regex_constants třída](../standard-library/regex-constants-class.md)\
[regex_error třída](../standard-library/regex-error-class.md)\
[\<funkce> regulárních výrazů](../standard-library/regex-functions.md)\
[regex_iterator třída](../standard-library/regex-iterator-class.md)\
[\<operátory> regulárních výrazů](../standard-library/regex-operators.md)\
[regex_token_iterator třída](../standard-library/regex-token-iterator-class.md)\
[regex_traits – třída](../standard-library/regex-traits-class.md)
