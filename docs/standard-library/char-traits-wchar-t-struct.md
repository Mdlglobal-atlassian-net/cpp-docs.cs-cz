---
title: char_traits&lt;wchar_t&gt; – struktura
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: a2f8a882020ddb3d87436d08b3d85ea9407b1c08
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458969"
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt; – struktura

Třída, která je specializací struktury template **char_traits\<CharType >** k elementu typu **wchar_t**.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>Poznámky

Specializace umožňuje struktuře využít funkce knihovny, které pracují s objekty tohoto typu **wchar_t**.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> řetězců

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[char_traits – struktura](../standard-library/char-traits-struct.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
