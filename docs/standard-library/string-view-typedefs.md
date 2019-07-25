---
title: '&lt;string_view&gt; definice typedef'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: c3367afe1353ac70abb74a59658a255614ac8470
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459185"
---
# <a name="ltstringviewgt-typedefs"></a>&lt;string_view&gt; definice typedef

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a>string_view

Typ, který popisuje specializaci šablony třídy [basic_string_view](../standard-library/basic-string-view-class.md) s elementy typu **char**.

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>Poznámky

Níže jsou uvedené ekvivalentní deklarace:

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

Seznam konstruktorů řetězců naleznete v tématu [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string_view"></a>u16string_view

Typ, který popisuje specializaci šablony třídy [basic_string_view](../standard-library/basic-string-view-class.md) s prvky typu `char16_t`.

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>Poznámky

Seznam konstruktorů řetězců naleznete v tématu [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string_view"></a>u32string_view

Typ, který popisuje specializaci šablony třídy [basic_string_view](../standard-library/basic-string-view-class.md) s prvky typu `char32_t`.

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>Poznámky

Seznam konstruktorů řetězců naleznete v tématu [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring_view"></a>wstring_view

Typ, který popisuje specializaci šablony třídy [basic_string_view](../standard-library/basic-string-view-class.md) s prvky typu **wchar_t**.

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>Poznámky

Níže jsou uvedené ekvivalentní deklarace:

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

Seznam konstruktorů řetězců naleznete v tématu [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Velikost **wchar_t** má dva bajty ve Windows, ale to není nutně případ pro všechny platformy. Pokud potřebujete string_view typ širokého znaku s šířkou, která je zaručená, aby zůstala stejná na všech platformách, použijte [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) nebo [u32string_view](../standard-library/string-view-typedefs.md#u32string_view).

## <a name="see-also"></a>Viz také:

[\<string_view>](../standard-library/string-view.md)
