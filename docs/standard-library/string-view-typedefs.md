---
title: '&lt;string_view&gt; – definice TypeDef'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 16d7ba49facf24dcffb7df444e445d83d92255e0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346644"
---
# <a name="ltstringviewgt-typedefs"></a>&lt;string_view&gt; – definice TypeDef

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a> string_view

Typ, který popisuje specializace šablony třídy [basic_string_view](../standard-library/basic-string-view-class.md) elementy typu **char**.

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>Poznámky

Níže jsou ekvivalentní deklarace:

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

Seznam konstruktory řetězce najdete v tématu [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string_view"></a> u16string_view

Typ, který popisuje specializace šablony třídy [basic_string_view](../standard-library/basic-string-view-class.md) elementy typu `char16_t`.

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>Poznámky

Seznam konstruktory řetězce najdete v tématu [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string_view"></a> u32string_view

Typ, který popisuje specializace šablony třídy [basic_string_view](../standard-library/basic-string-view-class.md) elementy typu `char32_t`.

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>Poznámky

Seznam konstruktory řetězce najdete v tématu [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring_view"></a>  wstring_view

Typ, který popisuje specializace šablony třídy [basic_string_view](../standard-library/basic-string-view-class.md) elementy typu **wchar_t**.

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>Poznámky

Níže jsou ekvivalentní deklarace:

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

Seznam konstruktory řetězce najdete v tématu [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Velikost **wchar_t** je o dva bajty na Windows, ale to není nutně platí pro všechny platformy. Pokud potřebujete typ širokého znaku string_view pomocí šířku, která je zaručeně, zůstane na všech platformách, [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) nebo [u32string_view](../standard-library/string-view-typedefs.md#u32string_view).

## <a name="see-also"></a>Viz také:

[\<string_view>](../standard-library/string-view.md)<br/>
