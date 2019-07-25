---
title: char_traits&lt;char16_t&gt; – struktura
ms.date: 11/04/2016
f1_keywords:
- char_traits<char16_t>
- iosfwd/std::char_traits<char16_t>
helpviewer_keywords:
- char_traits<char16_t> class
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
ms.openlocfilehash: d83f5278c2c4f8344334bfce40946612e9ca3e56
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448968"
---
# <a name="chartraitsltchar16tgt-struct"></a>char_traits&lt;char16_t&gt; – struktura

Struktura, která je specializací struktury template **\<char_traits CharType >** k elementu typu. `char16_t`

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<char16_t>;
```

## <a name="remarks"></a>Poznámky

Specializace umožňuje struktuře využít funkce knihovny, které pracují s objekty typu `char16_t`.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> řetězců

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<> řetězců](../standard-library/string.md)\
[char_traits – struktura](../standard-library/char-traits-struct.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
