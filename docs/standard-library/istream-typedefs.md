---
title: '&lt;IStream on Request&gt; – definice TypeDef | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: 20d92a0bf759c9f8170464985bd2b8af4d2bec08
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852266"
---
# <a name="ltistreamgt-typedefs"></a>&lt;IStream on Request&gt; – definice TypeDef

||||
|-|-|-|
|[iostream](#iostream)|[IStream on Request](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>  iostream

Typ `basic_iostream` specializované na `char`.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_iostream](../standard-library/basic-iostream-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.

## <a name="istream"></a>  IStream on Request

Typ `basic_istream` specializované na `char`.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_istream](../standard-library/basic-istream-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.

## <a name="wiostream"></a>  wiostream

Typ `basic_iostream` specializované na `wchar_t`.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_iostream](../standard-library/basic-iostream-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.

## <a name="wistream"></a>  wistream

Typ `basic_istream` specializované na `wchar_t`.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_istream](../standard-library/basic-istream-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.

## <a name="see-also"></a>Viz také

[\<IStream on Request >](../standard-library/istream.md)<br/>
