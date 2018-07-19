---
title: '&lt;regulární výraz&gt; – definice TypeDef | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b32031103e6e6d9922fdb3b0fc3a0d95e5eb280c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957038"
---
# <a name="ltregexgt-typedefs"></a>&lt;regulární výraz&gt; – definice TypeDef

||||
|-|-|-|
|[cmatch](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|
|[csub_match](#csub_match)|[regex](#regex)|[smatch](#smatch)|
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|
|[wcmatch](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|
|[wcsub_match](#wcsub_match)|[wregex](#wregex)|[wsmatch](#wsmatch)|
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|

## <a name="cmatch"></a>  cmatch – Typedef

Zadejte definici match_results – char.

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [match_results – třída](../standard-library/match-results-class.md) u iterátorů typu `const char*`.

## <a name="cregex_iterator"></a>  cregex_iterator – Typedef

Zadejte definici regex_iterator – char.

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [regex_iterator – třída](../standard-library/regex-iterator-class.md) u iterátorů typu `const char*`.

## <a name="cregex_token_iterator"></a>  cregex_token_iterator – Typedef

Definice typu char regex_token_iterator –

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md) u iterátorů typu `const char*`.

## <a name="csub_match"></a>  csub_match – Typedef

Zadejte definici sub_match – char.

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [sub_match – třída](../standard-library/sub-match-class.md) u iterátorů typu `const char*`.

## <a name="regex"></a>  Regex – Typedef

Zadejte definici basic_regex – char.

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [basic_regex – třída](../standard-library/basic-regex-class.md) pro prvky typu **char**.

> [!NOTE]
> Rozšířené znaky budou mít nepředvídatelné výsledky s `regex`. Hodnoty mimo rozsah 0 až 127 může mít za následek nedefinované chování.

## <a name="smatch"></a>  smatch – Typedef

Zadejte definici match_results – řetězec.

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [match_results – třída](../standard-library/match-results-class.md) u iterátorů typu `string::const_iterator`.

## <a name="sregex_iterator"></a>  sregex_iterator – Typedef

Zadejte definici regex_iterator – řetězec.

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [regex_iterator – třída](../standard-library/regex-iterator-class.md) u iterátorů typu `string::const_iterator`.

## <a name="sregex_token_iterator"></a>  sregex_token_iterator – Typedef

Zadejte definici regex_token_iterator – řetězec.

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md) u iterátorů typu `string::const_iterator`.

## <a name="ssub_match"></a>  ssub_match – Typedef

Zadejte definici sub_match – řetězec.

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [sub_match – třída](../standard-library/sub-match-class.md) u iterátorů typu `string::const_iterator`.

## <a name="wcmatch"></a>  wcmatch – Typedef

Zadejte definici match_results – wchar_t.

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [match_results – třída](../standard-library/match-results-class.md) u iterátorů typu `const wchar_t*`.

## <a name="wcregex_iterator"></a>  wcregex_iterator – Typedef

Zadejte definici regex_iterator – wchar_t.

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [regex_iterator – třída](../standard-library/regex-iterator-class.md) u iterátorů typu `const wchar_t*`.

## <a name="wcregex_token_iterator"></a>  wcregex_token_iterator – Typedef

Zadejte definici regex_token_iterator – wchar_t.

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md) u iterátorů typu `const wchar_t*`.

## <a name="wcsub_match"></a>  wcsub_match – Typedef

Zadejte definici sub_match – wchar_t.

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [sub_match – třída](../standard-library/sub-match-class.md) u iterátorů typu `const wchar_t*`.

## <a name="wregex"></a>  wregex – Typedef

Zadejte definici basic_regex – wchar_t.

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [basic_regex – třída](../standard-library/basic-regex-class.md) pro prvky typu **wchar_t**.

## <a name="wsmatch"></a>  wsmatch – Typedef

Zadejte definici match_results wstring –.

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [match_results – třída](../standard-library/match-results-class.md) u iterátorů typu `wstring::const_iterator`.

## <a name="wsregex_iterator"></a>  wsregex_iterator – Typedef

Zadejte definici regex_iterator wstring –.

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [regex_iterator – třída](../standard-library/regex-iterator-class.md) u iterátorů typu `wstring::const_iterator`.

## <a name="wsregex_token_iterator"></a>  wsregex_token_iterator – Typedef

Zadejte definici regex_token_iterator wstring –.

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md) u iterátorů typu `wstring::const_iterator`.

## <a name="wssub_match"></a>  wssub_match – Typedef

Zadejte definici sub_match wstring –.

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [sub_match – třída](../standard-library/sub-match-class.md) u iterátorů typu `wstring::const_iterator`.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants – třída](../standard-library/regex-constants-class.md)<br/>
[regex_error – třída](../standard-library/regex-error-class.md)<br/>
[\<regulární výraz > funkce](../standard-library/regex-functions.md)<br/>
[regex_iterator – třída](../standard-library/regex-iterator-class.md)<br/>
[\<regulární výraz > operátory](../standard-library/regex-operators.md)<br/>
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits – třída](../standard-library/regex-traits-class.md)<br/>
