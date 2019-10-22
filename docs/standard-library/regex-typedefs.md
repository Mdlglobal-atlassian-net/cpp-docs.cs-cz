---
title: '&lt;regex &gt; definice typedef'
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
ms.openlocfilehash: 4321d9ea6fd9ba57074b25e084553fe1f0846213
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689027"
---
# <a name="ltregexgt-typedefs"></a>&lt;regex &gt; definice typedef

||||
|-|-|-|
|[cmatch –](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|
|[csub_match](#csub_match)|[regulární](#regex)|[Smatch –](#smatch)|
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|
|[wcmatch –](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|
|[wcsub_match](#wcsub_match)|[wregex –](#wregex)|[wsmatch –](#wsmatch)|
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|

## <a name="cmatch"></a>cmatch – – typedef

Zadejte definici typu char match_results.

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template match_results](../standard-library/match-results-class.md) pro iterátory typu `const char*`.

## <a name="cregex_iterator"></a>cregex_iterator – typedef

Zadejte definici typu char regex_iterator.

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template regex_iterator](../standard-library/regex-iterator-class.md) pro iterátory typu `const char*`.

## <a name="cregex_token_iterator"></a>cregex_token_iterator – typedef

Definice typu pro char regex_token_iterator

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template regex_token_iterator](../standard-library/regex-token-iterator-class.md) pro iterátory typu `const char*`.

## <a name="csub_match"></a>csub_match – typedef

Zadejte definici typu char sub_match.

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template sub_match](../standard-library/sub-match-class.md) pro iterátory typu `const char*`.

## <a name="regex"></a>Regex – typedef

Zadejte definici typu char basic_regex.

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template basic_regex](../standard-library/basic-regex-class.md) pro elementy typu **char**.

> [!NOTE]
> Rozšířené znaky budou mít nepředvídatelné výsledky s `regex`. Hodnoty mimo rozsah 0 až 127 mohou mít za následek nedefinované chování.

## <a name="smatch"></a>Smatch – – typedef

Zadejte definici typu String match_results.

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template match_results](../standard-library/match-results-class.md) pro iterátory typu `string::const_iterator`.

## <a name="sregex_iterator"></a>sregex_iterator – typedef

Zadejte definici typu String regex_iterator.

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template regex_iterator](../standard-library/regex-iterator-class.md) pro iterátory typu `string::const_iterator`.

## <a name="sregex_token_iterator"></a>sregex_token_iterator – typedef

Zadejte definici typu String regex_token_iterator.

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template regex_token_iterator](../standard-library/regex-token-iterator-class.md) pro iterátory typu `string::const_iterator`.

## <a name="ssub_match"></a>ssub_match – typedef

Zadejte definici typu String sub_match.

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template sub_match](../standard-library/sub-match-class.md) pro iterátory typu `string::const_iterator`.

## <a name="wcmatch"></a>wcmatch – – typedef

Zadejte definici pro wchar_t match_results.

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template match_results](../standard-library/match-results-class.md) pro iterátory typu `const wchar_t*`.

## <a name="wcregex_iterator"></a>wcregex_iterator – typedef

Zadejte definici pro wchar_t regex_iterator.

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template regex_iterator](../standard-library/regex-iterator-class.md) pro iterátory typu `const wchar_t*`.

## <a name="wcregex_token_iterator"></a>wcregex_token_iterator – typedef

Zadejte definici pro wchar_t regex_token_iterator.

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template regex_token_iterator](../standard-library/regex-token-iterator-class.md) pro iterátory typu `const wchar_t*`.

## <a name="wcsub_match"></a>wcsub_match – typedef

Zadejte definici pro wchar_t sub_match.

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template sub_match](../standard-library/sub-match-class.md) pro iterátory typu `const wchar_t*`.

## <a name="wregex"></a>wregex – – typedef

Zadejte definici pro wchar_t basic_regex.

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template basic_regex](../standard-library/basic-regex-class.md) pro elementy typu **wchar_t**.

## <a name="wsmatch"></a>wsmatch – – typedef

Zadejte definici pro wstring match_results.

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template match_results](../standard-library/match-results-class.md) pro iterátory typu `wstring::const_iterator`.

## <a name="wsregex_iterator"></a>wsregex_iterator – typedef

Zadejte definici pro wstring regex_iterator.

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template regex_iterator](../standard-library/regex-iterator-class.md) pro iterátory typu `wstring::const_iterator`.

## <a name="wsregex_token_iterator"></a>wsregex_token_iterator – typedef

Zadejte definici pro wstring regex_token_iterator.

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template regex_token_iterator](../standard-library/regex-token-iterator-class.md) pro iterátory typu `wstring::const_iterator`.

## <a name="wssub_match"></a>wssub_match – typedef

Zadejte definici pro wstring sub_match.

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci [třídy Template sub_match](../standard-library/sub-match-class.md) pro iterátory typu `wstring::const_iterator`.

## <a name="see-also"></a>Viz také:

[\<regex >](../standard-library/regex.md) \
\ [třídy regex_constants](../standard-library/regex-constants-class.md)
\ [třídy regex_error](../standard-library/regex-error-class.md)
[funkce \<regex >](../standard-library/regex-functions.md) \
\ [třídy regex_iterator](../standard-library/regex-iterator-class.md)
[operátory \<regex >](../standard-library/regex-operators.md) \
\ [třídy regex_token_iterator](../standard-library/regex-token-iterator-class.md)
[regex_traits – třída](../standard-library/regex-traits-class.md)
