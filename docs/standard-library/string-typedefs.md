---
title: '&lt;řetězec&gt; – definice TypeDef | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 5747d511777ae6f1f32d8e93bb6ee90bd0193bf9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959976"
---
# <a name="ltstringgt-typedefs"></a>&lt;řetězec&gt; – definice TypeDef

||||
|-|-|-|
|[string](#string)|[u16string](#u16string)|[u32string](#u32string)|
|[wstring](#wstring)|

## <a name="string"></a>  řetězec

Typ, který popisuje specializace třídy šablony [basic_string](../standard-library/basic-string-class.md) elementy typu **char**.

Jiné – definice TypeDef, která specialize `basic_string` zahrnují [wstring](../standard-library/string-typedefs.md#wstring), [u16string](../standard-library/string-typedefs.md#u16string), a [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>Poznámky

Níže jsou ekvivalentní deklarace:

```cpp
string str("");

basic_string<char> str("");
```

Seznam konstruktory řetězce najdete v tématu [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string"></a>  u16string

Typ, který popisuje specializace třídy šablony [basic_string](../standard-library/basic-string-class.md) elementy typu `char16_t`.

Jiné – definice TypeDef, která specialize `basic_string` zahrnují [wstring](../standard-library/string-typedefs.md#wstring), [řetězec](../standard-library/string-typedefs.md#string), a [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>Poznámky

Seznam konstruktory řetězce najdete v tématu [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string"></a>  u32string

Typ, který popisuje specializace třídy šablony [basic_string](../standard-library/basic-string-class.md) elementy typu `char32_t`.

Jiné – definice TypeDef, která specialize `basic_string` zahrnují [řetězec](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string), a [wstring](../standard-library/string-typedefs.md#wstring).

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>Poznámky

Seznam konstruktory řetězce najdete v tématu [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring"></a>  wstring

Typ, který popisuje specializace třídy šablony [basic_string](../standard-library/basic-string-class.md) elementy typu **wchar_t**.

Jiné – definice TypeDef, která specialize `basic_string` zahrnují [řetězec](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string), a [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>Poznámky

Níže jsou ekvivalentní deklarace:

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

Seznam konstruktory řetězce najdete v tématu [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Velikost **wchar_t** je definováno implementací. Pokud váš kód závisí na **wchar_t** být určité velikosti, zkontrolujte implementace pro vaši platformu (třeba index Mei `sizeof(wchar_t)`). Pokud potřebujete znaku řetězec pomocí šířku, která je zaručeně, zůstane na všech platformách, [řetězec](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string), nebo [u32string](../standard-library/string-typedefs.md#u32string).

## <a name="see-also"></a>Viz také:

[\<řetězec >](../standard-library/string.md)<br/>
